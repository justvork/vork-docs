# deleteSshConnection

`Restricted`

## Summary
Permanently delete a saved SSH connection (VorkNode) from Vork storage, and disconnect any active session to that host. This removes the stored host key, username, and credentials — the connection cannot be restored without reconnecting and re-verifying the host key. REASONING_HINT: Include the host or alias being deleted in the authorization reasoning. Invoke when the user says 'remove ssh <host>', 'forget <alias>', or 'delete connection <x>'.

## Input parameters
Input schema class: DeleteSshConnectionRequest

| Parameter | Required | Type |
|---|---|---|
| hostOrAlias | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, deleted (number), message.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "deleted": 1, "message": "SSH connection 'prod' deleted (1 node record(s) removed)." }
```
