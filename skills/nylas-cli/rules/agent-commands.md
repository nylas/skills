---
title: Agent Accounts
section: agent
---

## Agent Accounts

Managed email identities for AI agents — send, receive, and manage email without OAuth, SMTP, MX records, or third-party mailboxes. One grant provides email, calendar, and contacts. Behaviour is controlled through a workspace that references a policy and rules.

**Domains:** accounts can use the free managed `*.nylas.email` domain or your own custom domain (added via the Dashboard). The free tier includes **1 `*.nylas.email` domain and 1 custom domain** at no cost; paid plans add more. (The overall account cap is not agent-specific — see [`auth-commands.md`](auth-commands.md).)

### How it works

The chain is `application → connector → grant (agent account) → workspace → policy + rules`. The **workspace** is the indirection layer: it holds a `policy_id` and `rules_ids[]`, so policy or rules can be swapped without editing the grant (no risk of breaking a running agent mid-send). On `account create`, Nylas auto-provisions the `nylas` connector (if absent) plus a default workspace and policy, so the account works immediately; attach a custom policy afterward via `nylas workspace update <workspace-id> --policy-id <id>`.

- **Inbound mail**: Nylas owns the `*.nylas.email` MX records → matches the recipient address to its grant → the workspace loads the policy and evaluates rules by priority → the message is delivered, or rejected if a rule fires a `block` action.
- **Outbound mail**: the active grant is resolved → its `workspace_id`/policy is fetched → outbound rules/limits are checked (a send is rejected if the policy restricts the recipient domain or a rate limit is exceeded) → delivery is DKIM-signed through Nylas infrastructure.

### Accounts

```bash
nylas agent account list                              # List agent accounts
nylas agent account list --json
nylas agent account create <email>                    # Create an agent identity
nylas agent account create <email> --app-password '...'  # Optional IMAP/SMTP app password for mail-client access
nylas agent account get [<agent-id|email>]            # Account details + workspace link
nylas agent account update [<agent-id|email>] --app-password '...'  # Rotate or add the app password
nylas agent account move <agent-id|email> --workspace-id <id>  # Move account to another workspace
nylas agent account delete <agent-id|email>           # Prompts for confirmation
nylas agent account delete <agent-id|email> --yes     # Skip confirmation (-y; or -f/--force)
```

An agent account is a `provider=nylas` grant. Creating it does **not** auto-switch — make it active with `nylas auth switch <email-or-grant-id>`, then the normal `nylas email`, `nylas calendar`, and `nylas contacts` commands run against it (same endpoints as OAuth grants). Active-grant selection works the same for all account types — see [`auth-commands.md`](auth-commands.md) ("Active account with multiple grants").

### Policies

```bash
nylas agent policy list                               # All policies (/v3/policies)
nylas agent policy create --name <name>               # Create by name
nylas agent policy create --data '{"name":"..."}'     # Inline JSON
nylas agent policy create --data-file policy.json     # JSON from file
nylas agent policy get|read <policy-id>               # get and read are aliases
nylas agent policy update <policy-id> --name <name>
nylas agent policy update <policy-id> --data-file update.json
nylas agent policy delete <policy-id> --yes
```

Policy delete is rejected while any `provider=nylas` agent workspace still references it.

### Rules

```bash
nylas agent rule list                                 # All rules + workspace attachments
nylas agent rule get|read <rule-id>                   # get and read are aliases
nylas agent rule create --name "Block example" \
  --condition from.domain,is,example.com --action block
nylas agent rule create --name "Archive outbound" --trigger outbound \
  --condition recipient.domain,is,example.com --action archive
nylas agent rule create --data-file rule.json
nylas agent rule update <rule-id> --name "..." --description "..."
nylas agent rule delete <rule-id> --yes
```

Flags: `--name`, `--description`, `--priority <int>`, `--trigger inbound|outbound` (defaults to `inbound` when using flags), `--enabled|--disabled`, `--match-operator all|any`, plus repeatable `--condition <field,operator,value>` and `--action <type[=value]>`. Condition fields include `from.domain`, `from`, `recipient.domain`, `subject`, `outbound.type`; for `in_list`, pass `field,in_list,list-id-1,list-id-2`. Actions include `block`, `archive`, `mark_as_read`, `mark_as_starred`, `mark_as_spam`. `--data`/`--data-file` accept a raw JSON body instead of flags.

### Lists

Reusable named lists of values (domains, addresses, etc.) referenced by rule conditions via `field,in_list,<list-id>` — edit a list to change what many rules match without touching each rule.

```bash
nylas agent list list                                 # List all lists
nylas agent list create --name "Blocked domains"      # Create a list
nylas agent list get <list-id>                        # Show a list and its items
nylas agent list items <list-id>                      # Show list items only
nylas agent list add <list-id> <value> [<value>...]   # Add items
nylas agent list remove <list-id> <value> [<value>...] # Remove items
nylas agent list update <list-id> --name "..." --description "..."
nylas agent list delete <list-id> --yes
```

### Workspaces

Workspaces are a top-level command (`nylas workspace`, aliases `workspaces`/`ws`). A workspace groups agent accounts and attaches a policy plus rules — the indirection that lets you swap policy/rules without editing the account.

```bash
nylas workspace list                                  # List workspaces
nylas workspace get <workspace-id>                    # Workspace details
nylas workspace create --name "My Workspace" --domain yourapp.nylas.email [--policy-id <id>] [--auto-group]
nylas workspace update <workspace-id> --policy-id <id>          # Swap the attached policy
nylas workspace update <workspace-id> --rules-ids <id1>,<id2>   # Attach rules (rules_ids[])
nylas workspace delete <workspace-id> --yes
```

`--name` and `--domain` are required on create.

### Status & Overview

```bash
nylas agent status                                    # Agent feature/config status
nylas agent status --json
nylas agent overview                                  # Summary across all agent resources (accounts, policies, rules, lists)
```

### Quick start

```bash
nylas agent account create support@yourapp.nylas.email      # create the grant
nylas auth switch support@yourapp.nylas.email               # make it the active account
nylas email send --to customer@example.com --subject "Receipt" --body "Order confirmed."
nylas email list --limit 5 --json
```

Route `nylas agent account`, `nylas agent policy`, `nylas agent rule`, `nylas agent list`, `nylas agent status`, `nylas agent overview` (alias `nylas agents`), and `nylas workspace` questions here. See "How it works" above for the architecture.
