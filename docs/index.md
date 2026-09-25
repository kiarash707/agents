---
layout: default
title: K-I Agent Marketplace
description: Claude Code native agents, swarms, workers, and MCP tools for continuous software engineering
---

# K-I Agent Marketplace

**Installable agentic workflows for Claude Code -- not just commands.**

K-I Agent provides native Claude Code plugins for multi-agent orchestration, /loop workers, security auditing, memory-powered RAG, and test generation.

## Quick Install

```bash
# Add the marketplace
/plugin marketplace add kiarash707/agents

# Install plugins
/plugin install ruflo-core@k-i-agent
/plugin install ruflo-swarm@k-i-agent
/plugin install ruflo-loop-workers@k-i-agent
```

## Plugins

| Plugin | Description | Install |
|--------|-------------|---------|
| **ruflo-core** | MCP server, base commands, project config | `/plugin install ruflo-core@k-i-agent` |
| **ruflo-swarm** | Teams, agents, Monitor streams, worktree isolation | `/plugin install ruflo-swarm@k-i-agent` |
| **ruflo-loop-workers** | /loop workers, CronCreate, cache-aware scheduling | `/plugin install ruflo-loop-workers@k-i-agent` |
| **ruflo-security-audit** | Security review, dependency checks, policy gates | `/plugin install ruflo-security-audit@k-i-agent` |
| **ruflo-rag-memory** | RuVector memory, HNSW search, AgentDB | `/plugin install ruflo-rag-memory@k-i-agent` |
| **ruflo-testgen** | Test gap detection, coverage analysis, TDD workflow | `/plugin install ruflo-testgen@k-i-agent` |
| **ruflo-docs** | Doc generation, drift detection, API docs | `/plugin install ruflo-docs@k-i-agent` |
| **ruflo-autopilot** | Autonomous /loop completion, learning, prediction | `/plugin install ruflo-autopilot@k-i-agent` |
| **ruflo-intelligence** | Self-learning SONA patterns, trajectory learning, routing | `/plugin install ruflo-intelligence@k-i-agent` |
| **ruflo-agentdb** | AgentDB controllers, HNSW vector search, RuVector | `/plugin install ruflo-agentdb@k-i-agent` |
| **ruflo-aidefence** | AI safety scanning, PII detection, prompt defense | `/plugin install ruflo-aidefence@k-i-agent` |
| **ruflo-browser** | Playwright browser automation, testing, scraping | `/plugin install ruflo-browser@k-i-agent` |
| **ruflo-jujutsu** | Git diff analysis, risk scoring, reviewer recs | `/plugin install ruflo-jujutsu@k-i-agent` |
| **ruflo-agent** | Sandboxed WASM agents and gallery sharing | `/plugin install ruflo-agent@k-i-agent` |
| **ruflo-workflows** | Workflow templates, orchestration, lifecycle | `/plugin install ruflo-workflows@k-i-agent` |
| **ruflo-daa** | Dynamic Agentic Architecture, cognitive patterns | `/plugin install ruflo-daa@k-i-agent` |
| **ruflo-ruvllm** | Local LLM inference, MicroLoRA, chat formatting | `/plugin install ruflo-ruvllm@k-i-agent` |
| **ruflo-rvf** | RVF portable memory, session persistence | `/plugin install ruflo-rvf@k-i-agent` |
| **ruflo-plugin-creator** | Scaffold, validate, publish new plugins | `/plugin install ruflo-plugin-creator@k-i-agent` |

## How It Works

K-I Agent plugins extend Claude Code with:
- **Skills** -- Teach Claude Code new workflows (swarm init, /loop workers, security scans)
- **Commands** -- Slash commands for common operations (/status, /audit, /memory)
- **Agents** -- Specialized agent definitions (coder, reviewer, architect, security-auditor)
- **MCP Server** -- 314 tools for coordination, memory, neural learning, and more

## Claude Code Native Integration

K-I Agent plugins use Claude Code's native capabilities when available:

| Feature | Plugin | Claude Code Native |
|---------|--------|--------------------|
| Periodic workers | ruflo-loop-workers | `/loop` + `ScheduleWakeup` |
| Live monitoring | ruflo-swarm | `Monitor` tool |
| Background jobs | ruflo-loop-workers | `CronCreate` |
| Agent isolation | ruflo-swarm | `isolation: "worktree"` |
| Multi-agent comms | ruflo-swarm | `TeamCreate` + `SendMessage` |
| Cross-session | ruflo-core | `PushNotification` + `RemoteTrigger` |
| Autonomous loops | ruflo-autopilot | `/loop` + `ScheduleWakeup` + autopilot MCP |

## Trust & Security

- All plugins are open source -- review before installing
- MCP servers run locally, no data leaves your machine
- Plugins declare required permissions in their manifest
- Pin versions for production use: `/plugin install ruflo-core@0.1.0@k-i-agent`
- Security scanning available via ruflo-security-audit
- Cryptographically-signed [witness manifest](../verification.md) attests every documented fix; see [Validation System](validation/) for the three-layer regression-protection stack

## Links

- [GitHub Repository](https://github.com/kiarash707/agents)
- [npm Packages](https://www.npmjs.com/package/@claude-flow/cli)
- [ADR-091: Native Integration](https://github.com/kiarash707/agents/blob/main/v3/docs/adr/ADR-091-loop-monitor-native-integration.md)
- [Issues & Support](https://github.com/kiarash707/agents/issues)
