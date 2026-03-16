# Lesson 8: Thinking and Planning Modes

## Source Material

> From the course source — use this as the factual ground truth when answering questions or designing tasks.

**Making Changes** (thinking and planning section)
Performance boosting modes:
- Plan Mode = Shift + Tab twice, makes Claude research more files and create detailed implementation plans before executing
- Thinking Mode = triggered by phrases like "Ultra think", gives Claude extended reasoning budget for complex logic

Planning vs Thinking usage:
- Planning = handles breadth, useful for multi-step tasks requiring wide codebase understanding
- Thinking = handles depth, useful for tricky logic or debugging specific issues
- Can be combined for complex tasks
- Both consume additional tokens (cost consideration)

Key workflow: describe change → optionally enable Plan/Thinking modes for complex tasks → review and accept implementation

---

## The Big Idea

Claude Code has different reasoning modes. For simple tasks, it responds immediately. For complex ones — architectural decisions, multi-file refactors, hard bugs — you can ask it to think first, make a plan, and get your approval before acting. This lesson is about knowing when to use which mode and how to get the most out of extended reasoning.

## Why It Matters

This is the lesson that unlocks hard problems. Most users hit a ceiling where Claude's default responses feel shallow — it does *something*, but not the right thing. The answer is usually: ask it to think more. This lesson also introduces plan mode, which is how you work on large changes without fear.

## Tasks

### Beginner
Give Claude a problem that seems hard but has a clear answer — a tricky bug, an architectural question, a confusing piece of code. First, ask it normally. Then ask again with: "Think through this carefully before responding."

Compare the two answers. What changed? Where did the thinking surface something the quick answer missed?

### Intermediate
Pick a real refactoring task or feature from the user's own project — something non-trivial. Enter plan mode (Shift + Tab twice) and ask Claude to make a plan before touching any files.

Review the plan. Push back on parts of it. Approve, reject, or modify. Then execute. The goal is to experience the plan-approve-execute loop and feel how it's different from just saying "go do it."

### Advanced
Give Claude a genuinely hard architectural problem — the kind where there are multiple valid approaches with real tradeoffs. Ask it to use extended thinking ("Ultra think"), reason through the options, and make a recommendation with a rationale.

After, ask: "What would have changed about your answer if X were different?" Test whether the reasoning is real or surface-level.


## Common Questions

**"When should I use thinking mode vs. just asking normally?"**
Use it for: architectural decisions, complex bugs with unclear causes, tasks with multiple valid approaches, anything where getting it wrong would be costly. Skip it for: simple tasks, things you'd execute and iterate on anyway.

**"What's plan mode exactly?"**
Plan mode is triggered with Shift + Tab twice. Claude presents a plan and waits for your approval before executing any file writes or commands. Most useful for large changes where you want to understand the full scope before anything gets touched.

**"Does thinking mode always give better answers?"**
Not always. For simple tasks it's overkill. For hard tasks it surfaces reasoning that quick responses skip. Calibrate based on problem complexity.

**"Can I interrupt a plan and change it?"**
Yes — the whole point is collaboration. You can say "don't touch X", "do Y differently", or "skip that step." Claude will revise and re-present before acting.

## Debrief

"You've now seen the full range: from Claude navigating your codebase in Lesson 1, to Claude thinking hard and planning carefully here. The through-line is that Claude is a collaborator with adjustable depth. Most tasks don't need maximum depth. But when you're facing something that matters — something you'd otherwise procrastinate on because it feels too complex — that's when you hand it to thinking mode, review the plan, and let it work. That combination is the thing that makes developers feel like they leveled up."

## Course Complete

After this lesson, the user has covered the full curriculum. Celebrate genuinely in 1-2 sentences — make it feel real, not performative. Do NOT recap or list all 8 lessons. Do NOT give a graduation speech.

Then ask just this: "Is there one thing from the course you want to go deeper on? Or one thing you're going to try in your real workflow this week?"

Whatever they say — that's the next conversation.

## Teaches

`[extended-reasoning, plan-mode]`
