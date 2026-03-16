# Lesson 4: Visual Communication

## The Big Idea

Claude Code can accept images as input. Screenshots of UIs, error messages, diagrams, mockups — you can drop them directly into the conversation. This collapses the gap between "here's what I see" and "here's what I need," especially for frontend work and debugging visual issues.

## Why It Matters

Describing a UI bug in words is slow and imprecise. Showing a screenshot and saying "make this look like that" is fast and exact. This lesson teaches users to use visual inputs as first-class communication, not an afterthought.

## Tasks

### Beginner
Ask the user to take a screenshot of any UI — their own app, a webpage, anything — and share it with Claude Code. Prompt: "What's wrong with this UI? What would you fix first?"

The goal isn't a perfect answer. It's to show that Claude Code can process images and reason about visual content. After, ask: "What surprised you about what Claude noticed?"

### Intermediate
Ask the user to find a UI they want to build or improve. Share a screenshot of a reference design (something they like from another app or the web) and ask Claude: "Help me build something like this using [their stack]."

Watch how Claude translates visual information into code direction. Discuss: what did it get right? What needs adjustment?

### Advanced
Share two screenshots — a "before" and an "after" of a UI change — and ask Claude: "What changed between these two? Write code to implement the change from the before state."

This tests whether Claude can diff visually and translate the delta into actionable code.

## Common Questions

**"Can I share a Figma design or wireframe?"**
Export it as an image first. PNG or JPG works. Claude doesn't read Figma files directly, but screenshots of designs work well.

**"Does Claude understand component structure from a screenshot?"**
Partially. It can infer layout, spacing, and likely component boundaries. It won't know your exact component names — pair the screenshot with a brief description of your stack.

**"Is this useful for non-UI work?"**
Yes — error messages, terminal output, architecture diagrams, data visualizations. Any time showing is faster than describing.

## Debrief

"Visual communication is a shortcut that most developers underuse. You just showed Claude a picture and got usable output — no long description, no guessing at what you meant. The instinct is still to describe things in words because that's what we're used to. The habit to build is: when you're about to describe something visual, ask yourself if a screenshot would be faster. Usually it is."

## Connects To

Lesson 8 (Thinking Modes): using extended thinking for complex visual-to-code translation
