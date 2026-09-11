# readProcessTool

## Summary
Reads and drains available unread output from a background process.

## Input parameters
Input schema class: ReadProcessRequest

| Parameter | Required | Type |
|---|---|---|
| pid | required | String |
| timeoutSeconds | optional | Integer |

## Expected output
Returns a JSON object.

If no unread output: status=NO_NEW_OUTPUT, process_active.
If output available: status=OK, process_active, output.
Error keys: status=ERROR, message.

Example:
```json
{ "status": "OK", "process_active": true, "output": "ready> " }
```
