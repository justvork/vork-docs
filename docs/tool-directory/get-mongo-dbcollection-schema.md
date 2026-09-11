# getMongoDBCollectionSchema

## Summary
Inspect a MongoDB collection and infer its field structure by sampling documents.

## Input parameters
Input schema class: GetMongoDbCollectionSchemaRequest

| Parameter | Required | Type |
|---|---|---|
| connectionName | optional | String |
| collection | optional | String |
| query | optional | String |
| sampleSize | optional | Integer |

## Expected output
Returns a JSON object.

Success keys: connectionName, database, collection, sampleSize, fields.
fields is an object mapping field names to arrays/sets of inferred type labels.
Error keys: status=error, message.

Example:
```json
{
  "connectionName": "default",
  "database": "crm",
  "collection": "customers",
  "sampleSize": 20,
  "fields": { "name": ["string"], "age": ["integer"] }
}
```
