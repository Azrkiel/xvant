# Hackathon rules for coding agents

Paste the block below into the project's `AGENTS.md` or `CLAUDE.md`. It replaces production rules until the project is submitted.

```markdown
## Hackathon mode (until <deadline>)

Read `HACKATHON.md` first. It is the only plan. The demo script in it decides what gets built.

### What to build
- Build only what the demo script shows. Anything else goes on the cut list in `HACKATHON.md`; do not build it.
- One happy input. Hardcode it. No rotation, offline handling, resume, export, auth or settings unless the script shows them.
- Fake a stage before perfecting it. A labelled fake that keeps the demo running beats a real stage that is half done.
- Use a library before writing your own.

### How to work
- Commit straight to main, small and often. No pull request, no CI gate, no review pass.
- Stay inside your lane's files (the Lanes table). If you need a file in another lane, say so and stop.
- No tests, no status or evidence docs, no refactors, unless asked. One recorded replay of the demo path is added after freeze.
- Stuck for 30 minutes: fake that stage, note it under "Faked for now", move on.
- You have standing approval for model calls, retries and re-runs on the demo path. Do not stop to ask, and do not ration them.
- Give the integrator your HACKATHON.md task ID and one thing to try by hand. Check off your upgrade after the human observes the expected result. While another lane is editing the plan, send the integrator your row update.

### What stays strict
- Never break the demo path on main. If it breaks, fixing it comes before everything else.
- Simulated and recorded modes are labelled on screen.
- No secrets in the repo.
- Do not describe a simulated or recorded result as measured, in code comments, UI text or the write-up.
- After the freeze gate: fixes to the demo path only.
```

## Why each rule exists

| Rule | The failure it prevents |
|---|---|
| Script decides scope | Features built on Saturday and cut on Sunday |
| One happy input | Hours spent on rotated pages and offline sync nobody demoed |
| Commit to main, own your files | Merge and rebase work crowding out features |
| No tests or status docs | More test lines than app lines; a status file edited in half of all commits |
| Standing approval | Agents idle while a human-approval queue grows; live runs skipped to save a call budget |
| Tell the human what to try | By-hand checks deferred until there are twenty of them |
| Label simulated modes | A write-up that reads as if a simulated result was measured |
