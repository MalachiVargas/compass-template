# Lesson 2: Tool Use System

## Source Material

> From the course source — use this as the factual ground truth when answering questions or designing tasks.

**Claude Code in Action** (tool use context)
Claude Code = AI assistant with tool-based capabilities for code tasks
Default tools = file reading/writing, command execution, basic development operations

Performance optimization demo: Claude analyzed Chalk JavaScript library (5th most downloaded JS package, 429M weekly downloads). Used benchmarks, profiling tools, created todo lists, identified bottlenecks, implemented fixes. Result = 3.9x throughput improvement.

Data analysis demo: Claude performed churn analysis on video streaming platform CSV data using Jupyter notebooks. Executed code cells iteratively, viewed results, customized successive analyses based on findings.

Tool extensibility: Claude Code accepts new tool sets. Example used Playwright MCP server for browser automation. Claude opened browser, took screenshots, updated UI styling, iterated on design improvements.

Key principle: Claude Code = flexible assistant that grows with team needs through tool expansion rather than fixed functionality.

**The Claude Code SDK**
Claude Code SDK = programmatic interface to use Claude Code via CLI, TypeScript, or Python libraries. Same tools as terminal version.

Primary use case = integration into larger pipelines/workflows to add intelligence to processes.

Key characteristics:
- Default permissions = read-only (files, directories, grep operations)
- Write permissions = must be manually enabled via query options or settings file
- Raw conversation output = shows message-by-message exchange between local Claude Code and language model

Best applications = helper commands, scripts, hooks within existing projects rather than standalone use.

Output format = conversational messages with final response from Claude as last message.

---

## The Big Idea

Claude Code has a set of tools — Read, Write, Edit, Bash, Grep, Glob, and more — and can chain them together to complete complex, multi-step tasks. You don't orchestrate this manually; you describe a goal and Claude figures out the sequence. The skill is learning how to describe goals in a way that produces the right tool chain.

## Why It Matters

This is where Claude Code stops feeling like a chatbot and starts feeling like a collaborator. Once users see Claude plan and execute a sequence of actions, they stop thinking "what command do I ask it to run" and start thinking "what outcome do I want."

## Tasks

### Beginner
Give the user a small real task in their own project: "Ask Claude to find all TODO comments in your codebase and summarize them in a list."

No further instruction. Let them write the prompt however they want. After, discuss: how many tools did Claude use? What was the sequence? Would you have done it differently?

### Intermediate
Ask the user to give Claude a task that requires at least three steps — something like: "Find the function that handles X, add a console.log to it, and tell me what file and line you changed."

The goal is to watch Claude plan before acting. After, ask: "Did Claude do what you expected? Where did it surprise you?"

### Advanced
Ask the user to intentionally give Claude an ambiguous multi-step task — something where the right approach isn't obvious. Watch how Claude handles uncertainty: does it ask for clarification, make an assumption, or try something and report back? Discuss the tradeoffs of each.


## Common Questions

**"How do I know which tools Claude will use?"**
You generally don't need to — Claude picks based on the task. But if you want to guide it, mention the approach in your prompt: "without running any commands" or "by editing the file directly" shifts the tool selection.

**"Can I tell Claude NOT to use certain tools?"**
Yes. "Don't run bash commands" or "read-only, don't make any changes" are understood. Claude respects constraints in the prompt.

**"What if Claude uses the wrong tool and breaks something?"**
Claude Code shows you what it's about to do before writing or running things (in default mode). You can reject individual tool calls. It's not all-or-nothing.

**"Why does Claude sometimes ask me a question mid-task?"**
When the next step requires a decision that affects the outcome, Claude pauses. This is a sign it's planning well, not a failure.

## Debrief

"The tool use system is what makes Claude Code an *agent* and not just a smarter autocomplete. You just gave it a goal and watched it figure out the steps. That gap — between stating a goal and watching it execute — is what most developers are still adjusting to. The instinct is to micromanage the steps. The skill is learning to trust the goal-setting and use your energy to describe outcomes clearly."

## Connects To

Lesson 3 (Context Management): keeping Claude focused as tasks get complex
Lesson 5 (Custom Commands): packaging multi-step tasks you run repeatedly
