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
hol-guard run <harness> --dry-run       # Preview the protected launch before activation
hol-guard run <harness>                 # Launch the coding agent through Guard
hol-guard doctor <harness> --json       # Verify harness-specific protection health
```

`hol-guard init` is the maintained guided first-run path. If manual setup is preferred, use `hol-guard bootstrap`, then `hol-guard install <harness>` with the exact identifier returned by `hol-guard detect --json`. Hermes also supports `hol-guard hermes bootstrap`. Never guess a harness identifier.

Do not skip the protected dry run. If it reports an unexpected mutation or error, stop instead of launching the real agent. Do not claim protection until Guard status/doctor output proves the harness is configured successfully.

After setup, run the Nylas task from the Guard-launched agent session. Do not use `hol-guard command test` as an authorization verdict; it is an inspection surface, not a replacement for runtime policy or Nylas authorization.

Reference: https://github.com/hashgraph-online/hol-guard/blob/release/3.0/docs/guard/get-started.md
