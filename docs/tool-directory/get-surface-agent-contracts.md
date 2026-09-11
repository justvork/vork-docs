# getSurfaceAgentContracts

`Default Tool`

## Summary
Return contracts for agents assigned to the current surface session, including agentTemplateId, name, and agentType.

## Input parameters
Input schema class: GetSurfaceAgentContractsRequest

| Parameter | Required | Type |
|---|---|---|
| surfaceUuid | optional | String |

## Expected output
Returns a JSON object.

Success keys: surfaceUuid, agents.
Each agents element keys: agentTemplateId, name, agentType.
Error keys: status=error, message.

Example:
```json
{
  "surfaceUuid": "...",
  "agents": [
    { "agentTemplateId": "...", "name": "Planner", "agentType": "BACKGROUND" }
  ]
}
```
