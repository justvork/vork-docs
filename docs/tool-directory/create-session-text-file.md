# createSessionTextFile

`Default Tool`

## Summary
Create a UTF-8 text file in either the per-session sandbox (default) or the shared area. Returns a download URL that can be rendered in chat attachments. Use area=SESSION for files scoped to the current chat session, or area=SHARED for cross-session exchange. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message.

## Input parameters
Input schema class: CreateSessionTextFileRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| content | required | String |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, area, path, name, size, downloadUrl.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "path": "notes/output.txt",
  "name": "output.txt",
  "size": 77,
  "downloadUrl": "/api/session-files/download?..."
}
```
