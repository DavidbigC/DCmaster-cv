# RISEx–Lighter Market Monitor and Execution Prototype

**My role [Mine]** — I chose the venue pair and asked for venue data quality, executable spread and order-entry behavior to be verified before assessing market making. AI coding agents built the monitor and execution prototype under my direction [Directed].

**Dates** — August–September 2026.

- Built a RISEx order-book collector with CRC32 validation and recovery, an independent Lighter feed and one-second, two-way edge estimates based on depth walked, fees and clip size. Collected funding, volume and carry, and replayed how long opportunities persisted after thresholds were crossed.
- Recorded observations in SQLite WAL and served live and historical views with FastAPI and uPlot.
- Built a separate Rust authenticated execution sidecar with signed post-only placement and cancellation, private WebSocket orders and fills, and timing traces. Added cancel-only handling for ambiguous outcomes and a guarded fee-test harness.
- The monitor and execution code are evidenced in the project. A production market-making deployment was not verified.
