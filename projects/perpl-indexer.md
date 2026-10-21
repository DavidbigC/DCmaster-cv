# Perpl On-Chain Indexer, L3 Order Book and Research Lake

**My role [Mine]:** I wanted to see who else was quoting on Perpl and how my market maker compared, and set the rule that indexing and research run locally, never on the trading server. AI agents designed and built the indexer and ran the analyses [Directed].

**Type:** blockchain data engineering for a perp DEX on Monad
**Dates:** 2026-07 → 2026-08
**Stack:** Python, Envio HyperSync, Monad JSON-RPC (eth_getLogs, eth_subscribe), SQLite, Parquet, DuckDB, Multicall3

---

- decoded an unverified exchange contract from events rather than sequencer calldata (direct user orders bypass the sequencer); reconciled field mappings with the official SDK ABI (191 events)
- full backfill: 94 shards, 8,653,596 fills + 316,851,059 actions, 18 GB, 22,144 requests with zero rate-limit errors
- taker attribution without the expensive per-action event (verified 638/638), making a ~100 GB backfill possible instead of ~1 TB
- storage chosen by benchmark: SQLite ingest journal + day-partitioned Parquet / DuckDB (18 GB → 2.85 GB; a wide scan went 121.6 s → 0.64 s); SQLite kept for narrow indexed lookups
- real-time L3 order book from proposed blocks with a safe-tier journal; validated against the venue's L2 feed; five live-only defects found and fixed
- chain logs lead the venue's own feed by ~390 ms; storm soak: 0 chain drops vs 18 venue drops
- powered the market-maker competitor study and fee / funding forensics

## Tags

blockchain ETL · columnar analytics · L3 order books · Monad · DuckDB / Parquet
