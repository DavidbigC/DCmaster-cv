# Perpl Market Maker (perpl-mm) — maker on Perpl, hedge on Lighter

**My role [Mine]:** my strategy from day one (quote one tick inside when the spread allows, otherwise join; hedge every fill at once; venue incentives as the income thesis). I specified the fair-value anchor, proposed the "EW-80 percentile" band idea, chose symbols, sizes and tiers, armed features one by one, moved it to a Tokyo server, ran it with live capital, and added a funding-hold workflow after the venue changed its fees. AI agents built the engine and console and ran the studies [Directed]. The implementation details below are [AI detail].

**Type:** live cross-venue market-making engine and operator console
**Dates:** 2026-07-13 → ongoing
**Stack:** Python asyncio, FastAPI, WebSockets, Rust signing daemon over a Unix socket, SQLite, uPlot, nginx, systemd, AWS Lightsail Tokyo

---

## Built

- pilot to production in one day; batched hedging, inventory caps, halt-on-hedge-failure, reconciliation, close-only mode
- event-driven, rate-limited fair-value quoting off Lighter, with an EWMA-recentred fair and a depth-aware hedge price
- quoting-model upgrade after an Avellaneda–Stoikov review (vol estimator, vol-scaled spread, reservation-price skew, markout guard, ladder), neutral by default
- percentile tier ladder off EW percentile basis bands (entries p60–p99, exits at reversion), multi-half-life bands, touch-anchored and cap-aware merged-book pricing
- fee-aware maker and taker entry and exit paths, including a taker-only option that ships off by default. The regime model uses basis and funding carry
- BTC, ETH and MON runtimes with multiplexed market-data subscriptions to stay within venue connection limits
- live hedging on Lighter main. Optional depth-aware routing across both deployments was built and tested, with Lighter rh in observation mode in the audited live maker setup
- inventory and margin gates, partial-fill hedge repair, depth-aware reduce-only exits and position reconciliation
- cash-basis trade attribution from actual Perpl and Lighter fills, with fee attribution, 1/5/30-second post-fill markouts and an idempotent funding ledger
- mobile operator console for live ladders, basis, inventory, equity, trade decisions and risk controls. It includes a read-only six-hour BTC/ETH funding forecast and funding-regime alerts
- [on-chain stale-quote cancellation](perpl-onchain-execution.md) on Monad via direct and FastLane routes, with a live Rust signer and receipt reconciliation

## Measured

- first day: −3.1 bps → +1.71 bps of the Perpl leg after the fair-value quoting change
- taker-open entries: 6.55 net bps per dollar vs 1.76 for maker (3.7×), 52 of 53 positive
- on-chain competitor study (1.24M fill legs, 71 accounts above $1M): ranked 7th of 71 at +3.50 bps spread capture on the Perpl leg; most was given back on the hedge — the hedge, not the quote, was the leak
- quote freshness: 67 updates/min, 3.3% stale (losing makers left quotes stale ~50% of the time)
- P&L concentrated 13–16 UTC because the venue's own spread widens in US hours; Saturdays ~10× worse
- entry losses are run-over selection, not toxicity; a volatility-ramped size keeps 77% of volume and cuts negative entry edge by ~two-thirds

## Research and operations

- hedge confirmation fell from ~1.8 s to ~0.5 s in the July measurements after switching to account WebSockets, with REST reconciliation as fallback
- measured Lighter WebSocket ping RTT at 3.8 ms p50 from Tokyo versus 95 ms over the previous connection. A separate study measured a ~200–300 ms Binance lead over Lighter
- dedicated instance after measuring the shared box above its sustainable CPU baseline; CPU audits halved engine load
- incidents owned: a sharp BTC spike liquidated the hedge leg, which led to equity-derived caps, liquidation classification and a margin ladder; order-id collisions between two engines; reconnect replays read as new fills

## Tags

market making · cross-venue hedging · percentile bands · funding and markouts · on-chain execution · FastLane · live operation
