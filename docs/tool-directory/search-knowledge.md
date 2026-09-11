# searchKnowledge

## Summary
Search knowledge base articles by category and keyword. Returns matching articles with content, timestamps, and UUIDs.

## Input parameters
Input schema class: SearchKnowledgeRequest

| Parameter | Required | Type |
|---|---|---|
| base | required | String |
| query | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, results (array), count.
Each results element keys: uuid, base, content, createdAt, updatedAt.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "results": [{ "uuid": "...", "base": "Deployment", "content": "..." }],
  "count": 1
}
```
