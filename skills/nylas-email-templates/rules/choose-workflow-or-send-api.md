---
title: Workflow or Send API
section: choose
---

## Workflow or Send API

A **workflow** links a template to a trigger (`trigger_event`). When the trigger fires, Nylas renders the template against the notification payload and sends the result. **A workflow can't decide whether to send.** It sends for every notification that matches its trigger and scope. There's no filter or condition, and no way to limit it to one Scheduler configuration or one calendar. Branching inside the template changes what the email says, not whether it goes out.

| Use a workflow when | Use the Send API when |
|---|---|
| Every matching notification should produce an email (every booking confirmation, every expired account) | Only some notifications should produce an email (only events your app created, only users who opted in) |
| The payload has every value the email needs | The email needs data your app holds |
| | The trigger is high-volume (`message.created`, `event.created` across whole calendars) |

For the Send API path, subscribe to the notification as a webhook, decide in your handler whether to send, and send a stored template with your own variables (`rules/api-send-template.md`).

Branching still helps inside a workflow. For example, `{{#if (eq configuration_id "...")}}` lets one booking workflow serve several Scheduler configurations.

Reference: https://developer.nylas.com/docs/v3/email/templates-workflows/
