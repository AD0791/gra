# AMD FVG Trade Setup — Futures Calibration Guide

## Core Concept Refresher

The AMD cycle (Accumulation → Manipulation → Distribution) is engineered institutional behaviour. On micro futures it plays out fastest at session opens and the London/NY overlap. The indicator hunts for a tight consolidation zone, a sweep of that zone's extreme, then an FVG that confirms reversal intent.

---

## Instrument Profiles

### MNQ — Micro E-mini Nasdaq-100
| Parameter | Value | Rationale |
|---|---|---|
| Accumulation Length | 20 | NQ builds tight bases quickly; longer windows dilute the signal |
| Accumulation Range Max % | 0.15 | Nasdaq is volatile — demand a genuinely tight coil |
| Max Search Window | 10 | Manipulation sweeps resolve fast on NQ |
| Min FVG Gap (ATR ×) | 0.15 | Requires a visible gap; filters noise-wicks |
| ATR Length | 14 | Standard |
| ATR SL Multiplier | 1.5 | Tight enough to respect structure, not so tight it gets clipped |
| Reward-to-Risk | 2.5 | Higher RRR offsets the false-breakout rate on NQ |
| Best Sessions | NY (08:00–10:30), London/NY overlap (08:00–12:00) |

**Notes:** Run on 1-min or 3-min charts. The first 90 minutes of the NY session generate the cleanest AMD cycles. Avoid the 12:00–14:00 EST lull.

---

### MGC — Micro Gold
| Parameter | Value | Rationale |
|---|---|---|
| Accumulation Length | 30 | Gold builds deliberate bases; 30 bars captures a proper range |
| Accumulation Range Max % | 0.15 | Gold is precise — tight ranges precede clean moves |
| Max Search Window | 15 | Manipulation can take longer on Gold |
| Min FVG Gap (ATR ×) | 0.10 | Gold FVGs tend to be proportionally smaller |
| ATR Length | 14 | Standard |
| ATR SL Multiplier | 1.8 | Gold can reverse viciously; give the trade breathing room |
| Reward-to-Risk | 2.0 | Conservative; Gold trends strongly once it moves |
| Best Sessions | London open (03:00–08:00 EST), NY open overlap (08:00–10:00 EST) |

**Notes:** Run on 5-min charts. The London open is the premier session for Gold AMD setups. Ignore signals during the 12:00–14:00 EST consolidation window. Enable the London session toggle.

---

### MYM — Micro E-mini Dow Jones
| Parameter | Value | Rationale |
|---|---|---|
| Accumulation Length | 25 | Dow accumulates more slowly than NQ; 25 bars is the sweet spot |
| Accumulation Range Max % | 0.20 | Dow allows slightly wider ranges before a real sweep |
| Max Search Window | 12 | Moderate search window; Dow sweeps are deliberate |
| Min FVG Gap (ATR ×) | 0.10 | Standard threshold works well |
| ATR Length | 14 | Standard |
| ATR SL Multiplier | 1.5 | Dow is less spiky than NQ; tighter stop holds |
| Reward-to-Risk | 2.0 | Clean 2:1 suits Dow's smoother trend behaviour |
| Best Sessions | NY session (08:00–17:00 EST), avoid pre-market |

**Notes:** Run on 2-min or 5-min charts. Dow AMD setups are most reliable at the 09:30 and 10:30 NY inflection points. The indicator's default NY session toggle is correct for MYM.

---

## Timeframe Matrix

| Instrument | Primary TF | Secondary TF | Avoid |
|---|---|---|---|
| MNQ | 1 min | 3 min | > 15 min (signal too infrequent) |
| MGC | 5 min | 15 min | < 3 min (too much noise) |
| MYM | 2 min | 5 min | 1 min (Dow chops at micro scale) |

---

## Session Toggles by Instrument

| Instrument | Sydney | Tokyo | London | New York |
|---|---|---|---|---|
| MNQ | Off | Off | Optional | **On** |
| MGC | Off | Off | **On** | **On** |
| MYM | Off | Off | Off | **On** |

---

## Quick-Start Checklist

1. Set the timeframe per the matrix above.
2. Enable only the relevant session(s).
3. Enter the parameter values from the instrument table.
4. Verify the accumulation boxes are appearing on genuine tight ranges (not trending segments).
5. Back-test 10–15 recent setups before going live; adjust ATR multiplier ±0.2 to fit current volatility regime.
