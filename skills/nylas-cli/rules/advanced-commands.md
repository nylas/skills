---
title: Advanced Command Families
section: advanced
---

## Advanced Command Families

```bash
nylas admin ...
nylas scheduler ...
nylas timezone ...
nylas agent ...
nylas workflow ...
nylas template ...
nylas email templates ...
```

These families are part of the current upstream CLI docs and should be treated as first-class command surfaces, not edge cases. When a question is about one of these areas, prefer the dedicated command reference over the older summary in the base skill files.

Key coverage to remember:

- `nylas admin` covers admin-level resources such as applications, callback URIs, connectors, credentials, and grants.
- `nylas scheduler` and `nylas workflow` cover hosted scheduling and workflow automation flows.
- `nylas timezone` covers timezone conversion, DST, and meeting-time helpers.
- `nylas template` and `nylas email templates` cover hosted and local template workflows.
- `nylas email-signing`, `nylas encryption`, and `nylas explain-gpg` are documentation/help topics tied to `nylas email send` signing/encryption flags, `nylas email read` decryption/verification, and GPG troubleshooting rather than standalone top-level command families.
