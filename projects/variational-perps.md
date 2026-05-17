# Variational Cross-Venue Perpetuals Platform

**Type:** Production autonomous bilateral market-making and cross-exchange arbitrage system
**Stack:** Python, Flask, gevent, Socket.IO, Rust, WebSockets, REST APIs, SQLite (WAL mode), Unix domain sockets, Gunicorn, Nginx, AWS Lightsail

---

## System Architecture

- Three-tier orchestration hierarchy: `Orchestrator → SymbolSupervisor → LegSession → RwaMakerExecutor`
- Orchestrator owns all symbols; hot-reloads YAML config (2s poll) and applies hourly signal overlays without downtime
- SymbolSupervisor manages per-symbol lifecycle with exponential-backoff cooldown ladder (5s → 10s → 20s → 30s → 60s max) and hysteresis re-opening gates to prevent thrashing
- LegSession wraps executor threads; soft shutdown with 8s timeout; terminal event forwarding for error escalation
- Two Rust signing daemons spawned as lazy sidecars, communicated with over Unix domain sockets (newline-delimited JSON, ~40µs IPC)

## Market-Making Engine (XEMM Pattern)

- Cross-exchange market-making: quote limit orders on trade.xyz, hedge fills on Lighter
- Multiple offset strategies: `improve`, `join`, `one_back`, `lighter_anchor`, `xyz_anchor` — configurable per session
- Reprice throttle: only replaces order when age ≥ `reprice_min_age_s` AND price diverges by ≥ `reprice_threshold_ticks`
- Adverse-move cancellation: cancel resting maker order when hedge-side moves against it by `adverse_move_cancel_bps`
- Depth-ratio quoting: limits quote size to a fraction of available Lighter hedge depth at acceptable slippage
- Funding skew: shifts entry threshold by `alpha × funding_diff_bps_per_hr`, capped at configurable max
- Thread-safe fill queue with deduplication across WS retries (fill key = oid:tid:sz:time_ms tuple)
- Periodic reconciliation (30s) against live open_orders to catch orphaned orders after cancel/fill races

## Risk Management

- Multi-level risk supervision: global notional USD cap, per-symbol max inventory cap, bilateral net-inventory check
- Position baseline tracking: caps the *change in position* since supervisor start
- Bilateral net-inventory monitor: quarantines symbols when `xyz_position + lighter_position` breaches tolerance
- Kill-all toggle (force-stops all legs), pause-opening toggle (holds new entries, leaves resting hedges)
- Startup reconciliation: cancels orphaned trade.xyz orders on boot; quarantines imbalanced symbols before first leg
- Oracle staleness gate: refuses to open legs if exchange data is stale beyond threshold

## Statistical Signal Computation

- Hourly signals job computes per-symbol advised thresholds from rolling snapshot history
- Exponential-weighted (EW) threshold with 24h halflife: `μ̂ = Σ(v_i × 2^(−age_i / 24)) / Σ(weights)`
- Winsor clipping at [1%, 99%] before EW calculation to neutralize spike contamination
- Outputs p70/p80/p90 threshold quantiles per direction (buy/sell treated independently)
- Funding halflife fitting: log-linear regression of `log|funding_diff|` vs time; halflife = −log(2)/slope, gated on R² > 0.30
- Pearson correlation between funding differential and basis for regime scoring

## Real-Time Market Data Infrastructure

- MarketDataHub singleton: one TradeXyzFeed + two LighterFeed instances (RWA + crypto split)
- ExchangeFeed base class: consumer-based subscription leases; deferred listener dispatch (lock released before calling listeners)
- Self-healing loop (8s tick): detects stale markets (no update in 45s), resubscribes; adaptive throttle on burst resubs
- LighterFeed inflight management: tracks pending subscribes by channel, TTL-evicts orphaned acks (30s), wire throttle 0.4s between messages
- Reconnect with exponential backoff (2s → 60s max); SSL EOF cooldown 8s post-disconnect
- Push-based price ticking: WS callbacks flag pending updates; flush thread batches Socket.IO events every 50ms

## Rust Signing Daemons

- `lighter-execd`: Schnorr signing over ECgFp5 elliptic curve (GF(p^5), p = 2^64 − 2^32 + 1), Poseidon2 hash (Goldilocks field), windowed scalar multiplication
- `tradexyz-execd`: EIP-712 signing (L1 phantom Agent domain, chainId=1337); action_hash = keccak256(msgpack(action) || nonce), alloy-signer secp256k1 ECDSA
- Both: local nonce cache (AtomicU64 floor) eliminates 10–70ms HTTP roundtrip per order; jittered exponential backoff reconnect
- Per-request latency breakdown: nonce_fetch_ms, sign_ms, total_ms reported to Python caller

## Data Storage (SQLite, WAL Mode)

- 9 tables: `rwa_sessions`, `rwa_fills`, `rwa_market_data`, `rwa_auto_signals`, `rwa_arb_snapshots`, `rwa_depth_snapshots`, `balance_history`, `trade_history`, `daily_arb_pnl`
- Order book depth snapshots at 1/2/5/10/20 bps buckets per venue/side (20 columns per row)
- Funding attribution: proportional split of funding payments across open fills; idempotent via UNIQUE(fill_id, exchange, source_event_id)
- Post-fill adverse selection tracking: 1s/5s/30s horizon drift in bps per fill
- WITHOUT ROWID + clustered PKs on (symbol, timestamp) for fast time-series reads

## Testing

- 87 test files covering all critical paths: orchestration lifecycle, executor order logic, market data feeds, signal computation, funding attribution, Rust daemon IPC
- Fake object injection via dataclass `Deps` pattern (no external I/O in unit tests)
- Real SQLite integration tests (tempfile-isolated per test, not mocked)
- Controllable fake clock for time-based logic tests without actual sleeps
- Monkeypatch-based module-level singleton injection for executor tests
- Data-driven tests: 100+ generated sample rows for percentile and threshold assertions

## Dashboard and Operational UI

- 18 HTML pages served via Flask template routes
- Live Socket.IO events: `rwa_arb_update` (2s cadence), `rwa_price_tick` (50ms cadence), session/fill events
- Background tasks: 2s broadcaster, 60s snapshot scheduler, 15min funding attribution refresh
- In-app docs renderer at `/docs/<page>` with Mermaid diagram support

## Infrastructure

- AWS Lightsail production deployment (ap-northeast-1), systemd service management
- Multi-account credential management (primary + indexed accounts)
- Live capital deployed; real execution risk with fill-on-both-legs requirement

## Tags

autonomous market-making · XEMM · cross-venue delta-neutral execution · RWA perpetuals (trade.xyz / Hyperliquid HIP-3) · zkSync DeFi (Lighter Protocol) · ZK crypto primitives (Schnorr, Poseidon2, ECgFp5) · EIP-712 signing · self-healing WebSocket infra · statistical signal computation · risk management systems · Rust + Python IPC · live capital
