# base64EncodeString

## Summary
Encode a UTF-8 string as Base64 text.

## Input parameters
Input schema class: Base64EncodeStringRequest

| Parameter | Required | Type |
|---|---|---|
| input | required | String |

## Expected output
Success output is a plain Base64 string.

Error: Source-specific; inspect runtime, because this lambda throws IllegalArgumentException instead of returning a fixed JSON error payload.

Example success:
```text
aGVsbG8gd29ybGQ=
```
