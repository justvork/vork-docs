# getSurfaceReflectionContracts

`Default Tool`

## Summary
Return input/output contracts for reflections attached to the current surface session. Call this before generating UI code that invokes reflections.

## Input parameters
Input schema class: GetSurfaceReflectionContractsRequest

| Parameter | Required | Type |
|---|---|---|
| surfaceUuid | optional | String |
| bindingGroupToolId | optional | String |
| bindingProfileName | optional | String |

## Expected output
Returns a JSON object.

Success keys: surfaceId, surfaceName, bindings.
Each bindings element keys: bindingId, bindingProfile, groupName, reflections.
Each reflections element keys: reflectionId, bindingId, bindingProfile, name, description, inputParameters, method, responseContentType, outputSchema, outputSchemaValid, outputSchemaText.
Error keys: status=error, message.

Example:
```json
{
  "surfaceId": "surface-sales",
  "surfaceName": "Sales",
  "bindings": [
    {
      "bindingId": "group-customer",
      "bindingProfile": "default",
      "groupName": "Customer",
      "reflections": [
        { "reflectionId": "findCustomers", "method": "GET", "responseContentType": "application/json", "outputSchemaValid": true }
      ]
    }
  ]
}
```
