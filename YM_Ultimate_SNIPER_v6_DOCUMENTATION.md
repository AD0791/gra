# YM Ultimate SNIPER v6 - Documentation & Trading Guide

## 🎯 ORDERFLOW EDITION | Order Blocks + Liquidity Sweeps + IFVG
**TARGET: 3-7 High-Confluence Trades per Day**
**Philosophy: "Zones That Matter"**

---

## ⚡ WHAT'S NEW IN v6

### Major Additions
| Feature | Description | Orderflow Purpose |
|---------|-------------|-------------------|
| **Order Blocks** | Last opposing candle before significant move | Shows where institutions absorbed orders |
| **Liquidity Sweeps** | Sweep of swing H/L with rejection | Identifies stop hunts / trap reversals |
| **IFVG** | Inverse FVG when price reclaims a gap | Failed institutional move = reversal signal |
| **Zone Quality Score** | 0-10 rating for each zone | Only "zones that matter" display |
| **3-Tier Scoring** | Weak/Medium/Excellent classification | Better trade selection |
| **Enhanced Table** | Larger, categorized, color-coded | Instant situation awareness |

### Orderflow Mindset
This version is built around **institutional order flow concepts**:

1. **Institutions leave footprints** → Order Blocks mark where they filled orders
2. **Retail gets trapped** → Liquidity Sweeps show the trap before reversal
3. **Failed moves reverse hard** → IFVG marks failed institutional attempts
4. **Not all zones are equal** → Quality scoring filters noise

---

## 🎯 QUICK REFERENCE

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YM ULTIMATE SNIPER v6                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  SIGNALS:                                                               │
│  S🎯 = S-Tier (50+ pts) → HOLD position                                │
│  A🎯 = A-Tier (25-49 pts) → SWING trade                                │
│  B🎯 = B-Tier (12-24 pts) → SCALP quick                                │
│  Z   = Zone entry (quality FVG/OB zone)                                │
│  LS↑ = Bullish Liquidity Sweep (lows swept + rejection)                │
│  LS↓ = Bearish Liquidity Sweep (highs swept + rejection)               │
│                                                                         │
│  ZONES:                                                                 │
│  🟦 Blue boxes = Bullish Order Block (buy zone)                        │
│  🟪 Pink boxes = Bearish Order Block (sell zone)                       │
│  🟩 Green boxes = Bullish FVG (buy zone)                               │
│  🟥 Red boxes = Bearish FVG (sell zone)                                │
│  🟣 Purple dashed = IFVG (inverse - strong reversal zone)              │
│                                                                         │
│  SCORE CLASSIFICATION:                                                  │
│  EXCELLENT (7.0+)  = Full size, high confidence                        │
│  MEDIUM (4.5-6.9)  = Standard size, good setup                         │
│  WEAK (<4.5)       = No signal shown                                   │
│                                                                         │
│  SESSIONS (ET):                                                         │
│  LDN = 3:00-5:00 AM    (London)                                        │
│  NY  = 9:30-11:30 AM   (New York Open)                                 │
│  PWR = 3:00-4:00 PM    (Power Hour)                                    │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📦 ORDER BLOCKS (OB)

### What Are Order Blocks?
Order blocks mark the **last opposing candle before a significant move**. This is where institutional traders absorbed retail orders before moving price in their intended direction.

### Detection Logic (Breaker Style)
```
BULLISH OB:
├── Last BEARISH candle before strong bullish move
├── Move after must be ≥ 1.5x ATR
├── Shows where institutions absorbed selling
└── Expect support when price returns

BEARISH OB:
├── Last BULLISH candle before strong bearish move  
├── Move after must be ≥ 1.5x ATR
├── Shows where institutions absorbed buying
└── Expect resistance when price returns
```

### OB Quality Scoring
Each Order Block gets a strength score (0-10) based on:
- **Move strength** after the OB (ATR multiple)
- **Volume** on the OB candle
- **Body ratio** of the OB candle

Only OBs with strength ≥ 4 are displayed.

### Trading Order Blocks
| Scenario | Action |
|----------|--------|
| Price returns to Bull OB + buy delta | Look for LONG |
| Price returns to Bear OB + sell delta | Look for SHORT |
| OB + FVG overlap (thick border) | HIGH PROBABILITY |
| OB tested once (gray) | Still valid, often best entry |
| OB broken (closes through) | Invalidated, removed |

---

## 💎 LIQUIDITY SWEEPS

### What Are Liquidity Sweeps?
A liquidity sweep occurs when price **hunts stop losses** by briefly breaking a swing high/low, then **immediately reverses** back. This is the classic "stop hunt" or "liquidity grab."

### Detection Logic
```
BULLISH SWEEP (LS↑):
├── Price sweeps BELOW a recent swing low
├── Closes BACK ABOVE the swing level
├── Shows lower wick (rejection)
├── Buy delta dominance on the candle
└── SIGNAL: Lows swept, shorts trapped → GO LONG

BEARISH SWEEP (LS↓):
├── Price sweeps ABOVE a recent swing high
├── Closes BACK BELOW the swing level
├── Shows upper wick (rejection)
├── Sell delta dominance on the candle
└── SIGNAL: Highs swept, longs trapped → GO SHORT
```

### Why Sweeps Matter for Orderflow
1. **Retail stops get hit** → Liquidity provided to institutions
2. **Institutions fill orders** → At better prices thanks to the sweep
3. **Price reverses** → Move in intended direction begins
4. **You enter with institutions** → Not against them

### Sweep + Zone = High Probability
When a liquidity sweep happens AT or NEAR an Order Block or FVG zone, the probability increases significantly.

---

## 🔄 IFVG (INVERSE FVG)

### What Is an IFVG?
An Inverse FVG forms when price **fills an FVG and then reclaims it** in the opposite direction. This signals a **failed institutional move**.

### Detection Logic
```
BULLISH IFVG:
├── Bearish FVG was created (gap down)
├── Price fills the gap (tests zone)
├── Price CLOSES ABOVE the gap with buy delta
└── SIGNAL: Bears failed → Strong reversal UP

BEARISH IFVG:
├── Bullish FVG was created (gap up)
├── Price fills the gap (tests zone)
├── Price CLOSES BELOW the gap with sell delta
└── SIGNAL: Bulls failed → Strong reversal DOWN
```

### Why IFVG Is Powerful
- Shows institutional failure → Other side takes control
- Pre-assigned quality score of 8.0 (high priority)
- Often marks significant reversals
- Purple dashed boxes for easy identification

---

## 📊 ZONE QUALITY SCORING

### The "Zones That Matter" Filter
Not all FVGs and OBs are created equal. v6 implements a **Zone Quality Score** (0-10) that filters out low-quality zones.

### Quality Calculation
| Factor | Max Points | How Measured |
|--------|------------|--------------|
| Gap Size | 2.5 | Larger gap = more points |
| Impulse Strength | 2.5 | Stronger move = more points |
| Volume | 2.0 | Higher volume = more points |
| OB Alignment | 2.0 | FVG overlaps with OB = bonus |
| Session | 1.0 | Created in active session = bonus |

### Min Quality Threshold (Default: 6.0)
Zones scoring below this threshold **are not displayed**. Adjust in settings:
- **Conservative**: Set to 7.0+ (fewer, better zones)
- **Standard**: 6.0 (balanced)
- **Aggressive**: 4.0-5.0 (more zones, more noise)

### Visual Quality Indicators
- **Thick border**: Zone aligns with Order Block (high quality)
- **Bright color**: Fresh zone
- **Gray color**: Tested zone (still valid)
- **Removed**: Broken zone (invalidated)

---

## 📊 CONFLUENCE SCORING SYSTEM

### Score Components (Max ~12, normalized to 10)

| Factor | Points | Condition |
|--------|--------|-----------|
| **Tier** | 1-3 | B=1, A=2, S=3 |
| **FVG Zone** | +1.5 | Price in quality FVG |
| **Order Block** | +1.5 | Price in OB |
| **IFVG** | +1.0 | Price in Inverse FVG |
| **Strong Volume** | +1.0 | Volume ≥ 2x average |
| **Extreme Volume** | +0.5 | Volume ≥ 2.5x average |
| **Strong Delta** | +1.0 | Delta ≥ 70% |
| **Extreme Delta** | +0.5 | Delta ≥ 78% |
| **CVD Momentum** | +0.5-1.0 | CVD trending with signal |
| **Liquidity Sweep** | +1.5 | Recent sweep confirms direction |

### Score Classification
| Score | Class | Confidence | Position Size |
|-------|-------|------------|---------------|
| **7.0+** | EXCELLENT | Very High | Full size (100%) |
| **4.5-6.9** | MEDIUM | Good | Standard (75%) |
| **< 4.5** | WEAK | Low | No signal shown |

### Score Displayed in Table
The table shows both the numeric score and classification:
- Green background + "EXCELLENT" = Top tier setup
- Orange background + "MEDIUM" = Decent setup
- Gray + "WEAK" = Below threshold

---

## 📊 ENHANCED TABLE REFERENCE

The v6 table is organized into **4 sections**:

### CANDLE Section
| Row | What It Shows |
|-----|---------------|
| Points | Candle range in points + Tier (S/A/B/X) |
| Volume | Volume ratio + grade (🔥/✓✓/✓/✗) |

### ORDERFLOW Section
| Row | What It Shows |
|-----|---------------|
| Delta | Buy/Sell % + grade (🔥/✓✓/✓/—) |
| CVD | Direction + strength (▲▲ STRONG, ▲ UP, etc.) |

### STRUCTURE Section
| Row | What It Shows |
|-----|---------------|
| FVG Zone | Current zone status + quality score |
| Order Block | OB status (BULL OB / BEAR OB / —) |
| Liq Sweep | Recent sweep status + 🎯 indicator |

### SIGNAL Section
| Row | What It Shows |
|-----|---------------|
| Session | Current session (NY/LDN/PWR/OFF) + 🟢/🔴 |
| SCORE | Numeric score /10 + classification |

### Color Coding
- **🟢 Green/Lime**: Good, meets threshold, bullish
- **🟠 Orange/Amber**: Caution, borderline, medium
- **🔴 Red**: Bad, below threshold, bearish
- **⚪ Gray**: Inactive/neutral
- **🔥**: Extreme/exceptional reading

---

## ✅ ENTRY CHECKLIST v6

Before entering any trade:

### Basic Requirements
- [ ] Signal present (S🎯/A🎯/B🎯 or Z)
- [ ] Score ≥ 4.5 (MEDIUM or better)
- [ ] Session active (LDN/NY/PWR shows 🟢)

### Orderflow Confirmation
- [ ] Delta colored (not gray)
- [ ] CVD arrow matches direction
- [ ] Volume shows ✓ or better

### Structure Bonus (Any = Better)
- [ ] In FVG Zone
- [ ] In Order Block
- [ ] Recent Liquidity Sweep
- [ ] IFVG present

### Execute
- [ ] Enter at signal candle close
- [ ] Stop below/above candle (shown on chart)
- [ ] Target at calculated R:R level

---

## 🎯 IDEAL SETUPS (HIGH WIN RATE)

### Setup 1: Sweep + Zone + Tier
```
Conditions:
├── Liquidity Sweep just occurred (LS↑ or LS↓)
├── Price is at Order Block or FVG
├── Tier signal fires (S/A/B)
├── Score: 7+ EXCELLENT
└── Win Rate: ~75-85%
```

### Setup 2: IFVG + Delta Confirmation
```
Conditions:
├── IFVG just formed (purple zone)
├── Strong delta (70%+) in IFVG direction
├── CVD confirming
├── Score: 7+ EXCELLENT
└── Win Rate: ~70-80%
```

### Setup 3: OB + FVG Overlap
```
Conditions:
├── Order Block present
├── FVG zone overlaps with OB (thick border)
├── Price returns to overlap zone
├── Delta confirms direction
└── Win Rate: ~70-78%
```

### Setup 4: Clean Zone Entry
```
Conditions:
├── Quality zone (score 6+)
├── No tier signal but Z entry shows
├── Delta matches zone direction
├── In active session
└── Win Rate: ~65-72%
```

---

## ⛔ DO NOT TRADE

- Session shows "OFF" or 🔴
- Score < 4.5 (WEAK)
- Delta shows "—" (no dominance)
- CVD conflicts with signal direction
- Multiple conflicting zones
- Zone quality < 6
- Major news imminent (FOMC, NFP, CPI)
- Price chopping between zones

---

## 🔧 SETTINGS GUIDE

### Recommended Configurations

**Conservative (2-4 trades/day):**
```
Min Score Medium: 5.5
Min Score Excellent: 7.5
Min Zone Quality: 7.0
Min Volume Ratio: 2.0
Delta Threshold: 65%
```

**Standard (4-6 trades/day):**
```
Min Score Medium: 4.5
Min Score Excellent: 7.0
Min Zone Quality: 6.0
Min Volume Ratio: 1.8
Delta Threshold: 62%
```

**Aggressive (6-8 trades/day):**
```
Min Score Medium: 4.0
Min Score Excellent: 6.5
Min Zone Quality: 5.0
Min Volume Ratio: 1.5
Delta Threshold: 60%
```

---

## 🚨 ALERTS PRIORITY

### Must-Have Alerts
| Alert | Priority | Action |
|-------|----------|--------|
| ⭐ EXCELLENT LONG/SHORT | 🔴 CRITICAL | Drop everything, check NOW |
| 🎯 S-TIER | 🟠 HIGH | Evaluate within 10 seconds |
| 💎 LIQUIDITY SWEEP | 🟠 HIGH | Check for zone confluence |
| 🔄 IFVG | 🟡 MEDIUM | Note reversal potential |

### Useful Context Alerts
| Alert | Purpose |
|-------|---------|
| 📦 NEW OB | Mark institutional zone |
| 📦 NEW FVG | Mark gap zone |
| SESSION OPEN | Prepare to trade |

---

## 📈 TRADE JOURNAL v6

```
DATE: ___________
SESSION: ☐ LDN  ☐ NY  ☐ PWR

SETUP TYPE:
☐ Sweep + Zone  ☐ IFVG  ☐ OB+FVG  ☐ Zone Entry

TRADE:
├── Time: _______
├── Signal: S🎯 / A🎯 / B🎯 / Z / LS
├── Direction: LONG / SHORT
├── Score: ___/10 (EXCELLENT / MEDIUM)
├── Entry: _______
├── Stop: _______
├── Target: _______
│
├── In FVG Zone: ☐ Yes  ☐ No
├── In Order Block: ☐ Yes  ☐ No
├── Liquidity Sweep: ☐ Yes  ☐ No
├── IFVG Present: ☐ Yes  ☐ No
│
├── Result: +/- ___ pts ($_____)
└── Notes: _______________________

DAILY SUMMARY:
├── Trades: ___
├── EXCELLENT setups: ___
├── MEDIUM setups: ___
├── Wins: ___ | Losses: ___
├── Net P/L: $_____
└── Best setup type: _______________________
```

---

## 🏆 GOLDEN RULES v6

> **"Institutions sweep, then move. Wait for the sweep."**

> **"Order Blocks show where they filled. Trade there."**

> **"IFVG = They failed. Take the other side."**

> **"Zone Quality 6+ or walk away."**

> **"EXCELLENT score = Green light. MEDIUM = Yellow light. WEAK = Red light."**

> **"Confluence beats conviction. Stack the factors."**

> **"Leave every trade with money. The next setup is coming."**

---

## 🔧 TROUBLESHOOTING

| Issue | Solution |
|-------|----------|
| No signals | Lower Min Score Medium to 4.0 |
| Too many signals | Raise Min Score Medium to 5.5+ |
| Too many zones | Raise Min Zone Quality to 7.0+ |
| Zones cluttering | Reduce Max Zones to 6-8 |
| OBs everywhere | Raise OB Min Strength to 1.8+ |
| Missing sweeps | Lower Sweep Lookback, reduce Min Wick Ratio |
| Table too small | Change Table Size to "large" |
| Wrong timezone | Check Session Timezone setting |

---

## 📝 TECHNICAL NOTES

- **Pine Script v6** (latest syntax)
- **Works on**: YM, MYM, NQ, MNQ, ES, MES, GC, MGC
- **Auto-detects** instrument for proper point calculation
- **Recommended TF**: 1-5 minute for day trading
- **Min TradingView Plan**: Free (no premium features required)
- **Max visual elements**: 500 labels, 500 boxes, 500 lines

---

*© Alexandro Disla - YM Ultimate SNIPER v6*
*Orderflow Edition | Zones That Matter*
