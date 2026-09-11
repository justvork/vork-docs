# encryptString

`Restricted`

## Summary
Encrypt a UTF-8 string using session encryption config if present; otherwise system default encryption is used.

## Input parameters
Input schema class: EncryptStringRequest

| Parameter | Required | Type |
|---|---|---|
| input | required | String |

## Expected output
Success output is an encrypted text string from EncryptionService (format depends on configured provider/mode).

Error: Source-specific; inspect runtime, because validation and file/config failures are thrown as exceptions rather than returned as fixed JSON in this lambda.

Example success:
```text
ENC:...
```
