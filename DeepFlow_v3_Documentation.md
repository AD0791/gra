# DeepFlow v3.0 — Exhaustion & Absorption Detector

## One Tool, One Job

DeepFlow v3 does one thing: it detects where aggressive orders die. Every other feature exists to make that detection more visible and more actionable.

When buyers fire heavy and price doesn't move — that's exhaustion. When a candle drops but the internals reveal buyers were actually stronger — that's absorption. Both patterns precede reversals. Both patterns are invisible on a standard chart. DeepFlow makes them visible as volume-proportional bubbles locked inside the candle wicks.

---

## How It Works

### The Intrabar Delta Engine

DeepFlow locks ALL calculations to a single intrabar resolution: **1S** (default), **1T** (tick), or **1min**. No auto-selection, no downsampling, no shortcuts. Every single intrabar at your chosen granularity is processed and classified.

**Available resolutions:**

| Resolution | What Each Intrabar Is | Default |
|---|---|---|
| **1S** | Every 1-second bar. One second of aggregated trades. | ✅ Default |
| **1T** | Every single executed trade. Maximum possible granularity. | |
| **1** | Every 1-minute bar. Deepest history but lowest precision. | |

**Intrabars per chart bar and history depth (1S default):**

TradingView enforces a hard 100,000 total intrabar limit. With 1S resolution, the math is simple: chart bar duration in seconds = intrabars per bar.

| Execution Chart | Intrabars per Bar | Available History |
|---|---|---|
| **2H** | 7,200 | ~13 bars |
| **1H** | 3,600 | ~27 bars |
| **4H** | 14,400 | ~6 bars |

| Monitoring Chart | Intrabars per Bar | Available History |
|---|---|---|
| **5 min** | 300 | ~333 bars |
| **15 min** | 900 | ~111 bars |
| **30 min** | 1,800 | ~55 bars |
| **45 min** | 2,700 | ~37 bars |

**The tradeoff is intentional.** On your 2H execution chart with 1S, you get 13 bars of data where every single second has been classified as buy or sell. That's 7,200 data points per bar constructing the delta. The precision is extreme. The S/R zone engine adapts automatically — it builds zones from whatever history is available.

If you need deeper history for zone context, switch to 1min resolution. You'll get 833 bars of history on 2H with 120 intrabars per bar — still solid delta precision with much more zone data.

**Why 1S is the default:** You're paying for second-level data. Every second of market activity on CME/CBOT futures can carry thousands of contracts. 1S resolution means no second is discarded, no data is wasted. On a 1H bar, 3,600 data points classify the session's buy/sell pressure with ~85-90% accuracy compared to true tick-by-tick tape.

### Cascading Priority Engine

The script enforces a strict priority order at runtime — not just in the default setting:

```
PRIORITY 1 → Your selected resolution (1S default, or 1T)
             If intrabars are returned → USE THEM. Done.
             Dashboard shows: "3600 × 1S" in TEAL.

PRIORITY 2 → 1-minute fallback (auto-loaded in background)
             Only activates if Priority 1 returns 0 intrabars.
             This means your data plan doesn't cover 1S for this symbol,
             or TradingView hit an intrabar limit.
             Dashboard shows: "120 × 1m FALLBACK" in YELLOW. ⚠️

PRIORITY 3 → Chaikin MFM formula (absolute last resort)
             Only activates if BOTH 1S and 1min return nothing.
             Should NEVER happen on CME/CBOT futures.
             Dashboard shows: "0 × CHAIKIN ⚠️" in RED.
             If you see this, something is broken.
```

The 1-minute data is always fetched in the background alongside your primary resolution. This costs one extra `request.*` call but guarantees you never silently fall to the crude Chaikin formula. The dashboard color-codes the engine status so you always know exactly what's driving your signals.

Each intrabar is classified as BUY or SELL using Buying/Selling Pressure analysis: if the close is in the upper half of the intrabar's range, buyers dominated. Lower half, sellers dominated. Across 120 intrabars on a 2H chart, this produces a reliable estimate of total buying volume vs. selling volume.

Delta = Buy Volume − Sell Volume. This is the net aggression.

### Exhaustion Detection

Exhaustion occurs when aggressive orders fire heavily but price barely moves. The passive side absorbed every contract.

```
CONDITIONS (all must be true):
  |delta| > average |delta| × threshold
  bar range < ATR × price factor
  bar range > 0 (not a perfect doji gap)
  volume > average volume × volume threshold
```

**Buy Exhaustion (yellow bubble at HIGH):** Buyers pushed hard (positive delta > threshold), but the bar is tiny. Passive sellers ate everything. The buying energy is spent. Potential top.

**Sell Exhaustion (amber bubble at LOW):** Sellers pushed hard (negative delta > threshold), but the bar is tiny. Passive buyers ate everything. The selling energy is spent. Potential bottom.

### Absorption Detection

Absorption occurs when the candle "lies" — its color doesn't match who was actually more aggressive.

```
CONDITIONS (all must be true):
  |delta| > average |delta| × threshold
  volume > average volume × volume threshold
  price direction ≠ delta direction
```

**Bullish Absorption (teal bubble at LOW):** Red candle (close < open) but delta is positive. Inside the candle, there were more buying-pressure intrabars than selling-pressure ones. Hidden demand under a bearish surface. Price likely reverses up.

**Bearish Absorption (purple bubble at HIGH):** Green candle (close > open) but delta is negative. Hidden supply under a bullish surface. Price likely reverses down.

### Why This Works on 1H/2H/4H

On a tick chart, exhaustion lasts seconds. On a 2H chart, exhaustion means **two full hours** where aggressive participants fired and failed. That's not a blip — it's institutional battle data. The signal-to-noise ratio is genuinely higher on these timeframes because you're capturing session-scale dynamics, not micro-noise.

---

## The Bubble System

### Visual Language

| Bubble | Color | Position | Meaning |
|---|---|---|---|
| ● Yellow | `#FFD600` | At HIGH | Buy exhaustion — buyers spent, potential top |
| ● Amber | `#FFAB00` | At LOW | Sell exhaustion — sellers spent, potential bottom |
| ● Teal | `#00BFA5` | At LOW | Bullish absorption — hidden demand |
| ● Purple | `#D500F9` | At HIGH | Bearish absorption — hidden supply |

### Bubble Size = Institutional Footprint

Bubble diameter is proportional to the bar's volume relative to its rolling average. A bar with 3× average volume produces a bubble near the maximum size. A bar with average volume produces a small bubble.

The formula maps volume ratio (0.5× to 4×) linearly to the configured point range (default 6pt to 18pt). This means bigger bubbles = heavier institutional participation = higher conviction signal.

### Strong Signals (◉)

When a signal exceeds the "strong" thresholds (higher delta AND higher volume), the bubble switches from ● to ◉ (double ring). These are your 3-5 contract setups. On YM mode, strong signals require:

- Delta > 2.2× average (vs. 1.5× for standard)
- Volume > 1.8× average (vs. 1.0× for standard)

On Gold Rush mode:

- Delta > 2.8× average (vs. 2.0× for standard)
- Volume > 2.2× average (vs. 1.3× for standard)

### Tooltip Information

Hover over any bubble to see the full breakdown: signal type, delta value, volume, and volume ratio. This is your confirmation data before entering a trade.

---

## S/R Zone Engine

### Concept

Where exhaustion or absorption has occurred before, it tends to occur again. Institutional participants defend the same price levels because their positions create liquidity clusters at those prices. By scanning available chart history for E/A events and clustering nearby ones, DeepFlow automatically identifies zones where passive orders have repeatedly absorbed aggressive orders.

### Algorithm

```
1. STORE: Every E/A event records (price, volume, delta, type, bar_index)
2. PRUNE: Events older than `History Lookback` bars are removed
3. CLUSTER: Every 5 bars, group events within `Cluster Distance × ATR`
   - Greedy nearest-neighbor from first unassigned event
   - Track event count, total volume, recency, and signal mix
4. FILTER: Only clusters with `Min Events` or more become zones
5. DRAW: Semi-transparent boxes at cluster boundaries
   - Mixed clusters (both EXH + ABS) → orange (strongest)
   - Exhaustion-only clusters → yellow
   - Absorption-only clusters → teal
   - More events → more opaque border
   - Strong signals → thicker border, tighter zone
6. CAP: Keep only the `Max Active Zones` strongest (by score)
7. EXTEND: Zones auto-extend rightward each bar
```

### Zone Colors

| Zone Type | Color | Meaning |
|---|---|---|
| Orange | `#FF9100` | Mixed E/A — both exhaustion AND absorption at this level. Strongest S/R. |
| Yellow | `#FFD600` | Exhaustion cluster — aggressive orders repeatedly died here. |
| Teal | `#00BFA5` | Absorption cluster — passive orders repeatedly won here. |

### How to Trade Zones

When price approaches a zone, watch for a new E/A signal at that level. A fresh exhaustion or absorption bubble at an existing zone is the highest-conviction setup the indicator produces — it means institutional defense at that level is active again, not just historical.

---

## Trading Modes

### YM Mode

Calibrated for YM (Dow Mini) and MYM (Micro Dow Mini). YM has lower liquidity than ES/NQ, which means exhaustion patterns form more cleanly and earlier. Less noise to filter through.

**Standard signals (1-2 MYM contracts):**

| Parameter | Value | Why |
|---|---|---|
| Exhaustion delta | 1.5× avg | Lower threshold catches early exhaustion |
| Exhaustion price factor | 0.45× ATR | Wider tolerance for "small" bars on YM |
| Exhaustion volume | 1.0× avg | No volume premium — YM volume is naturally thinner |
| Absorption delta | 1.3× avg | Sensitive to subtle absorption patterns |
| Absorption volume | 1.0× avg | Same reasoning |

**Strong signals (3-5 MYM contracts):**

| Parameter | Value |
|---|---|
| Delta threshold | 2.2× avg |
| Volume threshold | 1.8× avg |

**Trading workflow (YM Mode):**

```
1. Watch the 2H chart for E/A bubbles
2. Standard bubble → consider 1-2 MYM entries
3. Strong bubble (◉) at an existing S/R zone → 3-5 MYM entries
4. Drop to 15min/5min to time the entry precisely
5. Stop: beyond the wick where the bubble sits
6. Target: next S/R zone or recent swing
```

### Gold Rush Mode

Calibrated for high-liquidity markets: GC/MGC, SI, CL/MCL, NQ/MNQ, ES/MES. These markets are deep — aggressive orders can be massive, noise is higher, and fake-outs are common. Every signal must clear a higher bar.

**Standard signals:**

| Parameter | Value | Why |
|---|---|---|
| Exhaustion delta | 2.0× avg | Higher bar — need genuine delta excess |
| Exhaustion price factor | 0.35× ATR | Tighter — bar must be clearly compressed |
| Exhaustion volume | 1.3× avg | Volume premium — need above-average participation |
| Absorption delta | 1.8× avg | Higher bar for delta divergence |
| Absorption volume | 1.3× avg | Same volume premium |

**Strong signals:**

| Parameter | Value |
|---|---|
| Delta threshold | 2.8× avg |
| Volume threshold | 2.2× avg |

**Trading workflow (Gold Rush Mode):**

```
1. Watch the 2H or 4H chart for E/A bubbles
2. ONLY trade signals that appear at or near an existing S/R zone
3. Standard bubble at zone → consider entry with tight stop
4. Strong bubble (◉) at zone → full conviction entry
5. Drop to 15min/30min to confirm price reaction at the zone
6. Stop: beyond the zone boundary
7. Target: next zone or measured move
```

---

## Timeframe Strategy

### Execution Timeframes (where you trade)

All using 1S default resolution:

| Timeframe | Role | Intrabars (1S) | History | Signal Quality |
|---|---|---|---|---|
| **2H** | Primary execution | 7,200 | ~13 bars | Maximum precision per bar |
| 1H | Secondary execution | 3,600 | ~27 bars | Excellent precision, more history |
| 4H | Swing context | 14,400 | ~6 bars | Ultra-precise but very short history |

### Monitoring Timeframes (where you manage)

| Timeframe | Role | Intrabars (1S) | History |
|---|---|---|---|
| 5 min | Entry timing, stop management | 300 | ~333 bars |
| 15 min | Trade monitoring | 900 | ~111 bars |
| 30 min | Position management | 1,800 | ~55 bars |
| 45 min | Intermediate context | 2,700 | ~37 bars |

**Practical workflow:** Use the 2H chart for signal detection (13 bars of ultra-precise E/A data is enough to catch the current setup). Use 15min or 30min for monitoring (100+ bars of history lets the S/R zones build up properly). Use 5min for entry timing (333 bars = deep context with 300 intrabars per bar).

---

## Configuration Guide

### For YM / MYM

```
Mode: YM
Calc TF: 1S (default)
ATR Length: 14
Statistical Lookback: 20
Bubble Size: 6–18pt
Zone History: 300 bars (≈25 trading days on 2H)
Zone Cluster Distance: 0.5× ATR
Zone Min Events: 2
```

### For NQ / MNQ

```
Mode: Gold Rush
Calc TF: 1S (default)
ATR Length: 14
Statistical Lookback: 20
Zone Cluster Distance: 0.5× ATR
Zone Min Events: 2 (or 3 for fewer, stronger zones)
```

### For ES / MES

```
Mode: Gold Rush
Calc TF: 1S (default)
ATR Length: 14
Statistical Lookback: 20
Zone Cluster Distance: 0.4× ATR (ES has tighter structure)
Zone Min Events: 2
```

### For CL / MCL

```
Mode: Gold Rush
Calc TF: 1S (default)
ATR Length: 10 (CL is faster, shorter ATR is more responsive)
Statistical Lookback: 15 (CL regimes change quickly)
Zone Cluster Distance: 0.6× ATR (CL is volatile, wider clusters)
```

### For GC / MGC

```
Mode: Gold Rush
Calc TF: 1S (default)
ATR Length: 14
Statistical Lookback: 20
Zone Cluster Distance: 0.5× ATR
```

---

## Dashboard Reference

| Metric | What It Shows |
|---|---|
| **DF³** / Mode | Indicator name and active mode (YM or Gold Rush) |
| **Symbol** | Current instrument |
| **Δ Delta** | Current bar's buy − sell volume. Green = net buying, purple = net selling |
| **Buy\|Sell** | Percentage split of volume (e.g., 62% \| 38%) |
| **Vol Ratio** | Current bar volume as multiple of average. >2× is highlighted |
| **Signal** | Current bar's signal: EXH BUY, EXH SELL, ABS BULL, ABS BEAR, or — |
| **Engine** | Active resolution + intrabar count. TEAL = primary (1S/1T). YELLOW = 1min fallback. RED = Chaikin (broken). |
| **E/A Events** | Total stored events in the lookback window |
| **S/R Zones** | Number of active zones currently drawn |
| **ATR** | Current ATR value for reference |

★ prefix on signals indicates STRONG quality (3-5 contract setup).

---

## Alerts

| Alert | When It Fires | Urgency |
|---|---|---|
| Exhaustion — Buy Side | Standard buy exhaustion detected | Watch |
| Exhaustion — Sell Side | Standard sell exhaustion detected | Watch |
| Absorption — Bullish | Hidden demand under red candle | Watch |
| Absorption — Bearish | Hidden supply under green candle | Watch |
| ★ STRONG Exhaustion — Buy | Extreme buy exhaustion | Act |
| ★ STRONG Exhaustion — Sell | Extreme sell exhaustion | Act |
| ★ STRONG Absorption — Bull | Massive hidden demand | Act |
| ★ STRONG Absorption — Bear | Massive hidden supply | Act |
| ★ ANY Strong Signal | Any strong signal fires | Act |

"Watch" = evaluate context, check for zone confluence. "Act" = high probability setup, prepare entry.

---

## Important: TradingView Is Not Real Order Flow

This indicator exists within TradingView's limitations. Key realities:

1. **Intrabar classification is approximate.** The buy/sell split is estimated from price position within each 1-second bar (default), not from actual bid/ask tape data. At 1S resolution, accuracy is ~85-90% compared to true tick-level classification. At 1-minute fallback, ~75-85%. Sufficient for session-scale patterns (exhaustion, absorption) but not for scalping individual ticks.

2. **Every data point matters.** We treat each 1-second intrabar as potentially carrying enormous institutional volume. A single second on ES during a sweep can contain 5,000+ contracts. The statistical methods adapt thresholds to the instrument's normal volume profile.

3. **The engine tells you what it's using.** Check the dashboard "Engine" row. Teal = your primary resolution is active (1S or 1T). Yellow = fell back to 1-minute (check your data plan). Red = Chaikin formula (something is broken). You should always see teal on CME/CBOT futures with a second-level data plan.

4. **Historical vs. real-time divergence.** `request.security_lower_tf()` may produce different values on the current live bar vs. after it closes. Always confirm signals on closed bars.

5. **S/R zones are probabilistic, not deterministic.** A zone marks where E/A events have clustered historically. It does not guarantee price will react there again. Always combine with price action confirmation.

---

## Version History

| Version | Date | Changes |
|---|---|---|
| v1.0 | 2026-04 | Full suite with 6 modules. Required Premium. |
| v2.0 | 2026-04 | Intrabar engine rewrite. No Premium required. 6 modules. |
| v3.0 | 2026-04 | Stripped to E/A core. Volume bubbles in wicks. Auto S/R zones from E/A clusters. YM + Gold Rush modes. Locked calc TF to 1T/1S/1min (default 1S). Optimized for 2H execution. No candle coloring. |

---

*DeepFlow is not affiliated with DeepCharts® or Volumetrica Trading.*
