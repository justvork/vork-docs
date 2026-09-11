# getDateTime

`Default Tool`

## Summary
Return the current local system date and time, including timezone.

## Input parameters
Input schema class: GetDateTimeRequest

This tool accepts an object payload, but no explicit fields were declared in the schema class.

## Expected output
Returns a JSON object.

Success keys: status, isoDateTime, localDate, localTime, zoneId.

Example:
```json
{
  "status": "ok",
  "isoDateTime": "2026-09-10T14:05:32+01:00[Europe/London]",
  "localDate": "2026-09-10",
  "localTime": "14:05:32",
  "zoneId": "Europe/London"
}
```
