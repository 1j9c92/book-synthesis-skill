# Book Synthesis Skill

Most book tools give you a summary. This gives you a synthesis — every idea translated into your domain, your problems, your situation. The difference matters. A summary tells you what a book says. A synthesis tells you what it means for you, right now, given your actual work.

---

## What it does

Give it a book and it produces three things: a personalized synthesis where every example and "so what" is drawn from your world rather than the author's generic ones, a designed PDF where each concept gets a diagram matched to its structure (flow diagrams, loop diagrams, decision trees, comparison cards, leverage charts, timeline grids), and a clean markdown version for your notes system.

The visual design isn't decoration. Concepts that describe loops become loop diagrams. Comparisons become side-by-side cards. When the visual matches the concept's structure, you understand it faster and retain it longer.

---

## How it works

The first time you use it, it asks 12-13 questions (about 5 minutes) to build a reader profile — your role, how you think, what you're working on, where you tend to stall. It saves this as `READER_PROFILE.md`. After that, just name the book and it handles the rest automatically.

---

## Installation

**Claude Code:** Copy the `book-synthesis/` folder into your `.claude/skills/` directory.

**Cowork:** Download `book-synthesis.skill` from the releases page, open Cowork > Settings > Skills > Install from file, and select it.

---

## Usage

Say things like:

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

Your profile covers six things: your role and the decisions you make or influence, how you learn best, what you're building toward and what drains you, where you tend to stall, the worlds you want examples pulled from, and your default length and format preferences.

To update it at any time, say: *"Update my reader profile."*

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

MIT License
