---
name: xvant-review
description: Use ONLY when explicitly asked to review the current code or diff yourself, right now — "review this", "review the diff", "code review", "review PR #". Reviews changed code for correctness bugs and reuse/simplification cleanups. Does NOT self-trigger on a bare "done" (xvant-verify orchestrates that and calls this). Deep-review escalation, also explicit-only, fires on "deep review", "swarm review", "ultrareview": `swarm` = local zero-context multi-agent fan-out + tiered verifier (independent opinions, not cloud-verified); `ultra` = the billed cloud `/code-review ultra` the user launches. To dispatch a separate reviewer or review before a merge, use xvant-review-exchange.
---

# xvant-review

Review changed code for correctness bugs and quality. Explicit-invoke only.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Findings readable.

**Spine:** the built-in `/code-review` command. Run it on the current diff (effort low→max; `ultra` for deep multi-agent cloud review; `--comment` to post inline on a PR; `--fix` to apply findings). For a GitHub PR specifically, use `/code-review ultra <PR#>` or the built-in `/review`.

(The namespaced `code-review:code-review` plugin command was disabled along with its plugin; the built-in `/code-review` and `/review` survive and are what this skill uses.)

## Mode: DX review (graft, gstack devex-review)
When the concern is developer experience — API ergonomics, naming, onboarding friction, error messages — run the DX lens: `~/.claude/refs/gstack/devex-review/SKILL.md`.

## Deep review (explicit-invoke modes)
Escalation ladder above the base review, mirroring caveman lite→full→ultra. **Explicit-invoke only** — these never self-fire; ask for them by name. Base `/code-review` stays the default.

`base` (spine) → `swarm` (local, free, unverified fan-out) → `ultra` (cloud, billed, verified).

### Mode: ultra (cloud)
The real deep multi-agent review: `/code-review ultra` (or `/code-review ultra <PR#>` for a GitHub PR). Runs in Anthropic's cloud, is **billed**, and **only the user can launch it** — it cannot be triggered from here. This is the top of the ladder: verified findings, not opinions. Use `swarm` below as the local stand-in when spending isn't wanted.

### Mode: swarm (local DIY fan-out)
Honest scope: **fan-out WITHOUT cloud-grade verification.** It produces independent opinions from zero-context reviewers, NOT Anthropic-verified findings. Treat output as leads to confirm, not conclusions.

Mechanism — reuse `xvant-execute`'s **parallel-dispatch** infra (`~/.claude/skills/xvant-execute/SKILL.md` → "Mode: parallel dispatch"), but point the agents at the **diff** with reviewer personas instead of implementer personas. Each runs in its own fresh context window:
- `xvant-review-correctness` — logic, error handling, regressions
- `xvant-review-security` — injection, authz, secret leakage, crypto misuse
- `xvant-review-concurrency` — races, shared state, edge/boundary cases
- `xvant-review-architecture` — coupling, layering, testability, API design

Agent files live in `~/.claude/agents/xvant-review-*.md`: scoped read-only tools (Read/Grep/Glob — no exec), pinned models — judgment lanes (correctness, architecture) on sonnet, pattern-scan lanes (security, concurrency) on haiku. Reviewers are breadth-cheap idea generators; trust comes from the verifier below, not the reviewer's model size. (Like the rest of the kit, the agents register after a Claude Code restart.)

Collect findings, dedupe, then run the **tiered verifier**. Reviewers are read-only and never execute code — only tier 2 does, under isolation.

#### Tiered verifier
Every claim gets the cheapest sufficient check; nothing is reported as fact until verified or labeled.

- **Tier 1 — existing trusted tools (free, deterministic).** Run the repo's EXISTING tests / typecheck / lint / build against each claim. Anything a tier-1 tool can confirm or refute is settled here. No new code written.
- **Tier 2 — isolated repro (only for findings tier 1 cannot reach).** Spawn a repro-writing verifier in an **isolated git worktree** (use `xvant-worktree`, or the native Agent `isolation: "worktree"`) with **sandboxed exec, NO secrets, and NO network**.
  > Tier 2 EXECUTES CODE. It must never run outside that isolation — no secrets in the environment, no network egress, throwaway worktree discarded after. If isolation cannot be guaranteed, do NOT run tier 2: drop the finding to tier 3 instead.
- **Tier 3 — unverifiable.** Anything tiers 1–2 cannot settle is surfaced explicitly labeled **"unverified opinion"**, naming the reviewer and its reasoning. Never present a tier-3 item as a confirmed bug.

#### Report
End with two clearly separated lists: **verified findings** (tier 1/2, each with its evidence) and **unverified opinions** (tier 3). Note which reviewer raised each. State the honest caveat plainly: swarm is independent opinion plus local verification, not a cloud-verified review — escalate to `ultra` for that.

## Acting on findings
Fix Critical immediately, Important before proceeding, note Minor. Push back with technical reasoning if a finding is wrong for this codebase.

Sequenced as step 2 of `xvant-verify`. For requesting a review from / responding to a separate reviewer, use `xvant-review-exchange`. Security-specific review: `xvant-security`. Quality-only cleanup: `xvant-simplify`.
