# Lesson 6: MCP Servers

## Source Material

> From the course source — use this as the factual ground truth when answering questions or designing tasks.

**Extending Claude Code with MCP Servers**
MCP servers = external tools that extend Claude Code capabilities, run locally or remotely.

Playwright MCP server = popular server enabling Claude to control browsers for web automation.

Installation: Terminal command `claude mcp add [name] [start-command]` adds MCP server to Claude Code.

Permission management: Initial tool usage requires approval. Auto-approve by adding "MCP__[servername]" to settings.local.json allow array.

Practical example: Claude used Playwright to navigate localhost:3000, generate UI component, analyze styling quality, then automatically update generation prompts based on visual feedback.

Results: Automated prompt refinement produced significantly better component styling, demonstrating MCP servers unlock sophisticated development workflows.

Key benefit: MCP servers enable Claude to perform complex multi-step tasks involving external systems, expanding beyond code editing to full development automation.

---

## The Big Idea

MCP (Model Context Protocol) servers are plugins that give Claude Code access to external tools and services — databases, APIs, browsers, Slack, GitHub, and more. Instead of Claude being limited to your local filesystem, MCP servers let it reach out into your actual environment and take actions there.

## Why It Matters

This is where Claude Code stops being a coding assistant and starts being an agent that can actually do things in your world. For developers who are excited about automation, this is the lesson where that potential becomes tangible.

## Tasks

### Beginner
Have the user list what MCP servers they have installed by running `claude mcp list` or checking their Claude Code settings. If they have one installed, pick one together and look at what tools it exposes.

If none are installed, walk them through installing one simple server — the filesystem MCP or the fetch MCP are good starting points. Just get one working and make one tool call through it.

### Intermediate
Pick an MCP server that connects to something the user actually uses (GitHub, a database, their browser). Have them ask Claude to do something real with it — "check my open PRs", "query the users table", "open this URL and summarize it."

The goal is to see an end-to-end action: Claude receiving a natural language request, using an MCP tool, and returning a result from outside the local filesystem.

### Advanced
Have the user think about a workflow they run regularly that touches multiple systems — code + a ticket tracker, code + a database, code + Slack. Design a command (from Lesson 5) that combines local file operations with an MCP server call to complete the workflow in one shot.


## Common Questions

**"How are MCP servers different from regular tools like Read and Bash?"**
Built-in tools (Read, Bash, etc.) work on your local machine. MCP servers are integrations that connect Claude to specific external systems. They extend what Claude can reach.

**"Is it safe? Can Claude do things I don't want it to?"**
Claude Code asks for approval before taking actions by default. You control the permission level. MCP servers don't grant autonomous access — Claude still works within the approval model you've set.

**"How do I find MCP servers to install?"**
The Claude Code docs and community have growing lists. Common ones: filesystem, GitHub, Postgres, browser automation, Slack, Linear. Start with one that connects to something you already use.

**"Can I write my own MCP server?"**
Yes — the protocol is open and documented. If you have an internal tool or API you want Claude to access, you can build a server for it. This is where MCP gets genuinely powerful for teams.

## Debrief

"MCP is the bridge between Claude and the rest of your world. What you just did — calling out to an external system from inside Claude Code — is what turns this from a code editor extension into something that can actually run parts of your workflow. The mental model shift is: Claude isn't just inside your codebase anymore. It can be wherever you give it access to be."

## Connects To

Lesson 7 (GitHub Integration): a specific, high-value MCP use case
Lesson 5 (Custom Commands): combining commands with MCP calls for full workflow automation
