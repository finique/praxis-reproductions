# Rebuilding the futures panels (361154, 361025)

Two notebooks in this repository consume reference panels built from **licensed
Databento market data** (CME Globex + ICE US). Licensed market data is not
redistributed here — the same line MarketGraphs holds everywhere: analytics and
code travel, data values do not. This page specifies the panels exactly, so a
reader with their own Databento subscription can rebuild them independently.
The pull that produced them cost only a few dollars of Databento credits.

MarketGraphs also delivers the panel-build adapter code itself to clients under
the integration tier — run against **your** entitlement, on your side, so no
data changes hands. Contact us via https://market-graphs.com/praxis.

## Source data (both panels)

| | |
|---|---|
| Vendor | Databento |
| Datasets | `GLBX.MDP3` (CME Globex) · `IFUS.IMPACT` (ICE US — the five softs) |
| Series type | Continuous futures with per-date instrument mapping (symbology → roll dates) |
| Bars | Daily (`ohlcv-1d`) |
| Window | 2010-06 → 2026-06 |
| Roll rules | Databento continuous-contract rule semantics: `c` calendar · `n` open interest · `v` volume |

**Roots pulled (41):**
commodity — CL, BZ, HO, NG, RB, GC, SI, HG, PL, PA, ZC, ZS, ZW, ZL, ZM, ZO, KE,
LE, GF, HE, LBS, LBR (lumber, old + current), KC, SB, CC, CT, OJ ·
equity — ES, NQ, YM · bonds — ZT, ZF, ZN, ZB · FX — 6E, 6J, 6B, 6A, 6C, 6S, 6N.

Vendor gotchas to expect: the calendar-rule series for PL and PA are sparse —
use the open-interest rule for those regardless of the panel's headline rule;
the ICE softs are available on the open-interest rule only; mixed trading
calendars mean holiday gaps should be forward-filled only within each
contract's live span.

## `361154-futures-panel.parquet` — roll-adjusted price panel

- Continuous series on the **open-interest roll rule (`n`)**.
- **Ratio back-adjustment** at every roll: the vendor splice is unadjusted (the
  price jumps by the term-structure gap at each roll), so multiply the
  pre-roll history by the ratio of both contracts' closes on the day **before**
  the roll — both closes always exist in the bars union, keyed by
  `instrument_id` from the symbology mapping. Adjusted returns are then what a
  rolled position actually earned.
- Output: **wide daily close panel** — `DatetimeIndex` named `date`
  (2010-06-07 → 2026-06-29, 4,996 rows) × **40 columns** of canonical asset
  names (e.g. `Light crude oil`, `Gold`, `S&P500`, `US Tsy 10y`, `EUR/USD`).
- Save as `361154-futures-panel.parquet` next to the notebook.

## `361025-commodity-curve-panel.parquet` — four-point commodity curves

- Continuous series on the **calendar roll rule (`c`)** at depths
  `c.0`–`c.3`: for each commodity and day, the nearest four calendar
  contracts.
- Output: **long format**, columns
  `date · commodity · depth · close · instrument_id · tau_years`
  (`depth` = 0–3 nearest-first; `tau_years` = time to maturity in years),
  commodity roots only, 2010-06 → 2026-06 (269,568 rows in the reference
  build).
- Save as `361025-commodity-curve-panel.parquet` next to the notebook.

Either notebook picks the file up from its own directory and reproduces the
published claimed → measured numbers deterministically.
