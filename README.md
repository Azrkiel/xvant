# xvant

**One skill per moment. No overlap, no noise, fewer tokens.**

xvant is a curated kit of Claude Code skills. Install the popular packs side by side and you end up with around 150 skills that quietly fight each other: say "I'm done" and four different reviewers fire in a random order, say "review this" and three skills raise a hand, and every description sitting in context is costing you tokens. xvant takes the best of those packs and rebuilds them into 33 skills where exactly one skill owns each moment.

## The problem it solves

More skills is not more capability. Past a point it is just contention. superpowers, gstack, the official plugins, and the built-ins all overlap: multiple planners, multiple debuggers, four ways to review code, five ways to write a skill. They were never designed to share one toolbox, so at trigger time they collide and you get whichever one matched first.

## How it is built: spine + graft

Every xvant skill follows one rule.

- One winning skill becomes the **spine**, the base behavior.
- The useful parts of the overlapping skills are folded in as named **modes**.
- The leftovers are dropped.

The payoff is trigger distinctness. Each skill's description claims keywords no other skill claims, so the right one fires on the first try. When a skill should run only if you ask for it by name, its description says exactly that.

## What you get

**The "I'm done" pile, fixed.** `xvant-verify` is the only skill that triggers on "done." It runs the end-of-task chain in order instead of letting four skills race: runtime check, then code review, then security, then cleanup. `xvant-review`, `xvant-security`, and `xvant-simplify` still work on their own; they just stop fighting over the generic finish line.

**Diagram before you code.** Four skills (`plan`, `execute`, `architecture`, `debug`) make you render the flow as an ASCII diagram first, unhappy paths included. If a failure branch has no arrow, the diagram is not finished. That map stays in context while you build.

**Leaner replies by default.** A caveman-lite baseline strips filler, hedging, and pleasantries from every response while keeping articles and normal sentences, so the output stays readable. Human-facing prose, the `humanizer` skill, and safety warnings are exempt and stay full.

**A real lineage, not a reskin.** The spines come from work that has already been pressure-tested:
- superpowers for TDD, systematic debugging, planning, and verification-before-completion.
- gstack (Garry Tan) for the YC office-hours product diagnostic and the 10x CEO plan review. Both signatures are kept intact, not flattened into a generic checklist.
- The Anthropic skill set and Claude Code built-ins for the rest, from architecture deepening to browser QA.

## The arc

A single line from idea to shipped:

```
brainstorm -> plan -> tdd -> execute -> verify -> ship
```

or, when you want it built without being asked along the way, `intent`: one interview, then a hands-off build to a final report.

with `debug`, `plan-review`, `architecture`, `docs`, `handoff`, and the others on hand when the moment calls for them. Full map lives in `xvant-INDEX`.

## Install

```bash
# 1. drop the skills into place
cp -r xvant-* ~/.claude/skills/
cp -r _shared ~/.claude/skills/_shared

# 2. turn on the token baseline (append the block to your global CLAUDE.md)
cat install/caveman-lite-baseline.md >> ~/.claude/CLAUDE.md

# 3. restart Claude Code so the skills register
```

On Windows, copy the `xvant-*` and `_shared` folders into `%USERPROFILE%\.claude\skills\`, then append `install\caveman-lite-baseline.md` to `%USERPROFILE%\.claude\CLAUDE.md`.

## What's inside

33 skills across the full loop:

| Phase | Skills |
|---|---|
| Shape | brainstorm, plan, plan-review, to-work, hackathon, intent |
| Build | tdd, execute, worktree, debug, prototype |
| Check | verify, review, review-exchange, security, simplify |
| Ship | ship, release-guard, repo-guard |
| Improve | architecture |
| Author | write-skill, extend, configure, claude-md |
| Make | design, browse, docs, second-brain |
| Around the work | study, handoff, retro, schedule, caveman |

Each skill is a tight front end over a deeper reference, so it points at its source procedure instead of dumping a wall of text into your context.

## Design principles

- **Trigger distinctness over file count.** Keep two skills if they fire in genuinely different situations. Merge only the ones that fire on the same phrase.
- **Define once, reference everywhere.** Shared steps live in `_shared/` and get pointed at, never copy-pasted, so one fix propagates everywhere.
- **Reversible.** Delete an `xvant-*` folder to remove a single skill. Nothing is locked in.

## Credit

xvant stands on superpowers, gstack, the official Claude Code plugins, the bundled Anthropic skills, and the built-ins. It reorganizes their ideas into one coherent toolbox; it does not replace the originals, and you should go read them. `humanizer` is deliberately left out and untouched.

## License

MIT. Use it, fork it, or cut it down to the ten skills you actually reach for.
