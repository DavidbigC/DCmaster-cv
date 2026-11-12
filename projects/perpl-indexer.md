# Perpl On-Chain Indexer, L3 Order Book and Research Lake

**My role [Mine]:** I wanted to see who else was quoting on Perpl and how my market maker compared, and set the rule that indexing and research run locally, never on the trading server. AI agents designed and built the indexer and ran the analyses [Directed].

**Type:** blockchain data engineering for a perp DEX on Monad
**Dates:** 2026-07 → 2026-11 (indexer and L3 in July–August, transaction research through November)
**Stack:** Python, Envio HyperSync, Monad JSON-RPC (eth_getLogs, eth_subscribe), SQLite, Parquet, DuckDB, Multicall3

---

- decoded exchange events for an unverified Monad contract, including direct orders that bypass the sequencer. Cross-checked fields against the SDK ABI and handled event-layout changes after a contract upgrade
- full backfill: 94 shards, 8,653,596 fills + 316,851,059 actions, 18 GB, 22,144 requests with zero rate-limit errors
- taker attribution without the expensive per-action event (verified 638/638), making a ~100 GB backfill possible instead of ~1 TB
- storage chosen by benchmark: SQLite ingest journal + day-partitioned Parquet / DuckDB (18 GB → 2.85 GB; the action-count-by-type query fell from 121.61 s to 0.64 s). Kept SQLite for narrow indexed lookups
- reconstructed the live L3 book and FIFO queues from block-consistent contract snapshots and proposed-block events, with a safe-block journal and reconnect replay
- verified 1,399 of 1,399 price-level queues and full order membership across 60 independent replay windows, with no drift over a 1,200-block replay from one snapshot
- proposed-chain logs led the venue WebSocket by ~390 ms at p50 in a July study of provisional state. An eight-hour live RPC soak recovered 9,391 logs across a 160-block disconnect gap without a permanent hole
- validated the event decoding against engine acknowledgements, matching 1.23M of 1.24M acknowledgements to chain actions by request ID
- powered the market-maker competitor study, fee and funding forensics, and a later [execution study](perpl-onchain-execution.md) that matched 42,096 BTC maker fills to Monad events

## Tags

blockchain ETL · columnar analytics · L3 order books · Monad · DuckDB / Parquet
