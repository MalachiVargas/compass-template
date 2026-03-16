---
name: lesson
description: Run an interactive lesson in the Compass course. Use when the user invokes /lesson, says "next lesson", "continue the course", "what's next", "I'm ready", or asks to keep learning. Loads the user's progress and profile from memory, picks up from where they left off, and runs the task-based learning loop for the current lesson. Always personalize the task to the user's stated goals and background.
---

# Lesson — Interactive Learning Loop

## Before Starting

1. **Read `memory/user_profile.md`** — get their dream project, tech background, Claude Code experience, and what excites them.

2. **Read `memory/progress.md`** — get `current_course` (directory path) and the course's `current_lesson` and `status`. If no progress file exists, start at course `courses/01-claude-code`, lesson 1.

3. **Read `{current_course}/course.md`** — get the lesson file path for `current_lesson` from the lessons table.

4. **Read the lesson file** — it contains both the source material (ground truth) and the teaching guide. Read it fully before proceeding.

5. If `status` is `in_progress`, tell the user briefly where they left off based on `notes`, then continue. If `not_started`, begin fresh.

6. **Immediately update `memory/progress.md`** — set `status: in_progress` for this lesson so a mid-session quit can be detected next time.

---

## The Learning Loop

### 1. Frame the lesson
One or two sentences. Connect it to what they told you they care about. Make it feel relevant, not academic.

### 2. Assign the task
Pick a task from the lesson file that fits the user's experience level. Adapt it to their dream project — same concept, their context.

Give only enough context to understand what to do. Don't explain the concept first. Let them encounter it.

### 3. Let them try
Wait. Don't jump in. If they go quiet, a light nudge is fine: "What are you running into?"

### 4. Answer questions in context
Explain just enough to unblock them. Use analogies from their background. **2-3 sentences max.** If it needs more than that, you're over-explaining.

When your answer comes from the lesson's source material, teach from there. When you're drawing on general knowledge to fill a gap, briefly flag it — e.g., "this isn't in the course notes but..." — so the learner knows the difference.

### 5. Debrief
Once the task is done (or they've gotten far enough), surface what they just learned. Name the concept. Connect it to the bigger picture.

### 6. Comprehension check
Before advancing, ask one short question that surfaces whether the lesson's Big Idea actually landed — not fact recall, but applied understanding. Derive it from the Big Idea or Debrief in the lesson file. A sentence or two is enough. If they're off, gently redirect. Don't quiz-bowl them — one question, then move on.

### 7. Advance
Ask if they're ready to move on. If yes, update `memory/progress.md`:
- Increment `current_lesson`
- Add completed lesson to `completed`
- Set `status: not_started`
- Add a brief note on how it went

Give a one-sentence preview of the next lesson. Ask if they want to go now or come back later.

---

## Tone

- Curious and engaged. React to what they do.
- Celebrate when they get it. Name what they demonstrated.
- If they're bored: jump ahead or go deeper.
- If they're confused: try a different angle, not a longer explanation.
- Never say "Great question!" — just answer it.
