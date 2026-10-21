# mytradfiagent

**My role [Mine]:** my product idea (an AI research analyst for A-share and US markets); I chose the features (debate mode, fast mode, voice, sharing), the data sources and model providers, and run it live at tradfiagentcn.xyz. Built by AI coding agents in Feb 2026 [Directed].

**Type:** AI-powered financial research platform
**Stack:** Async Python, TypeScript, FastAPI-style backend, React / Vite frontend, PostgreSQL, SSE, financial APIs, multiple LLM providers

---

## Built / Implemented

- AI chat product for financial research
- Multi-turn autonomous research loop (up to 30-turn reasoning workflows)
- Hypothesis debate mode with multiple model roles
- Tool-calling system with 30+ financial data tools
- Structured report output
- User auth and conversation storage
- Admin controls; public sharing; voice input support
- Market data ingestion workflows
- Frontend chat interface

## Data / Infrastructure

- PostgreSQL-backed app data; separate market-data database
- OHLCV storage; financial statement ingestion
- Scheduled updates / cron-style jobs; long-running ingestion jobs

## Detail (from the repo README)

- Live at tradfiagentcn.xyz; 149 commits Feb 16–25 2026; FastAPI + React 19 / Vite, SSE
- 33+ financial data tools called in parallel; three modes: Normal (deep research, up to 30 turns), Debate (MiniMax + Qwen debaters + judge, auto PDF report), Fast (Grok with web search, under 5 s)
- Chinese A-share focus: EastMoney, Shanghai Stock Exchange, TradingView; 5-minute OHLCV for ~5,200 A-shares since 2020 with daily incremental updates; 10 years of quarterly financials incl. DuPont; fund research
- pandas-ta sandbox (40+ indicators); Whisper STT voice input with fuzzy stock-name matching; public share links

## Tags

AI engineer · data engineer · product builder · financial research tooling · LLM agent architecture · tool calling · multi-model orchestration
