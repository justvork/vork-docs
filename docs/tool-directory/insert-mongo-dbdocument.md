# insertMongoDBDocument

`Restricted`

## Summary
Insert a single JSON document into a MongoDB collection.

## Input parameters
Input schema class: InsertMongoDbDocumentRequest

| Parameter | Required | Type |
|---|---|---|
| connectionName | optional | String |
| collection | required | String |
| documentJson | required | String |

## Expected output
Returns a JSON object.

Success keys: status=ok, insertedId, collection.
Error keys: status=error, message.

Example:
```json
{ "status": "ok", "insertedId": {"$oid":"..."}, "collection": "customers" }
```
