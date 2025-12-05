# YM Ultimate SNIPER v8 - Complete Documentation

## 🎯 WIN AT ALL COST EDITION
### FIXED: Scoring System + Solid Table + All Timeframes + Filtered Visuals
**TARGET: 3-7 High-Confluence Trades per Day**
**Philosophy: "Zones That Matter" + "See Inside The Candle"**

---

# 📋 QUICK START CHEATSHEET

## ⚡ 60-SECOND SETUP

### Step 1: Add to Chart
1. Open TradingView → Indicators → Pine Editor
2. Paste the v8 code → Save → Add to Chart
3. Use 5-minute chart for day trading

### Step 2: Verify Settings (YM Default)
```
TIER THRESHOLDS:
├── S-Tier: 50 points (institutional sweep)
├── A-Tier: 25 point# YM Ultimate SNIPER v8 - Complete Documentation

## 🎯 WIN AT ALL COST EDITION
### FIXED: Scoring System + Solid Table + All Timeframes + Filtered Visuals
**TARGET: 3-7 High-Confluence Trades per Day**
**Philosophy: "Zones That Matter" + "See Inside The Candle"**

---

# 📋 QUICK START CHEATSHEET

## ⚡ 60-SECOND SETUP

### Step 1: Add to Chart
1. Open TradingView → Indicators → Pine Editor
2. Paste the v8 code → Save → Add to Chart
3. Use 5-minute chart for day trading

### Step 2: Verify Settings (YM Default)
```
TIER THRESHOLDS:
├── S-Tier: 50 points (institutional sweep)
├── A-Tier: 25 points (strong momentum)
└── B-Tier: 12 points (quick scalp)

INTRABAR: 1-minute (most precise)
SESSIONS: NY Window (0930-1130) ← Primary focus
```

### Step 3: Look for These Signals
```
⚡GOD    = GOD MODE (9.0+ score) → TAKE IT NOW, full size
S🎯      = S-Tier HOLD → 2.5-3.5 R:R target
A🎯      = A-Tier SWING → 2.0-2.5 R:R target
B🎯      = B-Tier SCALP → 1.5-2.0 R:R target
Z        = Zone entry (no tier but quality zone)
LS↑/↓   = Liquidity Sweep (filtered for quality)
✕        = Absorption (filtered for quality)
```

---

# 🔥 THE SCORE SYSTEM (v8 REBUILT)

## How It Works Now

The score is **100% ADDITIVE** - no more gating. Every factor adds points:

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

**Max Raw Score: ~22 points → Normalized to 10**

## Score Classifications

| Score | Classification | Action | Size |
|-------|---------------|--------|------|
| **9.0-10** | ⚡ GOD MODE | TAKE IT NOW | Full position |
| **8.0-8.9** | ⭐ EXCELLENT | High priority | 75-100% size |
| **5.0-7.9** | 🟡 MEDIUM | Standard setup | 50-75% size |
| **<5.0** | ❌ NO SIGNAL | No trade | — |

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
└── Stop: 2 ticks below signal candle low

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

## Available Timeframes (v8 COMPLETE!)

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

### Automatic Validation (v8 NEW!)
The script now automatically detects invalid intrabar configurations:

**When Intrabar TF is INVALID:**
1. **Yellow warning label** appears on chart: "⚠️ INTRABAR TF INVALID"
2. **Table shows**: "IB Data: ⚠️ INVALID TF" with yellow background
3. **Alert available**: "⚠️ INTRABAR CONFIG ERROR"
4. **Score impact**: Intrabar points (up to 5) are NOT added

**Example - 2 Minute Chart:**
```
VALID selections:   1T, 5T, 10T, 25T, 50T, 100T (any tick)
                    1S, 5S, 10S, 15S, 30S (any second)
                    1 (1-minute only)

INVALID selections: 2, 3, 5, 10, 15... (2min or higher)
                    D, W, M (obviously)
```

| Your Chart | Valid Intrabar Options |
|------------|------------------------|
| **2 minute** | **1T-1000T, 1S-30S, 1 only** |
| 5 minute | 1T-1000T, 1S-30S, 1-4 min |
| 15 minute | 1T-1000T, 1S-30S, 1-10 min |
| 1 hour | 1T-1000T, 1S-30S, 1-45 min |
| 4 hour | 1T-1000T, 1S-30S, 1-180 min |
| Daily | All tick, seconds, minutes up to 240 |

---

# 🎨 VISUAL FILTERING (v8 NEW!)

## The Problem (v7)
Too many sweep and absorption markers cluttered the chart with low-quality signals.

## The Solution (v8)
**Quality filters** - only show sweeps/absorption that MATTER.

### Sweep Quality Score
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

### Absorption Quality Score
```
+1.5 = In FVG Zone
+1.5 = In Order Block
+1.0 = Tier signal present
+0.5 = In session
+0.5 = CVD confirmation
───────────────────
MIN NEEDED: 2.0 to show
```

### Settings
```
VISUAL FILTERS:
├── Only Show Quality Sweeps: ON (default)
├── Only Show Quality Absorption: ON (default)
├── Min Sweep Quality Score: 2.0
└── Min Absorption Quality Score: 2.0

Turn OFF filters to see ALL signals (not recommended)
```

---

# 📈 CVD IMPLEMENTATION (v8 FIXED)

## What Changed

### v7 Issues:
- CVD accumulated forever (overflow risk)
- Short slope calculation (only 3 bars)
- No session reset

### v8 Fixes:
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

# ✅ ENTRY CHECKLIST v8

## Quick Checklist (Print This!)

### For ANY Signal:
- [ ] Score ≥ 3.5 (signal shown)
- [ ] Session active (🟢 in table)
- [ ] Direction matches bias

### For MEDIUM+ Signal (Score 5.0+):
- [ ] Delta matches direction (✓ or better)
- [ ] CVD trending with signal
- [ ] Volume ≥ 1.5x average

### For EXCELLENT Signal (Score 7.0+):
All above PLUS:
- [ ] In FVG Zone OR Order Block
- [ ] Strong delta (✓✓) or extreme (🔥)
- [ ] IB Delta confirms direction

### For GOD MODE (Score 8.5+):
All above PLUS:
- [ ] Multiple structure confluence (FVG + OB)
- [ ] Absorption or sweep present
- [ ] IB Momentum strong (🔥)
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

---

# 🏆 GOLDEN RULES v8

> **"The score doesn't lie. Trust the math."**

> **"GOD MODE = Don't think, just execute."**

> **"Filtered visuals = Quality over quantity."**

> **"If intrabar conflicts, trust intrabar."**

> **"Session matters - trade when institutions trade."**

> **"Stack confluence - score higher = win more."**

> **"Leave every trade with money. Next setup is coming."**

---

# 📝 TRADE JOURNAL v8

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
├── IB Delta: ____% (BULL / BEAR / NEUTRAL)
├── IB Momentum: ____% (BULL / BEAR / MIXED)
├── CVD: 🔥 / ↑↓ / neutral
│
├── Result: +/- ___ pts ($_____)
└── Notes: _______________________

DAILY SUMMARY:
├── Total Trades: ___
├── GOD MODE signals: ___
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
| No signals appearing | Lower Min Score threshold |
| Too many signals | Raise Min Score threshold |
| Score always 0 | Check if candle is tiered (meets point threshold) |
| Sweeps not showing | Check quality filter settings or lower threshold |
| Table transparent | ❌ Fixed in v8 - table is now solid |
| CVD not making sense | Now resets at session open - cleaner readings |
| Wrong tier thresholds | Adjust for your instrument (see setup guide) |
| Tick TF not available | Requires TradingView Premium+ subscription |

---

# 📚 VERSION HISTORY

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

*© Alexandro Disla - YM Ultimate SNIPER v8*
*WIN AT ALL COST Edition | Trust The Score*
s (strong momentum)
└── B-Tier: 12 points (quick scalp)

INTRABAR: 1-minute (most precise)
SESSIONS: NY Window (0930-1130) ← Primary focus
```

### Step 3: Look for These Signals
```
⚡GOD    = GOD MODE (9.0+ score) → TAKE IT NOW, full size
S🎯      = S-Tier HOLD → 2.5-3.5 R:R target
A🎯      = A-Tier SWING → 2.0-2.5 R:R target
B🎯      = B-Tier SCALP → 1.5-2.0 R:R target
Z        = Zone entry (no tier but quality zone)
LS↑/↓   = Liquidity Sweep (filtered for quality)
✕        = Absorption (filtered for quality)
```

---

# 🔥 THE SCORE SYSTEM (v8 REBUILT)

## How It Works Now

The score is **100% ADDITIVE** - no more gating. Every factor adds points:

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

**Max Raw Score: ~22 points → Normalized to 10**

## Score Classifications

| Score | Classification | Action | Size |
|-------|---------------|--------|------|
| **9.0-10** | ⚡ GOD MODE | TAKE IT NOW | Full position |
| **8.0-8.9** | ⭐ EXCELLENT | High priority | 75-100% size |
| **5.0-7.9** | 🟡 MEDIUM | Standard setup | 50-75% size |
| **<5.0** | ❌ NO SIGNAL | No trade | — |

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
└── Stop: 2 ticks below signal candle low

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

## Available Timeframes (v8 COMPLETE!)

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

### Automatic Validation (v8 NEW!)
The script now automatically detects invalid intrabar configurations:

**When Intrabar TF is INVALID:**
1. **Yellow warning label** appears on chart: "⚠️ INTRABAR TF INVALID"
2. **Table shows**: "IB Data: ⚠️ INVALID TF" with yellow background
3. **Alert available**: "⚠️ INTRABAR CONFIG ERROR"
4. **Score impact**: Intrabar points (up to 5) are NOT added

**Example - 2 Minute Chart:**
```
VALID selections:   1T, 5T, 10T, 25T, 50T, 100T (any tick)
                    1S, 5S, 10S, 15S, 30S (any second)
                    1 (1-minute only)

INVALID selections: 2, 3, 5, 10, 15... (2min or higher)
                    D, W, M (obviously)
```

| Your Chart | Valid Intrabar Options |
|------------|------------------------|
| **2 minute** | **1T-1000T, 1S-30S, 1 only** |
| 5 minute | 1T-1000T, 1S-30S, 1-4 min |
| 15 minute | 1T-1000T, 1S-30S, 1-10 min |
| 1 hour | 1T-1000T, 1S-30S, 1-45 min |
| 4 hour | 1T-1000T, 1S-30S, 1-180 min |
| Daily | All tick, seconds, minutes up to 240 |

---

# 🎨 VISUAL FILTERING (v8 NEW!)

## The Problem (v7)
Too many sweep and absorption markers cluttered the chart with low-quality signals.

## The Solution (v8)
**Quality filters** - only show sweeps/absorption that MATTER.

### Sweep Quality Score
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

### Absorption Quality Score
```
+1.5 = In FVG Zone
+1.5 = In Order Block
+1.0 = Tier signal present
+0.5 = In session
+0.5 = CVD confirmation
───────────────────
MIN NEEDED: 2.0 to show
```

### Settings
```
VISUAL FILTERS:
├── Only Show Quality Sweeps: ON (default)
├── Only Show Quality Absorption: ON (default)
├── Min Sweep Quality Score: 2.0
└── Min Absorption Quality Score: 2.0

Turn OFF filters to see ALL signals (not recommended)
```

---

# 📈 CVD IMPLEMENTATION (v8 FIXED)

## What Changed

### v7 Issues:
- CVD accumulated forever (overflow risk)
- Short slope calculation (only 3 bars)
- No session reset

### v8 Fixes:
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

# ✅ ENTRY CHECKLIST v8

## Quick Checklist (Print This!)

### For ANY Signal:
- [ ] Score ≥ 3.5 (signal shown)
- [ ] Session active (🟢 in table)
- [ ] Direction matches bias

### For MEDIUM+ Signal (Score 5.0+):
- [ ] Delta matches direction (✓ or better)
- [ ] CVD trending with signal
- [ ] Volume ≥ 1.5x average

### For EXCELLENT Signal (Score 7.0+):
All above PLUS:
- [ ] In FVG Zone OR Order Block
- [ ] Strong delta (✓✓) or extreme (🔥)
- [ ] IB Delta confirms direction

### For GOD MODE (Score 8.5+):
All above PLUS:
- [ ] Multiple structure confluence (FVG + OB)
- [ ] Absorption or sweep present
- [ ] IB Momentum strong (🔥)
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

---

# 🏆 GOLDEN RULES v8

> **"The score doesn't lie. Trust the math."**

> **"GOD MODE = Don't think, just execute."**

> **"Filtered visuals = Quality over quantity."**

> **"If intrabar conflicts, trust intrabar."**

> **"Session matters - trade when institutions trade."**

> **"Stack confluence - score higher = win more."**

> **"Leave every trade with money. Next setup is coming."**

---

# 📝 TRADE JOURNAL v8

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
├── IB Delta: ____% (BULL / BEAR / NEUTRAL)
├── IB Momentum: ____% (BULL / BEAR / MIXED)
├── CVD: 🔥 / ↑↓ / neutral
│
├── Result: +/- ___ pts ($_____)
└── Notes: _______________________

DAILY SUMMARY:
├── Total Trades: ___
├── GOD MODE signals: ___
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
| No signals appearing | Lower Min Score threshold |
| Too many signals | Raise Min Score threshold |
| Score always 0 | Check if candle is tiered (meets point threshold) |
| Sweeps not showing | Check quality filter settings or lower threshold |
| Table transparent | ❌ Fixed in v8 - table is now solid |
| CVD not making sense | Now resets at session open - cleaner readings |
| Wrong tier thresholds | Adjust for your instrument (see setup guide) |
| Tick TF not available | Requires TradingView Premium+ subscription |

---

# 📚 VERSION HISTORY

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

*© Alexandro Disla - YM Ultimate SNIPER v8*
*WIN AT ALL COST Edition | Trust The Score*
