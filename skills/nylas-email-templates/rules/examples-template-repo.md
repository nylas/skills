---
title: Example Templates
section: examples
---

## Example Templates

[nylas/workflow-email-templates](https://github.com/nylas/workflow-email-templates) has example templates for the common triggers and for the Send API. Every example has been render-tested in strict mode with full and sparse payloads. Start from the closest example rather than a blank file.

**What each folder holds:** folders are named exactly after their `trigger_event`, or `send-api/`. Each one has:
- one or more templates
- a `payload.sample.json`
- screenshots
- a README covering the trigger's payload gotchas

**Its scripts:**
- **`npm run render -- <folder>/<name>`:** render-tests a template in every case: full, sparse, no-recipient, the template's own cases, and every language for multilingual templates. It needs `NYLAS_API_KEY`.
- **`node scripts/install.mjs <folder>/<name>.html --workflow [--from you@yourdomain.com] [--dry-run]`:** creates the template and a disabled workflow.

**Adding a template there:**
1. Start the file with a header comment: a one-line `subject:`, the `trigger:`, and a `Replace ...` line for each placeholder.
2. If the template reads a custom metadata key, add `<name>.cases.json` with a case that sets it. Cases are deep-merged onto the sample payload, and `null` removes a key.
