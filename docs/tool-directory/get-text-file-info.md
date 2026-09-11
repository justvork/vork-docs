# getTextFileInfo

## Summary
Inspect a text/log file without returning its full content. Use this first for large files to get size and line count before searching.

## Input parameters
Input schema class: GetTextFileInfoRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, area, path, sizeBytes, lineCount, encoding.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "path": "server.log",
  "sizeBytes": 120934,
  "lineCount": 2871,
  "encoding": "UTF-8"
}
```
