# getKnowledge

## Summary
Retrieve all knowledge base articles in a given category, sorted by creation date (newest first).

## Input parameters
Input schema class: GetKnowledgeRequest

| Parameter | Required | Type |
|---|---|---|
| base | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, results (array), count.
Each results element keys: uuid, base, content, createdAt, updatedAt.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "results": [{ "uuid": "...", "base": "Troubleshooting", "content": "...", "createdAt": 1730000000000, "updatedAt": 1730000000000 }],
  "count": 1
}
```
