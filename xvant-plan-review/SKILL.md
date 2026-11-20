---
name: xvant-plan-review
description: "Use when critiquing an existing plan for scope, ambition, design, DX, failure modes or a 10x rethink."
---

Review only. Append a system audit, error/rescue map, failure modes and recommendations to the plan. Consider replacing a fundamentally unsound approach.

Trace each normal, nil, empty and upstream-error path. Name errors, expose failures, cover repeated interactions, slow networks, stale state, navigation and observability. Diagram nontrivial flows; record deferred work in TODOS. Procedures (skip telemetry): engineering `~/.claude/refs/gstack/plan-eng-review/SKILL.md`, design `~/.claude/refs/gstack/plan-design-review/SKILL.md`, developer experience `~/.claude/refs/gstack/plan-devex-review/SKILL.md`, question tuning `~/.claude/refs/gstack/plan-tune/SKILL.md`.

**10x CEO review:** have the user choose expansion (10x value for 2x effort), selective expansion (opt in per idea), hold scope (maximum rigor), or reduction (minimum viable scope). Commit to the posture; use AskUserQuestion for each scope change. Apply reversibility and magnitude, inversion, focus by subtraction, people-first thinking, decisions at 70% information and the 10-star product exercise. Prefer a complete solution where feasible. `~/.claude/refs/gstack/plan-ceo-review/SKILL.md`
