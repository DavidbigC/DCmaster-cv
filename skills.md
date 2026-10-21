# Skills Inventory

> Apply the claim levels in `README.md` → "How the Work Was Done". Sections marked [Mine] are personal skills. Everything else is technology used in my projects: tools from 2021–2025 work were hands-on; items that appear only in 2026 projects were implemented by AI agents under my direction [Directed] and are not personal expertise.

## What I Personally Bring [Mine]

- Trading strategy and market judgment: cross-venue arbitrage, market making, funding carry and basis trades, options selling and hedging ideas, RWA (commodities, indices) perps, prediction markets — choosing what to trade, where, and when to stop
- Risk ownership: setting position and capital limits, deciding when to arm, derisk, pause or pivot, learning from real losses
- Live operations: running strategies with real capital across several venues, funding and moving capital, monitoring, noticing when numbers look wrong
- Directing AI coding agents (Claude Code, OpenAI Codex): turning an idea into a brief with constraints, steering brainstorm → spec → plan → build, reviewing results, setting standing operating rules, judging output against live evidence
- Product thinking: deciding what a console or tool must show, what ships and what stays inert
- Reading and questioning analysis: asking the next question, rejecting results that conflict with live evidence, turning findings into decisions
- Crypto / DeFi domain breadth: perp DEXs, lending, LPs and CLAMMs, yield tokens, airdrops and points programs, bridges and protocol trust models
- Product and growth analytics: KPI and dashboard design, user behaviour analysis, campaign and incentive design, competitor and on-chain research, stakeholder reporting
- Research training: experimental design and statistical inference (MSc)

## Hands-On Technical Skills (2021–2025 work) [Mine]

- Python for data and automation: pandas, NumPy, Jupyter + ipywidgets, Plotly, Matplotlib, requests / aiohttp / asyncio, SQLAlchemy, Web3.py, Telegram bots
- SQL: Dune (DuneSQL) and dbt-style Spellbook models, Flipside, Allium, PostgreSQL, MySQL, SQLite
- Blockchain data and interaction: JSON-RPC on Sui, BNB Chain, Avalanche, Berachain and Arbitrum; receipt and transfer-log decoding; token metadata enrichment; Uniswap V3 sqrtPriceX96 pricing; Dolomite and Odos integrations; Alchemy, BscScan, Dune Python client, DappRadar API
- Warehousing: PostgreSQL schemas, incremental loads, deduplication and upserts, async batch ingestion with retries
- TypeScript / Node.js: Sui SDK (@mysten/sui), AlphaLend SDK, a Silo vault bot with multi-RPC failover, node-cron, PM2; Next.js + Reown frontend (Limito)
- Go: Lighter order scripts, a TCP hedge server for the Lighter ↔ Bluefin arb, order-book monitors, Paradex WebSocket client
- Solidity with Foundry: Uniswap hook for limit orders (Limito), Dune Sim IDX listener
- Indexing: Envio HyperIndex indexers
- Web apps: Flask + Flask-Login + Gunicorn on Render with Neon Postgres; Flask reporting dashboards
- BI and reporting: Tableau, Streamlit, R / R Markdown with ggplot
- Quantitative DeFi analysis: delta-neutral money-market + perp sizing, LP ratio maths, yield / APY modelling, funding-rate comparison across venues

---

## Languages

- Python
- Rust
- TypeScript
- JavaScript
- SQL
- R
- Go
- Solidity
- Swift (AppKit) — 2026, directed

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
- asyncio / FastAPI services, httpx, websockets
- curl_cffi browser-impersonation clients, per-credential session pooling
- HMAC- and Ed25519-signed exchange APIs, JWT cookie auth with token renewal
- Tokio (Rust async), ratatui TUIs; Textual (Python TUI)

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
- uPlot (high-frequency live charts), React 19, mobile-first operator dashboards
- PyQt6 and AppKit desktop UIs

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
- DuckDB over day-partitioned Parquet lakes
- SQLite at scale (18 GB ingest journal, WAL, covering indexes, VACUUM INTO backups)

## Data / Analytics / ETL

- SQLAlchemy
- pandas
- DuckDB (queryable analytical views over Parquet datasets)
- PyArrow / Parquet
- Optuna (Bayesian optimization, TPE and NSGA-II samplers)
- Numba (JIT-compiled numerical simulation)
- dbt exposure through Dune Spellbook model PRs (not merged)
- Envio HyperSync bulk chain-log backfills
- block bootstrap, walk-forward and out-of-sample validation
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
- multi-model debate (MiniMax, Qwen, judge), Grok, Groq, OpenRouter
- ElevenLabs realtime STT, Whisper STT; Ollama, MLX LoRA fine-tuning
- Claude Code and OpenAI Codex agentic workflows (specs, plans, subagent TDD, memory, skills) [Mine — this is how I work]

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
- Lighter (main and rh deployments, sub-accounts, positionFunding / fundings APIs, CCTP deposits, fast withdrawals)
- trade.xyz / Hyperliquid HIP-3 (RWA perpetuals)
- Derive
- Paradex
- Polymarket (Gamma REST API, CLOB WebSocket)
- EIP-712 structured data signing
- Schnorr signing over ECgFp5 / Poseidon2 for Lighter — crypto modules vendored from the open-source lighter-rust crate and integrated into my own Rust daemons (2026, directed); the curve arithmetic is not my work
- Omni / Variational (RFQ execution, settlement pools, relayer deposits, risk-limit and swap-financing APIs)
- Perpl on Monad (Ed25519 API auth, contract events, Multicall3 book snapshots, eth_subscribe / eth_getLogs)
- Ondo Perps, RISEx, PopDEX (Morph Tachyon), Kyan, Rysk
- Bluefin (Sui perps), AlphaLend, EdgeX, Paradex, Drift — 2025, hands-on
- Berachain, Dolomite, Odos, Silo (Arbitrum) — 2024–2025, hands-on

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
- systemd drop-ins and timers, nginx TLS + basic auth for several apps on one box
- git-push deploys to bare repos, deploy backups of server-owned state
- py-spy / perf profiling of live processes; Lightsail burst-credit capacity planning
- Docker + Helm chart + semantic-release CI (company dashboards)
- Telegram bots for signals, liquidation alarms and regime alerts

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
- funding-carry screening (edge × sign persistence ÷ cost), pair kill lists, clock gating
- Avellaneda–Stoikov-style quoting, exponentially-weighted percentile bands, percentile tier ladders
- spread vs direction P&L decomposition, markouts, slip attribution with edge-matched controls
- regime detection (displacement vs imbalance vs CUSUM comparison), lead-lag estimation
- funding clamps, funding regime following, basis + carry blending
- liquidation-distance guards and chunked de-risking
- RWA perp vs swap relative value; cross-deployment arbitrage

## Visualization / Reporting

- Tableau
- Plotly
- Streamlit
- Chart.js
- Recharts
- Jupyter notebooks
- interactive HTML charts
- uPlot, R Markdown / ggplot, Matplotlib

## Testing / QA

- Playwright
- end-to-end testing
- integration testing
- manual QA
- large pytest suites, mutation testing, fuzzing, golden-vector parity tests (2026, AI-built)

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

> **[AI detail]** for 2026 projects: patterns found in the code the agents built under my direction. Use them to describe what systems do, never as personal skills. 2021–2025 patterns (warehouses, decoding, notebooks, Dune workflows) are hands-on.

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
- Rust Schnorr signing daemon using vendored ECgFp5 + Poseidon2 primitives
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
- event-sourced chain indexing (events over calldata), dual-tier proposed / safe chain data
- SQLite ingest journal + Parquet / DuckDB analysis lake, chosen by benchmark
- "ship inert": features deploy disarmed and recording; the operator arms them [Mine — a rule I set]
- pure decision functions that always return a reason, wrapped by thin I/O services
- merged multi-venue order books with venue tags and cap-aware walks
- two-read reconciliation before declaring a position flat; no automatic retry on money-moving calls
- golden-vector parity tests between Python and Rust implementations
