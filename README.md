<div align="center">
  <a href="https://www.nylas.com/">
    <img width="100%" alt="Nylas" src="https://github.com/user-attachments/assets/137517ae-244d-47a5-8ca7-b12984971fc4" />
  </a>

  <h1>Nylas Skills</h1>

  <p>
    <strong>Agent Skills for building with Nylas — the infrastructure that powers communications</strong>
  </p>

  <p>
    <a href="https://developer.nylas.com/">📖 Docs</a> ·
    <a href="https://developer.nylas.com/docs/api/v3/">📚 API Reference</a> ·
    <a href="https://dashboard-v3.nylas.com/register">🚀 Sign up</a> ·
    <a href="https://github.com/orgs/nylas-samples/repositories">💡 Samples</a> ·
    <a href="https://forums.nylas.com">💬 Forum</a>
  </p>
</div>

<br />

[Agent Skills](https://skills.sh) for building with the Nylas platform. Works with Claude Code, Cursor, Codex CLI, and 40+ other AI coding agents. Built on [Nylas](https://developer.nylas.com/), the infrastructure that powers communications — integrate with Gmail, Microsoft, IMAP, Zoom, and 250+ providers in 5 minutes, or give your AI agent its own mailbox. Covers [Agent Accounts](https://developer.nylas.com/docs/v3/agent-accounts/), [Email](https://developer.nylas.com/docs/v3/email/), [Calendar](https://developer.nylas.com/docs/v3/calendar/), [Contacts](https://developer.nylas.com/docs/v3/email/contacts/), [Scheduler](https://developer.nylas.com/docs/v3/scheduler/), and [Notetaker](https://developer.nylas.com/docs/v3/notetaker/).

## Available Skills

### nylas-api

Build email, calendar, and contacts integrations with the Nylas v3 API.

**Use when:** code imports `nylas`/`@nylas/nylas`/`nylas-python`, or user asks about Nylas API, OAuth, agent accounts, webhooks, scheduler, notetaker, smart compose, transactional send.

**Covers:** Authentication (6 methods), Security & Prompt Safety (grant-scoped API data), Email (messages/threads/drafts/tracking/smart compose/templates/transactional), Calendar (events/availability/recurring/conferencing), Contacts, Agent Accounts (workspaces/policies/rules/deliverability), Webhooks & Pub/Sub & SNS, Scheduler (70+ UI components), Notetaker (meeting bot setup/AI notes), Admin (grants/connectors/API keys/domains), SDKs (Node.js/Python/Ruby/Kotlin), Best Practices (rate limits, error codes).

**Docs source:** [developer.nylas.com](https://developer.nylas.com) — skills keep checked-in rules as the working source and use external docs links as reference URLs only.

### nylas-cli

Manage email, calendar, and contacts from the terminal with the Nylas CLI.

**Use when:** user mentions `nylas init`, `nylas email`, `nylas calendar`, `nylas auth`, `nylas mcp`, `nylas agent`, `nylas tui`, `nylas audit`.

**Covers:** Setup & config, authentication, email (read/send/search/AI), calendar (events/RSVP/AI scheduling), contacts, agent accounts, webhooks, inbound email, dashboard management, MCP install (Claude Desktop/Code, Cursor, Windsurf, VS Code), AI config, audit logging, TUI/Air/demo mode.

**Docs source:** [cli.nylas.com/docs/commands](https://cli.nylas.com/docs/commands)

### nylas-hol-guard

Add a local HOL Guard safety boundary before a supported coding-agent harness performs state-changing Nylas workflows. Installs and invokes HOL Guard while keeping Nylas grants, scopes, policies, confirmations, and API validation authoritative.

**Use when:** an agent will send/reply to email, mutate calendar/contact/webhook state, manage Agent Accounts, or change Nylas administrative state from a supported local harness.

## Give your agent its own mailbox

These skills work with any Nylas grant — including [**Agent Accounts**](https://developer.nylas.com/docs/v3/agent-accounts/), Nylas-hosted email and calendar mailboxes you provision on your own domain and drive entirely through the API. Give an AI agent an `agent@yourdomain.com` identity that can send, receive, and RSVP without connecting a human's account.

- [Quickstart: Agent Accounts](https://developer.nylas.com/docs/v3/getting-started/agent-accounts/) — create your first mailbox in 5 minutes
- [Agent Accounts overview](https://developer.nylas.com/docs/v3/agent-accounts/) — what they are and when to use them
- [Cookbook recipes](https://developer.nylas.com/docs/cookbook/) — handle replies, multi-turn conversations, OTP extraction, and more

## Install

### Skills CLI

```bash
# Install all Nylas skills
npx skills add nylas/skills

# Or install individually
npx skills add nylas/skills --skill nylas-api
npx skills add nylas/skills --skill nylas-cli
npx skills add nylas/skills --skill nylas-hol-guard
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

Then open a new Claude Code session — skills will be available as `nylas-api`, `nylas-cli`, and `nylas-hol-guard`.

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
