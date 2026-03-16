# Lesson 3: Context Management

## The Big Idea

Claude's context window is finite. In a long session, older messages fade from relevance or get compressed. Knowing how to stay within context — and how to restart cleanly when you need to — is what separates people who get consistent results from people who find Claude "getting confused" later in a session.

## Why It Matters

This is the lesson that unlocks reliable long-session work. Users who don't understand context keep blaming Claude for forgetting things; users who do understand it structure their sessions to stay effective. It also introduces `/clear` and `CLAUDE.md` — two of the most practically useful things in Claude Code.

## Tasks

### Beginner
Ask the user to find or create a `CLAUDE.md` file in one of their projects (or in `~/.claude/CLAUDE.md` for global). Have them write just 3–5 lines: what the project is, what stack it uses, and one "don't do this" rule they'd want Claude to always follow.

Then start a new session and ask Claude something about the project. Does it behave differently? What did it pick up from `CLAUDE.md`?

### Intermediate
Ask the user to work on a task across two separate Claude Code sessions — same task, fresh context each time. First session: no CLAUDE.md or setup. Second session: start with a focused context summary ("We're working on X, here's what matters: ...").

Compare the quality of responses. What changed?

### Advanced
Give the user a long multi-file refactoring task. Midway through, have them `/clear` the context and resume with a tight summary of what's been done and what's left. The goal is to practice "context checkpoint" — the discipline of pausing, summarizing, and restarting clean rather than letting a session degrade.

## Common Questions

**"How do I know when my context is getting full?"**
Claude starts to lose coherence with earlier decisions, repeats itself, or makes mistakes it wouldn't have made fresh. The practical signal is when something feels off — that's usually context drift.

**"What should I put in CLAUDE.md?"**
Project overview, tech stack, conventions you care about, things Claude should never do in this project. Think of it as onboarding docs for Claude.

**"Should I use `/clear` a lot?"**
Use it when starting a genuinely new task, not mid-task. Mid-task clears lose important state. End-of-task clears keep the next task crisp.

**"Can I have multiple CLAUDE.md files?"**
Yes — one global (`~/.claude/CLAUDE.md`) and one per project. Project-level overrides global. Use global for your personal preferences, project-level for project-specific rules.

## Debrief

"Context is the medium you and Claude work in. Understanding it isn't about managing a technical limitation — it's about developing a workflow habit. The best Claude Code users think in sessions: what does Claude need to know right now, and what's noise? CLAUDE.md is how you answer that question permanently. `/clear` is how you answer it fresh."

## Connects To

Lesson 5 (Custom Commands): automating context-loading as a command
Lesson 8 (Thinking Modes): when extended context is worth the cost
