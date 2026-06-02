---
name: xvant-simplify
description: Use ONLY when explicitly asked to simplify or clean up code — "simplify this", "clean this up", "reduce duplication", "tidy the code". Quality only (reuse, simplification, efficiency, altitude); it does not hunt for bugs — use xvant-review for that. Does NOT self-trigger on a bare "done".
---

# xvant-simplify

Apply reuse / simplification / efficiency / altitude cleanups to changed code. Explicit-invoke only.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Spine:** the built-in `/simplify` command — reviews the changed code for reuse, simplification, efficiency, and altitude, then applies the fixes. Quality only, not bug-hunting.

## Discipline
- Reuse what exists before adding new code. DRY, YAGNI.
- Smallest diff that cleanly expresses the change; don't compress a needed rewrite into a patch.
- Keep behavior identical — verify tests stay green after each cleanup (see `xvant-verify`).

Sequenced as step 4 of `xvant-verify`. For bug-finding, use `xvant-review`.
