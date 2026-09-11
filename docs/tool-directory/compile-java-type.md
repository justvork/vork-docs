# compileJavaType

`Restricted`

## Summary
Compile Java source code into a runtime type, save it, and make it available immediately in Vork.

## Input parameters
Input schema class: CompileTypeRequest

| Parameter | Required | Type |
|---|---|---|
| group | optional | String |
| source | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, class, group.
Validation/error keys: status=error, message.
Confirmation gate keys: status=confirm_required, message.

Example success:
```json
{ "status": "ok", "class": "jadaptive.crm.Customer", "group": "jadaptive.crm" }
```
