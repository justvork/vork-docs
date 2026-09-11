# createFolder

`Default Tool`

## Summary
Create a directory in the current session sandbox (default) or shared area. Creates intermediate directories when necessary.

## Input parameters
Input schema class: CreateFolderRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, area, path.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "area": "SESSION", "path": "artifacts/output" }
```
