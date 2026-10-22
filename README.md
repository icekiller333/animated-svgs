# SVG Factory

**Live:** https://icekiller333.github.io/animated-svgs/

Two tools in one page:

## Icon Gallery (the front door)
Free black-line SVG icons to pull into your projects. Search by name/tag/set, filter by tag,
view the **latest 20 (Newest)** or browse **grouped by set** (Cyberpunk, Basics, Snacks,
Nature, Objects). Every icon: **Copy SVG** or **Download** right on the card. Icons with a
signature animation offer it as a second version (Shape / Animated toggle). **Animate it**
hands any icon to the Animator.

## Animator
A single-screen, Figma-style studio — canvas on the left, inspector on the right
(sticky canvas on mobile). No wizard, no steps:

- **SVG** — paste code, upload, or use the sample; collapses to a one-line bar once loaded.
- **Effect** — 7 basic animations as tiles that preview their motion: **Draw on** (one click —
  the tool works out the stroke order itself), Fade, Pulse, Spin, Bounce, Slide, Wiggle.
  One speed slider + Loop/Once; delay and easing live under "More options."
- **Export** — copy the code or download the file, always at the bottom of the panel.

Exports are **one self-contained .svg with pure CSS animation inside the file** — no
JavaScript, no SMIL, nothing external — so they play wherever SVG images play: `<img>` tags,
HTML pages, Rise, Storyline (best effort), D2L.

Design rationale: `DESIGN-BRIEF-v4.md` (information theory / UX research + decisions).
Single file: `index.html`. Standalone gallery files live in `gallery/`.
