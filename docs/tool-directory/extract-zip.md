# extractZip

## Summary
Extract a zip archive into the session/shared file area with safe path validation.

## Input parameters
Input schema class: ExtractZipRequest

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
  "archivePath": "bundle.zip",
  "destinationPath": "bundle",
  "filesExtracted": 12,
  "directoriesCreated": 5
}
```
