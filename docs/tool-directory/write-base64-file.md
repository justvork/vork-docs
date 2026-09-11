# writeBase64File

`Default Tool`

## Summary
Write a binary file into the current session sandbox (default) or shared area from Base64 content. The incoming base64Content is decoded to raw bytes before writing to disk. Both standard Base64 and URL-safe Base64 are accepted automatically (no mode switch required). Set attachToChat=false for intermediate files that should not appear in the assistant attachment list. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message.

## Input parameters
Input schema class: WriteBase64FileRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| base64Content | required | String |
| area | optional | String |
| attachToChat | optional | Boolean |

## Expected output
Returns a JSON object.

Success keys: status, area, path, name, sizeBytes, downloadUrl.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "path": "images/logo.png",
  "name": "logo.png",
  "sizeBytes": 4096,
  "downloadUrl": "/api/session-files/download?..."
}
```
