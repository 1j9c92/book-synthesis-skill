# Visual Design Principles for Book Synthesis PDFs

This document defines the complete design system for book synthesis PDFs. Read this entire file before generating any PDF. The goal: every output should look like a premium, well-designed book — not a formatted Word document.

---

## Design System

### Color Palette

```css
:root {
  --navy:      #1B2A4A;   /* Primary background — covers, section openers */
  --navy-mid:  #243354;   /* Secondary navy — callout backgrounds */
  --orange:    #E07B39;   /* Concept numbers, accent rules, highlights */
  --blue:      #3A6EA8;   /* Domain/application callouts */
  --teal:      #2A7F6F;   /* "So what" / action items */
  --amber:     #C9A227;   /* Quotes, domain example labels */
  --red:       #B03A2E;   /* "Bad" examples, failure modes, warnings */
  --slate:     #4A5568;   /* Personal connection callouts */
  --gray-100:  #F7F8FA;   /* Light callout backgrounds */
  --gray-200:  #E8ECF0;   /* Table alternating rows, dividers */
  --text:      #1A202C;   /* Body text */
  --text-light:#4A5568;   /* Secondary text, captions */
  --white:     #FFFFFF;
}
```

### Typography

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Playfair+Display:wght@700;800&display=swap');

body { font-family: 'Inter', -apple-system, sans-serif; font-size: 11pt; line-height: 1.7; color: var(--text); }
h1   { font-family: 'Playfair Display', Georgia, serif; font-size: 32pt; font-weight: 800; }
h2   { font-family: 'Inter', sans-serif; font-size: 16pt; font-weight: 700; color: var(--navy); }
h3   { font-family: 'Inter', sans-serif; font-size: 12pt; font-weight: 600; }
.label { font-size: 8pt; font-weight: 600; letter-spacing: 0.12em; text-transform: uppercase; }
```

### Base CSS (include in every HTML output)

```css
* { box-sizing: border-box; margin: 0; padding: 0; }
body { background: white; max-width: 780px; margin: 0 auto; padding: 40px 48px; }
.page-break { page-break-after: always; }
hr.divider { border: none; border-top: 1px solid var(--gray-200); margin: 32px 0; }
p { margin-bottom: 14px; }
strong { font-weight: 600; }
```

---

## Page Structure

Every PDF follows this page sequence:

1. **Cover page** (full-bleed dark card)
2. **Table of contents** (optional for long syntheses)
3. **Why This Book / Framing** (1 page)
4. **Idea pages** (1–2 pages each) — always starts with a section opener card
5. **What to Do Next** (closing timeline grid)
6. **One-sentence closing card**

---

## The 9 Visual Element Types

For each idea, select the visual type that best matches the concept's structure:

| Concept structure | Visual type |
|---|---|
| Sequential process or steps | Flow diagram (linear) |
| Circular cause-and-effect | Loop diagram (circular) |
| Good vs. bad / before vs. after | Side-by-side comparison |
| Framework with 4 elements | 4-card grid |
| Hierarchy / ranking | Horizontal bar chart |
| Decision with branching paths | Decision tree (flowchart) |
| Core concept with 3–4 components | Triad / hub diagram |
| Action plan over time | Timeline grid |
| Callout with action | So-What card |

---

### 1. Cover Page

```html
<div class="cover" style="
  background: var(--navy);
  color: white;
  padding: 64px 56px;
  min-height: 320px;
  border-radius: 8px;
  margin-bottom: 48px;
">
  <div class="label" style="color: var(--orange); margin-bottom: 24px;">
    BOOK NOTES — PERSONALIZED SYNTHESIS
  </div>
  <h1 style="color: white; margin-bottom: 12px; line-height: 1.1;">[Book Title]</h1>
  <p style="color: rgba(255,255,255,0.65); font-style: italic; font-size: 13pt; margin-bottom: 32px;">[Author Name]</p>
  <div style="width: 56px; height: 3px; background: var(--orange); margin-bottom: 32px;"></div>
  <p style="color: rgba(255,255,255,0.85); font-size: 12pt; line-height: 1.6; max-width: 520px; margin-bottom: 40px;">
    [One-line framing: "Every idea translated for [reader role] at [context] — your domain, your problems, your next move."]
  </p>
  <div style="display: flex; gap: 48px;">
    <div>
      <div class="label" style="color: rgba(255,255,255,0.5); margin-bottom: 6px;">READER</div>
      <div style="color: white; font-weight: 600;">[Reader role / title]</div>
    </div>
    <div>
      <div class="label" style="color: rgba(255,255,255,0.5); margin-bottom: 6px;">CONTEXT</div>
      <div style="color: white; font-weight: 600;">[Reader's current situation]</div>
    </div>
  </div>
</div>
```

---

### 2. Section Opener Card (one per idea)

```html
<div class="section-opener" style="
  background: var(--navy);
  color: white;
  padding: 40px 48px;
  border-radius: 6px;
  margin-bottom: 28px;
">
  <div class="label" style="color: var(--orange); margin-bottom: 16px;">IDEA [N] OF [TOTAL]</div>
  <div style="font-size: 48pt; font-weight: 800; color: rgba(255,255,255,0.15); line-height: 1; margin-bottom: -8px;">[N]</div>
  <h2 style="color: white; font-size: 22pt; margin-bottom: 12px;">[Idea Title]</h2>
  <p style="color: rgba(255,255,255,0.7); font-size: 12pt; font-style: italic;">[One-line thesis of the idea]</p>
</div>
```

---

### 3. Flow Diagram (Linear Process)

Use for: sequential steps, cascades, handoff chains, pipelines.

```html
<div class="flow-diagram" style="background: var(--gray-100); border-radius: 8px; padding: 28px 32px; margin: 24px 0;">
  <div class="label" style="color: var(--text-light); margin-bottom: 20px;">[Diagram Title]</div>
  <div style="display: flex; align-items: center; flex-wrap: wrap; gap: 8px;">
    <!-- Repeat this block for each step -->
    <div style="background: var(--navy); color: white; padding: 12px 18px; border-radius: 6px; text-align: center; min-width: 100px;">
      <div style="font-size: 8pt; color: var(--orange); font-weight: 600; letter-spacing: 0.08em; margin-bottom: 4px;">01</div>
      <div style="font-size: 10pt; font-weight: 600;">[Step Name]</div>
      <div style="font-size: 8.5pt; color: rgba(255,255,255,0.7); margin-top: 4px;">[Brief description]</div>
    </div>
    <!-- Arrow between steps -->
    <div style="color: var(--orange); font-size: 18pt; font-weight: 300;">→</div>
    <!-- Next step block... -->
  </div>
  <p style="font-size: 9pt; color: var(--text-light); font-style: italic; margin-top: 14px;">[Caption explaining what the diagram shows]</p>
</div>
```

For iterative/feedback flows, add a dashed return arrow below the steps:
```html
<div style="text-align: right; color: var(--orange); font-size: 8.5pt; margin-top: 8px; border-top: 1px dashed var(--orange); padding-top: 6px;">
  ↩ [Later steps reshape earlier ones — the process is a loop, not a ladder]
</div>
```

---

### 4. Circular Loop Diagram (Reinforcing / Balancing)

Use for: feedback loops, capability loops, virtuous/vicious cycles.

```html
<div style="background: var(--gray-100); border-radius: 8px; padding: 28px; margin: 24px 0;">
  <div class="label" style="color: var(--text-light); margin-bottom: 20px;">[Diagram Title] — [Caption like "Weaken any node and the loop degrades"]</div>
  <svg viewBox="0 0 400 260" xmlns="http://www.w3.org/2000/svg" style="width: 100%; max-width: 440px; display: block; margin: 0 auto;">
    <!-- Top node -->
    <rect x="140" y="10" width="120" height="44" rx="6" fill="#1B2A4A"/>
    <text x="200" y="30" text-anchor="middle" fill="white" font-size="10" font-weight="600" font-family="Inter,sans-serif">[Node A]</text>
    <text x="200" y="46" text-anchor="middle" fill="rgba(255,255,255,0.65)" font-size="8" font-family="Inter,sans-serif">[Brief label]</text>
    <!-- Right node -->
    <rect x="280" y="108" width="120" height="44" rx="6" fill="#3A6EA8"/>
    <text x="340" y="128" text-anchor="middle" fill="white" font-size="10" font-weight="600" font-family="Inter,sans-serif">[Node B]</text>
    <text x="340" y="144" text-anchor="middle" fill="rgba(255,255,255,0.75)" font-size="8" font-family="Inter,sans-serif">[Brief label]</text>
    <!-- Bottom node — use var(--red) if this is the weak link -->
    <rect x="140" y="206" width="120" height="44" rx="6" fill="#C9A227"/>
    <text x="200" y="226" text-anchor="middle" fill="white" font-size="10" font-weight="600" font-family="Inter,sans-serif">[Node C]</text>
    <text x="200" y="242" text-anchor="middle" fill="rgba(255,255,255,0.75)" font-size="8" font-family="Inter,sans-serif">[Brief label]</text>
    <!-- Left node -->
    <rect x="0" y="108" width="120" height="44" rx="6" fill="#2A7F6F"/>
    <text x="60" y="128" text-anchor="middle" fill="white" font-size="10" font-weight="600" font-family="Inter,sans-serif">[Node D]</text>
    <text x="60" y="144" text-anchor="middle" fill="rgba(255,255,255,0.75)" font-size="8" font-family="Inter,sans-serif">[Brief label]</text>
    <!-- Arrows connecting nodes clockwise -->
    <path d="M 200 54 Q 300 70 300 108" stroke="#E07B39" stroke-width="2" fill="none" marker-end="url(#arrow)"/>
    <path d="M 280 152 Q 260 206 260 206" stroke="#E07B39" stroke-width="2" fill="none" marker-end="url(#arrow)"/>
    <path d="M 140 228 Q 60 210 60 152" stroke="#E07B39" stroke-width="2" fill="none" marker-end="url(#arrow)"/>
    <path d="M 60 108 Q 80 54 140 32" stroke="#E07B39" stroke-width="2" fill="none" marker-end="url(#arrow)"/>
    <!-- Arrow labels on paths -->
    <text x="280" y="88" fill="#E07B39" font-size="8" font-family="Inter,sans-serif" text-anchor="middle">[feeds]</text>
    <text x="235" y="200" fill="#E07B39" font-size="8" font-family="Inter,sans-serif" text-anchor="middle">[generates]</text>
    <text x="60" y="190" fill="#E07B39" font-size="8" font-family="Inter,sans-serif" text-anchor="middle">[creates]</text>
    <text x="90" y="72" fill="#E07B39" font-size="8" font-family="Inter,sans-serif" text-anchor="middle">[informs]</text>
    <!-- Arrow marker definition -->
    <defs>
      <marker id="arrow" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto">
        <path d="M0,0 L0,6 L8,3 z" fill="#E07B39"/>
      </marker>
    </defs>
  </svg>
</div>
```

To show a **broken weak link**, change that node's fill to `#B03A2E` and add a dashed red border:
```html
<rect x="140" y="206" width="120" height="44" rx="6" fill="#B03A2E" stroke="#E07B39" stroke-width="2" stroke-dasharray="4,2"/>
```

---

### 5. Side-by-Side Comparison (Before/After, Good/Bad)

Use for: debate vs. inquiry, strategy vs. not-strategy, failure mode vs. correct approach.

```html
<div style="display: grid; grid-template-columns: 1fr auto 1fr; gap: 0; margin: 24px 0; border-radius: 8px; overflow: hidden;">
  <!-- Left panel (bad/before) -->
  <div style="background: #B03A2E; padding: 24px; color: white;">
    <div class="label" style="color: rgba(255,255,255,0.7); margin-bottom: 12px;">[LEFT LABEL — e.g., "DEBATE MODE"]</div>
    <p style="font-size: 12pt; font-weight: 700; margin-bottom: 16px;">[Central question or framing]</p>
    <div style="font-size: 10pt; line-height: 1.6; color: rgba(255,255,255,0.9);">
      [Content — positions, arguments, outcomes]
    </div>
    <div style="margin-top: 16px; padding-top: 12px; border-top: 1px solid rgba(255,255,255,0.2);">
      <strong style="font-size: 10pt;">Result:</strong> [Negative outcome]
    </div>
  </div>
  <!-- Center arrow -->
  <div style="background: var(--gray-200); display: flex; align-items: center; justify-content: center; padding: 0 16px; color: var(--navy); font-size: 20pt;">→</div>
  <!-- Right panel (good/after) -->
  <div style="background: #2A7F6F; padding: 24px; color: white;">
    <div class="label" style="color: rgba(255,255,255,0.7); margin-bottom: 12px;">[RIGHT LABEL — e.g., "INQUIRY MODE"]</div>
    <p style="font-size: 12pt; font-weight: 700; margin-bottom: 16px;">[Central question or framing]</p>
    <div style="font-size: 10pt; line-height: 1.6; color: rgba(255,255,255,0.9);">
      [Content — collaborative approach, questions asked]
    </div>
    <div style="margin-top: 16px; padding-top: 12px; border-top: 1px solid rgba(255,255,255,0.2);">
      <strong style="font-size: 10pt;">Result:</strong> [Positive outcome]
    </div>
  </div>
</div>
```

---

### 6. Four-Card Grid (Frameworks with 4 Components)

Use for: 4-step systems, hallmarks of a concept, management system components, options.

```html
<div style="background: var(--gray-100); border-radius: 8px; padding: 24px; margin: 24px 0;">
  <div class="label" style="color: var(--text-light); margin-bottom: 20px;">[FRAMEWORK TITLE]</div>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 12px;">
    <!-- Card 1 -->
    <div style="background: var(--navy); padding: 20px; border-radius: 6px; color: white;">
      <div class="label" style="color: var(--orange); margin-bottom: 8px;">1 — [COMPONENT NAME]</div>
      <p style="font-size: 10pt; color: rgba(255,255,255,0.9); line-height: 1.6;">[Description of this component]</p>
    </div>
    <!-- Card 2 -->
    <div style="background: #243354; padding: 20px; border-radius: 6px; color: white;">
      <div class="label" style="color: var(--orange); margin-bottom: 8px;">2 — [COMPONENT NAME]</div>
      <p style="font-size: 10pt; color: rgba(255,255,255,0.9); line-height: 1.6;">[Description]</p>
    </div>
    <!-- Card 3 -->
    <div style="background: #3A6EA8; padding: 20px; border-radius: 6px; color: white;">
      <div class="label" style="color: rgba(255,255,255,0.8); margin-bottom: 8px;">3 — [COMPONENT NAME]</div>
      <p style="font-size: 10pt; color: rgba(255,255,255,0.9); line-height: 1.6;">[Description]</p>
    </div>
    <!-- Card 4 -->
    <div style="background: #2A7F6F; padding: 20px; border-radius: 6px; color: white;">
      <div class="label" style="color: rgba(255,255,255,0.8); margin-bottom: 8px;">4 — [COMPONENT NAME]</div>
      <p style="font-size: 10pt; color: rgba(255,255,255,0.9); line-height: 1.6;">[Description]</p>
    </div>
  </div>
</div>
```

---

### 7. Horizontal Bar Chart (Hierarchy / Ranking)

Use for: leverage point hierarchies, priority rankings, strength comparisons.

```html
<div style="background: var(--gray-100); border-radius: 8px; padding: 24px 28px; margin: 24px 0;">
  <div class="label" style="color: var(--text-light); margin-bottom: 6px;">[CHART TITLE]</div>
  <p style="font-size: 9pt; color: var(--text-light); margin-bottom: 20px; font-style: italic;">Bar width = relative leverage / importance</p>
  <!-- Repeat this block; adjust width% per item's relative value -->
  <div style="margin-bottom: 8px; display: flex; align-items: center; gap: 12px;">
    <div style="font-size: 9pt; color: var(--text-light); text-align: right; min-width: 160px;">[Item label]</div>
    <div style="background: var(--gray-200); height: 28px; border-radius: 3px; width: 20%; display: flex; align-items: center; padding: 0 10px;">
      <span style="font-size: 8.5pt; color: var(--text-light);">[value or note]</span>
    </div>
  </div>
  <!-- High-leverage items get wider bars and darker color -->
  <div style="margin-bottom: 8px; display: flex; align-items: center; gap: 12px;">
    <div style="font-size: 9pt; color: var(--navy); font-weight: 600; text-align: right; min-width: 160px;">[High-leverage item]</div>
    <div style="background: var(--navy); height: 28px; border-radius: 3px; width: 80%; display: flex; align-items: center; padding: 0 10px;">
      <span style="font-size: 8.5pt; color: white; font-weight: 600;">[value or note]</span>
    </div>
  </div>
  <div style="display: flex; justify-content: space-between; margin-top: 12px;">
    <span style="font-size: 8pt; color: var(--text-light);">← Where organizations spend most effort</span>
    <span style="font-size: 8pt; color: var(--text-light);">Where the real leverage lives →</span>
  </div>
</div>
```

---

### 8. Decision Tree / Flowchart

Use for: clarify workflows, decision logic, "does this qualify as X" tests.

```html
<div style="background: var(--gray-100); border-radius: 8px; padding: 28px; margin: 24px 0;">
  <div class="label" style="color: var(--text-light); margin-bottom: 20px;">[DECISION TREE TITLE]</div>
  <svg viewBox="0 0 500 300" xmlns="http://www.w3.org/2000/svg" style="width: 100%; display: block;">
    <!-- Start node (rectangle) -->
    <rect x="170" y="10" width="160" height="40" rx="5" fill="#1B2A4A"/>
    <text x="250" y="34" text-anchor="middle" fill="white" font-size="10" font-weight="600" font-family="Inter,sans-serif">[STARTING ITEM]</text>
    <!-- Arrow down -->
    <line x1="250" y1="50" x2="250" y2="80" stroke="#1B2A4A" stroke-width="2" marker-end="url(#arr2)"/>
    <!-- Decision diamond -->
    <polygon points="250,80 330,120 250,160 170,120" fill="#C9A227"/>
    <text x="250" y="116" text-anchor="middle" fill="white" font-size="9" font-weight="600" font-family="Inter,sans-serif">[Question?]</text>
    <text x="250" y="130" text-anchor="middle" fill="rgba(255,255,255,0.8)" font-size="8" font-family="Inter,sans-serif"></text>
    <!-- No branch (left) -->
    <line x1="170" y1="120" x2="80" y2="120" stroke="#B03A2E" stroke-width="2" marker-end="url(#arr2)"/>
    <text x="125" y="113" text-anchor="middle" fill="#B03A2E" font-size="8" font-family="Inter,sans-serif">No</text>
    <rect x="10" y="100" width="70" height="40" rx="4" fill="#B03A2E"/>
    <text x="45" y="124" text-anchor="middle" fill="white" font-size="9" font-weight="600" font-family="Inter,sans-serif">[No path]</text>
    <!-- Yes branch (right) -->
    <line x1="330" y1="120" x2="420" y2="120" stroke="#2A7F6F" stroke-width="2" marker-end="url(#arr2)"/>
    <text x="375" y="113" text-anchor="middle" fill="#2A7F6F" font-size="8" font-family="Inter,sans-serif">Yes</text>
    <rect x="420" y="100" width="70" height="40" rx="4" fill="#2A7F6F"/>
    <text x="455" y="124" text-anchor="middle" fill="white" font-size="9" font-weight="600" font-family="Inter,sans-serif">[Yes path]</text>
    <!-- Arrow marker -->
    <defs>
      <marker id="arr2" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto">
        <path d="M0,0 L0,6 L8,3 z" fill="#1B2A4A"/>
      </marker>
    </defs>
  </svg>
</div>
```

---

### 9. Closing Timeline Grid (Action Plan)

Use for: "What to do next" sections — organize actions by timeframe.

```html
<div style="border: 1px solid var(--gray-200); border-radius: 8px; overflow: hidden; margin: 24px 0;">
  <div style="display: grid; grid-template-columns: repeat(4, 1fr);">
    <!-- Column headers -->
    <div style="background: var(--navy); padding: 12px 16px; color: white;">
      <div class="label" style="color: var(--orange); font-size: 8pt;">WEEK 1–2</div>
    </div>
    <div style="background: #243354; padding: 12px 16px; color: white;">
      <div class="label" style="color: var(--orange); font-size: 8pt;">MONTH 1</div>
    </div>
    <div style="background: #3A6EA8; padding: 12px 16px; color: white;">
      <div class="label" style="color: rgba(255,255,255,0.8); font-size: 8pt;">MONTH 2</div>
    </div>
    <div style="background: #2A7F6F; padding: 12px 16px; color: white;">
      <div class="label" style="color: rgba(255,255,255,0.8); font-size: 8pt;">MONTH 3</div>
    </div>
    <!-- Content cells -->
    <div style="padding: 16px; border-right: 1px solid var(--gray-200); border-top: 1px solid var(--gray-200);">
      <p style="font-size: 9.5pt; font-weight: 600; color: var(--navy); margin-bottom: 8px;">① [Action title]</p>
      <p style="font-size: 9pt; color: var(--text); line-height: 1.5;">[What to do and why it matters]</p>
    </div>
    <div style="padding: 16px; border-right: 1px solid var(--gray-200); border-top: 1px solid var(--gray-200);">
      <p style="font-size: 9.5pt; font-weight: 600; color: var(--navy); margin-bottom: 8px;">② [Action title]</p>
      <p style="font-size: 9pt; color: var(--text); line-height: 1.5;">[What to do]</p>
    </div>
    <div style="padding: 16px; border-right: 1px solid var(--gray-200); border-top: 1px solid var(--gray-200);">
      <p style="font-size: 9.5pt; font-weight: 600; color: var(--navy); margin-bottom: 8px;">③ [Action title]</p>
      <p style="font-size: 9pt; color: var(--text); line-height: 1.5;">[What to do]</p>
    </div>
    <div style="padding: 16px; border-top: 1px solid var(--gray-200);">
      <p style="font-size: 9.5pt; font-weight: 600; color: var(--navy); margin-bottom: 8px;">④ [Action title]</p>
      <p style="font-size: 9pt; color: var(--text); line-height: 1.5;">[What to do]</p>
    </div>
  </div>
</div>
```

---

## The 4 Callout Block Types

Use these throughout the body to distinguish content layers. Never use plain text blockquotes.

### Concept Block (navy left border)
```html
<div style="border-left: 4px solid var(--navy); background: var(--gray-100); padding: 16px 20px; margin: 20px 0; border-radius: 0 6px 6px 0;">
  <div class="label" style="color: var(--navy); margin-bottom: 8px;">THE PRINCIPLE</div>
  <p style="font-size: 10.5pt; color: var(--text);">[Core concept statement]</p>
</div>
```

### Domain Application Block (amber left border)
```html
<div style="border-left: 4px solid var(--amber); background: #FDF8EC; padding: 16px 20px; margin: 20px 0; border-radius: 0 6px 6px 0;">
  <div class="label" style="color: var(--amber); margin-bottom: 8px;">IN YOUR DOMAIN</div>
  <p style="font-size: 10.5pt; color: var(--text);">[Domain-specific example drawn from reader profile]</p>
</div>
```

### Personal Connection Block (slate left border + tinted)
```html
<div style="border-left: 4px solid var(--slate); background: #F0F2F5; padding: 16px 20px; margin: 20px 0; border-radius: 0 6px 6px 0;">
  <div class="label" style="color: var(--slate); margin-bottom: 8px;">CONNECTED TO YOUR SITUATION</div>
  <p style="font-size: 10.5pt; color: var(--text); font-style: italic;">[Direct connection to reader's specific challenges, goals, or blind spots]</p>
</div>
```

### So What Block (teal background — most important)
```html
<div style="background: var(--teal); padding: 18px 22px; margin: 24px 0; border-radius: 6px; color: white;">
  <div class="label" style="color: rgba(255,255,255,0.7); margin-bottom: 8px;">→ SO WHAT</div>
  <p style="font-size: 11pt; font-weight: 600; line-height: 1.6;">[One concrete action or reframe this person can act on immediately]</p>
</div>
```

---

## Closing Card

Every synthesis ends with a full-width dark card containing the one sentence that carries forward.

```html
<div style="background: var(--navy); padding: 48px 56px; border-radius: 8px; text-align: center; margin-top: 48px;">
  <div class="label" style="color: rgba(255,255,255,0.5); margin-bottom: 24px;">ONE SENTENCE TO CARRY FORWARD</div>
  <p style="font-size: 16pt; color: white; font-style: italic; line-height: 1.7; max-width: 560px; margin: 0 auto 24px;">
    "[The single most important sentence from the synthesis — the one that, if remembered, changes how the reader sees their work]"
  </p>
  <div style="width: 56px; height: 3px; background: var(--orange); margin: 0 auto 20px;"></div>
  <p style="color: rgba(255,255,255,0.5); font-size: 9pt;">That is the book. The rest is application.</p>
</div>
```

---

## PDF Generation Command

After generating the complete HTML file:

```bash
pip install weasyprint --break-system-packages 2>/dev/null
weasyprint [input.html] [output.pdf]
```

If weasyprint fails, fall back to:
```bash
pip install pdfkit --break-system-packages 2>/dev/null
python3 -c "import pdfkit; pdfkit.from_file('[input.html]', '[output.pdf]')"
```

---

## Design Anti-Patterns to Avoid

- **No blank pages.** Every page earns its space. Use callout cards, pull quotes, or section openers instead of white space.
- **No yellow highlight treatment.** Don't simulate a digital marker — use styled callout blocks instead.
- **No text-only diagrams.** "A → B → C" in plain text is not a diagram. If it needs to show a connection or flow, it needs a visual.
- **No unbroken wall-of-text sections.** Every 2–3 paragraphs should have a visual element, callout block, or table to break the flow.
- **No inconsistent visual vocabulary.** Pick your callout colors and stick to them — navy concept blocks, amber domain blocks, teal so-what blocks — every time.
- **No generic examples.** If an example doesn't reference the reader's domain, rewrite it until it does.
