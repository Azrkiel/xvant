# Parallel dispatch — fan-out helper (shared, referenced not copied)

Dispatch N independent, fresh-context subagents concurrently and collect structured results. Used by `xvant-review` swarm (stage 2, reviewer personas) and reusable by `xvant-execute` (implementer personas). Source method: superpowers dispatching-parallel-agents (`~/.claude/refs/superpowers/dispatching-parallel-agents/SKILL.md`).

## When
2+ independent sub-problems, no shared mutable state, each with a clear scope and an explicit output schema.

## Mechanism
1. **Define each agent's job:** its scope (which inputs — e.g. the diff digest + specific hunks/files), constraints, and an explicit **output schema** so results merge cleanly.
   Preserve the user's objective and acceptance criteria in the brief. List implementation assumptions separately so a worker can tell which choices it may revisit.
   For an investigation, request a sourced report with open questions. For an implementation, name its writable paths, isolation worktree and required checks. Order overlapping writes as dependent tasks.
2. **Launch in ONE batch** (parallel), each in its own context window. Don't serialize unless there's a real data dependency.
3. **Collect, then merge/dedupe** by a stable key (e.g. `file:line`). Record who returned each result, the revision or evidence it refers to, and any unresolved blocker. Reconcile uncertain worker outcomes before reassigning their work. Verify no conflicts before acting.

## Personas are caller-supplied
- `xvant-review` swarm → reviewer lenses (correctness / security / concurrency / architecture), read-only, return **suspected findings**.
- `xvant-execute` → implementer agents, return diffs/results.

Keep each agent single-responsibility and zero-context. Hand it the slice it needs, not the world.
