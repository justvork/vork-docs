# sshDownloadFile

## Summary
Download a file from a remote SSH host to either Vork's file storage service (no extra authorization required) or a local filesystem path (requires explicit user authorization). REASONING_HINT: Include the remote file path and destination in the authorization reasoning. Requires an active SSH connection established with connectSsh.

## Input parameters
Input schema class: DownloadFileRequest

| Parameter | Required | Type |
|---|---|---|
| hostOrAlias | required | String |
| remotePath | required | String |
| localPath | optional | String |

## Expected output
Returns a JSON object.

Success (session destination) keys: status, location=session, path, name, size, downloadUrl, attachmentRef.
Success (local destination) keys: status, location=local, path.
Error keys: status=error, message.
May suspend for local filesystem authorization.

Example (session):
```json
{
  "status": "ok",
  "location": "session",
  "path": "downloads/uuid-file.txt",
  "name": "uuid-file.txt",
  "size": 1280,
  "downloadUrl": "/api/session-files/download?...",
  "attachmentRef": "session-url:/api/session-files/download?..."
}
```
