# checkProcessTool

## Summary
Checks if a background process is still running.

## Input parameters
Input schema class: CheckProcessRequest

| Parameter | Required | Type |
|---|---|---|
| pid | required | String |

## Expected output
Returns a JSON object.

If running: status=RUNNING.
If exited: status=EXITED, exit_code.
Error keys: status=ERROR, message.

Example:
```json
{ "status": "EXITED", "exit_code": 0 }
```
