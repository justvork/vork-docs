# delegateTask

## Summary
Delegate work to another agent using a dynamic one-off background run. If jobUuid is provided, its policy/tooling settings are inherited and validated against the selected agent; if omitted, the run is created directly from the target background agent plus the provided prompt.

## Input parameters
Input schema class: DelegateTaskRequest

| Parameter | Required | Type |
|---|---|---|
| agentName | required | String |
| jobUuid | optional | String |
| prompt | required | String |
| sessionFiles | optional | List<String> |

## Expected output
Returns a JSON object.

Scheduled success keys: status=scheduled, jobId, jobName, agentName, agentUuid, invocationType, and optional copiedSessionFileCount/sourceJobUuid.
Error keys: status=error, message (+ contextual keys such as candidates, agentType, jobUuid).

Example:
```json
{
  "status": "scheduled",
  "jobId": "dynamic-abcd1234",
  "jobName": "Dynamic: Planner",
  "agentName": "Planner",
  "agentUuid": "...",
  "invocationType": "DYNAMIC"
}
```
