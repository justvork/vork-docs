# decryptString

`Restricted`

## Summary
Decrypt text using session encryption config if present; otherwise system default encryption is used.

## Input parameters
Input schema class: DecryptStringRequest

| Parameter | Required | Type |
|---|---|---|
| input | required | String |

## Expected output
Success output is a plain decrypted string.

Error: Source-specific; inspect runtime, because validation/config/keystore failures are thrown as exceptions and not encoded in a fixed JSON error object here.

Example success:
```text
my-secret
```
