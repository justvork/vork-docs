# generatePrivateKey

`Restricted`

## Summary
Generate an RSA or Ed25519 key pair, store the private key securely, and return safe references for later signing and verification.

## Input parameters
Input schema class: GeneratePrivateKeyRequest

| Parameter | Required | Type |
|---|---|---|
| keyAlgorithm | optional | String |
| keySize | optional | Integer |

## Expected output
Returns a JSON object with references, not raw private key bytes.

Success keys: status, secretName, privateKeySecretRef, publicKeyLookupRef, keyAlgorithm, suggestedSigningAlgorithm, nextStep, and keySize for RSA.
May suspend for secret name input.
Error: Source-specific; inspect runtime, because this tool throws exceptions for validation/crypto failures instead of building a fixed error envelope in-code.

Example:
```json
{
  "status": "ok",
  "secretName": "MY_SIGNING_KEY",
  "privateKeySecretRef": "{{MY_SIGNING_KEY_PRIVATE}}",
  "publicKeyLookupRef": "{{MY_SIGNING_KEY_PUBLIC}}",
  "keyAlgorithm": "RSA",
  "keySize": 2048,
  "suggestedSigningAlgorithm": "SHA256withRSA",
  "nextStep": "Call getPublicKey with secretName to retrieve the Base64 public key."
}
```
