# Lesson 5: Custom Commands and Automation

## The Big Idea

Claude Code lets you create custom slash commands — reusable prompts you can invoke with `/command-name`. Anything you find yourself asking Claude repeatedly, you can package as a command. This is where Claude Code stops being a tool you use and starts becoming a tool you've personalized.

## Why It Matters

Custom commands are the first place users go from "Claude is useful" to "Claude is part of my workflow." The lesson connects directly to the frustration the user named in onboarding — whatever tedious thing they keep doing manually is probably automatable here.

## Tasks

### Beginner
Ask the user: "What's something you ask Claude to do repeatedly — even something simple?" Then help them create a custom command for it.

Commands live in `.claude/commands/` as markdown files. Have them create one and invoke it. Even `analyze-function.md` with a simple prompt is enough to make the concept click.

### Intermediate
Ask the user to think about their most annoying recurring dev task — code review prep, writing a changelog entry, generating test cases, summarizing a PR. Help them design a command that takes that task from "30 minutes of work" to "/command and done."

Focus on making the prompt inside the command specific enough to be useful but general enough to work across instances.

### Advanced
Custom commands can reference files with `@filename` and accept arguments. Have the user create a command that uses `$ARGUMENTS` to accept input (e.g., a function name, a ticket number) and incorporates it into the prompt. Then chain two commands in sequence to accomplish a multi-step workflow.

## Common Questions

**"Where do command files live?"**
`.claude/commands/` inside your project for project-specific commands, or `~/.claude/commands/` for commands available everywhere.

**"What format are they?"**
Markdown files. The filename becomes the command name. The content is the prompt that runs when you invoke it.

**"Can commands run bash or call tools?"**
The command content is a prompt, so Claude can use any tools it normally has access to — including Bash. You're not writing a shell script; you're writing an instruction for Claude that can trigger tool use.

**"What's the difference between a command and a CLAUDE.md rule?"**
CLAUDE.md is always-on context. Commands are on-demand. Use CLAUDE.md for permanent preferences; commands for things you invoke intentionally.

## Debrief

"You just automated something. That's the shift this lesson is about — going from user to builder. Custom commands are the first place where Claude Code becomes yours, not just the default tool. Every command you create is a little productivity artifact that compounds over time. The best Claude Code workflows are full of them."

## Connects To

Lesson 6 (MCP Servers): extending commands with external tool access
Lesson 7 (GitHub Integration): commands for automating review workflows
