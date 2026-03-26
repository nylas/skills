---
name: nylas-cli
description: "Use the Nylas CLI to manage email, calendar, and contacts from the terminal. Use when user asks about Nylas CLI commands, nylas init, nylas email, nylas calendar, nylas contacts, nylas auth, nylas mcp, nylas chat, nylas tui, nylas air, nylas audit, or terminal-based email/calendar management. DO NOT use for Nylas API SDK integration."
compatibility: "Requires the Nylas CLI installed via Homebrew (brew install nylas/nylas-cli/nylas) or Go (go install github.com/nylas/cli/cmd/nylas@latest)"
license: MIT
metadata:
  author: nylas
  version: "2.0.0"
  organization: Nylas
  date: March 2026
  abstract: Complete CLI reference covering email, calendar, contacts, webhooks, inbound email, dashboard, MCP, AI chat, audit logging, and all tools/interfaces.
---

# Nylas CLI Reference

Email, calendar, and contacts from your terminal. One CLI for Google, Microsoft, and IMAP.

## Documentation

Full CLI docs at **https://cli.nylas.com/docs/commands**. **When the rules below don't cover what you need, use WebFetch on that URL to get the complete command reference.**

## Rules

Read individual rule files for command references. For the full compiled reference, read `AGENTS.md`.

### Setup & Configuration (CRITICAL)

- [`rules/setup-install.md`](rules/setup-install.md) — Installation, init (with SSO shortcuts), global flags, config management, env vars, shell completion, self-update

### Authentication (CRITICAL)

- [`rules/auth-commands.md`](rules/auth-commands.md) — Login, whoami, list, show, switch, logout, remove, token, scopes, providers, migrate

### Email (HIGH)

- [`rules/email-commands.md`](rules/email-commands.md) — Read, send, search, mark, smart-compose, AI analyze, metadata, attachments, folders, threads, drafts, templates, scheduled

### Calendar (HIGH)

- [`rules/calendar-commands.md`](rules/calendar-commands.md) — Events CRUD, RSVP, availability, find-time, AI scheduling/analyze/conflicts/reschedule

### Contacts (MEDIUM)

- [`rules/contacts-commands.md`](rules/contacts-commands.md) — CRUD, search, sync, groups

### Webhooks (HIGH)

- [`rules/webhooks-commands.md`](rules/webhooks-commands.md) — CRUD, triggers, test events, local webhook server

### Inbound Email (MEDIUM)

- [`rules/inbound-email.md`](rules/inbound-email.md) — Managed inbound addresses without OAuth, real-time monitoring

### Dashboard (MEDIUM)

- [`rules/dashboard-commands.md`](rules/dashboard-commands.md) — Account (register/login/SSO/logout), apps, API keys, organizations

### MCP & AI (HIGH)

- [`rules/mcp-ai-commands.md`](rules/mcp-ai-commands.md) — MCP install/status/serve for Claude Code/Cursor/all, AI chat with multiple agents (claude/codex/ollama), AI config

### Audit Logging (MEDIUM)

- [`rules/audit-commands.md`](rules/audit-commands.md) — Init, enable/disable, view logs/summary, export, config

### Tools & Interfaces (LOW)

- [`rules/tools-interfaces.md`](rules/tools-interfaces.md) — TUI, UI, Air web client, demo mode, timezone utilities
