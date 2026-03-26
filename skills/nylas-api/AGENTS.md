# Nylas v3 API Reference

Compiled reference for the Nylas v3 API. For the latest details, fetch docs as markdown: `curl --location 'https://developer.nylas.com/docs/v3/<topic>/' --header 'Accept: text/markdown'`

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

### API Auth (all requests)

```bash
curl -X GET "https://api.us.nylas.com/v3/grants/<GRANT_ID>/messages" \
  -H "Authorization: Bearer <NYLAS_API_KEY>"
```

### Providers

Google (OAuth), Microsoft (OAuth), Yahoo (OAuth), iCloud (app password), IMAP (username/password), Exchange/EWS (username/password), Zoom (OAuth).

---

## 2. Email API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/messages` | GET, PUT, DELETE | List, update, delete messages |
| `/v3/grants/{id}/messages/send` | POST | Send email (JSON or multipart) |
| `/v3/grants/{id}/messages/clean` | PUT | Clean/parse message HTML |
| `/v3/grants/{id}/messages/{id}/attachments` | GET | List attachments |
| `/v3/grants/{id}/messages/{id}/attachments/{id}/download` | GET | Download (25 MB limit) |
| `/v3/grants/{id}/threads` | GET, PUT, DELETE | Threads |
| `/v3/grants/{id}/drafts` | GET, POST, PUT, DELETE | Drafts |
| `/v3/grants/{id}/folders` | GET, POST, PUT, DELETE | Folders/labels |
| `/v3/grants/{id}/messages/smart-compose` | POST | AI draft generation |
| `/v3/grants/{id}/messages/smart-compose/reply` | POST | AI reply generation |
| `/v3/grants/{id}/messages/schedules` | GET | Scheduled messages |
| `/v3/grants/{id}/messages/templates` | CRUD | Grant-level templates |
| `/v3/templates` | CRUD | App-level templates |
| `/v3/send` | POST | Transactional send (no grant) |

**Filters:** `limit`, `subject`, `from`, `to`, `unread`, `starred`, `has_attachment`, `received_before`, `received_after`, `in`, `search_query_native`, `select`

---

## 3. Calendar API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/calendars` | GET, POST, PUT, DELETE | CRUD calendars |
| `/v3/grants/{id}/events` | GET, POST, PUT, DELETE | CRUD events |
| `/v3/grants/{id}/events/{id}/send-rsvp` | POST | RSVP |
| `/v3/calendars/availability` | POST | Check availability |
| `/v3/calendars/free-busy` | POST | Check free/busy |
| `/v3/grants/{id}/room-resources` | GET | Room resources |

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
| `/v3/webhooks/{id}/test` | Send test event |
| `/v3/webhooks/rotate-secret/{id}` | Rotate secret |
| `/v3/channels` | CRUD Pub/Sub channels |

**Triggers:** message.created/updated, event.created/updated/deleted, contact.created/updated/deleted, calendar.created/updated/deleted, grant.created/updated/deleted/expired, notetaker.created/updated/meeting_state/media/deleted

**Verification:** Initial GET with `challenge` param; return exact value within 10s. **Security:** Verify `x-nylas-signature` (HMAC-SHA256). **Retries:** 3 attempts, exponential backoff; 72hr failure → manual reactivation.

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
| `/v3/grants/{id}/notetakers` | Grant-scoped CRUD |
| `/v3/notetakers` | Standalone CRUD |
| `/v3/*/notetakers/{id}/media` | Get media (MP4, JSON, JPG, TXT) |
| `/v3/*/notetakers/{id}/history` | Status history |
| `/v3/*/notetakers/{id}/leave` | Leave meeting |
| `/v3/*/notetakers/{id}/cancel` | Cancel scheduled |

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
| `/v3/applications/{id}/api-keys` | API key management |
| `/v3/domains` | Domain management |
| `/v3/workspaces` | Workspace management |

---

## 9. SDK Quick Start

**Node.js** (`npm install nylas`):
```typescript
import Nylas from "nylas";
const nylas = new Nylas({ apiKey: "NYLAS_API_KEY" });
const messages = await nylas.messages.list({ identifier: "GRANT_ID", queryParams: { limit: 10 } });
await nylas.messages.send({ identifier: "GRANT_ID", requestBody: { subject: "Hello", body: "Body", to: [{ email: "r@example.com" }] } });
```

**Python** (`pip install nylas`):
```python
from nylas import Client
nylas = Client(api_key="NYLAS_API_KEY")
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
