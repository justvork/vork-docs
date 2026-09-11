# isCommandInstalled

## Summary
Check whether a command is available in registered session command paths.

## Input parameters
Input schema class: IsCommandInstalledRequest

| Parameter | Required | Type |
|---|---|---|
| command | required | String |

## Expected output
Returns a JSON object.

Success keys: status, command, installed, searchPaths, and optional matchedPath/executable.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "command": "jq",
  "installed": true,
  "searchPaths": ["/tmp/session/tools/bin"],
  "matchedPath": "/tmp/session/tools/bin",
  "executable": "/tmp/session/tools/bin/jq"
}
```
