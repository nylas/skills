---
title: MCP & AI Commands
section: mcp
---

## MCP (Model Context Protocol)

```bash
nylas mcp install                             # Install MCP for default assistant
nylas mcp install --assistant claude-code      # Install for Claude Code
nylas mcp install --assistant cursor           # Install for Cursor
nylas mcp install --all                        # Install for all assistants
nylas mcp status                              # Check MCP status
nylas mcp uninstall --assistant A              # Uninstall from assistant
nylas mcp serve                               # Start MCP server
```

## AI Chat

```bash
nylas chat                                    # Chat with your data (default agent)
nylas chat --agent claude                     # Use Claude as agent
nylas chat --agent codex                      # Use Codex as agent
nylas chat --agent ollama --model llama2       # Use local Ollama model
nylas chat --port 8080                        # Custom port
nylas chat --no-browser                       # CLI-only (no browser)
```

## AI Configuration

```bash
nylas ai config                               # Configure AI settings
```
