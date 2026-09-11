# listJavaTypes

## Summary
List all custom Java types that were compiled and saved in Vork.

## Input parameters
Input schema class: ListJavaTypesRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON object with key types (array).

Each types element keys: fqn, classFiles, createdAt.
If none: {"types":[]}.

Example:
```json
{
  "types": [
    { "fqn": "jadaptive.crm.Customer", "classFiles": 1, "createdAt": "Thu Sep 10 10:00:00 UTC 2026" }
  ]
}
```
