# Rust Shadow Engine (perpl-shadow)

**My role [Mine]:** my decision to have the market maker rewritten in Rust as a separate, read-only shadow app — partly curiosity, partly to measure what a faster language would buy. I accepted the finding that venue latency, not code speed, is the limit. AI agents wrote all of the Rust [Directed].

**Type:** faithful Rust port of the Python market-making engine, run in shadow
**Dates:** 2026-07-19
**Stack:** Rust, Tokio, WebSockets, SQLite

---

- consumes public market data only, simulates acks at the venue's measured latency, and builds + signs real hedge transactions with a throwaway key that are then dropped — runs beside the live engine with zero credentials and no HTTP client
- parity gate: golden vectors generated from the live Python modules, asserted in Rust to 1e-9
- first 65-minute live session: signal → signed order p50 709 µs / p99 928 µs vs p50 123 ms on the earlier Python-era path

## Tags

Rust · low-latency systems · cross-language parity testing
