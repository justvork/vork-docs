# createAttentionAlert

## Summary
Create an attention alert for one or more channels. Channel names are globally unique and case-insensitive. Resolution policy must be ACTION_REQUIRED or DISMISSABLE. Prefer DISMISSABLE when there is no actionUrl, and use ACTION_REQUIRED when actionUrl is present. Never use FIRST_ACK or ALL_ACK. If a channel query is ambiguous, this tool suspends and asks the user to choose the intended channel.

## Input parameters
Input schema class: CreateAttentionAlertToolRequest

| Parameter | Required | Type |
|---|---|---|
| channelNames | optional | List<String> |
| selectedChannelName | optional | String |
| alertName | optional | String |
| description | optional | String |
| resolutionPolicy | optional | String |
| actionUrl | optional | String |
| attentionAt | optional | Long |
| sourceType | optional | String |
| sourceId | optional | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, alertUuid, channels, policy, sourceType.
Error keys: status=error, message.
May suspend when channel query is ambiguous.

Example:
```json
{
  "status": "ok",
  "alertUuid": "...",
  "channels": ["ops-team"],
  "policy": "DISMISSABLE",
  "sourceType": "CUSTOM"
}
```
