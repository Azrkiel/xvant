---
name: xvant-handoff
description: "Use when asked to write a handoff, hand off work, wrap up the session or save state to resume with another agent. Human retrospectives use xvant-retro."
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
13. Next steps — choose the next meaningful milestone from the user's remaining scope. State the observable outcome, first executable action, dependencies or blockers, and the check that proves completion. Group related steps under that outcome. For example, carry a row-validation fix from parser output through the upload screen and verify that every error shows its original row number. If only a small fix remains, assign it. If work is complete or blocked, state the evidence or the exact unblock condition.

## Prompt for the next agent

After saving the handoff, end the reply with one copy-ready prompt in a fenced text block. Address the incoming agent directly. Fill in the following details from the checkout so the prompt works in a fresh session.

- **Start here.** Identify the repository, branch/worktree and exact saved handoff path. Give a short, ordered reading list with verified paths and what to learn from each (plan or decisions, implementation entry point, relevant tests). Flag any uncommitted files available only in the current worktree.
- **Deliver this outcome.** Put the milestone, first action, blockers and acceptance check from section 13 in the prompt itself. Tell the agent to carry the work through verification and report the result.
- **Delegate deliberately.** Include the main plan path and open task IDs, or tell the recipient to write those rows before spawning if the work has no plan yet. Tell each worker to check off its own row with evidence per `~/.claude/skills/_shared/parallel-dispatch.md`. Carry forward any pending integration checks. Use Haiku for focused lookups or a bounded check and Sonnet for implementation and integration. Give each worker its inputs, owned paths and expected result. Parallelize only independent assignments with disjoint writes. The receiving agent integrates the results and runs the acceptance check. Escalate only the unresolved part to a stronger model when the assigned tier hits a concrete obstacle. Include what it tried and the evidence it needs help interpreting.
- **When Claude is receiving (or the recipient is unknown),** include a Claude-specific instruction to invoke the installed `xvant-codex` skill for a named, bounded Codex assignment, such as independently checking the milestone's acceptance case. Specify the inputs and result Claude should verify. If the skill or a worker tier is unavailable, use the available worker or perform that assignment locally.
- **At the next handoff,** instruct the recipient to save the updated state and output a fresh copy-ready prompt with the new handoff path, required reading, remaining outcome and delegation plan.
