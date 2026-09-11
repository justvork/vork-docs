# getJavaTypeSource

## Summary
Retrieve the saved Java source for a compiled type so you can review or update it safely.

## Input parameters
Input schema class: GetTypeSchemaRequest

| Parameter | Required | Type |
|---|---|---|
| fqn | required | String |

## Expected output
Returns a JSON object.

Success keys: fqn, source.
Error keys: status=error, message.

Example:
```json
{
  "fqn": "jadaptive.crm.Customer",
  "source": "package jadaptive.crm; public record Customer(...) {}"
}
```
