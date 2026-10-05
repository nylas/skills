---
title: Manage Templates and Workflows, and Send a Stored Template
section: api
---

## Manage Templates and Workflows, and Send a Stored Template

| Action | Templates | Workflows |
|---|---|---|
| List | `GET /v3/templates` | `GET /v3/workflows` |
| Get | `GET /v3/templates/{id}` | `GET /v3/workflows/{id}` |
| Update | `PUT /v3/templates/{id}` (`name`, `subject`, `body`, `engine`) | `PUT /v3/workflows/{id}` (`name`, `trigger_event`, `template_id`, `delay`, `is_enabled`, `from`) |
| Delete | `DELETE /v3/templates/{id}` | `DELETE /v3/workflows/{id}` |

- **Grant-level:** the same paths under `/v3/grants/{grant_id}/`. Application-level lists don't include them.
- **Updating a template:** this changes the email for every workflow that uses it, so render-test before you `PUT`.
- **Removing `from`:** once a workflow has `from`, you can't remove it. Sending `"from": null` doesn't clear it, so delete the workflow and create a new one instead.

**Send a stored template.** Pass the template ID and variables in the `template` field. `strict` defaults to `true`, so keep it on: with `false`, missing variables render as empty strings.

```bash
# From the user's own mailbox
curl -s -X POST "$NYLAS_API_URI/v3/grants/$GRANT_ID/messages/send" \
  -H "Authorization: Bearer $NYLAS_API_KEY" -H "Content-Type: application/json" \
  -d '{
    "to": [{ "name": "Nyla Hart", "email": "nyla.hart@example.com" }],
    "template": { "id": "<TEMPLATE_ID>", "strict": true, "variables": { "meetingTitle": "Quarterly planning" } }
  }'

# From your own domain (transactional send)
curl -s -X POST "$NYLAS_API_URI/v3/domains/yourdomain.com/messages/send" \
  -H "Authorization: Bearer $NYLAS_API_KEY" -H "Content-Type: application/json" \
  -d '{
    "from": { "name": "Your Company", "email": "notifications@yourdomain.com" },
    "to": [{ "name": "Nyla Hart", "email": "nyla.hart@example.com" }],
    "template": { "id": "<TEMPLATE_ID>", "variables": { "meetingTitle": "Quarterly planning" } }
  }'
```

A `subject` or `body` in the request overrides the template's.

Reference: https://developer.nylas.com/docs/reference/api/messages/send-message/
