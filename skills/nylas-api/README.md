# nylas-api

Build email, calendar, and contacts integrations with the Nylas v3 API.

## What this skill covers

- **Authentication** — Hosted OAuth, BYO auth, IMAP, PKCE, service accounts, Nylas Connect
- **Email** — Messages, threads, drafts, folders, attachments, tracking, smart compose, templates, transactional send
- **Calendar** — Events, availability, free/busy, recurring, conferencing, group booking
- **Contacts** — CRUD, groups, sources, profile pictures
- **Webhooks** — Webhooks, Pub/Sub, triggers, verification, retries
- **Scheduler** — Configurations, bookings, hosted pages, 70+ UI components
- **Notetaker** — Recording, transcription, AI summaries, media
- **Admin** — Grants, connectors, API keys, domains, workspaces
- **SDKs** — Node.js, Python, Ruby, Kotlin/Java

## Structure

```
SKILL.md          # Concise rules index with doc links (loaded on activation)
CLAUDE.md         # Claude Code auto-loaded context
AGENTS.md         # Full compiled reference
metadata.json     # Skill metadata for marketplace
rules/            # Individual rule files (read on demand)
  _sections.md    # Rule ordering and priorities
  _template.md    # Template for new rules
```

## Docs source

- **Index**: https://developer.nylas.com/llms.txt
- **Full**: https://developer.nylas.com/llms-full.txt
- **Fetch any page**: `curl --location 'https://developer.nylas.com/docs/v3/<topic>/' --header 'Accept: text/markdown'`

## Contributing

See [CONTRIBUTING.md](../../CONTRIBUTING.md) for how to add or update rules.
