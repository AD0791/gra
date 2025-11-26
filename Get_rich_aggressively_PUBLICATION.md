# Get_rich_aggressively - Professional Order Flow Indicator

## 📊 Overview

**Get_rich_aggressively (GRA)** is a professional-grade order flow indicator designed for futures and crypto traders who understand Auction Market Theory and want to identify high-probability setups with exceptional risk-to-reward ratios (3:1 to 5:1).

This indicator answers the two most critical questions in trading:
1. **Who is in control?** Bulls or Bears based on volume delta and aggression
2. **Where are traders trapped?** Identifying failed breakouts that lead to explosive moves

Built specifically for **NQ (Nasdaq 100 Futures)**, **GC (Gold Futures)**, and **BTC (Bitcoin)**, with optimized settings for each instrument's unique volatility profile.

---

## 🎯 Core Concepts

### Volume Delta & Imbalance
The indicator calculates **buying pressure vs selling pressure** within each candle using intrabar analysis. When one side significantly overpowers the other, an **imbalance** exists—these are the moments where price moves with conviction.

**Imbalance Ratio Interpretation:**
- `1.5:1` → Moderate imbalance (tradeable)
- `2.0:1` → Strong imbalance (high conviction)
- `3.0:1+` → Extreme imbalance (institutional activity)

### Aggression Detection
The indicator identifies which side is **aggressing** (hitting market orders) vs **absorbing** (resting limit orders). When aggressive buyers overwhelm sellers, price moves UP. When aggressive sellers overwhelm buyers, price moves DOWN.

### Trap Detection
**Bull Traps** and **Bear Traps** are failed breakouts where traders get caught on the wrong side. These setups often lead to explosive reversals as trapped traders are forced to exit.

---

## 🔧 How To Use

### Visual Elements

| Element | Meaning |
|---------|---------|
| **Green Bubbles** (below bar) | Bullish volume aggression - buyers winning |
| **Red Bubbles** (above bar) | Bearish volume aggression - sellers winning |
| **▲ Triangle Up** | Long signal (3:1 or 4:1+ R:R) |
| **▼ Triangle Down** | Short signal (3:1 or 4:1+ R:R) |
| **BT / BT!** | Bull Trap (short opportunity) |
| **BrT / BrT!** | Bear Trap (long opportunity) |
| **Diamond** | Absorption candle (institutional activity) |
| **Colored Candles** | Green = positive delta, Red = negative delta |

### Info Panel (Top Right)

| Field | Description |
|-------|-------------|
| **Delta** | Current bar's volume delta (buy - sell pressure) |
| **Vol** | Volume ratio vs 20-period average |
| **Imb** | Imbalance ratio (who's winning) |
| **Ctrl** | Who's in control: BULLS / BEARS |
| **CVD** | Cumulative Volume Delta for session |
| **Sess** | Current session (LDN! = London Open, NY! = NY Open) |
| **Mkt** | Market condition: CHOP / FV / IMB! / OK |
| **Sig** | Active signal if any |

### Signal Hierarchy

**High Conviction Signals (4:1+ R:R):**
- Displayed as `▲ 4:1+` or `▼ 4:1+`
- Require: Strong imbalance (2:1+) + Big volume (2.5x+) + Delta trend confirmation
- Best during London Open or NY Open sessions

**Standard Signals (3:1 R:R):**
- Displayed as `▲ 3:1` or `▼ 3:1`
- Require: Moderate imbalance (1.5:1+) + Volume spike (1.5x+)
- Good any time market is not choppy

**Trap Signals:**
- `BT!` = Strong Bull Trap → SHORT
- `BrT!` = Strong Bear Trap → LONG
- Occur at swing highs/lows with rejection wicks

---

## ⚙️ Recommended Settings by Instrument

### 📈 NQ (Nasdaq 100 E-mini Futures)

NQ is highly liquid with clear institutional footprints. The default settings work excellently.

```
═══════════ VOLUME ANALYSIS ═══════════
Volume MA Length: 20
Volume Spike Threshold: 1.5
Big Trade Threshold: 2.5
Extreme Volume Threshold: 4.0

═══════════ IMBALANCE DETECTION ═══════════
Imbalance Ratio Threshold: 1.5
Strong Imbalance Threshold: 2.0
Delta Confirmation Bars: 3
Fair Value Range (%): 0.3

═══════════ TRAP DETECTION ═══════════
Swing Lookback Period: 20
Minimum Wick Ratio: 0.4
Max Body Ratio (Absorption): 0.35

═══════════ SESSION SETTINGS ═══════════
Timezone: America/New_York
London Open Window: 0300-0500
NY Open Window: 0930-1130
Only Signal During Key Sessions: OFF (or ON for higher conviction)

═══════════ TIMEFRAME SETTINGS ═══════════
Analysis Timeframe: 1 (1-minute intrabar analysis)
Use Intrabar Analysis: ON
```

**Best Timeframes for NQ:**
- **1-minute**: Scalping, quick entries
- **5-minute**: Day trading (RECOMMENDED)
- **15-minute**: Swing entries within day

**NQ Trading Tips:**
- Most reliable signals occur during **9:30-11:30 AM EST** (NY Open)
- Watch for traps at **overnight high/low** levels
- Volume spikes of **3x+** often precede 10-20 point moves
- Avoid trading during **12:00-2:00 PM EST** (lunch chop)

---

### 🥇 GC (Gold Futures)

Gold has different volatility patterns. Increase thresholds slightly to filter noise.

```
═══════════ VOLUME ANALYSIS ═══════════
Volume MA Length: 20
Volume Spike Threshold: 1.8        ← Increased (gold has more noise)
Big Trade Threshold: 3.0           ← Increased
Extreme Volume Threshold: 5.0      ← Increased

═══════════ IMBALANCE DETECTION ═══════════
Imbalance Ratio Threshold: 1.6     ← Slightly higher
Strong Imbalance Threshold: 2.2    ← Slightly higher
Delta Confirmation Bars: 4         ← More confirmation needed
Fair Value Range (%): 0.4          ← Gold chops more

═══════════ TRAP DETECTION ═══════════
Swing Lookback Period: 25          ← Wider swings
Minimum Wick Ratio: 0.45           ← Bigger wicks needed
Max Body Ratio (Absorption): 0.30  ← Tighter for absorption

═══════════ SESSION SETTINGS ═══════════
Timezone: America/New_York
London Open Window: 0300-0500      ← Gold moves well here
NY Open Window: 0830-1030          ← Earlier due to economic news
Only Signal During Key Sessions: ON ← Recommended for GC

═══════════ TIMEFRAME SETTINGS ═══════════
Analysis Timeframe: 1
Use Intrabar Analysis: ON
```

**Best Timeframes for GC:**
- **5-minute**: Day trading (RECOMMENDED)
- **15-minute**: Position entries
- **1-hour**: Swing trading

**Gold Trading Tips:**
- Gold reacts strongly to **economic data releases** (8:30 AM EST)
- **London session** (3-5 AM EST) often sets the daily direction
- Watch for traps at **round numbers** ($2000, $2050, etc.)
- Gold respects **previous day high/low** as key levels
- Absorption candles near support/resistance signal reversals

---

### ₿ BTC (Bitcoin)

Bitcoin trades 24/7 with unique session dynamics. Adjust for higher volatility.

```
═══════════ VOLUME ANALYSIS ═══════════
Volume MA Length: 30               ← Longer average (24/7 market)
Volume Spike Threshold: 2.0        ← Higher threshold (crypto volatility)
Big Trade Threshold: 3.5           ← Higher for significance
Extreme Volume Threshold: 6.0      ← Much higher for crypto

═══════════ IMBALANCE DETECTION ═══════════
Imbalance Ratio Threshold: 1.7     ← Higher due to volatility
Strong Imbalance Threshold: 2.5    ← Higher for conviction
Delta Confirmation Bars: 3
Fair Value Range (%): 0.5          ← BTC ranges more

═══════════ TRAP DETECTION ═══════════
Swing Lookback Period: 30          ← Wider lookback
Minimum Wick Ratio: 0.5            ← BTC has massive wicks
Max Body Ratio (Absorption): 0.25  ← Tighter (many dojis in crypto)

═══════════ SESSION SETTINGS ═══════════
Timezone: America/New_York
London Open Window: 0300-0500      ← European session start
NY Open Window: 0930-1130          ← US session (big moves)
Only Signal During Key Sessions: OFF ← BTC moves 24/7

═══════════ TIMEFRAME SETTINGS ═══════════
Analysis Timeframe: 1
Use Intrabar Analysis: ON
```

**Best Timeframes for BTC:**
- **5-minute**: Active trading
- **15-minute**: Day trading (RECOMMENDED)
- **1-hour**: Swing trading
- **4-hour**: Position trading

**Bitcoin Trading Tips:**
- **US Session** (9:30 AM - 4:00 PM EST) has highest volume
- **Asian Session** (8 PM - 4 AM EST) often consolidates
- Watch for traps at **psychological levels** ($60K, $65K, $70K, etc.)
- **Funding rate flips** often coincide with trap signals
- Weekend volume is lower—signals less reliable

---

## 📋 Trading Playbook

### Setup 1: High Conviction Imbalance Entry

**Conditions:**
- ▲ or ▼ signal appears with "4:1+" label
- Info panel shows "Ctrl: BULLS" or "Ctrl: BEARS"
- Info panel shows "Mkt: IMB!"
- During active session (LDN! or NY!)

**Entry:** Market order on signal bar close
**Stop Loss:** Beyond the signal candle's wick
**Take Profit:** 4:1 risk-to-reward minimum

---

### Setup 2: Trap Reversal

**Conditions:**
- BT! (Bull Trap) or BrT! (Bear Trap) appears
- Signal occurs at swing high/low
- Volume spike confirms (2x+ average)

**Entry:** 
- Bull Trap → SHORT on close below signal bar
- Bear Trap → LONG on close above signal bar

**Stop Loss:** Beyond the trap wick
**Take Profit:** Previous swing level (3:1+ R:R typical)

---

### Setup 3: Absorption Reversal

**Conditions:**
- Diamond marker appears (absorption)
- At key support/resistance level
- Followed by opposite-colored candle with volume

**Entry:** On confirmation candle close
**Stop Loss:** Beyond absorption candle
**Take Profit:** 2:1 minimum

---

### Setup 4: Session Open Momentum

**Conditions:**
- "L" (London) or "N" (NY) session marker appears
- First 30 minutes show clear delta direction
- Imbalance ratio > 1.5:1

**Entry:** With the dominant delta direction
**Stop Loss:** Session open price
**Take Profit:** Previous day high/low or 3:1 R:R

---

## ⚠️ When NOT to Trade

Avoid taking signals when:

1. **Info panel shows "Mkt: CHOP"** - Market is ranging without conviction
2. **Info panel shows "Mkt: FV"** - Fair value zone, expect mean reversion
3. **Ctrl shows "---"** - Neither side in control
4. **During lunch hours** (12:00-2:00 PM EST for futures)
5. **Before major news** (FOMC, NFP, CPI)
6. **Low volume sessions** (holidays, weekends for futures)

---

## 🔔 Alerts Setup

The indicator includes pre-built alerts. To set them up:

1. Click the "Alerts" button (clock icon) in TradingView
2. Select "Get_rich_aggressively" as condition
3. Choose from available alerts:
   - **EXTREME LONG** - 4:1+ bullish setup
   - **EXTREME SHORT** - 4:1+ bearish setup
   - **HIGH CONV LONG** - 3:1 bullish setup
   - **HIGH CONV SHORT** - 3:1 bearish setup
   - **BULL TRAP** - Failed breakout, short opportunity
   - **BEAR TRAP** - Failed breakdown, long opportunity
   - **LONDON OPEN** - Session notification
   - **NY OPEN** - Session notification

---

## 📚 Understanding the Logic

### Volume Delta Calculation

The indicator uses **intrabar analysis** to calculate precise volume delta:

```
For each lower-timeframe bar within the current bar:
    Buy Pressure = ((Close - Low) / Range) × Volume
    Sell Pressure = ((High - Close) / Range) × Volume
    Delta = Buy Pressure - Sell Pressure

Total Delta = Sum of all intrabar deltas
```

This method is more accurate than simple "green candle = buying" logic because it captures the **internal auction** within each candle.

### Imbalance Ratio

```
Bullish Imbalance = Buy Pressure / Sell Pressure
Bearish Imbalance = Sell Pressure / Buy Pressure

If ratio ≥ 1.5 AND volume spike → Standard signal
If ratio ≥ 2.0 AND big volume → High conviction signal
```

### Trap Detection

```
Bull Trap = 
    Price breaks ABOVE swing high +
    Closes BACK BELOW swing high +
    Upper wick ≥ 40% of candle range +
    Volume spike present

Bear Trap = 
    Price breaks BELOW swing low +
    Closes BACK ABOVE swing low +
    Lower wick ≥ 40% of candle range +
    Volume spike present
```

---

## 💡 Pro Tips

1. **Combine with market structure** - Signals at key S/R levels are stronger
2. **Watch CVD divergence** - If CVD trends opposite to price, reversal likely
3. **Stack confluences** - Trap + Absorption + Session Open = highest probability
4. **Scale in** - Enter 50% on signal, add on confirmation
5. **Use session filter** - Enable "Only Signal During Key Sessions" for cleaner signals
6. **Check higher timeframe** - Ensure signal aligns with HTF trend/bias

---

## ⚠️ Disclaimer

This indicator is a tool to assist your trading decisions, not a guarantee of profits. Past performance does not indicate future results. Always:

- Use proper risk management (1-2% max per trade)
- Paper trade before going live
- Understand the instrument you're trading
- Never risk more than you can afford to lose

---

## 🔄 Version History

**v1.0** - Initial release
- Volume delta calculation with intrabar analysis
- Imbalance detection and signals
- Bull/Bear trap identification
- Absorption candle detection
- Session filtering (London/NY)
- Real-time info panel
- Comprehensive alert system

---

## 📬 Support

If you have questions or suggestions, leave a comment below or send me a message.

**Happy Trading! Let's Get Rich Aggressively! 🚀**

---

*This indicator is inspired by Auction Market Theory, Order Flow concepts, and professional tools like DeepCharts, Sierra Chart, and Bookmap. It brings institutional-grade analysis to TradingView.*
