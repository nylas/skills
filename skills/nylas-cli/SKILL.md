---
name: nylas-cli
description: "Use the Nylas CLI to manage email, calendar, contacts, and Notetaker from the terminal. Use when user asks about Nylas CLI commands, nylas init, nylas email, nylas calendar, nylas contacts, nylas auth, nylas agent, agent accounts, nylas mcp, nylas notetaker, nylas otp, nylas tui, nylas air, nylas audit, nylas doctor, or terminal-based email/calendar management. DO NOT use for Nylas API SDK integration."
compatibility: "Requires the Nylas CLI installed via Homebrew or Go. Hosted installers from cli.nylas.com are optional, but should be downloaded and inspected before execution."
license: MIT
metadata:
  author: nylas
  version: "3.0.0"
  organization: Nylas
  date: June 2026
  abstract: CLI reference covering setup, auth, email, calendar, contacts, webhooks, agent accounts, timezone utilities, dashboard, MCP, Notetaker, OTP codes, audit logging, diagnostics, tools/interfaces, and advanced command families and workflows.
---

# Nylas CLI Reference

Email, calendar, contacts, and Notetaker from your terminal. One CLI for Google, Microsoft, IMAP, and meeting-bot workflows.

## Documentation

Official CLI docs source: **https://cli.nylas.com/docs/commands**.
Use the bundled rule files below and `AGENTS.md` as the working reference for agent actions.

## Rules

Read individual rule files for command references. For the full compiled reference, read `AGENTS.md`.

### Setup & Configuration (CRITICAL)

- [`rules/setup-install.md`](rules/setup-install.md) — Installation, init (with SSO shortcuts), global flags, config management, env vars, shell completion, self-update, `nylas doctor` diagnostics

### Authentication (CRITICAL)

- [`rules/auth-commands.md`](rules/auth-commands.md) — Login, whoami, list, show, switch, logout, add/remove/revoke grants, token, scopes, providers, detect, migrate

### Email (HIGH)

- [`rules/email-commands.md`](rules/email-commands.md) — Read, send, search, mark, smart-compose, AI analyze, metadata, attachments, folders, threads, drafts, templates, scheduled

### Calendar (HIGH)

- [`rules/calendar-commands.md`](rules/calendar-commands.md) — Events CRUD, RSVP, availability, find-time, AI scheduling/analyze/conflicts/reschedule

### Contacts (MEDIUM)

- [`rules/contacts-commands.md`](rules/contacts-commands.md) — CRUD, search, sync, groups

### Agent Accounts (HIGH)

- [`rules/agent-commands.md`](rules/agent-commands.md) — Managed email identities for AI agents: `nylas agent account|policy|rule|status` and `nylas workspace` (groups accounts, attaches policies + condition/action rules)

### Webhooks (HIGH)

- [`rules/webhooks-commands.md`](rules/webhooks-commands.md) — CRUD, triggers, test events, local webhook server

### Dashboard (MEDIUM)

- [`rules/dashboard-commands.md`](rules/dashboard-commands.md) — Account (register/login/SSO/logout), apps, API keys, organizations

### MCP & AI (HIGH)

- [`rules/mcp-ai-commands.md`](rules/mcp-ai-commands.md) — MCP install/status/serve for Claude Desktop, Claude Code, Cursor, Windsurf, VS Code, or all assistants; AI config (usage/budget)

### Notetaker (MEDIUM)

- [`rules/notetaker-commands.md`](rules/notetaker-commands.md) — AI meeting bot list/create/show/media/delete workflows

### OTP Codes (MEDIUM)

- [`rules/otp-commands.md`](rules/otp-commands.md) — Retrieve/watch 2FA one-time-password codes from email: `nylas otp get|watch|list|messages`

### Audit Logging (MEDIUM)

- [`rules/audit-commands.md`](rules/audit-commands.md) — Init, enable/disable, view logs/summary, export, config

### Tools & Interfaces (LOW)

- [`rules/tools-interfaces.md`](rules/tools-interfaces.md) — TUI, UI, Air web client, demo mode, `nylas commands` metadata, timezone utilities

### Advanced Families (LOW)

- [`rules/advanced-commands.md`](rules/advanced-commands.md) — Admin, scheduler, timezone, workflows, hosted templates, and GPG-related email feature docs
