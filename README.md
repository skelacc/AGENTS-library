# Agent-Kit: Reusable AI Agent Library

A portable collection of AI agents stored in GitHub and automatically synchronized into your projects.

## Overview

**Agent-Kit** is a library of reusable agent definitions that:
- Live in a central GitHub repository: https://github.com/skelacc/AGENTS-library
- Auto-sync into your projects via the **distribute-agents-agent (DAA)**
- Deploy to `.github/agents/` (or project root as fallback)
- Use lockfile-based versioning to prevent unwanted overwrites
- Work seamlessly with VS Code Copilot (agents named `AGENT.md`)

## Quick Start

## New Workflow (2026+)

1. **Clone this repository** (AGENTS-library) into a separate workspace (not your target project).
2. **Open the AGENTS-library workspace in VS Code.**
3. **Invoke the Distribute-Agents-Agent (DAA)** and provide the absolute path to the project you want to update (e.g., `/home/user/myproject`).
4. **DAA will update the agents in the target project's `.github/agents/` directory.**
5. **Choose your update mode:**
	- "Update all agents" (full replacement)
	- "Add new agents" (preserve existing, add new only)
	- "Sync agents" (auto-detect best mode)
	- "Setup agents" (initialize for new project)

**Manual Setup** (if you prefer):
```bash
cp -r agents/ <target-project>/.github/agents/
```

Then create `agents.lockfile` in your project root — see [SETUP.md](SETUP.md) for details.

## Using Agents

Mention trigger phrases naturally:

| Phrase | Agent | Action |
|--------|-------|--------|
| "Create an agent that..." | create-agent-agent | Generates new agent |
| "Update AGENTS.md" | doc-registry-agent | Refreshes documentation |
| "List all agents" | doc-registry-agent | Shows available agents |
| "Update all agents" | distribute-agents-agent | Syncs latest from GitHub |

**Example**:
```
"Create an agent that validates API responses"
→ New agent created in .github/agents/api-validator-agent/
```

## Key Features

- **VS Code Copilot Ready**: Each agent has `AGENT.md` entry point for automatic discovery
- **Auto-Registration**: DAA handles all distribution and lockfile management
- **Smart Updates**: Three sync modes — full update, add-new-only, or preserve
- **Customization-Safe**: Tracks local changes, protects against unwanted overwrites
- **Zero Configuration**: Works with default paths; customize as needed

## Project Structure

After DAA syncs:
```
your-project/
├── .github/
│   └── agents/
│       ├── create-agent-agent/
│       │   ├── agent.json
│       │   ├── AGENT.md          ← Entry point for VS Code Copilot
│       │   └── examples.md
│       ├── doc-registry-agent/
│       ├── distribute-agents-agent/
│       ├── architecture-monitor-agent/
│       └── test-verification-agent/
├── agents.lockfile               ← Prevents accidental overwrites
└── AGENTS.md                      ← Agent catalog (auto-maintained)
```

## Included Agents

| Agent | Purpose |
|-------|---------|
| **create-agent-agent** | Generates new agents from natural language descriptions |
| **doc-registry-agent** | Maintains AGENTS.md documentation automatically |
| **distribute-agents-agent** | Syncs agents from GitHub into your projects |
| **architecture-monitor-agent** | Tracks project structure and KPIs |
| **test-verification-agent** | Generates tests and validates functionality |

See [AGENTS.md](AGENTS.md) for full agent catalog.

## Next Steps

1. **Setup**: See [SETUP.md](SETUP.md) for detailed installation and configuration
2. **Triggers**: Use natural language to activate agents (examples above)
3. **Customize**: Edit agents in `.github/agents/<agent-name>/` as needed
4. **Extend**: Create new agents with "Create an agent that..."

## Documentation

- [SETUP.md](SETUP.md) — Installation, configuration, and troubleshooting
- [AGENTS.md](AGENTS.md) — Complete agent catalog with descriptions
- [prompts/agent-standards.md](prompts/agent-standards.md) — Standards for creating agents

---

**Version**: 1.0.0  
**Last Updated**: 2026-02-20  
**Repository**: https://github.com/skelacc/AGENTS-library
