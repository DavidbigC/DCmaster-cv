# Experience

> Claim levels: all company roles and 2021–2025 independent work are [Mine], hands-on. 2026 independent work is AI-built under my direction — see `README.md` → How the Work Was Done.

## FLOKI | Data Analyst | Dec 2024 – Apr 2026

- Dashboard design for product and protocol monitoring
- Tracking for Trading Bot, Floki ID, and TokenFi Launchpad activity
- Owned the product database powering BI and dashboards
- Built predictive analysis and forecasting workflows for trading volume, DAU, and fee trends
- Researched feature viability for FLOKI trading products, including trading terminal functionality
- Analyzed business and product performance to support growth planning, campaign design, and product decision-making
- Helped manage delivery for the trading web terminal from early research through implementation support
- Coordinated development efforts through sprint-style planning and focused working sessions
- Aligned stakeholders and contributors around feature direction and execution priorities
- Also covered business analysis: worked closely with the product manager to gather user feedback and turn it into feature requirements
- Backend access and a working knowledge of how the product backend is built, used to judge which features users asked for and what the system could support
- Researched competing wallets and trading apps (retention, hooks and growth mechanics) to inform wallet and trading-product design
- Traded meme coins myself to understand how the user base trades — user research, not speculation
- Competitor analysis: identified gaps and translated findings into recommendations for new features, campaigns, and system improvements
- Market and on-chain intelligence; whale / protocol / token metric monitoring
- Trading bot analytics support: monitoring, behaviour analysis, and product feedback loops
- Database schema collaboration with engineers; event-level data capture planning
- Supported evaluation of campaigns, events, feature changes, and broader product / infrastructure overhauls through data analysis
- Protocol scouting: surfaced early-stage projects for the TokenFi Launchpad pipeline
- Company Streamlit dashboards (102 commits, Apr 2025 → Mar 2026): Trading Bot, Web Bot (web trading terminal), Staking, Locker, UIS board, GenAI NFTs, Smart Contract Auditor; Docker + Helm deployment with semantic-release CI — see `projects/floki-dashboards.md`
- Dune dashboards for the trading bot; Dune Spellbook dbt PRs for Floki bot trades (not merged)
- Airdrop wallet reconciliation across Dune, the internal stake database and the distribution list

## Elfin Metaverse (Dragon Race) | Operation & Data Analyst | May 2024 – Mar 2025

- Product and growth analytics
- On-chain and off-chain user behaviour analysis
- Real-time Tableau dashboards (DAU/MAU, engagement, campaign performance); Streamlit dashboards
- DAU / MAU / campaign / engagement reporting
- Built an Elfin weekly reporting dashboard in Flask and MySQL, with a JSON data endpoint and charts for daily check-ins, retention and active gamers.
- Led the data strategy for the opBNB chain launch
- Token / point incentive modelling with Python agent-based simulations
- BattlePass launch support and ownership
- Retention improvement analysis

**Outcomes:**
- Doubled monthly active interactions, making the platform the #1 most-used dApp on Manta Network
- 90% reduction in manual reporting workload
- 1M+ unique active wallets in the first week of the opBNB launch, ranked #3 on opBNB
- 25% next-month retention improvement
- 10,000+ unique participants in BattlePass in under one month

## CARV (GEMI Foundation) | Community Lead & Business Development | May 2022 – Sep 2023

- Incentive structure redesign
- Engagement analytics; community KPI dashboarding
- A/B testing for reward systems
- Churn / sentiment / activity monitoring
- Regional campaign optimization
- CARV node sale dashboard

**Outcomes:**
- 100K+ community (Discord) messages per month, up over 300% year on year
- 200% increase in regional event participation

## Independent On-Chain Market Maker & Arbitrageur | 2021 – Present

Alongside the roles below until April 2026; full-time since May 2026. All venues are on-chain (Lighter, Omni/Variational, trade.xyz on Hyperliquid, Perpl), and the on-chain data work continues. 2021–2025 work is hands-on; from 2026 the strategy, risk and live operation are mine and the systems were built by AI coding agents under my direction. Never describe me as a "trader".

**2021–2025 (hands-on):**

- Blockchain warehousing scripts and transaction decoding (Sui, BNB Chain)
- DeFi automation: LFJ liquidity-book rebalancing, Dolomite, Berachain, Silo and Sui lending/funding bots
- Limito: CLAMM limit-order product (Node.js backend, Next.js frontend, Uniswap hook in Foundry)
- Lighter ↔ Bluefin arbitrage and market making with a Go hedge server; funding monitors across Lighter, EdgeX, Bluefin, Drift, Paradex and Binance
- Notebook-based yield / strategy analysis (Pendle PT, delta-neutral calculators), Dune research and dashboards
- Grid trading and risk-managed execution logic; delta-neutral stablecoin portfolio management

**2026 (AI-built under my direction; strategy, risk and operation mine):**

- Funding & spread arbitrage desk across Omni/Variational, Lighter and trade.xyz — the core trading business
- Set the strategy and operated a live Perpl market maker hedged on Lighter, owning quoting, hedge and inventory risk. Ranked 7th of 71 accounts above $1M volume on Perpl-leg spread capture in a commissioned study.
- Directed Perpl’s on-chain stale-quote cancellation path via direct Monad and FastLane submission. Staged and operated a live Rust signer and a separate Rust trigger that took ownership of both BTC reference-feed decision paths.
- Commissioned Perpl L3 queue reconstruction and a 42,096-fill study of adverse selection, transaction ordering and cancellation latency.
- Directed the standalone Lighter main ↔ rh arbitrage service migration with book-driven decisions and isolated account-pair risk. Also directed Within-Omni RWA pair trading and the rwa-auto / omni-auto engines.
- Treasury, rebalancer and liquidation-risk systems; Rust signing daemons and a read-only market-maker prototype
- Options and vol tooling: crypto_options_agg, HAR-RV advisory, Hyperliquid tick backtesting, lighter_hedge
- Commissioned research on funding, execution, institutional Treasury positioning, HIP-4 contracts and protocol economics. [Research projects](projects/market-data-research-tools.md)

## AI and Developer Tools (2026 projects, not a job)

- AI-native way of working: I originate and direct, AI agents (Claude Code, Codex) implement
- mytradfiagent, llm-wiki, local autocomplete, DCs-Transcriber, coding-agent usage HUD and a published Claude Code QA skill. Directed a local Web3 JD aggregator and CV tailoring workflow.

---

## Metrics / Outcomes Bank

Use selectively depending on role:

- 5+ years working across crypto, AI, data, analytics, and market systems
- Built and shipped multiple production systems independently
- Up to 30-turn autonomous reasoning workflows in AI research agent
- Doubled monthly active interactions at Dragon Race
- Reduced reporting workload by 90%
- 1M+ unique active wallets in one week on chain expansion
- Improved next-month retention by 25%
- 10,000+ unique participants in BattlePass launch in under one month
- 100K+ community messages per month at CARV after incentive redesign

Added in the 2026-10 audit (2026 systems; strategy and operation mine, implementation AI-built, most figures measured by the agents on my request):

- ranked 7th of 71 Perpl accounts above $1M volume on spread capture (+3.50 bps), measured from on-chain fills
- Perpl maker went from −3.1 bps to +1.71 bps of the Perpl leg within its first day after a quoting-model change
- taker-open entries: 6.55 net bps per dollar vs 1.76 for maker (3.7×), 52 of 53 positive
- funding & spread desk: ~78% of explained P&L came from funding over a 42-day attribution window (13,114 trades)
- Lighter main ↔ rh arb recorded 25.8% APR from inception to 5 October 2026, with ~80% spread income and ~20% funding, reconciled against equity
- funding regime-following +5–6.5%/yr vs −1.3%/yr static over 161 days, all 24 parameter sets positive out-of-sample
- indexed 8.65M fills + 316.9M actions with zero rate-limit errors; DuckDB/Parquet made wide scans 30–267× faster
- July Rust market-maker shadow: 709 µs p50 / 928 µs p99 from signal to wire-ready signed hedge over 36 simulated hedges
- 1,435 commits and ~83k lines of tests in the trading workspace, run by one person directing AI agents

**Perpl and Lighter execution update, November 2026**

- matched 42,096 BTC maker fills to Monad events and identified takers, submission routes and block ordering. A separate 24-hour cohort confirmed higher FastLane auction payments in 99 of 107 FastLane same-block losses
- validated Monad L3 FIFO reconstruction on 1,399 price-level queues across 60 independent replay windows
- Perpl's live on-chain cancel path cancelled 8,399 of 8,868 single-order submissions in a 2–4 November sample. The Rust signer went live on 5 November
- measured a 68 ms paired median improvement from submission to observed proposed block in a bounded dual-ingress trial with 14 comparable cancels
- measured 2.6 µs p50 / 6.4 µs p99 for the Rust cancellation decision alone across 300 synthetic events. Validated the separate trigger in shadow and verified live ownership of Binance and Lighter BTC cancellation decisions
- Rust-backed three-venue recording used 3.94 CPU seconds versus 7.76 on the same replay input with identical rows. Rolled the recorder out live
- validated the standalone Lighter arb port against 755,496 replayed decisions and 18 read API response bodies
- institutional positioning pipeline parsed 2.54 million 13F holding rows across 42 managers. The JD aggregator’s documented October backfill reached 12,078 active jobs with 96.8% full-description coverage

Use carefully depending on role / audience:

- 100% APR delta-neutral stablecoin strategy claim
- Live capital and live trading performance claims
- Incidents and losses (strong interview material on risk, not CV headlines)
- Ranking claims such as #1 most-used dApp on Manta Network

---

## Education

**University of Glasgow** — MSc Research Methods of Psychological Science, 2024
- Dissertation: the alleviating effect of cognitive load on cybersickness
- Experimental design, statistical inference, behavioural modelling, research methods

**Denison University** — BSc Psychology & Computer Science, 2021
- Psychology and computer science
- Interdisciplinary background useful for analytics, experimentation, AI products, and research

---

## Open-Source Contributions

- Submitted Spellbook dbt PRs for Floki bot trade models on Solana, Base and Ethereum and a Meteora v2 base-trades fix. All four closed without merge. [#7649](https://github.com/duneanalytics/spellbook/pull/7649) · [#7650](https://github.com/duneanalytics/spellbook/pull/7650) · [#7658](https://github.com/duneanalytics/spellbook/pull/7658) · [#8012](https://github.com/duneanalytics/spellbook/pull/8012)
- Submitted an April 2026 DefiLlama adapter PR for Elfa AI perpetuals volume on Hyperliquid. It closed without merge. [#6591](https://github.com/DefiLlama/dimension-adapters/pull/6591)
- Directed the coding-agent usage HUD additions in an upstream-derived CodexBar project. [HUD repository](https://github.com/DavidbigC/dc_coding_agent_display)

---

## Notes

- Keep all content factual.
- Prefer concrete systems, tools, tables, workflows, and outcomes.
- Avoid marketing language unless needed in a downstream tailored CV.
- If a skill is not supported by direct work, do not add it.
- Forked repositories are not primary evidence unless authored contributions are verified.
- Where code was vendored or ported (e.g. Lighter's ECgFp5 / Poseidon2 crypto), say so.
