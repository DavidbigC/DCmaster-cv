# Hyperliquid Vol & Options Strategy Research

**My role [Mine]:** my strategy questions (how to hedge a short strangle, when a breakout is fake, which strikes and DTEs to sell) and the decisions taken from the results; the backtests, optimisation and ML were run by AI agents (Apr 2026) [Directed].

**Type:** Quantitative options and volatility research project
**Stack:** Python, Numba, Optuna, DuckDB, PyArrow / Parquet, pandas, NumPy, Streamlit, Matplotlib, Binance Futures API, Hyperliquid tick archive, crypto_options_agg API

---

## Research Conducted

- Short-strangle strategy research with perpetual-futures delta-hedging across 15,000+ parameter combinations (strike distance, DTE, hedge mode, buffer, cooldown, bounce thresholds)
- Directional momentum strategy: 12h return breakout with 6h acceleration filter, realized vol threshold gating, persistence filtering; 89-trade backtest over 13 months, 67.4% win rate, Sharpe 4.58
- Systematic comparison of hedge policies: fake-breakout confirmation vs. preemptive vs. standard immediate — fake mode achieves ~3.66 Sharpe vs. 0.16 for immediate mode
- Regime detection: efficiency ratio, chop score, path length, trend strength used to classify market windows and switch strategy parameters dynamically
- Microstructure feature engineering from Hyperliquid tick data: signed relative trade flow, open pressure, block concentration z-scores (TWAP share, block share over 24h windows)
- Options APR surface analysis: live bid prices across strikes and DTEs from crypto_options_agg; asymmetric strike selection research
- Volatility forecasting research: HAR-RV model family (HAR-RV, HAR-RV-J with bipower variation, HARQ with realized quarticity, HAR-IV with DVol); VRP dynamics and IV–RV spread as primary options edge signal
- Markov-switching HAR and regime-switching vol models; DVol term structure shape, skew steepness, and funding rate divergence as regime transition features
- Tail risk research for short-strangle books: quantile regression for breach probability, realized semivariance (upside/downside decomposition), conditional density forecasting
- XGBoost / gradient-boosted trees on rich vol feature sets (lagged RV, IV level, skew, term structure, funding, jump indicators) as complement to HAR baseline

## Methods and Tooling

- Multi-objective Bayesian optimization (Optuna NSGA-II) — Pareto frontier across Sharpe × net P&L × Calmar; 5,000–20,000 trials per run; v1 TPE sampler, v2 NSGA-II genetic algorithm
- Random Forest (sklearn, 400 estimators, OOB scoring) for strategy performance prediction from 14+ parameter features; permutation importance ranking; multi-round iterative candidate proposal loop
- Regime classification: 4-state labels (volatile whipsaw, breakout trend, quiet chop, quiet drift) fitted with quantile thresholds on realized vol, efficiency ratio, chop score; per-regime policy selection on holdout set
- Bootstrap / Monte Carlo resampling for strategy risk metrics (p5 PnL, p95 drawdown, p5 win rate)
- Hedge policy scoring: 10 variants evaluated via weighted z-score composite (Sharpe + avg net − loss − crossings)
- Numba JIT-compiled simulation engines for sub-millisecond backtest execution
- Walk-forward train/test splits; OOB R² and permutation importance for model evaluation
- DuckDB analytical views over multi-gigabyte Parquet datasets (Hyperliquid S3 tick archives, ~18.7M ETH trades)
- GPU-accelerated ML stack (XGBoost CUDA, PyTorch CUDA, Numba JIT) on remote RTX 3070 via SSH

## Key Findings

- Fake-breakout confirmation filtering (wait for confirmed move beyond buffer for N seconds) reduces crossing frequency 100×+ while preserving profitable trend capture
- Asymmetric strikes outperform symmetric: near-ATM calls (+$100–$300) collect real premium; far OTM puts (−$500) near-zero cost due to ETH negative skew
- 7-DTE is the risk-adjusted optimum; shorter DTEs have zero OTM bids, longer DTEs collect less premium per unit of risk
- Cooldown periods of 250–600s between hedge re-entries prevent whipsaw losses
- Bounce gating (4–10 price contests minimum) validates a level as genuinely contested

## Data

- Hyperliquid S3 tick archive: ETH/BTC/SOL, ~9 months, ~18.7M ETH trades
- Binance Futures 1h OHLCV (ETH/BTC perpetuals, back to 2023-01-01) + funding rates

## Tags

quantitative options research · vol strategy backtesting · delta-hedging via perpetuals · Bayesian optimization · regime detection · microstructure analysis · Hyperliquid data · ML strategy search
