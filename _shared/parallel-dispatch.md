Use for 2+ independent tasks with disjoint writable state. Give each fresh-context worker a brief with the user's objective and acceptance criteria, implementation assumptions, scoped inputs, constraints and output schema.

- Investigation: request a sourced report and open questions. Review personas return suspected findings from their assigned diff slices.
- Implementation: identify writable paths, isolated worktree and required checks. Order overlapping writes as dependent tasks.

Launch independent workers in one batch. Collect and deduplicate by stable key (e.g. file:line and claim). Record worker, evidence/revision and blockers. Reconcile uncertain outcomes before reassignment and check for conflicts before acting.

Source procedure: `~/.claude/refs/superpowers/dispatching-parallel-agents/SKILL.md`.
