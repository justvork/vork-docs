# completeBackgroundTask

`Default Tool`

## Summary
Signals that the background task has entirely fulfilled its operational objectives and that the background processing loop should now gracefully terminate. You MUST supply a boolean 'success' value and a 'report' string summarising what was done and produced.

## Input parameters
Input schema class: CompleteBackgroundTaskRequest

| Parameter | Required | Type |
|---|---|---|
| sessionUuid | optional | String |
| success | required | boolean |
| report | required | String |

## Expected output
Returns a JSON object.

Success keys: status=shutdown_initiated.
Context errors use keys: error.

Example:
```json
{ "status": "shutdown_initiated" }
```
