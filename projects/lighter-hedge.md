# lighter_hedge — Delta-Hedging Engine for Option Strangles

**My role [Mine]:** my strategy (sell strangles, hedge strike breakouts with perps, filter fake breakouts using my vol research). AI agents wrote the Rust engine and TUI [Directed].

**Type:** Rust trading engine + terminal UI
**Dates:** 2026-03-21 → 22 (26 commits, ~8.8k lines Rust)
**Stack:** Rust, Tokio, ratatui, Lighter WebSocket + REST

---

- opens a perp hedge on Lighter when price breaks a sold strike, scales in by available book liquidity, closes on reversal
- three hedge modes: standard, fake-breakout buffer, preemptive
- wallet-key-only onboarding: discovers accounts, derives and registers an API signing key, cancels stale orders
- live account WebSocket, fill confirmation by transaction hash, closes always IOC
- circuit breakers: max position size, max session loss, no flip-to-opposite, close cooldown
- OKX + Bybit portfolio panel, multi-strategy monitor, hot-reload config, dry-run mode

## Tags

options hedging · Rust · trading tooling
