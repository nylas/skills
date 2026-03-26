# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, Cursor, Copilot, etc.) when working with the Nylas platform.

## Repository Overview

Skills for building with the Nylas platform — email, calendar, and contacts APIs. Skills follow the [Agent Skills](https://agentskills.io/) format.

## Available Skills

### nylas-api

Build email, calendar, and contacts integrations with the Nylas v3 API.

**Use when:** code imports `nylas`/`@nylas/nylas`/`nylas-python`, or user asks about Nylas API, OAuth grants, webhooks, scheduler, notetaker, smart compose, transactional send.

**Covers:** Authentication (6 methods), Email (messages/threads/drafts/tracking/smart compose/templates), Calendar (events/availability/recurring/conferencing), Contacts, Webhooks & Pub/Sub, Scheduler (70+ UI components), Notetaker (recording/transcription/AI summaries), Admin (grants/connectors/API keys/domains), SDKs (Node.js/Python/Ruby/Kotlin), Best Practices (rate limits with numbers, error codes).

### nylas-cli

Manage email, calendar, and contacts from the terminal with the Nylas CLI.

**Use when:** user mentions `nylas init`, `nylas email`, `nylas calendar`, `nylas auth`, `nylas mcp`, `nylas tui`, `nylas air`.

**Covers:** Setup & config, authentication, email (read/send/search/AI), calendar (events/RSVP/AI scheduling), contacts, webhooks, inbound email, dashboard management, TUI/Air/MCP/demo mode.

## Key Context

- **v3 only.** v2 is deprecated.
- **Base URLs**: `api.us.nylas.com` (US) / `api.eu.nylas.com` (EU)
- A **grant** = authenticated user account connected through Nylas.
- **Docs**: `https://developer.nylas.com/llms.txt`

## Skill Structure

Each skill contains:
- `SKILL.md` — Concise rules index with doc links (loaded on activation)
- `AGENTS.md` — Full compiled reference
- `CLAUDE.md` — Claude Code auto-loaded context
- `rules/` — Individual rule files, read on demand

### Context Efficiency

- `SKILL.md` is the index (<100 lines) — not the content dump
- Rules are individual files — agents read only what's relevant
- Doc links point to `developer.nylas.com/docs/...` for always-current details
