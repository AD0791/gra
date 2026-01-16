# SNIPER AMT Playbook - Quick Reference Guide

## Based on Fabio Valentini's Auction Market Playbook

---

## 🎯 THE CORE PRINCIPLE

**Three elements must align for every trade:**

| Step | Question | Tool |
|------|----------|------|
| **1. Market State** | Is market balanced or imbRUSSELLalanced? | Balance detection |
| **2. Location** | Where are the LVNs and POC? | Volume profile proxy |
| **3. Aggression** | Is there order flow confirmation? | Candle + volume analysis |

**If ANY element is missing → NO TRADE**

---

## 📊 INDICATOR #1: MR SNIPER (Mean Reversion)

### When to Use
- Market is **IN BALANCE** (ranging, consolidating)
- Price **breaks out but FAILS** to hold
- **London session** or compressed summer conditions
- Failed breakouts returning to value

### The Setup Sequence

```
1. BALANCE DETECTED
   └── Price rotating around POC
   
2. BREAKOUT ATTEMPT
   └── Price pushes beyond Value Area
   
3. FAILURE + RECLAIM ← KEY MOMENT
   └── Price comes BACK inside balance
   └── DO NOT trade first move back!
   
4. PULLBACK INTO LVN
   └── Wait for pullback after reclaim
   
5. AGGRESSION CONFIRMATION
   └── Entry candle shows buy/sell pressure
   └── Volume elevated (1.2×+ average)
   └── Fat body (60%+ of range)
   
6. ENTRY → TARGET: POC
```

### Signal Labels
- **MR↑** = Mean Reversion Long (failed breakdown)
- **MR↓** = Mean Reversion Short (failed breakout)
- **S/A/B** = Signal quality tier

### Risk Management
- **Stop**: Below recent low (long) / Above recent high (short)
- **Target**: POC (center of value)
- **Risk**: 0.25-0.5% per trade

---

## 📊 INDICATOR #2: TC SNIPER (Trend Continuation)

### When to Use
- Market is **OUT OF BALANCE** (trending, momentum)
- Clear **displacement** away from prior value
- **New York session** (AVOID London open fakeouts!)
- Strong directional moves with follow-through

### The Setup Sequence

```
1. IMPULSE DETECTED
   └── Strong directional move (2× ATR+)
   └── Multiple momentum bars
   └── Price above/below fast EMA
   
2. LVN ZONE IDENTIFIED
   └── 23.6% - 61.8% Fibonacci retracement
   └── Low volume pullback area
   
3. PRICE PULLS BACK TO LVN
   └── Retraces into the zone
   └── Volume decreases (exhaustion)
   
4. AGGRESSION CONFIRMATION
   └── Entry candle in trend direction
   └── Volume spikes (1.3×+ average)
   └── Fat body, minimal adverse wick
   └── EMA alignment confirms trend
   
5. ENTRY → TARGET: PREV POC
```

### Signal Labels
- **TC↑** = Trend Continuation Long
- **TC↓** = Trend Continuation Short
- **S/A/B** = Signal quality tier

### Risk Management
- **Stop**: Below LVN zone (long) / Above LVN zone (short)
- **Target**: Previous balance POC
- **Risk**: 0.25-0.5% per trade

---
TC SNIPER (Trend Continuation)

### When to Use
- Market is **OUT OF BALANCE** (trending, momentum)
- Clear **displacement** away from prior value
- **New York session** (AVOID London open fakeouts!)
- Strong directional moves with follow-through

### The Setup Sequence

```
1. IMPULSE DETECTED
   └── Strong directional move (2× ATR+)
   └── Multiple momentum bars
   └── Price above/below fast EMA
   
2. LVN ZONE IDENTIFIED
   └── 23.6% - 61.8% Fibonacci retracement
   └── Low volume pullback area
   
3. PRICE PULLS BACK TO LVN
   └── Retraces into the zone
   └── Volume decreases (exhaustion)
   
4. AGGRESSION CONFIRMATION
   └── Entry candle in trend direction
   └── Volume spikes (1.3×+ average)
   └── Fat body, minimal adverse wick
   └── EMA alignment confirms trend
   
5. ENTRY → TARGET: PREV POC
```
## 🔧 CHART SETUP FOR MINIMAL CLUTTER

### Recommended Layout

```
INDICATOR STACK (top to bottom):
├── SNIPER ORB (your existing)
├── SNIPER IB (your existing)
├── TC SNIPER (new) ← For trending markets
└── MR SNIPER (new) ← For ranging markets

TABLE POSITIONS:
├── TC SNIPER table → Top Right
├── MR SNIPER table → Top Right (stacks below)
├── ORB/IB tables → Bottom Right (if any)
```

### Display Settings for Clean Charts

**MR SNIPER:**
- ✅ Show Signals Only = ON (minimal clutter)
- ✅ Show POC = ON (always need target)
- ❌ Show Balance Zone = OFF (unless analyzing)

**TC SNIPER:**
- ✅ Show LVN Zones = ON (entry areas)
- ✅ Show Prev POC = ON (target)
- Set Signal Lookback = 30 (or lower)

---

## ⚡ DECISION FLOWCHART

```
START: What is the market doing?

         ┌─────────────────┐
         │  ROTATING?      │
         │  (Balance)      │
         └────────┬────────┘
                  │ YES
                  ▼
         ┌─────────────────┐
         │  Use MR SNIPER  │
         │  Wait for       │
         │  failed breakout│
         └─────────────────┘

         ┌─────────────────┐
         │  TRENDING?      │
         │  (Imbalance)    │
         └────────┬────────┘
                  │ YES
                  ▼
         ┌─────────────────┐
         │  Use TC SNIPER  │
         │  Wait for       │
         │  LVN pullback   │
         └─────────────────┘
```

---

## 📅 SESSION GUIDE

| Session | Best Model | Why |
|---------|-----------|-----|
| **London (3-5 AM ET)** | MR SNIPER | Many fakeouts, mean reversion works |
| **NY Open (9:30-11:30 AM ET)** | TC SNIPER | Institutional volume, real trends |
| **Midday (12-2 PM ET)** | Either/Neither | Low volume, be selective |
| **Summer/Compressed** | MR SNIPER | Markets stay stuck in range |

---

## ✅ ENTRY CHECKLIST

### MR SNIPER Entry
- [ ] Market was in balance
- [ ] Breakout attempt occurred
- [ ] Breakout FAILED (price reclaimed)
- [ ] Waited for pullback (not first move!)
- [ ] Entry candle shows aggression
- [ ] Volume elevated
- [ ] Session filter passed
- [ ] Target = POC

### TC SNIPER Entry
- [ ] Impulse leg detected (momentum + displacement)
- [ ] Price in LVN pullback zone
- [ ] Entry candle shows aggression IN TREND DIRECTION
- [ ] Volume elevated
- [ ] EMAs aligned (if enabled)
- [ ] NOT during London open (avoid fakeouts)
- [ ] Target = Previous POC

---

## ⚠️ CRITICAL RULES

1. **No aggression = No trade** (both indicators)
2. **Never widen stops** - if wrong, be wrong immediately
3. **Risk 0.25-0.5%** per trade max
4. **Exit at POC** - don't stretch for more (70% reverses there)
5. **Multiple small stops are normal** - trust the process
6. **London = fakeouts** - prefer MR model or stay flat
7. **NY = real moves** - TC model shines here

---

## 🎯 SIGNAL QUALITY TIERS

| Tier | Aggression Score | Action |
|------|-----------------|--------|
| **S** | 5-6 points | Full confidence entry |
| **A** | 4 points | Standard entry |
| **B** | 3 points | Reduced size or skip |

---

*"The key is to only act when the market is giving you clear conditions."*
*— Fabio Valentini*

---

**Files:**
- `SNIPER_Mean_Reversion_v1.pine` - MR SNIPER indicator
- `SNIPER_Trend_Continuation_v1.pine` - TC SNIPER indicator
