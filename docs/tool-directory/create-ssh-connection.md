# createSshConnection

`Restricted`

## Summary
Save a new SSH connection by collecting hostname, port, username and credentials through a secure form — credentials never appear in the conversation history. REASONING_HINT: Use this tool when the user wants to add, register, or set up a new SSH server rather than connect to one immediately. After saving, the connection can be opened with the connectSsh tool. An optional alias can be provided to give the connection a friendly name.

## Input parameters
Input schema class: SshCreateConnectionRequest

| Parameter | Required | Type |
|---|---|---|
| alias | optional | String |

## Expected output
Success output is a human-readable plain string message (not JSON), for example connection saved guidance.
Error may be either plain string or JSON error object depending branch.
May suspend for credential and host-key verification forms.

Example success:
```text
SSH connection saved: user@example.com. Use "connect to user@example.com" to open a session.
```
