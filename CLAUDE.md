# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a **PineScript v6** indicator repository for TradingView, targeting CME/CBOT futures markets (ES, NQ, YM, RTY, CL, GC, ZB, ZN, 6E). All scripts are deployed directly to TradingView — there is no local build, lint, or test toolchain.

## Active Scripts

| File | Description |
|---|---|
| `DeepFlow_v1.pine` | Order flow analytics using `request.footprint()` — requires TradingView Premium/Ultimate |
| `DeepFlow_v2.pine` | Standard edition redesign using `request.security_lower_tf()` — works on any TradingView plan |
| `SNIPER_ORB_v4.pine` | Opening Range Breakout with session killzones, FVG/iFVG zones, and VWAP |

The `legacy/` folder contains older indicator versions and their documentation. New development happens on the active scripts above.

## Code Architecture

### DeepFlow Structure (v1 & v2)

Both DeepFlow scripts follow a numbered section layout:
- **Section 0**: Color constants (DeepCharts® dark-mode palette — shared across all scripts)
- **Section 1**: All `input.*` declarations, organized by module group string
- **Sections 2+**: Module logic (CVD Engine, Big Trades, Exhaust/Absorb, IVB, FVG/IFVG, VP S/R)

Each module has a corresponding `input.bool` toggle under `GRP_MOD` that gates its execution.

### DeepFlow v2 Delta Engine

v2 reconstructs buy/sell volume without tick data by fetching intrabar candles via `request.security_lower_tf()`. Auto LTF selection: Weekly→60min, Daily→5min, 4H/1H→1min. If no intrabars are available, falls back to Chaikin MFM.

Classification methods (user-selectable):
- **Buying/Selling Pressure** (default): `(close-low) > (high-close)` → BUY
- **Polarity**: `close > open` → BUY

### Shared Color Palette

All scripts use the same DeepCharts® color constants (prefixed `C_`). When adding visual elements, reuse these rather than defining new colors:
- `C_BUY` / `C_SELL` — aggressive buy/sell signals
- `C_POC` — Point of Control (orange)
- `C_VA` — Value Area bounds (blue)
- `C_FVG_BULL` / `C_FVG_BEAR` — Fair Value Gaps
- `C_IFVG` — Inverse FVG (purple)
- `C_IVB` / `C_IVB_BREAK` — Initial Volume Balance / breakout

## PineScript Conventions

- Version declaration: `//@version=6` at top of every script
- `indicator()` call uses `overlay=true` and sets `max_boxes_count`, `max_labels_count`, `max_lines_count` to 500 and `max_bars_back` to 5000
- Input groups use descriptive emoji-prefixed strings (`"⚙️ General — Footprint Engine"`)
- Persistent state uses `var` declarations
- `request.security_lower_tf()` returns arrays; iterate with `array.size()` / `array.get()`

## Deployment

Copy script contents and paste into TradingView Pine Editor → Save → Add to Chart. v1 requires Premium/Ultimate subscription for `request.footprint()` access. v2 and SNIPER_ORB work on any plan.