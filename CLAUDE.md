# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a **PineScript v6** indicator repository for TradingView, targeting CME/CBOT futures markets (ES, NQ, YM, RTY, CL, GC, ZB, ZN, 6E). All scripts are deployed directly to TradingView — there is no local build, lint, or test toolchain.

## Active Scripts

| File | Description |
|---|---|
| `DeepFlow_v1.pine` | Full order flow analytics using `request.footprint()` — requires TradingView Premium/Ultimate |
| `DeepFlow_v2.pine` | Standard edition using `request.security_lower_tf()` — works on any TradingView plan |
| `DeepFlow_v3.pine` | Strategy version with asset presets (MYM/MGC/MNQ) and institutional calibration |
| `leg_profile.pine` | Structural leg profiler — builds volume profiles within ATR-based swing legs (LuxAlgo, MPL-2.0) |

The `legacy/` folder contains older indicator versions and their documentation. New development happens on the active scripts above.

## Deployment

Copy script contents and paste into TradingView Pine Editor → Save → Add to Chart. v1 requires Premium/Ultimate for `request.footprint()`. v2/v3 and leg_profile work on any plan.

## Code Architecture

### Numbered Section Layout

All DeepFlow scripts share a consistent numbered section structure:
- **Section 0**: `var color C_*` constants (DeepCharts® dark-mode palette)
- **Section 1**: All `input.*` declarations grouped by `GRP_*` string constants
- **Sections 2+**: Module logic, each gated by an `input.bool` toggle in `GRP_MOD`

`leg_profile.pine` follows the same input group convention but uses three top-level sections (swing detection, profile building, rendering).

### Delta Engine — Three Generations

**v1** uses `request.footprint()` directly, returning a footprint object with `.buy_volume()`, `.sell_volume()`, `.delta()`, `.poc()`, `.vah()`, `.val()` methods. Falls back to `(close-low)/(high-low) × volume` heuristic when footprint data is unavailable.

**v2** reconstructs delta without tick data via `request.security_lower_tf()`. Auto LTF selection: Weekly→60min, Daily→5min, 4H/1H→1min, ≤5min→1sec. Falls back to Chaikin MFM when no intrabars exist. Two user-selectable classification methods:
- **Buying/Selling Pressure** (default): `(close-low) > (high-close)` → BUY
- **Polarity**: `close > open` → BUY

**v3** uses a `get_delta()` function with cascading priority: primary resolution (1T/1S/1min) → 1-minute fallback → Chaikin MFM. Applies asset-specific sigma/body multipliers (Gold: `σ×1.15`, Nasdaq: `σ×0.9`, Dow: `σ×1.0`) before signal detection.

### Signal Detection Pattern

All three versions share a common statistical pattern for every signal type:

```pinescript
float avg = ta.sma(metric, lookback)[1]   // [1] = previous bar stats
float std = ta.stdev(metric, lookback)[1]
float threshold = avg + multiplier * std
bool signal = metric > threshold and confirmationCondition
```

The `[1]` offset prevents lookahead bias. Confirmation conditions vary: exhaustion requires small body (`barRange < ATR × factor`), absorption requires directional mismatch between price move and delta.

### Module Toggles

Every module in DeepFlow v1/v2 has an `i_show*` input.bool under `GRP_MOD`. Wrap all module logic in `if i_showXxx` to keep disabled modules from consuming execution time.

### Visual Object Management

Labels, boxes, and lines are tracked in `var array<label/box/line>` arrays. Pattern for bounded memory:

```pinescript
var array<label> myLabels = array.new<label>()
// ... create label, push to array
if myLabels.size() > i_maxMarkers
    label.delete(myLabels.shift())
```

For objects that persist and update in-place (e.g., Big Trades labels in v2), use `var label lastBuyBT = na` and redraw on the same bar before creating a new one.

### Custom Types (v1 and leg_profile)

v1 defines `FVGZone` (box + price bounds + fill state) and `NakedPOC` (price + line). `leg_profile.pine` defines `LTFBar` (intrabar OHLCV + classified buy/sell), `CandleProfile` (volume distribution matrix + POC), and `UntestedPOC` (forward-extended POC line + expiration).

### Shared Color Palette

All scripts reuse `C_*` constants. When adding visual elements, pull from these rather than defining new colors:

| Constant | Use |
|---|---|
| `C_BUY` / `C_SELL` | Buy/sell signals, bar coloring, delta direction |
| `C_POC` | Point of Control (orange) |
| `C_VA` | Value Area bounds (blue) |
| `C_FVG_BULL` / `C_FVG_BEAR` | Fair Value Gap boxes |
| `C_IFVG` | Inverse FVG (purple) |
| `C_IVB` / `C_IVB_BREAK` | Initial Volume Balance / breakout |
| `C_DASH_BG` / `C_DASH_TXT` | Dashboard table background / text |

## PineScript Conventions

- Every script starts with `//@version=6`
- `indicator()` uses `overlay=true, max_boxes_count=500, max_labels_count=500, max_lines_count=500, max_bars_back=5000`; `strategy()` (v3) drops `max_bars_back` and adds `initial_capital` / `default_qty_*`
- Input groups are `string` constants with emoji-prefixed names: `GRP_GEN = "⚙️ General — Footprint Engine"`
- All input variable names are prefixed `i_`
- Persistent state always uses `var`; never use bare `float`/`int`/`array` declarations for state that must survive across bars
- `request.security_lower_tf()` returns arrays — always check `.size() > 0` before accessing elements
- Bar coloring goes at the very end: `barcolor(delta > 0 ? C_BUY : delta < 0 ? C_SELL : na)`
- `alertcondition()` declarations close every script, one per signal type
