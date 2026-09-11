# getTypeSchema

## Summary
Return a JSON schema view of a compiled type so you can see expected fields and data types.

## Input parameters
Input schema class: GetTypeSchemaRequest

| Parameter | Required | Type |
|---|---|---|
| fqn | required | String |

## Expected output
Returns a JSON object with key schema.

schema is a generated JSON-schema-like object for the target type.
Error keys: status=error, message.

Example:
```json
{
  "schema": {
    "type": "object",
    "title": "Customer",
    "properties": { "uuid": {"type":"string"}, "name": {"type":"string"} }
  }
}
```
