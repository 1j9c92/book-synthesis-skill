# Book Synthesis Skill

**Most book tools give you a summary. This gives you a synthesis — every idea translated into your domain, your problems, your actual situation.**

Not what the book says. What it means for you.

---

## What it does

Give it a book. It produces:

- A **personalized synthesis** where every example and "so what" is drawn from your world — not the author's generic ones
- A **designed PDF** with diagrams built for the concept: flow diagrams, loop diagrams, decision trees, comparison cards, leverage charts, timeline grids
- A **clean markdown version** for your notes system

---

## How it works

**First time:** It asks you 12–13 questions (~5 minutes) to build a reader profile — your role, how you think, what you're working on, where you stall. Saves it as `READER_PROFILE.md`.

**Every time after:** Just name the book. It loads your profile and does the translation automatically.

The visual design isn't decoration. Concepts that describe loops become loop diagrams. Comparisons become side-by-side cards. When the visual matches the concept's structure, you understand it faster and retain it longer.

---

## Installation

### Claude Code
Copy the `book-synthesis/` folder into your `.claude/skills/` directory.

### Cowork
1. Download `book-synthesis.skill` from the releases page
2. Open Cowork → Settings → Skills → Install from file
3. Select `book-synthesis.skill`

---

## Usage

Say any of:

- *"Synthesize [Book Title] for me"*
- *"Make me book notes for [Book Title]"*
- *"I just finished [Book Title] — help me apply it"*
- *"Translate [Book Title] into my work"*

---

## Output design

| Element | What it's for |
|---|---|
| Dark navy cover card | Title, reader context, framing |
| Section opener cards | One per idea — number, title, one-line thesis |
| Flow diagrams | Processes, sequences, cascades |
| Circular loop diagrams | Feedback loops, cycles, capability systems |
| Side-by-side comparisons | Before/after, good/bad, two competing approaches |
| 4-card grids | Frameworks with 4 components |
| Horizontal bar charts | Hierarchies, rankings, leverage maps |
| Decision trees | Logic flows, decision criteria |
| Timeline grids | Action plans, 30/60/90-day experiments |

---

## Reader profile

Your profile covers:

- **Work & context** — role, decisions you make or influence, persistent problems
- **Cognitive style** — how you learn best
- **Motivation & growth** — what you're building toward, what drains you
- **Blind spots** — where you stall, recurring feedback
- **Example domains** — the worlds you want examples pulled from
- **Output preferences** — default length and format

Update it any time: *"Update my reader profile."*

---

## File structure

```
book-synthesis/
├── SKILL.md                    # Core skill logic and onboarding flow
├── README.md                   # This file
└── references/
    ├── visual-principles.md    # Design system with HTML/CSS/SVG patterns
    └── synthesis-template.md   # Synthesis prompt, voice guidelines, quality checklist
```

---

## Why synthesis, not summary

A summary tells you what a book says. A synthesis tells you what it means — for you, right now, given your actual situation. The gap between those two things is why most reading doesn't change how you work.

This skill closes that gap by doing the translation explicitly: replacing the author's examples with yours, mapping each idea to your specific problems, and ending with concrete experiments rather than vague takeaways.

---

MIT License
