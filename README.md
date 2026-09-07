# Praxis — reproductions

**Re-run our exact validations of published quant-research strategies — from public data only.** Five audits are open here; the rest are Praxis Pro, opened from the library. No account, no paid feeds, nothing to trust on faith. Each notebook rebuilds the data, runs the paper's strategy, and prints **claimed → measured** so you can check the alpha yourself.

This is [Praxis](https://market-graphs.com/praxis): not a strategy to trade — a **reproducible audit** of whether the alpha is real.

| Paper | Field | Verdict | Reproduce |
|---|---|---|---|
| **The Volatility Edge** — A Dual Approach for VIX ETNs Trading (2025) | Volatility | 🟢 Validated (~0.9, not the 1.0 headline) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/372649-the-volatility-edge.ipynb) |
| **Diversified reward-risk parity** in portfolio construction (2021) | Equities | 🟡 Overstated (replicates; the +48bp edge is noise, t = 0.69) | Praxis Pro — [members only](https://market-graphs.com/praxis/library) |
| **Lazy Factor and Probability Weighting** — gold/Bitcoin mean-variance (2023) | Cross-asset | 🔴 Fails (claimed $136,216 is arithmetically impossible; honest run $4,374) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/360760-gold-btc-lazy-factor.ipynb) |
| **Trend-Following via Dynamic Momentum Learning** — DMA/DMS futures trend (2021) | Futures | 🟡 Overstated (mechanics replicate incl. the 2009 crash-dodge; the +0.42 Sharpe lift measures +0.27 at t = 0.85 and reverses post-publication) | Praxis Pro — [members only](https://market-graphs.com/praxis/library) |
| **Network Momentum across Asset Classes** — graph-learning cross-asset momentum (2023) | Cross-asset futures | 🟡 Overstated (Sharpe 1.51 → 0.62; the network edge over individual momentum is +0.58 but insignificant, and a plain 12-month trend rule 0.80 beats the graph model) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/361154-network-momentum.ipynb) |
| **Trading with the Momentum Transformer** — attention-LSTM deep momentum network, cross-asset futures (2022) | Cross-asset futures | 🔴 Fails (Sharpe 2.54 → 0.13; its own LSTM benchmark measures −0.09, a plain 12-month trend rule 0.52, and breakeven cost is 0.14bps against a 1–3bps market) | Praxis Pro — [members only](https://market-graphs.com/praxis/library) |
| **Trading Signals In VIX Futures** — curve-state expected-utility signal (2021) | Volatility | 🟡 Overstated (mean fold Sharpe 4.53 → 1.58; the 5×550 network approximates a closed form, and the edge dies on the paper's own 20bps) | Praxis Pro — [members only](https://market-graphs.com/praxis/library) |
| **Downside Risk Reduction Using Regime-Switching Signals** — statistical jump-model regime timing on the S&P 500, DAX and Nikkei 225 (2024) | Equity indices (US · Germany · Japan) | 🔴 Fails (S&P Sharpe 0.68 → 0.50 = buy-and-hold's 0.50; a constant mix at its own exposure ties it, a 200-day moving average beats it; DAX worse than the index, Nikkei direction only, p = 0.23) | Praxis Pro — [members only](https://market-graphs.com/praxis/library) |
| **Quantitative Investment Diversification Strategies via Various Risk Models** — 3×3 covariance/optimizer grid, US equities (2024) | Equities (US industries) | 🟡 Overstated (Sharpe 1.04 → 0.60; statistically real but ~2× overstated, and the claimed +41.8%/yr excess measures +9.6% — FF3 α≈0, R²=0.95: closet market-beta) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/363172-risk-model-diversification.ipynb) |

Full reports & methodology: **https://market-graphs.com/praxis**


**Data note (363490):** the jump-model notebook ships the exact public total-return index and bill series it was validated on (`363490-data/`, sha256 in `MANIFEST.json`: S&P 500 = the real total-return index from 1988 with Shiller's dividends accrued onto the price index before that; DAX = the performance index; Nikkei 225 = price index plus a documented dividend-yield proxy; bills from FRED/OECD/IMF), so it lands on the report's numbers to the decimal.

**Data note:** the 358121 notebook ships a frozen snapshot of Cboe's own public VIX-futures
settlements (`358121-vx-data/`, checksummed) so it lands on the published numbers without
re-hitting Cboe; set `REFETCH` in the notebook to pull live and diff. Three other notebooks
(361154, 361025, 359741) consume panels built from licensed
Databento (CME/ICE) data, which is not redistributed here — [REBUILD.md](REBUILD.md)
specifies them exactly so you can rebuild under your own Databento entitlement.

*Same public data and logic as our engine — these land on our exact published numbers. The notebooks run the headline claimed → measured; the full C0–C7 gate suite lives in the reports.*
