# Nylas CLI Reference

Compiled reference. Official docs source: https://cli.nylas.com/docs/commands

---

## 1. Setup & Configuration

```bash
brew install nylas/nylas-cli/nylas            # Install
nylas init [--api-key K] [--region eu] [--google|--microsoft|--github]
nylas config list|get|set|reset|path          # Config management
nylas completion bash|zsh|fish|powershell     # Shell completion
nylas update                                  # Self-update
```

Flags: `--json`, `--no-color`, `--verbose`, `--limit N`, `--yes`, `--config PATH`
Env: `NYLAS_API_KEY`, `NYLAS_CLIENT_ID`, `NYLAS_GRANT_ID`, `NYLAS_DISABLE_KEYRING`

## 2. Authentication

```bash
nylas auth login [--provider microsoft]
nylas auth config|list|show|status|whoami|switch|logout|remove|token|scopes|providers|migrate
```

## 3. Email

```bash
nylas email list|read|send|search|delete|mark
nylas email smart-compose --prompt "..."
nylas email ai analyze [--unread]
nylas email metadata show <id>
nylas email attachments|folders|threads|drafts|templates|scheduled list
```

Filters: `--unread`, `--starred`, `--from`, `--to`, `--subject`, `--has-attachment`

## 4. Calendar

```bash
nylas calendar list
nylas calendar events list|show|create|update|delete|rsvp
nylas calendar availability check
nylas calendar find-time --participants P --duration D
nylas calendar schedule ai "..."
nylas calendar analyze
nylas calendar ai conflicts|reschedule
```

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
nylas dashboard register|login|sso|logout|status|refresh
nylas dashboard login --google|--microsoft|--github
nylas dashboard apps list|create|use
nylas dashboard apps apikeys list|create
nylas dashboard orgs list|switch
```

## 9. MCP & AI

```bash
nylas mcp install [--assistant claude-code|cursor] [--all]
nylas mcp status|uninstall|serve
nylas chat [--agent claude|codex|ollama] [--model M] [--port P] [--no-browser]
nylas ai config
```

## 10. Audit Logging

```bash
nylas audit init
nylas audit logs enable|disable|status|show|summary|clear
nylas audit export
nylas audit config show|set
```

## 11. Tools & Interfaces

| Command | Description |
|---------|-------------|
| `nylas tui` | Terminal UI |
| `nylas ui` | Alternate UI |
| `nylas air` | Web client (localhost:7365) |
| `nylas demo <resource>` | Demo mode |
| `nylas timezone list\|convert\|dst\|find-meeting\|info` | Timezone tools (offline) |
