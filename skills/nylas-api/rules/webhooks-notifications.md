---
title: Webhooks & Notifications
section: webhooks
---

## Webhooks & Notifications

**Prefer webhooks over polling for all integrations.**

### Webhook Endpoints

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/webhooks` | GET, POST | List/create webhooks |
| `/v3/webhooks/{id}` | GET, PUT, DELETE | Manage webhook |
| `/v3/webhooks/mock-payload` | POST | Get mock payload for testing |
| `/v3/webhooks/send-test-event` | POST | Send test event |
| `/v3/webhooks/rotate-secret/{id}` | POST | Rotate webhook secret |

### Pub/Sub Channels

Alternative to webhooks using Google Cloud Pub/Sub.

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/channels/pubsub` | GET, POST | List/create Pub/Sub channels |
| `/v3/channels/pubsub/{id}` | GET, PUT, DELETE | Manage channel |

### Common Trigger Types

**Messages:** `message.created`, `message.updated`, `message.created.metadata` (Google), `message.updated.metadata` (Google)
**Events:** `event.created`, `event.updated`, `event.deleted`
**Contacts:** `contact.created`, `contact.updated`, `contact.deleted`
**Calendars:** `calendar.created`, `calendar.updated`, `calendar.deleted`
**Grants:** `grant.created`, `grant.updated`, `grant.deleted`, `grant.expired`
**Notetaker:** `notetaker.created`, `notetaker.updated`, `notetaker.meeting_state`, `notetaker.media`, `notetaker.deleted`

**Payload variants:** `.truncated` is used only for `message.*` triggers when the payload exceeds 1 MB; other notification types are always sent in full. Re-query truncated messages via API. `.transformed` is used for customized `message.*` and `event.*` webhook payloads when field selection is enabled in the dashboard.

### Webhook Verification

Nylas sends an initial `GET` request with a `challenge` parameter. Your endpoint must return the exact challenge value with a `200 OK` within 10 seconds.

### Webhook Security

Every notification includes an `x-nylas-signature` header — HMAC-SHA256 of the payload using your webhook secret. Always verify this signature.

### Retry Behavior

If Nylas receives one of these temporary failure responses for a webhook notification, it retries delivery up to two more times for a total of three attempts, backing off exponentially: `408`, `429`, `502`, `503`, `504`, and `507`. The final attempt happens 10-20 minutes after the first.

Separately, Nylas marks an endpoint as `failing` after 95% non-`200` responses or non-responses over 15 minutes. While the endpoint is `failing`, Nylas continues delivery attempts for 72 hours. If failures remain above 95% over that 72-hour window, the endpoint becomes `failed` and must be manually reactivated.

Reference: [Notifications docs](https://developer.nylas.com/docs/v3/notifications/) | [Notification schemas](https://developer.nylas.com/docs/v3/notifications/notification-schemas/) | [Pub/Sub](https://developer.nylas.com/docs/v3/notifications/pubsub-channel/) | [Webhook best practices](https://developer.nylas.com/docs/dev-guide/best-practices/webhook-best-practices/)
