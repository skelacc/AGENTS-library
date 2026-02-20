# Agent-Kit: Core Agents Documentation

This document catalogs all agents included in the Agent-Kit collection. These agents are portable, reusable components that can be integrated into any project.

## How to Use This Documentation

1. **Find an agent**: Browse the list below
2. **Check triggers**: Use the listed phrases to activate agents
3. **Review purpose**: Understand what each agent does
4. **See location**: Find agent files for customization

---

## create-agent-agent
**Purpose**: Automatically detects requests for new agents and generates complete agent folder structures with all required files following unified standards
**Scope**: Agent creation, validation, and registration
**Status**: Active
**Triggers**: "Create an agent that...", "I want an agent which...", "Make me an agent for...", "I need an agent that..."
**Location**: `agent-kit/agents/create-agent-agent/`
**Configurable Paths**: agents_directory, skills_directory, prompts_directory

---

## doc-registry-agent
**Purpose**: Monitors all agents and maintains human-readable documentation with summaries of each agent's name, purpose, and activation triggers
**Scope**: Agent registration, documentation maintenance, and discovery
**Status**: Active
**Triggers**: "Register agent", "Update AGENTS.md", "List all agents", "Refresh agent docs"
**Location**: `agent-kit/agents/doc-registry-agent/`
**Configurable Paths**: agents_directory, documentation.agents_file, documentation.location

---

## distribute-agents-agent
**Purpose**: Automatically detects new projects and synchronizes agent-kit from the repository. Manages lockfile-based version control to prevent unwanted overwrites.
**Scope**: Project-level agent distribution, lockfile management, safe updates
**Status**: Active
**Triggers**: "Distribute agents", "Setup agents", "Sync agents", "Update all agents", "Add new agents", "Update agents to latest"
**Location**: `agent-kit/agents/distribute-agents-agent/`
**Behavior Modes**: Auto-sync new projects, lockfile-respecting, conflict-aware, customization-preserving
**Source Repository**: https://github.com/skelacc/AGENTS-library

---

## architecture-monitor-agent
**Purpose**: Monitors project architecture and KPIs, generating documentation with graphs and changelog updates.
**Scope**: Architecture visualization, KPI tracking, documentation updates in /documentation
**Status**: Active
**Triggers**: "Update architecture docs", "Generate architecture report", "Refresh project KPIs", "Every 2 commits"
**Location**: `agent-kit/agents/architecture-monitor-agent/`
**Outputs**: dependency-graph, module-graph, service-graph, kpis, changelog

---

## Configuration

All paths are configurable via `agent-kit/config.json`. Default structure:
- Agents: `agent-kit/agents/`
- Skills: `agent-kit/skills/`
- Prompts: `agent-kit/prompts/`
- Documentation: `AGENTS.md` (root)

See [SETUP.md](SETUP.md) for setup instructions.

## Creating New Agents

Use the create-agent-agent:
```
"Create an agent that [describe functionality]"
```

The new agent will be generated in your configured agents_directory with all required files.

## Need Help?

- Setup: Read [SETUP.md](SETUP.md)
- Examples: See [examples/integration-examples.md](examples/integration-examples.md)
- Standards: Review [prompts/agent-standards.md](prompts/agent-standards.md)
- Customization: Edit [config.json](config.json)

---

**Agent-Kit Version**: 1.0.0  
**Last Updated**: 2026-02-20  
**Maintained by**: doc-registry-agent
