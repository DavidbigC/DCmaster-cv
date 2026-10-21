# Lighter main ↔ Lighter rh Cross-Deployment Arbitrage (/arb)

**My role [Mine]:** my idea to arbitrage two deployments of the same perp DEX. I fund the sub-accounts, chose symbols, arm and disarm it, set the per-coin derisk behaviour (release only the coin causing the drain, smoothly, at 5%), and asked for multi-account sets to add inventory with risk isolated per pair. My regime-holding idea was tested and shown not to pay, so I kept the high-turnover approach. AI agents built it and ran the analyses [Directed].

**Type:** live taker-taker arbitrage
**Dates:** 2026-08-15 → ongoing
**Stack:** Python asyncio, FastAPI, Rust signing daemon, SQLite, uPlot

---

- own console and isolated sub-accounts; a pure decision function that always reports why it refused; standalone feeds; runtime credential profiles
- symbols BTC, ETH and XAU; regime gating with hysteresis
- per-coin liquidation guard: each pair held ≥5% from its own liquidation price, released in 1% chunks; account-level survival latch
- multi-account "sets" with risk isolated per account pair; Earned & APR ledger with time-weighted capital
- results: 25.8% APR since start (to 2026-10-05); income ~80% spread capture / ~20% funding, reconciled to equity within $3
- research: 42% of visible edge was lost to slip, 80% of that in the miss / repair path (latency and pick-off ruled out with edge-matched controls); displacement spikes (z ≥ 2) miss 35.6% vs 6.4%; regimes are real but turnover is the P&L, so gating loses money; gold's offset shown to be structural, not edge

## Tags

statistical arbitrage · execution analysis · slippage attribution · liquidation risk · capital accounting
