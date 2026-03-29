# Book Synthesis Skill

**Transform any business or nonfiction book into a deeply personalized synthesis — every idea translated into your domain, your problems, your life.**

Not a summary. A translation.

---

## What It Does

This skill takes any business or nonfiction book and produces:

- A **personalized synthesis** where every example, every connection, and every "so what" is drawn from your world — not the author's generic examples
- A **beautifully designed PDF** with high-quality visuals: flow diagrams, comparison matrices, loop diagrams, leverage charts, decision trees, timeline grids
- A **clean markdown version** for your notes system

The output looks like a premium briefing book written specifically for you — because it is.

---

## How It Works

**First time:** The skill walks you through 12–13 onboarding questions (about 5 minutes) to build your reader profile. It saves this as `READER_PROFILE.md` in your context folder.

**Every time after:** Just give it a book title. It loads your profile and personalizes everything automatically.

---

## Installation

### In Claude Code
```bash
# Install directly
claude skill install https://github.com/[your-username]/book-synthesis-skill
```

Or copy the `book-synthesis/` folder into your `.claude/skills/` directory.

### In Cowork
1. Download `book-synthesis.skill` from the releases page
2. Open Cowork → Settings → Skills → Install from file
3. Select `book-synthesis.skill`

---

## Usage

Once installed, trigger it by saying any of:

- *"Synthesize [Book Title] for me"*
- *"Make me personalized book notes for [Book Title]"*
- *"Translate [Book Title] into my work"*
- *"I just finished [Book Title] — help me apply it"*
- *"Create a book synthesis PDF for [Book Title]"*

---

## Output Design System

Every PDF uses a consistent visual language:

| Element | Purpose |
|---|---|
| Dark navy cover card | Book title, reader context, framing |
| Section opener cards | Chapter-style openers for each idea |
| Flow diagrams | Sequential processes, cascades, pipelines |
| Circular loop diagrams | Feedback loops, capability systems, cycles |
| Side-by-side comparisons | Before/after, good/bad, debate/inquiry |
| 4-card grids | Frameworks with 4 components |
| Horizontal bar charts | Hierarchies, rankings, leverage maps |
| Decision trees | Logic flows, decision criteria |
| Timeline grids | Action plans, 30/60/90-day experiments |
| So What callout cards | Concrete, immediate actions |

---

## Reader Profile

Your profile is saved to `READER_PROFILE.md` and covers:

- **Work & context** — your role, decisions, persistent problems
- **Cognitive style** — how you learn best
- **Motivation & growth** — what you're working on, what drains you
- **Blind spots** — where you stall, recurring feedback
- **Example domains** — the worlds you want examples drawn from
- **Output preferences** — default length and format

You can update your profile at any time by saying *"Update my reader profile"*.

---

## File Structure

```
book-synthesis/
├── SKILL.md                    # Core skill logic and onboarding flow
├── README.md                   # This file
└── references/
    ├── visual-principles.md    # Full design system with HTML/CSS/SVG patterns
    └── synthesis-template.md   # Synthesis prompt, voice guidelines, quality checklist
```

---

## Philosophy

Most book tools give you a summary. This skill gives you a synthesis — which is a different thing entirely.

A summary tells you what the book says. A synthesis tells you what it means, for you, given your specific situation. The difference is everything. Books are full of insights that never land because the reader can't see how they apply. This skill closes that gap by doing the translation work explicitly: replacing the author's examples with yours, connecting each idea to your specific problems, and giving you concrete experiments rather than vague inspiration.

The visual design is not decoration. It's signal. Concepts that describe loops become loop diagrams. Concepts that describe comparisons become side-by-side cards. When the visual matches the concept's structure, you understand it faster and remember it longer.

---

## Credits

Built for the Cowork/Claude Code plugin ecosystem. Inspired by the book synthesis workflow developed at [github.com/your-username].

Licensed under MIT.
