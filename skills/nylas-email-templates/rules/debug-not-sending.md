---
title: Why a Workflow Didn't Send
section: debug
---

## Why a Workflow Didn't Send

Check these in order:

1. **The logs:** in the Dashboard, open Logs, then System, and set Source to Workflows. Logs are kept for 14 days. A grant without send scopes logs `Workflow <ID> skipped: the grant is not valid or is missing the scopes required to send email`.
2. **The render:** render the template in strict mode against this exact payload (`rules/api-render-test.md`). A failed render sends nothing and reports nothing to your code.
3. **The workflow:** check `is_enabled`.
4. **The sender:** check the grant's send scopes, or that the `from` address is on your registered domain.
   - A mismatch returns `domain in url does not match the domain in the from email`.
   - With a strict DMARC policy, the From domain must exactly equal the registered domain.
5. **Trigger setup:** `disable_emails`, the webhook reminder, or `notify_individually` (`rules/api-create-workflow.md`).
6. **Duplicates:** check for an application-level and a grant-level workflow on the same trigger.

The first emails from a new sending domain often land in spam until it builds reputation.

Reference: https://developer.nylas.com/docs/cookbook/workflows/workflow-not-sending/
