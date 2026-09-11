# searchTextFile

## Summary
Search very large text/log files line-by-line with bounded contextual windows around matches. Prefer this over full-file reads when looking for errors, IDs, protocol events, or timestamps.

## Input parameters
Input schema class: SearchTextFileRequest

| Parameter | Required | Type |
|---|---|---|
| path | required | String |
| query | required | String |
| matchType | optional | String |
| caseSensitive | optional | Boolean |
| beforeLines | optional | Integer |
| afterLines | optional | Integer |
| maxMatches | optional | Integer |
| startLine | optional | Long |
| endLine | optional | Long |
| area | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, area, path, query, matchType, caseSensitive, beforeLines, afterLines, startLine, endLine, maxMatches, returnedMatches, totalMatches, allMatchesScanned, moreMatchesPossible, truncated, blocks.
Each blocks element keys: startLine, endLine, matchLines, text.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "path": "app.log",
  "query": "ERROR",
  "matchType": "CONTAINS",
  "returnedMatches": 2,
  "allMatchesScanned": true,
  "blocks": [{ "startLine": 120, "endLine": 123, "matchLines": [121], "text": "..." }]
}
```
