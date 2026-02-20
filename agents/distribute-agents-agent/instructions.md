# Distribute-Agents-Agent (DAA) — Implementation Notes

This file is kept for reference. The primary agent documentation is in **AGENT.md** (recognized by VS Code Copilot).

## Key Implementation Points

### Project Path Prompt
- Always request or confirm the target project path when DAA is invoked.
- Accept absolute or relative paths; resolve relative paths from the current workspace root.
- If the path is missing or unclear, ask before performing any sync logic.

### Deployment Target
DAA deploys agents to `.github/agents/` by default, not the entire agent-kit structure.

### Why .github/?
- Standard GitHub conventions directory
- Recognized by GitHub Actions and workflows
- Better for teams already using GitHub
- Fallback paths: `agent-kit/`, project root, `docs/` if `.github/` unavailable

### Agent Folder Structure
Each agent in `.github/agents/` contains:
```
.github/agents/<agent-name>/
├── agent.json
├── AGENT.md
└── examples.md
```

### VS Code Copilot Recognition
Agents must have `AGENT.md` as entry point for auto-discovery. Renamed from `instructions.md`.

### Configuration Paths
- Default: `.github/agents/`
- Configurable via: `.github/config.json`
- All paths relative to project root

### Lockfile Behavior
- Stores in project root
- Tracks versions and customizations
- Prevents duplicate syncs
- Enables safe updates

---

**For detailed behavior, see: [AGENT.md](AGENT.md)**
