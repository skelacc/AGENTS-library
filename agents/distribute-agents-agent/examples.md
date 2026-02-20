# Distribute-Agents-Agent Examples

## Example 1: Auto-Sync (New Project)

**Scenario**: New project, no agents.lockfile exists

**Response**:
```
✓ New project detected
✓ Fetching from https://github.com/skelacc/AGENTS-library...
✓ Agents distributed to .github/agents/

Synced (3): create-agent-agent, doc-registry-agent, distribute-agents-agent
Lockfile: .github/agents/agents.lockfile
Ready to use!
```

---

## Example 2: Already Synced (No Action)

**Scenario**: Lockfile exists

**Response**:
```
✓ Lockfile found (last synced 2026-02-15, v1.0.0)
No action needed. Use "Update agents" to refresh.
```

---

## Example 3: Full Update (Replace All)

**User**: "Update all agents to latest"

**Response**:
```
Found updates: create-agent-agent 1.0.0 → 1.0.2
⚠ Customizations detected. Replace? (y/n) → y

✓ Updated (3 agents)
✓ Backup: .github/agents/.daa-backup-2026-02-20/
✓ Lockfile updated
```

---

## Example 4: Add New Only (Preserve Existing)

**User**: "Add new agents"

**Response**:
```
New agents found: lint-runner-agent, test-monitor-agent

✓ Added 2 new agents
✓ Existing agents preserved (customizations intact)
✓ Lockfile updated
```

---

## Example 5: Network Fallback

**Scenario**: GitHub unreachable

**Response**:
```
⚠ Cannot reach GitHub
✓ Using cached version (synced 2026-02-19)
Will retry when network available.
```

---

**Version**: 1.0.0
