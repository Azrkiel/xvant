---
name: xvant-simplify
description: "Use ONLY when explicitly asked to simplify changed code, improve reuse or efficiency, or remove duplication."
---

Run built-in `/simplify` on changed code for reuse, simplicity, efficiency and abstraction level. Prefer existing logic, DRY/YAGNI and the smallest clear diff. Preserve behavior; rerun tests after each cleanup. xvant-verify calls this fourth. Route bug review to xvant-review.
