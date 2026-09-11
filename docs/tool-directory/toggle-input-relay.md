# toggleInputRelay

`Default Tool`

## Summary
Enable or disable secure relay input handling for this web chat session.

## Input parameters
Input schema class: ToggleInputRelayRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON object.

Success keys: status=ok, enabled (boolean).
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "enabled": true }
```
