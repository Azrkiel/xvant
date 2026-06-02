---
name: xvant-review-exchange
description: Use for the two halves of a code-review conversation with a separate reviewer — requesting a review from a reviewer subagent (including before a merge), or processing review feedback you have received. Triggers include "request a review", "get this reviewed", "review before merge", "I got review feedback", "respond to this review", "address these comments".
---

# xvant-review-exchange

Two halves of one low-frequency exchange. Pick the mode from intent.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

## Mode: SEND — request a review (spine: superpowers requesting-code-review)
Dispatch a reviewer subagent with precisely-crafted context, never your full session history.
1. Get SHAs: `BASE_SHA` (e.g. `origin/main` or `HEAD~1`), `HEAD_SHA=HEAD`.
2. Dispatch a `general-purpose` reviewer subagent given: a brief description of what you built, the plan/requirements it should meet, and the BASE/HEAD SHAs. Ask for Strengths + Issues ranked Critical/Important/Minor + an assessment.
3. Act on feedback: fix Critical now, Important before proceeding, note Minor. Push back (with reasoning) if the reviewer is wrong.

Mandatory after each subagent task, after a major feature, and before merge. Full: `~/.claude/refs/superpowers/requesting-code-review/SKILL.md`.

## Mode: RECEIVE — process feedback (spine: superpowers receiving-code-review)
Technical evaluation, not emotional performance. Verify before implementing; ask before assuming.
- **Forbidden:** "You're absolutely right!", "Great point!", any gratitude or performative agreement, and implementing before verifying.
- **Instead:** restate the requirement, or just fix it and show the code ("Fixed. <what changed>").
- Unclear on any item? STOP and ask before implementing anything — items may be related.
- External reviewer suggestion: check it's correct for THIS codebase, doesn't break things, isn't YAGNI (grep for usage), works on all targets. Push back with technical reasoning if wrong; if it conflicts with the user's prior decisions, stop and discuss.
- Implement order: blocking → simple → complex, testing each individually.

Full: `~/.claude/refs/superpowers/receiving-code-review/SKILL.md`.
