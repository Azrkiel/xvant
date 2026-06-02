---
name: xvant-plan
description: Use when you have a spec or requirements for a multi-step task and need a written implementation plan, before touching code. Triggers include "write a plan", "plan this out", "break this into tasks", and turning an approved design into bite-sized implementation steps.
---

# xvant-plan ◆

Write an implementation plan assuming the engineer has zero context for this codebase.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.
> Diagramming: follow `~/.claude/skills/_shared/ascii-diagram.md` — the plan MUST include an ASCII diagram of data flows, inputs/outputs, user flows, and error states. This is what `xvant-plan-review` then critiques.

**Announce:** "Using xvant-plan to write the implementation plan."

## Spine (superpowers writing-plans)

- **Map files first** — what each created/modified file is responsible for. Small, focused files over large ones. Files that change together live together.
- **Bite-sized steps (2-5 min each):** write failing test → run it (see it fail) → minimal code → run tests (pass) → commit. DRY, YAGNI, TDD, frequent commits.
- **No placeholders.** Never "TBD", "add error handling", "write tests for the above", or "similar to Task N". Every code step shows the actual code; every command shows expected output. References to types/functions must be defined in some task.
- **Header:** Goal (one sentence), Architecture (2-3 sentences), Tech stack. Steps use `- [ ]` checkboxes.
- **Self-review** against the spec: coverage (every requirement maps to a task), placeholder scan, type/name consistency. Fix inline.

Save to `docs/plans/YYYY-MM-DD-<feature>.md` (or beside the work if not a git repo).

## Graft: autonomous mode (gstack autoplan)
For a hands-off review pipeline (CEO → design → eng critique chained), see `~/.claude/refs/gstack/autoplan/SKILL.md`. Use when the user wants the plan auto-reviewed end-to-end rather than step-by-step.

## Fold option (not active)
`xvant-to-work` (spec → PRD/issues) could be a final "emit PRD/issues" mode here. Kept separate because it triggers distinctly. A future pass may fold it.

## Handoff
After the plan is saved and self-reviewed, offer execution: `xvant-execute` (this session, checkpointed) or subagent-driven (fresh subagent per task). Then stop for user choice.
