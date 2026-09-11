# readChatHistory

`Default Tool`

## Summary
Read one chat-history item's full content from the current session only. Supports references: message UUID, 'uuid:<uuid>', numeric index, 'index:<n>', '-1' for last item, 'last', and 'last-assistant'.

## Input parameters
Input schema class: ReadChatHistoryRequest

| Parameter | Required | Type |
|---|---|---|
| reference | required | String |

## Expected output
Returns a JSON object.

Success keys: status, sessionUuid, reference, index, messageUuid, role, timestamp, textResponse.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "sessionUuid": "...",
  "reference": "last-assistant",
  "index": 14,
  "messageUuid": "...",
  "role": "ASSISTANT",
  "timestamp": 1730000000000,
  "textResponse": "Here is the result..."
}
```
