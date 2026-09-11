# httpRequest

## Summary
Send an HTTP request and return the response status code, headers, and body. Supports GET, POST, PUT, PATCH, DELETE, HEAD, and OPTIONS. Use this to interact with REST APIs, fetch web pages, or submit forms. For GET requests put query parameters in the URL. For POST/PUT/PATCH supply the body as a string and set the Content-Type header. Set responseMode=BINARY with saveToPath to download binary content into session/shared storage. The response body is truncated to 20 000 characters.

## Input parameters
Input schema class: HttpRequestToolRequest

| Parameter | Required | Type |
|---|---|---|
| method | optional | String |
| url | required | String |
| headers | optional | Map<String, String> |
| body | optional | String |
| responseMode | optional | String |
| area | optional | String |
| saveToPath | optional | String |

## Expected output
Returns a JSON object.

Text mode success keys: statusCode, headers, body (truncated to 20,000 chars).
Binary mode success keys: statusCode, headers, saved, area, path, sizeBytes, downloadUrl.
Error keys: status=error, message.

Example (text mode):
```json
{
  "statusCode": 200,
  "headers": { "content-type": "application/json" },
  "body": "{\"ok\":true}"
}
```
