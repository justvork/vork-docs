# configureSessionApproval

`Restricted`

## Summary
Configure or clear a session-scoped approval override for protected tool calls. Admin-only: requires USERS_MANAGE. Use clear=true to remove override. When enabled, provide either policyId, policyName, or channelNames. responsePolicy supports FIRST, ALL, or QUORUM.

## Input parameters
Input schema class: ConfigureSessionApprovalRequest

| Parameter | Required | Type |
|---|---|---|
| enabled | optional | Boolean |
| clear | optional | Boolean |
| policyId | optional | String |
| policyName | optional | String |
| channelNames | optional | List<String> |
| responsePolicy | optional | String |
| quorum | optional | Integer |
| reason | optional | String |

## Expected output
Returns a JSON object.

Success (set) keys: status=ok, sessionUuid, override (object).
Success (clear) keys: status=ok, action=cleared.
Error keys: status=error, message.

Example (set):
```json
{
  "status": "ok",
  "sessionUuid": "...",
  "override": {
    "enabled": true,
    "policyId": "...",
    "channels": ["ops-team"],
    "responsePolicy": "FIRST"
  }
}
```
