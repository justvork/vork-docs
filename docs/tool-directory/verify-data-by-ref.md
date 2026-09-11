# verifyDataByRef

## Summary
Verify UTF-8 string data against a Base64 signature using the public key looked up by key identifier from generatePrivateKey. Pass secretName as either the plain key name or {{secretName}} reference. Supports SHA256withRSA and Ed25519.

## Input parameters
Input schema class: VerifyDataByRefRequest

| Parameter | Required | Type |
|---|---|---|
| data | required | String |
| signature | required | String |
| algorithm | required | String |
| secretName | required | String |

## Expected output
Success output is a plain string boolean: true or false.

Error: Source-specific; inspect runtime, because validation and crypto failures are thrown as exceptions rather than returned as fixed JSON by this lambda.

Example success:
```text
true
```
