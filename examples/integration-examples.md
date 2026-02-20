# Agent-Kit Integration Examples

This document provides real-world examples of integrating Agent-Kit from the global `~/.github/agent-kit/` location into your projects.

## Global Agent-Kit Location

Agent-Kit is stored globally at:
```
~/.github/agent-kit/
├── agents/
├── skills/
├── prompts/
└── config.json
```

Projects reference agents from this global location rather than copying files locally.

---

## Example 1: Project with Local Agent Config

**Project Structure:**
```
my-project/
├── .github/
│   └── agents-config.json     # Project-specific config
├── src/
└── AGENTS.md                  # Project's agent documentation
```

**Configuration (`.github/agents-config.json`):**
```json
{
  "agent_kit_location": "~/.github/agent-kit",
  "project_agents_enabled": true,
  "documentation": {
    "agents_file": "AGENTS.md",
    "location": "root"
  }
}
```

**AI Assistant Context (`.github/copilot-instructions.md`):**
```markdown
## Agent System

This project uses agents from the global Agent-Kit:
- Global agents: ~/.github/agent-kit/agents/
- Project config: .github/agents-config.json
- Project docs: AGENTS.md
```

---

## Example 2: Project Without Local Config

**Project Structure:**
```
simple-project/
├── src/
└── README.md
```

**Default Behavior:**
- Agents read from `~/.github/agent-kit/`
- Uses default global configuration
- No local project setup needed

**Usage:**
```
"Create an agent that [describe task]"
→ Agent created in ~/.github/agent-kit/agents/
→ Available to all your projects
```

---

## Example 3: Multiple Projects Sharing Agents

All projects on your system share the same agent collection:

```
~/projects/
├── project-a/
├── project-b/
└── project-c/

~/.github/agent-kit/
└── agents/
    ├── create-agent-agent/
    ├── doc-registry-agent/
    └── custom-agent/          # Available to all projects
```

Any agent created in one project becomes available to all projects automatically.

---

## Configuration Patterns

### Pattern 1: Use Global Defaults (Recommended)
No local configuration needed. Agents work out of the box.

### Pattern 2: Project-Specific Documentation
Create local `AGENTS.md` to document which agents your project uses:

```markdown
# Project Agents

This project uses these agents from ~/.github/agent-kit/:
- create-agent-agent
- doc-registry-agent
- custom-validator-agent
```

### Pattern 3: Project-Specific Agent Settings
Create `.github/agents-config.json` for project-specific behavior:

```json
{
  "enabled_agents": ["create-agent-agent", "doc-registry-agent"],
  "disabled_agents": ["experimental-agent"]
}
```

---

## Common Usage Patterns

### Creating Project-Specific Agents
```
"Create an agent that validates my project's file structure"
→ Agent stored globally but works for any project
→ Can be configured per-project if needed
```

### Listing Available Agents
```
"List all agents"
→ Shows all agents from ~/.github/agent-kit/
```

### Updating Agent Documentation
```
"Update AGENTS.md"
→ Updates local project documentation
```

---

## Best Practices

1. **Keep agents generic**: Agents in global location should work for any project type
2. **Document locally**: Use project's AGENTS.md to show which agents are relevant
3. **Configure per-project**: Use `.github/agents-config.json` for project-specific settings
4. **Create reusable agents**: Think "can other projects use this?" when creating agents

---

## Troubleshooting

### Issue: Can't find agents

**Solution:**
Verify global location exists:
```bash
ls ~/.github/agent-kit/agents/
```

### Issue: Agent not working for project

**Solution:**
Check if agent needs project-specific configuration in `.github/agents-config.json`

### Issue: Want project-specific agent

**Solution:**
Create it in global location with project-aware logic, or use configuration to enable/disable per-project

---

## Next Steps

1. Verify global agent-kit: `ls ~/.github/agent-kit/`
2. Start using agents: "Create an agent that [describe task]"
3. Document in your project: Add AGENTS.md listing relevant agents
4. Configure if needed: Create `.github/agents-config.json` for project settings

For more help, see the main documentation in `~/.github/agent-kit/README.md`
