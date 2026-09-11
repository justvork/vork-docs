# discoverExportableTypes

## Summary
List the Java types that Vork can export, including approved built-in types and runtime-created types.

## Input parameters
Input schema class: DiscoverExportableTypesRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON object with key types.

types is an array; each element keys: fqn, kind, entityType, description, exportable.
Error keys: status=error, message.

Example:
```json
{
  "types": [
    {
      "fqn": "sh.vork.ai.entity.AiSession",
      "kind": "BUILT_IN",
      "entityType": true,
      "description": "...",
      "exportable": true
    }
  ]
}
```
