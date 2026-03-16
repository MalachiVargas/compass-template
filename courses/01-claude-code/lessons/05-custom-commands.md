# Lesson 5: Custom Commands and Hooks

## Source Material

> From the course source — use this as the factual ground truth when answering questions or designing tasks.

**Custom Commands**
Custom Commands = user-defined automation commands in Claude Code accessed via forward slash

Location = .claude/commands/ folder in project directory
File naming = filename becomes command name (audit.md creates /audit command)
Activation = restart Claude Code after creating command files

Command structure = markdown file containing instructions for Claude to execute
Arguments = use $arguments placeholder in command text to accept runtime parameters
Argument types = any string (file paths, descriptive text, etc.)

Use cases = automating repetitive tasks like dependency auditing, test generation, vulnerability fixes
Execution = /commandname in Claude Code interface, optionally followed by argument string

**Hooks**
Hooks = commands that run before/after Claude executes tools

Pre-tool use hooks = run before tool execution, can inspect and block tool operations, send error messages to Claude
Post-tool use hooks = run after tool execution, perform follow-up operations, provide feedback to Claude

Configuration = added to Claude settings file (global/project/personal) via manual editing or /hooks command

Hook structure = two sections (pre-tool use, post-tool use), each with matcher (specifies which tools to target) and commands to execute

Hook Implementation Process:
1. Choose hook type (pre vs post)
2. Identify target tool names to monitor
3. Write command to receive tool call data via stdin as JSON
4. Parse JSON containing tool_name and input parameters
5. Exit with appropriate code to signal intent

Exit Codes:
- Exit 0 = allow tool call to proceed
- Exit 2 = block tool call (pre-tool use only)
- Standard error output = feedback message sent to Claude when blocking

Example — blocking .env file reads:
- Location = .claude/settings.local.json
- Hook type = pre-tool use
- Matcher = "read|grep"
- Command = "node ./hooks/read_hook.js"
- Logic: if file path includes ".env" → exit 2 + log error to stderr
- Must restart Claude after hook changes

**Useful Hooks**
TypeScript Type Checker Hook:
- Problem: Claude edits function signatures but doesn't update call sites, causing type errors
- Solution: Post-tool-use hook that runs `tsc --no-emit` after TypeScript file edits
- Process: Detects type errors → feeds errors back to Claude → Claude fixes call sites automatically

Query Deduplication Hook:
- Problem: Claude creates duplicate SQL queries/functions instead of reusing existing ones
- Solution: Hook monitors query directory → launches separate Claude instance → reviews for duplicates → provides feedback
- Trade-off: Additional time/cost vs cleaner codebase
- Recommendation: Only apply to critical directories

Both hooks use post-tool-use pattern to provide immediate feedback and course correction.

---

## The Big Idea

Claude Code lets you create custom slash commands — reusable prompts you can invoke with `/command-name`. Hooks go a step further: they run automatically before or after any tool call, letting you enforce rules, run checks, and feed results back to Claude without any manual intervention. Together, commands and hooks are how you make Claude Code yours.

## Why It Matters

Custom commands are the first place users go from "Claude is useful" to "Claude is part of my workflow." Hooks are where Claude Code becomes self-correcting — catching its own mistakes automatically. Both connect directly to whatever tedious thing the user named in onboarding.

## Tasks

### Beginner
Ask the user: "What's something you ask Claude to do repeatedly — even something simple?" Then help them create a custom command for it.

Commands live in `.claude/commands/` as markdown files. Have them create one and invoke it. Even `analyze-function.md` with a simple prompt is enough to make the concept click.

### Intermediate
Ask the user to think about their most annoying recurring dev task — code review prep, writing a changelog entry, generating test cases, summarizing a PR. Help them design a command that takes that task from "30 minutes of work" to "/command and done."

Then introduce hooks: show them how a post-tool-use hook could automatically run a check after Claude edits a file (e.g., a linter, a type check, a test run).

### Advanced
Custom commands can reference files with `@filename` and accept arguments. Have the user create a command that uses `$ARGUMENTS` to accept input and incorporates it into the prompt. Then design a hook that feeds results back to Claude — making a self-correcting loop (e.g., run tests after every file edit, feed failures back automatically).


## Common Questions

**"Where do command files live?"**
`.claude/commands/` inside your project for project-specific commands, or `~/.claude/commands/` for commands available everywhere.

**"What format are they?"**
Markdown files. The filename becomes the command name. The content is the prompt that runs when you invoke it.

**"Can commands run bash or call tools?"**
The command content is a prompt, so Claude can use any tools it normally has access to — including Bash. You're not writing a shell script; you're writing an instruction for Claude that can trigger tool use.

**"What's the difference between a command and a CLAUDE.md rule?"**
CLAUDE.md is always-on context. Commands are on-demand. Use CLAUDE.md for permanent preferences; commands for things you invoke intentionally.

**"When should I use a hook vs a command?"**
Commands are triggered by you. Hooks run automatically on every matching tool call. Use hooks for things that should always happen (type checking, linting); use commands for things you invoke intentionally.

## Debrief

"You just automated something — and then made it self-correcting. That's the shift this lesson is about: going from user to builder. Commands are the first place where Claude Code becomes yours. Hooks are where it starts enforcing your standards without you having to think about it. Every command and hook you create is a productivity artifact that compounds over time."

## Teaches

`[slash-commands, hooks, automation]`
