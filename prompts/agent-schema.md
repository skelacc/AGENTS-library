# Agent Schema

JSON schema for `agent.json` validation.

## Required Fields

- **name**: `^[a-z0-9]+(-[a-z0-9]+)*$` (match folder)
- **description**: 20-200 chars
- **scope**: 10-150 chars
- **inputs**: Array (min 1)
- **outputs**: Array (min 1)
- **triggers**: Array (min 1)
- **tools**: Array from: bash, view, create, edit, grep, glob
- **skills**: Array `^skills/[^/]+/[^/]+\.md$`
- **status**: active | inactive | experimental

## Optional Fields

- **dependencies**: Agent names array
- **standards**: Prompt paths array
- **version**: `\d+\.\d+\.\d+`

## Validation

- Name unique, matches folder
- Arrays have descriptive strings
- Tools from allowed list
- Skill paths exist
- No duplicates
