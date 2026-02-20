# Agent-Kit Quick Reference

One-page guide to using Agent-Kit effectively.

## Activation

Agents activate via trigger phrases:

```
"Create an agent that..."        → create-agent-agent
"Update AGENTS.md"                → doc-registry-agent
"List all agents"                 → doc-registry-agent
```

## File Locations

```
agent-kit/
├── README.md           - Overview & features
├── INTEGRATION.md      - Setup instructions
├── AGENTS.md           - Agent catalog
├── config.json        - Path configuration
├── agents/            - Agent definitions
├── prompts/           - Standards & guidelines
├── skills/            - Reusable procedures
├── templates/         - Quick start templates
└── examples/          - Integration patterns
```

## Configuration

Edit `agent-kit/config.json`:

```json
{
  "paths": {
    "agents_directory": "agent-kit/agents",
    "skills_directory": "agent-kit/skills",
    "prompts_directory": "agent-kit/prompts"
  },
  "documentation": {
    "agents_file": "AGENTS.md",
    "location": "root"
  }
}
```

## Common Tasks

### Create New Agent
```
"Create an agent that [describe what you need]"
```

Example:
```
"Create an agent that runs tests when files change"
```

### List Available Agents
```
"List all agents"
or
"What agents are available?"
```

### Update Documentation
```
"Update AGENTS.md"
or
"Refresh agent docs"
```

### Find Agent Details
Check `agent-kit/agents/<agent-name>/`:
- `agent.json` - Metadata, triggers, config
- `instructions.md` - Behavior rules
- `examples.md` - Usage examples

## Integration Patterns

### Root Level (Default)
```
your-project/
├── agent-kit/
└── src/
```

### In Documentation
```
your-project/
├── docs/
│   └── agent-kit/
└── src/
```

### In Tools Folder
```
your-project/
├── tools/
│   └── agent-kit/
└── src/
```

## Path Configuration

### Relative Paths (Recommended)
```json
{
  "agents_directory": "agent-kit/agents"
}
```

### Absolute Paths (Multi-Project)
```json
{
  "agents_directory": "/home/user/shared/agents"
}
```

### Custom Structure
```json
{
  "agents_directory": "automation/ai-agents",
  "skills_directory": "automation/procedures"
}
```

## Agent File Structure

```
agent-name/
├── agent.json          # Max 100 lines
├── instructions.md     # Max 150 lines
└── examples.md         # Max 80 lines
```

Optional:
```
skills/agent-name/
└── skill-file.md       # Max 100 lines
```

## Creating Custom Agents

Use natural language:
```
"Create an agent that [action] when [condition]"
```

Examples:
```
"Create an agent that validates JSON files in src/"
"Create an agent that monitors API response times"
"Create an agent that generates changelogs from commits"
"Create an agent that checks code coverage"
```

## Agent Standards

All agents must have:
- ✅ Descriptive name (lowercase-hyphen-separated)
- ✅ Clear purpose (20-200 chars)
- ✅ Defined scope (boundaries)
- ✅ Trigger phrases (activation)
- ✅ Input/output specifications
- ✅ Error handling

## Customization

### Modify Existing Agent
1. Edit `agent-kit/agents/<name>/instructions.md`
2. Update behavior rules
3. Test with example triggers
4. Run "Update AGENTS.md"

### Add New Skill
1. Create `agent-kit/skills/<agent-name>/skill.md`
2. Reference in agent.json: `"skills": ["skills/<agent>/skill.md"]`
3. Follow max 100 lines limit

### Change Paths
1. Edit `agent-kit/config.json`
2. Update paths to match your structure
3. Restart AI assistant
4. Test with "List all agents"

## Troubleshooting

### Agent Not Responding
- Check trigger phrases in AGENTS.md
- Verify agent status is "active" in agent.json
- Ensure AI assistant has file access

### Wrong Generation Path
- Update agents_directory in config.json
- Use absolute paths if relative fails
- Check current working directory

### Standards Not Followed
- Verify prompts_directory is correct
- Check prompts/ folder exists
- Review agent-standards.md

### Documentation Out of Sync
- Run "Update AGENTS.md"
- Check documentation.agents_file path
- Verify doc-registry-agent is active

## Cheat Sheet

| Task | Command |
|------|---------|
| Create agent | "Create an agent that [X]" |
| List agents | "List all agents" |
| Update docs | "Update AGENTS.md" |
| Check config | Read `agent-kit/config.json` |
| Find standards | Read `agent-kit/prompts/agent-standards.md` |
| See examples | Read `agent-kit/examples/integration-examples.md` |
| Setup help | Read `agent-kit/INTEGRATION.md` |

## Best Practices

1. **Keep it focused**: One agent = one responsibility
2. **Use clear triggers**: Make activation obvious
3. **Document examples**: Show real usage patterns
4. **Follow limits**: Respect line count restrictions
5. **Test thoroughly**: Validate before deploying
6. **Update docs**: Keep AGENTS.md current

## Resources

- **Full docs**: `agent-kit/README.md`
- **Setup guide**: `agent-kit/INTEGRATION.md`
- **Examples**: `agent-kit/examples/integration-examples.md`
- **Standards**: `agent-kit/prompts/agent-standards.md`
- **Templates**: `agent-kit/templates/`

## Support

Ask in conversation:
```
"How do I configure agent-kit for [my setup]?"
"Show me examples of [specific use case]"
"Help me create an agent that [describe need]"
```

---

**Version**: 1.0.0  
**Last Updated**: 2026-02-20  
**Quick Help**: Just ask! Agents understand natural language.
