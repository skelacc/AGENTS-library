# Agent-Kit Setup Guide

Agent-Kit is automatically synchronized to your projects via the distribute-agents-agent (DAA).

## How It Works

1. **DAA Detects**: When you open a project without `agents.lockfile`
2. **DAA Downloads**: Fetches latest agent-kit from https://github.com/skelacc/AGENTS-library
3. **DAA Creates Lockfile**: Locks the synced agents to prevent overwrites
4. **Ready to Use**: Agents available immediately in your project

## Automatic Setup (Recommended)

No manual setup needed! The DAA handles everything:

```
Open new project
  ↓
DAA detects missing agents.lockfile
  ↓
DAA fetches agent-kit from GitHub
  ↓
DAA creates .github/agents/ (or agent-kit/)
  ↓
DAA creates agents.lockfile
  ↓
✓ Agents ready to use
```

## Manual Setup (Alternative)

If you prefer to set up manually:

```bash
# Option 1: Into .github/agents/ (GitHub config directory)
cp -r agent-kit project/.github/agents/

# Option 2: Into project root
cp -r agent-kit project/agent-kit/

# Option 3: Into docs folder
cp -r agent-kit project/docs/agent-kit/
```

Then create an `agents.lockfile`:
```bash
cat > agents.lockfile << 'EOF'
{
  "synced_at": "2026-02-20T00:00:00Z",
  "source": "https://github.com/skelacc/AGENTS-library",
  "location": ".github/agents",
  "agents": {
    "create-agent-agent": "1.0.0",
    "doc-registry-agent": "1.0.0",
    "distribute-agents-agent": "1.0.0"
  }
}
EOF
```

## Configuration

The `agent-kit/config.json` file is pre-configured for relative paths:

```json
{
  "paths": {
    "agents_directory": "agents",
    "skills_directory": "skills",
    "prompts_directory": "prompts"
  },
  "documentation": {
    "agents_file": "AGENTS.md",
    "location": "project_root"
  }
}
```

**No edits needed** — works for any project location.

### If Agent-Kit is Nested Differently

**Agent-Kit at `project/tools/agent-kit/`:**
```json
{
  "paths": {
    "agents_directory": "tools/agent-kit/agents",
    "skills_directory": "tools/agent-kit/skills",
    "prompts_directory": "tools/agent-kit/prompts"
  }
}
```

**Agent-Kit at `project/.github/agents/`:**
```json
{
  "paths": {
    "agents_directory": ".github/agents/agents",
    "skills_directory": ".github/agents/skills",
    "prompts_directory": ".github/agents/prompts"
  }
}
```
```json
{
  "paths": {
    "agents_directory": ".github/agent-kit/agents",
    "skills_directory": ".github/agent-kit/skills"
  }
}
```

## Using Agents

Agents activate automatically via trigger phrases. Just mention them naturally:

| Phrase | Agent | Action |
|--------|-------|--------|
| "Create an agent that..." | create-agent-agent | Generates new agent |
| "Update AGENTS.md" | doc-registry-agent | Refreshes documentation |
| "List all agents" | doc-registry-agent | Displays available agents |

**Example**: 
```
"Create an agent that validates API responses"
→ New agent generated in agents/api-validator-agent/
```

## File Locations

Quick reference for where files are stored:

```
agent-kit/
├── config.json            # Paths & settings
├── agents/                # All agent definitions
│   └── <agent-name>/
│       ├── agent.json     # Metadata & triggers
│       ├── instructions.md # Behavior rules
│       └── examples.md    # Usage examples
├── skills/                # Reusable procedures
├── prompts/               # Standards & guidelines
├── templates/             # Quick-start templates
└── examples/              # Integration patterns
```

## Common Tasks

### Create a Custom Agent
```
"Create an agent that runs linting on changed files"


## Using Agents

Agents activate immediately via trigger phrases:

| Trigger | Agent | Result |
|---------|-------|--------|
| "Create an agent that..." | create-agent-agent | Creates new agent in your project |
| "Update AGENTS.md" | doc-registry-agent | Refreshes local documentation |
| "List all agents" | doc-registry-agent | Shows available agents |
| "Update all agents" | distribute-agents-agent | Syncs latest from GitHub |
| "Add new agents" | distribute-agents-agent | Downloads new agents only |

**Example**: 
```
"Create an agent that monitors file changes"
→ New agent in agents/file-monitor-agent/
→ Available in your project only
```

## Lockfile

The `agents.lockfile` prevents accidental overwrites:

```json
{
  "synced_at": "2026-02-20T10:30:00Z",
  "source": "https://github.com/skelacc/AGENTS-library",
  "location": ".github/agents",
  "agents": {
    "create-agent-agent": "1.0.0",
    "doc-registry-agent": "1.0.0",
    "distribute-agents-agent": "1.0.0"
  },
  "customizations": {
    "create-agent-agent": []
  }
}
```

**DAA respects lockfile**:
- ✓ First sync creates it automatically
- ✓ Subsequent syncs don't overwrite without permission
- ✓ Tracks which agents were synced and at what version
- ✓ Logs any local customizations

## Updating Agents

### Sync Latest (Full Update)
```
"Update all agents"
```
Replaces all agent files with latest versions from GitHub.

### Add New Only (Safe Update)
```
"Add new agents"
```
Downloads only new agents from GitHub, preserves your customizations.

### Check for Updates
```
"Check agent versions"
or
"Are there agent updates?"
```
Shows available updates without syncing.

## Troubleshooting

### Agents Not Syncing
- Check if DAA is active: "Distribute agents" or "Sync agents"
- Verify `agents.lockfile` exists in your project
- Confirm internet connection (needs to reach GitHub)

### DAA Refuses to Update (Customizations Protected)
- You modified agents locally (tracked in lockfile)
- Use "Add new agents" to get new agents without replacing customizations
- Or use "Update all agents" to replace all (will back up your changes)

### Agent Not Found After Sync
- Verify sync completed: check `agents.lockfile` was created
- Check agent directory location: `.github/agents/` or `agent-kit/`
- Reload AI assistant context after sync

### Configuration Not Applied
- Verify `agent-kit/config.json` has valid JSON syntax
- Check paths match your actual folder structure
- Restart AI assistant or refresh file context

---

**Next Steps**: 
1. Let DAA auto-sync your project, OR manually copy agent-kit
2. Review [AGENTS.md](AGENTS.md) to see available agents
3. Start using agents with natural language: "Create an agent that..."
