Read the scoped diff once (base...HEAD, staged or working tree). Index hunks by file and symbol. Return compact JSON or a table:

- files: path, change_type (added/modified/deleted/renamed), lang, symbols with name, hunk ranges (Lstart-Lend) and summary, plus file_summary.
- totals: files, insertions, deletions.

Give each reviewer the digest and its relevant hunks. Identify whole-diff consumers explicitly; the architecture reviewer needs the full diff.
