# Lesson 7: GitHub Integration

## Source Material

> From the course source — use this as the factual ground truth when answering questions or designing tasks.

**Github Integration**
Claude Code GitHub Integration = official integration allowing Claude to run inside GitHub actions

Setup Process:
- Run "/install GitHub app" command
- Install Claude Code app on GitHub
- Add API key
- Auto-generated pull request adds two GitHub actions

Default Actions:
1. Mention support = @Claude in issues/PRs to assign tasks
2. PR review = automatic code review on new pull requests

Customization:
- Actions are customizable via config files in .github/workflows directory
- Custom instructions = direct context/directions passed to Claude
- MCP server integration = allows Claude to access external tools (like Playwright for browser automation)

Permission Requirements:
- Must explicitly list all permissions for Claude Code in actions
- MCP server tools require individual permission listing (no shortcuts)

Example Use Case:
- Integrated Playwright MCP server for browser testing
- Development server setup before Claude runs
- Claude can visit app in browser, test functionality, create checklists
- Provides automated testing and issue verification

Key Features = mention-based task assignment, automated PR reviews, customizable workflows, MCP server integration for extended functionality

Infrastructure review example: Terraform-defined AWS infrastructure with DynamoDB table and S3 bucket shared with external partner. Developer added user email to Lambda function output. Claude Code automatically detected PII exposure risk in pull request review by analyzing infrastructure flow and identifying external data sharing.

---

## The Big Idea

Claude Code can integrate with GitHub workflows — reviewing PRs, writing commit messages, summarizing diffs, flagging issues, and more. With the right setup, Claude becomes part of the code review process itself, running automatically or on demand.

## Why It Matters

For most developers, code review is the highest-friction part of collaboration. It's slow, it's inconsistent, and it's hard to do well when you're tired or context-switching. Claude can do a first pass on every PR — not to replace human judgment, but to catch the obvious stuff before it becomes a back-and-forth.

## Tasks

### Beginner
Ask the user to take any recent git diff (from their own work) and share it with Claude: "Review this diff like a senior developer on my team. What concerns do you have?"

No GitHub integration needed yet — this is just practicing the workflow with a paste. The goal is to see the quality of review Claude provides and calibrate what "good" looks like.

### Intermediate
If the user has a GitHub repo, set up the GitHub MCP server and have Claude list their open PRs. Pick one and have Claude review it fully — not just summary, but line-level feedback.

Compare it to the manual review they would have written. What did Claude catch? What did it miss? What would you add to your CLAUDE.md or a custom command to make the review more targeted?

### Advanced
Design a custom command (`/review-pr`) that Claude runs on any PR — fetching the diff, checking it against project conventions (from CLAUDE.md), flagging common issues for the codebase, and outputting a structured review comment ready to post.

This is a real artifact the user can take away and use immediately.


## Common Questions

**"Will Claude just approve everything?"**
Claude doesn't approve — it analyzes. It'll flag logic issues, missing error handling, style violations, test gaps. It's not a rubber stamp; it's a first-pass reviewer with no social hesitation.

**"How do I make the review relevant to my project's conventions?"**
Put your conventions in CLAUDE.md. Claude reads it before reviewing. "We always handle errors with X pattern" or "never use Y" goes there.

**"Can Claude commit code or push branches?"**
With the right MCP setup and permissions, yes. But in this lesson the focus is review, not autonomous commits. Those require more deliberate permission configuration.

**"What if I don't use GitHub?"**
GitLab, Bitbucket, or any system with a diff you can share works for the core workflow. The GitHub MCP is just the cleanest integration for GitHub users.

## Debrief

"Code review is one of the first places Claude Code creates real team-level value. What you just did — getting a structured, context-aware review in seconds — is something that normally takes 30 minutes and requires someone not being too busy. The custom command you built is the kind of thing you'd share with your team. That's the scale this lesson points at: not just your workflow, but your team's workflow."

## Connects To

Lesson 5 (Custom Commands): the `/review-pr` command as a workflow artifact
Lesson 6 (MCP Servers): GitHub as an MCP integration
