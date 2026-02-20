# Generate agent.json

## Purpose
Creates validated agent.json (max 50 lines).

## Inputs
name, description, scope, inputs, outputs, triggers, tools, skills, status

## Procedure
1. Validate required fields
2. Check formats (pattern, lengths, enums)
3. Apply defaults: status="active", tools=["create","view","edit","bash"]
4. Build JSON (2-space indent)
5. Validate against schema
6. Write `/agents/<name>/agent.json`
7. Verify: `python3 -m json.tool <file>`

## Validation
Valid JSON, schema compliant, all required fields, max 50 lines

## Error Handling
- Invalid: Suggest correction
- Missing: Default or ask
- Unknown tool: Show allowed
- Bad path: Show pattern
- Write fail: Check perms

## Outputs
`/agents/<name>/agent.json` (max 50 lines)
