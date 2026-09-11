# base64DecodeString

## Summary
Decode Base64 text to a UTF-8 string.

## Input parameters
Input schema class: Base64DecodeStringRequest

| Parameter | Required | Type |
|---|---|---|
| input | required | String |

## Expected output
Success output is a plain UTF-8 decoded string.

Error: Source-specific; inspect runtime, because this lambda throws IllegalArgumentException/decoder exceptions and does not build a fixed JSON error payload.

Example success:
```text
hello world
```
