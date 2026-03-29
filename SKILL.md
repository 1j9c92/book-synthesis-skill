---
name: book-synthesis
description: Transform any business or nonfiction book into a deeply personalized synthesis — every idea translated into the reader's domain, problems, cognitive style, and life. Produces a beautifully designed PDF with visuals (flow diagrams, comparison matrices, process flows, decision trees, reinforcing loop diagrams, leverage charts) plus a markdown version. Use this skill whenever a user mentions a book they want synthesized, wants personalized book notes, asks for a "translation" of a book to their work, or says things like "synthesize this for me," "make me book notes," "turn this into something I can actually use," "I just read X — help me apply it," or uploads a book PDF and wants insight. Also trigger when a user wants to build a personal reading system or library of personalized notes. First-time users go through a one-time onboarding (12–13 questions, ~5 minutes) to build their READER_PROFILE.md. After that, every synthesis is fully personalized automatically — no re-onboarding needed.
---

# Book Synthesis Skill

This skill transforms any business or nonfiction book into a personalized synthesis — not a summary, but a translation. The reader's domain, daily problems, and cognitive style replace the book's generic examples. The output is a visually rich PDF and a markdown file, both designed to deliver immediate, applied insight.

## Quick Decision Tree

```
Does READER_PROFILE.md exist?
├── No → Run Onboarding (Section 1), save profile, then proceed to synthesis
└── Yes → Load profile, ask for book, proceed to synthesis (Section 2)
```

---

## Section 1 — Onboarding (First-Time Use Only)

When no profile exists, tell the user:

> "Before we synthesize your first book, I'm going to ask you 12–13 questions to build your reader profile. This happens once — after that, every book synthesis is personalized to you automatically. Takes about 5 minutes."

Then ask the questions **one phase at a time** — wait for responses before moving to the next phase. Don't dump all questions at once.

### Phase 1 — Work & Context

1. What's your current role, and what do you actually spend most of your week doing?
2. What kinds of decisions do you make or influence? Even if small or execution-level — be specific.
3. What are 2–3 problems that keep coming up in your work that you haven't fully solved?

### Phase 2 — Cognitive Style

4. When you read to learn something, what lands best for you? Pick one:
   - (a) Model or framework first, then examples
   - (b) Story first, then the concept
   - (c) Checklist or playbook you can run
   - (d) Visuals — diagrams, flow charts, maps

5. Do you read mostly to: learn new things, solve a specific problem you already have, or get new ideas and expand your thinking?

### Phase 3 — Motivation & Growth

6. What are you actively trying to get better at — professionally or personally?
7. What frustrates or drains you? Can be work or life — both are useful.
8. What does "a good week" look like for you? What made it good?

### Phase 4 — Blind Spots

9. Where do you most often stall or get stuck: starting something, finishing it, handing it off, or communicating about it?
10. Is there feedback you feel like you keep hearing — from a boss, partner, anyone — that you know has something to it even if it's uncomfortable?

### Phase 5 — Example Domains

11. What worlds do you want examples drawn from? List as many as you want — work domains, personal life areas, industries, hobbies. The more specific, the better.

### Phase 6 — Output Preferences

12. Default output length: short (3,000 words), medium (5,000), or long (10,000)?
13. Default output format: markdown note, PDF, or both?

### Saving the Profile

After all questions, write `READER_PROFILE.md` to the user's context folder (or current working directory if no context folder is specified). Use this format:

```markdown
# Reader Profile

## Identity & Context
[Role, what they do, decisions they make, persistent problems]

## Cognitive Style
[How they learn best, why they read]

## Motivation & Growth
[What they're working on, what drains them, what a good week looks like]

## Blind Spots & Growth Edges
[Where they stall, recurring feedback — phrased as behavioral preferences, not personal disclosures]

## Example Domains
[The worlds they want examples drawn from]

## Output Preferences
- Default length: [short / medium / long]
- Default format: [markdown / PDF / both]
```

Confirm with the user: "Your reader profile is saved. From now on, just tell me the book title and I'll personalize the synthesis for you automatically."

---

## Section 2 — Book Synthesis Workflow

### Step 1: Get the Book

Ask: *"What book would you like me to synthesize? You can give me the title and author, paste in key passages, or upload the book PDF. Do you want to change your default length or format for this one?"*

### Step 2: Load the Profile

Read `READER_PROFILE.md`. This is your personalization engine — every example, connection, and "so what" must be drawn from the reader's domains and mapped to their specific problems, cognitive style, and growth edges.

### Step 3: Generate the Synthesis

Follow the full synthesis instructions in `references/synthesis-template.md`. Key rules:
- **This is not a summary. It is a translation.** Replace all generic examples with domain-specific ones drawn from the reader's profile.
- Identify 5–10 of the book's most important ideas
- For each idea: state it clearly, explain the underlying principle (the why), give a domain-specific example, connect it explicitly to the reader's situation, and provide a concrete "so what"
- Match the voice to the reader's cognitive style preference from their profile
- Open with a 1-paragraph framing of why this book is relevant to this reader right now
- Close with a "what to do next" section — 3–5 concrete experiments, not homework

### Step 4: Generate the Visual PDF

Read `references/visual-principles.md` before generating any PDF. Every synthesis must include the full visual treatment:

- **Full-bleed cover card** — dark navy, book title, reader context
- **Section opener cards** for each idea — oversized number, bold title, one-line thesis
- **At least one purpose-built diagram per idea** — chosen from the 9 diagram types based on the concept's structure (see visual-principles.md)
- **4 callout block types** — concept (blue), domain application (amber), personal connection (slate), so what (green)
- **Closing action timeline grid** — cards organized by timeframe (this week / month 1 / month 2–3)

Generate as rich HTML → convert to PDF using `weasyprint`. Also save a clean markdown version.

### Step 5: Save Outputs

Save to the user's outputs folder:
- `[Book-Title]-Synthesis.pdf`
- `[Book-Title]-Synthesis.md`

Confirm with a direct link to both files.

---

## Section 3 — Quality Standards

**Personalization test:** Before finishing, ask: "Would a reader who didn't know this person recognize these as their examples?" If yes, you haven't personalized enough — rewrite.

**Visual test:** Every idea should have at least one diagram. If an idea describes a process → use a flow diagram. If it describes a comparison → use a side-by-side comparison card. If it describes a hierarchy → use a ranked bar chart or pyramid. If it describes a loop → use a circular flow diagram. Never leave a concept without visual support.

**Voice test:** Match the reader's stated cognitive style. Framework-first readers get the model before the story. Visual learners get a diagram before the explanation. Playbook readers get actionable checklists.

**Length discipline:** Short = 3,000 words. Medium = 5,000 words. Long = 10,000 words. Cut anything that doesn't land specifically for this reader. A shorter, sharper synthesis is always better than a padded one.

---

## Reference Files

- `references/visual-principles.md` — Full design system: color palette, typography, 9 diagram types with HTML/CSS/SVG patterns, callout block templates, cover and section opener patterns
- `references/synthesis-template.md` — Full synthesis prompt, per-idea structure, voice guidelines, length guidance
