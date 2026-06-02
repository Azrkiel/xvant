---
name: xvant-plan-review
description: Use to critique an existing implementation or product plan before building — pressure-test scope, ambition, failure modes, and edge cases. Triggers include "review this plan", "think bigger", "expand scope", "is this plan solid", "rethink this plan", and "is this ambitious enough". Not for reviewing already-written code (use xvant-review).
---

# xvant-plan-review

Make a plan extraordinary and catch every landmine before it ships. Do NOT change code or start implementation — review only.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Findings stay readable.
> Reasoning depth is exempt from caveman — think expansively (cathedral-mode where chosen), present findings lean.

**Spine:** gstack plan-eng-review. Full procedures (ignore gstack telemetry preamble):
- Engineering rigor: `~/.claude/refs/gstack/plan-eng-review/SKILL.md`
- Design critique: `~/.claude/refs/gstack/plan-design-review/SKILL.md`
- DX critique: `~/.claude/refs/gstack/plan-devex-review/SKILL.md`
- Question tuning: `~/.claude/refs/gstack/plan-tune/SKILL.md`

## Prime directives (eng review)
Zero silent failures. Every error has a name (no catch-all). Every data flow has shadow paths (nil / empty / upstream-error) — trace all four. Interactions have edge cases (double-click, navigate-away, slow net, stale state, back button). Observability is scope, not an afterthought. Diagrams mandatory for non-trivial flows. Everything deferred gets written to TODOS.

## ★ Mode: 10x CEO review (preserve — Garry signature)
Four scope postures — the user picks one and you COMMIT to it (every scope change is an explicit opt-in via AskUserQuestion, never silent):
- **SCOPE EXPANSION** — build a cathedral. Ask "what makes this 10x better for 2x the effort?"
- **SELECTIVE EXPANSION** — hold scope as baseline, surface each expansion as its own opt-in.
- **HOLD SCOPE** — accepted scope, maximum rigor on failure modes/edges/observability.
- **SCOPE REDUCTION** — surgeon: minimum viable version, cut the rest.

Think with CEO instincts (don't enumerate them, internalize): reversibility×magnitude doors (Bezos), inversion ("what makes us fail?", Munger), focus-as-subtraction (Jobs 350→10), people>products>profits (Horowitz), 70% info is enough to decide, Brian Chesky founder-mode 10-star product thinking. Completeness is cheap with AI — prefer the full implementation over the shortcut. Full set: `~/.claude/refs/gstack/plan-ceo-review/SKILL.md`.

## Output
A review report appended to the plan: system audit, error/rescue map, failure modes, opinionated recommendations. You may say "scrap it and do this instead" if a fundamentally better approach exists.
