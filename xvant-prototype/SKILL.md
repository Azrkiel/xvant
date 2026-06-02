---
name: xvant-prototype
description: Use for a throwaway exploratory prototype or spike to learn something fast, where production discipline (TDD, full review) is intentionally relaxed. Triggers include "prototype this", "quick spike", "throwaway version", "just hack something to see if it works", "proof of concept".
---

# xvant-prototype

Fast exploratory build to answer a question. Explicitly throwaway.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Spine:** prototype — `~/.claude/refs/anthropic-skills/engineering/prototype/SKILL.md`.

## Rules
- Optimize for learning speed, not quality. TDD and full review are relaxed here (this is the sanctioned exception in `xvant-tdd`).
- **Label it throwaway.** When the prototype answers its question, the real build starts fresh: `xvant-brainstorm` → `xvant-plan` → `xvant-tdd`. Don't promote spike code to production without a rewrite.
- Timebox it; report findings, not polish.
