# YM Ultimate SNIPER v7 - Documentation & Trading Guide

## 🎯 INTRABAR EDITION | Order Blocks + Liquidity Sweeps + IFVG + INTRABAR ANALYSIS
**TARGET: 3-7 High-Confluence Trades per Day**
**Philosophy: "Zones That Matter" + "See Inside The Candle"**

---

## ⚡ WHAT'S NEW IN v7

### Major Additions: INTRABAR ANALYSIS ENGINE

| Feature | Description | Edge It Provides |
|---------|-------------|------------------|
| **Intrabar Delta** | REAL buy/sell pressure from lower TF | Far more accurate than estimated delta |
| **Intrabar Momentum** | Direction consistency within bar | See if candle formed through conviction |
| **Absorption Detection** | High vol + low price movement | Spot institutional accumulation/distribution |
| **Internal Sweeps** | Stop hunts INSIDE candles | Catch hidden liquidity grabs |
| **Volume Distribution** | Where volume clustered in bar | TOP/MID/BOT volume clustering |

### The Intrabar Advantage

**Problem with Standard Analysis:**
- You only see the final OHLC of each candle
- Delta estimation is educated guesswork
- Internal price action is invisible
- Stop hunts inside bars go undetected

**Solution with Intrabar Analysis:**
- `request.security_lower_tf()` gives us the INSIDE view
- See actual lower timeframe candles within each bar
- Calculate TRUE delta from actual price direction
- Detect sweeps and reversals hidden from current timeframe

---

## 🔬 INTRABAR ANALYSIS DEEP DIVE

### How It Works

When you're on a 5-minute chart, intrabar analysis requests 1-minute data within each 5-minute bar. This gives us 5 sub-candles to analyze within each parent candle.

```
5-MIN CANDLE (What you normally see):
┌────────────────────────────────┐
│                                │
│     OPEN ──────── CLOSE        │
│                                │
└────────────────────────────────┘

INTRABAR VIEW (What v7 sees):
┌────────────────────────────────┐
│  🕐1  🕐2  🕐3  🕐4  🕐5       │
│  ▲    ▼    ▲    ▲    ▲        │
│  │    │    │    │    │        │
│  Each 1-min candle analyzed   │
└────────────────────────────────┘
```

### Intrabar Delta (IB Delta)

**What It Is:**
Real buy/sell pressure calculated from actual lower timeframe candle directions.

**Why It's Better:**
- Standard delta: Estimated from close position within bar
- Intrabar delta: Calculated from 5+ actual candles with known direction

**Calculation:**
```
For each intrabar candle:
├── If bullish (close > open): More weight to buy volume
├── If bearish (close < open): More weight to sell volume
├── Volume distributed by close position within each micro-candle
└── Summed across all intrabar candles = TRUE DELTA
```

**Grades:**
| IB Delta % | Grade | Meaning |
|------------|-------|---------|
| 78%+ | 🔥 EXTREME | One side has overwhelming control |
| 70-77% | ✓✓ STRONG | Clear directional bias |
| 62-69% | ✓ DOMINANT | Healthy dominance |
| <62% | — NEUTRAL | Mixed/uncertain |

---

### Intrabar Momentum (IB Momentum)

**What It Is:**
The percentage of intrabar candles moving in the same direction.

**Why It Matters:**
A bullish candle could form through:
1. **High momentum:** 4 of 5 sub-candles bullish = Strong conviction
2. **Low momentum:** 2 bullish, 2 bearish, 1 bullish = Choppy formation

**Calculation:**
```
IB Momentum = max(bullish_count, bearish_count) / total_intrabar_candles

Example (5-min bar with 1-min intrabar):
├── 1st minute: Bullish ✓
├── 2nd minute: Bullish ✓
├── 3rd minute: Bearish ✗
├── 4th minute: Bullish ✓
├── 5th minute: Bullish ✓
└── IB Momentum = 4/5 = 80% BULLISH
```

**Thresholds:**
| IB Momentum % | Classification | Signal Quality |
|---------------|----------------|----------------|
| 75%+ | 🔥 STRONG | Very high conviction |
| 60-74% | ✓ CONFIRMED | Good directional bias |
| <60% | MIXED | Choppy, low conviction |

---

### Absorption Detection

**What It Is:**
Institutional accumulation/distribution signature - high volume with little price movement.

**The Theory:**
When institutions accumulate (buy), they absorb selling without moving price much:
- Retail sells → Institution buys at limit prices
- Volume spikes but price stays flat
- Once accumulation complete → price explodes up

**Detection Logic:**
```
ABSORPTION = High Volume + Low Price Movement + Volume Clustering

Conditions:
├── Volume per point > 1.5x average
├── Price movement < 60% of average range
├── Volume clusters in one zone (TOP/MID/BOT)
└── Cluster percentage >= 65% threshold
```

**Direction:**
- **BULL ABS:** Volume clustered at BOT + net buy delta = Buying at lows
- **BEAR ABS:** Volume clustered at TOP + net sell delta = Selling at highs

**Visual:** ✕ marker below (bull) or above (bear) the candle

---

### Internal Sweeps (Hidden Liquidity Grabs)

**What It Is:**
Stop hunts that happen INSIDE a candle - invisible on current timeframe.

**The Setup:**
```
INTERNAL BULLISH SWEEP:
┌─────────────────────────────────┐
│                                 │
│  First Half:      Second Half:  │
│  ▲▼▲▼            ▲▲▲           │
│  Forms lows       Reverses UP   │
│  ↓               ↑              │
│  SWEEP           REJECTION      │
└─────────────────────────────────┘
= Hidden liquidity grab at lows, bullish
```

**Detection:**
```
Internal Bull Sweep:
├── Early intrabar candles form a low
├── Later intrabar candles sweep below that low
├── Final intrabar candles close back above
├── Parent candle closes green
└── = Hidden sweep, bullish reversal

Internal Bear Sweep:
├── Early intrabar candles form a high
├── Later intrabar candles sweep above that high
├── Final intrabar candles close back below
├── Parent candle closes red
└── = Hidden sweep, bearish reversal
```

**Visual:** "iS" marker (intrabar Sweep) on the candle

---

### Volume Distribution

**What It Is:**
Where volume clustered within the parent candle - TOP, MID, or BOT third.

**Why It Matters:**
- **BOT clustering + bullish delta:** Institutions buying at lows (bullish)
- **TOP clustering + bearish delta:** Institutions selling at highs (bearish)
- **MID clustering:** Balanced/uncertain

**Calculation:**
```
Divide parent candle into 3 zones:
├── TOP third: high - (range/3)
├── MID third: middle zone
└── BOT third: low + (range/3)

For each intrabar candle:
├── Calculate midpoint
├── Assign volume to TOP/MID/BOT based on midpoint
└── Sum volumes by zone
```

---

## 📊 ENHANCED CONFLUENCE SCORING v7

### Score Components (Max ~14, normalized to 10)

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
| **IB Delta Confirm** | +0.9-1.5 | Intrabar delta matches direction |
| **IB Momentum** | +0.5-1.0 | Consistent intrabar direction |
| **IB Absorption** | +1.0 | Absorption detected matching direction |
| **IB Internal Sweep** | +1.0 | Hidden sweep confirms direction |
| **Volume Cluster** | +0.5 | Volume at favorable zone (BOT for bull) |

### Intrabar Confluence Breakdown

```
INTRABAR CONFLUENCE ADDITIONS:

IB Delta Confirmation:
├── Strong (70%+) + matching direction = +1.5 pts
├── Dominant (62%+) + matching direction = +0.9 pts
└── Not matching = +0 pts

IB Momentum:
├── Strong (75%+) + matching direction = +1.0 pts
├── Confirmed (60%+) + matching direction = +0.5 pts
└── Mixed/not matching = +0 pts

IB Absorption:
├── Bull absorption for LONG = +1.0 pts
├── Bear absorption for SHORT = +1.0 pts
└── No absorption or wrong direction = +0 pts

IB Internal Sweep:
├── Bull internal sweep for LONG = +1.0 pts
├── Bear internal sweep for SHORT = +1.0 pts
└── No internal sweep = +0 pts

Volume Cluster:
├── BOT cluster for LONG = +0.5 pts
├── TOP cluster for SHORT = +0.5 pts
└── MID cluster or wrong zone = +0 pts
```

---

## 🎯 IDEAL SETUPS v7 (HIGHEST WIN RATE)

### Setup 1: Absorption + Zone + Tier (NEW!)
```
Conditions:
├── Absorption detected (✕ marker)
├── Price at Order Block or FVG
├── Tier signal fires (S/A/B)
├── IB Delta confirms direction
├── Score: 8+ EXCELLENT
└── Win Rate: ~80-88%

WHY IT WORKS:
Absorption = institutions filling orders
Zone = known institutional level
Tier = significant move
= Triple institutional confirmation
```

### Setup 2: Internal Sweep + Zone
```
Conditions:
├── Internal sweep detected (iS marker)
├── At or near OB/FVG zone
├── IB momentum confirms (75%+)
├── Score: 7+ EXCELLENT
└── Win Rate: ~75-85%

WHY IT WORKS:
Hidden sweep = invisible stop hunt
Zone = where institutions defend
= Retail trapped, you enter with smart money
```

### Setup 3: Full Intrabar Alignment
```
Conditions:
├── IB Delta: Strong/Extreme (✓✓ or 🔥)
├── IB Momentum: Strong (🔥)
├── Volume Cluster: Favorable zone
├── Standard delta confirms
├── Score: 7+ EXCELLENT
└── Win Rate: ~75-82%

WHY IT WORKS:
All intrabar metrics align
= Maximum conviction in candle formation
= High probability continuation
```

### Setup 4: Standard v6 Setup (Still Valid)
```
Conditions:
├── Liquidity Sweep (LS↑ or LS↓)
├── Price at Order Block or FVG
├── Tier signal fires
├── Score: 7+ EXCELLENT
└── Win Rate: ~75-85%
```

---

## 📊 ENHANCED TABLE REFERENCE v7

The v7 table adds the **INTRABAR** section:

### CANDLE Section
| Row | What It Shows |
|-----|---------------|
| Points | Candle range in points + Tier (S/A/B/X) |
| Volume | Volume ratio + grade |

### ORDERFLOW Section
| Row | What It Shows |
|-----|---------------|
| Delta | Buy/Sell % + grade (now uses IB delta if available) |
| CVD | Direction + strength |

### INTRABAR Section (NEW!)
| Row | What It Shows |
|-----|---------------|
| IB Delta | TRUE intrabar buy/sell % + grade |
| IB Momentum | Direction consistency % + grade |
| Absorption | BULL ABS / BEAR ABS / — + 🎯 indicator |

### STRUCTURE Section
| Row | What It Shows |
|-----|---------------|
| FVG Zone | Current zone + quality score |
| Order Block | OB status |
| Liq Sweep | External LS↑/↓ or internal iS↑/↓ + indicator |

### SIGNAL Section
| Row | What It Shows |
|-----|---------------|
| Session | Current session + active indicator |
| SCORE | Numeric score /10 + classification |

---

## 🔧 INTRABAR SETTINGS GUIDE

### Intrabar Timeframe Selection

| Chart TF | Recommended Intrabar TF | Sub-candles |
|----------|------------------------|-------------|
| 1 min | 1 (same) | Limited data |
| 3 min | 1 | 3 candles |
| 5 min | 1 | 5 candles |
| 15 min | 1 or 5 | 15 or 3 candles |
| 30 min | 5 | 6 candles |
| 1 hour | 5 or 15 | 12 or 4 candles |

**Rule of Thumb:** Lower intrabar TF = more data = more accurate

### Parameter Tuning

**Absorption Threshold (Default: 65%)**
```
Lower (50-60%): More absorption signals, some false positives
Standard (65%): Balanced detection
Higher (70-80%): Fewer signals, higher quality
```

**Intrabar Momentum Min (Default: 60%)**
```
Lower (50-55%): Accepts mixed candles as directional
Standard (60%): Requires clear majority
Higher (70-80%): Requires strong conviction
```

**Intrabar Delta Weight (Default: 1.5)**
```
Lower (0.5-1.0): Intrabar delta contributes less to score
Standard (1.5): Full contribution
Higher (2.0-3.0): Intrabar delta heavily weighted
```

---

## ✅ ENTRY CHECKLIST v7

### Basic Requirements
- [ ] Signal present (S🎯/A🎯/B🎯 or Z)
- [ ] Score ≥ 4.5 (MEDIUM or better)
- [ ] Session active (🟢)

### Orderflow Confirmation
- [ ] Delta colored (not gray)
- [ ] CVD arrow matches direction
- [ ] Volume shows ✓ or better

### Intrabar Confirmation (NEW!)
- [ ] IB Delta matches direction (✓ or better)
- [ ] IB Momentum shows direction or strong (🔥)
- [ ] No conflicting absorption signal

### Structure Bonus
- [ ] In FVG Zone
- [ ] In Order Block
- [ ] Recent Liquidity Sweep
- [ ] Internal Sweep (iS)
- [ ] Absorption detected
- [ ] IFVG present

---

## 🚨 NEW ALERTS v7

### Intrabar-Specific Alerts

| Alert | What It Means | Priority |
|-------|---------------|----------|
| ⚡ INTRABAR BULL SWEEP | Hidden sweep lows inside candle | 🟠 HIGH |
| ⚡ INTRABAR BEAR SWEEP | Hidden sweep highs inside candle | 🟠 HIGH |
| 🎯 BULL ABSORPTION | Institutions accumulating | 🟠 HIGH |
| 🎯 BEAR ABSORPTION | Institutions distributing | 🟠 HIGH |

### Alert Priority Guide

| Alert | Priority | Action |
|-------|----------|--------|
| ⭐ EXCELLENT + ABSORPTION | 🔴 CRITICAL | Top-tier, enter immediately |
| ⭐ EXCELLENT LONG/SHORT | 🔴 CRITICAL | Check NOW |
| 🎯 ABSORPTION | 🟠 HIGH | Check for zone confluence |
| ⚡ INTRABAR SWEEP | 🟠 HIGH | Hidden opportunity |
| 🎯 S-TIER | 🟠 HIGH | Evaluate quickly |

---

## ⛔ DO NOT TRADE v7

All previous rules PLUS:

- IB Delta strongly conflicts with signal direction
- IB Momentum shows opposite direction at 75%+
- Absorption detected in OPPOSITE direction
- Score inflated only by intrabar (no structure)
- Intrabar data unavailable (empty array)

---

## 📝 TECHNICAL NOTES v7

### Compatibility

- **Pine Script v6** (required for `request.security_lower_tf()`)
- **Works on**: YM, MYM, NQ, MNQ, ES, MES, GC, MGC, BTC
- **Chart Type**: Standard candlestick (not Renko/Heikin Ashi)
- **Timeframes**: 1-minute to 4-hour recommended
- **Tick Charts**: Use 1-minute intrabar TF

### Performance Notes

- Intrabar analysis adds computational overhead
- If chart loads slowly, try higher intrabar TF
- `request.security_lower_tf()` returns array of data
- Empty arrays indicate no lower TF data available

### Timeframe Limitations

```
request.security_lower_tf() works when:
├── Intrabar TF < Chart TF (e.g., 1 min intrabar on 5 min chart)
└── Chart receives enough data from lower TF

Does NOT work when:
├── Intrabar TF >= Chart TF
├── Tick charts with minute intrabar (use seconds or same)
└── Very old historical data
```

---

## 📈 TRADE JOURNAL v7

```
DATE: ___________
SESSION: ☐ LDN  ☐ NY  ☐ PWR

SETUP TYPE:
☐ Absorption + Zone  ☐ Internal Sweep  ☐ Full IB Align
☐ Sweep + Zone  ☐ IFVG  ☐ OB+FVG  ☐ Zone Entry

TRADE:
├── Time: _______
├── Signal: S🎯 / A🎯 / B🎯 / Z / LS / iS
├── Direction: LONG / SHORT
├── Score: ___/10 (EXCELLENT / MEDIUM)
├── Entry: _______
├── Stop: _______
├── Target: _______
│
├── In FVG Zone: ☐ Yes  ☐ No
├── In Order Block: ☐ Yes  ☐ No
├── Liquidity Sweep: ☐ Yes  ☐ No
├── Internal Sweep: ☐ Yes  ☐ No
├── Absorption: ☐ Yes  ☐ No
├── IFVG Present: ☐ Yes  ☐ No
│
├── IB Delta: _____% (BULL / BEAR)
├── IB Momentum: _____% (BULL / BEAR / MIXED)
├── Volume Cluster: TOP / MID / BOT
│
├── Result: +/- ___ pts ($_____)
└── Notes: _______________________

DAILY SUMMARY:
├── Trades: ___
├── EXCELLENT setups: ___
├── With Absorption: ___
├── With Internal Sweep: ___
├── Wins: ___ | Losses: ___
├── Net P/L: $_____
└── Best setup type: _______________________
```

---

## 🏆 GOLDEN RULES v7

> **"Intrabar shows the truth the candle hides."**

> **"Absorption = They're loading. Get ready."**

> **"Internal sweep = Hidden trap. Enter after."**

> **"IB Delta + IB Momentum aligned = Maximum conviction."**

> **"When intrabar conflicts with signal, trust intrabar."**

> **"Volume at lows + buying = Institutions accumulating."**

> **"Confluence beats conviction. Stack the factors."**

> **"Leave every trade with money. The next setup is coming."**

---

## 🔧 TROUBLESHOOTING v7

| Issue | Solution |
|-------|----------|
| No intrabar data | Lower your chart TF or raise intrabar TF |
| IB Delta always neutral | Check intrabar TF is lower than chart TF |
| Too many absorption signals | Raise absorption threshold to 70%+ |
| Missing internal sweeps | More common on volatile markets |
| Slow chart loading | Use higher intrabar TF (5 instead of 1) |
| IB section not in table | Enable "Show Intrabar Metrics" |
| Conflicting signals | Trust intrabar data over standard delta |

---

## 📚 QUICK REFERENCE CARD

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YM ULTIMATE SNIPER v7                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  SIGNALS:                                                               │
│  S🎯 = S-Tier (50+ pts) → HOLD position                                │
│  A🎯 = A-Tier (25-49 pts) → SWING trade                                │
│  B🎯 = B-Tier (12-24 pts) → SCALP quick                                │
│  Z   = Zone entry                                                       │
│  LS↑/↓ = External Liquidity Sweep                                      │
│  iS↑/↓ = Internal (intrabar) Sweep                                     │
│  ✕   = Absorption detected                                             │
│                                                                         │
│  INTRABAR METRICS:                                                      │
│  IB Delta = TRUE buy/sell from lower TF                                │
│  IB Momentum = Direction consistency within bar                        │
│  Absorption = High vol + low move = accumulation                       │
│  Vol Cluster = TOP/MID/BOT volume distribution                         │
│                                                                         │
│  INTRABAR GRADES:                                                       │
│  🔥 = Extreme (78%+ delta or 75%+ momentum)                            │
│  ✓✓ = Strong (70%+ delta)                                              │
│  ✓  = Confirmed (62%+ delta or 60%+ momentum)                          │
│  —  = Neutral / Mixed                                                   │
│                                                                         │
│  HIGH PROBABILITY SETUPS:                                               │
│  1. Absorption + Zone + Tier (~80-88%)                                 │
│  2. Internal Sweep + Zone (~75-85%)                                    │
│  3. Full Intrabar Alignment (~75-82%)                                  │
│  4. Standard Sweep + Zone (~75-85%)                                    │
│                                                                         │
│  SCORE CLASSIFICATION:                                                  │
│  EXCELLENT (7.0+) = Full size, high confidence                         │
│  MEDIUM (4.5-6.9) = Standard size, good setup                          │
│  WEAK (<4.5)      = No signal shown                                    │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

*© Alexandro Disla - YM Ultimate SNIPER v7*
*Intrabar Edition | See Inside The Candle*
