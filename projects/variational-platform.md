# Variational Trading Platform — 2026 Overview

**My role [Mine]:** I decided what to build at every stage, chose venues and strategies, set risk limits and the agents' operating rules, funded and ran the accounts, and judged results by P&L. AI agents (Claude Code, Codex) wrote the code, tests and docs — the repo statistics below measure their output under my direction [Directed].

**Type:** multi-app cross-venue trading platform (market making, arbitrage, funding carry, treasury, risk), run as a one-person team
**Dates:** 2026-01-25 → ongoing
**Stack:** Python (Flask + Socket.IO + gevent; FastAPI + asyncio), Rust (Tokio daemons and a shadow engine), SQLite, DuckDB / Parquet, JavaScript dashboards (uPlot), nginx, systemd, AWS Lightsail (Tokyo)

---

## Scale

- 1,435 commits across 76 branches
- Python: main Flask app ~45.9k lines, market-maker app ~33.6k, scripts ~25.7k, research ~6k; HTML/JS dashboards ~23.6k lines
- Rust: signing daemons ~6.4k lines; shadow engine ~11.5k lines
- Tests: 417 files / ~83k lines; market-maker partition 2,637 tests (~32 s)
- 137 design specs and implementation plans, 2 ADRs, a domain glossary, 13 research write-ups, 8 code-review reports

## Four apps in one repo

| App | What it does | Stack | Runs |
|---|---|---|---|
| main ("variational") | funding/spread desk, rwa-maker / rwa-auto, omni-auto, Within-Omni, liquidation guard, Telegram alerts | Flask, Socket.IO, gevent, SQLite | AWS Lightsail |
| perpl-mm | Perpl market maker, Lighter main ↔ rh arb, funding panels, PopDEX monitor | FastAPI, asyncio, SQLite, uPlot | dedicated AWS Lightsail |
| risex-mm | RISEx ↔ Lighter basis collector, funding dashboard, maker execution | FastAPI, httpx, websockets | not deployed |
| treasury | cross-venue deposits / withdrawals and rebalancer | CLI + Textual TUI, web3 | local only |

## Venues

trade.xyz (HIP-3 RWA perps on Hyperliquid), Omni / Variational (RFQ crypto + commodity perps), Lighter main and Lighter rh (two separate deployments), Perpl (Monad), plus read-only or experimental integrations with Ondo Perps, RISEx, PopDEX, Binance and Hyperliquid.

## Timeline

- **Jan–Feb:** funding-rate scanner Variational ↔ Lighter across 80+ perp pairs, TWAP execution, Telegram alerts
- **May:** rwa-maker and rwa-auto (trade.xyz ↔ Lighter); research pack on Hummingbot XEMM, professional MM firms, open-source arb bots and optimal-MM literature; verified-taker executor; unified portfolio; omni-auto; structured logging; liquidation alarms; full code review
- **Jun:** treasury layer and rebalancer; funding ledger backfill; CL ↔ WTI funding research
- **Jul:** Ondo arb page; Perpl market maker; Rust shadow engine; latency research; chain indexer and L3 book
- **Aug:** Lighter main ↔ rh arb; dual-venue hedging; competitor study; CPU audits; RISEx
- **Sep:** Within-Omni pair trading; liquidation guard; funding-regime research; XAU on the arb; backwardation page
- **Oct:** arb returns ledger and multi-account sets; Perpl pivot from market making to funding holding; PopDEX research and monitor

## Operating rules I set for the agents [Mine]

- ship new features inert (disarmed, recording) and never touch my live parameters
- live trading data on the servers is authoritative and is never overwritten from a laptop
- keep production boxes under 20% CPU (Lightsail burst baseline)
- my observation of a bug is ground truth; report averages over the dashboard window, not medians
- run research locally, never on the trading server

## Other pieces

- **omni-auto:** autonomous taker-taker engine Omni ↔ Lighter with cadence tiers and EW percentile thresholds
- **verified-taker:** quorum-window confirmation, depth verification, simultaneous IOC, residual repair, shadow mode
- **rwa-trading modes:** maker-on-trade.xyz, taker-both, maker-on-Lighter executors
- **Ondo arb page:** Omni ↔ Ondo Perps scanner with hourly funding and symbol aliasing
- **RISEx:** checksummed book collector, BTC basis model, funding dashboard, maker permit signing and an authenticated maker execution daemon
- **PopDEX:** protocol trust-model due diligence; read-only maker / Lighter-hedge spread monitor that paper-hedges every public fill
- **Backwardation page:** oil forward curve and the cost of the next roll
- **Monitoring sidecars:** Binance / Lighter / Perpl touch collector, reorg monitor, competitor reports, memory probe

## Tags

one-person trading platform · AI-directed engineering · multi-venue integration · Python + Rust · production operations · research-driven trading
