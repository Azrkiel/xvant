# xvant

A curated, no-overlap kit of Claude Code skills. Each `xvant-*` skill is one capability
with a winning **spine** plus **grafted** modes absorbed from overlapping skills
(superpowers, gstack, the official Claude Code plugins, the bundled Anthropic skills, and
Claude Code built-ins). The goal is **trigger distinctness** — one skill per moment, no two
firing on the same phrase.

See `xvant-INDEX/SKILL.md` for the full map (spine + grafts per skill, ★ signatures, ◆ ASCII step).

## Operating principles
- Skills compete at trigger time, not runtime — distinct trigger keywords; explicit-only skills say so.
- Spine + graft: one winning base per skill; overlaps folded in as named modes; redundant ones dropped.
- Define once, reference everywhere: shared steps live in `_shared/` (e.g. `ascii-diagram.md`) and are referenced, never copy-pasted.
- Caveman-lite is the always-on output baseline (see `install/`), with carve-outs for human prose, the `humanizer` skill, and safety warnings.
- ★ Garry signatures preserved: office-hours decomposition (`xvant-brainstorm`) and the 10x / 10-star CEO review (`xvant-plan-review`).
- ◆ ASCII diagram step in exactly four: `xvant-plan`, `xvant-execute`, `xvant-architecture`, `xvant-debug`.

## Install
1. Copy each `xvant-*/` folder into `~/.claude/skills/` and copy `_shared/` to `~/.claude/skills/_shared/`.
2. Append the contents of `install/caveman-lite-baseline.md` to `~/.claude/CLAUDE.md` (creates the always-on baseline).
3. Restart Claude Code so the skills register.

Some skills reference source procedures under `~/.claude/refs/{superpowers,gstack,anthropic-skills}`
and the official plugin marketplace cache. Those paths are environment-local; on a fresh
machine, repoint or re-clone the sources, or rely on each skill's inlined spine.

## Notes
- `humanizer` is intentionally **not** part of this kit and is left untouched.
- Reversible: drop an `xvant-*/` folder to remove one skill.
- This repo is a snapshot export; edits to the live skills in `~/.claude/skills/` are not auto-synced here.
