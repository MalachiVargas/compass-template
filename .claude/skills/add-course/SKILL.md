---
name: add-course
description: Add a new course to Compass from raw source material. Use when the user invokes /add-course or wants to add a new course to the platform. Reads source material, generates the course manifest and lesson files with embedded source, and registers the course in the platform.
---

# Add Course — Course Generator

This skill scaffolds a new course from raw source material. The source drives everything — lesson files embed the relevant source sections so the lesson skill is always grounded in accurate content.

## Before Starting

Ask the user for:
1. The course number (e.g., `02`)
2. The course name/slug (e.g., `nextjs-fundamentals`)
3. Confirmation that source material is placed at `courses/{n}-{name}/source/`

If source material isn't there yet, tell them to drop it in that folder first and then re-run `/add-course`.

---

## Generation Process

### 1. Read the source
Read all files in `courses/{n}-{name}/source/`. Understand the full content — topics covered, structure, key concepts.

### 2. Identify lessons
Based on the source, identify natural lesson breaks. Aim for 6-10 lessons. Each lesson should:
- Cover one coherent concept or skill
- Be completable in a single session
- Have a clear "big idea" that can be turned into a task

### 3. Generate `course.md`
Write `courses/{n}-{name}/course.md`:

```markdown
---
id: {n}
title: {Course Title}
dir: courses/{n}-{name}
---

# {Course Title}

{1-2 sentence description}

## Lessons

| # | Title | File |
|---|-------|------|
| 1 | {Lesson Title} | courses/{n}-{name}/lessons/01-{slug}.md |
...
```

### 4. Generate lesson files
For each lesson, write `courses/{n}-{name}/lessons/{nn}-{slug}.md` with this structure:

```markdown
# Lesson N: {Title}

## Source Material

> From the course source — use this as the factual ground truth when answering questions or designing tasks.

{Paste the relevant raw source excerpts for this lesson here}

---

## The Big Idea

{One paragraph — the core insight this lesson teaches}

## Why It Matters

{One paragraph — why this unlocks something for the learner}

## Tasks

### Beginner
{Task for someone new to this concept}

### Intermediate
{Task requiring more experience}

### Advanced
{Task that pushes understanding to its limits}

## Common Questions

{3-5 questions a learner would likely ask, with concise answers grounded in the source}

## Debrief

{A closing statement that names what the learner just demonstrated and connects it to the bigger picture}

## Teaches

{Comma-separated list of concept slugs this lesson introduces, e.g. `[concept-a, concept-b]`}
```

### 5. Update `memory/progress.md`
Add the new course to the progress file:

```
{n}-{name}:
  current_lesson: 1
  difficulty_tier: ""
  status: not_started
  completed: []
  mastered_concepts: []
  notes: ""
```

Do NOT change `current_course` — the learner chooses when to switch courses.

---

## After Generation

Tell the user:
- How many lessons were created
- A one-sentence summary of each lesson
- How to switch to the new course: update `current_course` in `memory/progress.md` to `courses/{n}-{name}` and run `/lesson`
