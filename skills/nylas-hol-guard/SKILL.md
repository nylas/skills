---
name: nylas-hol-guard
description: "Use HOL Guard as an optional local pre-execution safety boundary for AI coding agents before state-changing Nylas API or CLI workflows. Use when a supported local harness will send or reply to email, create/update/delete calendar events, mutate contacts or webhooks, manage agent accounts, or change Nylas admin state. Keep Nylas grants, scopes, policies, confirmations, audit logs, and API validation authoritative."
compatibility: "Requires Python 3.10+ and a HOL Guard-supported local AI harness. Nylas credentials and authorization remain separate."
license: MIT
metadata:
  author: hashgraph-online
  version: "1.0.0"
  organization: Hashgraph Online
  date: August 2026
  abstract: Local HOL Guard setup and protected-session guidance for state-changing Nylas agent workflows.
---

# Nylas + HOL Guard

Use HOL Guard at the local AI-harness boundary before an agent performs state-changing Nylas work. HOL Guard is additive: it does not replace Nylas authentication, grant scopes, Agent Account policies, confirmations, audit logging, or API validation.

## Rules

### Setup & Protected Session (CRITICAL)

- [`rules/setup-hol-guard.md`](rules/setup-hol-guard.md) — Install HOL Guard, initialize a supported harness, verify status, and launch the protected agent session.

### Nylas Mutations (HIGH)

- [`rules/safety-mutations.md`](rules/safety-mutations.md) — Use the protected session for email, calendar, contacts, webhooks, agent-account, and admin mutations while preserving Nylas-native controls.

## Working model

1. Confirm the work is state-changing and the local AI harness is supported.
2. Install and initialize HOL Guard only with the user's approval.
3. Verify `hol-guard status`, then launch the coding agent through `hol-guard run <harness>`.
4. Perform Nylas work inside that protected session using the existing `nylas-api` or `nylas-cli` skill.
5. Keep least-privilege Nylas grants/scopes and product-native confirmations/policies in force.

Read-only Nylas inspection does not by itself require this skill. Do not describe HOL Guard as authorization for a Nylas operation or as an in-process Nylas server control.

## References

- Nylas API docs: https://developer.nylas.com/docs/api/v3/
- Nylas Agent Accounts: https://developer.nylas.com/docs/v3/agent-accounts/
- HOL Guard install guide: https://github.com/hashgraph-online/hol-guard/blob/main/docs/guard/get-started.md
