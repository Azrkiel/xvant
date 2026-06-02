# ASCII Diagram Step (shared reference)

Before writing or changing code, render the relevant flow as an ASCII diagram in the
conversation. The point is not decoration — it forces the model to commit to every branch
(happy path, edge cases, error states) BEFORE coding, and keeps that map in context while
implementing.

Draw whichever of these fit the task:
- Data flows: inputs → transforms → outputs
- User flows: each step a user takes, including failure paths
- Error states: what happens on each failure, and what the user/system sees
- Plus, where relevant: state machines, dependency graphs, processing pipelines, decision trees

Rules:
- Cover the unhappy paths explicitly. If a branch (validation fail, timeout, empty result,
  auth error) has no arrow, the diagram is incomplete.
- Keep it plain keyboard characters (boxes, |, v, -->), readable inline.
- Stop and let the human sanity-check the diagram before implementing.

Example shape:

```
[User submits form]
       |
       v
[Validate] --invalid--> [Return 400 + message]
       |
     valid
       v
[Save to DB] --db error--> [Return 500 + log]
       |
    success
       v
[Return 201 + record]
```

---

This file is a **reference, not a triggerable skill** (underscore-prefixed dir, no
frontmatter). Skills that need the diagram step instruct the agent to follow this file:
`xvant-plan` (diagram is part of plan output), `xvant-execute` (entry step before first
code), `xvant-architecture` (system-level diagrams), `xvant-debug` (actual-vs-expected).
