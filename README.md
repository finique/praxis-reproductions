# Praxis — reproductions

**Re-run our exact validations of published quant-research strategies — from public data only.** No account, no paid feeds, nothing to trust on faith. Each notebook rebuilds the data, runs the paper's strategy, and prints **claimed → measured** so you can check the alpha yourself.

This is [Praxis](https://market-graphs.com/praxis): not a strategy to trade — a **reproducible audit** of whether the alpha is real.

| Paper | Field | Verdict | Reproduce |
|---|---|---|---|
| **The Volatility Edge** — A Dual Approach for VIX ETNs Trading (2025) | Volatility | 🟢 Validated (~0.9, not the 1.0 headline) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/372649-the-volatility-edge.ipynb) |
| **Diversified reward-risk parity** in portfolio construction (2021) | Equities | 🟡 Overstated (replicates; the +48bp edge is noise, t = 0.69) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/359491-reward-risk-parity.ipynb) |
| **Lazy Factor and Probability Weighting** — gold/Bitcoin mean-variance (2023) | Cross-asset | 🔴 Fails (claimed $136,216 is arithmetically impossible; honest run $4,374) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/360760-gold-btc-lazy-factor.ipynb) |
| **Trend-Following via Dynamic Momentum Learning** — DMA/DMS futures trend (2021) | Futures | 🟡 Overstated (mechanics replicate incl. the 2009 crash-dodge; the +0.42 Sharpe lift measures +0.27 at t = 0.85 and reverses post-publication) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/358063-futures-dynamic-momentum.ipynb) |
| **Network Momentum across Asset Classes** — graph-learning cross-asset momentum (2023) | Cross-asset futures | 🟡 Overstated (Sharpe 1.51 → 0.62; the network edge over individual momentum is +0.58 but insignificant, and a plain 12-month trend rule 0.80 beats the graph model) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finique/praxis-reproductions/blob/main/361154-network-momentum.ipynb) |

Full reports & methodology: **https://market-graphs.com/praxis**

*Same public data and logic as our engine — these land on our exact published numbers. The notebooks run the headline claimed → measured; the full C0–C7 gate suite lives in the reports.*
