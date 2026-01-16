# 🎯 SNIPER INDICATORS CHEATSHEET

---

## 📊 SNIPER INITIAL BALANCE V1

### What It Does
Draws the first hour's high/low range with extensions and breakout signals.

### IB Times (Auto-Selected)
| Market Type | IB Period (ET) |
|-------------|----------------|
| Index (ES/NQ/YM) | 9:30 - 10:30 |
| Gold (GC/MGC) | 8:30 - 9:30 |
| Energy (CL) | 9:00 - 10:00 |

### Levels Drawn
| Level | Style | Purpose |
|-------|-------|---------|
| IB High | Solid | Resistance |
| IB Low | Solid | Support |
| IB Mid | Dashed | Mean reversion |
| 50% Ext | Dotted | Target 1 |
| 100% Ext | Dotted | Target 2 |
| 1SD (1.28x) | Dashed | 80% range |
| 2SD (2.0x) | Dashed | 95% range |

### Signals
| Signal | Meaning | Action |
|--------|---------|--------|
| `IB↑` | Breakout above IB High | Look for long |
| `IB↓` | Breakout below IB Low | Look for short |
| `RT↑` | Retest long entry | **BEST ENTRY** - Go long |
| `RT↓` | Retest short entry | **BEST ENTRY** - Go short |
| `FK` | Fakeout warning | **AVOID** - Don't enter |

### Entry Requirements (All Must Be True)
- ✅ Close above/below level (not just wick)
- ✅ Volume ≥ 1.3x average
- ✅ Body ≥ 60% of candle
- ✅ Minimal adverse wick

### Quick Trade Plan
```
LONG: Wait for RT↑ → SL below IB Low → TP at 50% or 100% ext
SHORT: Wait for RT↓ → SL above IB High → TP at 50% or 100% ext
```

---

## 🔫 SNIPER ORB V4

### What It Does
Draws 5/15/30 minute Opening Range Breakout levels with confirmation patterns.

### Session Times
| Session | Hours (ET) |
|---------|------------|
| London | 3:00 - 9:30 |
| New York | 9:30 - 17:00 |

### Levels Drawn
| Level | Color Default | Purpose |
|-------|---------------|---------|
| 5m ORB H/L | Blue | Scalp levels |
| 15m ORB H/L | Cyan | Swing levels |
| 30m ORB H/L | Purple | **Primary levels** |
| Targets 1x-3x | Green/Red | Profit targets |

### Signals
| Signal | Meaning | Priority |
|--------|---------|----------|
| `ORB↑` | Confirmed breakout up | ⭐⭐ |
| `ORB↓` | Confirmed breakout down | ⭐⭐ |
| `RT↑` | Retest long entry | ⭐⭐⭐ **BEST** |
| `RT↓` | Retest short entry | ⭐⭐⭐ **BEST** |
| `FVG↑` | FVG zone long | ⭐⭐⭐ |
| `FVG↓` | FVG zone short | ⭐⭐⭐ |
| `ABS` | Absorption (caution) | ⚠️ Warning |
| `FK!` | Fakeout detected | ❌ Avoid |

### FVG Zones (Blue Boxes)
- **Bullish FVG** = Gap below price → Support zone
- **Bearish FVG** = Gap above price → Resistance zone
- **Best Entry** = Price touches FVG + Engulfing candle

### Bar Colors
| Color | Meaning |
|-------|---------|
| Bright Green | Bullish breakout confirmed |
| Bright Red | Bearish breakout confirmed |
| Light Green | Bullish retest entry |
| Light Red | Bearish retest entry |

### Info Table Key
| Field | Green = Good | Yellow/Orange = Caution |
|-------|--------------|-------------------------|
| Volume | HIGH VOL | Normal |
| Body | STRONG (70%+) | Normal/Weak |
| Status | BROKE HIGH/LOW | IN RANGE |

### Quick Trade Plan
```
LONG:
1. Wait for 30m ORB to complete
2. Watch for ORB↑ breakout
3. WAIT for pullback to ORB High
4. Enter on RT↑ or FVG↑ signal
5. SL = Below 30m ORB Low
6. TP = Target 1x or 2x

SHORT:
1. Wait for 30m ORB to complete
2. Watch for ORB↓ breakout
3. WAIT for pullback to ORB Low
4. Enter on RT↓ or FVG↓ signal
5. SL = Above 30m ORB High
6. TP = Target 1x or 2x
```

---

## ⚡ QUICK RULES

### ✅ TAKE These Signals
- RT↑/RT↓ with high volume
- FVG↑/FVG↓ with engulfing candle
- Any signal where Volume = "HIGH" AND Body = "STRONG"

### ❌ SKIP These Signals
- Any signal without volume confirmation
- Any signal near ABS (absorption) warning
- Any signal followed by FK! (fakeout)
- Breakouts with weak body (< 60%)

### 🛡️ Challenge Mode Rules
1. Only take RT signals (skip initial breakouts)
2. Require FVG confluence
3. Volume MUST be elevated
4. Exit at first target
5. 1 contract max

---

## 📐 STOP LOSS PLACEMENT

| Trade Type | Stop Loss Location |
|------------|-------------------|
| IB Long | Below IB Low |
| IB Short | Above IB High |
| ORB Long | Below 30m ORB Low |
| ORB Short | Above 30m ORB High |
| Retest Entry | Below/Above the retested level + buffer |

---

## 🎯 TARGET PLACEMENT

| Target | Calculation |
|--------|-------------|
| 50% | IB/ORB Range × 0.5 from breakout level |
| 100% | IB/ORB Range × 1.0 from breakout level |
| 1SD | IB Range × 1.28 from breakout level |
| 2SD | IB Range × 2.0 from breakout level |

---

## ⏰ BEST TRADING WINDOWS

| Session | Peak Volatility |
|---------|-----------------|
| NY Open | 9:30 - 11:30 ET |
| London Open | 3:00 - 5:00 ET |
| Gold | 8:30 - 10:30 ET |

---

*Stay patient. Wait for confirmation. Protect capital.*
