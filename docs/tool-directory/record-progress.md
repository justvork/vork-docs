# recordProgress

`Default Tool`

## Summary
Persist a concise progress checkpoint to session memory for use in later turns. Use this after completing significant steps (e.g. host scanned, report generated, report sent).

## Input parameters
Input schema class: RecordProgressRequest

| Parameter | Required | Type |
|---|---|---|
| entry | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, storedKey.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "storedKey": "BG_PROGRESS_0003" }
```
