---
title: Email Messages API
section: email
---

## Email Messages API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/messages` | GET | List messages |
| `/v3/grants/{id}/messages/{message_id}` | GET, PUT, DELETE | Get, update, or delete a message |
| `/v3/grants/{id}/messages/send` | POST | Send email (JSON or multipart for attachments) |
| `/v3/grants/{id}/messages/clean` | PUT | Clean/parse message HTML |
| `/v3/grants/{id}/attachments/{attachment_id}` | GET | Get attachment metadata (`message_id` query param required) |
| `/v3/grants/{id}/attachments/{attachment_id}/download` | GET | Download an attachment (`message_id` query param required) |
| `/v3/grants/{id}/threads` | GET | List threads |
| `/v3/grants/{id}/threads/{thread_id}` | GET, PUT, DELETE | Get, update, or delete a thread |
| `/v3/grants/{id}/drafts` | GET, POST | List or create drafts |
| `/v3/grants/{id}/drafts/{draft_id}` | GET, PUT, DELETE | Get, update, or delete a draft |
| `/v3/grants/{id}/drafts/{draft_id}` | POST | Send a draft |
| `/v3/grants/{id}/folders` | GET, POST | List or create folders/labels |
| `/v3/grants/{id}/folders/{folder_id}` | GET, PUT, DELETE | Get, update, or delete a folder/label |

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

**Note:** Use `select` parameter to return only needed fields. To discover attachment IDs, fetch the message and select `attachments` (for example, `GET /messages/{message_id}?select=attachments`). The 25 MB limit applies to multipart upload/send requests, not attachment downloads. The Threads endpoint makes many provider calls per request, so use filters and limits to avoid rate limiting.

Reference: [Email docs](https://developer.nylas.com/docs/v3/email/) | [Messages API](https://developer.nylas.com/docs/v3/email/messages/) | [Threads](https://developer.nylas.com/docs/v3/email/threads/) | [Attachments](https://developer.nylas.com/docs/v3/email/attachments/)
