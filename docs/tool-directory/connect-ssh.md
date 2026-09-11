# connectSsh

`Restricted`

## Summary
Establish an SSH connection to a remote host and start an interactive shell session. REASONING_HINT: Include the host and alias in the authorization reasoning. Invoke this tool when the user says 'ssh <host>', 'connect <host>', or asks to connect to a server. The host may be specified as user@host:port, user@host, host:port, or just host — the user@ prefix is an SSH login username, never a friendly label. ALIAS_HINT: when the user says 'connect to X as Y' or 'call it Y', Y is a friendly alias for the connection — put Y in the 'alias' field and leave the username out of 'host' unless explicitly given. An optional alias can be provided to refer to the connection by a short name in subsequent tool calls.

## Input parameters
Input schema class: SshConnectRequest

| Parameter | Required | Type |
|---|---|---|
| host | required | String |
| alias | optional | String |

## Expected output
Success output is a plain string confirmation message.

Error keys: status=error, message.
May suspend for host-key trust flow.

Example success:
```text
You are now connected to example.com with alias "prod".
```
