# exportJavaType

## Summary
Export stored JSON data for one exportable type, either by record ID or as all records for that type.

## Input parameters
Input schema class: ExportJavaTypeRequest

| Parameter | Required | Type |
|---|---|---|
| fqn | required | String |
| mode | optional | String |
| uuid | optional | String |

## Expected output
Returns a JSON object.

Success keys: exportFormatVersion, fqn, kind, entityType, mode, requestedUuid, recordCount, records, typeDefinition, description.
Error keys: status=error, message.

Example:
```json
{
  "exportFormatVersion": "1.0",
  "fqn": "jadaptive.crm.Customer",
  "kind": "CUSTOM",
  "entityType": true,
  "mode": "BY_ID",
  "requestedUuid": "cust-1",
  "recordCount": 1,
  "records": [{ "uuid": "cust-1", "name": "Acme" }],
  "typeDefinition": { "fqn": "jadaptive.crm.Customer", "record": true },
  "description": "Runtime-compiled type"
}
```
