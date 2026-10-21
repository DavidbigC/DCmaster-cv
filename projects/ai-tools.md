# Personal AI Tools and Developer Tooling (2026)

**My role [Mine]:** my ideas, product decisions and daily use; all AI-built [Directed].

---

## llm-wiki — LLM-maintained knowledge base

**Dates:** 2026-04-24 → 26 (45 commits) · **Stack:** Python, FastAPI, SSE, OpenRouter → MiniMax fallback, fswatch / launchd, Obsidian

- ingest pipeline turns dropped files and repos into linked Obsidian wiki pages; lint and query tools; skips unchanged files
- web app with real-time streaming ingest, chat, graph view, sources browser, GitHub repo import, LLM folder "cleanse"
- 4,535 pages generated from my own repos and notes

## DCs-Transcriber — macOS voice input (public repo, used daily)

**Dates:** 2026-04-14 → 18 · **Stack:** Swift, AppKit, AVAudioEngine, ElevenLabs Scribe v2 realtime, OpenAI-compatible LLM refinement

- hold-a-key dictation from the menu bar: global hotkey, live waveform in a floating panel, realtime transcription, optional LLM clean-up, text injected into the focused app, clipboard fallback, history

## ai keyboard — local AI autocomplete with personal fine-tuning

**Dates:** 2026-02-26 → 27 · **Stack:** Python, pynput, PyQt6, Ollama (qwen2.5:0.5b), MLX LoRA, SQLite

- system-wide suggestion popup with Tab-to-accept; context history feeds an MLX LoRA fine-tuning loop that retrains and exports a personal model to Ollama

## Developer tooling

- **CodexBar fork — floating HUD** with token statistics for Claude Code / Codex usage (Swift)
- **rust-js-qa-skill** — a Claude Code skill for Rust + TypeScript/JavaScript QA
- **mdviewer** — small Node markdown viewer

## Tags

AI-native builder · local LLMs · speech-to-text · knowledge management · macOS apps
