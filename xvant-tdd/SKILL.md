---
name: xvant-tdd
description: "Use when implementing a feature, behavior change or bugfix that needs a failing test before production code."
---

Start with a failing test for each behavior or bug. Delete premature implementation and write it fresh after RED.

1. RED: one named test of real behavior; mock only when unavoidable. Run it and observe failure for the expected missing behavior. If already green, correct the test.
2. GREEN: write the smallest implementation. Run the test and suite; check for clean output.
3. REFACTOR: improve names or remove duplication while green. Repeat per behavior.

Aim for 80–90% meaningful coverage including edges and errors. Ask before exceptions for prototypes, generated code or configuration. Send unexplained failures to xvant-debug before further fixes. Full procedure: `~/.claude/refs/superpowers/test-driven-development/SKILL.md`.
