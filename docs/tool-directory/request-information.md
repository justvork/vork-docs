# requestInformation

## Summary
Request information from one or more channels by generating per-recipient input links, creating attention alerts, and optionally sending out-of-band notifications. requesterMessage and recipientMessage are required and must be explicitly authored for each call. Response policy can be AUTO, FIRST, ALL, or QUORUM. The tool suspends the current session until the response threshold is met.

## Input parameters
Input schema class: RequestInformationToolRequest

| Parameter | Required | Type |
|---|---|---|
| channelNames | optional | List<String> |
| promptText | required | String |
| requesterMessage | required | String |
| recipientMessage | required | String |
| responsePolicy | optional | String |
| quorumCount | optional | Integer |
| sendNotifications | optional | Boolean |
| alertName | optional | String |
| alertResolutionPolicy | optional | String |
| attentionAt | optional | Long |
| requestCampaignId | optional | String |
| responsesJson | optional | String |
| responseCount | optional | Integer |

## Expected output
Primary behavior is suspension (campaign form flow).

Explicit immediate JSON errors use keys: status=error, message.
Resume shortcut success keys (when aggregated responses are provided and campaign is satisfied): status=ok, campaignId, responseCount, responsesJson.

Example resume payload:
```json
{
  "status": "ok",
  "campaignId": "req-123",
  "responseCount": 2,
  "responsesJson": "[{...}]"
}
```
