# Architecture-Monitor-Agent Examples

## Example 1: Full Architecture Refresh

### User Input
"Generate architecture report"

### Agent Response
Detects recent changes, scans modules and services, updates all documentation files in /documentation, and appends a changelog entry.

### Expected Output
- documentation/architecture-overview.md updated
- documentation/dependency-graph.md updated
- documentation/module-graph.md updated
- documentation/service-graph.md updated
- documentation/kpis.md updated
- documentation/changelog.md appended
- documentation/scope.md updated

---

## Example 2: KPI-Only Update

### User Input
"Refresh project KPIs"

### Agent Response
Updates documentation/kpis.md and documentation/changelog.md, reuses existing graphs if no structural changes are detected.

### Expected Output
- documentation/kpis.md updated
- documentation/changelog.md appended
- documentation/scope.md updated (scope confirmation)

---

**Version**: 1.0.0  
**Last Updated**: 2026-02-20
