# listNotificationLedgerEntries

`Restricted`

## Summary
Show paged notification delivery history with optional filters for status, destination, and provider.

## Input parameters
Input schema class: ListNotificationLedgerEntriesRequest

| Parameter | Required | Type |
|---|---|---|
| page | optional | Integer |
| pageSize | optional | Integer |
| finalState | optional | String |
| idempotencyKey | optional | String |
| destination | optional | String |
| providerConfigId | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, total, page, pageSize, entries (array of NotificationLedgerEntry objects).
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "total": 12,
  "page": 0,
  "pageSize": 50,
  "entries": [{ "uuid": "...", "finalState": "SENT" }]
}
```
