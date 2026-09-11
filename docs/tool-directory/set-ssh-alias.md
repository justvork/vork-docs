# setSshAlias

## Summary
Rename the alias of an existing SSH connection. REASONING_HINT: Include the current identifier and the new alias in the authorization reasoning. Invoke when the user says 'alias <host> as <name>' or 'rename connection <x> to <y>'. The hostOrAlias field accepts the current alias or hostname to identify the connection.

## Input parameters
Input schema class: SetSshAliasRequest

| Parameter | Required | Type |
|---|---|---|
| hostOrAlias | required | String |
| newAlias | required | String |

## Expected output
Success output is a plain string confirmation message.

Error keys: status=error, message.

Example success:
```text
Connection "old-alias" has been renamed to "new-alias".
```
