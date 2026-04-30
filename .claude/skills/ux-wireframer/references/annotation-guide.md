# UX Annotation Guide

Annotations explain *why* a layout decision was made, not just *what* it is. They are essential in lo-fi and mid-fi wireframes, optional in hi-fi.

---

## Annotation Types

### 1. Layout Decision
Why this structure was chosen over alternatives.

> ① Hero uses single-column centered layout to force sequential reading and prevent attention split between headline and media.

### 2. Conversion Rationale
Why a specific placement improves conversion.

> ② First CTA appears above the fold to capture high-intent visitors who don't need to scroll.

### 3. UX Pattern Reference
Names the pattern being used and why it was chosen.

> ③ Pain list uses ❌ marker icons rather than bullet points — visual negativity cues increase emotional identification.

### 4. Content Assumption
Flags where copy, images, or data is placeholder.

> ④ [ASSUMPTION] Testimonial section uses 3 cards. If fewer than 3 real testimonials exist, collapse to 1 featured quote instead.

### 5. Interaction Note
Describes behavior on click, hover, or scroll.

> ⑤ FAQ items use native `<details>` accordion — no JavaScript required, works on all devices.

### 6. Responsive Note
Flags how a section transforms on mobile.

> ⑥ 3-column benefits grid collapses to 1 column on mobile (<640px). Icon stays above text.

---

## Annotation Panel HTML Template

Place this at the bottom of any wireframe HTML:

```html
<div class="annotation-panel" id="annotations">
  <button class="annotation-toggle" onclick="toggleAnnotations()">
    📋 Annotations (8)
  </button>
  <div class="annotation-body" id="annotation-body">
    <ol class="annotation-list">
      <li><strong>Hero layout:</strong> Single column forces sequential reading. Prevents attention split.</li>
      <li><strong>CTA above fold:</strong> High-intent visitors convert without scrolling.</li>
      <li><strong>Pain markers:</strong> ❌ icons increase emotional identification vs plain bullets.</li>
      <li><strong>Video position:</strong> After headline — visitor reads promise first, then sees proof.</li>
      <li><strong>Guarantee before final CTA:</strong> Risk reversal must appear at decision point, not after.</li>
      <li><strong>FAQ accordion:</strong> Native details element — zero JS, full accessibility.</li>
      <li><strong>Footer minimal:</strong> No outbound nav links — keeps conversion funnel closed.</li>
      <li><strong>[ASSUMPTION] Testimonials:</strong> 3 cards shown. Collapse to 1 featured quote if fewer available.</li>
    </ol>
  </div>
</div>

<style>
.annotation-panel {
  position: fixed;
  bottom: 20px; right: 20px;
  width: 340px;
  background: #1A1A2E;
  border: 1px solid #C9A84C;
  border-radius: 10px;
  font-family: system-ui, sans-serif;
  font-size: 13px;
  color: #fff;
  z-index: 9999;
  box-shadow: 0 8px 32px rgba(0,0,0,0.4);
}
.annotation-toggle {
  width: 100%;
  padding: 12px 16px;
  background: none;
  border: none;
  color: #C9A84C;
  font-weight: 700;
  font-size: 13px;
  cursor: pointer;
  text-align: left;
}
.annotation-body { padding: 0 16px 16px; display: block; }
.annotation-body.hidden { display: none; }
.annotation-list {
  margin: 0; padding-left: 20px;
  display: flex; flex-direction: column; gap: 10px;
}
.annotation-list li { line-height: 1.5; color: rgba(255,255,255,0.8); }
.annotation-list li strong { color: #C9A84C; }
</style>

<script>
function toggleAnnotations() {
  const body = document.getElementById('annotation-body');
  body.classList.toggle('hidden');
}
</script>
```

---

## Numbered Callout Markers (in-page)

To add numbered circles directly on wireframe elements:

```html
<div style="position:relative; display:inline-block;">
  <!-- your element -->
  <span class="callout-num" style="top:-10px; right:-10px;">①</span>
</div>
```

```css
.callout-num {
  position: absolute;
  width: 22px; height: 22px;
  background: #C9A84C;
  color: #0E1628;
  border-radius: 50%;
  font-size: 11px;
  font-weight: 700;
  display: flex; align-items: center; justify-content: center;
  z-index: 10;
}
```

---

## When to Annotate

**Always annotate:**
- Non-obvious section order
- Any section above or below where convention would place it
- Placeholder content assumptions
- Conversion-critical decisions (CTA placement, price reveal position, guarantee position)

**Annotate if notable:**
- Mobile behavior different from desktop
- Interaction patterns (accordion, tabs, modals)
- Copy assumptions made due to missing client content

**Don't annotate:**
- Standard patterns explained by their presence (a nav is a nav)
- Visual style choices (color, font) in lo-fi wireframes
- Every single element — annotations lose value when overused
