# think

`Default Tool`

## Summary
Log your reasoning or analysis mid-turn without ending the turn. Call this to express your thinking, then IMMEDIATELY invoke the next action tool. NEVER end a turn with only a think call.

## Input parameters
Input schema class: ThinkRequest

| Parameter | Required | Type |
|---|---|---|
| reasoning | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, hint.

Example:
```json
{ "status": "ok", "hint": "Reasoning logged. Invoke your next tool now." }
```
