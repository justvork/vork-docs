# getPublicKey

## Summary
Return the Base64-encoded X.509 public key bytes for a key identifier created by generatePrivateKey. Use the same secretName/reference used for signing.

## Input parameters
Input schema class: GetPublicKeyRequest

| Parameter | Required | Type |
|---|---|---|
| secretName | required | String |

## Expected output
Returns a JSON object.

Success keys: status, secretName, publicKeyBase64, javaHint.
Error: Source-specific; inspect runtime, because missing/invalid inputs are thrown as exceptions and not wrapped in a fixed in-lambda error object.

Example:
```json
{
  "status": "ok",
  "secretName": "MY_SIGNING_KEY",
  "publicKeyBase64": "MIIBIjANBgkq...",
  "javaHint": "Reconstruct using KeyFactory and X509EncodedKeySpec(Base64-decoded bytes)."
}
```
