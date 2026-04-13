# MakoBot Case Studies

Real-world examples of how [MakoBot](https://makobot.com) saves hours per session when building software with AI coding assistants.

---

## What is MakoBot?

AI coding assistants (Claude Code, Cursor, ChatGPT, Gemini) are powerful but amnesiac. Every new session starts from zero. MakoBot fixes this by running in the background, watching your projects, and maintaining a persistent memory layer that any AI tool can read.

- **brain.md** -- cross-project timeline of all activity
- **context.md** -- per-project commit history and state
- **notes.md** -- manual decisions and gotchas
- **claude-sessions.md** -- what happened in every AI session

When you start a new session, the AI reads these files and picks up exactly where the last session left off. No re-explaining. No lost context. No wasted time.

---

## Case Studies

| # | Project | What Was Built | Time Saved |
|---|---------|---------------|------------|
| 1 | [LengLeng Build Session](01-lengleng-build-session.md) | 6 features + security audit + signed release in one evening | ~2 hours |

---

## How It Works

```
You: "Recover"

AI reads brain.md...
  - Current version: 0.4.0
  - Last session: provider overhaul completed
  - Next up: website, testing, notifications
  - 3 uncommitted files

AI: "Here's where things stand..."
  (starts working immediately)
```

No setup. No training. No vector databases. Just markdown files that any AI can read.

---

## Get MakoBot

- **Website:** [makobot.com](https://makobot.com)
- **Built by:** [MakoBytes.com](https://makobytes.com)
