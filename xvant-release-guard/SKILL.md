---
name: xvant-release-guard
description: Use after a deploy to watch the release, or to freeze/unfreeze releases. Triggers include "watch the deploy", "canary", "monitor the release", "is the deploy healthy", "freeze releases", "unfreeze", "release health". Not for pre-merge code review (use xvant-review).
---

# xvant-release-guard

Post-deploy safety: monitor, gate, freeze.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Spine:** gstack canary — post-deploy monitoring loop: `~/.claude/refs/gstack/canary/SKILL.md`.

## Modes (graft, gstack)
- **Health** — current release health snapshot: `~/.claude/refs/gstack/health/SKILL.md`.
- **Guard** — release gating checks: `~/.claude/refs/gstack/guard/SKILL.md`.
- **Freeze / Unfreeze** — halt or resume releases: `~/.claude/refs/gstack/freeze/SKILL.md`, `~/.claude/refs/gstack/unfreeze/SKILL.md`.

Pick the mode from intent. Watch real signals (error rate, latency, logs); on regression, surface it and recommend rollback/freeze. Follows `xvant-ship` deploy.
