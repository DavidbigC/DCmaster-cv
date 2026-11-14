# Rust Shadow Engine (perpl-shadow)

**My role [Mine]:** my decision to have the market maker rewritten in Rust as a separate, read-only shadow app — partly curiosity, partly to measure what a faster language would buy. The experiment measured local signing time and helped assess which delays were outside the engine. AI agents wrote all of the Rust [Directed].

**Type:** faithful Rust port of the Python market-making engine, run in shadow
**Dates:** 2026-07-19
**Stack:** Rust, Tokio, WebSockets, SQLite

---

- consumes public market data only, simulates acks at the venue's measured latency, and builds + signs real hedge transactions with a throwaway key that are then dropped — runs beside the live engine with zero credentials and no HTTP client
- parity gate: golden vectors from the live Python modules checked Rust pricing, EW percentile bands, rungs, tier book and cash accounting to 1e-9
- seeded the shadow band from a read-only copy of live history, kept results in a separate SQLite store, and timestamped feed receipt, parsing, decision and signing. Used public prints to model fills after measured acknowledgement latency.
- 65-minute public-feed shadow run: signal to wire-ready signed hedge was 709 µs p50 / 928 µs p99 over 36 simulated hedges. The earlier Python-era path measured 123 ms p50 under different conditions.

The November [live cancellation signer and Rust BTC cancellation trigger](perpl-onchain-execution.md) were separate projects.

## Tags

Rust · low-latency systems · cross-language parity testing
