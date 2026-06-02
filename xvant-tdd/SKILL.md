---
name: xvant-tdd
description: Use when implementing any feature or bugfix, before writing implementation code. Triggers on starting to build a function, fix a bug, or change behavior — write the test first, watch it fail, then minimal code.
---

# xvant-tdd

Write the test first. Watch it fail. Write minimal code to pass.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Core principle:** If you didn't watch the test fail, you don't know if it tests the right thing. Violating the letter of the rules is violating the spirit.

## The Iron Law
```
NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST
```
Wrote code before the test? Delete it — don't keep it as "reference", don't "adapt" it. Implement fresh from tests.

## Red-Green-Refactor
1. **RED** — one minimal test of real behavior (clear name, one thing, no mocks unless unavoidable).
2. **Verify RED** — run it, confirm it FAILS for the expected reason (feature missing, not a typo). Passes immediately? You're testing existing behavior — fix the test.
3. **GREEN** — simplest code that passes. No extra features, no premature abstraction (YAGNI).
4. **Verify GREEN** — run it; output pristine (no errors/warnings); other tests still pass.
5. **REFACTOR** — remove duplication, improve names; stay green; add no behavior.
6. Repeat for the next behavior.

## Coverage target
Aim for **80-90%** meaningful coverage, not 100%. Cover behavior, edge cases, and error paths; don't write hollow tests chasing a number.

## Exceptions (ask first)
Throwaway prototypes, generated code, config files. "Skip TDD just this once" is a rationalization — stop.

Bug fix? Write a failing test that reproduces it, then fix. The test proves the fix and prevents regression. If a test fails for an unexplained reason (not the expected RED, or a fix doesn't take), STOP and hand to `xvant-debug` rather than stacking fixes. Full reference + rationalization table: `~/.claude/refs/superpowers/test-driven-development/SKILL.md`.
