# DagCode

A personal fork of [OpenCode](https://github.com/anomalyco/opencode) with some minor customizations.

## What's different

- **Cosmetic rebrand** -- TUI strings, terminal title, ASCII logo, and uninstall flow say "DagCode" instead of "OpenCode"
- **Provider-aware agent model selection** -- Subagent models can be configured per provider, so switching your primary between e.g. Anthropic and GitHub Copilot automatically resolves the right subagent models
- **Subagent model display** -- Task blocks and the subagent session header show which provider/model the subagent is using
- **Build lifecycle info** -- Sidebar shows build date and upstream version status
- **Logo tweaks** -- Orange accent color for the "DAG" portion, fixed shadow alignment

## Provider-aware model config

The main feature addition. In `opencode.json`, the agent `model` field accepts a provider-keyed object:

```json
{
  "agent": {
    "explore": {
      "model": {
        "anthropic": "anthropic/claude-haiku-4-5",
        "github-copilot": "github-copilot/claude-sonnet-4.5"
      }
    },
    "general": {
      "model": {
        "anthropic": "anthropic/claude-sonnet-4-6",
        "github-copilot": "github-copilot/claude-sonnet-4.5"
      }
    }
  }
}
```

Plain string model config still works as before for backward compatibility.

## Building

Requires [Bun](https://bun.sh/).

```bash
cd packages/opencode
bun install
bun dev          # dev mode
bun run build.ts --single  # single-platform release build
```

## Upstream

This fork tracks [anomalyco/opencode](https://github.com/anomalyco/opencode). Changes are kept cosmetic/minimal to make upstream merges straightforward.
