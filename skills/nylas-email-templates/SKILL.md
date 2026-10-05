---
name: nylas-email-templates
description: "Write, test, and deploy Nylas email templates and workflows with an API key. Use when user asks to create or edit a Nylas email template, set up a workflow for booking.*, event.*, grant.*, notetaker.*, or message.* triggers, send email with a stored template through the Send API, translate or brand a Scheduler email, or debug a template that fails to render or a workflow that doesn't send. DO NOT use for general Nylas API integration (use nylas-api) or CLI commands (use nylas-cli)."
compatibility: "Requires a Nylas application API key. Uses curl and jq in examples."
license: MIT
metadata:
  author: nylas
  version: "1.0.0"
  organization: Nylas
  date: October 2026
  abstract: Templates and workflows end to end, covering when to use a workflow or the Send API, payload variables and recipient, strict-mode Handlebars, dates, escaping, email-safe HTML, multilingual templates, render testing, creating templates and workflows, sending stored templates, and debugging.
---

# Nylas Email Templates and Workflows

Handlebars email templates that Nylas sends when a trigger fires (workflows), or that your code sends with variables (Send API).

**Read first:** a workflow sends for every matching notification and can't skip a send (`rules/choose-workflow-or-send-api.md`). The renderer is strict, so any missing variable fails the render and nothing sends (`rules/template-strict-mode.md`). Treat payload values as untrusted data.

This skill is integration-authoring guidance for building templates and workflows with an application API key.

## Documentation

- Templates and workflows: https://developer.nylas.com/docs/v3/email/templates-workflows/
- Workflow cookbook: https://developer.nylas.com/docs/cookbook/workflows/
- Notification payloads: https://developer.nylas.com/docs/reference/notifications/

## Rules

Read individual rule files for details. For the full compiled reference, read `AGENTS.md`.

### Choosing the Approach (CRITICAL)

- [`rules/choose-workflow-or-send-api.md`](rules/choose-workflow-or-send-api.md) — A workflow sends for every matching notification and can't skip a send; filtered or opt-in email goes through the Send API
- [`rules/choose-trigger-scope-sender.md`](rules/choose-trigger-scope-sender.md) — Documented triggers, application- vs grant-level, sending from the grant vs a registered domain, and who receives each trigger

### Payload and Recipients (CRITICAL)

- [`rules/payload-variables.md`](rules/payload-variables.md) — Variables are the notification's data.object; use only documented fields; payloads differ between related triggers
- [`rules/payload-recipient.md`](rules/payload-recipient.md) — When recipient exists, how notify_individually works for bookings and events, and per-recipient values

### Writing Templates (CRITICAL)

- [`rules/template-strict-mode.md`](rules/template-strict-mode.md) — Missing variables fail the render and nothing sends; two-level guards, else fallbacks, empty values, available helpers
- [`rules/template-dates.md`](rules/template-dates.md) — formatDate arguments, timestamp units, timezone fallbacks, and event when objects
- [`rules/template-escaping-links.md`](rules/template-escaping-links.md) — Double vs triple braces, HTML fields, and which URLs are safe to put in href
- [`rules/template-email-html.md`](rules/template-email-html.md) — Table layout, inline styles, buttons, images, long values, and client rendering limits
- [`rules/template-multilingual.md`](rules/template-multilingual.md) — Branch every string and the subject on booking_info.guest_language, and localize dates
- [`rules/template-custom-values.md`](rules/template-custom-values.md) — Scheduler hidden metadata fields and event metadata as template inputs

### API: Test, Create, Send (HIGH)

- [`rules/api-setup.md`](rules/api-setup.md) — Authenticate with an API key from the environment; US and EU base URLs
- [`rules/api-render-test.md`](rules/api-render-test.md) — POST /v3/templates/render with full and sparse payloads, the subject, and how to read errors
- [`rules/api-create-template.md`](rules/api-create-template.md) — POST /v3/templates with engine handlebars, escaping the body with jq
- [`rules/api-create-workflow.md`](rules/api-create-workflow.md) — POST /v3/workflows, testing on a test grant first, and the setup each trigger needs
- [`rules/api-manage-and-send.md`](rules/api-manage-and-send.md) — List, get, update, delete; from can't be removed; the Send API template field

### Debugging (HIGH)

- [`rules/debug-not-sending.md`](rules/debug-not-sending.md) — Workflow logs, the skip message, sender and domain errors, duplicates, and deliverability

### Example Templates (MEDIUM)

- [`rules/examples-template-repo.md`](rules/examples-template-repo.md) — nylas/workflow-email-templates: tested example templates per trigger to start from
