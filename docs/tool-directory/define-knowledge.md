# defineKnowledge

`Restricted`

## Summary
Persistently define a new knowledge article in the knowledge base. The base is a category name (e.g. 'Deployment', 'Troubleshooting'). Content is the free-text article.

## Input parameters
Input schema class: DefineKnowledgeRequest

| Parameter | Required | Type |
|---|---|---|
| base | required | String |
| content | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, uuid, base, createdAt.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "uuid": "...", "base": "Troubleshooting", "createdAt": 1730000000000 }
```
