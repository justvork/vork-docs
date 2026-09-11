# listSshConnections

## Summary
List all active SSH connections for the current session, showing each connection's alias and hostname. Invoke when the user asks which hosts are connected, or to see open SSH sessions.

## Input parameters
Input schema class: ListSshConnectionsRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns JSON.

If empty: object with keys connections (empty array), message.
Otherwise: object with key connections where each element has alias and canonicalHost.
Error keys: status=error, message.

Example:
```json
{
  "connections": [
    { "alias": "prod", "canonicalHost": "example.com:22" }
  ]
}
```
