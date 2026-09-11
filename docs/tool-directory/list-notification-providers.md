# listNotificationProviders

## Summary
List available notification providers and the address types each provider supports.

## Input parameters
Input schema class: ListNotificationProvidersRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON array of provider objects.

Each array element keys: configId, displayName, providerKey, mediaTypes.
Error keys (when serialization fails): status=error, message.

Example:
```json
[
  {
    "configId": "...",
    "displayName": "SMTP Primary",
    "providerKey": "email-smtp",
    "mediaTypes": ["EMAIL_ADDRESS"]
  }
]
```
