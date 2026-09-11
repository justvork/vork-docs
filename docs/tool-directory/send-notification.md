# sendNotification

`Restricted`

## Summary
Send a notification through a configured provider to an email address or phone number for internal or external recipients.

## Input parameters
Input schema class: SendNotificationRequest

| Parameter | Required | Type |
|---|---|---|
| providerConfigId | required | String |
| title | required | String |
| body | required | String |
| bodyContentType | optional | String |
| idempotencyGroup | optional | String |
| originatingAgent | optional | String |
| originatingSkill | optional | String |
| recipientType | required | NotificationRecipientType |
| externalParticipant | optional | String |
| address | required | String |

## Expected output
Returns a JSON object.

Always includes status and recipientType.
May include message, ledgerEntryId, idempotencyKey, mediaType, destination, providerConfigId, providerKey, providerMessageReferenceId, finalState.
Input-validation and serialization errors use status=error, message.

Example:
```json
{
  "status": "ok",
  "recipientType": "EXTERNAL",
  "ledgerEntryId": "...",
  "idempotencyKey": "...",
  "mediaType": "EMAIL_ADDRESS",
  "destination": "user@example.com",
  "providerConfigId": "...",
  "providerKey": "email-smtp",
  "finalState": "SENT"
}
```
