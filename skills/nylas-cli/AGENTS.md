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
```

Prefer package-managed installs. If you use a hosted installer from `cli.nylas.com`, download it and inspect it before executing it instead of piping it directly into a shell.

Flags: `--config PATH`, `--format table|json|yaml`, `--json`, `--no-color`, `--quiet`, `--verbose`, `--wide`
Env: `NYLAS_API_KEY`, `NYLAS_CLIENT_ID`, `NYLAS_GRANT_ID`, `NYLAS_DISABLE_KEYRING`

## 2. Authentication

```bash
nylas auth login [--provider microsoft]
nylas auth add|config|detect|list|show|status|whoami|switch <email>|logout|remove <grant-id>|revoke <grant-id>|token|scopes|providers|migrate
```

`nylas auth remove` removes a grant from local CLI config only. Use `nylas auth revoke` to revoke the grant on the Nylas server.

## 3. Email

```bash
nylas email list|read|send|search|delete|mark
nylas email smart-compose --prompt "..."
nylas email ai analyze [--unread]
nylas email metadata show <id>
nylas email attachments|folders|threads|drafts|templates|scheduled list
```

Filters: `--unread`, `--starred`, `--from`, `--to`, `--subject`, `--has-attachment`
Email workflows: local templates (`nylas email templates ...`), hosted templates (`nylas template ...`), stored signatures, scheduled sends, and GPG-related signing/encryption flows (`nylas email send --sign/--encrypt`, `nylas email read --decrypt/--verify`) are documented in the dedicated email rules and the CLI command reference.

## 4. Calendar

```bash
nylas calendar list
nylas calendar events list|show|create|update|delete|rsvp
nylas calendar availability check
nylas calendar find-time --participants P --duration D
nylas calendar schedule ai "..."
nylas calendar ai analyze
nylas calendar ai conflicts check --title T --start RFC3339 --duration MIN
nylas calendar ai reschedule ai <event-id>
```

Calendar workflows: timezone conversion, DST warnings, timezone locking, working-hours validation, and break validation are covered by the dedicated calendar rule, the timezone utilities docs, and the command reference.

## 5. Contacts

```bash
nylas contacts list|show|create|search|sync
nylas contacts groups list
```

## 6. Webhooks

```bash
nylas webhook list|create|update|delete|triggers
nylas webhook test send <url>
nylas webhook server [--port 8080 --tunnel cloudflared]
```

## 7. Inbound Email

```bash
nylas inbound list|create|messages|monitor
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
nylas ai config
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

## 12. Audit Logging

```bash
nylas audit init
nylas audit logs enable|disable|status|show|summary|clear
nylas audit export
nylas audit config show|set
```

## 13. Tools & Interfaces

| Command | Description |
|---------|-------------|
| `nylas tui` | Terminal UI |
| `nylas ui` | Alternate UI |
| `nylas air` | Web client (localhost:7365) |
| `nylas demo <resource>` | Demo mode |
| `nylas timezone list\|convert\|dst\|find-meeting\|info` | Timezone tools (offline) |

## 14. Advanced Families

```bash
nylas admin ...
nylas scheduler ...
nylas timezone ...
nylas agent ...
nylas workflow ...
nylas template ...
nylas email ... --sign/--encrypt/--decrypt/--verify
```

These command families and related email feature docs are current in the upstream CLI docs and should be checked in the command reference before answering with syntax details.
