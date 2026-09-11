# createMongoDBConnection

`Restricted`

## Summary
Create and save a MongoDB connection profile for your user account, then verify it can connect before storing it.

## Input parameters
Input schema class: CreateMongoDbConnectionRequest

| Parameter | Required | Type |
|---|---|---|
| connectionName | optional | String |
| connectionString | optional | String |
| host | optional | String |
| port | optional | Integer |
| database | optional | String |
| authDatabase | optional | String |
| username | optional | String |
| password | optional | String |
| credentialPromptComplete | optional | Boolean |

## Expected output
Returns a JSON object.

Success keys: status=ok, connectionName, database.
Error keys: status=error, message.
May suspend for secure credential form input before completion.

Example:
```json
{
  "status": "ok",
  "connectionName": "default",
  "database": "crm"
}
```
