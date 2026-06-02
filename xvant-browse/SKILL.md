---
name: xvant-browse
description: Use to drive a headless browser — load pages, click/type, screenshot, QA a running site, or scrape content. Triggers include "open this URL", "browse to", "screenshot the site", "scrape this page", "check the site in a browser", "QA the deployed app".
---

# xvant-browse

Headless browser automation: navigate, interact, capture, scrape.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Spine:** gstack browse (Playwright-based CLI). Full reference + setup: `~/.claude/refs/gstack/browse/SKILL.md`. First run needs a one-time build (`./setup` in the gstack browse dir); the skill detects this. Prefer the browse binary over chrome MCP tools.

## Graft modes
- **Scrape** structured content from a page: `~/.claude/refs/gstack/scrape/SKILL.md`.
- **Cookie/session setup** for authed sites: `~/.claude/refs/gstack/setup-browser-cookies/SKILL.md`.

Use for QA of a running app (pairs with `xvant-verify`'s runtime check) and for any "see the real page" task.
