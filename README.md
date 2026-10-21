# David Chen — Master CV

**GitHub:** [github.com/DavidbigC](https://github.com/DavidbigC)
**Website:** [davidbigc.github.io/Site](https://davidbigc.github.io/Site/)
**X:** [@davidbigcccc](https://x.com/davidbigcccc)
**Dune:** [dune.com/davidbigc](https://dune.com/davidbigc) · [dune.com/dragonborn](https://dune.com/dragonborn)
**Flipside:** [flipsidecrypto.xyz/DavidC/dashboards](https://flipsidecrypto.xyz/DavidC/dashboards)
**Live AI product:** [tradfiagentcn.xyz](https://tradfiagentcn.xyz) · **Public options dashboard:** dcoption.xyz

*Last full audit: 2026-10-21 — every GitHub repo, authored PRs, local projects and the private trading workspace.*

---

## How the Work Was Done — read this before generating any CV

My work splits into two eras:

- **2021–2025: hands-on.** I wrote the code, SQL and analysis myself: blockchain data warehouses, Dune / Flipside research and dashboards, DeFi bots and calculators, the Limito CLAMM tool, the Lighter ↔ Bluefin arb with a Go hedge server, indexers, and the dashboards in my analyst roles.
- **2026: AI-directed.** From early 2026 I build by directing AI coding agents (Claude Code and OpenAI Codex). I come up with the ideas, set strategy, requirements and risk limits, approve designs, operate the systems with live capital and judge results; the agents write the code and run most of the measurements I ask for.

**Claim levels used in this repo:**

- **[Mine]** — my own ideas, decisions, domain judgment, operation, or hands-on work (all 2021–2025 work)
- **[Directed]** — I conceived and directed it; AI agents implemented it (2026 technical systems)
- **[AI detail]** — implementation internals recorded for reference; not personal expertise

**Phrasing rules:**

- 2021–2025 work: normal verbs ("built", "wrote", "designed").
- 2026 work: "conceived and directed", "led AI coding agents to build", "specified", "set the strategy / risk limits for", "operated with live capital", "commissioned analysis that showed…". Do not say "implemented / coded / engineered", and do not list 2026 implementation techniques as personal skills.
- Positioning: a hands-on on-chain / DeFi data builder (2021–2025) who became an AI-native builder and operator in 2026 — owning the strategy, the risk and the live operation.

---

## Converting a Markdown CV to PDF

The `resume.css` in this repo is the stylesheet. It uses `@page` rules and a `.markdown-body` wrapper — it's designed for [`md-to-pdf`](https://github.com/simonhaenisch/md-to-pdf).

**One-time setup:**
```bash
npm install -g md-to-pdf
```

**Convert any CV markdown to PDF:**
```bash
md-to-pdf --stylesheet resume.css "David Chen - Quant Researcher CV.md"
# outputs: David Chen - Quant Researcher CV.pdf
```

**Typical workflow:**
1. LLM generates a tailored CV as a `.md` file (e.g. `David Chen - Quant Role CV.md`)
2. Run the `md-to-pdf` command above
3. PDF is output in the same directory

**Notes:**
- `md-to-pdf` renders via headless Chrome (Puppeteer) — the output matches browser print quality
- The CSS hides `<hr>` dividers, centers the name/contact header, and applies tight print margins
- Font size is 9.5pt by default — adjust `font-size` in `resume.css` if you need more/less content per page
- If `md-to-pdf` isn't available, fallback: open the markdown in a browser renderer that wraps content in `.markdown-body`, load `resume.css`, and print to PDF

---

## How to Keep This Repo Updated

The source of truth is the **local master file** at `job_related/David Chen - Ultra CV Master.md` (not committed here — contains PII and private account figures).

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

**Rule of thumb:** if it went into the local master, it belongs here too — minus PII, account identifiers, server details, and dollar capital / P&L figures of private trading accounts (keep bps, ranks and percentages).

---

## How to Use This Repo (for LLM-assisted CV generation)

This repo is a structured master CV datasource. To generate a tailored CV from a job description:

1. Read **How the Work Was Done** above and apply its claim levels
2. Read `skills.md` for the skills inventory (personal skills first, then technologies used)
3. Read `experience.md` for work history, outcomes, open-source PRs and education
4. Read the project files in `projects/` that are relevant to the role (see Role Index below)
5. Generate a tailored CV in Markdown, ranked: **critical match → nice to have → bonus**
6. Render to PDF using `resume.css`

**Ranking guidance:** For each JD requirement, classify every bullet from this repo as:
- `[CRITICAL]` — direct match to a must-have requirement
- `[NICE]` — relevant but not explicitly required
- `[BONUS]` — impressive differentiator, include if space allows

---

## Short Summary

- 5+ years across crypto, AI, data, analytics, trading systems, and product operations
- Formal training in experimental design, statistical inference, behavioural modelling, and research methods (MSc)
- [Mine] 2021–2025: hands-on on-chain data work — PostgreSQL warehouses for Sui and BNB Chain, Dune / Flipside / Allium research and dashboards, DeFi automation and calculators, a CLAMM limit-order product, cross-venue arb bots
- [Mine] Product and growth analytics in three crypto companies: FLOKI, Dragon Race (#1 dApp on Manta, 1M+ wallets in an opBNB launch week), CARV
- [Mine + Directed] Since Jan 2026, conceived, directed and operated a multi-app cross-venue trading platform as a one-person team with AI coding agents: 1,435 commits, four apps, live capital on five venues (trade.xyz, Omni/Variational, Lighter main, Lighter rh, Perpl)
- [Mine] Run a delta-neutral funding and spread arbitrage desk across Omni, Lighter and trade.xyz; attribution showed ~78% of profit came from funding, which reshaped how I choose and cut pairs
- [Mine] Set the strategy for and ran a market maker on Perpl (Monad) hedged on Lighter that ranked 7th of 71 accounts above $1M volume on spread capture (+3.50 bps), per an on-chain study I commissioned
- [Mine + Directed] Commissioned a ~15-study research library (RWA arbitrage universe, funding mechanisms, oracle risk, 135-symbol funding-harvest screen, oil rolls and backwardation, funding prediction) and traded from it
- [Mine] Run AI agents like an engineering team: brief → spec → plan → build with tests → review → operate; standing operating rules for the agents (ship features inert, never touch live parameters, live data is authoritative)

---

## Domain Capabilities

### On-Chain Research / Crypto Analytics — hands-on [Mine]
- Dune, Allium and Flipside analysis; Dune dashboards (Floki trading bot, Contango, SOFA, CARV node sale)
- Transaction decoding and warehousing for Sui and BNB Chain
- Whale behaviour, TVL, wallet flows, launchpad activity monitoring
- Submitted Dune Spellbook dbt model PRs (Floki bot trades on Solana / Base / Ethereum, Meteora fix) — not merged

### Product Analytics / Growth Analytics — hands-on [Mine]
- KPI dashboards (Tableau, Streamlit), DAU/MAU, campaign performance, protocol interactions
- User behaviour analysis for feature prioritisation, retention, growth, incentive design
- Forecasting, competitor intelligence, protocol scouting

### Trading Strategy & Operation [Mine]
- Funding-rate and spread arbitrage across crypto perps, RWAs and tokenised equities
- Market making on a perp DEX with cross-venue hedging; cross-deployment arbitrage
- Options selling with perp delta hedging; volatility-based advisory
- Risk ownership: limits, arming / derisking decisions, incident follow-through, strategy pivots

### Trading Systems — AI-built under my direction [Directed]
- Funding/spread desk executor and scanners; rwa-auto / omni-auto autonomous engines
- Perpl market maker with percentile tier ladders and cross-venue hedging
- Lighter main ↔ rh arbitrage console with per-coin liquidation guards
- Within-Omni RWA future-vs-swap pair trading; treasury and rebalancer; liquidation-risk stack
- Perpl chain indexer (316.9M actions), real-time L3 order book, Parquet + DuckDB research lake
- Rust signing daemons and a Rust shadow engine (709 µs p50 signal → signed order)

### AI / LLM Systems — AI-built under my direction [Directed]
- mytradfiagent: live AI financial research agent (33+ tools, multi-model debate, A-share data)
- llm-wiki (LLM-maintained knowledge base), ai keyboard (local autocomplete with LoRA fine-tuning), DCs-Transcriber (macOS voice input)

---

## Role Index

### Trading / Quant / Market Making → read these files
- `projects/funding-desk.md` — funding & spread arbitrage desk (core trading business)
- `projects/perpl-mm.md` — Perpl market maker
- `projects/lighter-arb.md` — Lighter main ↔ rh arbitrage
- `projects/research-library.md` — research behind the trading decisions
- `projects/within-omni.md`, `projects/variational-perps.md` — RWA engines
- `projects/har-dashboard.md`, `projects/vol-research.md`, `projects/lighter-hedge.md`, `projects/crypto-options-agg.md` — options and volatility
- `skills.md` → What I Personally Bring; Quant / Trading / Market

### Data Engineering / Blockchain Data → read these files
- `projects/sui-warehouse.md`, `projects/floki-bsc-warehouse.md` (hands-on)
- `projects/perpl-indexer.md` (directed)
- `projects/defi-tools-2024-2025.md` (hands-on)
- `skills.md` → Hands-On Technical Skills

### Product / Growth Analyst → read these files
- `experience.md` → FLOKI, Dragon Race, CARV
- `projects/floki-dashboards.md`

### AI / AI-Native Builder → read these files
- `projects/mytradfiagent.md`, `projects/ai-tools.md`
- `projects/variational-platform.md` (how a one-person team runs AI agents at scale)

### On-Chain Research → read these files
- `projects/sui-warehouse.md`, `projects/floki-bsc-warehouse.md`, `projects/defi-tools-2024-2025.md`
- `experience.md` → FLOKI; open-source PRs

---

## Projects Overview

| File | Project | Era | Type |
|------|---------|-----|------|
| [variational-platform.md](projects/variational-platform.md) | Variational Trading Platform — 2026 overview | 2026 directed | Multi-app trading platform |
| [funding-desk.md](projects/funding-desk.md) | Funding & Spread Arbitrage Desk | 2026 mine + directed | Core trading business |
| [research-library.md](projects/research-library.md) | Cross-Venue Research Library | 2026 mine + directed | ~15 trading studies |
| [perpl-mm.md](projects/perpl-mm.md) | Perpl Market Maker | 2026 mine + directed | Live market making |
| [perpl-indexer.md](projects/perpl-indexer.md) | Perpl On-Chain Indexer & L3 Book | 2026 directed | Blockchain data engineering |
| [lighter-arb.md](projects/lighter-arb.md) | Lighter main ↔ rh Arbitrage | 2026 mine + directed | Live cross-deployment arb |
| [within-omni.md](projects/within-omni.md) | Within-Omni RWA Pair Trading | 2026 directed | Relative value, RWAs |
| [treasury-and-risk.md](projects/treasury-and-risk.md) | Treasury, Rebalancer & Liquidation-Risk Stack | 2026 directed | Capital and risk |
| [rust-shadow-engine.md](projects/rust-shadow-engine.md) | Rust Shadow Engine | 2026 directed | Low-latency port |
| [variational-perps.md](projects/variational-perps.md) | rwa-auto / rwa-maker (trade.xyz ↔ Lighter) | 2026 directed | Autonomous XEMM |
| [har-dashboard.md](projects/har-dashboard.md) | HAR-RV Live Volatility Advisory | 2026 directed | Vol forecasting |
| [vol-research.md](projects/vol-research.md) | Hyperliquid Vol & Options Research | 2026 directed | Backtesting + ML |
| [lighter-hedge.md](projects/lighter-hedge.md) | lighter_hedge | 2026 directed | Rust strangle hedger |
| [crypto-options-agg.md](projects/crypto-options-agg.md) | crypto_options_agg | 2026 directed | Options analytics (dcoption.xyz) |
| [mytradfiagent.md](projects/mytradfiagent.md) | mytradfiagent | 2026 directed | Live AI research agent |
| [polymarket.md](projects/polymarket.md) | Polymarket 5-Min Monitor | 2026 directed | Prediction-market research |
| [ai-tools.md](projects/ai-tools.md) | llm-wiki, ai keyboard, DCs-Transcriber, dev tooling | 2026 directed | Personal AI tools |
| [floki-dashboards.md](projects/floki-dashboards.md) | FLOKI product dashboards | 2025 hands-on | Company BI |
| [sui-warehouse.md](projects/sui-warehouse.md) | SUI Transaction Data Warehouse | 2025 hands-on | Blockchain ETL |
| [floki-bsc-warehouse.md](projects/floki-bsc-warehouse.md) | FLOKI BSC Transaction Warehouse | 2025 hands-on | BNB Chain ingestion |
| [clamm-pendle-lfj.md](projects/clamm-pendle-lfj.md) | Limito / Pendle / LFJ | 2024–2025 hands-on | DeFi tooling |
| [defi-tools-2024-2025.md](projects/defi-tools-2024-2025.md) | Other 2024–2025 DeFi tools & research | 2024–2025 hands-on | Bots, indexers, analysis |

---

## Education

**University of Glasgow** — MSc Research Methods of Psychological Science, 2024
- Dissertation: the alleviating effect of cognitive load on cybersickness
- Experimental design, statistical inference, behavioural modelling, research methods

**Denison University** — BSc Psychology & Computer Science, 2021
- Interdisciplinary background useful for analytics, experimentation, AI products, and research
