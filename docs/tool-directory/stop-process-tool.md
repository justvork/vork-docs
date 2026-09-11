# stopProcessTool

## Summary
Terminates a background process and cleans up its memory footprint.

## Input parameters
Input schema class: StopProcessRequest

| Parameter | Required | Type |
|---|---|---|
| pid | required | String |

## Expected output
Returns a JSON object.

Success keys: status=TERMINATED.
Error keys: status=ERROR, message.

Example:
```json
{ "status": "TERMINATED" }
```
