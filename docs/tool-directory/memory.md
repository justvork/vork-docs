# memory

`Default Tool`

## Summary
Session key/value memory store. Use operation=set|get|list|delete to manage reusable context that is injected into future system prompts.

## Input parameters
Input schema class: MemoryRequest

| Parameter | Required | Type |
|---|---|---|
| operation | optional | String |
| key | optional | String |
| value | optional | String |
| prefix | optional | String |

## Expected output
Returns a JSON object; shape depends on operation.

set success keys: status, operation=set, key.
get success keys: status, operation=get, key, value, found.
list success keys: status, operation=list, prefix, count, entries.
delete success keys: status, operation=delete, key, deleted.
Errors: status=error, message.

Example (get):
```json
{ "status": "ok", "operation": "get", "key": "FOO", "value": "bar", "found": true }
```
