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
| `/v3/webhooks/{id}/mock-payload` | GET | Get mock payload for testing |
| `/v3/webhooks/{id}/test` | POST | Send test event |
| `/v3/webhooks/rotate-secret/{id}` | POST | Rotate webhook secret |

### Pub/Sub Channels

Alternative to webhooks using Google Cloud Pub/Sub.

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/channels` | GET, POST | List/create Pub/Sub channels |
| `/v3/channels/{id}` | GET, PUT, DELETE | Manage channel |

### Trigger Types

**Messages:** `message.created`, `message.updated`, `message.created.metadata` (Google), `message.updated.metadata` (Google)
**Events:** `event.created`, `event.updated`, `event.deleted`
**Contacts:** `contact.created`, `contact.updated`, `contact.deleted`
**Calendars:** `calendar.created`, `calendar.updated`, `calendar.deleted`
**Grants:** `grant.created`, `grant.updated`, `grant.deleted`, `grant.expired`
**Notetaker:** `notetaker.created`, `notetaker.updated`, `notetaker.meeting_state`, `notetaker.media`, `notetaker.deleted`

**Payload variants:** `.truncated` (payload >1 MB, re-query via API), `.transformed` (custom field selection applied)

### Webhook Verification

Nylas sends an initial `GET` request with a `challenge` parameter. Your endpoint must return the exact challenge value with a `200 OK` within 10 seconds.

### Webhook Security

Every notification includes an `x-nylas-signature` header — HMAC-SHA256 of the payload using your webhook secret. Always verify this signature.

### Retry Behavior

3 total delivery attempts with exponential backoff (final at ~10-20 min). Retries on: 408, 429, 502, 503, 504, 507. After 72 hours of 95%+ failures, the webhook is marked **Failed** and requires manual reactivation.

Reference: [Notifications docs](https://developer.nylas.com/docs/v3/notifications/) | [Notification schemas](https://developer.nylas.com/docs/v3/notifications/notification-schemas/) | [Pub/Sub](https://developer.nylas.com/docs/v3/notifications/pubsub-channel/) | [Webhook best practices](https://developer.nylas.com/docs/dev-guide/best-practices/webhook-best-practices/)
