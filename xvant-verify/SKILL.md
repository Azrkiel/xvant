---
name: xvant-verify
description: Use when about to claim work is done, fixed, complete, or passing — before committing, pushing, or opening a PR. Triggers include "done", "is this finished", "wrap this up", "is it complete", "ready to commit?". This is the end-of-task orchestrator; it sequences the review, security, and cleanup passes. For integrating or releasing finished work, use xvant-ship.
---

# xvant-verify (orchestrator)

The single skill that fires on "I'm done." Evidence before claims, then sequence the other end-of-task passes so they don't compete.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

## The Iron Law (spine: superpowers verification-before-completion)
```
NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE
```
If you haven't run the verifying command in this message, you cannot claim it passes. Before any "done/passing/fixed" or expression of satisfaction: identify the command that proves it → run it fresh → read full output + exit code → only then state the claim WITH the evidence. "Should work", "I'm confident", "linter passed" are not evidence.

## Orchestration sequence
On a bare "done / is this finished / wrap up", run these in order (don't make the user invoke each):

1. **Runtime check** — does it actually run/work? Use the built-in `/verify` (run the app/feature and observe real behavior), not just unit tests.
2. **Code review** — invoke `xvant-review` on the diff. Fix Critical/Important before proceeding. At a pre-merge gate it MAY escalate to xvant-review's `swarm` mode for a deeper pass — explicit choice, never automatic on a bare "done".
3. **Security pass** — invoke `xvant-security` on the change.
4. **Cleanup pass** — invoke `xvant-simplify` for reuse/simplification.

Report each pass's result with evidence. Only after all four: state the work is complete. Then offer `xvant-ship`.

`xvant-review`, `xvant-security`, and `xvant-simplify` remain separate, invokable skills — this skill calls them so they don't all self-trigger on the generic "done". Full reference: `~/.claude/refs/superpowers/verification-before-completion/SKILL.md`.
