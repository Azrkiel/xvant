---
name: xvant-configure
description: Use to change how the Claude Code harness behaves — edit settings.json, allow commands/permissions, set env vars, reduce permission prompts, rebind keys, or make something happen automatically (enable or recommend an automation: "from now on when X", "whenever X", "before/after X"). Triggers include "allow this command", "change my settings", "reduce permission prompts", "rebind a key", "I want X to happen automatically". For authoring the hook script / MCP server / plugin itself, use xvant-extend.
---

# xvant-configure

Change how the Claude Code harness behaves. Automated behaviors need hooks (the harness runs them, not the model) — memory/preferences can't fulfill "whenever X do Y".

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Spine:** the built-in `update-config` skill — settings.json/settings.local.json edits, permissions (allow/move), env vars, and hooks for automation ("from now on when X", "each time X", "before/after X"). Use it for any settings or hook change.

## Graft modes
- **Fewer permission prompts** — scan transcripts for common safe calls and build an allowlist: built-in `fewer-permission-prompts`.
- **Keybindings** — rebind keys, chords, submit key (`~/.claude/keybindings.json`): built-in `keybindings-help`.
- **What to automate** — recommend which hooks/automations would help, then wire them: `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/claude-code-setup/skills/claude-automation-recommender/SKILL.md`.

For simple settings (theme/model), suggest the `/config` command. For writing the hook script itself, see `xvant-extend`.
