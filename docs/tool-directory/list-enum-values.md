# listEnumValues

## Summary
List all allowed constant values for an enum type by its fully qualified name.

## Input parameters
Input schema class: ListEnumValuesRequest

| Parameter | Required | Type |
|---|---|---|
| fqn | required | String |

## Expected output
Returns a JSON object.

Success keys: fqn, values (array of enum constant strings).
Error keys: status=error, message.

Example:
```json
{ "fqn": "jadaptive.crm.Status", "values": ["ACTIVE", "INACTIVE"] }
```
