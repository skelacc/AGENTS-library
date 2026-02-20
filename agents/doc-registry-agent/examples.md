# Doc-Registry-Agent Examples

## Example 1: Register New Agent

### User Input
CAA sends registration request after creating test-runner-agent.

### DRA Response

**Action**: Validating agent metadata...
**Status**: agent.json valid, all required fields present
**Operation**: Inserting into AGENTS.md at line 42 (after "doc-registry-agent")

**Written to AGENTS.md**:
```markdown
## test-runner-agent
**Purpose**: Runs Python tests on file changes, reports only failures
**Scope**: Python test execution and failure reporting
**Status**: Active
**Triggers**: "*.py file saved", "Run tests", "Test this"
**Location**: `/agents/test-runner-agent/`

---
```

**Result**: ✓ Agent registered successfully

---

## Example 2: Refresh All Documentation

### User Input
"Refresh agent docs"

### DRA Response

**Scanning**: `/agents/` directory...
**Found**: 3 agents
- create-agent-agent (active)
- doc-registry-agent (active)
- test-runner-agent (active)

**Rebuilding**: AGENTS.md...
**Preserved**: Header and introduction
**Updated**: All 3 agent entries
**Written**: 52 lines to AGENTS.md

**Result**: ✓ Documentation refreshed

---

## Example 3: Discover All Agents

### User Input
"List all agents"

### DRA Response

**Agents in system**: 3 total

1. **create-agent-agent** (Active)
   - Purpose: Generates new agents automatically
   - Triggers: "Create an agent that...", "I need an agent for..."

2. **doc-registry-agent** (Active)
   - Purpose: Maintains agent documentation
   - Triggers: "Register agent", "List all agents"

3. **test-runner-agent** (Active)
   - Purpose: Runs Python tests, reports failures
   - Triggers: "*.py file saved", "Run tests"

**Documentation**: See AGENTS.md for full details
