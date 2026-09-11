# sshUploadFile

`Restricted`

## Summary
Upload a file to a remote SSH host via SFTP. If the file is already in Vork's file storage service (specified by UUID or filename), it is uploaded immediately. If the filename refers to a local filesystem path, explicit user authorization is required first. REASONING_HINT: Include the file source and remote destination in the authorization reasoning. Requires an active SSH connection established with connectSsh.

## Input parameters
Input schema class: UploadFileRequest

| Parameter | Required | Type |
|---|---|---|
| hostOrAlias | required | String |
| filename | required | String |
| remotePath | optional | String |

## Expected output
Returns a JSON object.

Session-source success keys: status, source=session, path, remote.
Local-source success keys: status, source=local, path, remote.
Error keys: status=error, message.
May suspend for local filesystem authorization.

Example:
```json
{ "status": "ok", "source": "session", "path": "uploads/script.sh", "remote": "/tmp/script.sh" }
```
