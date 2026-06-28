# Nylas CLI Skill

- Install: `brew install nylas/nylas-cli/nylas` or `go install github.com/nylas/cli/cmd/nylas@latest`. If using a hosted installer from `cli.nylas.com`, download and inspect it before execution rather than piping it directly into a shell.
- First run: `nylas init` | SSO: `nylas init --google|--microsoft|--github`
- Global flags: `--config PATH`, `--format table|json|yaml`, `--json`, `--no-color`, `--quiet`, `--verbose`, `--wide`
- Config: `~/.config/nylas/config.yaml` | Manage: `nylas config list|get|set|reset`
- **Official docs source**: https://cli.nylas.com/docs/commands

## Rules

| File | Topic |
|------|-------|
| `rules/setup-install.md` | Install, init, config, env vars, completion, update, `nylas doctor` |
| `rules/auth-commands.md` | Login, whoami, switch, token, scopes, migrate |
| `rules/email-commands.md` | Read, send, search, smart-compose, AI, metadata |
| `rules/calendar-commands.md` | Events, RSVP, availability, AI scheduling |
| `rules/contacts-commands.md` | CRUD, search, sync, groups |
| `rules/agent-commands.md` | Agent accounts: `nylas agent account|policy|rule|status` + `nylas workspace` |
| `rules/webhooks-commands.md` | CRUD, triggers, test, local server |
| `rules/dashboard-commands.md` | Account, apps, API keys, orgs |
| `rules/mcp-ai-commands.md` | MCP install/serve, AI config (usage/budget) |
| `rules/notetaker-commands.md` | `nylas notetaker list|create|show|media|leave|delete` |
| `rules/otp-commands.md` | `nylas otp get|watch|list|messages` (2FA codes from email) |
| `rules/audit-commands.md` | Audit logging, export |
| `rules/tools-interfaces.md` | TUI, UI, Air, demo, `nylas commands`, timezones |
| `rules/advanced-commands.md` | Admin, scheduler, timezone, workflows, hosted templates, and GPG-related email feature docs |
