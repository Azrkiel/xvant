---
name: xvant-to-work
description: Use to convert a spec, design, or rough requirements into backlog-ready work items — a PRD or a set of issues/tickets. Triggers include "turn this into a PRD", "write a PRD", "create issues", "make tickets", "break this into GitHub issues". Not for the implementation plan itself (use xvant-plan).
---

# xvant-to-work

Emit backlog-ready artifacts from a spec: a PRD, or discrete issues/tickets.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Spine:** anthropic to-prd. Full procedures:
- PRD: `~/.claude/refs/anthropic-skills/engineering/to-prd/SKILL.md`
- Issues/tickets: `~/.claude/refs/anthropic-skills/engineering/to-issues/SKILL.md`

## Modes
- **PRD mode** — structured product requirements doc: problem, users, goals, scope, non-goals, acceptance criteria, open questions.
- **Issues mode** — decompose into independently-shippable issues, each with a title, context, acceptance criteria, and dependencies/labels. If a tracker CLI is available (`gh`, `glab`), offer to create them; otherwise emit markdown.

Pick mode from the user's phrasing ("PRD" vs "issues/tickets"). When unsure, ask once.

Relationship: this is the output side of a spec. The build plan itself is `xvant-plan`.
