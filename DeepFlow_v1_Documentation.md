# DeepFlow v1.0 — Order Flow Analytics for TradingView

## Architecture & Design Philosophy

DeepFlow is a PineScript v6 indicator that brings DeepCharts-grade order flow analysis to TradingView. It leverages the `request.footprint()` API (shipped March 2026) to access **true buy/sell volume, Point of Control, Value Area, delta, and per-row imbalances** — eliminating the need for bid/ask approximations that older PineScript indicators relied on.

### Core Principle

> On tick charts, every bar is one executed trade. Each tick can carry a massive block of contracts. DeepFlow treats every tick as a meaningful data point, applying statistical methods to extract institutional footprints from the tape.

### Data Pipeline

```
request.footprint()          ← Primary: real exchange buy/sell data
        │
        ├──→ fp.buy_volume() / fp.sell_volume() / fp.delta()
        ├──→ fp.poc() / fp.vah() / fp.val()
        ├──→ fp.rows() → volume_row[] → imbalance scanning
        │
        ▼
Heuristic Fallback           ← Secondary: when footprint returns na
  buyVol = volume × (close - low) / (high - low)
  sellVol = volume - buyVol
```

The footprint engine provides exchange-level buy/sell classification (trades at ask = buy, trades at bid = sell). The heuristic fallback activates only on bars where footprint data is unavailable.

### Requirements

| Requirement | Detail |
|---|---|
| **TradingView Plan** | Premium or Ultimate (for `request.footprint()`) |
| **PineScript Version** | v6 |
| **Recommended Timeframe** | 1T (tick), 1–5 min for intraday |
| **Target Markets** | CME/CBOT futures: ES, NQ, YM, RTY, CL, GC, ZB, ZN, 6E |

---

## Module Reference

### Module 1: CVD — Cumulative Volume Delta

**What it does:** Tracks the running sum of (buy volume − sell volume) across all bars. CVD reveals the cumulative directional pressure beneath price — whether buyers or sellers are in control over time.

**How it works:**

```
delta = fp.delta()                    // True buy − sell per bar
cvd   = cumulative_sum(delta)         // Running total
cvdMA = SMA(cvd, length)             // Smoothed trend
```

**Divergence Detection:** The module scans for disagreements between price and CVD:

- **Bullish divergence:** Price makes a lower low, but CVD makes a higher low. Sellers are losing conviction despite pushing price down. Mean-reversion setup.
- **Bearish divergence:** Price makes a higher high, but CVD makes a lower high. Buyers are weakening despite the price advance. Exhaustion signal.

**Display:**
- CVD line + moving average plotted in a **separate pane** below the chart
- Divergence diamonds plotted on the **main chart** at the divergence bar

**Key Settings:**

| Setting | Default | Purpose |
|---|---|---|
| CVD MA Length | 20 | Smoothing period for the CVD trend line |
| Divergence Lookback | 10 | Bars to scan for swing extremes |

**Trading Application:**

| Model | Signal |
|---|---|
| Mean-Reversion | CVD bullish divergence near support → long entry |
| Continuation | CVD confirming trend (rising CVD + rising price) → hold/add |

---

### Module 2: Big Trades Detection

**What it does:** Identifies institutional-size orders by flagging bars where volume is a statistical outlier relative to recent activity. On tick charts, each bar is a single trade — so volume = contracts in that execution.

**How it works:**

```
mean      = SMA(volume, lookback)
stdev     = STDEV(volume, lookback)
threshold = mean + multiplier × stdev

isBigTrade = volume > max(threshold, minContracts)
direction  = delta >= 0 ? BUY : SELL
```

This is a direct approximation of DeepCharts' **Deep Trades** feature, which uses MBO (Market-by-Order) data for order reconstruction. Since we lack MBO data, we use statistical anomaly detection instead. On tick data this is highly effective because each bar IS a single order execution.

**Display:** Labels at each big trade showing contract count, colored cyan (buy) or deep orange (sell).

**Key Settings:**

| Setting | Default | Tuning Guide |
|---|---|---|
| Statistical Lookback | 100 | More bars = smoother threshold, slower to adapt |
| Std Dev Multiplier | 2.5 | Lower = more signals (2.0), higher = fewer but stronger (3.5) |
| Min Contracts Filter | 0 | Absolute floor. Set per-instrument (see table below) |
| Max Markers | 50 | Keeps chart clean. Oldest markers auto-delete |

**Recommended Minimum Contracts by Instrument:**

| Instrument | Typical Big Trade | Suggested Min |
|---|---|---|
| ES (E-mini S&P) | 50–200+ contracts | 50 |
| NQ (E-mini Nasdaq) | 20–100+ contracts | 20 |
| YM (E-mini Dow) | 30–150+ contracts | 30 |
| CL (Crude Oil) | 100–500+ contracts | 100 |
| GC (Gold) | 50–200+ contracts | 50 |
| ZB (30-Year Bond) | 100–500+ contracts | 100 |

**Trading Application:**

| Model | Signal |
|---|---|
| Continuation | Big buy trade in an uptrend → institutional commitment to the move |
| Mean-Reversion | Big sell trade at support + absorption signal → trapped sellers |

---

### Module 3: Exhaustion / Absorption

**What it does:** Detects two critical order flow patterns that precede reversals or confirm trend strength.

#### Exhaustion

Heavy delta (aggressive orders) but minimal price movement. Aggressive participants are "running out of energy" — their orders are being fully absorbed by passive counterparties.

```
isExhaustion = |delta| > avgDelta × multiplier
               AND barRange < ATR × priceFactor
               AND volume > avgVolume × 1.2
```

- **Buy Exhaustion (EXH at top):** Massive buying delta, but price didn't rise. Passive sellers absorbing all buy pressure → potential top.
- **Sell Exhaustion (EXH at bottom):** Massive selling delta, but price didn't fall. Passive buyers absorbing all sell pressure → potential bottom.

#### Absorption

Price moves one direction, but delta reveals the opposite side was more aggressive. The passive side "absorbed" the aggressive side's pressure.

```
Bullish Absorption = bearish candle (close < open)
                     AND positive delta (buyers more aggressive)
                     AND significant volume
                     → Passive buyers won. Price likely to reverse up.

Bearish Absorption = bullish candle (close > open)
                     AND negative delta (sellers more aggressive)
                     AND significant volume
                     → Passive sellers won. Price likely to reverse down.
```

**Display:**
- **EXH** labels in yellow — positioned above bar for buy exhaustion, below for sell exhaustion
- **ABS ▲** labels in teal (bullish absorption), **ABS ▼** in purple (bearish absorption)

**Key Settings:**

| Setting | Default | Purpose |
|---|---|---|
| Delta Threshold (× avg) | 2.0 | Delta must exceed this multiple of average |
| Exhaustion Max Price Move | 0.3 | Price range must be below 30% of ATR |
| ATR Length | 14 | Period for ATR calculation |
| Max Markers | 30 | Chart cleanliness |

**Trading Application:**

| Model | Signal |
|---|---|
| Mean-Reversion | Exhaustion at key level (POC, VA, naked POC) → reversal entry |
| Continuation | Absorption WITH trend → strong hands defending, trend continues |
| Confluence | Exhaustion + CVD divergence + FVG = highest probability reversal |

---

### Module 4: IVB — Initial Volume Balance

**What it does:** Implements DeepCharts' **Deep-M IVB** concept — an Opening Range Breakout strategy enhanced with volume confirmation. Tracks the high/low of the first N minutes after RTH open, then monitors for volume-confirmed breakouts.

**How it works:**

```
1. RTH session starts → begin tracking IB high/low
2. For the first N minutes, update IB range
3. After IB period ends → IB is "complete"
4. Monitor for breakouts:
   - close > IB_High AND volume > sessionAvg × multiplier → BREAKOUT UP
   - close < IB_Low  AND volume > sessionAvg × multiplier → BREAKOUT DOWN
```

**Display:**
- Dashed blue-gray **box** spanning the IB range
- Dotted **extension lines** projecting IB high/low to session end
- Amber **arrow markers** at breakout points

**Key Settings:**

| Setting | Default | Purpose |
|---|---|---|
| RTH Session | 0930-1600 | Regular trading hours (adjust per instrument) |
| Timezone | America/New_York | Exchange timezone |
| IB Period (minutes) | 30 | Classic 30-min IB. Also try 5, 15, 60 |
| Extend Lines | true | Project IB levels through the session |
| Breakout Volume | 1.5× avg | Volume confirmation threshold |

**Session Times by Instrument:**

| Instrument | RTH Session | Timezone |
|---|---|---|
| ES, NQ, YM, RTY | 0930-1600 | America/New_York |
| CL | 0900-1430 | America/New_York |
| GC | 0820-1330 | America/New_York |
| ZB, ZN | 0820-1500 | America/New_York |
| 6E | 0820-1500 | America/New_York |

**Trading Application:**

| Model | Signal |
|---|---|
| Mean-Reversion | Price INSIDE IB + near POC → fade extremes toward IB midpoint |
| Continuation | IB breakout with volume → ride the breakout direction |
| Context | 80% of IB breakouts that fail within 15 min → mean-reversion opportunity |

---

### Module 5: FVG / IFVG — Fair Value Gaps

**What it does:** Automatically detects Fair Value Gaps (3-candle price imbalances) and tracks them as dynamic support/resistance zones. When an FVG is fully mitigated (filled), it optionally converts to an **Inverse FVG (IFVG)** — a zone that flips polarity and acts as S/R from the opposite direction.

**How it works:**

```
Bullish FVG: bar[0].low > bar[2].high  (gap up between current bar and 2 bars ago)
Bearish FVG: bar[0].high < bar[2].low  (gap down)

Gap must exceed minAtrMult × ATR to filter noise.

Mitigation: When price closes through an FVG zone
  → If IFVG enabled: zone flips color (purple) and acts as opposing S/R
  → If auto-remove enabled: zone is deleted
  → IFVG is removed when price breaks through it again
```

**Display:**
- Green semi-transparent boxes for bullish FVGs
- Red semi-transparent boxes for bearish FVGs
- Purple semi-transparent boxes for IFVGs
- All boxes auto-extend rightward and auto-delete after 500 bars

**Key Settings:**

| Setting | Default | Purpose |
|---|---|---|
| Max Active Boxes | 15 | Prevents chart clutter |
| Auto-Remove Mitigated | true | Clean up filled FVGs |
| Convert to IFVG | true | Flip mitigated FVGs to inverse S/R |
| Min Gap Size (× ATR) | 0.1 | Filter tiny insignificant gaps |
| Box Transparency | 85 | Visual weight (lower = more opaque) |

**Trading Application:**

| Model | Signal |
|---|---|
| Mean-Reversion | Price enters unfilled FVG → trade the fill (expect mean-reversion to gap midpoint) |
| Continuation | Price respects FVG as support/resistance → bounce confirms trend |
| IFVG Play | Mitigated bullish FVG becomes resistance → short entries at IFVG level |

---

### Module 6: Volume Profile S/R Zones

**What it does:** Extracts real-time POC, Value Area High, and Value Area Low from the footprint data and displays them as dynamic support/resistance levels. Additionally tracks **Naked POCs** — previous session POCs that have never been retested by price — which act as powerful price magnets.

**How it works:**

```
POC = fp.poc()      → Price level with highest total volume (market consensus)
VAH = fp.vah()      → Upper bound of 70% volume zone (fair value ceiling)
VAL = fp.val()      → Lower bound of 70% volume zone (fair value floor)

Naked POC Tracking:
  1. On new RTH session → store previous session's POC
  2. Each bar → check if price touched any stored POC
  3. If touched → remove (no longer naked)
  4. If untouched → extend the dashed line forward
```

**Display:**
- **POC:** Solid orange line (current bar's POC)
- **VAH/VAL:** Dotted blue lines with semi-transparent fill between them
- **Naked POCs:** Dashed coral lines extending from the session they were created

**Bonus: Imbalance Scanner**
Scans all footprint rows for stacked buy/sell imbalances (3+ consecutive rows where one side dominates 3:1). These mark institutional demand/supply zones.

**Key Settings:**

| Setting | Default | Purpose |
|---|---|---|
| Track Naked POCs | true | Enable/disable naked POC tracking |
| Max Naked POCs | 10 | Limit displayed historical POCs |
| Show Value Area | true | VAH/VAL lines + fill |
| Show Session POC | true | Current bar POC line |
| S/R Line Width | 2 | Visual weight of level lines |

**Trading Application:**

| Model | Signal |
|---|---|
| Mean-Reversion | Price at/beyond VA boundary → expect rotation back toward POC |
| Mean-Reversion | Price approaching naked POC → magnet effect, expect interaction |
| Continuation | Price accepting above VAH (multiple bars) → bullish acceptance, buy dips |
| Confluence | Naked POC + FVG zone + exhaustion signal = highest probability reversal |

---

## Trading Models

### Mean-Reversion Model

The core premise: price oscillates around the Volume Profile POC. When price deviates too far (beyond VA), exhaustion signals appear, or FVGs get filled, it tends to revert.

**Entry Confluence Stack (strongest to weakest):**

1. Price at VAH/VAL or naked POC level
2. Exhaustion signal (EXH) at the level
3. CVD divergence confirming loss of momentum
4. FVG or IFVG zone at the level
5. Big trade(s) opposing the trend at the level
6. Price inside IVB range (rotation environment)

**How to trade it:**
- Wait for 2+ confluence factors
- Enter toward POC direction
- Stop beyond the VA extreme or recent swing
- Target: POC (first), opposite VA boundary (second)

### Continuation Model

The core premise: when price breaks through a level with genuine order flow support, the trend continues.

**Entry Confluence Stack:**

1. IVB breakout with volume confirmation
2. CVD confirming (rising CVD + rising price, or falling CVD + falling price)
3. Bullish absorption during pullback (passive buyers defending, trend intact)
4. Price accepting above/below VA (multiple bars closing beyond)
5. Big trades in trend direction (institutional commitment)
6. FVG left behind in the move (unfilled gap = supply/demand imbalance)

**How to trade it:**
- Wait for breakout with 2+ confluence factors
- Enter on first pullback that holds (absorption + VA acceptance)
- Stop below the breakout level (IB high/low or VA boundary)
- Target: ADR extension, next naked POC, or next significant FVG

---

## Configuration Guide by Instrument

### ES (E-mini S&P 500)
```
Ticks Per Row: 1-4          (1 tick = $12.50)
IB Session:    0930-1600    (New York)
IB Period:     30 min
Min Contracts: 50
Std Dev Mult:  2.5
```

### NQ (E-mini Nasdaq)
```
Ticks Per Row: 1-4          (1 tick = $5.00)
IB Session:    0930-1600    (New York)
IB Period:     30 min
Min Contracts: 20
Std Dev Mult:  2.5
```

### YM (E-mini Dow)
```
Ticks Per Row: 1-5          (1 tick = $5.00)
IB Session:    0930-1600    (New York)
IB Period:     30 min
Min Contracts: 30
Std Dev Mult:  2.5
```

### CL (Crude Oil)
```
Ticks Per Row: 5-10         (1 tick = $10.00)
IB Session:    0900-1430    (New York)
IB Period:     15 min
Min Contracts: 100
Std Dev Mult:  2.0          (CL is more volatile, lower threshold catches action)
```

### GC (Gold)
```
Ticks Per Row: 5-10         (1 tick = $10.00)
IB Session:    0820-1330    (New York)
IB Period:     30 min
Min Contracts: 50
Std Dev Mult:  2.5
```

### ZB / ZN (Treasury Bonds / Notes)
```
Ticks Per Row: 1-2          (ZB: 1 tick = $31.25)
IB Session:    0820-1500    (New York)
IB Period:     30 min
Min Contracts: 100
Std Dev Mult:  2.5
```

---

## Dashboard Panel

The real-time dashboard displays in a configurable corner of the chart:

| Metric | Description |
|---|---|
| **Delta** | Current bar's buy − sell volume (green/red) |
| **CVD** | Running cumulative delta value |
| **Buy Vol** | Current bar's buy volume |
| **Sell Vol** | Current bar's sell volume |
| **POC** | Current bar's Point of Control price |
| **VAH** | Current Value Area High |
| **VAL** | Current Value Area Low |
| **IVB** | Status: FORMING / INSIDE / BREAK ▲ / BREAK ▼ |

---

## Alert System

DeepFlow provides 8 configurable alerts:

| Alert | Trigger |
|---|---|
| Big Buy Trade | Volume outlier with positive delta |
| Big Sell Trade | Volume outlier with negative delta |
| Buy Exhaustion | High buying delta, price stalled |
| Sell Exhaustion | High selling delta, price stalled |
| Bullish Absorption | Bearish bar but positive delta |
| Bearish Absorption | Bullish bar but negative delta |
| IVB Breakout Up | Price breaks above IB with volume |
| IVB Breakout Down | Price breaks below IB with volume |
| CVD Bullish Divergence | Price lower low, CVD higher low |
| CVD Bearish Divergence | Price higher high, CVD lower high |

Set these in TradingView via the indicator's alert configuration panel.

---

## Color Theme Reference

DeepFlow uses a dark-mode palette inspired by DeepCharts:

| Element | Color | Hex |
|---|---|---|
| Buy / Bullish | Bright green | `#00E676` |
| Sell / Bearish | Bright red | `#FF1744` |
| POC | Orange | `#FF9100` |
| Value Area | Blue | `#2979FF` |
| VWAP / CVD | Light blue | `#42A5F5` |
| Bullish Absorption | Teal | `#00BFA5` |
| Bearish Absorption | Purple | `#D500F9` |
| Exhaustion | Yellow | `#FFD600` |
| Big Trade Buy | Cyan | `#00E5FF` |
| Big Trade Sell | Deep orange | `#FF6D00` |
| FVG Bullish | Green | `#00C853` |
| FVG Bearish | Red | `#FF1744` |
| IFVG | Purple | `#AB47BC` |
| IVB Range | Blue-gray | `#78909C` |
| IVB Breakout | Amber | `#FFAB00` |
| Naked POC | Coral | `#FF6E40` |
| Dashboard BG | Dark navy | `#1A1A2E` |

---

## Technical Notes

### Performance on Tick Charts
On 1T charts, each bar is a single trade. The footprint data per-bar is minimal (often 1 row), but delta/buy/sell classification is precise. The Big Trades and CVD modules are most powerful on tick data. Volume Profile S/R becomes more meaningful on 1–5 min charts where multiple ticks aggregate.

### Footprint Limitations
- Only **one** `request.footprint()` call allowed per script
- Requires **Premium or Ultimate** TradingView plan
- Returns `na` on bars without footprint data (handled gracefully via fallback)
- Cannot request footprint data for a different timeframe

### `bid` / `ask` Variables (1T Only)
PineScript v6 added `bid` and `ask` built-in variables, available only on the 1T timeframe. These provide the best bid/ask prices at the time of each tick. DeepFlow currently uses the footprint API for buy/sell classification (which is more comprehensive), but these variables could be used for additional precision in future versions.

### Object Limits
PineScript allows max 500 each of boxes, labels, and lines. DeepFlow manages these via:
- Configurable `Max Markers` per module
- Auto-deletion of oldest objects when limits are reached
- Age-based removal (FVG boxes older than 500 bars are cleaned up)

---

## Version History

| Version | Date | Changes |
|---|---|---|
| v1.0 | 2026-04 | Initial release. 6 modules, footprint engine, dashboard, alerts. |

---

*DeepFlow is not affiliated with DeepCharts® or Volumetrica Trading. DeepCharts® is a registered trademark of Volumetrica Trading. This indicator is inspired by their concepts and reimplemented independently for TradingView using PineScript v6.*
