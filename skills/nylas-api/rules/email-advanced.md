---
title: Email Advanced Features
section: email
---

## Email Advanced Features

### Message Tracking

Track opens and link clicks on sent emails.

| Feature | Doc Link |
|---------|----------|
| Open & click tracking | https://developer.nylas.com/docs/v3/email/message-tracking/ |
| Webhook triggers | `message.opened`, `message.link_clicked` |

### Smart Compose

AI-powered email composition and reply suggestions.

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/messages/smart-compose` | POST | Generate email draft |
| `/v3/grants/{id}/messages/{message_id}/smart-compose` | POST | Generate a reply to a specific message |

Reference: https://developer.nylas.com/docs/v3/email/smart-compose/

### Templates & Workflows

Reusable email templates at app-level and grant-level, plus automated workflows.

| Endpoint | Purpose |
|----------|---------|
| `/v3/grants/{id}/templates` | Grant-level templates |
| `/v3/templates` | App-level templates |
| `/v3/grants/{id}/workflows` | Grant-level workflows |
| `/v3/workflows` | App-level workflows |

Reference: https://developer.nylas.com/docs/v3/email/templates-workflows/

### Scheduled Send

Schedule emails to be sent at a future time.

| Endpoint | Purpose |
|----------|---------|
| `/v3/grants/{id}/messages/schedules` | List scheduled messages |
| `/v3/grants/{id}/messages/schedules/{id}` | Get/delete scheduled message |

Reference: https://developer.nylas.com/docs/v3/email/scheduled-send/

### Transactional Send

Send emails without a grant using verified domains. No OAuth required.

| Endpoint | Purpose |
|----------|---------|
| `/v3/domains/{domain_name}/messages/send` | Send transactional email |

Reference: https://developer.nylas.com/docs/v3/getting-started/transactional-send/

### Other Email Features

| Feature | Doc Link |
|---------|----------|
| Domain warming | https://developer.nylas.com/docs/v3/email/domain-warming/ |
| Domains & verification | https://developer.nylas.com/docs/v3/email/domains/ |
| Headers & MIME data | https://developer.nylas.com/docs/v3/email/headers-mime-data/ |
| Parse messages | https://developer.nylas.com/docs/v3/email/parse-messages/ |
| Sending errors | https://developer.nylas.com/docs/v3/email/sending-errors/ |
| Attachments | https://developer.nylas.com/docs/v3/email/attachments/ |
