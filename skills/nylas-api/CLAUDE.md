# Nylas API Skill

- v3 only. v2 is deprecated. Base URLs: `api.us.nylas.com` / `api.eu.nylas.com`
- Auth: Bearer token (API key) + grant ID in path
- **When rules don't cover it, fetch docs**: `curl --location 'https://developer.nylas.com/docs/v3/<topic>/' --header 'Accept: text/markdown'`
- **Find the right page**: `https://developer.nylas.com/llms.txt`

## Rules

| File | Topic |
|------|-------|
| `rules/auth-oauth-flow.md` | OAuth, BYO, IMAP, PKCE, service accounts, Nylas Connect |
| `rules/auth-providers.md` | Google, Microsoft, Yahoo, iCloud, IMAP, Exchange, Zoom |
| `rules/email-messages.md` | Messages, threads, drafts, folders, attachments, search |
| `rules/email-advanced.md` | Tracking, smart compose, templates, scheduled/transactional send |
| `rules/calendar-events.md` | Events, availability, recurring, conferencing, group booking |
| `rules/contacts-crud.md` | CRUD, groups, sources, profile pictures |
| `rules/webhooks-notifications.md` | Webhooks, Pub/Sub, triggers, verification, retries |
| `rules/scheduler-booking.md` | Configurations, bookings, UI components, meeting types |
| `rules/notetaker-meetings.md` | Recording, transcription, AI summaries, media |
| `rules/admin-grants.md` | Grants, connectors, API keys, domains, workspaces |
| `rules/sdk-quickstart.md` | Node.js, Python, Ruby, Kotlin/Java |
| `rules/best-practices-patterns.md` | Rate limits, error codes, pagination, metadata |
