# listAgentTemplates

`Default Tool`

## Summary
List all configured agent templates. Returns each template's UUID, name, system prompt, and the list of allowed tool bean IDs.

## Input parameters
Input schema class: ListAgentTemplatesRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON array.

Each array element keys: uuid, name, agentType, systemPrompt, allowedTools.
Error keys: status=error, message.

Example:
```json
[
  {
    "uuid": "...",
    "name": "Planner",
    "agentType": "BACKGROUND",
    "systemPrompt": "...",
    "allowedTools": ["listAvailableTools", "recordProgress"]
  }
]
```
