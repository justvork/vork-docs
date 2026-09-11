# signData

`Restricted`

## Summary
Sign UTF-8 string data using a private key and algorithm (for example SHA256withRSA). Returns Base64 signature text. privateKey should normally be provided as a secret reference such as {{signing.key.main}} from generatePrivateKey.privateKeySecretRef. Supported signature algorithms include SHA256withRSA and Ed25519.

## Input parameters
Input schema class: SignDataRequest

| Parameter | Required | Type |
|---|---|---|
| data | required | String |
| privateKey | required | String |
| algorithm | required | String |

## Expected output
Success output is a plain Base64 signature string.

Error: Source-specific; inspect runtime, because validation/crypto failures are thrown as exceptions (no fixed in-lambda JSON error object).

Example success:
```text
MEUCIQDt...
```
