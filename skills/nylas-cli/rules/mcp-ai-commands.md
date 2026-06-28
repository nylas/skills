---
title: MCP & AI Commands
section: mcp
---

## MCP (Model Context Protocol)

```bash
nylas mcp install                             # Install MCP for default assistant
nylas mcp install --assistant claude-desktop  # Install for Claude Desktop
nylas mcp install --assistant claude-code     # Install for Claude Code
nylas mcp install --assistant cursor          # Install for Cursor
nylas mcp install --assistant windsurf        # Install for Windsurf
nylas mcp install --assistant vscode          # Install for VS Code
nylas mcp install --all                       # Install for all detected assistants
nylas mcp status                              # Check MCP status
nylas mcp uninstall --assistant A             # Uninstall from assistant
nylas mcp serve                               # Start MCP server
```

## AI Configuration

```bash
nylas ai config                               # Configure AI settings
nylas ai usage                                # Show AI usage statistics
nylas ai set-budget                           # Set monthly AI usage budget
nylas ai show-budget                          # Show current AI budget configuration
nylas ai clear-data                           # Clear all AI data and learned patterns
```
