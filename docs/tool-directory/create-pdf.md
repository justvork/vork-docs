# createPdf

`Default Tool`

## Summary
Create a PDF file from MARKDOWN (default) or HTML content, store it in the session/shared file area, and return a direct download URL. Set attachToChat=false to generate the PDF without adding a chat attachment. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message.

## Input parameters
Input schema class: CreatePdfRequest

| Parameter | Required | Type |
|---|---|---|
| content | required | String |
| format | optional | String |
| outputPath | optional | String |
| area | optional | String |
| attachToChat | optional | Boolean |

## Expected output
Returns a JSON object.

Success keys: status, area, path, name, sizeBytes, downloadUrl.
Error keys: status=error, message.

Example:
```json
{
  "status": "ok",
  "area": "SESSION",
  "path": "report.pdf",
  "name": "report.pdf",
  "sizeBytes": 12345,
  "downloadUrl": "/api/session-files/download?..."
}
```
