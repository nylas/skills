# nylas-cli

Manage email, calendar, contacts, Slack, and Notetaker from the terminal with the Nylas CLI.

## What this skill covers

- **Setup** — Install (Homebrew or Go, with hosted installers as inspect-before-run alternatives), init with SSO, global flags, config management
- **Authentication** — Login, whoami, switch, add/remove/revoke grants, token, scopes, migrate
- **Email** — Read, send, search, smart-compose, AI analyze, metadata, templates, GPG-related signing/encryption flows, scheduled mail
- **Calendar** — Events CRUD, RSVP, availability, AI scheduling, timezone tools, DST handling, timezone locking, working-hours and break validation
- **Contacts** — CRUD, search, sync, groups
- **Webhooks** — CRUD, triggers, test events, local server
- **Slack** — Workspace auth, channels, messages, send/reply, users, search
- **Notetaker** — AI meeting bot list/create/show/media/delete
- **Inbound Email** — Managed inbound addresses, real-time monitoring
- **Dashboard** — Account, apps, API keys, organizations
- **MCP & AI** — MCP install for Claude Desktop, Claude Code, Cursor, Windsurf, or VS Code; AI chat (claude/codex/ollama)
- **Audit** — Logging, export, config
- **Tools** — TUI, UI, Air web client, demo mode, timezones
- **Advanced Families** — Admin, scheduler, timezone, agent, workflows, hosted templates, and GPG-related email feature docs

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
