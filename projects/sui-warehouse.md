# SUI Transaction Data Warehouse

**Type:** Blockchain transaction ingestion / warehouse pipeline
**Stack:** Python, PostgreSQL, SQLAlchemy, Sui JSON-RPC

---

## Built / Implemented

- Transaction monitor and normalization logic
- Transaction storage flow; object change parsing; event parsing; gas usage extraction
- Checkpoint-based transaction retrieval

## Schema Elements

- transaction digest, sender, timestamp, checkpoint
- transaction type, status, package ID, function, gas used
- created / deleted / modified objects, events JSON

## Tags

analytics engineering · blockchain ETL · warehouse ingestion · Sui · JSON-RPC · PostgreSQL schema design
