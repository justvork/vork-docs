# writeProcessTool

## Summary
Writes input text to the stdin of a running background process.

## Input parameters
Input schema class: WriteProcessRequest

| Parameter | Required | Type |
|---|---|---|
| pid | required | String |
| input | required | String |

## Expected output
Returns a JSON object.

Success keys: status=WRITTEN.
Error keys: status=ERROR, message.

Example:
```json
{ "status": "WRITTEN" }
```
