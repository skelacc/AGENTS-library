# Agent-Kit Setup Guide

Agent-Kit is automatically synchronized to your projects via the **distribute-agents-agent (DAA)**. Agents are deployed to your project's `.github/agents/` directory.

## How It Works

```
Open new project
↓
DAA detects missing agents.lockfile
↓
DAA fetches agents from GitHub repository
↓
DAA creates .github/agents/ with agent folders
↓
DAA creates agents.lockfile for version tracking
↓
✓ Agents ready to use with VS Code Copilot
```

## Automatic Setup (Recommended)

No manual setup needed! The DAA handles everything automatically:

1. **Open** your project in VS Code
2. **Wait** for DAA to detect missing agents.lockfile
3. **Done** — agents appear in `.github/agents/`

The lockfile prevents accidental overwrites on future syncs.

## Manual Setup (Alternative)

If you prefer to set up agents manually:

```bash
# Copy agents into project
cp -r agents/ your-project/.github/agents/

# Create lockfile
cat > your-project/agents.lockfile << 'LOCKFILE'
{
  "synced_at": "2026-02-20T00:00:00Z",
  "source": "https://github.com/skelacc/AGENTS-library",
  "location": ".github/agents",
  "agents": {
    "create-agent-agent": "1.0.0",
    "doc-registry-agent": "1.0.0",
    "distribute-agents-agent": "1.0.0",
    "architecture-monitor-agent": "1.0.0",
    "test-verification-agent": "1.0.0"
  }
}
LOCKFILE
```

## Project Structure

After setup, your project will have:

```
your-project/
├── .github/
│   └── agents/
│       ├── create-agent-agent/
│       │   ├── agent.json           # Agent metadata
│       │   ├── AGENT.md             # Entry point (VS Code Copilot)
│       │   └── examples.md          # Usage examples
│       ├── doc-registry-agent/
│       ├── distribute-agents-agent/
│       ├── architecture-monitor-agent/
│       └── test-verification-agent/
├── agents.lockfile                  # Version & customization tracking
└── AGENTS.md                         # Agent catalog (auto-maintained)
```

## Agent Entry Point

VS Code Copilot **requires** agents to be named `AGENT.md` to be auto-discovered. Each agent folder contains:

- **AGENT.md** — Entry point with purpose, behavior rules, and triggers
- **agent.json** — Metadata and configuration
- **examples.md** — Usage examples and workflows

## Configuration

Agents use configurable paths in `.github/config.json`:

```json
{
  "paths": {
    "agents_directory": ".github/agents",
    "skills_directory": ".github/skills",
    "prompts_directory": ".github/prompts"
  },
  "documentation": {
    "agents_file": "AGENTS.md",
    "location": "project_root"
  }
}
```

**The defaults work for most projects.** Only customize if agents are in a different location.

### Custom Paths

If agents are nested differently (e.g., `tools/agent-kit/`):

```json
{
  "paths": {
    "agents_directory": "tools/agent-kit/agents",
    "skills_directory": "tools/agent-kit/skills",
    "prompts_directory": "tools/agent-kit/prompts"
  }
}
```

## Using Agents

Agents activate automatically via trigger phrases. Use natural language:

### Trigger Examples

| Phrase | Agent | Result |
|--------|-------|--------|
| "Create an agent that..." | create-agent-agent | New agent in `.github/agents/` |
| "Update AGENTS.md" | doc-registry-agent | Documentation refreshed |
| "List all agents" | doc-registry-agent | Shows all available agents |
| "Update all agents" | distribute-agents-agent | Syncs latest from GitHub |
| "Add new agents" | distribute-agents-agent | Adds only new agents (preserves existing) |

**Example**:
```
"Create an agent that validates API responses"
↓
New folder: .github/agents/api-validator-agent/
├── agent.json
├── AGENT.md
└── examples.md
```

## Synchronizing Agents

### Check for Updates
```
"Update all agents"
```
Fetches latest from GitHub and replaces all agent files.

### Add New Agents Only
```
"Add new agents"
```
Downloads only new agents from GitHub. Preserves any customizations you've made locally.

### Manual Sync
```
"Distribute agents"
or
"Setup agents"
```
DAA auto-detects the best sync mode based on your lockfile.

## Lockfile

The `agents.lockfile` in your project root tracks:
- When agents were last synced
- Which agents are installed and at what version
- Any local customizations (changes you made)
- Protects against accidental overwrites

**Example lockfile**:
```json
{
  "synced_at": "2026-02-20T10:30:00Z",
  "source": "https://github.com/skelacc/AGENTS-library",
  "location": ".github/agents",
  "agents": {
    "create-agent-agent": "1.0.0",
    "doc-registry-agent": "1.0.0",
    "distribute-agents-agent": "1.0.0",
    "architecture-monitor-agent": "1.0.0",
    "test-verification-agent": "1.0.0"
  },
  "customizations": {
    "create-agent-agent": ["Modified AGENT.md", "Added new skill"]
  }
}
```

DAA respects the lockfile:
- ✓ First sync: Creates lockfile automatically
- ✓ Later syncs: Won't overwrite without permission
- ✓ Customizations: Tracked and protected
- ✓ Updates: Handled safely via sync modes

## Troubleshooting

### Agents Not Syncing?

1. **Check internet connection** — DAA needs to reach GitHub
2. **Verify permissions** — `.github/` directory must be writable
3. **Force sync**: "Distribute agents" → "Setup agents"
4. **Check lockfile**: Verify `agents.lockfile` exists in project root

### Agent Not Found After Sync?

1. **Verify sync completed** — look for `agents.lockfile`
2. **Check location** — navigate to `.github/agents/`
3. **Reload AI context** — close and reopen VS Code

### DAA Refuses to Update (Customizations Protected)?

You've modified agents locally. Options:

- **Keep changes**: "Add new agents" (gets new agents only)
- **Replace all**: "Update all agents" (DAA will back up changes)

### Configuration Not Applied?

1. **Verify syntax** — check `.github/config.json` for valid JSON
2. **Check paths** — ensure paths match your actual folder structure
3. **Restart** — close and reopen VS Code

## Updating Agents Over Time

### Initial Sync
DAA creates `agents.lockfile` and copies all agents.

### Adding New Agents
```
"Add new agents"
```
Downloads new agents from GitHub without replacing existing ones.

### Full Update
```
"Update all agents"
```
Replaces all agents with latest versions. Warns if customizations exist.

### Preserving Customizations
- Always use "Add new agents" for safety
- Customize agents *after* they're synced
- DAA tracks changes in lockfile
- Locked agents won't be overwritten accidentally

## Getting Help

### Read More
- [README.md](README.md) — Quick overview
- [AGENTS.md](AGENTS.md) — Complete agent catalog
- Individual `AGENT.md` files — Agent-specific instructions

### Examples
See `/examples/` directory for integration patterns and workflows.

---

**Version**: 1.0.0  
**Last Updated**: 2026-02-20  
**Repository**: https://github.com/skelacc/AGENTS-library
