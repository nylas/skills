---
title: API Key and Base URL
section: api
---

## API Key and Base URL

This skill is integration-authoring guidance: it covers writing templates and configuring workflows with an application API key, not reading users' mail or calendars.

- **API key:** read it from the environment, such as `NYLAS_API_KEY`. Never hardcode it in a template, a script, or a commit.
- **Base URL:** `https://api.us.nylas.com` for US applications, `https://api.eu.nylas.com` for EU applications. Every path starts with `/v3/`.
- **Headers:** `Authorization: Bearer $NYLAS_API_KEY` and `Content-Type: application/json`.

```bash
export NYLAS_API_KEY=nyk_...
export NYLAS_API_URI=https://api.us.nylas.com   # or https://api.eu.nylas.com
```
