---
name: xvant-ultra-plan
description: Use ONLY when explicitly asked to bulletproof a plan with a cross-model debate — "/xvant-ultra-plan", "ultra plan", "bulletproof this plan", "debate this plan with codex". Orchestrates Claude planning, Claude self-critique, an independent Codex critique, a neutral judge, and a reconciled final plan. Expensive and explicit-invoke only. For a normal plan use xvant-plan.
---

# xvant-ultra-plan (orchestrator)

A cross-model debate that hardens a plan before any code is written. Claude proposes, Claude attacks its own plan, Codex independently attacks it from a different model's perspective, a neutral stake-free judge rules on the disagreements, and Claude synthesizes the final reconciled plan. Explicit-invoke only — this is the most expensive thing in the kit.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Codex raw output and the judge's rulings are shown verbatim.

**Announce:** "Using xvant-ultra-plan — Claude and Codex will debate this plan, then a neutral judge decides."

## Standing directive (applies to every step)

**Choose the hard route: the most complete and robust end product — NOT the most complex.** Completeness and robustness win ties. But a genuinely 10x-simpler approach that produces a better end product can still win on merit — "hard" means best outcome, and sometimes the best outcome is simpler. Over-engineering is a failure of this directive, not a fulfillment of it. (This is the kit's boil-the-ocean/completeness principle, bounded by the Jobs "focus as subtraction" instinct already in the CEO review.)

## Honesty is load-bearing

This whole skill is worthless if the models perform agreement. Each step below carries explicit anti-sycophancy framing. Enforce it.

## Step 1 — Claude drafts the plan

Invoke `xvant-plan` in full. Output must include the plan, its **ASCII diagram** (data flows, inputs/outputs, user flows, error states), the tech stack, and the spec/requirement mapping. Save to `docs/plans/YYYY-MM-DD-<feature>.md`.

## Step 2 — Claude self-critique (adversarial, not self-graded)

Invoke `xvant-plan-review` (eng rigor + ★ 10x CEO). Then produce a **self-weakness list** framed as an attack, NOT a confession:

> "Write the strongest possible case that THIS plan fails in production. You are not defending it — you are trying to kill it. For each weakness: what breaks, why, and what assumption or decision it traces back to. Then, separately, state why you made each shaky choice anyway."

Inversion is the point — "argue it fails" gets past the self-protection that "what are you unsure about?" triggers. Record this as **Claude's weakness list** (do not send it to Codex).

## Step 3 — Codex independent critique (unanchored)

Hand Codex the **plan + ASCII diagram + spec** — NOT Claude's weakness list. Anchoring Codex to Claude's confessed weaknesses makes it miss the unconfessed one, which defeats the second model. Codex finds shaky parts independently.

Preflight: `which codex 2>/dev/null || echo NOT_FOUND`. If `NOT_FOUND`: tell the user to install (`npm install -g @openai/codex`) + `codex login`, and stop (you were asked for the cross-model debate explicitly — don't fake it). Detect base branch if needed.

Run (5-min timeout, `timeout: 300000`):

```
codex exec "You are a fiercely competitive, brutally honest staff engineer reviewing another engineer's implementation plan. Be adversarial but HONEST: where the plan is right, say so plainly — do not manufacture disagreement to look smart. Review through three lenses: (1) FEASIBILITY — will this actually work? what are the unstated assumptions? (2) COMPLETENESS — what's missing: error paths, edge cases, race conditions, failure modes, observability? (3) SIMPLICITY — is there a 10x-simpler approach that yields a BETTER end product (not just less code)? For each shaky part you find, propose the solution you would use instead, and defend it. Where you'd diverge from this plan, say how and why. Do NOT write a whole rival plan — give me your divergences and your reasoning. THE PLAN AND DIAGRAM:\n<paste plan + ASCII diagram + spec>" -s read-only -c 'model_reasoning_effort="xhigh"' --enable web_search_cached
```

Present Codex output verbatim in a `CODEX SAYS (plan critique)` block. Record this as **Codex's findings**.

## Step 4 — Surface the gap

Explicitly diff the two lists:

```
GAP ANALYSIS:
  Both caught:        <issues on both Claude's and Codex's lists>
  Only Claude caught: <unique to Claude's self-critique>
  Only Codex caught:  <unique to Codex — the "didn't know it didn't know" set>
```

The **Only Codex caught** column is the highest-value output of this skill — call it out.

## Step 5 — Neutral judge (fresh, stake-free subagent)

Spin up a **fresh general-purpose Claude subagent** that did NOT see Steps 1–4 happen. It has no plan to defend. Give it ONLY: {the spec, each contested point, Claude's position on it, Codex's position on it}. It rules on **contested points only** — where they already agree, there is nothing to judge.

Subagent prompt framing:

> "You are a neutral technical judge. You did not write either position and have no plan to defend — judge purely on which produces the most complete, robust end product (the hard route), allowing that a genuinely simpler approach can be better. Be honest: you may take the best of both. For each contested point, rule:
>
> - **CLAUDE** — Claude's approach wins (reason)
> - **CODEX** — Codex's approach wins (reason)
> - **BOTH WRONG → <alternative>** — neither is right; here's the better approach (reason)
> - **MERGE → <synthesis>** — take the best of each; here's the combined approach (reason)
>   One line of reasoning per ruling."

The judge may request **exactly one rematch** on a single point if it genuinely cannot rule — not a general re-debate. Output a **ruling ledger**: each contested point → verdict + reason.

## Step 6 — Claude synthesizes the final plan

Claude folds the judge's rulings into the plan. **The judge's verdicts (including MERGE and alternative rulings) are authoritative — do not re-litigate them.** Rewrite affected steps; **regenerate the ASCII diagram** if the flow changed. Anything the judge deferred or couldn't resolve becomes an explicit `## OPEN QUESTIONS` section routed to the user (mirrors eng-review's TODOS discipline) — the plan still proceeds, the questions ride along visibly.

Save the reconciled plan over the Step 1 file. Then hand off: offer `xvant-execute` (or subagent-driven execution). Verification happens later as a separate bookend — `xvant-verify` (optionally cross-model via `xvant-review-exchange`) after code exists. Verify is NOT part of this skill; there's no code to verify at plan time.

## Cost note

Every Codex call runs at `model_reasoning_effort="xhigh"` — the most ChatGPT-plan usage you can spend per call. On Plus this can hit the weekly window fast. If you're approaching the limit, drop the Step 3 call to `"high"`. Reserve `xhigh` for the plans that truly warrant it; use plain `xvant-plan` for routine work.

## Invariants

- **Codex is read-only** and **unanchored** (never sees Claude's weakness list in Step 3).
- **Judge is stake-free** (fresh subagent, never the author of either position) and rules on contested points only, one rematch max.
- **One round by default.** No loop-until-converge — that thrashes and drains the weekly limit.
- **Honesty over agreement** at every step; concede when the other side is right.
- **Hard route = most complete + robust, not most complex.**
