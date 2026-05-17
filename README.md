# David Chen — Master CV

**GitHub:** [github.com/DavidbigC](https://github.com/DavidbigC)
**Website:** [davidbigc.github.io/Site](https://davidbigc.github.io/Site/)
**X:** [@davidbigcccc](https://x.com/davidbigcccc)
**Dune:** [dune.com/davidbigc](https://dune.com/davidbigc)

---

## How to Keep This Repo Updated

The source of truth is the **local master file** at `job_related/David Chen - Ultra CV Master.md` (not committed here — contains PII).

When you complete a new project, role, or research area:

1. **Update the local master first** — open a Claude Code session and describe what you built. Claude reads your code/folders and adds the relevant bullets, skills, and project entry to the master `.md`.
2. **Then mirror the changes here** — update the corresponding file(s) in this repo:
   - New project → create `projects/<project-name>.md`
   - New skills → append to `skills.md`
   - New role or outcomes → update `experience.md`
   - New domain capability → update the Domain Capabilities section in `README.md`
3. **Commit and push:**
   ```bash
   cd job_related/devmaster-cv
   git add .
   git commit -m "feat: add <project or skill name>"
   git push
   ```

**Rule of thumb:** if it went into the local master, it belongs here too (minus PII).

---

## How to Use This Repo (for LLM-assisted CV generation)

This repo is a structured master CV datasource. To generate a tailored CV from a job description:

1. Read this `README.md` for the full capability overview and role index
2. Read `skills.md` for the complete skills inventory
3. Read `experience.md` for work history, outcomes, and education
4. Read the project files in `projects/` that are relevant to the role (see Role Index below)
5. Generate a tailored CV in Markdown, ranked: **critical match → nice to have → bonus**
6. Render to PDF using `resume.css`

**Ranking guidance:** For each JD requirement, classify every bullet from this repo as:
- `[CRITICAL]` — direct match to a must-have requirement
- `[NICE]` — relevant but not explicitly required
- `[BONUS]` — impressive differentiator, include if space allows

---

## Short Summary

- 5+ years working across crypto, AI, data, analytics, trading systems, and product operations
- Formal training in experimental design, statistical inference, behavioural modelling, and research methods (MSc)
- Built and operated production systems in AI research, options analytics, arbitrage, on-chain warehousing, and DeFi automation
- Worked across product analytics, growth analytics, on-chain research, quantitative tooling, and data infrastructure
- Built analytics for business monitoring, forecasting, feature prioritisation, campaign evaluation, and operational decision support
- Managed product delivery for crypto trading features from early viability research through cross-functional implementation
- Experience spans Python, TypeScript / Node.js, Rust, SQL, PostgreSQL, SQLite, DuckDB, APIs, WebSockets, blockchain data, Linux, AWS, and production observability workflows

---

## Domain Capabilities

### AI / LLM Systems
- Built production AI-powered financial research agent
- Multi-turn agent workflows with planning, tool use, and structured output generation
- Hypothesis-driven debate flows for investment research
- OpenAI-compatible model integration; prompt design, tool schema, context handling
- User-facing AI product with auth, chat history, admin controls, deployment

### Data Infrastructure / Analytics Engineering
- PostgreSQL-backed ingestion and warehousing for blockchain transaction data
- Schema design for transaction facts, token metadata, event capture, balances, positions, trade logs
- Incremental update flows, backfill ingestion, deduplication, upsert logic, retry mechanisms
- Async and batch processing patterns for API-driven ingestion

### Product Analytics / Growth Analytics
- Dashboards for product KPIs, DAU/MAU, campaign performance, protocol interactions
- User behaviour analysis for feature prioritisation, retention, growth, incentive design
- Forecasting and trend analysis for key business metrics
- Competitor intelligence and market insight for product decisions

### On-Chain Research / Crypto Analytics
- Dune, Allium, and Flipside for on-chain data analysis
- Contributed to Dune Spellbook dbt models (Solana Meteora edge case correction)
- Transaction decoding and warehousing for Sui and BNB Chain datasets
- Whale behaviour, TVL, wallet flows, launchpad activity monitoring

### Quant / Trading / Market Systems
- Autonomous bilateral market-making (XEMM) across trade.xyz and Lighter with live capital
- Multi-level risk supervision: global notional caps, per-symbol inventory, bilateral net-inventory, kill-switches
- HAR-RV vol forecasting system: deployed, 733 days BTC/ETH, regime-conditional VRP signals
- Short-strangle strategy research: 15,000+ parameter sweeps, Bayesian Pareto optimization, delta-hedging via perps
- ZK protocol integration: Lighter (ECgFp5/Poseidon2/Schnorr), trade.xyz (EIP-712)
- Options analytics: Greeks, IV surface, SVI fitting, arb detection, scanner tooling
- Regime detection: HAR structural breaks, efficiency ratio, chop score, HMM research

### Product / Builder Work
- Shipped full-stack products independently from concept to production
- Backend, frontend, database design, deployment, and analytics across multiple live systems
- Feature viability research, product scoping, implementation coordination

---

## Role Index

### Quant / Trading Role → read these files
- `projects/variational-perps.md` — XEMM, risk supervision, ZK signing, live capital (strongest signal)
- `projects/har-dashboard.md` — HAR-RV forecasting, VRP signals, regime detection
- `projects/vol-research.md` — short-strangle backtesting, Bayesian optimization, ML strategy search
- `projects/crypto-options-agg.md` — options analytics platform
- `skills.md` → Quant / Trading / Market section

### AI Engineer Role → read these files
- `projects/mytradfiagent.md` — AI research agent, multi-turn loops, tool calling
- `skills.md` → AI / LLM section
- `experience.md` → FLOKI, Dragon Race

### Analytics Engineer / Data Engineer Role → read these files
- `projects/sui-warehouse.md` — blockchain ETL, PostgreSQL schema
- `projects/floki-bsc-warehouse.md` — BNB Chain pipeline, async ingestion
- `skills.md` → Data / Analytics / ETL section
- `experience.md` → FLOKI role

### Product Analyst Role → read these files
- `experience.md` → FLOKI, Dragon Race, CARV roles
- `skills.md` → Visualization / Reporting section

### On-Chain Research Role → read these files
- `projects/sui-warehouse.md`
- `projects/floki-bsc-warehouse.md`
- `experience.md` → FLOKI role
- `skills.md` → Blockchain / On-Chain Data section

---

## Projects Overview

| File | Project | Type |
|------|---------|------|
| [projects/variational-perps.md](projects/variational-perps.md) | Variational Cross-Venue Perpetuals Platform | Live XEMM market-making system |
| [projects/har-dashboard.md](projects/har-dashboard.md) | HAR-RV Live Volatility Advisory System | Vol forecasting + advisory dashboard |
| [projects/vol-research.md](projects/vol-research.md) | Hyperliquid Vol & Options Strategy Research | Backtesting + ML strategy research |
| [projects/crypto-options-agg.md](projects/crypto-options-agg.md) | crypto_options_agg | Options analytics platform (dcoption.xyz) |
| [projects/mytradfiagent.md](projects/mytradfiagent.md) | mytradfiagent | AI financial research platform |
| [projects/sui-warehouse.md](projects/sui-warehouse.md) | SUI Transaction Data Warehouse | Blockchain ETL pipeline |
| [projects/floki-bsc-warehouse.md](projects/floki-bsc-warehouse.md) | FLOKI BSC Transaction Warehouse | BNB Chain ingestion pipeline |
| [projects/polymarket.md](projects/polymarket.md) | Polymarket 5-Min Monitor | Prediction market Rust TUI + research |
| [projects/clamm-pendle-lfj.md](projects/clamm-pendle-lfj.md) | CLAMM / Pendle / LFJ | DeFi tooling (concentrated liquidity, yield) |

---

## Education

**University of Glasgow** — MSc Research Methods of Psychological Science, 2024
- Experimental design, statistical inference, behavioural modelling, research methods

**Denison University** — BSc Psychology & Computer Science, 2021
- Interdisciplinary background useful for analytics, experimentation, AI products, and research
