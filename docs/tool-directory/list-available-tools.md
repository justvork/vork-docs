# listAvailableTools

`Default Tool`

## Summary
List all registered tool callbacks with their IDs and descriptions. Use this to discover valid tool IDs when building or reviewing an AgentTemplate's allowedTools list.

## Input parameters
Input schema class: ListAvailableToolsRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON array.

Each array element keys: id, name, description, parameterSchema, dependsOn.
Error keys: status=error, message.

Example:
```json
[
  {
    "id": "listFiles",
    "name": "listFiles",
    "description": "...",
    "parameterSchema": {"type":"object"},
    "dependsOn": []
  }
]
```
