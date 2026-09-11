# downloadFolderAsZip

`Default Tool`

## Summary
Zip a folder in the current session sandbox (default) or shared area and return a download URL. Use this when the user asks to download a directory as a single archive. By default attachOnlyZip=true, so intermediate generated files are removed from the attachment list and only the zip is attached. Set attachToChat=false if the zip should be generated without any chat attachment. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message.

## Input parameters
Input schema class: DownloadFolderAsZipRequest

| Parameter | Required | Type |
|---|---|---|
| folderPath | required | String |
| outputZipPath | optional | String |
| area | optional | String |
| attachToChat | optional | Boolean |
| attachOnlyZip | optional | Boolean |

## Expected output
Returns a JSON object.

Success keys: status, area, folderPath, zipPath, sizeBytes, downloadUrl.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "folderPath": "reports",
  "zipPath": "reports.zip",
  "sizeBytes": 9321,
  "downloadUrl": "/api/session-files/download?..."
}
```
