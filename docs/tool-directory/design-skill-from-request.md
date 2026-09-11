# designSkillFromRequest

## Summary
Analyze a natural-language skill request using the full non-hidden tool catalog and return a draft skill design without persisting changes.

## Input parameters
Input schema class: DesignSkillRequest

| Parameter | Required | Type |
|---|---|---|
| request | required | String |
| skillName | optional | String |
| category | optional | String |
| targetGroup | optional | String |
| author | optional | String |
| visibility | optional | SkillVisibility |
| dryRun | optional | Boolean |

## Expected output
Returns a JSON object (SkillAuthoringResult).

Top-level keys: status, feasible, rationale, dryRun, skillUuid, skillName, selectedTools, primaryToolMatches, selectedSubSkillUuids, selectedSimilarSkillUuids, availableToolIds, attachedToConcierge, resolvedGroupUuid, resolvedGroupName, groupCreated, recommendedAutoShareWithinGroup, autoShareRecommendation, generatedSkillRequest.
Error keys: status=error, message (serialization fallback).

Example:
```json
{
  "status": "ok",
  "feasible": true,
  "skillName": "Investigate Build Failure",
  "selectedTools": ["searchTextFile", "readTextFileRange"],
  "generatedSkillRequest": { "name": "Investigate Build Failure" }
}
```
