# Delegating from the main plan

**Before spawning.** The orchestrator owns one written plan. Reuse the current plan and its IDs, including plans started in an earlier session. Give any unnumbered assignment a stable ID and a checkbox. Group small implementation steps under one independently verifiable outcome. For a standalone review or exercise without a project plan, keep a short checklist in the orchestrator's working notes outside the target tree.

```markdown
- [ ] T3 Show every rejected row in the upload screen | owner: UI worker | needs: T2 | check: pytest tests/test_upload.py
```

**Brief.** Send the plan path and task ID, goal, relevant constraints, required inputs, writable paths or worktree, and acceptance check. Point to the relevant section or files. Keep chat history, unrelated tasks and long logs out of the brief. For a blind vote, review or pressure test, supply only the allowed evidence and an opaque task ID; the lead retains the mapping. Batch independent tasks with disjoint writes. Sequence dependencies.

**Worker checkoff.** Run the assigned check. On success, change only your task's `[ ]` to `[x]` in the plan and append a short result with a retrievable check, artifact or revision. If the check fails, skips the behavior, or leaves work incomplete, keep the row unchecked and record what remains unverified. Return one line, e.g. `T3 done | pytest tests/test_upload.py passed | abc1234`. Keep detailed logs at the evidence path. Return any findings or decisions explicitly required by the calling skill.

- In an isolated worktree, check off your row in its copy of the plan. Return the revision or patch containing that edit and the deliverable. The lead reconciles that row into the canonical plan when integrating the work.
- In a shared checkout, allow one plan writer at a time. When several workers finish together, or the plan is absent, read-only or intentionally hidden, return the exact proposed row update by ID. The lead applies those updates serially. Keep each worker's existing file and tool permissions.

**Integration and resume.** Read changed rows and evidence. Match the assigned owner, acceptance check and revision before applying a result. Ignore repeat deliveries of the same result. Reconcile stale or conflicting updates against the current plan by ID. Reopen a row if integration invalidates its check. Keep the milestone’s integration check visibly pending in the plan until it passes on the combined revision. Record that result separately from the worker checkoffs. Resume from unchecked rows and outstanding integration checks; open detailed logs only for a failure, conflict or decision.

For investigations, ask for sourced findings and open questions. Review findings stay suspected until verified; deduplicate by file, line and claim. Source procedure: `~/.claude/refs/superpowers/dispatching-parallel-agents/SKILL.md`.
