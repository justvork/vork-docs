# listFiles

`Default Tool`

## Summary
List files/folders for a directory in the current session sandbox (default) or shared area. File entries include download URLs.

## Input parameters
Input schema class: ListFilesRequest

| Parameter | Required | Type |
|---|---|---|
| path | optional | String |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, area, path, count, items.
Each items element keys: name, path, directory, sizeBytes, modifiedAt, and downloadUrl for files.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "path": "",
  "count": 1,
  "items": [{ "name": "notes.txt", "path": "notes.txt", "directory": false, "sizeBytes": 42, "modifiedAt": 1730000000000, "downloadUrl": "/api/session-files/download?..." }]
}
```
