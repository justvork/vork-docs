# executeCommandAndOutputTool

## Summary
Executes a synchronous shell command, waits for it to complete, and returns the full output.

## Input parameters
Input schema class: ExecuteCommandAndOutputRequest

| Parameter | Required | Type |
|---|---|---|
| command | required | String |

## Expected output
Returns a JSON object.

Success keys: exit_code, output, and optional timed_out=true.
Error keys: status=ERROR, message.

Example:
```json
{ "exit_code": 0, "output": "hello\\n" }
```
