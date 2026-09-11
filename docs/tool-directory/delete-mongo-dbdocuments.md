# deleteMongoDBDocuments

`Restricted`

## Summary
Delete one or many MongoDB documents using a filter or natural-language query.

## Input parameters
Input schema class: DeleteMongoDbDocumentsRequest

| Parameter | Required | Type |
|---|---|---|
| connectionName | optional | String |
| collection | optional | String |
| query | optional | String |
| filterJson | optional | String |
| multi | optional | Boolean |

## Expected output
Returns a JSON object.

Success keys: status=ok, collection, deletedCount.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "collection": "customers", "deletedCount": 4 }
```
