# sshUploadTextFile

`Restricted`

## Summary
Write text content directly to a file on a remote SSH host via SFTP. The content is provided as a string and written as UTF-8. Use this instead of sshUploadFile when the content is already available as text (e.g. a generated script, config file, or document) rather than a stored file. REASONING_HINT: Include the remote destination path and a brief summary of the content in the authorization reasoning. Requires an active SSH connection established with connectSsh.

## Input parameters
Input schema class: UploadTextFileRequest

| Parameter | Required | Type |
|---|---|---|
| hostOrAlias | required | String |
| content | required | String |
| remotePath | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, remote, bytes.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "remote": "/tmp/config.txt", "bytes": 256 }
```
