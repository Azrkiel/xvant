---
name: xvant-review
description: Use ONLY when explicitly asked to review the current code or diff yourself, right now — "review this", "review the diff", "code review", "review PR #". Reviews changed code for correctness bugs and reuse/simplification cleanups. Does NOT self-trigger on a bare "done" (xvant-verify orchestrates that and calls this). To dispatch a separate reviewer or review before a merge, use xvant-review-exchange.
---

# xvant-review

Review changed code for correctness bugs and quality. Explicit-invoke only.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Findings readable.

**Spine:** the built-in `/code-review` command. Run it on the current diff (effort low→max; `ultra` for deep multi-agent cloud review; `--comment` to post inline on a PR; `--fix` to apply findings). For a GitHub PR specifically, use `/code-review ultra <PR#>` or the built-in `/review`.

(The namespaced `code-review:code-review` plugin command was disabled along with its plugin; the built-in `/code-review` and `/review` survive and are what this skill uses.)

## Mode: DX review (graft, gstack devex-review)
When the concern is developer experience — API ergonomics, naming, onboarding friction, error messages — run the DX lens: `~/.claude/refs/gstack/devex-review/SKILL.md`.

## Acting on findings
Fix Critical immediately, Important before proceeding, note Minor. Push back with technical reasoning if a finding is wrong for this codebase.

Sequenced as step 2 of `xvant-verify`. For requesting a review from / responding to a separate reviewer, use `xvant-review-exchange`. Security-specific review: `xvant-security`. Quality-only cleanup: `xvant-simplify`.
