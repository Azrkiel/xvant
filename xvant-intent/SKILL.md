---
name: xvant-intent
description: "Use when asked to build end to end, hands-off, “run with it” or “without asking me” after one interview. Checkpointed plans use xvant-plan."
---

Understand once, then steer from an approved charter. Label every requirement, decision and feature `user` (exact quote), `drafted` (user selected it) or `intent` (your decision and the goal it serves).

For independent readers, critics, builders or proxy voters, track each assignment in `INTENT.md` by ID and apply the read-only result rule in `~/.claude/skills/_shared/parallel-dispatch.md`. Preserve the inputs and independent response required by each exercise.

**Understand.** Follow `references/understand.md`. Learn why, taste, principles, trade-offs and yes/no examples. For gaps, propose a specific answer with assumptions and 2–3 options, one question per turn. Collect human inputs. Settle accounts/identity, storage/migrations, external or paid services, credentials, spending, publishing and destructive changes. Get one charter approval.

State the depth and allow the user to adjust it:

| Ambition | Interview | Default addition budget |
|---|---|---|
| Throwaway | Job, Good looks like, Fails if; 3 calibration items | None |
| Personal | Full North Star, 3 principles, 5 items | Small |
| Shared | Full North Star, principles, trade-offs, 6–8 items | Small |
| Product | Full interview | Moderate |

**Steer.** Tell the user the next contact is the report unless a charter stop condition occurs. Follow `references/steer.md`. Use real acceptance-command output. Finish all must-haves before additions. Each addition must serve a named goal/principle, fit ambition and budget, respect non-goals, remain isolated and reversible, avoid one-way doors and pass the proxy vote. For an unforeseen one-way decision, take a reversible path or stop. Otherwise decide, log and continue. Disclose non-independent proxies/readers/builders and halve the addition budget.

**Resume.** Keep `INTENT.md` (ledger and run state), `CHARTER.md` and `INTENT-REPORT.md` in the project. Reference `@CHARTER.md` from Claude instructions or “Read CHARTER.md before any work” from AGENTS.md. On user edits or new input, update ledger and charter, log and continue. Reopen Understand for a one-way decision.

Use the relevant reference as needed: `references/ledger.md`, `references/north-star.md`, `references/critics-and-decisions.md`, `references/charter.md`, `references/phase-plan.md`. Use `templates/INTENT.md`, `templates/charter.md` and `templates/report.md` for the three state files. The G1 lexicon, optional G4 reader agreement and proxy calibration checks live in `scripts/lexicon.py`, `scripts/agreement.py` and `scripts/proxy_check.py`.

Source: https://github.com/Azrkiel/Intent (`skills/intent/`). Its `backend/tests/test_skill_scripts.py` guards the lexicon and agreement copies.
