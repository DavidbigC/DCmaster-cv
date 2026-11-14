# Perpl On-Chain Execution and FastLane Research

**My role [Mine]:** I operated the Perpl maker with live capital, set the risk limits for cancelling stale quotes, and commissioned the transaction-ordering and latency studies. I used the results to assess which changes merited live trials. AI agents built the execution stack, ran the measurements and analysed the chain data under my direction [Directed].

**Type:** live on-chain order cancellation, execution research and staged performance work

**Dates:** 2026-10 → 2026-11

**Stack:** Monad, FastLane, Solidity, Foundry, Rust / Tokio, Python, EVM JSON-RPC, WebSockets, SQLite

## Live cancellation and risk controls [Directed]

- Added an on-chain cancellation path for resting Perpl quotes at risk of becoming stale, using Binance and Lighter reference prices. The engine can hold the affected quote side during a cancel, handle late order acknowledgements, and fall back to its normal reconciliation path.
- Mapped API order IDs to on-chain IDs with exchange logs and order-state checks. Handled reprices, reused IDs and in-flight order changes so stale acknowledgements could not redirect a cancel. Added resolver fallback and receipt reconciliation for RPC failures. In one reporting incident, independent receipt checks resolved 141 apparent failures into 134 confirmed cancellations and seven orders already gone.
- Used direct Monad submission and FastLane's transaction-ordering auction. Validated both routes against a deployed Solidity router with Foundry mainnet fork tests and a bounded live check. Isolated the signer and enforced cancellation-only application policy, rate limits and a fee/spend budget. Monitored transaction outcomes, unresolved orders and service health.
- Moved live transaction signing and submission to a Rust service on 5 November, preserving order safeguards, nonce ownership, spend accounting and receipt handling. In an earlier production sample on 2–4 November, 8,399 of 8,868 single-order submissions cancelled their targets, 466 found orders already gone and three failed on-chain.

- Added price-reference freshness checks, a bounded cancel request lifetime, backoff and breaker behavior, and a dashboard for recent cancels, failures, spend runway and alerts. Used a dedicated cancel signer over a Unix socket, separate from the decision process and the quoting engine.
- Ported API-to-chain order lookup with RPC failover and added stamped order-state replay across reconnects. Added rollback controls for the staged handoff.

## Transaction-ordering research [Directed]

- Matched 42,096 BTC maker fills to Monad events across July–November 2026, combining the historical index with public RPC data. Used receipt events and calldata to attribute the taker, identify the submission route and distinguish auction bids from priority fees. Identical fills that could not be uniquely resolved were left unmatched.
- Compared maker fills with the competing cancel by block and transaction position. In one 24-hour matched cohort, 111 of 162 fills landed earlier in the same block. FastLane accounted for 107 of those 111 cases, and receipt evidence confirmed higher auction payments than the competing cancel in 99 of the 107. Block order established the outcome. Proposer arrival times remained unobserved.
- Joined reference-feed, decision, submission and block timestamps to distinguish detection lag from signing, propagation and block inclusion. A bounded live dual-ingress trial measured a 68 ms paired median reduction from send to observed proposed block across 14 comparable cancels.

- A separate 7 November study covered 3,426 maker fills and attributed stale-quote loss to fill-before-cancel races, late or misdirected cancels, missing chain IDs, budget refusals and trigger conditions. Compared detection and inclusion delays for jumps and gradual moves and estimated the benefit of changes to each stage. [Perpl research](perpl-research.md)

## Rust decision and feed work [Directed]

- Tested a separate Rust decision process against real order state and production feeds in shadow mode. An exact-order-ID comparison matched six of nine Python cancels in the first bounded BTC run and exposed threshold and input-timing disagreements. Python retained decision authority during that trial. In the November live rollout the separate Rust trigger took ownership of both Binance- and Lighter-driven BTC cancellations, with a Python fallback. Verified live ownership of both branches in the engine status on 14 November.
- Benchmarked the Rust decision path at 2.6 µs median / 6.4 µs p99 over 300 synthetic cancellation events, excluding signing, network and chain time. Investigated queue starvation and scheduling tails separately with replay and live public-feed tests. Fixed buffered bursts that could monopolize the reader and drop updates, then verified complete in-order delivery on bounded burst fixtures.
- Rolled out a Rust-backed Binance, Perpl and Lighter market-data recorder. Same-input replay preserved all three feeds' recorded rows and reduced CPU time from 7.76 to 3.94 seconds. A short live comparison also verified in-order parity for Binance and Perpl and confirmed that Lighter capture resumed.

See also the [Perpl market maker](perpl-mm.md), [Monad indexer and L3 book](perpl-indexer.md), and [July Rust market-maker prototype](rust-shadow-engine.md).
