---
name: xvant-plan
description: "Use when turning approved requirements into a written, multi-step implementation plan before coding."
---

Announce “Using xvant-plan to write the implementation plan.” Write for an engineer new to the repo.

- Header: one-sentence goal, 2–3 architecture sentences, tech stack. Include the flow and failure paths using `~/.claude/skills/_shared/ascii-diagram.md`.
- Map each file to a responsibility. Group related changes. Write 2–5 minute checkbox steps: failing test, observe failure, minimal code, green tests, commit. Include actual code, exact commands and expected output.
- Map every requirement to a task. Resolve placeholders and undefined or inconsistent names. Save to `docs/plans/YYYY-MM-DD-<feature>.md` or beside the work outside Git.
- For autonomous plan review, use `~/.claude/refs/gstack/autoplan/SKILL.md` for CEO, design and engineering critique.
- Offer checkpointed xvant-execute or fresh subagents per task, then wait for the user's choice.
