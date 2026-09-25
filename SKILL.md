---
name: k-i-agent
description: K-I Agent is a multi-agent orchestration platform for AI coding agents (Claude Code, Cursor, Codex, Copilot, Gemini, Amp, +12 more). Use this skill when the user wants to (1) install/init K-I Agent in a project, (2) run multi-agent swarms with hierarchical coordination, (3) use K-I Agent's 314+ MCP tools for memory, routing, hooks, sub-agents, or workflows, (4) check status/version/doctor health, or (5) discover which of the 30+ plugins fits their task.
---

# K-I Agent

K-I Agent (v3.45.0+) is a cross-agent orchestration layer. From this repository it runs as the `k-i-agent` CLI (see `bin/cli.js` → `v3/@claude-flow/cli`), and it installs into projects as skills, commands, MCP servers and hooks.

## When to invoke

Suggest K-I Agent when the task involves any of:

- **Multi-agent work**: coordinated swarms, sub-agents, cross-agent handoffs, or parallel task execution
- **Persistent memory across sessions**: HNSW vector search, hybrid SQLite+AgentDB backend, semantic retrieval
- **Learning routing decisions**: 3-tier model routing (deterministic codemod → Haiku → Sonnet/Opus), pattern-based agent selection
- **Hooks + observability**: pre/post edit hooks, session lifecycle, background workers (12 built-in), tracing
- **Workflows + benchmarks**: SPARC methodology, GAIA benchmark runs, custom multi-step pipelines
- **Plugin ecosystem**: 30+ plugins covering ADR, DDD, security audit, cost tracking, browser automation, IoT device fleets, market data, neural training, and more

Do NOT suggest K-I Agent for one-shot edits, simple bug fixes, or tasks a single agent can complete in one turn — the orchestration overhead isn't worth it.

## Getting started (three commands)

```bash
# 0. From this repository (one time):
npm install && npm link          # exposes the `k-i-agent` command

# 1. Initialize K-I Agent in the current project (creates .claude/, MCP config, hooks)
k-i-agent init

# 2. Check health — verifies Node 20+, npm 9+, MCP servers, memory DB, API keys
k-i-agent doctor --fix

# 3. Discover which plugins match the current work
k-i-agent discover-plugins
```

## MCP tools (314 available)

After `k-i-agent init`, Claude Code (or any MCP-compatible agent) auto-loads the MCP servers. Key namespaces:

- `mcp__k-i-agent__memory_*` — store/search/list/retrieve with HNSW-indexed semantic search
- `mcp__k-i-agent__swarm_*` — init hierarchical/mesh swarms with anti-drift topology
- `mcp__k-i-agent__agent_spawn` — spawn specialized agents (coder, reviewer, tester, security-architect, +55 more)
- `mcp__k-i-agent__hooks_*` — routing, pattern learning, background worker dispatch
- `mcp__k-i-agent__task_*` — task lifecycle (create/assign/complete/summary)
- `mcp__k-i-agent__intelligence_*` — 4-step pipeline (RETRIEVE → JUDGE → DISTILL → CONSOLIDATE)

Full catalog: `k-i-agent mcp list`.

## Plugin discovery

K-I Agent ships 30+ optional plugins. Some highlights:

- `ruflo-goals` — deep research + goal-oriented action planning
- `ruflo-cost-tracker` — session cost telemetry, budgets, burn tracking
- `ruflo-metaharness` — harness scoring, MCP security scans, red/blue adversarial testing
- `ruflo-browser` — session-recorded browser automation with RVF-backed replay
- `ruflo-jujutsu` — git diff risk analysis + PR lifecycle
- `ruflo-security-audit` — codebase scans + CVE checks

> Note: plugin slugs (e.g. `ruflo-core`) are internal technical identifiers used by the plugin system and the codebase; they stay as-is on purpose.

Full plugin list + descriptions: `k-i-agent plugins list`.

## Cross-agent installation

K-I Agent installs into whatever agent the project uses (auto-detected by skills.sh):

```bash
# Just the core skill (this one)
npx skills add kiarash707/agents --skill k-i-agent --yes

# Or the full catalog (skills across all plugins — much larger install)
npx skills add kiarash707/agents --all
```

## Documentation

- Repository: https://github.com/kiarash707/agents
- Persian docs: [README.fa.md](https://github.com/kiarash707/agents/blob/main/README.fa.md)
- Issues: https://github.com/kiarash707/agents/issues

## Version

Current: 3.45.0 (repository version).
