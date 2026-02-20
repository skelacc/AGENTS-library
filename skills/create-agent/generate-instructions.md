# Generate instructions.md

## Purpose
Creates instructions.md (max 150 lines).

## Inputs
From agent.json: name, description, scope, inputs, outputs, triggers

## Procedure
1. **Purpose**: 1 para, 3-5 sentences
2. **Behavior Rules**: Numbered, min 3
3. **Input Interpretation**: Triggers, extraction, defaults
4. **Output Rules**: Formats, destinations
5. **Error Handling**: Failure modes
6. **DRA Interaction**: Registration
7. Apply markdown formatting: use proper headings, numbered/bulleted lists, and code blocks as needed, following the project markdown/style guide.
8. Enforce 150-line limit
9. Write `/agents/<name>/instructions.md`
10. Validate sections, no placeholders

## Validation
Max 150 lines, all sections, purpose 3-5 sentences, min 3 rules, no TODO/TBD

## Error Handling
- Missing data: Use agent.json or warn
- Too long: Condense essentials
- Generic: Add specifics

## Outputs
`/agents/<name>/instructions.md` (max 150 lines)
