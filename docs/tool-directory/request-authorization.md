# requestAuthorization

`Restricted`

## Summary
Create a pre-authorization token for an exact restricted tool payload. This tool is itself restricted and requires explicit approval. Tokens are one-time and consumed only when the target restricted tool is called with an exact payload match.

## Input parameters
Input schema class: RequestAuthorizationToolRequest

| Parameter | Required | Type |
|---|---|---|
| toolName | required | String |
| argumentsJson | required | String |
| scope | optional | String |
| ttlSeconds | optional | Integer |
| reason | optional | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, preAuthorizationToken, toolName, scope, argumentsSha256, expiresAt.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "preAuthorizationToken": "...",
  "toolName": "createSkill",
  "scope": "single-use",
  "argumentsSha256": "...",
  "expiresAt": 1730000000000
}
```
