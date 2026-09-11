# readTextFileRange

## Summary
Read a precise inclusive line range from a text/log file. Use after searchTextFile identifies an interesting region; avoids loading the entire file.

## Input parameters
Input schema class: ReadTextFileRangeRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| startLine | required | Long |
| endLine | required | Long |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, area, path, startLine, endLine, linesRead, bytesRead, text.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "path": "app.log",
  "startLine": 10,
  "endLine": 20,
  "linesRead": 11,
  "bytesRead": 512,
  "text": "..."
}
```
