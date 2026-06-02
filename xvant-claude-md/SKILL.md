---
name: xvant-claude-md
description: Use to create or improve a project's CLAUDE.md / codebase documentation. Triggers include "init CLAUDE.md", "document this codebase", "improve my CLAUDE.md", "set up project instructions", "onboard this repo". Not for editing the global ~/.claude/CLAUDE.md baseline.
---

# xvant-claude-md

Create or sharpen a project's `CLAUDE.md` so future sessions have the context they need.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

## Modes
- **Init (spine: built-in `init`)** — initialize a new `CLAUDE.md` documenting the codebase: structure, key commands (build/test/run), conventions, gotchas. Use on a repo with no `CLAUDE.md`.
- **Improve (spine: claude-md-improver)** — audit and tighten an existing `CLAUDE.md`: remove stale/obvious content, add missing commands and conventions, keep it scannable. `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/claude-md-management/skills/claude-md-improver/SKILL.md`.

## What belongs in CLAUDE.md
Project-specific config and conventions an agent can't derive quickly: test/build/deploy commands, architecture decisions, naming/patterns, things NOT to touch, skill-routing rules. Keep out: generic best practices, anything the code already makes obvious.
