---
title: Contacts API
section: contacts
---

## Contacts API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/contacts` | GET, POST | List/create contacts |
| `/v3/grants/{id}/contacts/{id}` | GET, PUT, DELETE | Get/update/delete contact |
| `/v3/grants/{id}/contacts/groups` | GET | List contact groups |

### Contact Sources

Use the `source` query parameter to control where contacts are fetched from:

| Source | Description |
|--------|-------------|
| `address_book` (default) | User's address book contacts |
| `domain` | Organization/domain directory contacts |
| `inbox` | Contacts extracted from inbox participants |

### Profile Pictures

Add `?profile_picture=true` to get Base64-encoded profile images in the response.

### Contact Fields

Supports: names, email addresses, phone numbers, physical addresses, instant messenger handles, web pages, profile images, company, job title, manager, office location, birthday, notes.

Reference: [Contacts docs](https://developer.nylas.com/docs/v3/email/contacts/)
