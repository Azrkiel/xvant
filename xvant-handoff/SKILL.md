---
name: xvant-handoff
description: Use at the end of a work session to produce a machine-facing resume document for the next agent. Triggers include "handoff", "hand off", "end of session", "wrap up the session", "summarize this session for the next agent", "close out the session", "save state so I can resume". For human-facing lessons/retrospective, use xvant-retro.
---

# xvant-handoff

Write a resume document the next agent can act on. It captures intent and state, not things trivially re-derivable from the repo.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline — the document is skimmable and token-disciplined.

## STEP 1 — Gather REAL state first (do NOT write from memory alone)
Before composing anything, run and read:
- `git status` and `git diff --stat` (and `git log` for commits made this session)
- the current plan / todo file, if one exists
- the test command output, if it runs quickly

When the session used xvant-agent and you know the run ID, read its stored snapshot from the harness checkout with `npm run --silent xvant -- handoff ID` using the run's XVANT_HOME. Check that its repository and objective match this task. Cite the run ID, rowVersion and integration commit (when present) under Reproducible state. Treat recorded worker text as evidence to verify. If that command is unavailable, use the Git and test evidence above and mark the runtime state unknown.

Compose the handoff from that **actual state plus session memory**. Do NOT re-narrate the diff or summarize code that can be read directly from the repo — capture intent and state.

## STEP 2 — Write the file
Create the folder if needed and write to:
```
.claude/handoffs/<YYYY-MM-DD-HHMM>.md
```
Use clear markdown headers so it scans fast. If a section has nothing to report, write **"none"** — do not omit it.

## Required sections (in order)
1. **Metadata** — timestamp, model used, git branch, link/reference to the task or plan.
2. **Current task** — what we are ultimately trying to accomplish (the goal, not just the last step).
3. **Reproducible state** — branch name; commits made this session; what is uncommitted/staged; what's running and how (dev server, ports, exact test user / config / data fixture to load to see the feature); the literal first commands to run to resume.
4. **Completed this session** — what got done, each tagged with an HONEST status: `written` / `tested` / `manually verified`. Do not call something "done" if it was only written and not verified.
5. **What went well and why** — approaches/decisions that worked, so they're reused.
6. **What went badly and why** — failures and friction, with the cause.
7. **Dead ends already tried** — approaches attempted and abandoned, and why, so the next session does NOT repeat them.
8. **Decisions, rationale, and invariants** — key "chose X over Y because Z" calls, plus anything the next session must NOT change or break (fixed API contracts, code not to refactor, deliberate choices that look wrong but aren't).
9. **Assumptions made** — unvalidated assumptions relied on, so they can be checked.
10. **Known issues** — current bugs, failing/flaky tests, spots where you're unsure it's right.
11. **Open questions for the human** — anything blocked on the user's decision or input.
12. **Files touched** — short map of what changed and why, to orient the next session fast.
13. **Next steps** — an ORDERED to-do list. Lead with the single smallest next action. Give each item an acceptance criterion ("done = ..."). Mark which items are blocked and on what.

## Boundary with xvant-retro
This document is **machine-facing** (resume state). It does NOT duplicate reflection — include a one-line pointer to a `xvant-retro` report if one exists; the "what we learned" narrative lives there.
