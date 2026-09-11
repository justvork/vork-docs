# exportJavaTypeSource

## Summary
Export the saved Java source code for a runtime-created custom type.

## Input parameters
Input schema class: ExportJavaTypeSourceRequest

| Parameter | Required | Type |
|---|---|---|
| fqn | required | String |

## Expected output
Returns a JSON object for runtime-compiled custom types.

Success keys: exportFormatVersion, fqn, kind, source.
Error keys: status=error, message.

Example:
```json
{
  "exportFormatVersion": "1.0",
  "fqn": "jadaptive.crm.Customer",
  "kind": "CUSTOM",
  "source": "package ..."
}
```
