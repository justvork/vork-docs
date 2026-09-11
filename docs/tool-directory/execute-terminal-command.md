# executeTerminalCommand

`Restricted`

## Summary
Run a terminal command in the virtual SSH environment and stream live output back to the session.

## Input parameters
Input schema class: ExecuteTerminalCommandRequest

| Parameter | Required | Type |
|---|---|---|
| command | required | String |
| host | optional | String |

## Expected output
Returns a JSON object.

Success keys: status (COMPLETED or ABORTED), command, terminalId, output, and optional outputFileUuid.
Validation error keys: status=error, message.
Abort shortcut may return status=aborted, message.

Example:
```json
{
  "status": "COMPLETED",
  "command": "ls -la",
  "terminalId": "...",
  "output": "total 8 ...",
  "outputFileUuid": "/api/session-files/download?..."
}
```
