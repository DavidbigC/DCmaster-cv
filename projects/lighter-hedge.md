# lighter_hedge — Delta-Hedging Engine for Option Strangles

**My role [Mine]:** my strategy (sell strangles, hedge strike breakouts with perps, filter fake breakouts using my vol research). AI agents wrote the Rust engine and TUI [Directed].

**Type:** Rust trading engine + terminal UI
**Dates:** 21–30 March 2026
**Stack:** Rust, Tokio, ratatui, Lighter WebSocket + REST

---

- opens a perp hedge on Lighter when price breaks a sold strike, scales in by available book liquidity, closes on reversal
- three hedge modes: standard, fake-breakout buffer, preemptive
- wallet-key-only onboarding: discovers accounts, derives and registers an API signing key, cancels stale orders
- live account WebSocket, fill confirmation by transaction hash, closes always IOC
- circuit breakers: max position size, max session loss, no flip-to-opposite, close cooldown
- OKX and Bybit portfolio panel, Bybit option-position auto-sync across subaccounts, a multi-strategy monitor, hot-reload configuration and dry-run mode
- Added single-leg call and put configurations, time-confirmed strike breaks with an override, expiry cleanup and aggregate hedge targets across enabled strategies.
- Used a dedicated Lighter position WebSocket with REST reconciliation and reconnect recovery.

## Tags

options hedging · Rust · trading tooling
