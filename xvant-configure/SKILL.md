---
name: xvant-configure
description: "Use when changing Claude settings, permissions, env, keybindings or enabling automatic behavior. Hook authoring uses xvant-extend."
---

Use built-in `update-config` for settings.json/settings.local.json, permissions, env and automation hooks. Implement recurring event behavior with a harness hook. For theme/model suggest `/config`.

- Repeated safe calls: `fewer-permission-prompts` scans transcripts for allowlist candidates.
- Key chords and submit keys: `keybindings-help`, ~/.claude/keybindings.json.
- Recommend and wire automations: `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/claude-code-setup/skills/claude-automation-recommender/SKILL.md`. To author a hook script, use xvant-extend.
