# YM Ultimate SNIPER v8.1 - SNIPER STRICT EDITION

## 🎯 CHANGELOG: What's New in v8.1

### The Problem We Fixed
**GOD MODE was handing out awards like participation trophies.** Too many wicky, indecisive candles were getting GOD MODE status just because they had enough confluence points. A GOD MODE candle should show **CLEAR DOMINANCE** - fat body, minimal adverse wick, consistent pressure throughout formation.

---

## 🔥 MAJOR CHANGES

### 1. CANDLE DOMINANCE INDEX (CDI) - NEW METRIC

The CDI quantifies "who won the candle" on a 0-10 scale:

```
CDI COMPONENTS:
├── Body Score (0-4 pts): How fat is the body?
├── Adverse Wick Score (0-3 pts): How small is the wick against direction?
├── Favorable Wick Score (0-2 pts): Clean entry side?
└── Closing Strength (0-1 pt): Did it close near the extreme?

CDI RATINGS:
├── 8.0+ = 🔥 DOMINANT (ideal for GOD MODE)
├── 6.0-7.9 = ✓✓ STRONG  
├── 4.0-5.9 = ✓ ACCEPTABLE
└── <4.0 = WEAK (not GOD MODE worthy)
```

### 2. STRICT GOD MODE GATES (6 GATES)

**Score alone no longer qualifies for GOD MODE.** Now a candle must pass ALL 6 gates:

| Gate | Requirement | Default |
|------|-------------|---------|
| **1. Score** | Must meet GOD MODE threshold | ≥9.0 |
| **2. Body** | Body ratio must be "fat" | ≥70% |
| **3. Adverse Wick** | Wick against direction must be small | ≤20% |
| **4. Delta** | Buy/sell dominance must be strong | ≥70% |
| **5. Session** | Must be in active session (configurable) | LDN/NY/PWR |
| **6. Pressure** | Intrabar pressure must be consistent | Same side dominated early AND late |

**If ANY gate fails, GOD MODE is DENIED** - even with a 10/10 score!

### 3. 30-BAR SIGNAL DISPLAY LIMIT

**Past signals are now hidden.** Only the last 30 bars show tier markers, sweeps, and absorption signals. This keeps the chart clean and focused on recent action.

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

### 4. PRESSURE CONSISTENCY TRACKING

New intrabar analysis that tracks if the **same side dominated throughout the candle**:

```
CANDLE FORMATION ANALYSIS:
├── First Half: Who dominated? (earlyBuyVol vs earlySellVol)
├── Second Half: Who dominated? (lateBuyVol vs lateSellVol)
└── Consistent? = Same side won BOTH halves

PRESSURE CONSISTENT = Buyers dominated early AND late
                   OR Sellers dominated early AND late

PRESSURE MIXED = Buyers dominated early, sellers late
              OR Sellers dominated early, buyers late
```

**GOD MODE requires consistent pressure** when intrabar analysis is enabled.

### 5. GOD MODE DENIAL REASON IN TABLE

When a candle scores 9.0+ but fails a gate, the table now shows **WHY**:

```
DENIAL REASONS:
├── "DENIED: WICK" = Adverse wick too large (>20%)
├── "DENIED: DELTA" = Delta dominance too weak (<70%)
├── "DENIED: SESSION" = Not in active session
├── "DENIED: VOLUME" = Volume below 1.5x
└── "DENIED: PRESSURE" = Mixed pressure during formation
```

---

## 📊 NEW TABLE SECTIONS

### CANDLE QUALITY Section (NEW)
```
══ CANDLE QUALITY ══
Body      | 78%      | FAT
Adv Wick  | 12%      | CLEAN
CDI       | 8.2/10   | 🔥
```

### INTRABAR Section (UPDATED)
```
══ INTRABAR ══
IB Data   | 12 bars  | ✓
IB Delta  | 74% BUY  | 🔥
Pressure  | CONSISTENT | ✓    ← NEW
```

---

## ⚙️ NEW SETTINGS

### CANDLE DOMINANCE (v8.1) Group
```
GOD MODE: Min Body Ratio     = 0.70 (body must be 70%+ of range)
GOD MODE: Max Adverse Wick   = 0.20 (wick against direction ≤20%)
GOD MODE: Min Delta Dominance = 0.70 (70%+ buy/sell dominance)
GOD MODE: Min Intrabar Delta = 0.68 (intrabar delta ≥68%)
GOD MODE: Require Active Session = ON
GOD MODE: Require 1.5x+ Volume = ON
```

### SIGNAL DISPLAY (v8.1) Group
```
Show Signals: Last N Bars = 30
Show Historical FVG/OB Zones = ON (zones always visible)
```

---

## 🎯 PRACTICAL IMPACT

### Before v8.1 (Too Many False GOD MODE)
```
Candle: 35 point move, score 9.2, BUT:
- Body only 55% of range (thin)
- Upper wick 35% (buyers got pushed back hard)
- Intrabar showed mixed pressure
RESULT: GOD MODE ⚡ (WRONG!)
```

### After v8.1 (Strict GOD MODE)
```
Same candle: Score 9.2, but:
- Gate 2 FAILED: Body 55% < 70% required
- Gate 3 FAILED: Wick 35% > 20% allowed
- Gate 6 FAILED: Pressure inconsistent
RESULT: DENIED: WICK (Correct - this was a fake-out candle)
```

---

## 🏆 THE NEW GOD MODE STANDARD

A TRUE GOD MODE candle must show:

1. **HIGH SCORE** (≥9.0) - Multiple confluence factors aligned
2. **FAT BODY** (≥70%) - Clear directional commitment
3. **CLEAN WICKS** (≤20% adverse) - Minimal pushback
4. **STRONG DELTA** (≥70%) - One side clearly dominated
5. **IN SESSION** - Institutional participation
6. **CONSISTENT PRESSURE** - Same side controlled throughout

**Translation:** *"Institutions stepped in with size, pushed hard in one direction, and never let up. No hesitation, no give-back. This is a candle that means business."*

---

## 📈 YM/MYM OPTIMIZATION NOTES

The default settings are tuned for YM's characteristics:
- Lower volatility than NQ/GC/BTC → Tighter gates work better
- 50 pts for S-Tier is already conservative
- 70% body ratio filters out the indecisive noise
- Session requirement is crucial - YM moves on institutional flow

### Low Volume Conditions
The strict gates actually **help** in low volume:
- Wicky candles (common in low vol) get filtered
- Pressure consistency catches fake moves
- CDI prevents thin-body noise from triggering

---

## 🚀 QUICK START

1. Apply v8.1 to your 5-minute YM chart
2. Set intrabar to "1" (1-minute) or "100T" (tick)
3. Watch the CANDLE QUALITY section in the table
4. GOD MODE will now be RARE - but TRUSTWORTHY
5. Check the DENIAL reason if score is 9+ but no ⚡

---

*v8.1 SNIPER STRICT EDITION - "Fat Candles Only"*
*© Alexandro Disla*
