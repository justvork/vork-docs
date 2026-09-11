# configureEncryption

`Restricted`

## Summary
Configure session encryption mode for encryptString/decryptString. Use type=RSA with a PKCS#8 private key file, or type=SOFTWARE with a .p12 keystore file. For SOFTWARE, keystoreAlias and keystorePassword are optional and defaults are used when omitted. Use clear=true to revert to system default encryption.

## Input parameters
Input schema class: ConfigureEncryptionRequest

| Parameter | Required | Type |
|---|---|---|
| type | optional | String |
| filePath | optional | String |
| keystoreAlias | optional | String |
| keystorePassword | optional | String |
| clear | optional | Boolean |

## Expected output
Returns a JSON object.

Success (set) keys: status, sessionUuid, configuration (object with type, filePath, optional keystoreAlias/keystorePassword).
Success (clear) keys: status, cleared=true.
Error: Source-specific; inspect runtime for thrown validation exceptions not encoded in-tool.

Example (set):
```json
{
  "status": "ok",
  "sessionUuid": "...",
  "configuration": { "type": "RSA", "filePath": "keys/private.pem" }
}
```
