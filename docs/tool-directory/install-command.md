# installCommand

## Summary
Register a command binary directory under the session tools environment so local process execution can resolve it via PATH.

## Input parameters
Input schema class: InstallCommandRequest

| Parameter | Required | Type |
|---|---|---|
| binPath | required | String |
| command | optional | String |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, sessionUuid, registeredBinPath, command, commandPaths.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "sessionUuid": "...",
  "registeredBinPath": "/tmp/session/tools/bin",
  "command": "jq",
  "commandPaths": ["/tmp/session/tools/bin"]
}
```
