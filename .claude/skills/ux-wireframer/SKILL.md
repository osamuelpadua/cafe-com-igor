---
name: ux-wireframer
description: Generate UX wireframes and UI mockups as interactive HTML artifacts. Use this skill whenever the user mentions wireframe, wireframing, mockup, UI layout, page structure, lo-fi design, hi-fi design, UX flow, screen design, interface layout, landing page layout, app screen, or any request to visualize how a page or interface should look before building it. Also trigger when the user shares a copy document, briefing, or content list and wants to see how it translates visually into a screen. Produces annotated wireframes ranging from low-fidelity grayscale sketches to high-fidelity styled mockups — all as interactive HTML rendered directly in chat.
---

# UX Wireframer / UI Generator

This skill produces wireframes and UI mockups as **interactive HTML artifacts** rendered directly in the chat. Outputs range from rough lo-fi sketches to detailed hi-fi mockups depending on what the user needs.

## When this skill is called

The user wants to visualize a page, screen, or interface. They may provide:
- A copy document or content list (like a landing page script)
- A briefing or feature description
- A screenshot of an existing page to redesign
- A verbal description of what they want
- A combination of the above

Your job: **translate that input into a rendered visual wireframe or mockup**.

---

## Step 1 — Assess Fidelity Level

Before building, determine the fidelity level. If not stated, infer from context:

| Signal | Fidelity |
|---|---|
| "wireframe", "sketch", "lo-fi", "structure only" | **Lo-fi** |
| "mockup", "layout", "how it looks", no strong signal | **Mid-fi** |
| "high fidelity", "close to final", "with branding/colors" | **Hi-fi** |
| Brand colors/fonts provided | **Hi-fi** |

If unclear, default to **mid-fi** and note that the user can request a different fidelity.

---

## Step 2 — Extract Page Architecture

From the input material, identify:

1. **Sections** — what are the distinct blocks? (hero, pain block, solution, benefits, CTA, FAQ, footer…)
2. **Content per section** — headline, subheadline, body copy, images, buttons, lists
3. **Hierarchy** — what is most important on the page?
4. **Interaction points** — CTAs, forms, accordions, modals, tabs
5. **Repeating patterns** — cards, testimonial blocks, icon+text rows

For landing pages specifically, read `references/landing-page-patterns.md` for section archetypes and conversion patterns.

---

## Step 3 — Choose Output Mode

### Lo-fi Wireframe
- Grayscale only (`#F5F5F5`, `#E0E0E0`, `#BDBDBD`, `#757575`, `#212121`)
- No real fonts — use placeholder bars of varying widths for text
- Boxes with × for images
- Label each section clearly (e.g. `[HERO]`, `[BENEFITS]`, `[CTA]`)
- Show structure, spacing, and hierarchy — not content
- Add sticky annotation layer: numbered callouts explaining layout decisions

### Mid-fi Wireframe
- Grayscale + one accent color for CTAs and key highlights
- Real copy text (pulled from user's content) in real fonts
- Actual section headings visible
- Images shown as colored placeholder boxes with label
- Buttons styled with proper shape/size, no final color
- Annotations optional — include if layout has complex decisions

### Hi-fi Mockup
- Full color, real typography (Google Fonts)
- Brand colors if provided; otherwise derive a palette from context (product type, tone, audience)
- Real copy, real hierarchy, real spacing
- Styled components: buttons, cards, badges, dividers
- Hover states on interactive elements (CSS only)
- Mobile-responsive layout
- Read `references/hi-fi-components.md` for reusable component patterns

---

## Step 4 — Build the HTML Artifact

### Structure rules

```
Page
├── Sticky nav (if multi-section page)
├── Sections (in copy order)
│   ├── Each section has: wrapper > container > content
│   └── Max content width: 860px centered
├── Floating annotation panel (lo-fi/mid-fi only)
└── Section jump links (for long pages)
```

### CSS architecture

```css
:root {
  /* Always define these */
  --max-width: 860px;
  --section-padding: 80px 24px;
  --border-radius: 8px;

  /* Fidelity-specific */
  /* Lo-fi: grays only */
  /* Mid-fi: grays + 1 accent */
  /* Hi-fi: full brand palette */
}
```

### Required behaviors
- Each section visually distinct (alternating bg, border, or spacing)
- CTAs must look like real buttons (not just text)
- Mobile breakpoint at 640px minimum
- Scroll is smooth; sections have `id` anchors
- Long pages (>6 sections): include a floating mini-nav or progress indicator

### Annotation system (lo-fi and mid-fi)
Add a collapsible annotation panel to the side or bottom. Number each major layout decision:

```
① Hero uses full-width background + centered text to maximize authority
② Pain block uses 3-column icon grid — scannable without reading
③ CTA button sticky on mobile scroll
```

---

## Step 5 — Deliver and Explain

After the artifact renders:

1. **Name each section** you built and why it's in that order
2. **Flag any assumptions** made where input was ambiguous
3. **Offer next steps**: fidelity upgrade, specific section redesign, mobile view, or alternative layout

Keep explanation concise — the wireframe is the deliverable, not the explanation.

---

## Special Cases

### Landing Page (sales page, VSL page)
Follow AIDA + PAS hybrid structure. Read `references/landing-page-patterns.md` for the full section sequence and conversion notes.

### App Screen / Dashboard
Use a sidebar + main content layout by default. Each panel is a separate component. Read `references/app-screen-patterns.md`.

### Email Template
Fixed 600px width, inline styles, table-based layout. Read `references/email-patterns.md`.

### Multi-page flow / funnel
Render each screen as a tabbed panel. Add click-through simulation between steps.

---

## Output Quality Checklist

Before presenting, verify:

- [ ] Correct number of sections matches input content
- [ ] Hierarchy is visually clear (size, weight, spacing)
- [ ] CTAs are prominent and above the fold on at least one screen
- [ ] Mobile layout doesn't break at 375px
- [ ] Annotations explain at least 3 non-obvious layout decisions
- [ ] No Lorem Ipsum if real copy was provided
- [ ] Fidelity is consistent throughout (don't mix lo-fi boxes with hi-fi buttons)

---

## Reference Files

| File | When to read |
|---|---|
| `references/landing-page-patterns.md` | Any sales/landing page wireframe |
| `references/hi-fi-components.md` | Hi-fi mockups needing styled components |
| `references/app-screen-patterns.md` | App screens, dashboards, SaaS UIs |
| `references/annotation-guide.md` | When adding detailed UX annotations |
