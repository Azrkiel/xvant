---
name: xvant-retro
description: Use for a human-facing retrospective or session report — lessons learned, what went well and badly, and why. Triggers include "retro", "retrospective", "what did we learn", "what went well", "session report", "post-mortem". This owns the reflective content; for a machine-facing resume document use xvant-handoff.
---

# xvant-retro

Human-facing reflection: what worked, what didn't, why, and what to carry forward.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Spine:** session-report — structured session summary for a person to read: `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/session-report/skills/session-report/SKILL.md`.

## Graft mode
- **Cross-project / global retro** (patterns across sessions): `~/.claude/refs/gstack/retro/SKILL.md`.

## Boundary with xvant-handoff
This skill owns the **reflective** content — lessons, decisions-and-why, what to reuse, what to avoid next time. It does NOT reproduce the machine-facing resume state (branch, commands to resume, next steps) — that lives in `xvant-handoff`, which links here rather than duplicating reflection.
