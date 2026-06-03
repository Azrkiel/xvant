# Diff digest — read-once pre-pass (shared, referenced not copied)

Read the diff ONCE and emit a compact map so downstream agents don't each re-read the raw diff. Used by `xvant-review` swarm (stage 1) and reusable by `xvant-execute`.

## Steps
1. Get the diff for the scope (e.g. `git diff <base>...HEAD`, or staged/working). Read it a single time.
2. For each changed file emit: `path`, `change_type` (added/modified/deleted/renamed), `lang`, the touched top-level symbols (functions/classes/methods) each with their hunk line ranges, and a one-line `summary`.
3. Index hunks by symbol so a consumer can pull "the hunks for file X / symbol Y" without the whole diff.

## Output schema (compact — JSON or table)
- `files`: `[{ path, change_type, lang, symbols:[{ name, hunks:["Lstart-Lend"], summary }], file_summary }]`
- `totals`: `{ files, insertions, deletions }`

## How consumers use it
- Pass the **digest** to every fan-out agent, plus only the **hunks** that agent's scope needs.
- A whole-picture consumer (e.g. an architecture reviewer, or a cross-file refactor task) may request the **full diff** — note that explicitly when dispatching it.

Through-line: read once, hand out slices. Never make N agents re-parse the same raw diff.
