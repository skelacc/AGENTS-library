# Register Agent

## Purpose
Prepares AGENTS.md entry for DRA.

## Inputs
name, description (1st sentence), scope, status, location

## Procedure
1. Extract 1st sentence (or 80 chars)
2. Format:
```
## name
**Purpose**: desc
**Scope**: scope
**Status**: Status
**Location**: `/agents/name/`
```
3. Generate diff with `+ ` prefix
4. Find insertion point (alphabetical)
5. Create DRA metadata
6. Output preview

## Validation
All fields, valid markdown, capitalized status, path exists

## Error Handling
- No desc: Use name
- Invalid status: "Experimental"
- No AGENTS.md: Note creation
- Duplicate: Ask to update

## Outputs
Diff preview, metadata JSON
