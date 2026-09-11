# Skill-generated tools

These tools are created from saved skills at runtime.

## How tool names are built
The name comes from each skill toolName value.

## Input parameters
The input schema is built from skill parameters. Secret fields are not exposed to the AI directly.

## Expected output
Successful runs return the skill result payload. Missing required inputs return missing_parameters.

## Access and assignment
- Hidden: no
- Restricted: controlled by skill allow-lists and runtime authorization rules
- Automatic assignment: injected when the active agent or session has assigned skill UUIDs

