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
