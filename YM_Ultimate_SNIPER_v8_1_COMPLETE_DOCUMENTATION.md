# YM Ultimate SNIPER v8.1 - Complete Documentation

## 🎯 SNIPER STRICT EDITION
### "Fat Candles Only - Show Me Who Won"
**TARGET: 3-7 High-Confluence Trades per Day**
**Philosophy: "Zones That Matter" + "See Inside The Candle" + "Leave Every Trade With Money"**

---

# 📋 QUICK START CHEATSHEET

## ⚡ 60-SECOND SETUP

### Step 1: Add to Chart
1. Open TradingView → Indicators → Pine Editor
2. Paste the v8.1 code → Save → Add to Chart
3. Use 5-minute chart for day trading

### Step 2: Verify Settings (YM Default)
```
TIER THRESHOLDS:
├── S-Tier: 50 points (institutional sweep)
├── A-Tier: 25 points (strong momentum)
└── B-Tier: 12 points (quick scalp)

GOD MODE GATES (v8.1 NEW):
├── Min Body Ratio: 70%
├── Max Adverse Wick: 20%
├── Min Delta Dominance: 70%
├── Require Session: ON
└── Require Volume: ON

INTRABAR: 1-minute (most precise)
SESSIONS: NY Window (0930-1130) ← Primary focus
SIGNAL DISPLAY: Last 30 bars only
```

### Step 3: Look for These Signals
```
⚡GOD    = GOD MODE (passed ALL 6 gates) → TAKE IT NOW, full size
S🎯      = S-Tier HOLD → 2.5-3.5 R:R target
A🎯      = A-Tier SWING → 2.0-2.5 R:R target
B🎯      = B-Tier SCALP → 1.5-2.0 R:R target
Z        = Zone entry (no tier but quality zone)
LS↑/↓   = Liquidity Sweep (filtered for quality)
✕        = Absorption (filtered for quality)
```

---

# 🔥 v8.1 NEW: STRICT GOD MODE SYSTEM

## The Problem We Fixed
**GOD MODE was handing out awards like participation trophies.** Too many wicky, indecisive candles were getting GOD MODE status just because they had enough confluence points. A GOD MODE candle should show **CLEAR DOMINANCE** - fat body, minimal adverse wick, consistent pressure throughout formation.

## The 6 Gates of GOD MODE

**Score alone no longer qualifies for GOD MODE.** Now a candle must pass ALL 6 gates:

| Gate | What It Checks | Requirement | Default |
|------|----------------|-------------|---------|
| **1. Score** | Confluence threshold | Must meet minimum | ≥9.0 |
| **2. Body** | Fat candle requirement | Body ratio must be "fat" | ≥70% |
| **3. Adverse Wick** | Minimal pushback | Wick against direction | ≤20% |
| **4. Delta** | One side dominated | Buy/sell dominance | ≥70% |
| **5. Session** | Institutional participation | Active trading window | LDN/NY/PWR |
| **6. Pressure** | Consistent through formation | Same side dominated early AND late | Consistent |

**If ANY gate fails, GOD MODE is DENIED** - even with a 10/10 score!

### Gate Failure Examples
```
Candle: 35 point move, score 9.2, BUT:
- Body only 55% of range (thin) → DENIED: WICK
- Upper wick 35% (buyers got pushed back hard) → DENIED: WICK
- Intrabar showed mixed pressure → DENIED: PRESSURE
```

## GOD MODE Denial Reasons (Shown in Table)
```
DENIAL REASONS:
├── "DENIED: WICK" = Adverse wick too large (>20%)
├── "DENIED: DELTA" = Delta dominance too weak (<70%)
├── "DENIED: SESSION" = Not in active session
├── "DENIED: VOLUME" = Volume below 1.5x
└── "DENIED: PRESSURE" = Mixed pressure during formation
```

---

# 📊 v8.1 NEW: CANDLE DOMINANCE INDEX (CDI)

The CDI quantifies **"who won the candle"** on a 0-10 scale:

## CDI Components
```
CDI CALCULATION:
├── Body Score (0-4 pts): How fat is the body?
│   └── currentBodyRatio × 5 (capped at 4)
├── Adverse Wick Score (0-3 pts): How small is the wick against direction?
│   └── (1 - adverseWickRatio) × 3
├── Favorable Wick Score (0-2 pts): Clean entry side?
│   └── <15% = 2pts, <25% = 1pt, else 0
└── Closing Strength (0-1 pt): Did it close near the extreme?
    └── Close position relative to range
```

## CDI Ratings
| CDI Score | Rating | Table Display | GOD MODE Worthy? |
|-----------|--------|---------------|------------------|
| **8.0+** | 🔥 DOMINANT | 🔥 | ✅ Yes |
| **6.0-7.9** | ✓✓ STRONG | ✓✓ | Maybe (check other gates) |
| **4.0-5.9** | ✓ ACCEPTABLE | ✓ | ❌ No |
| **<4.0** | WEAK | — | ❌ No |

## CDI Score Contribution to Confluence
```
CDI >= 8.0 → +1.5 points to raw score
CDI >= 6.0 → +0.75 points to raw score
CDI < 6.0  → +0 points
```

---

# 📈 v8.1 NEW: PRESSURE CONSISTENCY TRACKING

New intrabar analysis that tracks if the **same side dominated throughout the candle**:

## How It Works
```
CANDLE FORMATION ANALYSIS:
├── First Half: Who dominated? (earlyBuyVol vs earlySellVol)
├── Second Half: Who dominated? (lateBuyVol vs lateSellVol)
└── Consistent? = Same side won BOTH halves

PRESSURE CONSISTENT:
├── Buyers dominated early AND late
└── OR Sellers dominated early AND late

PRESSURE MIXED:
├── Buyers dominated early, sellers late
└── OR Sellers dominated early, buyers late
```

## Why It Matters
**Mixed pressure = possible fake-out candle.** Even if the final result looks bullish, if sellers dominated the first half and buyers only took over late, the move may not be sustainable.

**GOD MODE requires consistent pressure** when intrabar analysis is enabled.

---

# 🎨 v8.1 NEW: 30-BAR SIGNAL DISPLAY LIMIT

## The Problem
Past signals cluttered the chart, making it hard to focus on current action.

## The Solution
**Only the last 30 bars show tier markers, sweeps, and absorption signals.** This keeps the chart clean and focused on recent action.

```
WHAT'S HIDDEN AFTER 30 BARS:
├── Tier signals (S/A/B/Z)
├── GOD MODE markers
├── Liquidity sweep diamonds
├── Absorption crosses
└── Stop/Target lines

WHAT ALWAYS SHOWS:
├── FVG/IFVG zones (structural)
├── Order Blocks (structural)
├── Session markers (context)
└── Session background colors
```

**Configurable:** Change "Show Signals: Last N Bars" in settings (10-100)

---

# 🔥 THE SCORE SYSTEM (v8 REBUILT + v8.1 ENHANCED)

## How It Works

The score is **100% ADDITIVE** - no gating. Every factor adds points:

| Category | Factor | Points |
|----------|--------|--------|
| **TIER** | S-Tier | +3.0 |
| | A-Tier | +2.0 |
| | B-Tier | +1.0 |
| **ZONES** | In FVG Zone | +1.5 |
| | In Order Block | +1.5 |
| | In IFVG | +1.0 |
| **VOLUME** | Meets minimum (1.5x) | +0.5 |
| | Strong (2.0x) | +0.75 |
| | Extreme (2.5x) | +0.75 |
| **DELTA** | Buy/Sell dominant (60%+) | +1.0 |
| | Strong (70%+) | +0.5 |
| | Extreme (78%+) | +0.5 |
| **CVD** | Bullish/Bearish | +0.5 |
| | Strong momentum | +0.5 |
| | Extreme momentum | +0.5 |
| **CANDLE** | Strong body (60%+) | +0.5 |
| | Significant range (1.2x avg) | +0.5 |
| | Clean wicks | +0.5 |
| **v8.1: CDI** | CDI >= 8.0 | +1.5 |
| | CDI >= 6.0 | +0.75 |
| **SWEEP** | Recent sweep (within 3 bars) | +1.5 |
| | Current bar sweep | +0.5 |
| **SESSION** | In key session | +1.0 |
| **INTRABAR** | IB Delta dominant | +1.0 |
| | IB Delta strong | +0.5 |
| | IB Delta extreme | +0.5 |
| | IB Momentum confirmed | +0.5 |
| | IB Momentum strong | +0.5 |
| | Absorption detected | +1.0 |
| | Internal sweep | +0.5 |
| | Volume cluster (favorable) | +0.5 |
| | **v8.1: Pressure consistent** | +0.5 |

**Max Raw Score: ~24 points → Normalized to 10**

## Score Classifications

| Score | Classification | Action | Size |
|-------|---------------|--------|------|
| **9.0-10** | ⚡ GOD MODE* | TAKE IT NOW | Full position |
| **8.0-8.9** | ⭐ EXCELLENT | High priority | 75-100% size |
| **5.0-7.9** | 🟡 MEDIUM | Standard setup | 50-75% size |
| **<5.0** | ❌ NO SIGNAL | No trade | — |

*v8.1: GOD MODE requires passing ALL 6 gates, not just score!

---

# 📊 INSTRUMENT-SPECIFIC SETUP

## YM (Dow Jones Mini) - DEFAULT

```
TIER THRESHOLDS:
├── S-Tier: 50 points
├── A-Tier: 25 points
└── B-Tier: 12 points

TICK VALUE: 1.00 (1 tick = 1 point)
CONTRACT VALUE: $5 per point

RECOMMENDED:
├── Chart: 5-minute
├── Intrabar TF: 1 (1-minute) OR 100T (tick for Premium+)
├── Sessions: NY Open (9:30-11:30)
├── Stop: 2 ticks below signal candle low
└── Signal Display: 30 bars

v8.1 GOD MODE GATES (YM optimized):
├── Min Body: 70% (tighter than other instruments)
├── Max Adverse Wick: 20%
├── Min Delta: 70%
└── Pressure Consistency: Required

PRO TIP: Use 100T or 250T tick intrabar for true order flow
```

## NQ (Nasdaq Mini)

```
TIER THRESHOLDS:
├── S-Tier: 100 points
├── A-Tier: 50 points
└── B-Tier: 25 points

TICK VALUE: 0.25 (4 ticks = 1 point)
CONTRACT VALUE: $5 per point ($20 per tick)

RECOMMENDED:
├── Chart: 5-minute
├── Intrabar TF: 1 (1-minute)
├── Min Volume Ratio: 1.8 (more volatile)
├── Delta Threshold: 0.62 (stricter)
└── Sessions: NY Open + Power Hour
```

## GC (Gold)

```
TIER THRESHOLDS:
├── S-Tier: 20 points (=$200)
├── A-Tier: 10 points (=$100)
└── B-Tier: 5 points (=$50)

TICK VALUE: 0.10 (10 ticks = 1 point)
CONTRACT VALUE: $10 per point ($1 per tick)

RECOMMENDED:
├── Chart: 5-minute
├── Intrabar TF: 1 (1-minute)
├── Sessions: London + NY overlap
├── Min Volume Ratio: 1.5
└── Note: More responsive to geopolitical events
```

## BTC (Bitcoin Futures)

```
TIER THRESHOLDS:
├── S-Tier: 500 points
├── A-Tier: 250 points
└── B-Tier: 100 points

TICK VALUE: 5.00 (1 tick = 5 points)
CONTRACT VALUE: $5 per point

RECOMMENDED:
├── Chart: 15-minute (less noise)
├── Intrabar TF: 5 (5-minute)
├── Sessions: Consider 24/7 (disable session filter)
├── Min Volume Ratio: 2.0 (crypto is spiky)
├── Absorption Threshold: 0.70 (stricter)
└── Note: Higher volatility, use wider stops
```

## ES (S&P 500 Mini)

```
TIER THRESHOLDS:
├── S-Tier: 20 points
├── A-Tier: 10 points
└── B-Tier: 5 points

TICK VALUE: 0.25 (4 ticks = 1 point)
CONTRACT VALUE: $12.50 per point ($50 per tick)

RECOMMENDED:
├── Chart: 5-minute
├── Intrabar TF: 1 (1-minute)
├── Sessions: NY Open (primary)
├── Note: Most liquid, cleanest price action
└── Good for learning the system
```

---

# 🕐 INTRABAR TIMEFRAME GUIDE

## Available Timeframes (COMPLETE!)

### TICK TIMEFRAMES (Premium+ Required)
| Timeframe | Code | Best For |
|-----------|------|----------|
| 1 Tick | 1T | **ULTIMATE PRECISION** - every single trade |
| 5 Ticks | 5T | Ultra-precise scalping |
| 10 Ticks | 10T | High-frequency analysis |
| 25 Ticks | 25T | Tick scalping |
| 50 Ticks | 50T | Short-term tick analysis |
| 100 Ticks | 100T | Standard tick analysis |
| 250 Ticks | 250T | Medium tick grouping |
| 500 Ticks | 500T | Larger tick grouping |
| 1000 Ticks | 1000T | High-level tick view |

### SECOND TIMEFRAMES
| Timeframe | Code | Best For |
|-----------|------|----------|
| 1 Second | 1S | Ultra-scalping |
| 5 Seconds | 5S | Scalping, high-frequency |
| 10 Seconds | 10S | Fast scalping |
| 15 Seconds | 15S | Quick scalps |
| 30 Seconds | 30S | Short-term scalps |

### MINUTE TIMEFRAMES
| Timeframe | Code | Best For |
|-----------|------|----------|
| 1 Minute | 1 | **RECOMMENDED** for 5m charts |
| 2 Minutes | 2 | 10m charts |
| 3 Minutes | 3 | 15m charts |
| 5 Minutes | 5 | 15-30m charts |
| 10 Minutes | 10 | 30m-1h charts |
| 15 Minutes | 15 | 1h charts |
| 30 Minutes | 30 | 1-2h charts |
| 45 Minutes | 45 | 2-4h charts |
| 1 Hour | 60 | 4h charts |
| 2 Hours | 120 | Daily charts |
| 3 Hours | 180 | Daily charts |
| 4 Hours | 240 | Weekly charts |

### HIGHER TIMEFRAMES
| Timeframe | Code | Best For |
|-----------|------|----------|
| Daily | D | Weekly/Monthly charts |
| Weekly | W | Monthly charts |
| Monthly | M | Long-term analysis |

## 🔥 TICK DATA ADVANTAGE

**Why Use Tick Data?**
- **True Order Flow**: See every single transaction
- **No Time Aggregation**: Pure price/volume action
- **Institutional Footprint**: Catch block trades instantly
- **Maximum IB Precision**: Most accurate delta/momentum
- **v8.1 Pressure Tracking**: More data points for consistency check

**Best Tick Settings by Instrument:**
| Instrument | Chart TF | Recommended Tick IB |
|------------|----------|---------------------|
| YM | 5 min | 100T or 250T |
| NQ | 5 min | 50T or 100T (more liquid) |
| ES | 5 min | 50T or 100T (most liquid) |
| GC | 5 min | 100T or 250T |
| BTC | 15 min | 250T or 500T |

## ⚠️ CRITICAL RULE
**Intrabar TF MUST be LOWER than your chart TF!**

### Automatic Validation
The script automatically detects invalid intrabar configurations:

**When Intrabar TF is INVALID:**
1. **Yellow warning label** appears on chart: "⚠️ INTRABAR TF INVALID"
2. **Table shows**: "IB Data: ⚠️ INVALID TF" with yellow background
3. **Alert available**: "⚠️ INTRABAR CONFIG ERROR"
4. **Score impact**: Intrabar points (up to 5.5) are NOT added

| Your Chart | Valid Intrabar Options |
|------------|------------------------|
| **2 minute** | **1T-1000T, 1S-30S, 1 only** |
| 5 minute | 1T-1000T, 1S-30S, 1-4 min |
| 15 minute | 1T-1000T, 1S-30S, 1-10 min |
| 1 hour | 1T-1000T, 1S-30S, 1-45 min |
| 4 hour | 1T-1000T, 1S-30S, 1-180 min |
| Daily | All tick, seconds, minutes up to 240 |

---

# 🎨 VISUAL FILTERING

## Sweep Quality Score
A sweep needs confluence to display:
```
+1.5 = In FVG Zone
+1.5 = In Order Block
+1.0 = Strong volume
+0.5 = In session
+1.0 = Intrabar confirmation
───────────────────
MIN NEEDED: 2.0 to show
```

## Absorption Quality Score
```
+1.5 = In FVG Zone
+1.5 = In Order Block
+1.0 = Tier signal present
+0.5 = In session
+0.5 = CVD confirmation
───────────────────
MIN NEEDED: 2.0 to show
```

## Settings
```
VISUAL FILTERS:
├── Only Show Quality Sweeps: ON (default)
├── Only Show Quality Absorption: ON (default)
├── Min Sweep Quality Score: 2.0
└── Min Absorption Quality Score: 2.0

v8.1 SIGNAL DISPLAY:
├── Show Signals: Last N Bars = 30
└── Show Historical FVG/OB Zones = ON
```

---

# 📈 CVD IMPLEMENTATION

## What Changed from v7

### v7 Issues:
- CVD accumulated forever (overflow risk)
- Short slope calculation (only 3 bars)
- No session reset

### v8+ Fixes:
```
1. SESSION RESET: CVD resets at London/NY open
2. PROPER SLOPE: Calculated over 5 bars
3. STDEV COMPARISON: Strong/Extreme = slope > 1-2 stdev
```

## CVD Readings in Table

| Display | Meaning | Score Contribution |
|---------|---------|-------------------|
| 🔥 BULL | Extreme bullish momentum | +1.5 total |
| 🔥 BEAR | Extreme bearish momentum | +1.5 total |
| ↑ BULL | Strong bullish trend | +1.0 total |
| ↓ BEAR | Strong bearish trend | +1.0 total |
| bull | Bullish bias | +0.5 |
| bear | Bearish bias | +0.5 |
| — | Neutral/mixed | +0 |

---

# 📊 TABLE SECTIONS (v8.1 UPDATED)

## ORDERFLOW Section
```
══ ORDERFLOW ══
Tier      | S-TIER    | 52.3 pts
Volume    | STRONG    | 2.1x
Delta     | BUY 73%   | 🔥
CVD       | ↑ BULL    | ✓
```

## CANDLE QUALITY Section (v8.1 NEW)
```
══ CANDLE QUALITY ══
Body      | 78%       | FAT
Adv Wick  | 12%       | CLEAN
CDI       | 8.2/10    | 🔥
```

## INTRABAR Section (v8.1 UPDATED)
```
══ INTRABAR ══
IB Data   | 12 bars   | ✓
IB Delta  | 74% BUY   | 🔥
Pressure  | CONSISTENT| ✓    ← v8.1 NEW
```

## STRUCTURE Section
```
══ STRUCTURE ══
FVG Zone  | BULL FVG  | 7.2
Order Block| BULL OB  | ✓
Liq Sweep | BULL LS↑  | 🎯
```

## SIGNAL Section
```
══ SIGNAL ══
Session   | NY        | 🟢
SCORE     | 9.4/10    | GOD MODE
                      | (or DENIED: WICK)
```

---

# ✅ ENTRY CHECKLIST v8.1

## Quick Checklist (Print This!)

### For ANY Signal:
- [ ] Score ≥ 5.0 (signal shown)
- [ ] Session active (🟢 in table)
- [ ] Direction matches bias

### For MEDIUM+ Signal (Score 5.0+):
- [ ] Delta matches direction (✓ or better)
- [ ] CVD trending with signal
- [ ] Volume ≥ 1.5x average

### For EXCELLENT Signal (Score 8.0+):
All above PLUS:
- [ ] In FVG Zone OR Order Block
- [ ] Strong delta (✓✓) or extreme (🔥)
- [ ] IB Delta confirms direction

### For GOD MODE (v8.1 STRICT):
All above PLUS:
- [ ] Score ≥ 9.0
- [ ] Body ratio ≥ 70% (FAT in table)
- [ ] Adverse wick ≤ 20% (CLEAN in table)
- [ ] CDI ≥ 8.0 (🔥 in table)
- [ ] Pressure CONSISTENT (not MIXED)
- [ ] **ALL 6 GATES PASSED**
- [ ] **FULL SIZE - DON'T HESITATE**

---

# ⛔ DO NOT TRADE

1. **Score below threshold** - No signal shown = no trade
2. **Outside session** - Unless you've disabled session filter
3. **Delta conflicts** - Bearish candle but buy dominant delta
4. **No intrabar data** - Shows "0 bars" in IB Data
5. **CVD strongly opposite** - 🔥 BEAR on a long signal
6. **After major news** - Wait for dust to settle
7. **Low volume overall** - Market too quiet
8. **v8.1: GOD MODE DENIED** - Don't force it, check the reason
9. **v8.1: Pressure MIXED** - High risk of reversal
10. **v8.1: Thin body (CDI < 6)** - Indecisive candle

---

# 🏆 GOLDEN RULES v8.1

> **"The score doesn't lie. Trust the math."**

> **"GOD MODE is EARNED, not given. Pass the gates."**

> **"Fat candles only. Thin = indecision = danger."**

> **"Filtered visuals = Quality over quantity."**

> **"If intrabar conflicts, trust intrabar."**

> **"Session matters - trade when institutions trade."**

> **"Consistent pressure = sustainable move."**

> **"Mixed pressure = possible trap."**

> **"Stack confluence - score higher = win more."**

> **"Leave every trade with money. Next setup is coming."**

---

# ⚙️ ALL SETTINGS REFERENCE

## TIER THRESHOLDS
```
S-Tier (Points)     = 50 (YM), 100 (NQ), 20 (GC/ES), 500 (BTC)
A-Tier (Points)     = 25 (YM), 50 (NQ), 10 (GC/ES), 250 (BTC)
B-Tier (Points)     = 12 (YM), 25 (NQ), 5 (GC/ES), 100 (BTC)
```

## SNIPER FILTERS
```
Min Volume Ratio       = 1.5
Delta Dominance %      = 0.60 (60%)
Min Body Ratio         = 0.60 (60%)
Min Range vs Avg       = 1.2
```

## CANDLE DOMINANCE (v8.1 NEW)
```
GOD MODE: Min Body Ratio       = 0.70 (70%)
GOD MODE: Max Adverse Wick     = 0.20 (20%)
GOD MODE: Min Delta Dominance  = 0.70 (70%)
GOD MODE: Min Intrabar Delta   = 0.68 (68%)
GOD MODE: Require Active Session = ON
GOD MODE: Require 1.5x+ Volume   = ON
```

## SIGNAL DISPLAY (v8.1 NEW)
```
Show Signals: Last N Bars      = 30
Show Historical FVG/OB Zones   = ON
```

## INTRABAR ANALYSIS
```
Enable Intrabar Analysis       = ON
Intrabar Timeframe             = 1 (or 100T for tick)
Absorption Detection %         = 0.65 (65%)
Min Intrabar Momentum          = 0.60 (60%)
Show Intrabar Metrics in Table = ON
Intrabar Delta Confluence Weight = 1.5
Absorption Confluence Weight     = 1.0
```

## VISUAL FILTERS
```
Only Show Quality Sweeps       = ON
Only Show Quality Absorption   = ON
Min Sweep Quality Score        = 2.0
Min Absorption Quality Score   = 2.0
```

## SESSION WINDOWS
```
Only Signal in Key Sessions    = ON
Timezone                       = America/New_York
London Window                  = 0300-0500
NY Open Window                 = 0930-1130
NY Power Hour                  = 1500-1600
Include Power Hour             = ON
```

## ORDER BLOCKS
```
Show Order Blocks              = ON
OB Lookback Bars               = 20
OB Min Move Strength (ATR)     = 1.5
Max Active Order Blocks        = 8
```

## LIQUIDITY SWEEPS
```
Show Liquidity Sweeps          = ON
Swing Lookback                 = 15
Min Sweep Wick Ratio           = 0.30 (30%)
Max Sweep Signal Age (bars)    = 3
```

## FVG & IFVG ZONES
```
Show FVG Zones                 = ON
Show IFVG (Inverse FVG)        = ON
Min Gap Size (ATR%)            = 0.25
Max Zone Age (bars)            = 75
Max Active Zones               = 10
Min Zone Quality Score         = 5.0
```

## CONFLUENCE SCORING
```
Min Score: Show Signal         = 5.0
Min Score: MEDIUM              = 5.0
Min Score: EXCELLENT           = 8.0
Min Score: GOD MODE            = 9.0
```

---

# 📝 TRADE JOURNAL v8.1

```
DATE: ___________
SESSION: ☐ LDN  ☐ NY  ☐ PWR
INSTRUMENT: YM / NQ / ES / GC / BTC

TRADE:
├── Time: _______
├── Signal: ⚡GOD / S🎯 / A🎯 / B🎯 / Z
├── Direction: LONG / SHORT
├── SCORE: ___/10
├── Classification: GOD MODE / EXCELLENT / MEDIUM / WEAK
│
├── Entry: _______
├── Stop: _______
├── Target: _______
│
├── In FVG Zone: ☐ Yes  ☐ No
├── In Order Block: ☐ Yes  ☐ No
├── Liquidity Sweep: ☐ Yes  ☐ No
├── Absorption: ☐ Yes  ☐ No
│
├── Body Ratio: ___% (FAT/OK/THIN)
├── Adverse Wick: ___% (CLEAN/OK/MESSY)
├── CDI: ___/10
│
├── IB Delta: ____% (BULL / BEAR / NEUTRAL)
├── IB Momentum: ____% (BULL / BEAR / MIXED)
├── Pressure: CONSISTENT / MIXED
├── CVD: 🔥 / ↑↓ / neutral
│
├── GOD MODE: ☐ Passed  ☐ Denied: _______
│
├── Result: +/- ___ pts ($_____)
└── Notes: _______________________

DAILY SUMMARY:
├── Total Trades: ___
├── GOD MODE signals: ___ (passed: ___, denied: ___)
├── EXCELLENT signals: ___
├── Win Rate: ___%
├── Net P/L: $_____
└── Best score today: ___
```

---

# 🔧 TROUBLESHOOTING

| Issue | Solution |
|-------|----------|
| **Yellow "INVALID TF" warning** | Your intrabar TF is >= chart TF. Select LOWER! |
| **IB Data shows "⚠️ INVALID TF"** | Same as above - pick 1T, 1S, or 1 for most charts |
| **Table row error** | Fixed in v8.1 - table rows increased to 22 |
| No signals appearing | Lower Min Score threshold |
| Too many signals | Raise Min Score threshold |
| Score always 0 | Check if candle is tiered (meets point threshold) |
| Sweeps not showing | Check quality filter settings or lower threshold |
| No GOD MODE despite high score | Check the DENIAL reason - a gate failed |
| GOD MODE "DENIED: WICK" | Candle has >20% adverse wick |
| GOD MODE "DENIED: PRESSURE" | Intrabar showed mixed pressure |
| Signals only on recent bars | v8.1 feature - configurable in settings |
| CVD not making sense | Resets at session open - cleaner readings |
| Wrong tier thresholds | Adjust for your instrument (see setup guide) |
| Tick TF not available | Requires TradingView Premium+ subscription |

---

# 📚 VERSION HISTORY

## v8.1 - SNIPER STRICT EDITION
- ✅ **STRICT GOD MODE** - 6 gates system (score alone not enough)
- ✅ **CANDLE DOMINANCE INDEX (CDI)** - "Who won the candle" 0-10 score
- ✅ **PRESSURE CONSISTENCY** - Track early vs late intrabar pressure
- ✅ **30-BAR SIGNAL LIMIT** - Clean chart, only recent signals shown
- ✅ **GOD MODE DENIAL REASONS** - Table shows WHY gates failed
- ✅ **ENHANCED TABLE** - New Candle Quality section with Body, Wick, CDI
- ✅ **FIXED TABLE ROWS** - No more row count errors

## v8 - WIN AT ALL COST EDITION
- ✅ REBUILT scoring system (100% additive, no gating)
- ✅ SOLID table (no transparency)
- ✅ ALL TradingView timeframes for intrabar (1S to Monthly)
- ✅ FILTERED sweeps/absorption (quality-based)
- ✅ FIXED CVD (session reset, proper slope)
- ✅ GOD MODE classification (8.5+ score)
- ✅ Instrument-specific documentation

## v7 - Intrabar Edition
- Added intrabar analysis engine
- Added absorption detection
- Added internal sweep detection

## Previous Versions
- GRA v5 SNIPER + DeepFlow Zones SNIPER merged

---

# 🎯 THE NEW GOD MODE STANDARD

A TRUE GOD MODE candle must show:

1. **HIGH SCORE** (≥9.0) - Multiple confluence factors aligned
2. **FAT BODY** (≥70%) - Clear directional commitment
3. **CLEAN WICKS** (≤20% adverse) - Minimal pushback
4. **STRONG DELTA** (≥70%) - One side clearly dominated
5. **IN SESSION** - Institutional participation
6. **CONSISTENT PRESSURE** - Same side controlled throughout

**Translation:** *"Institutions stepped in with size, pushed hard in one direction, and never let up. No hesitation, no give-back. This is a candle that means business."*

---

*© Alexandro Disla - YM Ultimate SNIPER v8.1*
*SNIPER STRICT EDITION | "Fat Candles Only"*
*Trust The Score. Pass The Gates. Win At All Cost.*
