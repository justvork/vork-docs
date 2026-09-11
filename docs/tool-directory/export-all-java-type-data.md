# exportAllJavaTypeData

## Summary
Export stored JSON data for every exportable entity type as a full snapshot.

## Input parameters
Input schema class: ExportAllJavaTypeDataRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON object.

Success keys: exportFormatVersion, typeCount, totalRecords, exports.
exports elements follow TypeDataExportPackage keys: exportFormatVersion, fqn, kind, entityType, mode, requestedUuid, recordCount, records, typeDefinition, description.
Error keys: status=error, message.

Example:
```json
{
  "exportFormatVersion": "1.0",
  "typeCount": 2,
  "totalRecords": 15,
  "exports": [{ "fqn": "...", "recordCount": 10 }]
}
```
