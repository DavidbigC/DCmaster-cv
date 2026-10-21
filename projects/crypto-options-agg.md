# crypto_options_agg

**My role [Mine]:** my idea for a multi-venue options workspace for my own options selling; I chose the venues, views and scanners and published it as a public self-hosted site (repo is private). AI agents wrote the code and ran the Node → Rust migration (Mar 2026) [Directed].

**Type:** Crypto options analytics platform
**Stack:** Node.js, Express, Next.js, TypeScript, JavaScript, Rust, Axum, React, PostgreSQL, SQLite, WebSockets, SSE, REST APIs, Playwright, Docker Compose, Caddy, Prometheus, Loki, Grafana, Wagmi

---

## Built / Implemented

- Live options chain interface; exchange-specific and combined exchange views
- Options analytics for BTC, ETH, and SOL across Bybit, OKX, Deribit, Derive
- Arbitrage and box spread views
- Gamma scanner (straddles + strangles ranked by BE/day)
- Vega scanner (straddles + strangles ranked by BE IV move)
- Multi-leg strategy optimizer
- Position builder and portfolio page
- Analysis page: IV smile + SVI fit, ATM IV term structure, 25Δ skew & butterfly
- Wallet-connected account and portfolio flows
- Auth-protected hub backend with JWT-based sessions
- Live SSE / streaming product flows
- Brand and deployment setup for a public production site

## Data / Infrastructure

- Bybit, OKX, Deribit, and Derive integrations
- Streaming and polling market-data services; backend-side calculation model for shared outputs
- Exchange quote comparison logic; exchange badges with best bid/ask per leg
- Rust backend services for market APIs, streaming, and trading-connected workflows
- PostgreSQL-backed hub service with migrations and encrypted credential storage
- Playwright-based end-to-end testing plus repo-based QA workflows
- Docker Compose / Podman-based local and production orchestration
- Caddy reverse proxy for HTTPS public serving
- Prometheus, Loki, Promtail, and Grafana for metrics, logs, and operational visibility

## Additions (2026-10 audit)

- 250 commits, Mar 6 → Apr 1 2026; Rust (Axum) backend ~25k lines, Next.js frontend ~12.8k, hub backend ~3.3k
- original Node/Express backend migrated to Rust with a parity-verification script
- more venues: Binance options, Kyan, Lighter trading integration
- Polymarket analysis service (implied move distribution by expiry); SVI vol-surface fitting; public vs private run modes

## Tags

derivatives tooling · DEX options familiarity · quant interface · full-stack analytics app · production deployment · product engineering
