---
title: Trigger, Scope, Sender, Recipients
section: choose
---

## Trigger, Scope, Sender, Recipients

**Triggers.** These are the documented `trigger_event` values: `booking.cancelled`, `booking.created`, `booking.pending`, `booking.reminder`, `booking.rescheduled`, `calendar.created`, `calendar.deleted`, `calendar.updated`, `contact.deleted`, `contact.updated`, `event.created`, `event.deleted`, `event.updated`, `folder.created`, `folder.deleted`, `folder.updated`, `grant.created`, `grant.deleted`, `grant.expired`, `grant.imap_sync_completed`, `grant.updated`, `message.bounce_detected`, `message.created`, `message.link_clicked`, `message.opened`, `message.send_failed`, `message.send_success`, `message.updated`, `notetaker.created`, `notetaker.deleted`, `notetaker.media`, `notetaker.meeting_state`, `notetaker.updated`, and `thread.replied`. The API can accept a trigger that never fires, so pick one whose payload has what the email needs. For example, `notetaker.created` has no participants or title.

**Scope.**
- **Application-level** (`/v3/templates`, `/v3/workflows`): fires for every grant in the application and shows in the Dashboard.
- **Grant-level** (`/v3/grants/{grant_id}/templates`, `/v3/grants/{grant_id}/workflows`): fires for one grant only, is listed only under that grant, and doesn't appear in the Dashboard's workflow list.
- **Both at once:** the two levels fire independently, so having both for the same trigger sends duplicates.

**Sender.**
- **Without `from`:** the workflow sends through the grant that triggered it. The email comes from the user's own name and address, replies go to the user, it counts against their provider's sending limits, and the grant needs mail send scopes; a grant without them is skipped.
- **With `from: { email, name }`:** it sends through transactional send on a domain you've registered. The template must be application-level, and the address must be on that exact domain.
- **`grant.expired` and `grant.deleted`:** these workflows must set `from`.

**Recipients.** You can't choose them per workflow.
- **`booking.*`:** everyone in `booking_info.participants`.
- **`event.created` and `event.updated`:** the event's `participants`.
- **Every other trigger:** the grant owner.
- **Round-robin bookings:** the chosen host and the guest.
- **A standalone Notetaker** (one with no grant) never triggers a workflow email.

Reference: https://developer.nylas.com/docs/v3/email/templates-workflows/#where-does-a-workflow-send-from
