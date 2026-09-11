# updateMongoDBDocuments

`Restricted`

## Summary
Update one or many MongoDB documents using a filter and MongoDB update JSON.

## Input parameters
Input schema class: UpdateMongoDbDocumentsRequest

| Parameter | Required | Type |
|---|---|---|
| connectionName | optional | String |
| collection | optional | String |
| query | optional | String |
| filterJson | optional | String |
| updateJson | required | String |
| multi | optional | Boolean |
| upsert | optional | Boolean |

## Expected output
Returns a JSON object.

Success keys: status=ok, collection, matchedCount, modifiedCount, upsertedId.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "collection": "customers",
  "matchedCount": 3,
  "modifiedCount": 3,
  "upsertedId": null
}
```
