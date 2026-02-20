# Agent-Kit: Reusable AI Agent Library

A portable collection of agent definitions stored in a central GitHub repository and synchronized into projects via the distribute-agents-agent (DAA).

## What is Agent-Kit?

Agent-Kit is a library of reusable agent definitions that:
- **Lives in GitHub**: Stored at https://github.com/skelacc/AGENTS-library
- **Auto-syncs to projects**: DAA detects new projects and downloads agent-kit
- **Locked per-project**: Each project has an `agents.lockfile` preventing unwanted overwrites
- **Non-conflicting**: Agents copied INTO projects, not stored globally

## Setup

The distribute-agents-agent (DAA) handles all setup automatically:

```bash
# DAA detects new project and syncs automatically
# Creates agents.lockfile in your project
# No manual setup required!
```

**Manual setup** (if preferred):
```bash
# Copy agent-kit into your project
cp -r agent-kit project/.github/agents/
# or
cp -r agent-kit project/
```

## Quick Usage

Agents activate automatically when you mention trigger phrases:

```
"Create an agent that validates API responses"
→ Creates new agent in agents/ directory

"Update AGENTS.md"
→ Refreshes agent documentation

"List all agents"
→ Shows available agents
```

## Kit Structure

```
agent-kit/
├── README.md              # Overview (this file)
├── SETUP.md               # Installation & configuration guide
├── AGENTS.md              # Registered agent catalog (auto-maintained)
├── config.json            # Path configuration
├── agents/                # Agent definitions
├── skills/                # Reusable agent procedures
├── prompts/               # Agent standards & guidelines
├── templates/             # Templates for quick customization
└── examples/              # Integration examples
```

## Included Agents

Check [AGENTS.md](AGENTS.md) for the complete catalog of available agents.

## Getting Started

See [SETUP.md](SETUP.md) for detailed installation and configuration instructions.

---

**Version**: 1.0.0  
**Last Updated**: 2026-02-20
