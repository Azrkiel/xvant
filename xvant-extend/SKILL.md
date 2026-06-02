---
name: xvant-extend
description: Use when authoring an extension artifact for Claude Code itself — writing an MCP server, a hook script, or a plugin (commands/agents/structure). Triggers include "build an MCP server", "write a hook script", "create a plugin", "add a slash command", "make an agent". For enabling or recommending an automation or changing settings (not writing the script), use xvant-configure; for authoring a skill, use xvant-write-skill.
---

# xvant-extend

Advanced authoring for Claude Code extensions. Pick the section that matches the task. (For skills, use `xvant-write-skill`.)

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

## Section: MCP server (spine: mcp-server-dev)
Build a Model Context Protocol server / app, with prompt-caching-aware design where relevant.
- Server: `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/mcp-server-dev/skills/build-mcp-server/SKILL.md`
- App: `.../mcp-server-dev/skills/build-mcp-app/SKILL.md`
- Bundle (.mcpb): `.../mcp-server-dev/skills/build-mcpb/SKILL.md`
- Integrating an MCP server into a plugin: `.../plugin-dev/skills/mcp-integration/SKILL.md`

## Section: hook / automation rule (spine: plugin-dev hook-development + hookify)
For automated behaviors ("whenever X, do Y") — the harness runs these, not the model.
- Hook development: `.../plugin-dev/skills/hook-development/SKILL.md`
- Writing hook rules: `.../hookify/skills/writing-rules/SKILL.md`
- For settings.json changes/permissions/env without writing a hook, use the built-in `update-config`.

## Section: plugin (spine: plugin-dev)
- Structure: `.../plugin-dev/skills/plugin-structure/SKILL.md`
- Commands: `.../plugin-dev/skills/command-development/SKILL.md`
- Agents: `.../plugin-dev/skills/agent-development/SKILL.md`
- Settings: `.../plugin-dev/skills/plugin-settings/SKILL.md`

(All paths under `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/`.)
