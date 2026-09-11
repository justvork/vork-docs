# extractTar

## Summary
Extract a tar archive into the session/shared file area with safe path validation.

## Input parameters
Input schema class: ExtractTarRequest

| Parameter | Required | Type |
|---|---|---|
| archivePath | required | String |
| destinationPath | required | String |
| area | optional | String |
| attachToChat | optional | Boolean |

## Expected output
Returns a JSON object.

Success keys: status, area, archivePath, destinationPath, filesExtracted, directoriesCreated.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "archivePath": "backup.tar",
  "destinationPath": "restore",
  "filesExtracted": 8,
  "directoriesCreated": 3
}
```
