# Create-Agent-Agent Examples

## Example 1: Documentation Agent

### User Input
"I need an agent that maintains documentation for /src files."

### CAA Response
**Detected**: Documentation agent
**Extracted**: Purpose: Maintain docs, Scope: /src only, Triggers: File changes

**Generated**: `/agents/doc-maintenance-agent/` with agent.json, instructions.md, examples.md

**AGENTS.md Preview**:
```diff
+ ## doc-maintenance-agent
+ **Purpose**: Maintains documentation for /src source code
+ **Scope**: /src directory only
+ **Status**: Active
+ **Location**: `/agents/doc-maintenance-agent/`
```

---

## Example 2: Testing Agent

### User Input
"Create an agent that runs Python tests and shows only failures."

### CAA Response
**Detected**: Test automation
**Generated**: `/agents/test-runner-agent/`

**agent.json**:
```json
{
  "name": "test-runner-agent",
  "description": "Runs Python tests, reports only failures",
  "triggers": ["*.py saved", "\"Run tests\""],
  "tools": ["bash", "view"],
  "status": "active"
}
```

**AGENTS.md Preview**:
```diff
+ ## test-runner-agent
+ **Purpose**: Runs Python tests, reports only failures
+ **Scope**: Python test execution
+ **Status**: Active
+ **Location**: `/agents/test-runner-agent/`
```
