# Case Study: Building LengLeng with MakoBot's Cross-Project Memory

**Date:** April 12, 2026  
**Project:** LengLeng (AI voice assistant for Windows)  
**AI Tool:** Claude Code (VS Code extension)  
**MakoBot Role:** Cross-project memory and context persistence

---

## The Problem

Building a complex desktop app across multiple sessions with AI coding assistants means starting cold every time. The AI doesn't know what was built yesterday, what decisions were made, what patterns exist in your other projects, or where your tools are installed. You waste 20-30 minutes per session just re-explaining context.

## What MakoBot Did

MakoBot runs in the background watching project folders. Every git commit gets logged to a shared `brain.md` file. Manual decisions, session summaries, and technical patterns are saved to structured memory files. When a new AI session starts, the assistant reads these files and picks up exactly where the last session left off.

## The Session

In a single evening session, we built 6 major features for LengLeng: a floating desktop widget, a skills system, a projects tab, voice shutdown commands, a stats dashboard, and security hardening. Here's where MakoBot's memory made the difference.

### 1. Zero Ramp-Up Time

The session started with one word: **"Recover"**

The AI read MakoBot's brain.md and instantly knew:
- Current version: 0.4.0
- Last session: provider overhaul completed and tested
- What was done: 16+ files changed across dynamic model detection, Ollama/LM Studio setup
- What was next: website, testing, notification sounds
- Git status: 3 uncommitted files

No explanation needed. No "what are we working on?" No re-reading code. Just straight to work.

### 2. Cross-Project Pattern Reuse

When building the floating desktop widget, we needed a hover-to-expand circle that floats on the desktop — similar to MakoBot's own floating widget. Instead of designing from scratch, the AI read MakoBot's `FloatingWidget.xaml.cs` directly:

- Popup placement logic (screen-edge aware)
- Close timer with hover detection
- Drag-move handling
- Button hover state patterns (MouseEnter/MouseLeave with color shifts)
- Visual feedback (border color flash on actions)

The entire architecture was adapted in one pass. No trial and error. The proven pattern from one project transferred directly to another because MakoBot had the code indexed.

### 3. Infrastructure Knowledge

MakoBot's notes.md contained exact paths and configurations that would have taken significant time to hunt down:

| What | Where MakoBot Had It |
|------|---------------------|
| Code signing endpoint and credentials | notes.md (exact endpoint, account name, auth method) |
| Installer compiler path | notes.md (exact install location on this machine) |
| Signing retry behavior | notes.md (knew that timestamp server hiccups are transient — just retry) |
| Code signing library path | csproj cross-reference via brain.md |
| Remote repo URL | git remote stored in project context |

Without these, each piece would have required manual discovery or asking the user to look it up.

### 4. Decision Continuity

Previous sessions established hard rules that MakoBot preserved:

- **"Never ship broken code"** — elevated to absolute rule after a past incident. This session: ran full security audit before publishing, found and fixed 3 critical vulnerabilities.
- **"Use 127.0.0.1 not localhost"** — a security tool on this machine blocks localhost connections. Every local API URL in the codebase follows this because the decision was saved.
- **"Use raw HttpClient, not community SDK wrappers"** — decided in a previous session after evaluating trade-offs. No one accidentally re-added the dependency.
- **"Provider X is the best fit for this app"** — testing conclusions from the last session informed how we rank and promote providers in the UI.

These aren't things you can derive from reading code. They're human decisions with context that only exist because MakoBot captured them.

### 5. Session Handoff

At the end of the session, build progress was updated automatically. The next session (whether tonight, tomorrow, or next week) will know:

- Skills system built with SkillManager.cs
- Projects tab built with ProjectManager.cs  
- Floating widget built with FloatingWidget.xaml/.cs
- Security fixes applied to BrowserTool.cs
- Installer built from Release (not Debug — was a bug we fixed)
- v0.4.0 released to GitHub with signed installer

No sticky notes. No "where was I?" moments. The context persists.

## What Was Built

| Feature | Files Created/Modified | Time Saved by Memory |
|---------|----------------------|---------------------|
| Floating Widget | 2 new files, adapted from MakoBot pattern | ~45 min (pattern reuse) |
| Skills System | 1 new file + UI + prompt injection | ~10 min (knew existing prompt architecture) |
| Projects Tab | 1 new file + UI + prompt injection | ~10 min (same pattern as skills) |
| Voice Shutdown | MainWindow.xaml.cs modification | ~5 min (knew ProcessUserTextAsync location) |
| Security Audit | 3 files fixed | ~20 min (knew signing pipeline, didn't need to figure it out) |
| Build + Sign + Release | Installer + GitHub release | ~30 min (had exact paths and commands) |

**Estimated time saved by MakoBot memory: ~2 hours** in a single session.

## The Takeaway

AI coding assistants are powerful, but they're amnesiac. Every new session is a blank slate. MakoBot solves this by maintaining a persistent, structured memory layer that any AI tool can read:

- **brain.md** — cross-project timeline of all activity
- **context.md** — per-project commit history and state
- **notes.md** — manual decisions and gotchas
- **claude-sessions.md** — what happened in every AI session

The AI doesn't need to be "trained" on your codebase. It just needs to read the right files at the start of each session. MakoBot writes those files automatically.

---

*Built by [MakoBytes.com](https://makobytes.com) | [makobot.com](https://makobot.com)*
