---
title: HOL Guard Setup and Protected Session
section: setup
---

## HOL Guard Setup and Protected Session

Use this only for a supported local AI coding-agent harness. Ask before installing software or changing harness configuration.

```bash
pipx install hol-guard                  # Install the published HOL Guard package
hol-guard init                          # Guided first-run setup; explains changes before applying them
hol-guard detect --json                 # Confirm the supported local harness
hol-guard status                        # Verify current protection posture
hol-guard run <harness>                 # Launch the coding agent through Guard
```

If a manual harness setup is required, follow HOL Guard's current install guide. Generic supported harnesses use `hol-guard install <harness>`; Hermes uses `hol-guard hermes bootstrap`. Do not guess a harness identifier.

After setup, run the Nylas task from the Guard-launched agent session. Do not use `hol-guard command test` as an authorization verdict; it is an inspection surface, not a replacement for runtime policy or Nylas authorization.

Reference: https://github.com/hashgraph-online/hol-guard/blob/main/docs/guard/get-started.md
