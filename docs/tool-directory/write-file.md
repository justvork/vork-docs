# writeFile

`Default Tool`

## Summary
Write a UTF-8 file into the current session sandbox (default) or shared area. Returns a direct download URL that can be rendered in chat attachments. Use this for generating markdown, text, JSON, code, or configuration files. Set attachToChat=false for intermediate files that should not appear in the assistant attachment list. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message.

## Input parameters
Input schema class: WriteFileRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| content | required | String |
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
  "path": "notes/todo.md",
  "name": "todo.md",
  "sizeBytes": 88,
  "downloadUrl": "/api/session-files/download?..."
}
```
