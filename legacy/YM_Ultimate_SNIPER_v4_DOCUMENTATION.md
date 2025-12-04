# YM Ultimate SNIPER v4 - Documentation & Trading Guide

## 🎯 Unified GRA + DeepFlow | YM-Optimized for Low Volatility
**TARGET: 3-7 High-Confluence Trades per Day**

> **Philosophy:** *YM's lower volatility is not a weakness—it's our edge. Predictability + precision = consistent profits.*

---

## 🆕 VERSION 4 CHANGES

### Major Updates
- **POC Removed**: The Point of Control visualization has been completely removed
- **New Candle-Anchored Imbalances**: Precise buy/sell imbalance markers directly on candles at exact price levels
- **Pattern Classification**: Imbalances now classify as Continuation, Absorption, or Reversal
- **Stable Positioning**: All candle elements use `bar_index` anchoring for resize-proof display
- **Enhanced Confluence**: Candle imbalance alignment now contributes to confluence scoring

### Why These Changes?
1. **POC Issues**: The POC visualization had positioning bugs during chart resize
2. **Better Order Flow**: Candle-anchored imbalances provide more precise entry/exit information
3. **Pattern Recognition**: Understanding whether an imbalance signals continuation vs reversal is critical for trade direction

---

## ⚡ QUICK REFERENCE CARD

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    YM ULTIMATE SNIPER v4 - QUICK REFERENCE                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  💰 YM BASICS:                                                              │
│  ═════════════                                                              │
│  • 1 tick = 1 point = $5/contract                                          │
│  • Typical daily range: 150-400 points                                      │
│  • 30-40% less volatile than NQ                                            │
│  • More institutional, less retail noise                                    │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  🎯 TIER THRESHOLDS (YM-OPTIMIZED):                                        │
│  ══════════════════════════════════                                         │
│  S-TIER: 50+ pts  = $250+/contract  → HOLD (Institutional sweep)           │
│  A-TIER: 25-49 pts = $125-245/contract → SWING (Strong momentum)           │
│  B-TIER: 12-24 pts = $60-120/contract  → SCALP (Quick grab)                │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  📊 CANDLE IMBALANCE MARKERS (NEW in v4):                                  │
│  ═════════════════════════════════════════                                  │
│  🟢 Green Solid  = Buy Imbalance (Continuation)                            │
│  🔴 Red Solid    = Sell Imbalance (Continuation)                           │
│  🟡 Gold Dashed  = Absorption (Counter-flow being absorbed)                │
│  🟣 Purple Dotted = Reversal (Exhaustion signal)                           │
│                                                                             │
│  PATTERN LOGIC:                                                             │
│  • CONT: Imbalance aligns with candle direction (flow WITH trend)          │
│  • ABS:  Imbalance at extreme opposite to direction (absorbed counter)     │
│  • REV:  Imbalance fighting the move (exhaustion warning)                  │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ⏰ SESSION WINDOWS:                                                        │
│  ═══════════════════                                                        │
│  LDN   → 3:00-5:00 AM ET   (European flow)                                 │
│  NY    → 9:30-11:30 AM ET  (US opening drive)                              │
│  PWR   → 3:00-4:00 PM ET   (End-of-day rebalancing)                        │
│                                                                             │
│  Expected Trades: 1-2 LDN | 2-3 NY | 1-2 PWR = 4-7 total                   │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  📊 CONFLUENCE SCORING (MAX 10 POINTS):                                    │
│  ═══════════════════════════════════════                                   │
│  Tier Signal:       S=3, A=2, B=1 points                                   │
│  In Active Zone:    +2 points                                              │
│  Imbalance Aligned: +1 point (2+ buy imb lower half on bull, etc.)        │
│  Imbalance Support: +1 point (supporting S/R zone nearby)                  │
│  Strong Volume:     +1 point (2x+ average)                                 │
│  Strong Delta:      +1 point (70%+ dominance)                              │
│  CVD Momentum:      +1 point (CVD trending with signal)                    │
│                                                                             │
│  MINIMUM SCORE: 5/10 to show signal (adjustable)                           │
│  IDEAL SCORE:   7+/10 for highest probability                              │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  🚨 SIGNAL TYPES:                                                          │
│  ═════════════════                                                          │
│  S🎯 / A🎯 / B🎯 → GRA Tier Signals (Full confluence)                      │
│  Z🎯            → Zone Entry (At DFZ zone + delta + volume)                │
│  SP             → Single Print (Institutional impulse)                     │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ✓ ENTRY CHECKLIST:                                                        │
│  ═══════════════════                                                        │
│  □ Signal appears (check Score ≥5)                                         │
│  □ Session active (LDN!/NY!/PWR!)                                          │
│  □ Table: Vol GREEN, Delta colored, Body GREEN                             │
│  □ CVD arrow (▲/▼) matches direction                                       │
│  □ Check IMB row for alignment (more B than S for longs)                   │
│  □ Look for CONT markers on candle (green on bull, red on bear)            │
│  □ Note stop/target lines on chart                                         │
│  □ Check Zone status (bonus if IN ZONE)                                    │
│  □ Execute at signal candle close                                          │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ⛔ DO NOT TRADE WHEN:                                                      │
│  ════════════════════                                                       │
│  ✗ Session shows "---"                                                      │
│  ✗ Score < 5/10                                                             │
│  ✗ Vol shows RED (<1.8x)                                                    │
│  ✗ Delta < 62%                                                              │
│  ✗ Multiple REV (reversal) markers visible                                  │
│  ✗ Just before major news (FOMC, NFP, etc.)                                 │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🎯 CANDLE-ANCHORED IMBALANCE SYSTEM

### What Are Candle Imbalances?

Candle imbalances show WHERE within a candle buyers or sellers significantly dominated. Unlike full footprint charts (which show every price level), this system only marks **meaningful imbalances** at exact price levels where the buy/sell ratio exceeds your threshold (default 2:1).

### Visual Markers

| Marker | Color | Style | Meaning |
|--------|-------|-------|---------|
| **CONT** | Green/Red | Solid (thick) | Continuation - Flow WITH the candle direction |
| **ABS** | Gold | Dashed | Absorption - Counter-flow being absorbed |
| **REV** | Purple | Dotted | Reversal - Exhaustion, potential turn |

### Pattern Classification Logic

```
BULLISH CANDLE (Green):
═══════════════════════
                    ┌─────┐
                    │     │ ← Red ABS here = sellers absorbed at high (bullish)
                    │█████│
                    │█████│ ← Green CONT here = buyers pushing (continuation)
      Upper Wick →  │█████│
                    │█████│
                    ├─────┤
                    │█████│
      Body →        │█████│ ← Green CONT in lower body = strong continuation
                    │█████│
                    │█████│
                    ├─────┤
      Lower Wick →  │     │ ← Green CONT here = aggressive accumulation
                    │     │ ← Purple REV if SELL imbalance here = warning
                    └─────┘

BEARISH CANDLE (Red):
═══════════════════════
                    ┌─────┐
      Upper Wick →  │     │ ← Red CONT here = sellers initiating (continuation)
                    │     │ ← Purple REV if BUY imbalance here = exhaustion
                    ├─────┤
      Body →        │█████│ ← Red CONT in upper body = strong continuation
                    │█████│
                    │█████│
                    │█████│
                    ├─────┤
                    │█████│
      Lower Wick →  │█████│ ← Green ABS here = buyers absorbed at low (bearish)
                    │     │
                    └─────┘
```

### How to Read Imbalances

**For LONG Entries:**
- ✅ Look for GREEN CONT markers in lower half of candle body
- ✅ Gold ABS at upper wick = sellers being absorbed (bullish)
- ⚠️ Purple REV at bottom = buyers exhausting, caution
- ❌ Multiple RED markers throughout = bearish pressure

**For SHORT Entries:**
- ✅ Look for RED CONT markers in upper half of candle body
- ✅ Gold ABS at lower wick = buyers being absorbed (bearish)
- ⚠️ Purple REV at top = sellers exhausting, caution
- ❌ Multiple GREEN markers throughout = bullish pressure

### Table Display: IMB Row

The info panel now shows: `IMB: 3B/1S`
- **3B** = 3 price levels with Buy imbalance
- **1S** = 1 price level with Sell imbalance

For longs, you want more B than S. For shorts, more S than B.

---

## 📊 IMBALANCE S/R ZONES

### What Are They?

When multiple consecutive price levels (default: 3+) all show the same type of imbalance, they form a **stacked imbalance zone**. These zones act as support/resistance because:
- **Bullish Zone** (green): Aggressive buying created a demand zone
- **Bearish Zone** (red): Aggressive selling created a supply zone

### Zone Behavior

```
Zone States:
═══════════
FRESH (bright) → Just created, untested
TESTED (gray)  → Price touched zone midpoint
BROKEN (dim)   → Price closed through zone
```

### Trading S/R Zones

| Zone Type | Price Approaches From | Expected Behavior |
|-----------|----------------------|-------------------|
| Bullish Zone | Above (falling) | Support - look for bounce |
| Bullish Zone | Below (rising) | May pause, then breakthrough |
| Bearish Zone | Below (rising) | Resistance - look for rejection |
| Bearish Zone | Above (falling) | May pause, then breakthrough |

---

## 🔧 CONFIGURATION GUIDE

### Candle Imbalance Settings

| Setting | Default | Range | Purpose |
|---------|---------|-------|---------|
| Show Candle Imbalances | On | - | Toggle visibility |
| Imbalance Ratio | 2.0 | 1.5-4.0 | Buy must be 2x sell to mark |
| Price Resolution | 8 | 4-16 | More = finer granularity |
| Only on Tiered | Off | - | Only show on B+ candles |
| Only in Sessions | On | - | Filter by session |

### Recommended Configurations

**Conservative (Clean Chart):**
```
Imbalance Ratio: 2.5
Price Resolution: 6
Only on Tiered: ON
Only in Sessions: ON
```

**Standard (Balanced):**
```
Imbalance Ratio: 2.0
Price Resolution: 8
Only on Tiered: OFF
Only in Sessions: ON
```

**Aggressive (Maximum Info):**
```
Imbalance Ratio: 1.5
Price Resolution: 12
Only on Tiered: OFF
Only in Sessions: OFF
```

---

## 📋 CONFLUENCE SCORING (Updated)

### Score Breakdown

```
CONFLUENCE SCORE CALCULATION (v4):
══════════════════════════════════

BASE POINTS (Tier):
├── S-Tier signal: +3 points
├── A-Tier signal: +2 points
└── B-Tier signal: +1 point

BONUS POINTS:
├── Inside Active Zone (DFZ): +2 points
│   └── Price within bull/bear FVG zone
│
├── Imbalance Aligned: +1 point (NEW in v4)
│   └── 2+ buy imbalances in lower half on bull candle
│   └── 2+ sell imbalances in upper half on bear candle
│
├── Imbalance Support: +1 point
│   └── Price near recent S/R imbalance zone
│
├── Strong Volume: +1 point
│   └── 2x+ average volume
│
├── Strong Delta: +1 point
│   └── 70%+ buy or sell dominance
│
└── CVD Momentum: +1 point
    └── CVD trending with signal direction

MAXIMUM: 10 points
MINIMUM TO SIGNAL: 5 points (adjustable)
```

---

## 📊 VISUAL GUIDE

```
PERFECT YM SNIPER v4 SETUP:
═══════════════════════════════════════════════════════════════════

                              │  Current Price
                              │
    ┌─────────────────────────┴────────────────────────────────┐
    │          BEARISH S/R ZONE (Red, from stacked imbalances) │
    └──────────────────────────────────────────────────────────┘
                              │
            ══════════════════╪══════════════════  SP High (Purple)
                              │
        ┌─────────────────────┤
        │                     │
        │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│ ← A🎯 LONG Signal
        │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│   Score: 8/10
        │ ━━━ (Gold ABS)      │ ← Sellers absorbed at top
        │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
        │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
        │ ━━━ (Green CONT)    │ ← Buyers pushing = continuation
        │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│
        │ ━━━ (Green CONT)    │ ← Strong accumulation
        └─────────────────────┤
                              │
            ══════════════════╪══════════════════  SP Low (Purple)
                              │
    ┌─────────────────────────┴────────────────────────────────┐
    │          BULLISH S/R ZONE (Green, from stacked imbalances│
    └──────────────────────────────────────────────────────────┘
                              │
                        Stop Loss

CONFLUENCE CHECK:
✓ A-Tier signal (+2)
✓ At edge of bullish S/R zone (+1)
✓ Imbalance aligned (2 green CONT in lower half) (+1)
✓ Strong volume 2.3x (+1)
✓ Delta 72% buyers (+1)
✓ CVD bullish (+1)
✓ In FVG zone (+2)
TOTAL: 9/10 = ELITE SETUP

IMB Display: 3B/1S (Bullish!)

ACTION: Full size LONG at signal candle close
STOP: Below S/R zone
TARGET: 2:1 R:R (auto-calculated)
```

---

## 🔧 TROUBLESHOOTING

| Issue | Cause | Fix |
|-------|-------|-----|
| No imbalance markers | Session filter on | Check "Only in Sessions" |
| Too many markers | Low ratio/high resolution | Raise ratio to 2.5+, lower resolution to 6 |
| Markers not visible | Wrong colors for theme | Adjust colors in settings |
| Zones cluttering chart | Max zones too high | Reduce to 8-10 |
| Elements moving on resize | Using old version | Update to v4 |

---

## 🎯 TRADING WORKFLOW (v4)

### Pre-Trade Checklist

1. **Session Check**: Is LDN/NY/PWR active?
2. **Signal Check**: S🎯, A🎯, or B🎯 present?
3. **Score Check**: Is score ≥5 (ideally 7+)?
4. **IMB Check**: Does IMB row favor your direction?
5. **Pattern Check**: Are candle markers showing CONT (continuation)?
6. **Zone Check**: Is price near supportive S/R zone?

### During Trade

1. **Watch for REV markers**: Purple dotted = potential exhaustion
2. **Monitor IMB shifts**: If ratio flips, consider exit
3. **Respect S/R zones**: These are institutional levels

### Exit Rules

| Condition | Action |
|-----------|--------|
| Target hit | Full exit |
| REV markers appear | Tighten stop or partial exit |
| Price enters opposing zone | Consider exit |
| IMB shifts against you | Tighten stop |

---

## 📈 POSITION SIZING BY TIER

| Tier | Size | Hold Time | Target R:R | IMB Requirement |
|------|------|-----------|------------|-----------------|
| S-TIER (50+ pts) | Full | 2-5 min | 2.5:1 | 3+ aligned imbalances |
| A-TIER (25-49 pts) | 75% | 1-3 min | 2.0:1 | 2+ aligned imbalances |
| B-TIER (12-24 pts) | 50% | 30-90 sec | 1.5:1 | 1+ aligned imbalance |

---

## 🏆 GOLDEN RULES FOR YM v4

> **"Imbalances tell the story. Green CONT on longs, Red CONT on shorts."**

> **"Absorption (ABS) is your friend. Counter-flow getting absorbed = your direction strengthening."**

> **"Reversal (REV) is your warning. Multiple purple markers = step aside."**

> **"S/R zones from stacked imbalances are institutional. Respect them."**

> **"The IMB ratio in the table is your quick-glance sentiment. 4B/1S = bullish bias."**

---

## 📝 PINE SCRIPT v6 TECHNICAL NOTES

### Positioning System

**Candle-Anchored Elements** (stick to specific bars):
- Use `bar_index` for x-coordinates
- Includes: Imbalance markers

**Time-Extended Elements** (extend into future):
- Use `xloc.bar_time` with `time` coordinates
- Includes: FVG zones, S/R zones, Single prints

### Key UDTs

```
CandleImb:
├── barIdx (bar_index position)
├── priceLevel (exact price)
├── isBuyImb (true/false)
├── pattern ("CONT"/"ABS"/"REV")
└── marker (line reference)

ImbSRZone:
├── priceTop/priceBottom
├── isBullish
├── startTime
└── zoneBox (box reference)
```

---

## 🚨 ALERT SETUP

| Alert | Priority | Action |
|-------|----------|--------|
| 🎯 YM S-TIER LONG/SHORT | 🔴 CRITICAL | Drop everything, check immediately |
| 🎯 YM A-TIER LONG/SHORT | 🟠 HIGH | Evaluate within 15 seconds |
| 🎯 YM B-TIER LONG/SHORT | 🟡 MEDIUM | Check if available |
| 🎯 YM ZONE BUY/SELL | 🟢 STANDARD | Good context entry |
| 📦 NEW ZONE | 🔵 INFO | Mark on mental map |
| ⭐ SINGLE PRINT | 🔵 INFO | Note for future S/R |

### Alert Message Format (v4)

```
🎯 YM A-LONG | YM1! @ 42,150 | 68%B | Score: 7/10 | IN ZONE | IMB: 3B/1S | Stop: 42,098 | SWING
```

---

## 📊 DAILY TRADE JOURNAL TEMPLATE (v4)

```
DATE: ___________
SESSION: □ LDN  □ NY  □ PWR

TRADE 1:
├── Time: _______
├── Signal: S🎯 / A🎯 / B🎯 / Z🎯
├── Score: ___/10
├── IMB: ___B / ___S
├── Pattern: □ CONT  □ ABS  □ REV
├── Entry: _______
├── Stop: _______
├── Target: _______
├── In Zone: □ Yes  □ No
├── Result: +/- ___ pts ($_____)
└── Notes: _______________________

DAILY SUMMARY:
├── Total Trades: ___
├── Win Rate: ___%
├── Net P/L: $_____
├── Best Setup: _______
├── IMB Read Accuracy: ___%
└── Improvement: _______________________
```

---

*© Alexandro Disla - YM Ultimate SNIPER v4*
*Pine Script v6 | TradingView*
*Unified GRA v5 + DeepFlow Zones + Candle-Anchored Imbalances | YM-Optimized*
