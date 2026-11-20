---
name: xvant-debug
description: "Use when a bug, crash, unexpected result, flaky test or unexplained failure needs diagnosis before a fix."
---

Before editing, draw actual versus expected flow with `~/.claude/skills/_shared/ascii-diagram.md`.

1. Read the full error, reproduce consistently, inspect recent changes. Instrument each component boundary and trace the first bad value to its source.
2. Read a working analogue and its dependencies; list differences.
3. State one causal hypothesis. Vary one thing in the smallest test. Revise if disproved.
4. Reproduce with a failing xvant-tdd test, fix the root cause and verify. After three failed fixes, stop and reconsider architecture.

Prioritize multiple issues: `~/.claude/refs/anthropic-skills/engineering/triage/SKILL.md`. Quick single-bug diagnosis: `~/.claude/refs/anthropic-skills/engineering/diagnose/SKILL.md`. Multilayer investigation: `~/.claude/refs/gstack/investigate/SKILL.md`. Full systematic procedure: `~/.claude/refs/superpowers/systematic-debugging/SKILL.md`.
