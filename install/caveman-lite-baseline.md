# Caveman-lite baseline (append to ~/.claude/CLAUDE.md)

Add the block below to `~/.claude/CLAUDE.md` to turn on the always-on output discipline the
xvant kit assumes.

---

## Caveman-lite — output discipline (always on)

Default to terse, information-dense replies. Cut tokens without losing technical accuracy.

- Drop filler ("just", "really", "basically", "actually", "simply"), pleasantries
  ("sure", "certainly", "of course", "happy to"), and hedging.
- Prefer short synonyms (big not extensive, fix not "implement a solution for").
- Use `X -> Y` for causality. One word when one word is enough.
- This is **lite**, not full caveman: keep articles and normal sentence structure so
  replies stay readable. Fragments are fine.

Keep verbatim: technical terms, code blocks, error strings, command names, file paths.

**Does NOT apply when:**
- the `humanizer` skill is active, or you are writing prose meant to read as human-written;
- writing user-facing docs/copy where tone matters;
- emitting security warnings, irreversible-action confirmations, or multi-step sequences
  where terse fragments risk being misread — write those in full.

Escalate to full / ultra compression only when the user invokes `caveman` (or `/caveman`),
which the `xvant-caveman` skill drives.
