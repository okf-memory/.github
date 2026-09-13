<!-- Same as profile/README.md for GitHub repo root view -->
<div align="center">

# OKF Memory

### Deterministic, Sub-300µs Persistent Project Memory for AI Coding Agents

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![OKF Version](https://img.shields.io/badge/Spec-OKF_v0.2-purple.svg?style=flat-square)](https://okf-memory.dev)
[![Language: Go](https://img.shields.io/badge/Go-1.22+-00ADD8.svg?style=flat-square&logo=go)](https://go.dev)
[![Search Latency](https://img.shields.io/badge/Search_Latency-<300µs-brightgreen.svg?style=flat-square)](#-key-benchmarks)
[![Dependencies](https://img.shields.io/badge/External_Dependencies-0-success.svg?style=flat-square)](#)

[**Website & Docs**](https://okf-memory.dev) • [**Quickstart**](#-quickstart) • [**Repositories**](#-ecosystem-repositories) • [**Architecture**](#-architecture--philosophy)

---

</div>

## 💡 What is OKF Memory?

**OKF Memory** is an open-source initiative providing **Git-native, deterministic project memory** for AI coding agents (Claude Code, Cursor, Windsurf, Aider, OpenDevin, and local LLMs).

Instead of dumping massive, stale documentation into LLM context windows or relying on black-box vector databases that suffer from high latency and semantic hallucination, OKF implements **progressive disclosure**:
1. **Lightweight Indexing**: Agents discover knowledge concepts via fast search and short descriptions.
2. **On-Demand Context Loading**: Detailed concepts, code snippets, and architectural rules are pulled into context only when needed.
3. **Deterministic Graph**: Built-in validation ensures zero broken links, zero orphaned concepts, and zero description drift.

```
┌────────────────────────────────────────────────────────────────────────┐
│                        AGENT CONTEXT EVOLUTION                         │
├───────────────────────────────────┬────────────────────────────────────┤
│   Traditional RAG / Flat Dumps    │        OKF Memory Approach         │
├───────────────────────────────────┼────────────────────────────────────┤
│ • 10k–30k token context bloat     │ • <800 tokens per loaded concept   │
│ • 3–8s TTFT prefill latency       │ • <300µs in-memory BM25 retrieval  │
│ • Stale, conflicting hallucination│ • Deterministic, version-tracked   │
│ • Requires external server/db     │ • Git-native, 100% offline pure Go │
└───────────────────────────────────┴────────────────────────────────────┘
```

---

## ⚡ Quickstart

### 1. Install the CLI (`okf`)

```bash
# macOS & Linux via Homebrew
brew install okf-memory/tap/okf

# Universal 1-Liner (macOS / Linux)
curl -fsSL https://okf-memory.dev/install.sh | sh

# Go Toolchain
go install github.com/okf-memory/okf-agent-memory/cmd/okf@latest
```

### 2. Initialize in Any Project

```bash
cd your-project
okf init
```

This creates a conformant `knowledge/` bundle and configures your agent rules (`AGENTS.md`) without overwriting existing guidelines.

---

## 📦 Ecosystem Repositories

| Repository | Purpose | Status |
| :--- | :--- | :--- |
| [**`okf-agent-memory`**](https://github.com/okf-memory/okf-agent-memory) | Pure Go reference engine, embedded stdio MCP server, and `okf` CLI. | ![OSS](https://img.shields.io/badge/Open_Source-MIT-blue?style=flat-square) |
| [**`homebrew-tap`**](https://github.com/okf-memory/homebrew-tap) | Official Homebrew distribution formula for macOS and Linux. | ![Release](https://img.shields.io/badge/Homebrew-Formula-green?style=flat-square) |
| [**`okf-memory.github.io`**](https://github.com/okf-memory/okf-memory.github.io) | Static documentation, interactive terminal simulator, and landing portal. | ![Docs](https://img.shields.io/badge/Documentation-Live-brightgreen?style=flat-square) |
| **`okf-memory-hub`** *(Private Beta)* | Zero-Knowledge E2EE knowledge vault and cross-repo federated sync. | ![Private Beta](https://img.shields.io/badge/Status-In_Development-orange?style=flat-square) |

---

## 🧩 Supported Agent Environments

OKF Memory works out of the box with any tool or agent supporting MCP (Model Context Protocol) or native terminal commands:

- **Claude Code** / **Anthropic CLI** (`.agents/skills/okf-memory/` & stdio MCP)
- **Cursor** / **Windsurf** (Workspace rules + MCP config)
- **Aider** & **OpenDevin**
- **Local Coding Agents** (Ollama, Qwen-2.5-Coder, Llama-3, DeepSeek-R1)

---

## 🎯 Architecture & Philosophy

1. **Zero External Dependencies**: Pure Go. No Python runtime, no Node.js daemon, no PostgreSQL, no vector store required.
2. **Git is the Database**: All knowledge items are human-readable Markdown files with structured YAML frontmatter living directly in your repository.
3. **Open Knowledge Format (OKF v0.2)**: Strict schema conformance, bi-directional relationship graphs, provenance tracking (`generated` vs `verified`), and drift detection.
4. **Local-First & Privacy by Design**: All core memory operations run entirely on your local machine with zero external telemetry.

---

## 🤝 Community & Contributing

OKF Memory is an open, community-driven standard. We welcome contributions, bug reports, and agent integrations:

- 💬 **Discussions & Issues**: Open an issue in [`okf-agent-memory`](https://github.com/okf-memory/okf-agent-memory/issues).
- 🌐 **Website**: [okf-memory.dev](https://okf-memory.dev)
- 📬 **Security & Contact**: `hello@okf-memory.dev`
