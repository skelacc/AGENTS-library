# Agent-Kit: Reusable AI Agent System

A global collection of specialized AI agents stored in `~/.github/agent-kit/` that works across all your projects.

## What is Agent-Kit?

Agent-Kit is a framework for creating and managing autonomous AI agents. Each agent is a specialized assistant that:
- Automatically detects when it's needed (via trigger phrases)
- Follows strict standards and behavior rules
- Produces consistent, predictable outputs
- Works across all your projects without duplication

## Global Installation

Agent-Kit lives in one place and serves all your projects:

```
~/.github/agent-kit/
├── agents/              # All your agents
├── skills/              # Reusable procedures
├── prompts/             # Agent standards
├── templates/           # Quick start templates
└── config.json          # Global configuration
```

### Setup

Agent-Kit should be installed at `~/.github/agent-kit/`. If not already there:

```bash
# Verify installation
ls ~/.github/agent-kit/

# If not present, agent-kit needs to be initialized
# (This will be handled by the distribute-agents-agent in future)
```

## How It Works

1. **Global Storage**: All agents stored in `~/.github/agent-kit/`
2. **Project Access**: Any project can use any agent
3. **No Duplication**: Create once, use everywhere
4. **Auto-Discovery**: AI assistants reference the global location

## Using Agents

Agents activate automatically via trigger phrases:

```
"Create an agent that validates API responses"
→ create-agent-agent generates a new agent in ~/.github/agent-kit/agents/

"Update AGENTS.md"
→ doc-registry-agent refreshes project documentation

"List all agents"
→ Shows all available agents from global collection
```

## Included Agents

### create-agent-agent
Creates new agents automatically from natural language descriptions. Agents are stored globally in `~/.github/agent-kit/agents/`.

**Triggers**: "Create an agent that...", "I want an agent which...", "Make me an agent for..."

### doc-registry-agent
Maintains project AGENTS.md files documenting which agents are relevant to each project.

**Triggers**: "Register agent", "Update AGENTS.md", "List all agents"

## Global Structure

```
~/.github/agent-kit/
├── README.md                 # This file
├── INTEGRATION.md            # Project setup guide
├── config.json               # Global configuration
├── agents/                   # All agent definitions
│   ├── create-agent-agent/
│   │   ├── agent.json        # Metadata
│   │   ├── instructions.md   # Behavior rules
│   │   └── examples.md       # Usage examples
│   └── doc-registry-agent/
│       ├── agent.json
│       ├── instructions.md
│       └── examples.md
├── prompts/                  # Shared standards
│   ├── agent-standards.md    # File structure rules
│   ├── agent-schema.md       # JSON schema
│   └── agent-style-guide.md  # Writing guidelines
├── skills/                   # Reusable procedures
│   └── create-agent/
│       ├── create-folder-structure.md
│       ├── generate-agent-json.md
│       ├── generate-instructions.md
│       └── register-agent.md
├── templates/                # Starting points
│   ├── AGENTS.md.template    # Documentation template
│   ├── agent.json.template   # Metadata template
│   └── instructions.md.template
└── examples/                 # Integration patterns
    └── integration-examples.md
```

## Project Integration

Each project references the global agent-kit without copying files:

### Option 1: Minimal (Recommended)
No local configuration needed. Just use agents.

### Option 2: Documentation
Create `AGENTS.md` in your project listing relevant agents:
```markdown
# Project Agents
This project uses agents from ~/.github/agent-kit/
```

### Option 3: Custom Configuration
Create `.github/agents-config.json` for project-specific settings:
```json
{
  "agent_kit_location": "~/.github/agent-kit",
  "enabled_agents": ["create-agent-agent", "doc-registry-agent"]
}
```

- **relative**: Paths relative to project root (default)
- **absolute**: Full system paths (for multi-project setups)
- **custom**: Define your own directory structure

## Creating Custom Agents

Use the create-agent-agent to generate new agents:

```
"Create an agent that monitors API health and sends alerts when endpoints fail"
```

The agent will be generated in `agent-kit/agents/api-monitor-agent/` with all required files.

## Integration Examples

### Python Project
```python
# Add to your AI assistant's context
from pathlib import Path
agent_kit = Path("agent-kit")
## AI Assistant Integration

Reference the global agent-kit in your AI assistant configuration:

### GitHub Copilot
Add to `.github/copilot-instructions.md`:
```markdown
## Agent System
This project uses agents from ~/.github/agent-kit/
- Agent catalog: ~/.github/agent-kit/AGENTS.md
- Agent standards: ~/.github/agent-kit/prompts/agent-standards.md
```

### Cursor / Windsurf
Add to `.cursorrules`:
```
@file:~/.github/agent-kit/AGENTS.md
@file:~/.github/agent-kit/prompts/agent-standards.md
```

### Claude / ChatGPT
Reference the global location:
```
"Use agents from ~/.github/agent-kit/"
```

## Standards & Quality

All agents follow strict standards:
- **Line limits**: No file exceeds 150 lines
- **Clear triggers**: Every agent has explicit activation phrases
- **Error handling**: Comprehensive error management
- **Generic design**: Works across all project types

See `~/.github/agent-kit/prompts/agent-standards.md` for complete guidelines.

## Creating Custom Agents

Use natural language to create new agents:
```
"Create an agent that validates commit messages"
"Create an agent that runs tests on changed files"
"Create an agent that generates documentation"
```

Agents are stored globally and available to all projects immediately.

## Best Practices

1. **Keep agents generic**: Design for reuse across all projects
2. **Use descriptive triggers**: Make activation phrases obvious
3. **Document thoroughly**: Update examples with real usage
4. **Test across projects**: Validate in multiple contexts
5. **Follow standards**: Use global standards for consistency

## Troubleshooting

### Agent Not Activating
- Check trigger phrases: `cat ~/.github/agent-kit/AGENTS.md`
- Verify agent status is "active" in agent.json
- Confirm AI assistant references global location

### Global Location Not Found
```bash
# Verify installation
ls ~/.github/agent-kit/

# Check agents directory
ls ~/.github/agent-kit/agents/
```

### Want Project-Specific Behavior
Create `.github/agents-config.json` in your project to configure per-project settings

---

**Version**: 1.0.0  
**Last Updated**: 2026-02-20  
**Compatibility**: Works with Claude, GPT-4, and other AI assistants that support structured prompts
