# folderExists

## Summary
Check whether a folder exists in the session/shared file area.

## Input parameters
Input schema class: FolderExistsRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, area, path, exists (boolean).
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "area": "SESSION", "path": "reports", "exists": true }
```
