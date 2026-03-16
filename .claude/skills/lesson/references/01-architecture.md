# Lesson 1: Coding Assistant Architecture

## The Big Idea

Claude Code doesn't read your codebase like a human scrolling through files. It uses tools — Read, Grep, Glob, Bash — to find and examine exactly what's relevant. Understanding this changes how you work with it. You stop trying to explain everything upfront and start letting Claude navigate.

## Why It Matters

Users who understand this stop paste-dumping entire files and start giving Claude a starting point. They get faster, more accurate results. This is the mental model that unlocks everything else in the course.

## Tasks

### Beginner
Ask the user to open a real project they have on their machine (any project — even a small one) and ask Claude Code: "What does this project do?" without providing any code.

Watch what happens. Claude will use Glob and Read to explore. After, ask the user: "What tools did you see Claude use? What did it look at first?"

The point is to make the tool use visible and demystify it.

### Intermediate
Ask the user to give Claude Code a vague instruction about their project — something like "find where user auth is handled" or "where does data get fetched?" — and observe how Claude navigates.

Then ask: "If you were Claude, what would *you* search for to find that?" Compare their answer to what Claude actually did.

### Advanced
Ask the user to intentionally mislead Claude — give it a wrong assumption about the codebase (e.g., "the config is in config.js" when it's not). Watch how Claude corrects itself through tool use. Discuss: what did Claude do when it couldn't find what you told it to?

## Common Questions

**"Why doesn't Claude just read all the files at once?"**
Context windows have limits, and reading everything would be slow and expensive. Claude reads what's relevant — like a senior dev who knows which files to open first.

**"Should I paste my code into the prompt?"**
Usually no. Give Claude the path and let it read. Pasting dumps unstructured noise; the Read tool preserves structure and line numbers.

**"How does Claude know where to start looking?"**
It uses your prompt as a signal. File names you mention, function names, error messages — all of these become search terms. The more specific your prompt, the better the navigation.

## Debrief

"What you just saw is the foundation of everything. Claude Code isn't an autocomplete — it's an agent that navigates your codebase the same way you do, just faster. Every other lesson builds on this: tools for multi-step tasks, context management, automation — it all assumes you understand that Claude is *exploring*, not reading your mind."

## Connects To

Lesson 2 (Tool Use): how tools combine for complex tasks
Lesson 3 (Context Management): how to keep Claude focused on what matters
