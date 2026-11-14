# Lighter main ↔ Lighter rh Cross-Deployment Arbitrage (/arb)

**My role [Mine]:** my idea to arbitrage two deployments of the same perp DEX. I fund the sub-accounts, chose symbols, arm and disarm it, set the per-coin derisk behaviour (release only the coin causing the drain, smoothly, at 5%), and asked for multi-account sets to add inventory with risk isolated per pair. My regime-holding idea was tested and shown not to pay, so I kept the high-turnover approach. AI agents built it and ran the analyses [Directed].

**Type:** live taker-taker arbitrage
**Dates:** 2026-08-15 → ongoing
**Stack:** Python asyncio, FastAPI, WebSockets, Rust signing daemon, SQLite, uPlot, systemd

---

- own console and isolated sub-accounts; a pure decision function that always reports why it refused; standalone feeds; runtime credential profiles
- started with crypto and added RWA markets, with per-market arming, observation-only instruments and regime gating with hysteresis
- per-coin liquidation guard: each pair held ≥5% from its own liquidation price, released in 1% chunks; account-level survival latch
- multi-account "sets" with risk isolated per account pair; Earned & APR ledger with time-weighted capital
- recorded 25.8% APR from inception to 5 October 2026, with roughly 80% of income from spread capture and 20% from funding, reconciled against equity
- research: 42% of visible edge was lost to slip, 80% of that in the miss / repair path (latency and pick-off ruled out with edge-matched controls); displacement spikes (z ≥ 2) miss 35.6% vs 6.4%; regimes are real but turnover is the P&L, so gating loses money; gold's offset shown to be structural, not edge

## November execution and service work [Directed]

- Added an optional Binance displacement gate with market-data readings recorded on fills, plus order-book nonce gap detection.
- Added book-update-driven decisions, with slower account and risk reads and a polling fallback. Used sorted books, a warm position baseline and fill-level book-age telemetry. After the initial rollout was rolled back for CPU cost, a nine-market replay measured 5.4% of one core in the revised book-driven mode versus 12.3% before the changes.
- Added an optional persistent WebSocket path for signed Lighter submissions. A warm request benchmark measured ~4 ms over WebSocket versus ~11 ms over REST. The released path defaults to REST.
- Sent paired immediate-or-cancel orders with order-ID-based fill confirmation, residual-leg repair or unwind, and explicit handling of ambiguous outcomes. Reconstructed position basis from the fill ledger on restart and checked it against venue positions.
- Split the arb out of the Perpl app into a standalone Git repo and FastAPI service with its own database and deployment. Verified parity on 755,496 replayed decisions and 18 read API response bodies. Staged the migration of historical fills, snapshots, funding and capital records.
- Added a per-market moving-centre percentile band with side-by-side minute histories. The alternate mode shipped off by default.

## Tags

statistical arbitrage · execution analysis · slippage attribution · liquidation risk · capital accounting
