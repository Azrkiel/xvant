# Registry and lineage

## Operating principles
- **Skills compete at trigger time, not runtime.** Goal is trigger distinctness, not minimum file count. Each description uses distinct keywords; explicit-only skills say so.
- **Spine + graft.** One winning base per skill; overlapping skills folded in as named modes; redundant ones dropped.
- **Define once, reference everywhere.** Shared steps live in `~/.claude/skills/_shared/` (e.g. `ascii-diagram.md`) and are referenced, never copy-pasted.
- **Caveman-lite is the global baseline** (`~/.claude/CLAUDE.md`), always on, with carve-outs for humanizer, human prose, and safety warnings.
- **★ Garry signatures preserved:** office-hours decomposition (in `xvant-brainstorm`) and the 10x / 10-star CEO review (in `xvant-plan-review`).
- **◆ ASCII diagram step** grafted into exactly four: `xvant-plan`, `xvant-execute`, `xvant-architecture`, `xvant-debug`.
- **`humanizer` is untouched** and exempt from the baseline.

## Registry (roughly lifecycle order)
| Skill | Spine | Grafted modes |
|---|---|---|
| xvant-brainstorm | superpowers brainstorming | ★ office-hours (startup six-Q + builder), spec rigor |
| xvant-plan ◆ | superpowers writing-plans | autoplan autonomous mode |
| xvant-plan-review | gstack plan-eng-review | ★ 10x CEO review, plan-design/devex, plan-tune |
| xvant-to-work | anthropic to-prd | to-issues |
| xvant-tdd | superpowers test-driven-development | (80–90% coverage target) |
| xvant-execute ◆ | superpowers executing-plans | subagent-driven, parallel-dispatch, gstack pair-agent |
| xvant-worktree | superpowers using-git-worktrees | — |
| xvant-debug ◆ | superpowers systematic-debugging | triage, diagnose quick-path, gstack investigate |
| xvant-review | built-in code-review | gstack devex-review; deep-review mode `swarm` (local zero-context multi-agent fan-out + tiered verifier) — explicit-invoke only |
| xvant-review-exchange | superpowers requesting + receiving | merged send/receive modes |
| xvant-verify | superpowers verification-before-completion | ORCHESTRATOR → runtime check → review → security → simplify |
| xvant-security | built-in security-review | gstack cso (explicit-invoke only) |
| xvant-simplify | built-in simplify | — (explicit-invoke only) |
| xvant-ship | superpowers finishing-a-development-branch | gstack ship / land-and-deploy / setup-deploy |
| xvant-release-guard | gstack canary | freeze / unfreeze / guard / health |
| xvant-architecture ◆ | improve-codebase-architecture | zoom-out overview |
| xvant-write-skill | superpowers writing-skills | skill-creator, gstack skillify, write-a-skill, plugin-dev |
| xvant-extend | mcp-server-dev / hook-development+hookify / plugin-dev | build-mcp-app/mcpb (merged: MCP/hook/plugin) |
| xvant-configure | built-in update-config | fewer-permission-prompts, keybindings-help, automation-recommender |
| xvant-claude-md | claude-md-improver | built-in init |
| xvant-design | frontend-design | gstack design-consultation / html / review |
| xvant-browse | gstack browse | scrape, setup-browser-cookies |
| xvant-docs | gstack document-generate | document-release, make-pdf, landing-report, edit-article |
| xvant-second-brain | second-brain | obsidian-vault reference |
| xvant-study | anthropic grill-me | grill-with-docs, gstack learn |
| xvant-handoff | gstack context-save/restore + custom 13-section spec | next-agent prompt with required reading, a verifiable milestone and model assignments; links to retro |
| xvant-repo-guard | anthropic git-guardrails | setup-pre-commit, gstack careful/guard/redact |
| xvant-prototype | anthropic prototype | (throwaway; relaxes TDD) |
| xvant-hackathon | original (field notes from two 36-hour builds) | modes: prep, submit; overrides plan / tdd / verify until submission; reuses `_shared/parallel-dispatch.md` |
| xvant-intent | original (port of the Intent app's method, Azrkiel/Intent) | two stages: Understand (only stage that asks) → Steer (hands-off build, decision policy, aligned additions gated by a 3-proxy vote, stop conditions, report); bundled `scripts/` (lexicon, reader agreement, proxy check) |
| xvant-retro | session-report | gstack retro (human-facing; owns reflection) |
| xvant-schedule | built-in schedule | built-in loop |
| xvant-caveman | built-in caveman (full/ultra) | escalates the lite baseline |

`_shared/` references (no trigger): `ascii-diagram.md` (◆ flow diagram) · `diff-digest.md` (read-diff-once pre-pass) · `parallel-dispatch.md` (main-plan task assignment, worker checkoff and integration). The review swarm uses the digest and the read-only dispatch path.

## Collisions resolved
- **End-of-task pile** (verify/review/security/simplify all fired on "done"): `xvant-verify` is the sole "done" trigger and sequences the other three; those three are explicit-invoke only.
- **Session-end pair** (handoff vs retro): split by audience — `xvant-handoff` = machine-facing resume state; `xvant-retro` = human-facing lessons. Handoff links to retro, never duplicates reflection.
- **Timeboxed-build pair** (hackathon vs prototype): split by judges and a clock — `xvant-hackathon` = a judged demo build with a deadline (plans the whole event, owns the word "hackathon"); `xvant-prototype` = an untimed spike that answers one question. While `xvant-hackathon` is active it outranks `xvant-plan`, `xvant-tdd` and `xvant-verify`; its honesty line is not relaxed.
- **Idea-to-build trio** (intent vs brainstorm vs plan): split by who decides during the build — `xvant-brainstorm` = explore whether and what to build, with the user; `xvant-plan` → `xvant-execute` = a written plan run with human checkpoints; `xvant-intent` = interview once, then build the whole thing without asking, owning "end to end" / "hands-off" / "run with it". `xvant-intent` never crosses a one-way door (accounts, data store, paid or external services, deleting data, publishing) on its own.
- **Deep-review / swarm** (deep review / swarm review): a deeper "review my changes" pass shares `xvant-review`'s trigger, so it was folded in as the explicit `swarm` mode rather than a separate `xvant-ultrareview` skill (explicit-mode escalation, like caveman) — avoids reintroducing the trigger collision the kit exists to prevent. Reviewer subagents live in `~/.claude/agents/xvant-review-*.md`.

## Dropped / excluded
- `claude-api` (built-in) — pure passthrough, use the built-in directly.
- Key-gated: gstack codex (OpenAI), design-shotgun (GPT Image), gbrain/setup-gbrain/sync-gbrain, benchmark/paid-evals.
- Out of scope: iOS suite, messaging integrations, makers, math-olympiad, playground, openclaw host variants, deprecated/in-progress Anthropic drafts.

## Provenance
Superpowers + code-review plugins were **disabled** in `settings.json` after xvant absorbed them (reversible — flip back to `true`). Originals live under `~/.claude/refs/{superpowers,gstack,anthropic-skills}` and the plugin marketplace cache. gstack was cloned reference-only to `~/.claude/refs/gstack` (no skill activation, GBrain/Codex/keys skipped). Delete any `xvant-*` folder to undo a single skill; the kit is fully reversible.
