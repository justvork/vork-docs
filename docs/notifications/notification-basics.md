# Notification Basics

Notifications in Vork are designed to be safe, flexible, and easy to check.

If you are new to this area, start with `listNotificationProviders`, then send one small test message with `sendNotification`.

## Provider Types Supported Today

Vork currently supports these destination types:
- Email address
- Phone number (SMS)
- Telegram
- Slack

Vork currently includes these provider types:
- SMTP Email
- SendGrid Email
- Twilio SMS
- Telegram
- Slack

## Which Providers Work With Direct Sending

Direct sending means you call `sendNotification` with a destination address.

Right now, direct sending is designed for:
- SMTP Email
- SendGrid Email
- Twilio SMS

Telegram and Slack are still supported in the app, but they require prior setup/registration and are not treated as direct-address providers for `sendNotification`.

## Using Notification Tools in a Skill or AI

If you want a skill or agent to send messages for you, it is usually safe to include these two tools:
- `listNotificationProviders`
- `sendNotification`

This works well because the AI can first check what provider is available, then pick one that matches your destination type.

Simple instruction patterns you can use:
- "Send an email to person@example.com"
- "Send an SMS to +14155552671"

You can also be a little more specific when needed:
- "Send an email to person@example.com with subject 'Reminder' and include this message body."
- "Send an SMS to +14155552671 with this alert text."

Best practice:
- Let the AI call `listNotificationProviders` first.
- Then let it call `sendNotification` using a matching provider.
- For repeated or retried sends, include an `idempotencyGroup` so the same person does not receive duplicate messages.

## Where Notifications Can Be Triggered

You can trigger notifications from tools, and Vork can also trigger them automatically during built-in flows.

### Tool-driven triggers

- `sendNotification`: sends one message to one destination.
- `requestInformation` with `sendNotifications=true`: sends request links to selected channels.

### Built-in app triggers

- Background authorization flow: when a background task needs approval, Vork sends out-of-band notification links to configured user notification targets.
- Request campaigns: when a campaign is created with notifications enabled, Vork sends channel/user notification links so people can respond.

## How To Send a Notification (Simple Flow)

1. Call `listNotificationProviders`.
2. Pick a `providerConfigId` that matches your destination type.
3. Call `sendNotification` with title, body, recipient type, and address.
4. Check results with:
- `listNotificationLedgerEntries` for row-by-row details.
- `summarizeNotificationLedger` for quick totals and trends.

## Idempotency: How To Prevent Duplicate Messages

Idempotency is a safety feature that helps you avoid sending the same message multiple times to the same destination.

You use it by setting `idempotencyGroup` in `sendNotification`.

### What happens when you set idempotencyGroup

Vork creates a hidden dedupe key using:
- your `idempotencyGroup`,
- the destination type (for example email vs SMS), and
- the destination address.

If a previous send already succeeded for the same combination, Vork skips a duplicate send and records it as already sent.

### Important behavior

- A previous `SENT` result blocks duplicates.
- A previous `FAILED` result does not block retries.
- This means you can safely retry failures with the same `idempotencyGroup`.

## Idempotency Pattern for Skills and Agents

When skills or agents send messages in loops or retries, use a stable group value for one logical campaign.

Good examples:
- `invoice-reminder-2026-09-11`
- `onboarding-day-1`
- `security-alert-incident-4481`

Then keep that value the same across retries for the same campaign.

### Practical example

If your skill sends onboarding emails and gets retried, keep `idempotencyGroup=onboarding-day-1` for that run.

Outcome:
- First successful send to `person@example.com` is delivered.
- Repeated attempts to the same person are suppressed as duplicates.
- Failed sends can be retried safely until one succeeds.

## Troubleshooting Checklist

If users report missing or duplicate notifications:

1. Open `summarizeNotificationLedger` for a quick state overview.
2. Filter `listNotificationLedgerEntries` by destination and time.
3. Check whether rows are `SENT`, `FAILED`, or `ALREADY_SENT`.
4. If duplicate suppression is too broad, split campaigns by using a more specific `idempotencyGroup`.
5. If failures are high, test provider configuration and retry with the same idempotency group.

## Quick Encouragement

Start small.

Send one test message, verify it in the ledger, then scale up.

That one habit catches most issues early and keeps your users from receiving extra notifications.
