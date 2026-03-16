# Compass

An interactive course platform powered by Claude Code. Learners learn by doing tasks, not by reading docs or watching videos. Claude acts as a personalized guide — onboarding each learner, assigning tasks tied to their goals, and adapting to their experience level.

Comes with a full example course: **Claude Code in Action** (8 lessons).

---

## How It Works

1. Clone the repo and open it in Claude Code
2. Run `/start` — Claude interviews you about your background and goals
3. Run `/lesson` — Claude picks up where you left off and assigns a task
4. Do the task, ask questions, get debriefed, advance

All personalization is driven by `memory/user_profile.md` and `memory/progress.md`, which Claude writes and reads automatically.

---

## Skills

| Command | What it does |
|---------|--------------|
| `/start` | Onboards a new learner. Runs a 5-question interview, saves profile, kicks off lesson 1. Detects returning users and skips re-onboarding. |
| `/lesson` | Runs the current lesson. Reads progress, picks the right task level, debriefs, checks comprehension, advances. |
| `/add-course` | Scaffolds a new course from raw source material. Generates `course.md` and all lesson files with embedded source. |
| `/switch-course` | Switches the active course without losing progress in any other course. |

Skills live in `.claude/skills/`. Each skill is a markdown file — readable, editable, no code required.

---

## Adding a Course

1. Create a folder: `courses/{n}-{name}/source/`
2. Drop your raw source material (notes, transcripts, docs) into `source/`
3. Run `/add-course` — Claude reads the source, identifies lesson breaks, and generates all lesson files with source embedded

Each lesson file contains:
- **Source Material** — raw excerpts from your source, used as ground truth
- **Big Idea** — the core concept
- **Tasks** — beginner / intermediate / advanced variants
- **Common Questions** — pre-answered FAQs
- **Debrief** — closing framing
- **Connects To** — links to related lessons

---

## File Structure

```
compass/
├── CLAUDE.md                          # Platform instructions for Claude
├── memory/
│   ├── user_profile.md                # Written by /start, read by /lesson
│   └── progress.md                    # Tracks current course and lesson
├── courses/
│   └── 01-claude-code/
│       ├── course.md                  # Course manifest with lesson table
│       ├── source/                    # Raw source material
│       └── lessons/
│           ├── 01-architecture.md
│           └── ...
└── .claude/
    └── skills/
        ├── start/
        │   ├── SKILL.md
        │   └── evals/evals.json
        ├── lesson/
        │   ├── SKILL.md
        │   └── evals/evals.json
        ├── add-course/
        │   └── SKILL.md
        └── switch-course/
            └── SKILL.md
```

---

## Evals

Each skill has an `evals/evals.json` file with test cases that verify the skill behaves correctly. Each eval has a `prompt`, `expected_output`, and `expectations` checklist. Run them manually by simulating the prompt and checking Claude's response against the expectations.

---

## Requirements

- [Claude Code](https://claude.ai/code)
- An Anthropic API key
