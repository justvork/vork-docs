# listMongoDBCollections

## Summary
List collections available in a MongoDB database using a saved connection profile.

## Input parameters
Input schema class: ListMongoDbCollectionsRequest

| Parameter | Required | Type |
|---|---|---|
| connectionName | optional | String |

## Expected output
Returns a JSON object.

Success keys: connectionName, database, collections (array of strings).
Error keys: status=error, message.

Example:
```json
{
  "connectionName": "default",
  "database": "crm",
  "collections": ["customers", "orders"]
}
```
