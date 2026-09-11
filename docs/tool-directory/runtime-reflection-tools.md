# Reflection-generated tools

These tools are created from reflection records at runtime.

## How tool names are built
Vork builds names in the shape groupId.artifactId.toolId when group metadata is available.

## Input parameters
Each tool uses the reflection input schema, plus bindingName when needed. Required fields come from the reflection parameter contract.

## Expected output
The tool returns the reflection execution response as JSON text. Missing required fields return a missing_parameters response.

## Access and assignment
- Hidden: no (these tools are visible when injected into a session)
- Restricted: inherited from reflection and binding policy, not a static bean annotation
- Automatic assignment: injected into sessions when active reflection bindings apply

