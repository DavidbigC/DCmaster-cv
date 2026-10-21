# Polymarket 5-Min Monitor

**My role [Mine]:** my trading hypothesis (late-window probability thresholds) and the entry rules chosen from the backtest; AI agents built the Rust monitor and ran the backtests (Mar 2026) [Directed].

**Type:** Live prediction market trading monitor and backtest research
**Stack:** Rust (Tokio, tokio-tungstenite, sqlx, crossterm), Python, SQLite, Polymarket Gamma REST API, Polymarket CLOB WebSocket

---

## Built / Implemented

- Live Rust TUI monitor subscribing to Polymarket 5-minute BTC/ETH/SOL markets via CLOB WebSocket
- Alert system firing when price crosses probability thresholds (70/80/90%) within configurable final time windows (30–90 seconds)
- SQLite outcome logging for live alerts, markets, and trades
- Python analysis toolkit for EV and win rate binning by probability band and time window
- Backtest research: asset-specific entry rules (BTC: 20–45s remaining, 70–80% probability → ~91% win rate); EV-filtered signal tiers accounting for Polymarket taker fees
- Combined BTC + ETH + SOL backtest: win rate rises toward settlement, from 87.3% (90 s left, >70%, n = 2,474) to 96.8% (30 s left, >90%, n = 1,855)
- Telegram alert integration

## Tags

prediction markets · binary options research · Rust async TUI · CLOB WebSocket · Polymarket
