---
title: Installation & Setup
section: setup
---

## Installation & Setup

```bash
brew install nylas/nylas-cli/nylas                 # Homebrew (macOS/Linux)
go install github.com/nylas/cli/cmd/nylas@latest  # Go
```

Prefer package-managed installs. If you use a hosted installer from `cli.nylas.com`, download it and inspect it before executing it instead of piping it directly into a shell.

### First-Time Setup

```bash
nylas init                                    # Interactive setup wizard
nylas init --api-key nyl_abc123               # Quick setup with existing key
nylas init --api-key nyl_abc123 --region eu   # EU region
nylas init --google                           # Google SSO shortcut
nylas init --microsoft                        # Microsoft SSO shortcut
nylas init --github                           # GitHub SSO shortcut
```

### Agents: First-Run / Not Configured

`nylas init` opens a browser for SSO and runs **only interactively (a TTY)**. An agent cannot complete it — in a non-interactive shell it fails fast with `--api-key is required in non-interactive mode`. Do not run it yourself or loop on it.

When a command fails with `API key not configured`, or `nylas auth status --json` returns `"configured": false`:

1. **User already has an API key** → set up non-interactively, no browser:
   ```bash
   export NYLAS_API_KEY=nyl_...        # or have them run: nylas init --api-key nyl_...
   ```
2. **Brand-new user (no key)** → you cannot sign them in. Tell the human to run, in **their own terminal**:
   ```bash
   nylas init                          # opens a browser to log in / create an account
   nylas init --google                 # provider shortcut (or --microsoft / --github)
   ```
   Then wait for them to confirm it finished.
3. **Verify before continuing** — never assume success:
   ```bash
   nylas auth status --json            # → {"configured": true, "default_grant": "...", "grant": {...}}
   ```

Don't put a user's API key into their shell history for them — prefer the env var, or have them run `nylas init --api-key` themselves.

### Global Flags

`--config PATH`, `--format table|json|yaml`, `--json`, `--no-color`, `--quiet`/`-q`, `--verbose`/`-v`, `--wide`/`-w`, `--help`/`-h`

### Config Management

```bash
nylas config list                             # Show all config
nylas config get <key>                        # Get a value
nylas config set <key> <value>                # Set a value
nylas config reset [--force]                  # Reset config
nylas config path                             # Show config file path
```

Config file: `~/.config/nylas/config.yaml` | Credentials in system keyring or encrypted file storage, depending on platform/environment

### Environment Variables

`NYLAS_API_KEY`, `NYLAS_CLIENT_ID`, `NYLAS_GRANT_ID`, `NYLAS_DISABLE_KEYRING`

### Shell Completion & Updates

```bash
nylas completion bash|zsh|fish|powershell     # Generate completions
nylas update                                  # Self-update the CLI
```

### Diagnostics

```bash
nylas doctor                                  # Check credentials, grants, secret store, connectivity, config
nylas doctor --verbose                        # Detailed diagnostic output
```
