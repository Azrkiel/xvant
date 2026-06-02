---
name: xvant-schedule
description: Use to run something repeatedly on a schedule or interval, or once at a future time — cron routines, recurring agents, polling, or in-session loops. Triggers include "every 5 minutes", "schedule this", "run on a cron", "keep checking", "run once at 3pm", "remind me tomorrow", "loop this command". Not for one-off immediate tasks.
---

# xvant-schedule

Recurring or future-timed execution. Pick the mode by where it should run.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

## Modes
- **Remote / cron routine (spine: built-in `schedule`)** — create/update/list/run scheduled remote agents that execute on a cron schedule, or a one-time scheduled run ("run once at 3pm", "remind me tomorrow"). Survives across sessions.
- **In-session loop (graft: built-in `loop`)** — run a prompt or slash command on a recurring interval within a session (`/loop 5m /foo`), or self-paced. Use for "poll the deploy every 5 min", "keep running X".

Use cron/schedule for durable automation; use loop for live polling during a session. Never use either for a single immediate task.
