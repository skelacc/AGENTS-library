# Create Folder Structure

## Purpose
Creates agent directories.

## Inputs
- `agent_name`: lowercase-hyphen
- `needs_skills`: boolean

## Procedure
1. Validate: `^[a-z0-9]+(-[a-z0-9]+)*$`
2. Check no conflict: `/agents/<name>/`
3. Create: `mkdir -p agents/<name>`
4. If skills: `mkdir -p skills/<name>`
5. Verify exists

## Validation
Dirs exist, empty, permissions 755

## Error Handling
- Invalid name: Auto-convert or suggest
- Conflict: List existing, suggest alt
- Permission denied: Report

## Outputs
- `/agents/<name>/`
- `/skills/<name>/` (if needed)
