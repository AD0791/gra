# DeepFlow v2.0 — Order Flow Analytics (Standard Edition)

## Overview

DeepFlow v2.0 delivers professional-grade order flow analytics on any TradingView plan — no Premium or tick data subscription required. It reconstructs buy/sell volume by fetching intrabar candles via `request.security_lower_tf()` and classifying each one directionally.

This edition is focused on three high-signal modules: **Big Trades**, **Exhaustion**, and **Absorption** — the three patterns that reveal institutional intent most clearly on CME/CBOT futures.

**Target markets:** CME/CBOT Futures — ES, NQ, YM, RTY, CL, GC, ZB, ZN, 6E

---

## Architecture

### Intrabar Delta Engine

The engine fetches lower-timeframe candles within each chart bar and classifies each one as buy or sell. Three LTF options are available:

| Option | Description                                     | Best For     |
|--------|-------------------------------------------------|--------------|
| `Auto` | Selects 1S for ≤5m charts, 1 for longer         | Default      |
| `1T`   | 1-tick (most precise, very resource-intensive)  | Tick charts  |
| `1S`   | 1-second (60–300 intrabars per bar)             | 1m–5m charts |
| `1`    | 1-minute                                        | 15m+ charts  |

**Classification methods:**

- **Buying/Selling Pressure** (recommended): `(close-low) > (high-close)` → BUY. Measures close position within the bar's range. More accurate on futures.
- **Polarity**: `close > open` → BUY. Simpler, slightly less accurate.

**Fallback — Chaikin MFM:** When intrabars are unavailable (first bars, data gaps), the engine falls back to Marc Chaikin's Money Flow Multiplier:

```text
MFM     = [(close - low) - (high - close)] / (high - low)
buyVol  = volume × (1 + MFM) / 2
sellVol = volume × (1 - MFM) / 2
```

---

## Responsive Rendering

All visual elements reposition automatically on zoom, scroll, and toggle:

| Element           | Mechanism                                                                 |
|-------------------|---------------------------------------------------------------------------|
| Big Trade labels  | `yloc.belowbar` / `yloc.abovebar` — tracks bar extremes at any zoom level |
| EXH / ABS signals | `plotshape` — TradingView positions natively, scales with chart           |
| Delta bar color   | `barcolor()` — always in sync with current bar                            |

Toggling a module removes all its markers cleanly because PineScript recalculates the entire script from scratch on any input change.

---

## Modules

### [1] Big Trades Detection

Identifies bars where institutional-scale volume traded with strong directional conviction. Two conditions must be met simultaneously:

1. `volume > mean + k × stddev` — statistical volume anomaly
2. `|delta%| > 30%` — directional conviction (filters out high-volume chop)

Labels appear directly above or below the bar (using `yloc.abovebar` / `yloc.belowbar`) showing the volume multiple, e.g., `2.3× vol`. They track bar extremes at any zoom level.

| Color        | Meaning                               |
|--------------|---------------------------------------|
| Cyan label   | Big Buy (institutional accumulation)  |
| Orange label | Big Sell (institutional distribution) |

**Settings:**

| Parameter            | Default | Description                                           |
|----------------------|---------|-------------------------------------------------------|
| Statistical Lookback | 50      | Bars used to compute mean and standard deviation      |
| Std Dev Multiplier   | 2.0     | `1.5` = more signals · `3.0` = fewest, strongest only |

---

### [2] Exhaustion

**Definition:** Large delta but tiny price range relative to ATR.

Aggressive participants pushed volume hard into the market but barely moved price. A passive wall absorbed the aggression — exhaustion of the active side.

**Signals:**

| Marker                          | Meaning                                                      |
|---------------------------------|--------------------------------------------------------------|
| `EXH` circle above bar (yellow) | Buy Exhaustion — heavy buying hit a wall, potential top      |
| `EXH` circle below bar (yellow) | Sell Exhaustion — heavy selling hit a wall, potential bottom |

**Detection logic:**

```text
|delta|   > avgAbsDelta × DeltaThreshold
barRange  < ATR × MaxPriceMove
volume    > avgVolume × 1.1
```

---

### [3] Absorption

**Definition:** Price direction contradicts delta direction.

The passive side silently absorbed all aggression from the active side. Price closed in the "wrong" direction relative to delta — a reliable leading reversal signal.

**Signals:**

| Marker                                 | Meaning                                                                               |
|----------------------------------------|---------------------------------------------------------------------------------------|
| `ABS` triangle-up below bar (teal)     | Bull Absorption — red candle, positive delta → hidden buying, likely reverses up      |
| `ABS` triangle-down above bar (purple) | Bear Absorption — green candle, negative delta → hidden selling, likely reverses down |

**Detection logic:**

```text
Bull: close < open  AND  delta >  avgAbsDelta × DeltaThreshold  AND  volSignificant
Bear: close > open  AND  delta < -avgAbsDelta × DeltaThreshold  AND  volSignificant
```

**Settings (shared with Exhaustion):**

| Parameter                           | Default | Description                                           |
|-------------------------------------|---------|-------------------------------------------------------|
| Delta Threshold (× avg)             | 1.8     | Minimum delta relative to average to qualify a signal |
| Exhaustion: Max Price Move (× ATR)  | 0.4     | Max bar range as a fraction of ATR (exhaustion only)  |
| ATR Length                          | 14      | Lookback for ATR calculation                          |

---

## Bar Coloring

Bars are shaded by delta intensity. The color saturation scales with `|delta| / avg_delta`:

- **Green tint** — positive delta (more buying pressure)
- **Red tint** — negative delta (more selling pressure)
- Stronger delta → more vivid color; near-zero delta → near-transparent

---

## Deployment

1. Copy the full script contents from `DeepFlow_v2.pine`
2. Open TradingView Pine Editor
3. Paste → Save → Add to Chart
4. Works on **any TradingView plan** — no Premium required

**Recommended timeframes:** 1m, 5m, 15m, 1H (intraday scalping / day trading)

**Recommended markets:** ES, NQ, YM, RTY (index futures) · CL, GC (commodities) · ZB, ZN (bonds)

---

## Input Reference

### ⚙️ Intrabar Delta Engine

| Input                | Default                  | Options                                  |
|----------------------|--------------------------|------------------------------------------|
| Lower Timeframe      | Auto                     | Auto · 1T · 1S · 1                       |
| Delta Classification | Buying/Selling Pressure  | Buying/Selling Pressure · Polarity       |

### 🔌 Module Toggles

| Input                   | Default |
|-------------------------|---------|
| Big Trades Detection    | On      |
| Exhaustion / Absorption | On      |

### 🐋 Big Trades Detection

| Input                | Default | Range     |
|----------------------|---------|-----------|
| Statistical Lookback | 50      | 10 – 300  |
| Std Dev Multiplier   | 2.0     | 1.0 – 5.0 |

### ⚡ Exhaustion / Absorption

| Input                              | Default | Range      |
|------------------------------------|---------|------------|
| Delta Threshold (× avg)            | 1.8     | 1.0 – 5.0  |
| Exhaustion: Max Price Move (× ATR) | 0.4     | 0.05 – 1.0 |
| ATR Length                         | 14      | 5 – 50     |

---

## Alerts

| Alert               | Trigger                                     |
|---------------------|---------------------------------------------|
| Big Buy             | Institutional-scale buy bar detected        |
| Big Sell            | Institutional-scale sell bar detected       |
| Buy Exhaustion      | Heavy buying hit a wall — potential top     |
| Sell Exhaustion     | Heavy selling hit a wall — potential bottom |
| Bullish Absorption  | Hidden buy pressure under red bar           |
| Bearish Absorption  | Hidden sell pressure under green bar        |
