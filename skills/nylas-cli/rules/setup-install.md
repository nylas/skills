---
title: Installation & Setup
section: setup
---

## Installation & Setup

```bash
brew install nylas/nylas-cli/nylas            # macOS/Linux
go install github.com/nylas/cli/cmd/nylas@latest  # Go
```

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

`--json`, `--no-color`, `--verbose`/`-v`, `--limit N`, `--yes`/`-y`, `--help`/`-h`, `--config PATH`

### Config Management

```bash
nylas config list                             # Show all config
nylas config get <key>                        # Get a value
nylas config set <key> <value>                # Set a value
nylas config reset [--force]                  # Reset config
nylas config path                             # Show config file path
```

Config file: `~/.config/nylas/config.yaml` | Credentials in system keyring

### Environment Variables

`NYLAS_API_KEY`, `NYLAS_CLIENT_ID`, `NYLAS_GRANT_ID`, `NYLAS_DISABLE_KEYRING`

### Shell Completion & Updates

```bash
nylas completion bash|zsh|fish|powershell     # Generate completions
nylas update                                  # Self-update the CLI
```
