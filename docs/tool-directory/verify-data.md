# verifyData

## Summary
Verify UTF-8 string data against a Base64 signature and public key using the provided algorithm. Returns true or false.

## Input parameters
Input schema class: VerifyDataRequest

| Parameter | Required | Type |
|---|---|---|
| data | required | String |
| publicKey | required | String |
| signature | required | String |
| algorithm | required | String |

## Expected output
Success output is a plain string boolean: true or false.

Error: Source-specific; inspect runtime, because validation/crypto failures are thrown as exceptions (no fixed in-lambda JSON error object).

Example success:
```text
false
```
