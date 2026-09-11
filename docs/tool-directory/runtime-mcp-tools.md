# MCP binding tools

These tools are created from connected MCP bindings at runtime.

## How tool names are built
Vork builds names in the shape mcp_bindingName__toolId.

## Input parameters
The input schema is built from MCP parameter config. AI-visible fields come from AI_REQUIRED and AI_OPTIONAL modes.

## Expected output
The tool returns the MCP server response body. If required values are missing, Vork returns missing_parameters.

## Access and assignment
- Hidden: no
- Restricted: wrapped with secure authorization when a binding tool requires authorization
- Automatic assignment: injected when session MCP bindings are active

