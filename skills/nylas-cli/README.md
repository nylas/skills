# nylas-cli

Manage email, calendar, contacts, and Notetaker from the terminal with the Nylas CLI.

## What this skill covers

- **Setup** — Install (Homebrew or Go, with hosted installers as inspect-before-run alternatives), init with SSO, global flags, config management, `nylas doctor` diagnostics
- **Authentication** — Login, whoami, switch, add/remove/revoke grants, token, scopes, migrate
- **Email** — Read, send, search, smart-compose, AI analyze, metadata, templates, GPG-related signing/encryption flows, scheduled mail
- **Calendar** — Events CRUD, RSVP, availability, AI scheduling, timezone tools, DST handling, timezone locking, working-hours and break validation
- **Contacts** — CRUD, search, sync, groups
- **Agent Accounts** — Managed email identities for AI agents: `nylas agent account|policy|rule|status` and `nylas workspace` (groups accounts, attaches policies + condition/action rules)
- **Webhooks** — CRUD, triggers, test events, local server
- **Notetaker** — AI meeting bot list/create/show/media/leave/delete
- **OTP Codes** — Retrieve and watch 2FA one-time-password codes from email
- **Dashboard** — Account, apps, API keys, organizations
- **MCP & AI** — MCP install for Claude Desktop, Claude Code, Cursor, Windsurf, or VS Code; AI config (usage/budget)
- **Audit** — Logging, export, config
- **Tools** — TUI, UI, Air web client, demo mode, `nylas commands` metadata, timezones
- **Advanced Families** — Admin, scheduler, timezone, workflows, hosted templates, and GPG-related email feature docs

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
