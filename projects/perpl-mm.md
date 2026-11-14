# Perpl Market Maker (perpl-mm)

**My role [Mine]** — I designed the strategy, chose the markets, sizes and tiers, set the quoting and hedge rules, decided which features to arm, and operated the engine with live capital. I chose to start by quoting one tick inside when the spread allowed, join otherwise, immediately hedge fills on Lighter, and evaluate Perpl’s maker incentives as part of the economics. AI coding agents built and tested the system and ran the studies under my direction [Directed].

**Dates** — July 2026 onward. Production work documented through November 2026.

**Stack [AI detail]** — Python asyncio, FastAPI, WebSockets, Rust signing and feed services, Unix sockets, SQLite, uPlot, nginx and systemd on AWS Lightsail in Tokyo.

Browse the detailed [strategy research](perpl-research.md), [on-chain cancellation system](perpl-onchain-execution.md) and [L3 data project](perpl-indexer.md).

## Quote model and order placement [Directed]

- Took a BTC pilot to live production in its first day. Moved from touch-based quoting to a rate-limited, event-driven Lighter fair-value anchor, with EWMA recentering and executable hedge-depth pricing.
- Commissioned an Avellaneda–Stoikov review and directed the addition of volatility-scaled spreads, inventory reservation-price skew, a markout guard, and a multi-rung order ladder. The model additions shipped neutral by default.
- Directed exponentially weighted percentile basis bands with parallel half-lives and p60–p99 entries. Added per-side tier direction and sizing, fee-adjusted exit anchors, per-tier reversion targets and inventory reserves, and a persistent tierbook that restores position composition after restart.
- Preserved valuable queue position with touch-aware chase/hold logic and partial-fill requeue rules. Introduced rung-to-order matching, tested it in shadow, and assigned tiers to independent signed WebSocket lanes with account-wide request IDs, per-lane message budgets and order ownership.
- Introduced fee-aware maker and taker entries and exits, depth-bounded reduce-only closes, and a taker-only mode that shipped disabled. Reworked entry and exit thresholds after the fill ledger showed the reduce-only taker fee had moved from zero to 3.45 bps.
- Probed SOL on both venues and ran a SOL pilot. Later expanded the supported runtimes to BTC, ETH and MON, with independent parameters and stores and a shared Perpl market-data subscription. The November deployment was configured for BTC.

## Hedge execution and risk [Directed]

- Batched fills for immediate Lighter hedging, confirmed execution through the account WebSocket, and used REST for reconciliation. Recorded signed fill quantities and actual prices, kept opposite-direction batches distinct, and repaired residual exposure after partial or delayed hedge fills.
- Built liquidity-aware IOC hedge ladders that reprice from live depth and enforce venue minimums. Tested depth- and capacity-aware routing across Lighter main and rh, with per-venue fill and inventory attribution. The audited live maker used Lighter main, with rh observed separately.
- Directed equity-derived inventory and margin limits, acknowledgement-latency halts, stale-feed gates, inventory reconciliation, and recovery after hedging catches up. Developed matched reduce-only de-risking and a liquidation-distance state machine with staged recovery and operator acknowledgement.
- Handled order-ID collisions between engines, reconnect replays, lost or late acknowledgements, and live position reads during hedging. Added close-only wind-down and venue-side order sweeps with retries after engine stop.
- Added fast and slow volatility estimates, Binance displacement gates, volatility-based quote widening and a size ramp during bursts. Added a separate [on-chain cancellation path](perpl-onchain-execution.md) for exposed resting orders.

## Accounting, funding and operator tooling [Directed]

- Built cash-basis attribution across both legs from actual fills, including fees, hedge slippage, funding, and 1/5/30-second markouts. Linked fills to trade decisions, recording the selected tier, market context and entry and exit basis.
- Added venue equity, hourly account snapshots and a cashflow ledger that distinguishes deposits, withdrawals and transfers from trading P&L. Reconstructed Perpl funding from position history and booked Lighter funding from actual venue payments, with idempotent backfill and daily P&L views.
- Captured oracle, mark and funding data. Added manual quote-side emphasis and an independently armable automated basis-plus-carry signal. The later six-hour BTC/ETH funding-hold forecast, regime chart and alerts were a separate read-only workflow. [Funding and strategy research](perpl-research.md)
- Directed a mobile operator console with live market ladders, tier controls, inventory, position basis, liquidation risk, account history, fills and execution traces. Added the chain L3 mirror, Telegram alerts, a heartbeat watchdog and per-symbol controls for configuration and lifecycle.
- Moved the strategy from a local launchd setup to a dedicated Tokyo Lightsail instance after profiling resource use. Reduced engine CPU load through shared feed and book frames, incremental sorted price levels, cached pricing and JSON work, pooled connections and bounded sampling, redraws and retention. Rolled out Rust-backed public feed capture and separated Lighter main ↔ rh arb into its own service. [Lighter arb](lighter-arb.md)

## Measured outcomes

- First day after the fair-value quoting change, the **Perpl leg** went from −3.1 to +1.71 bps.
- In the taker-open sample, entries earned 6.55 net bps versus 1.76 for maker entries, with 52 of 53 positive.
- The on-chain competitor study covered 1.24 million fill legs. The Perpl leg ranked 7th of 71 accounts above $1 million traded volume for spread capture at +3.50 bps. The hedge gave back most of that capture.
- Quote freshness in the measured sample was 67 updates per minute with 3.3% stale. Session profiling highlighted 13:00–16:00 UTC and materially worse Saturdays.
- In the July measurements, hedge confirmation dropped from about 1.8 s to 0.5 s after the move to account WebSockets. Tokyo Lighter WebSocket ping was 3.8 ms p50 against 95 ms over the prior VPN connection.

## Related projects

[Monad indexer and L3 book](perpl-indexer.md) · [On-chain execution and FastLane](perpl-onchain-execution.md) · [Funding, market microstructure and decision research](perpl-research.md) · [July Rust shadow engine](rust-shadow-engine.md) · [Standalone Lighter arb](lighter-arb.md)
