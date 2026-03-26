---
title: Email Messages API
section: email
---

## Email Messages API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/messages` | GET, PUT, DELETE | List, update, delete messages |
| `/v3/grants/{id}/messages/send` | POST | Send email (JSON or multipart for attachments) |
| `/v3/grants/{id}/messages/clean` | PUT | Clean/parse message HTML |
| `/v3/grants/{id}/messages/{id}/attachments` | GET | List attachments |
| `/v3/grants/{id}/messages/{id}/attachments/{id}/download` | GET | Download attachment (25 MB limit) |
| `/v3/grants/{id}/threads` | GET, PUT, DELETE | List, update, delete threads |
| `/v3/grants/{id}/drafts` | GET, POST, PUT, DELETE | CRUD drafts |
| `/v3/grants/{id}/drafts/{id}` | POST (send) | Send a draft |
| `/v3/grants/{id}/folders` | GET, POST, PUT, DELETE | Manage folders/labels |

**Send email:**

```bash
curl -X POST "https://api.us.nylas.com/v3/grants/<GRANT_ID>/messages/send" \
  -H "Authorization: Bearer <API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "subject": "Hello",
    "body": "<p>Message body</p>",
    "to": [{"email": "recipient@example.com", "name": "Recipient"}]
  }'
```

**Filters:** `limit`, `subject`, `from`, `to`, `unread`, `starred`, `has_attachment`, `received_before`, `received_after`, `in`, `search_query_native`, `select` (field selection to reduce payload)

**Note:** Use `select` parameter to return only needed fields. The Threads endpoint makes many provider calls per request — use filters and limits to avoid rate limiting.

Reference: [Email docs](https://developer.nylas.com/docs/v3/email/) | [Messages API](https://developer.nylas.com/docs/v3/email/messages/) | [Threads](https://developer.nylas.com/docs/v3/email/threads/) | [Attachments](https://developer.nylas.com/docs/v3/email/attachments/)
