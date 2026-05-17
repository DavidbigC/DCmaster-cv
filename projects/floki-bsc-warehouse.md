# FLOKI BSC Transaction Warehouse

**Type:** BNB Chain transaction warehouse and enrichment pipeline
**Stack:** Python, PostgreSQL, SQLAlchemy, pandas, asyncio, aiohttp, Web3.py, Flipside, Dune, Alchemy

---

## Built / Implemented

- Candidate transaction collection from Flipside and Dune
- Transaction receipt retrieval; transfer decoding; buy/sell classification
- Token metadata enrichment; async missing-transaction processing; database sync

## Schema Elements

- Transaction facts; token contract metadata (name, symbol, decimals)
- Denominated amounts; user address; blockchain marker

## Tags

blockchain ETL · product analytics data source · on-chain decoding · BNB Chain · async ingestion · Web3.py
