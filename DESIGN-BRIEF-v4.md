# SVG Factory v4 — Design Brief
Researched 2026-10-22 at Ken's direction before building. Status: APPROVED with the three decisions recorded at the bottom — building now. (Three small local edits from the aborted first pass — gallery-default tabs, gallery heading, search-box markup — are in the local index.html, unpushed; live site is still v3.2 + tags.)

## The problem, restated
One page was trying to be two products: an icon library (browse → copy → leave) and an animation studio (load → select → animate → export). Mixed together, each made the other feel cluttered. The fix is separation at the top level, then ruthless simplification inside each.

## What the research says

### 1. Hick's Law — decision time grows with choices
Decision time rises logarithmically with the number and complexity of options (T = a + b·log₂(n+1)). Every screen should present few choices; the rest gets categorized or deferred. Our Motion step showed 9 effects × 5 tuning controls × recolor × morph fields — the single biggest clutter source.
→ Cap each decision point: 6 effects, 1 always-visible tuning control (speed), the rest deferred.

### 2. Progressive disclosure (NN/g) — get the split right, max 2 levels
NN/g: initially show only the most important options; disclose the rest on request. Two failure modes: (a) wrong split — too much up front destroys focus, too little forces constant drilling; (b) weak progression cues — the way forward must be obvious and well-labeled ("information scent"). More than 2 disclosure levels reliably hurts usability; if you need a third, simplify the feature set or chunk harder instead.
→ Exactly 2 levels everywhere: primary controls visible; one clearly-labeled secondary ("More options") per area. No third level exists in v4.

### 3. Staged disclosure caveat (NN/g) — wizards fail when steps interlock
Staged (wizard) flows work when steps are independent. When users must bounce between steps — their hotel-booking study is the classic case — the interdependent controls belong on ONE screen. Our 4-step wizard separates parts ⇄ effect ⇄ preview, but animating is a tight loop across all three (pick part → apply → look → adjust). The wizard forces navigation for what should be glances.
→ Kill the stepper. The Animator becomes a single screen: canvas always visible; one control column ordered by the loop (source → parts → effect → applied → export bar).

### 4. Tesler's Law — complexity is conserved; the system should absorb it
Complexity can't be deleted, only moved. Move it into the tool: per-effect tuned defaults (each preset ships with its best duration/easing), automatic path-length math, group anchors computed from bounds. The user should meet complexity only where it's genuinely their decision (what moves, how fast, loop or once).
→ Defaults per preset, not global sliders-first. Speed slider is the one tuning control shown by default because it's the one people actually reach for.

### 5. Recognition over recall + Jakob's Law
Users shouldn't have to remember what "Wiggle" looks like or learn a new mental model. Noun Project / Iconify set the icon-library pattern (search-led, faceted tags, grid, copy-at-the-item); Figma-style inspectors set the editor pattern (panel follows selection). Effect tiles should preview the actual motion (animated thumbnails), not just name it.
→ Effect picker = tiles that play the effect on a sample glyph. Gallery = search + tag facets + uniform grid, actions on the card.

### 6. Motion vocabulary — keep it tiny
Motion-system research: 4–5 durations and 3–4 easings is a full vocabulary; more and users can't tell them apart. Our easing dropdown (5 curves) + duration + delay + loop was 4 knobs where 1–2 suffice at the basic level.
→ Basics: speed (per-effect default, one slider), loop/once toggle. Delay + easing move to "More options."

### 7. Animation-software landscape
Three paradigms exist: timelines (After Effects/Lottie, SVGator, Keyshape), state machines (Rive), code (GSAP). All are pro tools with pro learning curves — wrong model for "animate an icon with a basic CSS loop." The consumer pattern that works (Canva / LottieFiles one-click effects) is preset + preview + export. Ken already chose this in the v1 spec ("preset animator, not a timeline editor"); v4 leans all the way in and cuts the pro-leaning features (draw ordering, morph targets, color-fade endpoints) that crept back in.

## The v4 blueprint

### Top level — two tools, one switch
- Nav: **Icons** | **Animator**. Icons is the landing view (it's the product's front door and the higher-frequency use).
- Header line states the split in one sentence: icons to pull into projects; an animator when you want one moving.

### Tool 1 — Icons (gallery)
- Prominent search bar at top (title + tags), tag chips as facets beneath it, result count visible.
- Uniform grid; every card identical anatomy: preview, name, tags, actions.
- Actions by frequency: **Copy SVG** (primary), **Download**, **Animate it** (hands the icon to Tool 2). Signature-animation versions stay behind the existing Shape/Animated toggle, only on cards that have one.
- Honest empty state when a search/filter matches nothing.

### Tool 2 — Animator (single screen, no steps)
Canvas always visible (left on desktop, sticky top on mobile). One control column, sections in loop order, all on one screen:
1. **Source** — paste/upload/sample. Once an SVG is loaded this collapses to a one-line bar ("Sample loaded · Change") — the big textarea is level-1 only when there's nothing loaded.
2. **Parts** — as v3: tap parts in the canvas (glow/dim), list as backup, groups collapse long lists and animate as one unit.
3. **Effect** — 6 basic CSS effects as tiles that preview the motion: Fade, Pulse, Spin, Bounce, Slide, Wiggle. One speed slider + Loop/Once beneath. "More options" reveals delay + easing (level 2, the only level 2).
4. **Applied effects** — always visible list (the state of the work; hiding state causes errors), each removable.
5. **Export bar** — pinned at the panel's end: Copy code / Download, always one tap away. No separate Export step.

### What's cut, and why
- Draw-on, Color fade, Morph, Recolor: not "basic," and Morph is SMIL — cutting it makes the export promise clean: **every animation is pure CSS inside the SVG, no JavaScript, no SMIL.** If missed, they return later as a single clearly-labeled "More effects" disclosure — as a group, not scattered controls.
- The 4-step stepper and per-step hints/next buttons (staged disclosure that fights the loop).
- Easing/delay from the primary level (moved, not deleted).

### Naming (information scent)
- "Create" → **Animator** (says what happens there). "Gallery" → **Icons** (says what's there). Effects keep plain names. "More options" instead of "Timing & options" (matches what's behind it).

## Ken's decisions (2026-10-22)
1. **Draw-on STAYS as a one-click AUTO preset.** Its job: a simple reveal — make the strokes look drawn. The tool figures out the order itself (v1 heuristic: document order with staggered timing); no per-stroke ordering UI. Order quality can improve in later versions. It joins the basics as a 7th preset and stays pure CSS (stroke-dashoffset).
2. **Gallery grouped BY SET with headings, plus a "Newest" view showing the latest 20.** Sets: Cyberpunk (10), Basics (7), Snacks (2), Nature (2), Objects (2).
3. **Animator desktop layout: Figma style** — canvas left, inspector panel right. Mobile keeps the sticky-canvas-top pattern.

## v4.1 correction (2026-10-22, Ken's feedback on v4)
Ken: the Animator "still has the individual line selection part, which is way too complicated."
He was right — the brief preserved the v3 parts/groups model out of caution, which contradicted
his actual direction ("basic animations," declutter). The deploy itself was verified live and
correct; the scope was the error. **v4.1 removes part selection entirely**: no parts list, no
tap-to-select, no groups UI. The whole SVG animates as one unit (the group-wrapper mechanism,
applied to the entire graphic); Draw-on still chains the individual strokes internally with the
auto stagger — the system handles the per-line work, the user never sees it. Panel is now just
SVG → Effect → Export. Lesson recorded: when Ken says "basic/simple," simplify the interaction
model itself, not just the chrome around it.
