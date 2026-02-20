# Agent Standards

## File Structure

Required:
```
/agents/<agent-name>/
├── agent.json          # Metadata (max 50 lines)
├── instructions.md     # Operations (max 150 lines)
└── examples.md         # 2 examples (max 80 lines)
```

Optional:
```
/skills/<agent-name>/
└── skill-name.md       # Procedures (max 100 lines)
```

## Naming

- **Agent names**: lowercase-hyphen-separated (e.g., `test-runner-agent`)
- **File names**: Exact: `agent.json`, `instructions.md`, `examples.md`

## agent.json Required Fields

```json
{
  "name": "lowercase-hyphen-separated",
  "description": "Complete sentence (20-200 chars)",
  "scope": "Clear boundaries (10-150 chars)",
  "inputs": ["input types"],
  "outputs": ["output types"],
  "triggers": ["activation phrases"],
  "tools": ["tool names"],
  "skills": ["skill/paths.md"],
  "status": "active|inactive|experimental"
}
```

Optional: `dependencies`, `standards`, `version`

## instructions.md Required Sections

1. **Purpose** (1 paragraph, 3-5 sentences)
2. **Behavior Rules** (numbered, min 3)
3. **Input Interpretation Rules**
4. **Output Rules**
5. **Error Handling**
6. **Interaction with DRA**

## examples.md Format

Minimum 2 examples:
```markdown
## Example N: Scenario

### User Input
"exact request"

### Agent Response
[what happens]

### Expected Output
[result]
```

## Quality Rules

- No placeholders (TODO, TBD, FIXME)
- Complete information only
- Follow line limits strictly
- Use clear, simple language
