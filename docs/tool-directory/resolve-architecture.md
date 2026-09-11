# resolveArchitecture

`Default Tool`

## Summary
Detect the runtime architecture for the current execution environment. No arguments required.

## Input parameters
Input schema class: ResolveArchitectureRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON object.

Success keys: status, hostOs, hostArchitecture, detectedArchitecture, targetArchitecture, targetArchitectureEnv, inDocker.

Example:
```json
{
  "status": "ok",
  "hostOs": "Mac OS X",
  "hostArchitecture": "aarch64",
  "detectedArchitecture": "arm64",
  "targetArchitecture": "arm64",
  "targetArchitectureEnv": null,
  "inDocker": false
}
```
