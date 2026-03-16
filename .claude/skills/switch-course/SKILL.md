---
name: switch-course
description: Switch to a different course. Use when the user invokes /switch-course or says they want to change courses, start a new course, or switch to a different topic.
---

# Switch Course

## Process

1. **Read `memory/progress.md`** to get the list of available courses and current progress in each.

2. **Show the user their options** — list each course with its title (from its `course.md`) and current status:
   - Which lesson they're on
   - How many lessons completed
   - Whether it's in progress or not started

   Example:
   ```
   1. Claude Code in Action — Lesson 3/8, in progress
   2. Next.js Fundamentals — Lesson 1/6, not started
   ```

3. **Ask which course they want** — if only one other course exists, confirm it directly. If multiple, let them pick.

4. **Update `memory/progress.md`** — change `current_course` to the selected course directory.

5. **Confirm the switch** — tell them which course they're now in, which lesson they'll pick up at, and that they can run `/lesson` to start.

## Edge Cases

- If they're already on the course they asked for, tell them and do nothing.
- If they ask for a course that doesn't exist, list what's available and ask again.
- If there's only one course in the system, tell them and suggest `/add-course` to add another.
