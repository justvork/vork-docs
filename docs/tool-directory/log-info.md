# logInfo

## Summary
Write a message to the application log at INFO level for tracking and diagnostics.

## Input parameters
Input schema class: LogInfoRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON object.

Success keys: status=ok.
Error keys: status=error, message.

Example:
```json
{ "status": "ok" }
```
