---
name: xvant-debug
description: Use when encountering any bug, test failure, crash, or unexpected behavior, before proposing fixes. Triggers include "this is broken", "why is this failing", "debug this", a stack trace, a flaky test, or behavior that diverges from expectation.
---

# xvant-debug ◆

Find the root cause before any fix. Symptom fixes are failure.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.
> Diagram step: follow `~/.claude/skills/_shared/ascii-diagram.md` to draw the ACTUAL vs EXPECTED flow — locate exactly where reality diverges before touching code.

## The Iron Law
```
NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST
```

## Four phases (spine: superpowers systematic-debugging)
1. **Root cause** — read the full error/stack; reproduce consistently; check recent changes (git diff/log); in multi-component systems, add diagnostic instrumentation at each boundary and run once to see WHERE it breaks; trace bad values back to their source.
2. **Pattern analysis** — find working examples in the same codebase; read references completely; list every difference; understand dependencies.
3. **Hypothesis** — state one hypothesis ("X is the cause because Y"); test with the smallest possible change, one variable at a time; confirmed → phase 4, else new hypothesis. Don't stack fixes.
4. **Fix** — write a failing test reproducing it (`xvant-tdd`), implement ONE root-cause fix, verify. After 3 failed fixes, STOP and question the architecture.

## Graft: triage (prioritization)
Many issues at once? Prioritize by impact/blast-radius before diving in: `~/.claude/refs/anthropic-skills/engineering/triage/SKILL.md`.

## Graft: quick-path (diagnose)
Fast first-pass diagnosis for a clearly-scoped single bug: `~/.claude/refs/anthropic-skills/engineering/diagnose/SKILL.md`. Still obey the Iron Law.

## Graft: investigate (gstack)
Evidence-gathering for thorny multi-layer bugs: `~/.claude/refs/gstack/investigate/SKILL.md`.

Full reference + rationalization table: `~/.claude/refs/superpowers/systematic-debugging/SKILL.md`.
