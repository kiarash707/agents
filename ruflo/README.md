<div align="center">

![K-I Agent Banner](assets/banner.png)

[![Version](https://img.shields.io/badge/version-3.45.0-6366f1?style=for-the-badge&logo=git&logoColor=white)]()
[![MIT License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-20+-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178c6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org)

# K-I Agent

**An agent meta-harness for Claude Code and Codex.**

Deploy 100+ specialized agents in coordinated swarms — with self-learning, fault-tolerant consensus, vector memory, and MCP integration. 35 native plugins, 12 background workers, and enterprise security guardrails.

🇮🇷 **فارسی — Persian documentation & tutorials:**
[دوکیومنت کامل فارسی](README.fa.md) · [راهنمای نصب و شروع سریع](docs/fa/quickstart.md) · [آموزش K-I Agent به زبان ساده](docs/fa/k-i-agent-explained.md)

📘 **New to the project?** Start with the English tutorial: [**K-I Agent Explained — build an AI team that plans, remembers, tests, and improves**](docs/k-i-agent-explained.md)

</div>

---

> **Agent = Model + Harness.** The model writes; the harness gives it tools, memory, loops, sandboxes, and controls so it can actually work. **K-I Agent is the harness** — the execution layer around Claude Code and Codex that adds specialized agents, coordinated swarms, self-learning memory, federated communication across machines, and security guardrails. So agents don't just run — they collaborate.

One `init` command gives your coding assistant a nervous system: agents self-organize into swarms, learn from every task, remember across sessions, and — with federation — securely talk to agents on other machines without leaking data. You keep writing code. K-I Agent handles the coordination.

```
Self-Learning / Self-Optimizing Agent Architecture

User --> K-I Agent (CLI/MCP) --> Router --> Swarm --> Agents --> Memory --> LLM Providers
                          ^                           |
                          +---- Learning Loop <-------+
```

> **What does that mean in practice?** You don't need to learn hundreds of MCP tools or dozens of CLI commands. After `init`, just use Claude Code normally — the hooks system automatically routes tasks, learns from successful patterns, and coordinates agents in the background.

## Quick Start

There are **two different install paths** with very different surface areas. Pick based on what you need:

| | **Claude Code Plugin** | **CLI install (`k-i-agent init`)** |
|---|---|---|
| What it gives you | Slash commands + a few skills + agent definitions per-plugin | The full loop — agents, 60+ commands, skills, MCP server, hooks, daemon |
| Files in your workspace | **Zero** | `.claude/`, config, CLAUDE.md, helpers, settings |
| MCP server registered | Only the core plugin | Yes |
| Hooks installed | No | Yes |
| Best for | Try a single plugin's commands without committing to the full install | Production use — everything works as documented |

### Path A — Claude Code plugins (lite, slash commands only)

Inside Claude Code:

```
/plugin marketplace add kiarash707/agents

/plugin install ruflo-core@k-i-agent
/plugin install ruflo-swarm@k-i-agent
```

This adds slash commands and agent definitions. For the full loop (hooks, MCP server, background workers), use Path B.

### Path B — CLI install (full setup)

```bash
# 1. Clone this repository
git clone https://github.com/kiarash707/agents.git k-i-agent
cd k-i-agent

# 2. Install and link the CLI
npm install
npm link            # exposes the `k-i-agent` command

# 3. Initialize in your project
k-i-agent init      # interactive setup wizard
k-i-agent doctor    # health check — Node 20+, MCP, memory DB, API keys
```

> **Tip:** test `init` in a disposable project first, then apply it to important work. Initialization writes project configuration — review the changes.

### Registering the MCP server manually

```bash
# Claude Code
claude mcp add k-i-agent -- npx --yes k-i-agent mcp start
claude mcp list

# Codex CLI
codex mcp add k-i-agent -- npx --yes k-i-agent mcp start
codex mcp list
```

## What You Get

| Capability | Description |
|------------|-------------|
| 🤖 **100+ Agents** | Specialized agents for coding, testing, security, docs, architecture |
| 📡 **Comms Layer** | Zero-trust federation — agents across machines/orgs discover, authenticate, and exchange work securely |
| 🐝 **Swarm Coordination** | Hierarchical, mesh, and adaptive topologies with consensus (Raft, Byzantine, Gossip) |
| 🧠 **Self-Learning** | SONA neural patterns, ReasoningBank, trajectory learning |
| 💾 **Vector Memory** | HNSW-indexed AgentDB — semantic (meaning-based) retrieval with sub-ms lookups |
| ⚡ **Background Workers** | 12 auto-triggered workers (audit, optimize, testgaps, etc.) |
| 🧩 **Plugin Marketplace** | 35 native Claude Code plugins in this repository |
| 🔌 **Multi-Provider** | Claude, GPT, Gemini, Cohere, Ollama with smart routing |
| 🛡️ **Security** | AIDefence, input validation, CVE remediation, path traversal prevention |
| 🌐 **Agent Federation** | Cross-installation agent collaboration with zero-trust security |
| 🔬 **MetaHarness** | Audit your AI agent setup: grade readiness, scan tool configs for security issues, snapshot the project to catch regressions |
| 🌍 **Self-hosted Web UI** | Multi-model chat with parallel MCP tool calling — the source is in this repo (`ruflo/src/ruvocal/`), self-hostable via Docker |
| 🎯 **GOAP Planner UI** | Goal-Oriented Action Planning front-end — plain-English goals → executable agent plans (`v3/goal_ui/`, self-hostable) |

<details>
<summary><strong>🧩 All 35 plugins</strong></summary>

#### Core & Orchestration

| Plugin | What it does |
|--------|-------------|
| [**ruflo-core**](plugins/ruflo-core/README.md) | Foundation — server, health checks, plugin discovery |
| [**ruflo-swarm**](plugins/ruflo-swarm/README.md) | Coordinate multiple agents as a team |
| [**ruflo-autopilot**](plugins/ruflo-autopilot/README.md) | Let agents run autonomously in a loop |
| [**ruflo-loop-workers**](plugins/ruflo-loop-workers/README.md) | Schedule background tasks on a timer |
| [**ruflo-workflows**](plugins/ruflo-workflows/README.md) | Reusable multi-step task templates |
| [**ruflo-federation**](plugins/ruflo-federation/README.md) | Agents on different machines collaborate securely |

#### Memory & Knowledge

| Plugin | What it does |
|--------|-------------|
| [**ruflo-agentdb**](plugins/ruflo-agentdb/README.md) | Fast vector database for agent memory |
| [**ruflo-rag-memory**](plugins/ruflo-rag-memory/README.md) | Smart retrieval — hybrid search, graph hops, diversity ranking |
| [**ruflo-rvf**](plugins/ruflo-rvf/README.md) | Save and restore agent memory across sessions |
| [**ruflo-ruvector**](plugins/ruflo-ruvector/README.md) | GPU-accelerated search, Graph RAG, 103 tools |
| [**ruflo-knowledge-graph**](plugins/ruflo-knowledge-graph/README.md) | Build and traverse entity relationship maps |

#### Intelligence & Learning

| Plugin | What it does |
|--------|-------------|
| [**ruflo-intelligence**](plugins/ruflo-intelligence/README.md) | Agents learn from past successes and get smarter |
| [**ruflo-graph-intelligence**](plugins/ruflo-graph-intelligence/) | Sublinear graph reasoning — PageRank, delta updates, complexity-aware execution |
| [**ruflo-daa**](plugins/ruflo-daa/README.md) | Dynamic agent behavior and cognitive patterns |
| [**ruflo-ruvllm**](plugins/ruflo-ruvllm/README.md) | Run local LLMs (Ollama, etc.) with smart routing |
| [**ruflo-goals**](plugins/ruflo-goals/README.md) | Break big goals into plans and track progress |

#### Code Quality & Testing

| Plugin | What it does |
|--------|-------------|
| [**ruflo-testgen**](plugins/ruflo-testgen/README.md) | Find missing tests and generate them automatically |
| [**ruflo-browser**](plugins/ruflo-browser/README.md) | Automate browser testing with Playwright |
| [**ruflo-jujutsu**](plugins/ruflo-jujutsu/README.md) | Analyze git diffs, score risk, suggest reviewers |
| [**ruflo-docs**](plugins/ruflo-docs/README.md) | Generate and maintain documentation automatically |

#### Security & Compliance

| Plugin | What it does |
|--------|-------------|
| [**ruflo-security-audit**](plugins/ruflo-security-audit/README.md) | Scan for vulnerabilities and CVEs |
| [**ruflo-aidefence**](plugins/ruflo-aidefence/README.md) | Block prompt injection, detect PII, safety scanning |

#### Architecture & Methodology

| Plugin | What it does |
|--------|-------------|
| [**ruflo-adr**](plugins/ruflo-adr/README.md) | Track architecture decisions with a living record |
| [**ruflo-ddd**](plugins/ruflo-ddd/README.md) | Scaffold domain-driven design — contexts, aggregates, events |
| [**ruflo-sparc**](plugins/ruflo-sparc/README.md) | Guided 5-phase development methodology with quality gates |
| [**ruflo-metaharness**](plugins/ruflo-metaharness/README.md) | Grade your agent setup, scan tool configs for security risks, track changes over time ([guide](docs/metaharness-user-guide.md)) |
| [**ruflo-arena**](plugins/ruflo-arena/README.md) | Competitive strategy tournaments — pit agent strategies against each other, hill-climb and co-evolve the winners |

#### DevOps & Observability

| Plugin | What it does |
|--------|-------------|
| [**ruflo-migrations**](plugins/ruflo-migrations/README.md) | Manage database schema changes safely |
| [**ruflo-observability**](plugins/ruflo-observability/README.md) | Structured logs, traces, and metrics in one place |
| [**ruflo-cost-tracker**](plugins/ruflo-cost-tracker/README.md) | Track token usage, set budgets, get cost alerts |

#### Extensibility

| Plugin | What it does |
|--------|-------------|
| [**ruflo-agent**](plugins/ruflo-agent/README.md) | Run agents — local WASM sandbox + managed cloud agents |
| [**ruflo-plugin-creator**](plugins/ruflo-plugin-creator/README.md) | Scaffold, validate, and publish your own plugins |

#### Domain-Specific

| Plugin | What it does |
|--------|-------------|
| [**ruflo-iot-cognitum**](plugins/ruflo-iot-cognitum/README.md) | IoT device management — trust scoring, anomaly detection, fleets |
| [**ruflo-neural-trader**](plugins/ruflo-neural-trader/README.md) | AI trading with 4 agents, backtesting, 112+ tools |
| [**ruflo-market-data**](plugins/ruflo-market-data/README.md) | Ingest market data, vectorize OHLCV, detect patterns |

</details>

## How It Works

```
User --> Claude Code / CLI
          |
          v
    Orchestration Layer
    (MCP Server, Router, Hooks)
          |
          v
    Swarm Coordination
    (Queen, Topology, Consensus)
          |
          v
    100+ Specialized Agents
    (coder, tester, reviewer, architect, security...)
          |
          v
    Memory & Learning
    (AgentDB, HNSW, SONA, ReasoningBank)
          |
          v
    LLM Providers
    (Claude, GPT, Gemini, Cohere, Ollama)
```

**The four pieces that are easy to confuse:**

- **The model** — Claude, GPT, Gemini, or another supported model supplies reasoning. K-I Agent is not a model; it is the machinery around one.
- **A skill** — instructions that teach a compatible agent how to approach a task (a playbook).
- **MCP** — Model Context Protocol: the standard way an assistant discovers and calls tools.
- **The runtime and plugins** — the software that actually performs the operations.

<details>
<summary><strong>🤝 Agent Federation — Slack for agents</strong></summary>

Federation gives agents **shared workspaces across trust boundaries**: agents on different machines, orgs, or cloud regions can discover each other, prove who they are (mTLS + ed25519), and collaborate — with PII stripped before anything leaves your node and every message auditable.

```
Your Agent --> [ Remove secrets ] --> [ Sign message ] --> [ Encrypted channel ]
Their Agent <-- [ Block attacks ] <-- [ Check identity ] <----------------------+
```

| Capability | How it works |
|---|---|
| 🔒 Zero-trust federation | Remote agents start untrusted. Identity proven via mTLS + ed25519 challenge-response. |
| 🛡️ PII-gated data flow | A detection pipeline scans every outbound message: BLOCK, REDACT, HASH, or PASS per trust level. |
| 📊 Behavioral trust scoring | Peers are continuously evaluated. Upgrades require history; downgrades are instant. |
| 📋 Compliance built-in | Audit trails as compliance modes; every federation event produces a structured record. |
| 🤝 9 MCP tools + 10 CLI commands | `federation init`, `federation join`, `federation send`, `federation trust`, `federation audit`… |

**The one rule to remember: never put a secret in a federation message.**

📘 Full guide: [`docs/federation/`](docs/federation/)

</details>

## Documentation

### 🇮🇷 Persian (فارسی)

| Doc | Description |
|-----|-------------|
| **[README فارسی](README.fa.md)** | معرفی کامل پروژه + راهنمای نصب به فارسی |
| **[شروع سریع (فارسی)](docs/fa/quickstart.md)** | نصب و اولین پروژه قدم‌به‌قدم |
| **[K-I Agent به زبان ساده](docs/fa/k-i-agent-explained.md)** | آموزش کامل — از ایده پایه تا تیم‌های هوشمند، حافظه و فدراسیون |
| **[راهنمای کاربر (فارسی)](docs/fa/userguide.md)** | دستورات اصلی، حافظه، سوارم، MCP و پیکربندی |

### English

| Doc | When to read it |
|-----|-----------------|
| **[K-I Agent Explained](docs/k-i-agent-explained.md)** | A 14-chapter tutorial: from the basic idea to a first useful task, memory, agent teams, plugins, cost and verification. |
| **[Status](docs/STATUS.md)** | What currently works — capability counts, test baselines, what's next. |
| **[User Guide](docs/USERGUIDE.md)** | Daily reference — every command, every config flag, every plugin. |
| **[MetaHarness Guide](docs/metaharness-user-guide.md)** | Grade your agent setup, scan tool configs for security, detect regressions. |
| **[Federation](docs/federation/)** | Zero-trust cross-machine agent collaboration — setup, trust levels, mesh layer. |
| **[Verification](verification/README.md)** | Cryptographically prove your installed bytes match the signed witness. |
| **[Team Gateway Checklist](docs/TEAM-GATEWAY-CHECKLIST.md)** | Before-merge gates, dual-mode handoff, memory namespace sharing. |

## Security

K-I Agent applies defense-in-depth at system boundaries:

- **Input validation** using Zod schemas for all public API inputs
- **Parameterized SQL queries** to prevent injection attacks
- **Path traversal prevention** via the `PathValidator` module
- **Command injection protection** via the `SafeExecutor` module
- **AIDefence** — prompt-injection blocking and PII detection

See [SECURITY.md](SECURITY.md) for the vulnerability reporting policy.

## Support

| Resource | Link |
|----------|------|
| Documentation | [User Guide](docs/USERGUIDE.md) · [Persian guide](README.fa.md) |
| Issues & Bugs | [GitHub Issues](https://github.com/kiarash707/agents/issues) |
| Contributing | [CONTRIBUTING.md](CONTRIBUTING.md) |

## License & Credits

**K-I Agent** is licensed under the [MIT License](LICENSE).

This project is a rebranded fork that builds on the open-source project
**[ruflo](https://github.com/ruvnet/ruflo)** by **[ruvnet](https://github.com/ruvnet)**.
The original code is available under the MIT License, which requires its
copyright notice to be retained in [LICENSE](LICENSE) — that notice is kept
intact out of respect for the original author and the license terms.
