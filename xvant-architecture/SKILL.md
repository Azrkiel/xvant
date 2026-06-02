---
name: xvant-architecture
description: Use when improving a codebase's structure rather than fixing a specific bug — find refactoring opportunities, consolidate tightly-coupled modules, make it more testable and AI-navigable, or get a high-level overview of an unfamiliar system. Triggers include "improve the architecture", "refactor this", "find deepening opportunities", "zoom out on this codebase".
---

# xvant-architecture ◆

Improve structure: deepen modules, clarify boundaries, raise testability and AI-navigability.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.
> Diagram step: follow `~/.claude/skills/_shared/ascii-diagram.md` for SYSTEM-level diagrams — dependency graphs and module boundaries, not per-feature flows. Render before recommending changes.

**Spine:** improve-codebase-architecture — find deepening opportunities, informed by the domain language in `CONTEXT.md` and the decisions in `docs/adr/`. Full reference: `~/.claude/refs/anthropic-skills/engineering/improve-codebase-architecture/SKILL.md`.

## What to look for
- Modules that are shallow (thin wrapper over a wide interface) → deepen them.
- Tightly-coupled clusters that always change together → consolidate behind one interface.
- Files that grew too large / do too much → split by responsibility.
- Tangled boundaries that block testing → introduce seams.

## Mode: zoom-out (graft)
For a fast high-level map of an unfamiliar system before diving in: `~/.claude/refs/anthropic-skills/engineering/zoom-out/SKILL.md`.

Don't propose unrelated refactors — stay focused on what serves the goal. Big structural changes get an `xvant-plan` + `xvant-plan-review` first.
