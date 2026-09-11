# searchMongoDBDocuments

## Summary
Search and read MongoDB documents using either a raw filter or a natural-language query, with paging and sorting.

## Input parameters
Input schema class: SearchMongoDbDocumentsRequest

| Parameter | Required | Type |
|---|---|---|
| connectionName | optional | String |
| collection | optional | String |
| query | optional | String |
| filterJson | optional | String |
| projectionJson | optional | String |
| sortField | optional | String |
| sortOrder | optional | String |
| page | optional | Integer |
| pageSize | optional | Integer |

## Expected output
Returns a JSON object.

Success keys: connectionName, database, collection, total, page, pageSize, filter, results.
results is an array of document objects.
Error keys: status=error, message.

Example:
```json
{
  "connectionName": "default",
  "database": "crm",
  "collection": "customers",
  "total": 42,
  "page": 0,
  "pageSize": 20,
  "filter": {},
  "results": [{ "_id": {"$oid":"..."}, "name": "Acme" }]
}
```
