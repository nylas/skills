# Nylas CLI Skill

- Install: `brew install nylas/nylas-cli/nylas` or `go install github.com/nylas/cli/cmd/nylas@latest`
- First run: `nylas init` | SSO: `nylas init --google|--microsoft|--github`
- Global flags: `--json`, `--verbose`, `--limit N`, `--yes`, `--config PATH`
- Config: `~/.config/nylas/config.yaml` | Manage: `nylas config list|get|set|reset`
- **Official docs source**: https://cli.nylas.com/docs/commands

## Rules

| File | Topic |
|------|-------|
| `rules/setup-install.md` | Install, init, config, env vars, completion, update |
| `rules/auth-commands.md` | Login, whoami, switch, token, scopes, migrate |
| `rules/email-commands.md` | Read, send, search, smart-compose, AI, metadata |
| `rules/calendar-commands.md` | Events, RSVP, availability, AI scheduling |
| `rules/contacts-commands.md` | CRUD, search, sync, groups |
| `rules/webhooks-commands.md` | CRUD, triggers, test, local server |
| `rules/inbound-email.md` | Managed inbound addresses |
| `rules/dashboard-commands.md` | Account, apps, API keys, orgs |
| `rules/mcp-ai-commands.md` | MCP install/serve, AI chat (claude/codex/ollama) |
| `rules/slack-commands.md` | `nylas slack auth|channels|messages|send|reply|users|search` |
| `rules/notetaker-commands.md` | `nylas notetaker list|create|show|media|delete` |
| `rules/audit-commands.md` | Audit logging, export |
| `rules/tools-interfaces.md` | TUI, UI, Air, demo, timezones |
| `rules/advanced-commands.md` | Admin, scheduler, timezone, agent, workflows, hosted templates, and GPG-related email feature docs |
