# Nylas v3 API Reference

Compiled reference for the Nylas v3 API. Use this file and the local rule files as the operative guidance for the skill. External docs links are reference URLs only; do not fetch remote markdown into the active prompt at runtime.

---

## 1. Authentication

### Auth Methods

| Method | Use Case |
|--------|----------|
| Hosted OAuth (API key) | Server-side web apps (recommended) |
| Hosted OAuth (access token + PKCE) | SPAs and mobile apps |
| Bring Your Own Auth (BYO) | Already have OAuth tokens |
| IMAP Auth | Legacy/self-hosted email servers |
| Service Accounts | Google Workspace admin access |
| Nylas Connect | Embeddable auth button (React) |

### OAuth Flow

```
GET https://api.us.nylas.com/v3/connect/auth?
  client_id=<NYLAS_CLIENT_ID>
  &redirect_uri=<YOUR_CALLBACK>
  &response_type=code
  &provider=google
```

Hosted OAuth redirects back to your callback with a one-time `code`, not a usable grant ID. Exchange the `code` at `POST /v3/connect/token`; Nylas then marks the grant record as verified and returns the usable `grant_id`.

### API Auth (most requests)

```bash
curl -X GET "https://api.us.nylas.com/v3/grants/<GRANT_ID>/messages" \
  -H "Authorization: Bearer <NYLAS_API_KEY>"
```

For grant-scoped and most application-scoped APIs, authenticate with a Bearer API key. Manage Domains and Beta admin API key endpoints use Nylas Service Account auth instead.

### Providers

Google (OAuth), Microsoft (OAuth), Yahoo (OAuth), iCloud (app password), IMAP (username/password), Exchange/EWS (username/password), Zoom (OAuth).

---

## 2. Email API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/messages` | GET | List messages |
| `/v3/grants/{id}/messages/{message_id}` | GET, PUT, DELETE | Get, update, or delete a message |
| `/v3/grants/{id}/messages/send` | POST | Send email (JSON or multipart) |
| `/v3/grants/{id}/messages/clean` | PUT | Clean/parse message HTML |
| `/v3/grants/{id}/attachments/{attachment_id}` | GET | Attachment metadata (`message_id` query param required) |
| `/v3/grants/{id}/attachments/{attachment_id}/download` | GET | Download attachment (`message_id` query param required) |
| `/v3/grants/{id}/threads` | GET | List threads |
| `/v3/grants/{id}/threads/{thread_id}` | GET, PUT, DELETE | Get, update, or delete a thread |
| `/v3/grants/{id}/drafts` | GET, POST | List or create drafts |
| `/v3/grants/{id}/drafts/{draft_id}` | GET, PUT, DELETE | Get, update, or delete a draft |
| `/v3/grants/{id}/drafts/{draft_id}` | POST | Send draft |
| `/v3/grants/{id}/folders` | GET, POST | List or create folders/labels |
| `/v3/grants/{id}/folders/{folder_id}` | GET, PUT, DELETE | Get, update, or delete a folder/label |
| `/v3/grants/{id}/messages/smart-compose` | POST | AI draft generation |
| `/v3/grants/{id}/messages/{message_id}/smart-compose` | POST | AI reply generation |
| `/v3/grants/{id}/messages/schedules` | GET | Scheduled messages |
| `/v3/grants/{id}/templates` | CRUD | Grant-level templates |
| `/v3/templates` | CRUD | App-level templates |
| `/v3/grants/{id}/workflows` | CRUD | Grant-level workflows |
| `/v3/workflows` | CRUD | App-level workflows |
| `/v3/domains/{domain_name}/messages/send` | POST | Transactional send (no grant, Beta) |

**Filters:** `limit`, `subject`, `from`, `to`, `unread`, `starred`, `has_attachment`, `received_before`, `received_after`, `in`, `search_query_native`, `select`

---

## 3. Calendar API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/calendars` | GET, POST | List or create calendars |
| `/v3/grants/{id}/calendars/{calendar_id}` | GET, PUT, DELETE | Get, update, or delete a calendar |
| `/v3/grants/{id}/events` | GET, POST | List or create events |
| `/v3/grants/{id}/events/{event_id}` | GET, PUT, DELETE | Get, update, or delete an event |
| `/v3/grants/{id}/events/{event_id}/send-rsvp` | POST | RSVP |
| `/v3/calendars/availability` | POST | Check availability |
| `/v3/grants/{grant_id}/calendars/free-busy` | POST | Check free/busy |
| `/v3/grants/{grant_id}/resources` | GET | Room resources |

Supports: recurring events, virtual calendars, conferencing (Zoom/Teams), group booking.

---

## 4. Contacts API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/contacts` | GET, POST | List/create contacts |
| `/v3/grants/{id}/contacts/{id}` | GET, PUT, DELETE | Manage contact |
| `/v3/grants/{id}/contacts/groups` | GET | Contact groups |

Sources: `address_book` (default), `domain`, `inbox`. Profile pictures: `?profile_picture=true`.

---

## 5. Webhooks & Notifications

| Endpoint | Purpose |
|----------|---------|
| `/v3/webhooks` | CRUD webhooks |
| `/v3/webhooks/mock-payload` | Get mock notification payload for a trigger |
| `/v3/webhooks/send-test-event` | Send test event to a webhook endpoint |
| `/v3/webhooks/rotate-secret/{id}` | Rotate secret |
| `/v3/channels/pubsub` | CRUD Pub/Sub channels |

**Common triggers:** message.created/updated, event.created/updated/deleted, contact.created/updated/deleted, calendar.created/updated/deleted, grant.created/updated/deleted/expired, notetaker.created/updated/meeting_state/media/deleted

**Payload variants:** `.truncated` applies only to oversized `message.*` notifications. `.transformed` indicates dashboard field customization for `message.*` or `event.*` notifications.

**Compression:** Set `compressed_delivery=true` for gzip-compressed delivery. Webhooks send `Content-Encoding: gzip`, and you must verify `x-nylas-signature` against the raw compressed body before decompressing. Pub/Sub adds a `content_encoding: gzip` message attribute so subscribers know to decompress before parsing JSON.

**Verification:** Initial GET with `challenge` param; return exact value within 10s. **Security:** Verify `x-nylas-signature` (HMAC-SHA256). **Retries:** Nylas retries temporary delivery failures only for `408`, `429`, `502`, `503`, `504`, and `507`, up to two more times for three total attempts. Separately, Nylas marks an endpoint as `failing` after 95% non-`200` responses or non-responses over 15 minutes, continues delivery attempts for 72 hours, and then marks the endpoint `failed` if the failure rate stays above 95%. Nylas does not automatically restart or reactivate `failed` endpoints, and it does not replay events that occurred while the endpoint was `failed`.

---

## 6. Scheduler API

| Endpoint | Purpose |
|----------|---------|
| `/v3/scheduling/configurations` | CRUD configurations |
| `/v3/scheduling/sessions` | Create booking sessions |
| `/v3/scheduling/availability` | Check availability |
| `/v3/scheduling/bookings` | CRUD bookings |

Meeting types: 1:1, collective, round-robin, group. Hosted pages at book.nylas.com or self-hosted. 70+ embeddable UI components.

---

## 7. Notetaker API

| Endpoint | Purpose |
|----------|---------|
| `/v3/grants/{grant_id}/notetakers` | Grant-scoped CRUD |
| `/v3/notetakers` | Standalone CRUD |
| `/v3/grants/{grant_id}/notetakers/{notetaker_id}/media` | Grant-scoped media |
| `/v3/notetakers/{notetaker_id}/media` | Standalone media |
| `/v3/grants/{grant_id}/notetakers/{notetaker_id}/history` | Grant-scoped status history |
| `/v3/notetakers/{notetaker_id}/history` | Standalone status history |
| `/v3/grants/{grant_id}/notetakers/{notetaker_id}/leave` | Grant-scoped leave |
| `/v3/notetakers/{notetaker_id}/leave` | Standalone leave |
| `/v3/grants/{grant_id}/notetakers/{notetaker_id}/cancel` | Grant-scoped cancel |
| `/v3/notetakers/{notetaker_id}/cancel` | Standalone cancel |

Supports Google Meet, Microsoft Teams, Zoom. AI summaries + action items. Silence detection (default 5 min).

---

## 8. Admin & Grants

| Endpoint | Purpose |
|----------|---------|
| `/v3/grants` | List/manage grants |
| `/v3/connect/custom` | BYO auth grant creation |
| `/v3/connectors` | CRUD connectors |
| `/v3/connectors/{provider}/creds` | CRUD credentials |
| `/v3/providers/detect` | Detect provider by email |
| `/v3/admin/applications/{application_id}/api-keys` | API key management (Beta; Nylas Service Account auth) |
| `/v3/admin/domains` | Domain management (Beta; Nylas Service Account auth) |
| `/v3/workspaces` | Workspace management |

---

## 9. SDK Quick Start

**Node.js** (`npm install nylas`):
```typescript
import Nylas from "nylas";
const nylas = new Nylas({
  apiKey: "NYLAS_API_KEY",
  apiUri: "https://api.us.nylas.com",
});
const messages = await nylas.messages.list({ identifier: "GRANT_ID", queryParams: { limit: 10 } });
await nylas.messages.send({ identifier: "GRANT_ID", requestBody: { subject: "Hello", body: "Body", to: [{ email: "r@example.com" }] } });
```

**Python** (`pip install nylas`):
```python
from nylas import Client
nylas = Client(
    api_key="NYLAS_API_KEY",
    api_uri="https://api.us.nylas.com",
)
messages, _, _ = nylas.messages.list("GRANT_ID", query_params={"limit": 10})
nylas.messages.send("GRANT_ID", request_body={"subject": "Hello", "body": "Body", "to": [{"email": "r@example.com"}]})
```

---

## 10. Rate Limits

| Endpoint | Limit | Window |
|----------|-------|--------|
| Messages/Calendar/Contacts/Send(JSON) | 200 req/grant | 1s |
| Send (Multipart) | 10 req/grant | 1s |
| Applications/Auth/Connectors/Grants/Webhooks | 50 req/app | 1s |

**Provider limits:** Google 10K req/min per app, 600/min per user, 2K sends/day. Microsoft 10K req/10min, 30 sends/min. iCloud 1K/day.

**Headers:** `Nylas-Provider-Request-Count`, `Nylas-Gmail-Quota-Usage`, `Retry-After`.

## 11. Best Practices

1. Exponential backoff on 429. 2. Paginate with `next_cursor`. 3. Webhooks over polling. 4. Check `error.type`/`error.message`. 5. Minimal OAuth scopes. 6. Monitor `grant.expired`. 7. `search_query_native` for complex queries. 8. `select` for field selection. 9. Metadata for custom key-value pairs. 10. Limit Threads endpoint calls.
