# Report Templates Skill

## Purpose
Standardize documentation outputs so every run produces consistent, reusable artifacts for other agents.

## Procedure
1. Ensure /documentation exists.
2. Create or update these files with the template headers if missing:
   - documentation/scope.md
   - documentation/architecture-overview.md
   - documentation/hardware-architecture.md
   - documentation/software-architecture.md
   - documentation/dependency-graph.md
   - documentation/module-graph.md
   - documentation/service-graph.md
   - documentation/kpis.md
   - documentation/changelog.md
   - documentation/tasks.md
3. For each file, include:
   - Title
   - "Last Updated" timestamp line
   - Required sections below

## Templates

### scope.md
- Scope Understood
- Out of Scope
- Assumptions
- Open Questions

### architecture-overview.md
- System Summary
- Key Components
- Data Flow Overview
- Risks / Unknowns

### hardware-architecture.md
- Runtime Environment
- Deployment Targets
- Infra Dependencies

### software-architecture.md
- Layers / Modules
- Key Interfaces
- External Integrations

### dependency-graph.md
- Mermaid graph
- Notes (limits, unknowns)

### module-graph.md
- Mermaid graph
- Notes (limits, unknowns)

### service-graph.md
- Mermaid graph
- Notes (limits, unknowns)

### kpis.md
- Metrics Snapshot
- Changes Since Last Run
- Evidence References

### changelog.md
- Date
- Summary
- Files Updated
- Reason for Change

### tasks.md
- Backlog
- In Progress
- Done
- Trash

Add tasks mentioned in conversations to Backlog with a short context note.

## Output Rules
- Never delete sections; append or update within sections.
- Keep timestamps ISO 8601.
- Maintain concise bullets for readability.
