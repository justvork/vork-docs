# disconnectSsh

## Summary
Close an active SSH connection and release all associated resources (terminal sessions, SFTP client, and the underlying SSH client). REASONING_HINT: Include the host or alias being disconnected in the authorization reasoning. Invoke when the user says 'disconnect <host>', 'close ssh <alias>', or 'exit <host>'.

## Input parameters
Input schema class: DisconnectSshRequest

| Parameter | Required | Type |
|---|---|---|
| hostOrAlias | required | String |

## Expected output
Success output is a plain string confirmation message.

Error keys: status=error, message.

Example success:
```text
SSH connection "prod" has been closed.
```
