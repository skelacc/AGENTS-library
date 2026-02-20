# Collect KPIs Skill

## Purpose
Gather a lightweight, repeatable set of KPIs for project health and architecture stability.

## Procedure
1. Count code modules/packages and list top-level services.
2. Track dependency count and changes since last run.
3. Record test coverage if available (or mark unknown).
4. Capture build or CI status if present in repo configs.
5. Write a concise KPI snapshot to documentation/kpis.md.

## Output Format (kpis.md)
- Last Updated (timestamp)
- Total modules
- Total services
- Dependency count
- Test coverage (if known)
- Build status (if known)
- Notable changes since last run
