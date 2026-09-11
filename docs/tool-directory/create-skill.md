# createSkill

`Restricted`

## Summary
Persist a skill from explicit fields only. Use this after design is complete. No natural-language inference is performed by this tool.

## Input parameters
Input schema class: CreateSkillRequest

| Parameter | Required | Type |
|---|---|---|
| name | required | String |
| description | required | String |
| groupUuid | required | String |
| visibility | optional | SkillVisibility |
| parameters | optional | List<SkillParameter> |
| instructions | required | String |
| allowedTools | optional | List<String> |
| allowedTypes | optional | List<String> |
| subSkillUuids | optional | List<String> |
| secrets | optional | List<SkillSecret> |

## Expected output
Returns a JSON object.

Success keys: status=ok, skillUuid, name, groupUuid.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "skillUuid": "...", "name": "Summarize Logs", "groupUuid": "..." }
```
