---
name: nylas-api
description: "Build email, calendar, and contacts integrations with the Nylas v3 API. Use when code imports nylas, @nylas/nylas, nylas-python, or user asks about Nylas API, email API integration, calendar API, contacts API, OAuth grants, webhooks, scheduler, notetaker, smart compose, or transactional send. DO NOT use for Nylas CLI commands."
compatibility: "Requires a Nylas API key from dashboard.nylas.com. SDKs available for Node.js (npm install nylas), Python (pip install nylas), Ruby (gem install nylas), and Kotlin/Java."
license: MIT
metadata:
  author: nylas
  version: "2.0.0"
  organization: Nylas
  date: March 2026
  abstract: Complete v3 API integration guide covering authentication, email, calendar, contacts, webhooks, scheduler, notetaker, smart compose, transactional send, admin APIs, UI components, and all provider-specific guides.
---

# Nylas v3 API Integration Guide

- **Always use v3.** The v2 API is deprecated.
- A **grant** = an authenticated user account (Gmail, Outlook, etc.) connected through Nylas.
- **Base URLs**: `https://api.us.nylas.com` (US) / `https://api.eu.nylas.com` (EU). All paths `/v3/`.
- **Auth**: Bearer token (API key) + grant ID in path.
- **SDKs**: Node.js, Python, Ruby, Kotlin/Java.

## Documentation

The docs at **https://developer.nylas.com** are the source of truth. **When the rules below don't cover what you need, use WebFetch to get current docs.** Fetch any page as markdown:

```bash
curl --location 'https://developer.nylas.com/docs/v3/email/' --header 'Accept: text/markdown'
```

- **Docs index** (find the right page): `https://developer.nylas.com/llms.txt`
- **Full docs** (everything in one file): `https://developer.nylas.com/llms-full.txt`

## Rules

Read individual rule files for endpoints, examples, and SDK code. For the full compiled reference, read `AGENTS.md`.

### Authentication (CRITICAL)

- [`rules/auth-oauth-flow.md`](rules/auth-oauth-flow.md) — Hosted OAuth, BYO auth, IMAP auth, PKCE, service accounts, Nylas Connect | [Docs](https://developer.nylas.com/docs/v3/auth/)
- [`rules/auth-providers.md`](rules/auth-providers.md) — Google, Microsoft, Yahoo, iCloud, IMAP, Exchange, Zoom setup | [Docs](https://developer.nylas.com/docs/provider-guides/)

### Email API (HIGH)

- [`rules/email-messages.md`](rules/email-messages.md) — Messages, threads, drafts, folders, attachments, search, filters | [Docs](https://developer.nylas.com/docs/v3/email/)
- [`rules/email-advanced.md`](rules/email-advanced.md) — Tracking, smart compose, templates, workflows, scheduled/transactional send | [Docs](https://developer.nylas.com/docs/v3/email/message-tracking/)

### Calendar API (HIGH)

- [`rules/calendar-events.md`](rules/calendar-events.md) — Events, availability, free/busy, recurring, virtual calendars, conferencing, group booking | [Docs](https://developer.nylas.com/docs/v3/calendar/)

### Contacts API (MEDIUM)

- [`rules/contacts-crud.md`](rules/contacts-crud.md) — CRUD, groups, sources (address_book/domain/inbox), profile pictures | [Docs](https://developer.nylas.com/docs/v3/email/contacts/)

### Webhooks & Notifications (HIGH)

- [`rules/webhooks-notifications.md`](rules/webhooks-notifications.md) — Webhooks, Pub/Sub, triggers, schemas, verification, retry behavior | [Docs](https://developer.nylas.com/docs/v3/notifications/)

### Scheduler API (MEDIUM)

- [`rules/scheduler-booking.md`](rules/scheduler-booking.md) — Configurations, bookings, hosted pages, meeting types, UI components | [Docs](https://developer.nylas.com/docs/v3/scheduler/)

### Notetaker API (MEDIUM)

- [`rules/notetaker-meetings.md`](rules/notetaker-meetings.md) — Recording, transcription, AI summaries, calendar sync, media (MP4/JSON/TXT) | [Docs](https://developer.nylas.com/docs/v3/notetaker/)

### Admin & Grants (MEDIUM)

- [`rules/admin-grants.md`](rules/admin-grants.md) — Grants, connectors, credentials, API keys, domains, workspaces | [Docs](https://developer.nylas.com/docs/api/v3/admin/)

### SDKs (HIGH)

- [`rules/sdk-quickstart.md`](rules/sdk-quickstart.md) — Node.js, Python, Ruby, Kotlin/Java quick starts | [Docs](https://developer.nylas.com/docs/v3/sdks/)

### Best Practices (HIGH)

- [`rules/best-practices-patterns.md`](rules/best-practices-patterns.md) — Rate limits (with numbers), error codes (200/400/500/700), pagination, metadata, field selection | [Docs](https://developer.nylas.com/docs/dev-guide/best-practices/) | [Errors](https://developer.nylas.com/docs/api/errors/)
