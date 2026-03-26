# nylas-cli

Manage email, calendar, and contacts from the terminal with the Nylas CLI.

## What this skill covers

- **Setup** — Install (brew/go), init with SSO, global flags, config management
- **Authentication** — Login, whoami, switch, token, scopes, migrate
- **Email** — Read, send, search, smart-compose, AI analyze, metadata
- **Calendar** — Events CRUD, RSVP, availability, AI scheduling
- **Contacts** — CRUD, search, sync, groups
- **Webhooks** — CRUD, triggers, test events, local server
- **Inbound Email** — Managed inbound addresses, real-time monitoring
- **Dashboard** — Account, apps, API keys, organizations
- **MCP & AI** — MCP install for Claude Code/Cursor, AI chat (claude/codex/ollama)
- **Audit** — Logging, export, config
- **Tools** — TUI, UI, Air web client, demo mode, timezones

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

- **Full reference**: https://cli.nylas.com/docs/commands

## Contributing

See [CONTRIBUTING.md](../../CONTRIBUTING.md) for how to add or update rules.
