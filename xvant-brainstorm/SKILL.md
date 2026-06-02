---
name: xvant-brainstorm
description: Use before any creative or product work — a new feature, idea, component, or behavior change — before designing or writing code. Triggers include "brainstorm this", "I have an idea", "is this worth building", "help me think through", and designing something that does not exist yet.
---

# xvant-brainstorm

Turn ideas into validated designs through collaborative dialogue, then hand off a spec.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite output discipline. Human-facing design prose is exempt — keep it readable.

**Announce:** "Using xvant-brainstorm to shape this before we build."

**HARD GATE:** Do NOT write code, scaffold, or take any implementation action until a design is presented AND the user approves it. Applies to every project regardless of perceived simplicity.

## Process (spine: superpowers brainstorming)

1. **Explore context** — read relevant files, docs, recent commits. If the request is multiple independent subsystems, decompose first and brainstorm one at a time.
2. **Ask one question at a time** — prefer multiple choice. Understand purpose, constraints, success criteria. Never batch a wall of questions.
3. **Propose 2-3 approaches** with trade-offs; lead with your recommendation and why.
4. **Present the design in sections** scaled to complexity; get approval after each.
5. **Write the spec** to a sensible location (default `docs/specs/YYYY-MM-DD-<topic>.md`; if not a git repo, put it beside the work). Self-review for placeholders, contradictions, scope, ambiguity. Fix inline.
6. **User reviews the spec**, then hand off to `xvant-plan`. Do not jump to any other skill.

## ★ Mode: Office Hours (preserve — Garry signature)

When the work is a product/startup idea, run the YC diagnostic before solutions. Full procedure: `~/.claude/refs/gstack/office-hours/SKILL.md` (ignore its gstack telemetry/gbrain preamble).

- **Startup mode** — six forcing questions: demand reality, status quo, desperate specificity, narrowest wedge, observation, future-fit. Specificity is the only currency: a name, a role, a company, a reason — not "everyone needs this".
- **Builder mode** — for hackathons, learning, side projects, OSS: enthusiastic design-thinking collaborator, not interrogation.

Output of office-hours is a design doc, never code.

## Don'ts
- No implementation before approval.
- No "this is too simple to need a design" — short designs are fine, but present one.
