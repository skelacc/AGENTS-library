# Agent Style Guide

## Writing

- Clarity: Simple, direct language
- Complete: No TODO/TBD
- Consistent: Follow patterns

## Markdown

Headings:
- Unordered lists: `-`
- Ordered lists: numbers
- Indentation: 2 spaces
- Section: `##`
- Subsection: `###`
- Maximum depth: `####`
Lists: `-` unordered, numbers ordered, 2-space indent
Code: `inline` or ```language blocks

## agent.json

Order: name, description, scope, inputs, outputs, triggers, tools, skills, status
Format: 2-space indent, double quotes, multi-line for long arrays

## instructions.md

- Purpose: 1 paragraph, 3-5 sentences
- Rules: Numbered, bold labels, imperative
- Tone: Active voice, present tense

## examples.md

```markdown
## Example N: Scenario
### User Input
"request"
### Agent Response
[action]
### Expected Output
[result]
```

## Patterns

- Agents: **Full Name (Abbr)** then abbr
- Files: `file.ext`
- Dirs: `path/`
- Fields: **fieldName**
