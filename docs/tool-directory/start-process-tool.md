# startProcessTool

## Summary
Starts a long-running background process and returns a reference PID to interact with it later.

## Input parameters
Input schema class: StartProcessRequest

| Parameter | Required | Type |
|---|---|---|
| command | required | String |

## Expected output
Returns a JSON object.

Success keys: status=STARTED, pid.
Error keys: status=ERROR, message.

Example:
```json
{ "status": "STARTED", "pid": "proc-123" }
```
