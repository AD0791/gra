# DeepFlow Zones SNIPER - Documentation & Cheatsheet

## 🎯 DeepFlow Zones - SNIPER Edition
**Horizontal Limit Order Zones | Institutional FVG + Single Prints**

> **Philosophy:** *Only mark the zones where institutions MUST have orders. Everything else is noise.*

---

## ⚡ QUICK CHEATSHEET

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     DEEPFLOW ZONES SNIPER - QUICK REFERENCE                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  🎯 ZONE CREATION REQUIREMENTS (ALL MUST BE TRUE):                          │
│  ══════════════════════════════════════════════════                         │
│  ✓ FVG exists     → Gap between candle low and 2-bar-ago high              │
│  ✓ Gap Size       → At least 30% of ATR (significant gap)                  │
│  ✓ Impulse Candle → 1.8x average range + 65% body ratio                    │
│  ✓ Volume         → 2.0x+ average on impulse candle                        │
│  ✓ Direction      → Middle candle confirms gap direction                   │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  📊 ZONE TYPES:                                                             │
│  ══════════════                                                             │
│  🟢 BULLISH ZONE  → Green box BELOW price (buy zone)                        │
│  🔴 BEARISH ZONE  → Red box ABOVE price (sell zone)                         │
│  ⚫ TESTED ZONE   → Gray box (CE level touched)                             │
│  ⬛ BROKEN ZONE   → Dark gray (price closed through)                        │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ⭐ SINGLE PRINT LINES:                                                     │
│  ══════════════════════                                                     │
│  Requirements:                                                              │
│  • Range 1.8x+ average                                                      │
│  • Body 65%+ of range                                                       │
│  • Volume 2.0x+ average                                                     │
│  • Delta 60%+ confirms direction                                            │
│                                                                             │
│  Usage:                                                                     │
│  • Gold lines at HIGH and LOW of impulse candle                            │
│  • Price often returns to these levels                                      │
│  • Use as support/resistance for entries                                    │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  🚨 ENTRY SIGNALS:                                                          │
│  ═══════════════════                                                        │
│  BUY🎯 appears when:                                                        │
│  • Price is inside BULLISH zone                                             │
│  • Delta shows 60%+ buy dominance                                           │
│  • Volume is 1.5x+ average                                                  │
│                                                                             │
│  SELL🎯 appears when:                                                       │
│  • Price is inside BEARISH zone                                             │
│  • Delta shows 60%+ sell dominance                                          │
│  • Volume is 1.5x+ average                                                  │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  📐 ZONE ANATOMY:                                                           │
│  ═════════════════                                                          │
│                                                                             │
│     BULLISH FVG ZONE:                 BEARISH FVG ZONE:                     │
│                                                                             │
│     Current Low ─────────────────     ───────────────── 2-bar-ago Low       │
│     ┌─────────────────────────┐       ┌─────────────────────────┐          │
│     │ █████ ZONE █████████████│       │ █████ ZONE █████████████│          │
│     │- - - CE (50%) - - - - - │       │- - - CE (50%) - - - - - │          │
│     │ ████████████████████████│       │ ████████████████████████│          │
│     └─────────────────────────┘       └─────────────────────────┘          │
│     2-bar-ago High ──────────────     ───────────────── Current High        │
│                                                                             │
│     Entry: At or near CE line         Entry: At or near CE line             │
│     Stop: Below zone bottom           Stop: Above zone top                  │
│     Target: 1:1 or 2:1 R:R            Target: 1:1 or 2:1 R:R                │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ⛔ ZONE IS INVALID WHEN:                                                   │
│  ═════════════════════════                                                  │
│  ✗ Gap size < 30% of ATR (too small)                                        │
│  ✗ No impulse candle (weak move)                                            │
│  ✗ Volume < 2x average (retail move)                                        │
│  ✗ Zone age > 50 bars (stale)                                               │
│  ✗ Price already closed through zone                                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 DETAILED DOCUMENTATION

### What Makes SNIPER Zones Different?

Standard FVG indicators create zones everywhere. SNIPER zones only appear when there's **institutional footprint**:

| Filter | Standard FVG | SNIPER Zones | Why It Matters |
|--------|-------------|--------------|----------------|
| Gap Size | Any gap | **≥30% ATR** | Significant imbalance |
| Volume | Optional | **2.0x+ avg** | Institutional volume |
| Impulse | None | **1.8x range** | Real momentum |
| Body | None | **65%+ ratio** | Conviction candle |
| Max Zones | 20-50 | **10 max** | Only the best |
| Zone Life | 100 bars | **50 bars** | Fresh zones only |

---

### How Zones Are Created

```
BULLISH FVG FORMATION:
═══════════════════════

Bar 0 (2 bars ago):    Bar 1 (Impulse):    Bar 2 (Current):
┌─────┐                ┌─────┐             ┌─────┐
│     │                │█████│             │     │
│     │ HIGH ──────    │█████│             │     │
│     │         │      │█████│             │     │
└─────┘         │      │█████│             │     │── LOW
                │      └─────┘             └─────┘
                │                              │
                └──────── GAP ────────────────┘
                       (FVG ZONE)

Requirements Met:
✓ Current LOW > 2-bar-ago HIGH (gap exists)
✓ Gap ≥ 30% of ATR (significant)
✓ Bar 1 range ≥ 1.8x average (impulse)
✓ Bar 1 body ≥ 65% of range (conviction)
✓ Bar 1 volume ≥ 2x average (institutional)
✓ Bar 1 was bullish (direction confirms)

RESULT: VALID SNIPER BULLISH ZONE CREATED
```

---

### Single Print Lines Explained

Single Prints mark **institutional impulse candles** where price moved so fast that no orders were filled at those levels. These levels often act as magnets for price.

```
SINGLE PRINT CANDLE:
════════════════════

                    HIGH ═══════════════════════════════ (Gold Line)
                      │
    ┌─────────────────┤
    │█████████████████│  ← Large body (65%+)
    │█████████████████│  ← Strong volume (2x+)
    │█████████████████│  ← Clear delta (60%+)
    │█████████████████│
    └─────────────────┤
                      │
                    LOW ═══════════════════════════════ (Gold Line)

These horizontal lines extend 500 bars into the future.
Price often returns to test these levels.
```

---

### Entry Strategy

#### Zone Entry Checklist
```
□ Zone is active (green/red, not gray)
□ Price enters zone from outside
□ Wait for entry signal (BUY🎯 or SELL🎯)
□ Verify: Delta + Volume confirming
□ Enter at CE line (dotted white line)
□ Stop below/above zone
□ Target: Opposite side of zone (1:1) or 2:1
```

#### Single Print Entry
```
□ Price returns to single print level
□ Look for reaction (rejection candle)
□ Combine with GRA signal if possible
□ Enter on confirmation candle
□ Stop beyond the single print line
```

---

### Table Legend

| Field | Reading | Color Meaning |
|-------|---------|---------------|
| **Delta** | Buy/Sell % | 🟢 Buy dom, 🔴 Sell dom, ⚪ Neutral |
| **Vol** | Volume ratio | 🟢 ≥2x, ⚪ <2x |
| **Buy ⬚** | Active buy zones | Count of bullish zones |
| **Sell ⬚** | Active sell zones | Count of bearish zones |
| **Zone** | Current position | AT BUY / AT SELL / --- |
| **Impulse** | Current bar status | 🟡 Yes (impulse), ⚫ No |

---

### Zone States

| State | Visual | Meaning | Action |
|-------|--------|---------|--------|
| **Fresh** | Bright color | Never tested | Best entries |
| **Tested** | Gray | CE touched | Still valid, less reliable |
| **Broken** | Dark gray | Price closed through | Invalid, ignore |

---

### Integration with GRA v5

The magic happens when you combine both indicators:

```
HIGHEST PROBABILITY SETUP:
══════════════════════════

1. DeepFlow shows active zone (green/red box)
2. Price enters the zone
3. GRA5 fires a signal INSIDE the zone
4. Delta confirms on both indicators
5. Volume confirms on both indicators

This is your SNIPER entry. Take it.

Example:
┌─────────────────────────────────────────┐
│  Price enters BULLISH zone              │
│  GRA5 shows: A🎯 LONG                   │
│  DFZ shows: BUY🎯                       │
│  Table: Vol 2.1x, Delta 67%B            │
│                                         │
│  ACTION: Full size LONG at CE           │
│  STOP: Below zone bottom                │
│  TARGET: 2:1 R:R                        │
└─────────────────────────────────────────┘
```

---

### Settings by Instrument

| Instrument | Vol Mult | Gap ATR | Impulse | Max Zones |
|------------|----------|---------|---------|-----------|
| **NQ/ES** | 2.0x | 30% | 1.8x | 10 |
| **YM** | 2.0x | 30% | 1.8x | 10 |
| **GC** | 2.5x | 40% | 2.0x | 8 |
| **BTC** | 2.0x | 25% | 1.5x | 10 |

---

### Common Mistakes

| Mistake | Why It's Bad | Solution |
|---------|-------------|----------|
| Trading every zone | Most zones fail | Wait for entry signal |
| Entering at zone edge | Wrong R:R | Enter at CE (middle) |
| Ignoring broken zones | Already invalidated | Gray = don't trade |
| No delta confirmation | Could be false zone | BUY🎯/SELL🎯 required |
| Too many zones | Chart noise | Max 10 zones |

---

### Alert Configuration

| Alert | Priority | Action |
|-------|----------|--------|
| 🎯 BUY/SELL ZONE ENTRY | 🔴 High | Check chart immediately |
| NEW BULL/BEAR ZONE | 🟠 Medium | Note new zone location |
| 🎯 SINGLE PRINT | 🟢 Low | Mark potential S/R |

---

### Pine Script v6 Notes

This indicator uses Pine Script v6 features:
- Array-based zone management
- `request.security_lower_tf()` for delta
- Dynamic zone state tracking
- Efficient garbage collection

**Minimum TradingView Plan:** Pro (for intrabar data)

---

## 🏆 Golden Rules

1. **Fewer zones = Better zones.** If you see more than 5 active zones, your settings are too loose.

2. **Fresh zones > Tested zones.** The first touch is always the best.

3. **CE is king.** The middle of the zone (50% level) is your entry point.

4. **Zone + GRA signal = Sniper entry.** This confluence is what we're hunting for.

5. **Gray zones don't exist.** Once broken, pretend the zone was never there.

---

*© Alexandro Disla - DeepFlow Zones SNIPER*
*Pine Script v6 | TradingView*
