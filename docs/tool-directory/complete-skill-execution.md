# completeSkillExecution

`Default Tool`

## Summary
Signals that the skill has fully completed its objective. Call this exactly once with the skill output when all required work is done.

## Input parameters
Input schema class: CompleteSkillExecutionRequest

| Parameter | Required | Type |
|---|---|---|
| success | required | boolean |
| output | required | String |

## Expected output
Returns a JSON object.

Success keys: status=skill_complete, output.
Context errors use keys: error.

Example:
```json
{ "status": "skill_complete", "output": "final answer" }
```
