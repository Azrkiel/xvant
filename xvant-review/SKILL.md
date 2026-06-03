---
name: xvant-review
description: Use ONLY when explicitly asked to review the current code or diff yourself, right now — "review this", "review the diff", "code review", "review PR #". Reviews changed code for correctness bugs and reuse/simplification cleanups. Does NOT self-trigger on a bare "done" (xvant-verify orchestrates that and calls this). Deep-review `swarm` mode, also explicit-only, fires on "deep review" / "swarm review": a local zero-context multi-agent fan-out + tiered verifier (independent opinions, free, run locally — not externally verified). To dispatch a separate reviewer or review before a merge, use xvant-review-exchange.
---

# xvant-review

Review changed code for correctness bugs and quality. Explicit-invoke only.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Findings readable.

**Spine:** the built-in `/code-review` command. Run it on the current diff (effort low→max; `--comment` to post inline on a PR; `--fix` to apply findings). For a GitHub PR specifically, use the built-in `/review`.

(The namespaced `code-review:code-review` plugin command was disabled along with its plugin; the built-in `/code-review` and `/review` survive and are what this skill uses.)

## Mode: DX review (graft, gstack devex-review)
When the concern is developer experience — API ergonomics, naming, onboarding friction, error messages — run the DX lens: `~/.claude/refs/gstack/devex-review/SKILL.md`.

## Deep review — swarm mode (explicit-invoke only)
A deeper local pass above the base review. **Explicit-invoke only** — never self-fires; ask for it by name (`swarm`, "deep review", "swarm review"). Base `/code-review` stays the default. Free and fully local — no paid or cloud step.

**Honest scope:** swarm fans out zero-context reviewers that produce independent **opinions**, then partially verifies them. It is NOT cloud-grade verified-finding review. Confirmed findings are labeled by how they were confirmed; everything else is surfaced as **"suspected, unconfirmed."** Never dress an opinion up as a fact.

**Through-line:** read once, run cheap checks before expensive ones, never verify the same thing twice.

Run these six stages in THIS order — the ordering is the optimization, do not reorder:

1. **DIGEST (read once).** One pre-pass reads the diff a single time and emits a compact map (files, per-file change type, touched symbols, hunk ranges) — follow `~/.claude/skills/_shared/diff-digest.md`. Downstream agents get this digest plus only the hunks they need, never the full raw diff each.
2. **FAN-OUT (parallel, fresh context).** Dispatch the four reviewer lenses concurrently via `~/.claude/skills/_shared/parallel-dispatch.md`, each a zero-context subagent returning **suspected findings only**:
   - `xvant-review-correctness` — logic, error handling, regressions
   - `xvant-review-security` — injection, authz, secret leakage, crypto misuse
   - `xvant-review-concurrency` — races, shared state, edge/boundary cases
   - `xvant-review-architecture` — coupling, layering, testability, API design; **always sees the whole diff** (the guaranteed catcher for cross-cutting issues). The other three get digest + their hunks.
3. **DEDUP (before any verification).** Merge overlapping/duplicate findings across reviewers by a stable key (`file:line` + claim) so each suspect is investigated **once**, not N times.
4. **BATCH TIER-1 (cheap, once).** Run the repo's EXISTING tooling a single time — test suite, typecheck, lint, build — and check the whole deduped list against that one run. Deterministic and trusted. Confirm or kill as many findings as possible here. No new code.
5. **SELECTIVE TIER-2 (only what tier-1 could not reach).** Hand the still-open findings to `xvant-review-verifier`, high-severity first, **capped** (default 5; stop at the cap). It writes a minimal repro test per finding and runs it to confirm/refute.
   > Tier-2 EXECUTES CODE. It must run in an **isolated git worktree** (`xvant-worktree`, or native Agent `isolation: "worktree"`) with a **sandboxed exec environment: NO secrets mounted, NO network**. Tier-2 must NEVER run without that isolation — if it can't be guaranteed, skip tier-2 and leave the finding "suspected, unconfirmed."
6. **SYNTHESIZE (one final pass).** `xvant-review-verifier` produces the report: **tier-1-confirmed and tier-2-confirmed findings first, by severity**, each with its evidence; then everything unverifiable surfaced honestly as **"suspected, unconfirmed,"** naming the reviewer that raised it. No opinions dressed as facts.

**Agents** (`~/.claude/agents/xvant-review-*.md`; register after a Claude Code restart):
- The four reviewers — read-only tools (Read/Grep/Glob), pinned to a **cheap** model: proposing candidates doesn't need the big model.
- `xvant-review-verifier` — the only agent that executes code (Bash + worktree); pinned to the **expensive** model: tier-2 judgment and synthesis need it.

The fan-out and digest mechanics live in `_shared/` (referenced above), so `xvant-execute` can reuse the same infra without duplication.

## Acting on findings
Fix Critical immediately, Important before proceeding, note Minor. Push back with technical reasoning if a finding is wrong for this codebase.

Sequenced as step 2 of `xvant-verify`. For requesting a review from / responding to a separate reviewer, use `xvant-review-exchange`. Security-specific review: `xvant-security`. Quality-only cleanup: `xvant-simplify`.
