---
name: xvant-handoff
description: "Use when asked to hand off, wrap up the session or save state to resume with another agent. Human retrospectives use xvant-retro."
---

Read `git status`, `git diff --stat`, this session's commits, the current plan and quick test results. Combine these with session intent. Link to retrievable facts and any xvant-retro report.

For a known xvant-agent run, execute `npm run --silent xvant -- handoff ID` in the harness checkout with its XVANT_HOME. Match repository and objective. Record ID, rowVersion and available integration commit under Reproducible state. Verify worker claims. If unavailable, mark runtime state unknown and use Git/test evidence.

Write `.claude/handoffs/<YYYY-MM-DD-HHMM>.md`, creating the directory as needed. Keep these headings in order. Write “none” for empty sections.

1. Metadata — timestamp, model, branch, task/plan link.
2. Current task — overall goal.
3. Reproducible state — branch, commits, staged/unstaged work, running services, ports, test fixture/config and first resume commands.
4. Completed this session — tag each item written, tested or manually verified.
5. What went well and why.
6. What went badly and why.
7. Dead ends already tried — approach and reason.
8. Decisions, rationale, and invariants — alternatives and contracts to preserve.
9. Assumptions made — what remains unvalidated.
10. Known issues — failures, flakes and uncertainties.
11. Open questions for the human.
12. Files touched — purpose of each change.
13. Next steps — smallest action first, acceptance criterion per item and blockers.
