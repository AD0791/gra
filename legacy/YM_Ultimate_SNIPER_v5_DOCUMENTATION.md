# YM Ultimate SNIPER v5 - Documentation & Trading Guide

## 🎯 Unified GRA + DeepFlow | YM/MYM Optimized
**TARGET: 3-7 High-Confluence Trades per Day**

---

## ⚡ QUICK START

```
┌─────────────────────────────────────────────────────────────────┐
│                  YM ULTIMATE SNIPER v5                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  SIGNALS:                                                       │
│  S🎯 = S-Tier (50+ pts) → HOLD position                        │
│  A🎯 = A-Tier (25-49 pts) → SWING trade                        │
│  B🎯 = B-Tier (12-24 pts) → SCALP quick                        │
│  Z  = Zone entry (price at FVG zone)                           │
│                                                                 │
│  SESSIONS (ET):                                                 │
│  LDN = 3:00-5:00 AM    (London)                                │
│  NY  = 9:30-11:30 AM   (New York Open)                         │
│  PWR = 3:00-4:00 PM    (Power Hour)                            │
│                                                                 │
│  COLORS:                                                        │
│  🟩 Green zones = Bullish FVG (buy zone)                       │
│  🟥 Red zones = Bearish FVG (sell zone)                        │
│  🟣 Purple lines = Single prints (S/R levels)                  │
│                                                                 │
│  TABLE (Top Right):                                             │
│  Pts   = Candle point range                                    │
│  Tier  = S/A/B/X classification                                │
│  Vol   = Volume ratio (green = good)                           │
│  Delta = Buy/Sell dominance                                    │
│  Sess  = Current session                                       │
│  Zone  = In FVG zone status                                    │
│  Score = Confluence score /10                                  │
│  CVD   = Cumulative delta direction                            │
│  R:R   = Risk:Reward ratio                                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 VERSION 5 CHANGES

### What's New
- **Removed all imbalance code** - caused compilation errors
- **Simplified delta analysis** - uses candle structure instead of intrabar data
- **Cleaner confluence scoring** - 5 clear factors, max 10 points
- **Reliable table** - updates on last bar only, no flickering
- **Works on YM and MYM** - same logic applies to micro contracts

### Removed Features
- Candle-anchored imbalance markers
- Imbalance S/R zones
- Intrabar volume profile analysis
- POC visualization

### Kept & Improved
- Tier classification (S/A/B)
- FVG zone detection & visualization
- Single print detection
- Session windows with backgrounds
- Confluence scoring
- Stop/Target auto-calculation
- All alerts

---

## 🎯 SIGNAL TYPES

### Tier Signals (S🎯, A🎯, B🎯)

These are high-confluence signals that pass all filters:

| Tier | Points | Value/Contract | Action | Hold Time |
|------|--------|----------------|--------|-----------|
| **S** | 50+ | $250+ | HOLD | 2-5 min |
| **A** | 25-49 | $125-245 | SWING | 1-3 min |
| **B** | 12-24 | $60-120 | SCALP | 30-90 sec |

**Filters Required:**
1. Tier threshold met (points)
2. Volume ≥ 1.8x average
3. Delta dominance ≥ 62%
4. Body ratio ≥ 70%
5. Range ≥ 1.3x average
6. Proper wicks (no reversal wicks)
7. CVD confirmation (optional)
8. In trading session

### Zone Signals (Z)

Zone entries trigger when:
- Price is inside an FVG zone
- Delta shows dominance in zone direction
- Volume is above average
- In active session
- No tier signal already present

---

## 📊 CONFLUENCE SCORING

**Maximum Score: 10 points**

| Factor | Points | Condition |
|--------|--------|-----------|
| Tier | 1-3 | B=1, A=2, S=3 |
| In Zone | +2 | Price inside FVG zone |
| Strong Volume | +2 | Volume ≥ 2x average |
| Strong Delta | +2 | Delta ≥ 70% |
| CVD Momentum | +1 | CVD trending with signal |

**Score Interpretation:**
- **7-10**: Elite setup - full size
- **5-6**: Good setup - standard size
- **4**: Minimum threshold - reduced size
- **< 4**: No signal shown

---

## ⏰ SESSION WINDOWS

### London (3:00-5:00 AM ET)
- European institutional flow
- Character: Slow build-up, clean trends
- Expected trades: 1-2
- Best for: Zone entries, A/B tier

### NY Open (9:30-11:30 AM ET)
- Highest volume, most institutional activity
- Character: Initial balance, breakouts
- Expected trades: 2-3
- Best for: S/A tier, zone confluence

### Power Hour (3:00-4:00 PM ET)
- End-of-day rebalancing, MOC orders
- Character: Mean reversion or trend acceleration
- Expected trades: 1-2
- Best for: Zone entries, B tier scalps

---

## 🟩 FVG ZONES

### What Are FVG Zones?
Fair Value Gaps (FVGs) are price gaps between candles where price moved so fast that a gap was left. These gaps often act as support/resistance.

### Zone Requirements
- Gap size ≥ 25% of ATR
- Impulse candle has strong body (≥ 70%)
- Impulse candle is 1.5x average range
- Volume above average on impulse
- Created during active session

### Zone States
1. **Fresh** (bright color) - Just created, untested
2. **Tested** (gray) - Price touched zone midpoint
3. **Broken** (removed) - Price closed through zone

### Trading FVG Zones
| Zone | Approach From | Expected |
|------|--------------|----------|
| 🟩 Bull | Above (falling) | Support - look for bounce |
| 🟥 Bear | Below (rising) | Resistance - look for rejection |

---

## 🟣 SINGLE PRINTS

Single prints mark candles with:
- Range > 1.3x average
- Body > 70% of range
- Volume > 1.8x average
- Clear delta dominance

These become horizontal support/resistance lines extending into the future.

---

## 📊 TABLE REFERENCE

| Row | Label | Meaning |
|-----|-------|---------|
| 1 | Pts | Current candle point range |
| 2 | Tier | S/A/B/X classification |
| 3 | Vol | Volume ratio vs 20-bar average |
| 4 | Delta | Buy/Sell percentage dominance |
| 5 | Sess | Current session (LDN/NY/PWR/OFF) |
| 6 | Zone | In FVG zone (BULL/BEAR/---) |
| 7 | Score | Confluence score out of 10 |
| 8 | CVD | Delta momentum direction |
| 9 | R:R | Risk:Reward if signal active |

### Color Coding
- **Green/Lime**: Good, meets threshold
- **Yellow**: Caution, borderline
- **Red**: Bad, below threshold
- **Gray**: Inactive/neutral

---

## 🔧 SETTINGS GUIDE

### Tier Thresholds
| Setting | Default | Notes |
|---------|---------|-------|
| S-Tier | 50 pts | ~$250/contract |
| A-Tier | 25 pts | ~$125/contract |
| B-Tier | 12 pts | ~$60/contract |

### Sniper Filters
| Setting | Default | Notes |
|---------|---------|-------|
| Min Volume Ratio | 1.8x | Lower = more signals |
| Delta Dominance | 62% | Lower = more signals |
| Body Ratio | 70% | Higher = fewer, cleaner |
| Range Multiplier | 1.3x | Higher = fewer, bigger moves |
| CVD Confirm | On | Off = more signals |

### Recommended Configurations

**Conservative (3-4 trades/day):**
```
Min Confluence: 6
Volume Ratio: 2.0
Delta Threshold: 65%
Body Ratio: 75%
```

**Standard (5-7 trades/day):**
```
Min Confluence: 4
Volume Ratio: 1.8
Delta Threshold: 62%
Body Ratio: 70%
```

**Aggressive (7-10 trades/day):**
```
Min Confluence: 3
Volume Ratio: 1.5
Delta Threshold: 60%
Body Ratio: 65%
```

---

## ✓ ENTRY CHECKLIST

Before entering any trade:

1. ☐ Signal present (S🎯, A🎯, B🎯, or Z)
2. ☐ Session active (LDN, NY, or PWR)
3. ☐ Score ≥ 4 (preferably 6+)
4. ☐ Vol shows GREEN
5. ☐ Delta colored (not gray)
6. ☐ CVD arrow matches direction
7. ☐ Note stop/target lines
8. ☐ Execute at signal candle close

---

## ⛔ DO NOT TRADE

- Session shows "OFF"
- Score < 4
- Vol shows RED
- Delta gray (no dominance)
- Multiple conflicting signals
- Major news imminent (FOMC, NFP, CPI)
- Overnight session (11:30 PM - 3:00 AM ET)

---

## 🎯 POSITION SIZING

| Tier | Score | Size | Stop |
|------|-------|------|------|
| S (50+ pts) | 7+ | 100% | Below/above candle |
| A (25-49 pts) | 5-6 | 75% | Below/above candle |
| B (12-24 pts) | 4 | 50% | Below/above candle |
| Zone | Any | 50% | Beyond zone |

---

## 🚨 ALERTS

### Priority Alerts (Set These)
| Alert | Action |
|-------|--------|
| 🎯 S-TIER | Drop everything, check immediately |
| 🎯 A-TIER | Evaluate within 15 seconds |
| 🎯 B-TIER | Check if available |
| 🎯 ZONE | Good context entry |

### Info Alerts (Optional)
| Alert | Purpose |
|-------|---------|
| NEW BULL/BEAR FVG | Mark zones on mental map |
| SINGLE PRINT | Note for future S/R |
| SESSION OPEN | Prepare to trade |

---

## 📈 TRADE JOURNAL

```
DATE: ___________
SESSION: ☐ LDN  ☐ NY  ☐ PWR

TRADE:
├── Time: _______
├── Signal: S🎯 / A🎯 / B🎯 / Z
├── Direction: LONG / SHORT
├── Score: ___/10
├── Entry: _______
├── Stop: _______
├── Target: _______
├── In Zone: ☐ Yes  ☐ No
├── Result: +/- ___ pts ($_____)
└── Notes: _______________________

DAILY:
├── Trades: ___
├── Wins: ___ | Losses: ___
├── Net P/L: $_____
└── Best setup: _______________________
```

---

## 🏆 GOLDEN RULES

> **"Wait for the session. Off-hours = noise."**

> **"Score 6+ is your edge. Anything less is gambling."**

> **"Zone + Tier = bread and butter combo."**

> **"One great trade beats five forced trades."**

> **"Leave every trade with money. YM gives you time."**

---

## 🔧 TROUBLESHOOTING

| Issue | Solution |
|-------|----------|
| No signals | Lower min score to 3-4 |
| Too many signals | Raise min score to 6+ |
| Zones cluttering | Reduce max zones to 8 |
| Missing sessions | Check timezone setting |
| Table not updating | Resize chart or refresh |

---

## 📝 TECHNICAL NOTES

- **Pine Script v6**
- **Works on**: YM, MYM, any Dow futures
- **Recommended TF**: 1-5 minute for day trading
- **Min TradingView Plan**: Free (no intrabar data required)

---

*© Alexandro Disla - YM Ultimate SNIPER v5*
*Clean Build | Proven Components Only*
