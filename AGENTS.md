# Agent-Kit: Core Agents Documentation

This document catalogs all agents included in the Agent-Kit collection. These agents are portable, reusable components that can be integrated into any project.

## How to Use This Documentation

1. **Find an agent**: Browse the list below
2. **Check triggers**: Use the listed phrases to activate agents
3. **Review purpose**: Understand what each agent does
4. **Read AGENT.md**: See agent folder for detailed instructions

---

## create-agent-agent

**Purpose**: Automatically detects requests for new agents and generates complete agent folder structures with all required files following unified standards

**Scope**: Agent creation, validation, and registration  
**Status**: Active  
**Triggers**: "Create an agent that...", "I want an agent which...", "Make me an agent for...", "I need an agent that..."  
**Location**: `.github/agents/create-agent-agent/` (or `agents/` in library)  
**Entry Point**: `AGENT.md`

---

## doc-registry-agent

**Purpose**: Monitors all agents and maintains human-readable documentation with summaries of each agent's name, purpose, and activation triggers

**Scope**: Agent registration, documentation maintenance, and discovery  
**Status**: Active  
**Triggers**: "Register agent", "Update AGENTS.md", "List all agents", "Refresh agent docs"  
**Location**: `.github/agents/doc-registry-agent/` (or `agents/` in library)  
**Entry Point**: `AGENT.md`

---

## distribute-agents-agent

**Purpose**: Automatically detects new projects and synchronizes agents from the GitHub repository into `.github/agents/`. Manages lockfile-based version control to prevent unwanted overwrites.

**Scope**: Project-level agent distribution, lockfile management, safe updates  
**Status**: Active  
**Triggers**: "Distribute agents", "Setup agents", "Sync agents", "Update all agents", "Add new agents", "Update agents to latest"  
**Location**: `.github/agents/distribute-agents-agent/` (or `agents/` in library)  
**Entry Point**: `AGENT.md`  
**Behavior Modes**: Auto-sync new projects, lockfile-respecting, conflict-aware, customization-preserving  
**Source Repository**: https://github.com/skelacc/AGENTS-library

---

## architecture-monitor-agent

**Purpose**: Monitors project architecture and KPIs, generating documentation with graphs and changelog updates.

**Scope**: Architecture visualization, KPI tracking, documentation updates in /documentation  
**Status**: Active  
**Triggers**: "Update architecture docs", "Generate architecture report", "Refresh project KPIs", "Every 2 commits"  
**Location**: `.github/agents/architecture-monitor-agent/` (or `agents/` in library)  
**Entry Point**: `AGENT.md`  
**Outputs**: dependency-graph, module-graph, service-graph, kpis, changelog

---

## test-verification-agent

**Purpose**: Generates tests, runs them, and records results under /tests/, plus persona walkthrough feedback with traceable evidence.

**Scope**: Project purpose discovery, test authoring, test execution, UX persona walkthroughs  
**Status**: Active  
**Triggers**: "Generate tests", "Write tests", "Verify project functionality", "Run test validation", "Create user personas"  
**Location**: `.github/agents/test-verification-agent/` (or `agents/` in library)  
**Entry Point**: `AGENT.md`  
**Outputs**: test-plan, test-cases, test-results, persona-walkthroughs, scope

---

## Entry Point: AGENT.md

Each agent folder contains **AGENT.md** as the entry point for VS Code Copilot. This file includes:
- Purpose and scope
- Behavior rules and operational guidelines
- Input interpretation and trigger detection
- Output rules and formats
- Error handling procedures

Related files:
- **agent.json** — Metadata and configuration
- **examples.md** — Usage examples and workflows

---

## Configuration

Agents use configurable paths. Default structure (in project):
```
your-project/
├── .github/
│   ├── agents/          # Agent folder location
│   │   ├── create-agent-agent/
│   │   ├── doc-registry-agent/
│   │   ├── distribute-agents-agent/
│   │   ├── architecture-monitor-agent/
│   │   └── test-verification-agent/
│   ├── config.json      # Optional path configuration
│   └── skills/          # Optional skills directory
├── agents.lockfile      # Version tracking and lockfile
└── AGENTS.md           # This file (auto-maintained)
```

Default locations are configurable via `config.json`. See [SETUP.md](SETUP.md) for configuration details.

## Creating New Agents

Use the create-agent-agent:
```
"Create an agent that [describe functionality]"
```

The new agent will be generated in `.github/agents/<agent-name>/` with:
- `AGENT.md` — Entry point for VS Code Copilot
- `agent.json` — Metadata
- `examples.md` — Usage examples

---

## Quick Links

- **Setup**: [SETUP.md](SETUP.md) — Installation and configuration guide
- **Overview**: [README.md](README.md) — Project overview
- **Standards**: [prompts/agent-standards.md](prompts/agent-standards.md) — Agent creation standards
- **Examples**: See [examples/](examples/) for integration patterns

---

**Agent-Kit Version**: 1.0.0  
**Last Updated**: 2026-02-20  
**Maintained by**: doc-registry-agent  
**Repository**: https://github.com/skelacc/AGENTS-library
