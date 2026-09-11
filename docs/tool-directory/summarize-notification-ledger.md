# summarizeNotificationLedger

`Restricted`

## Summary
Return notification delivery totals and grouped health statistics without listing every ledger row.

## Input parameters
Input schema class: SummarizeNotificationLedgerRequest

| Parameter | Required | Type |
|---|---|---|
| sinceEpochMillis | optional | Long |
| providerConfigId | optional | String |
| idempotencyGroup | optional | String |
| destination | optional | String |

## Expected output
Returns a JSON object.

Success keys: status, total, duplicateSuppressedCount, uniqueDestinationCount, byFinalState, byProviderKey, byMediaType, appliedFilters.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "total": 120,
  "duplicateSuppressedCount": 15,
  "uniqueDestinationCount": 37,
  "byFinalState": { "SENT": 100, "FAILED": 5, "ALREADY_SENT": 15 },
  "byProviderKey": { "email-smtp": 120 },
  "byMediaType": { "EMAIL_ADDRESS": 120 },
  "appliedFilters": {}
}
```
