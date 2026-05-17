# Skills Inventory

## Languages

- Python
- Rust
- TypeScript
- JavaScript
- SQL
- R
- Go
- Solidity

## Spoken Languages

- English
- Mandarin

## Backend / App

- FastAPI
- APScheduler (background job scheduling)
- Flask
- Express
- Node.js
- Axum
- Podman
- Redis
- containerized local development and testing environments
- Docker-compatible container workflows
- Docker Compose
- REST APIs
- JSON-RPC
- WebSockets
- SSE
- Socket.IO (server and client)
- JWT auth
- SIWE / wallet auth
- auth flows
- admin tooling
- cron / scheduled jobs
- database migrations
- Linux service operations
- Nginx
- Caddy
- gevent (cooperative multitasking, monkey-patching, async workers)
- Unix domain socket IPC
- Python–Rust sidecar process architecture
- hot-reload config systems
- self-healing WebSocket feed infrastructure

## Frontend / UI

- Next.js
- React
- TypeScript frontend apps
- Wagmi
- React Query
- Vite
- HTML / CSS
- Tailwind CSS
- chart-based interfaces
- TradingView Lightweight Charts

## Databases / Storage

- PostgreSQL
- SQLite
- MySQL
- MongoDB
- table schema design
- column type decisions
- upserts
- local analytical storage
- event-level storage
- transaction-level storage

## Data / Analytics / ETL

- SQLAlchemy
- pandas
- DuckDB (queryable analytical views over Parquet datasets)
- PyArrow / Parquet
- Optuna (Bayesian optimization, TPE and NSGA-II samplers)
- Numba (JIT-compiled numerical simulation)
- dbt exposure through Dune Spellbook contributions
- Kafka
- forecasting
- trend analysis
- business performance analysis
- experiment analysis
- ETL pipelines
- API-driven ingestion
- async batching
- retry logic
- rate limiting
- deduplication
- backfills
- incremental updates
- schema design
- dashboard data preparation
- product KPI tracking
- user behaviour analysis
- stakeholder-facing analysis

## AI / LLM

- LLM agent architecture
- prompt engineering
- multi-turn reasoning flows
- tool calling systems
- OpenAI-compatible API integration
- hypothesis-driven AI workflows
- AI-assisted research tooling

## Blockchain / On-Chain Data

- Dune
- Dune Spellbook
- Allium
- Flipside
- Alchemy
- BscScan
- Web3.py
- Sui RPC
- transaction receipt decoding
- token transfer decoding
- event / log decoding
- token metadata enrichment
- wallet flow analysis
- protocol monitoring
- GMX
- Hyperliquid (SDK, order placement, EIP-712 signing, perpetuals API)
- Lighter Protocol (zkSync L2 — Schnorr signing, ECgFp5 curve, Poseidon2 hash, market API)
- trade.xyz / Hyperliquid HIP-3 (RWA perpetuals)
- Derive
- Paradex
- Polymarket (Gamma REST API, CLOB WebSocket)
- EIP-712 structured data signing
- Schnorr signature implementation (custom ZK-friendly curve)
- ZK-friendly hash functions (Poseidon2, Goldilocks field)
- ECgFp5 elliptic curve arithmetic

## Infrastructure / Reliability / Observability

- AWS Lightsail (VPS provisioning, instance setup, port/firewall configuration)
- AWS EC2 (broader exposure across projects)
- Grafana
- Loki
- Prometheus
- Promtail
- Linux (Ubuntu)
- Redis
- Kafka
- Podman
- Docker Compose
- Nginx
- Caddy
- SSH key-based authentication
- SCP file transfers to remote servers
- remote command execution via SSH heredocs
- Ubuntu server provisioning from scratch
- Python virtualenv setup on remote servers
- systemd service unit authoring
- systemd lifecycle management
- `journalctl` log tailing and filtering
- Gunicorn WSGI server configuration
- Nginx WebSocket reverse proxy config
- server-side `.env` credential management and rotation workflows
- production monitoring
- observability dashboards
- log aggregation
- metrics collection
- reverse proxy setup
- HTTPS / TLS production serving
- public production deployment
- incident investigation
- root cause tracing across logs, databases, and code
- runbook-oriented operational thinking
- SLI / SLO / SLA exposure

## Quant / Trading / Market

- statistical arbitrage
- delta-neutral strategies
- funding rate monitoring
- perpetuals
- options analytics
- options Greeks
- volatility analysis
- liquidity modelling
- market microstructure analysis
- trading bots
- grid trading
- risk management
- derivatives product research
- trading parameter analysis
- concentrated liquidity strategies
- market making workflows
- autonomous bilateral market making (XEMM pattern)
- cross-venue order execution (maker on one venue, taker hedge on another)
- short-strangle backtesting with delta-hedging via perpetuals
- multi-objective Bayesian optimization for strategy search (Optuna NSGA-II, Pareto frontier)
- walk-forward validation and holdout backtesting
- fake-breakout / confirmation-gate hedge filtering
- regime detection (efficiency ratio, chop score, trend strength, realized vol)
- realized volatility computation and persistence filtering for entry gating
- microstructure feature engineering (signed trade flow, open pressure, block concentration)
- options APR surface analysis across strikes and DTEs
- HAR-RV model family (HAR-RV, HAR-RV-J, HARQ, HAR-IV): implementation, OLS fitting, crypto-specific calibration
- bipower variation and jump variation decomposition
- variance risk premium (VRP) analysis: IV–RV spread as primary edge signal
- Hidden Markov Models (HMM) for vol regime detection: Gaussian/Student-t HMM, Baum-Welch, Viterbi (researched)
- Markov-switching HAR and regime-switching vol models
- quantile regression for tail breach probability (short-strangle risk)
- realized semivariance (upside/downside vol decomposition)
- XGBoost / gradient-boosted trees for feature-rich vol forecasting
- pure Python OLS implementation: Gauss elimination, partial pivoting, ridge regularization, t-stats, R²
- Random Forest for strategy performance prediction and iterative candidate proposal
- bootstrap / Monte Carlo resampling for strategy risk metric estimation
- regime-adaptive policy switching (best hedge policy selected per regime label)
- GPU-accelerated ML environment setup (XGBoost CUDA, PyTorch CUDA) for large-scale optimization
- adverse-move cancellation logic
- reprice throttle / tick-gate logic
- funding skew adaptive threshold adjustment
- depth-ratio quoting (quoting as fraction of available hedge depth)
- order book depth bucket analysis (1/2/5/10/20 bps cumulative size)
- multi-level risk supervision (global notional cap, per-symbol inventory cap, bilateral net-inventory)
- session-scoped position baseline tracking
- post-fill adverse selection tracking (1s/5s/30s drift)
- funding attribution (proportional split across open fills)
- exponential-weighted statistical signal computation (EW mean, Winsor clipping, halflife)
- Pearson correlation for regime scoring
- live capital deployment and operational trading system management

## Visualization / Reporting

- Tableau
- Plotly
- Streamlit
- Chart.js
- Recharts
- Jupyter notebooks
- interactive HTML charts

## Testing / QA

- Playwright
- end-to-end testing
- integration testing
- manual QA

---

## Databases / Warehouses / Pipelines Worked On

- PostgreSQL databases for blockchain transaction warehousing
- PostgreSQL schemas for product / protocol analytics
- SQLite databases for trade logs, balances, P&L, positions, and local app state
- product databases for conversation history, user auth, and app data
- local database-backed tools for portfolio tracking and monitoring

Typical work done:
- schema design, primary keys and deduplication logic, column type selection
- event-level, transaction-level, and metadata tables
- incremental updates, backfills, API polling, WebSocket ingestion
- async batch processing, retry and failure handling
- downstream dashboard / analytics outputs
- local development and test environment setup with containers

---

## Repo-Evidenced Technical Patterns

- PostgreSQL schema design for blockchain transaction warehouses
- SQLite-backed local analytics and execution tools (WAL mode, WITHOUT ROWID + clustered PKs for time-series)
- Podman-based containerized local development environments
- Docker Compose orchestration for multi-service apps
- async ingestion with batching, retry logic, and rate limiting
- JSON-RPC and REST-based blockchain data retrieval
- transaction receipt decoding and transfer log parsing
- token metadata enrichment
- Dune / Flipside / Alchemy-backed data workflows
- notebook-based quantitative research
- Plotly interactive chart generation
- WebSocket-based market data systems with self-healing and rate-limit adaptation
- Socket.IO real-time push from server to browser (trading events, price ticks, session state)
- SSE-based streaming APIs
- Rust API services with Axum
- JWT-based auth flows and SIWE wallet authentication
- PostgreSQL migrations for app services
- Playwright end-to-end testing and Rust integration tests
- Caddy-based reverse proxy and HTTPS serving
- Prometheus / Loki / Promtail / Grafana observability stack
- tracing-based JSON application logging
- backend-as-source-of-truth calculation architecture
- Python–Rust Unix domain socket IPC (newline-delimited JSON protocol, sub-50µs latency)
- Rust Schnorr signing daemon with ECgFp5 + Poseidon2 ZK crypto primitives
- Rust EIP-712 signing daemon with alloy-signer secp256k1 ECDSA and local atomic nonce management
- local nonce cache architecture for blockchain order placement (eliminates per-order HTTP roundtrip)
- gevent cooperative multitasking for concurrent WebSocket + HTTP serving in single-process Flask
- three-tier orchestration hierarchy (Orchestrator → Supervisor → Session) for autonomous trading systems
- hot-reload YAML config with signal overlay and pinning (live parameter changes without process restart)
- multi-level risk supervision: global notional cap, per-symbol inventory cap, bilateral net-inventory monitor
- XEMM cross-exchange market-making: adverse-move cancel, reprice throttle, depth-ratio quoting, funding skew
- consumer-based WebSocket subscription leases (union semantics, add/remove without global resubscribe)
- deferred listener dispatch (release state lock before calling listeners — prevents WS thread blocking)
- exponential-weighted statistical thresholds with Winsor clipping, multiple quantile outputs, halflife fitting
- post-fill adverse selection measurement (1s/5s/30s horizon drift per fill)
- proportional funding attribution across open fills with idempotent upsert
- shadow mode adapter pattern for live production migration (legacy → new data source with disagreement logging)
- real SQLite integration tests with tempfile isolation (not mocked) plus controllable fake clock
- comprehensive fake object injection via dataclass Deps pattern for fast unit tests
- Numba JIT-compiled backtest engines for fast parameter sweep simulation
- multi-objective Bayesian optimization with Optuna NSGA-II (Pareto frontier across Sharpe, return, Calmar)
- walk-forward backtesting with holdout validation
- DuckDB analytical views over multi-gigabyte Parquet (Hyperliquid tick archive, ~18.7M trades)
- fake-breakout confirmation gate pattern for delta-hedge entry filtering (reduces whipsaw crossings 100×)
- regime detection feature computation (efficiency ratio, chop score, trend strength) for adaptive strategy switching
- microstructure feature engineering from tick data (signed trade flow, open pressure, block concentration)
- Random Forest for strategy performance prediction with OOB validation and permutation importance
- bootstrap / Monte Carlo resampling for strategy risk percentile estimation (p5/p95 metrics)
- 4-state regime classification with quantile-fitted thresholds and adaptive hedge policy switching per regime
- GPU-accelerated ML environment (XGBoost CUDA + PyTorch CUDA + Numba) for large-scale optimization runs
- HAR-RV vol forecasting: bipower variation, jump decomposition, VRP analysis, IV–RV spread as edge signal
- XGBoost on rich vol feature sets (lagged RV, DVol, skew, funding, jump indicators) as Tier 3 layer above HAR
- quantile regression and realized semivariance for short-strangle tail breach probability
- Markov-switching HAR and regime-switching vol models with DVol term structure signals

*Forked repos should not be treated as primary evidence unless actual authored work is verified.*
