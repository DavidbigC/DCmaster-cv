# Perpl Market Maker (perpl-mm) — maker on Perpl, hedge on Lighter

**My role [Mine]:** my strategy from day one (quote one tick inside when the spread allows, otherwise join; hedge every fill at once; venue incentives as the income thesis). I specified the fair-value anchor, proposed the "EW-80 percentile" band idea, chose symbols, sizes and tiers, armed features one by one, moved it to a Tokyo server, ran it with live capital, and called the pivot to funding holding after the venue's fee change. AI agents built the engine and console and ran the studies [Directed]; internals are [AI detail].

**Type:** live cross-venue market-making engine and operator console
**Dates:** 2026-07-13 → 2026-10 (pivoted to funding holding 2026-10-13)
**Stack:** Python asyncio, FastAPI, WebSockets, Rust signing daemon over a Unix socket, SQLite, uPlot, nginx, systemd, AWS Lightsail Tokyo

---

## Built

- pilot to production in one day; batched hedging, inventory caps, halt-on-hedge-failure, reconciliation, close-only mode
- fair-value quoting off the Lighter book, then an EWMA-recentred fair
- quoting-model upgrade after an Avellaneda–Stoikov review (vol estimator, vol-scaled spread, reservation-price skew, markout guard, ladder), neutral by default
- percentile tier ladder off EW percentile basis bands (entries p60–p99, exits at reversion), multi-half-life bands, touch-anchored and cap-aware merged-book pricing
- taker-open and taker-close paths; regime actor leaning quotes from basis + carry
- multi-symbol runtimes (BTC, ETH, MON); one shared market-data socket under the venue's ~5-WebSocket-per-IP limit
- dual-venue hedging across Lighter main and Lighter rh with a merged venue-tagged book
- operator console: halt vs close-and-stop, live ladders, positions and equity across venues, funding carry panel, per-trade decision log, mobile layout

## Measured

- first day: −3.1 bps → +1.71 bps of the Perpl leg after the fair-value quoting change
- taker-open entries: 6.55 net bps per dollar vs 1.76 for maker (3.7×), 52 of 53 positive
- on-chain competitor study (1.24M fill legs, 71 accounts above $1M): ranked 7th of 71 at +3.50 bps spread capture on the Perpl leg; most was given back on the hedge — the hedge, not the quote, was the leak
- quote freshness: 67 updates/min, 3.3% stale (losing makers left quotes stale ~50% of the time)
- P&L concentrated 13–16 UTC because the venue's own spread widens in US hours; Saturdays ~10× worse
- entry losses are run-over selection, not toxicity; a volatility-ramped size keeps 77% of volume and cuts negative entry edge by ~two-thirds

## Research and operations

- latency: Lighter WS 3.8 ms from Tokyo vs 95 ms from home; Binance leads Lighter by ~200–300 ms
- dedicated instance after measuring the shared box above its sustainable CPU baseline; CPU audits halved engine load
- incidents owned: a sharp BTC spike liquidated the hedge leg, which led to equity-derived caps, liquidation classification and a margin ladder; order-id collisions between two engines; reconnect replays read as new fills

## Tags

market making · cross-venue hedging · percentile bands · latency research · on-chain competitor analysis · live operation
