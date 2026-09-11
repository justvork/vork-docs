# getSurfaceSkillContracts

`Default Tool`

## Summary
Return contracts for skills attached to the current surface session, including groupId and skillId values and each skill output schema.

## Input parameters
Input schema class: GetSurfaceSkillContractsRequest

| Parameter | Required | Type |
|---|---|---|
| surfaceUuid | optional | String |

## Expected output
Returns a JSON object.

Success keys: surfaceUuid, skills.
Each skills element keys: groupId, skillId, toolName, name, outputContentType, outputSchema.
Error keys: status=error, message.

Example:
```json
{
  "surfaceUuid": "...",
  "skills": [
    {
      "groupId": "grp-sales",
      "skillId": "skill-summarize",
      "toolName": "summarizeSales",
      "name": "Summarize Sales",
      "outputContentType": "application/json",
      "outputSchema": { "type": "object" }
    }
  ]
}
```
