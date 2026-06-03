# Parallel dispatch — fan-out helper (shared, referenced not copied)

Dispatch N independent, fresh-context subagents concurrently and collect structured results. Used by `xvant-review` swarm (stage 2, reviewer personas) and reusable by `xvant-execute` (implementer personas). Source method: superpowers dispatching-parallel-agents (`~/.claude/refs/superpowers/dispatching-parallel-agents/SKILL.md`).

## When
2+ independent sub-problems, no shared mutable state, each with a clear scope and an explicit output schema.

## Mechanism
1. **Define each agent's job:** its scope (which inputs — e.g. the diff digest + specific hunks/files), constraints, and an explicit **output schema** so results merge cleanly.
2. **Launch in ONE batch** (parallel), each in its own context window. Don't serialize unless there's a real data dependency.
3. **Collect, then merge/dedupe** by a stable key (e.g. `file:line`). Verify no conflicts before acting.

## Personas are caller-supplied
- `xvant-review` swarm → reviewer lenses (correctness / security / concurrency / architecture), read-only, return **suspected findings**.
- `xvant-execute` → implementer agents, return diffs/results.

Keep each agent single-responsibility and zero-context. Hand it the slice it needs, not the world.
