# readFile

`Default Tool`

## Summary
Read a file from the current session sandbox (default) or shared area. Returns UTF-8 text content for text files and base64 for binary files.

## Input parameters
Input schema class: ReadFileRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| area | optional | String |
| maxBytes | optional | Integer |

## Expected output
Returns a JSON object.

Common success keys: status, area, path, name, downloadUrl, bytesRead, truncated.
Text files add keys: encoding, content.
Binary files add keys: contentBase64, contentType.
Error keys: status=error, message.

Example (text file):
```json
{
  "status": "ok",
  "area": "SESSION",
  "path": "notes.txt",
  "name": "notes.txt",
  "downloadUrl": "/api/session-files/download?...",
  "bytesRead": 120,
  "truncated": false,
  "encoding": "UTF-8",
  "content": "hello"
}
```
