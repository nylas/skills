# Nylas CLI Reference

Compiled reference. Official docs source: https://cli.nylas.com/docs/commands

---

## 1. Setup & Configuration

```bash
brew install nylas/nylas-cli/nylas                 # Homebrew
go install github.com/nylas/cli/cmd/nylas@latest  # Go
nylas init [--api-key K] [--region eu] [--google|--microsoft|--github]
nylas config list|get|set|reset|path          # Config management
nylas completion bash|zsh|fish|powershell     # Shell completion
nylas update                                  # Self-update
nylas doctor [--verbose]                       # Diagnose credentials, grants, secret store, connectivity, config
```

Prefer package-managed installs. If you use a hosted installer from `cli.nylas.com`, download it and inspect it before executing it instead of piping it directly into a shell.

Flags: `--config PATH`, `--format table|json|yaml`, `--json`, `--no-color`, `--quiet`, `--verbose`, `--wide`
Env: `NYLAS_API_KEY`, `NYLAS_CLIENT_ID`, `NYLAS_GRANT_ID`, `NYLAS_DISABLE_KEYRING`

## 2. Authentication

```bash
nylas auth login [--provider microsoft]
nylas auth add|config|detect|list|show|status|whoami|switch <email-or-grant-id>|logout|remove <grant-id>|revoke <grant-id>|token|scopes|providers|migrate
```

`nylas auth remove` removes a grant from local CLI config only. Use `nylas auth revoke` to revoke the grant on the Nylas server. With multiple grants, all commands run against the active/default one (`✓` in the `nylas auth list` DEFAULT column); change it with `nylas auth switch`, or override per-command with `NYLAS_GRANT_ID`. Free tier allows up to 5 grants total across any provider mix (OAuth, IMAP, agent accounts).

## 3. Email

```bash
nylas email list|read|send|search|delete
nylas email mark read|unread|starred|unstarred <id>
nylas email tracking-info <id>
nylas email smart-compose --prompt "..."
nylas email ai analyze [--unread]
nylas email metadata show <id>
nylas email attachments list|show|download | folders list|create|show|rename|delete
nylas email signatures|drafts|threads|templates|scheduled <verb>   # each is its own CRUD subgroup
```

Filters: `--unread`, `--starred`, `--from`, `--to`, `--subject`, `--has-attachment`
Email workflows: local templates (`nylas email templates ...`), hosted templates (`nylas template ...`), stored signatures, scheduled sends, and GPG-related signing/encryption flows (`nylas email send --sign/--encrypt`, `nylas email read --decrypt/--verify`) are documented in the dedicated email rules and the CLI command reference.

## 4. Calendar

```bash
nylas calendar list|show|create|update|delete            # calendars
nylas calendar events list|show|create|update|delete|rsvp
nylas calendar recurring list|update|delete
nylas calendar virtual list|show|create|delete
nylas calendar availability check
nylas calendar find-time --participants P --duration D
nylas calendar schedule ai "..."
nylas calendar ai analyze|analyze-thread|conflicts|reschedule|adapt|focus-time
nylas calendar ai conflicts check --title T --start RFC3339 --duration MIN
nylas calendar ai reschedule ai <event-id>
```

Calendar workflows: timezone conversion, DST warnings, timezone locking, working-hours validation, and break validation are covered by the dedicated calendar rule, the timezone utilities docs, and the command reference.

## 5. Contacts

```bash
nylas contacts list|show|create|update|delete|search|sync
nylas contacts groups list|show|create|update|delete
nylas contacts photo download|info <id>
```

## 6. Agent Accounts

Managed email identities for AI agents — no OAuth/SMTP/MX. One grant gives email, calendar, and contacts. Domains: free managed `*.nylas.email` or a custom domain (Dashboard); free tier includes 1 of each. Behaviour is controlled by a workspace that references a policy and rules.

```bash
nylas agent account list|get [id|email]|create <email> [--app-password '...']|update [id|email] --app-password '...'|delete <id|email> [--yes]
nylas agent policy list|get|read <id>|create [--name N | --data '{...}' | --data-file f.json]|update <id> [...]|delete <id> --yes
nylas agent rule list|get|read <id>|create --name N [--trigger inbound|outbound] [--priority] [--enabled|--disabled] [--match-operator all|any] --condition <field,op,val> --action <act>|update <id> [...]|delete <id> --yes
nylas agent status [--json]
nylas workspace list|get <id>|create --name N --domain D [--policy-id <id>] [--auto-group]|update <id> [--policy-id <id>] [--rules-ids <id1>,<id2>]|delete <id> --yes
```

An agent account is a `provider=nylas` grant; after `nylas agent account create <email>`, run `nylas auth switch <email-or-grant-id>` to make it active (create does not auto-switch), then the normal `nylas email|calendar|contacts` commands run against it. Workspaces (`nylas workspace`, alias `ws`) group accounts and attach a policy + rules. Rule condition fields: `from.domain`, `from`, `recipient.domain`, `subject`, `outbound.type` (for `in_list`: `field,in_list,id1,id2`); actions: `block`, `archive`, `mark_as_read`, `mark_as_starred`, `mark_as_spam`. Policy delete is rejected while a `provider=nylas` workspace still references it.

## 7. Webhooks

```bash
nylas webhook list|create|update|delete|triggers|rotate-secret|verify
nylas webhook test send|payload <url>
nylas webhook pubsub list|show|create|update|delete
nylas webhook server [--port 8080 --tunnel cloudflared]
```

## 8. Dashboard

```bash
nylas dashboard register|login|logout|status|refresh
nylas dashboard login --google|--microsoft|--github
nylas dashboard sso login|register --provider google|microsoft|github
nylas dashboard apps list|create|use
nylas dashboard apps apikeys list|create
nylas dashboard orgs list|switch
```

## 9. MCP & AI

```bash
nylas mcp install [--assistant claude-desktop|claude-code|cursor|windsurf|vscode] [--all]
nylas mcp status|uninstall|serve
nylas chat [--agent claude|codex|ollama] [--model M] [--port P] [--no-browser]
nylas ai config|usage|set-budget|show-budget|clear-data
```

## 10. Slack Integration

```bash
nylas slack auth set --token xoxp-...
nylas slack auth status
nylas slack auth remove
nylas slack channels list
nylas slack channels info C01234567890
nylas slack messages list --channel general
nylas slack send --channel general --text "Hello team!"
nylas slack reply --channel general --thread 1234567890.123456 --text "Reply"
nylas slack users list
nylas slack search --query "project update"
```

## 11. Notetaker (AI Meeting Bot)

```bash
nylas notetaker list
nylas notetaker create --meeting-link "https://zoom.us/j/123456789"
nylas notetaker show <notetaker-id>
nylas notetaker media <notetaker-id>
nylas notetaker delete <notetaker-id> --force
```

Aliases: `nylas nt`, `nylas bot`

`nylas notetaker list --state` currently supports `scheduled`, `connecting`, `attending`, `complete`, `cancelled`, and `failed`.

## 12. OTP Codes

```bash
nylas otp get [--raw] [--no-copy]             # Latest 2FA code from email (copies to clipboard by default)
nylas otp watch [--interval 10] [--no-copy]   # Watch for new OTP codes
nylas otp list                                # Configured accounts
nylas otp messages [--limit 10]              # Recent messages (debug)
```

## 13. Audit Logging

```bash
nylas audit init
nylas audit logs enable|disable|status|show|summary|clear
nylas audit export
nylas audit config show|set
```

## 14. Tools & Interfaces

| Command | Description |
|---------|-------------|
| `nylas tui` | Terminal UI |
| `nylas tui theme init\|list\|set-default\|validate` | TUI themes |
| `nylas ui` | Alternate UI |
| `nylas air` | Web client (localhost:7365) |
| `nylas demo <resource>` | Demo mode |
| `nylas commands [path...] [--json\|--all]` | Machine-readable command/flag metadata |
| `nylas timezone list\|convert\|dst\|find-meeting\|info` | Timezone tools (offline) |

## 15. Advanced Families

```bash
nylas admin applications|callback-uris|connectors|credentials <crud> ; nylas admin grants list|stats
nylas scheduler bookings list|show|confirm|cancel|reschedule ; nylas scheduler configurations <crud> ; nylas scheduler sessions create|show
nylas timezone ...
nylas workflow ...
nylas template ...
nylas email ... --sign/--encrypt/--decrypt/--verify
```

These command families and related email feature docs are current in the upstream CLI docs and should be checked in the command reference before answering with syntax details.
