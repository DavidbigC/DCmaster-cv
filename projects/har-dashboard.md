# HAR-RV Live Volatility Advisory System

**Type:** Live vol forecasting and options trading advisory platform
**Stack:** Python, FastAPI, APScheduler, DuckDB, TradingView Lightweight Charts (SPA frontend), Deribit API, Hyperliquid API, Binance API

---

## System Overview

- Continuously ingests multi-source market data and runs HAR-RV forecasting every 5 minutes
- Computes Variance Risk Premium (VRP = IV − forecast RV), evaluates regime conditions, and surfaces straddle/strangle trade recommendations via REST API to a live dashboard
- Running in production with APScheduler background jobs for candle ingestion, DVOL, full Deribit options chain snapshots, and derivatives metrics

## HAR-RV Forecasting

- Standard 1-step HAR-RV: `RV_{t+1} = β₀ + β_D × RV_t + β_W × avg(RV_{t-7}) + β_M × avg(RV_{t-30})`
- Monthly component dropped (t-stat ≈ 0 on crypto — crypto-specific calibration decision)
- Horizon-specific OLS fits for h ∈ {7, 14, 30} days; target = mean(RV over window), capturing mean-reversion at longer horizons
- Asset-specific fits on 733 days of BTC/ETH data:
  - BTC: β_D=0.35, β_W=0.44, β_M=0.0
  - ETH: β_D=0.40, β_W=0.29, β_M=0.0
- Pure Python linear algebra: Gauss elimination with partial pivoting + ridge regularization; returns β̂, standard errors, t-stats, R², RMSE
- HAR coefficient research: grid search over β and window-size spaces (~1,800 combinations), ranked by walk-forward Sharpe
- HAR-X funding extension: HAR augmented with Binance/Hyperliquid funding rate and premium features (researched, not yet live)

## Regime Detection

- 4-factor scoring: persistence score (7d mean RV / prior-month RV), spike score (today RV / 7d mean), IV slope (7d/30d tenor ratio), β_w structural break ratio (45d vs 90d window)
- 4 states: NORMAL, SPIKE, REGIME, AMBIGUOUS — each gates/modifies signals differently
- REGIME state: requires 1.5× VRP threshold for SHORT (premium compresses in high-vol regimes)
- SPIKE state: suppresses LONG signals (transient burst expected to mean-revert)
- HMM research documented for future deployment: 3–4 state Gaussian/Student-t HMM, Baum-Welch + Viterbi; `hmmlearn` / `pomegranate` candidates; not yet deployed

## Feature Set

**Realized vol inputs:**
- 1-min returns from Hyperliquid ETH/BTC perps, Deribit perps, Binance spot
- Days with <60 min data excluded (quality gate)
- Daily, 7-day rolling avg, 30-day rolling avg HAR components

**Implied vol inputs:**
- DVOL (Deribit 30-day vol index), ATM IV by tenor (7d/14d/30d expiries from live options chain)
- IV slope (7d/30d ratio), IV z-scores (7d and 30d rolling vs 90-day baseline)

**Derivatives features:**
- Binance USDM: funding rate, open interest, basis, taker buy/sell ratio, global long/short account ratio
- Hyperliquid: funding rate, premium, mark/oracle/mid prices, daily notional volume, impact bid/ask

## Backtesting

- Walk-forward: weekly entry points from (start + 30d) to (now − horizon)
- Separate LONG vs SHORT win rate and avg PnL per horizon
- Advisor auto-selects best horizon {7/14/30} by highest avg PnL on signalled side (≥3 trades minimum)
- 30-minute in-process cache with explicit refresh endpoint

## Frontend

- Single-page app with TradingView Lightweight Charts; auto-refresh every 60s
- Views: advisor ticket (recommendation, strikes, VRP, win rate, Sharpe, per-horizon alternatives table), IV vs RV overlay chart, regime analysis chart with state labels, full backtest trade history

## Data / Infrastructure

- DuckDB local database: 6 tables (candles_1m, dvol_1m, option_chain_snapshots, advice_log, market_features, collector_runs)
- APScheduler jobs: candles (2 min), DVOL (2 min), options chain (1 hr), derivatives features (5 min), strategy advisor (5 min)
- FastAPI backend; all jobs fire synchronously on startup for immediate dashboard population

## Tags

vol forecasting · HAR-RV implementation · VRP-based options signals · regime-aware advisory · live multi-source market data · DuckDB · APScheduler · FastAPI · TradingView
