# Nylas Skills

[Agent Skills](https://skills.sh) for building with the Nylas platform. Works with Claude Code, Cursor, Codex CLI, and 40+ other AI coding agents.

## Available Skills

### nylas-api

Build email, calendar, and contacts integrations with the Nylas v3 API.

**Use when:** code imports `nylas`/`@nylas/nylas`/`nylas-python`, or user asks about Nylas API, OAuth, webhooks, scheduler, notetaker, smart compose, transactional send.

**Covers:** Authentication (6 methods), Email (messages/threads/drafts/tracking/smart compose/templates/transactional), Calendar (events/availability/recurring/conferencing), Contacts, Webhooks & Pub/Sub, Scheduler (70+ UI components), Notetaker (recording/transcription/AI summaries), Admin (grants/connectors/API keys/domains), SDKs (Node.js/Python/Ruby/Kotlin), Best Practices (rate limits, error codes).

**Docs source:** [developer.nylas.com](https://developer.nylas.com) — skills link to fetchable doc pages and teach agents to use `llms.txt` for always-current details.

### nylas-cli

Manage email, calendar, and contacts from the terminal with the Nylas CLI.

**Use when:** user mentions `nylas init`, `nylas email`, `nylas calendar`, `nylas auth`, `nylas mcp`, `nylas chat`, `nylas tui`, `nylas audit`.

**Covers:** Setup & config, authentication, email (read/send/search/AI), calendar (events/RSVP/AI scheduling), contacts, webhooks, inbound email, dashboard management, MCP install (Claude Code/Cursor), AI chat (claude/codex/ollama), audit logging, TUI/Air/demo mode.

**Docs source:** [cli.nylas.com/docs/commands](https://cli.nylas.com/docs/commands)

## Install

### Skills CLI

```bash
# Install all Nylas skills
npx skills add nylas/skills

# Or install individually
npx skills add nylas/skills/nylas-api
npx skills add nylas/skills/nylas-cli
```

### Claude Code Plugin

```bash
/plugin marketplace add nylas/skills
```

## Test Locally

```bash
# Install from local path into a test project
cd /path/to/your/project
npx skills add /path/to/this/repo --agent claude-code --copy --all

# Or install globally
npx skills add /path/to/this/repo -g --agent claude-code --copy --all
```

Then open a new Claude Code session — skills will be available as `nylas-api` and `nylas-cli`.

## Skill Structure

```
skills/{skill-name}/
  SKILL.md       # Concise rules index with doc links
  AGENTS.md      # Full compiled reference
  CLAUDE.md      # Claude Code auto-loaded context
  README.md      # Contributor guide
  LICENSE.txt    # MIT license
  rules/         # Individual rule files (read on demand)
```

## Links

- [Nylas API Docs](https://developer.nylas.com)
- [Nylas CLI Docs](https://cli.nylas.com/docs/commands)
- [skills.sh](https://skills.sh)
- [Agent Skills Spec](https://agentskills.io)

## License

MIT
