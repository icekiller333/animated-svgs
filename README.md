# SVG Factory

Animate any SVG — no code to write.

**SVG Factory** is a free, single-page tool: paste or upload an SVG, pick the parts, apply preset animations with sliders, then copy the code or download a self-contained animated `.svg` file.

Exports contain only CSS / SMIL animation baked inside the SVG itself — no scripts, no external files — so they play wherever SVG images play: as an `<img>`, inline in HTML, and in Rise, Storyline, and D2L (Storyline best-effort).

## Features

- **Input:** paste SVG code, upload a file, drag-and-drop, or start from the built-in sample
- **Part picker:** select individual shapes/paths and animate one or many at once
- **Draw-on:** select strokes, set the reveal order and speed
- **Effects:** draw-on, fade, pulse, spin, bounce, slide-in, wiggle, color fade, and path morph (SMIL), with duration, delay, easing, and loop/once controls
- **Recolor:** set fill/stroke colors on selected parts
- **Output:** copy the animated SVG code, or download the `.svg` file
- **Gallery:** ready-made animated SVGs to copy or download, curated by the maintainer

## Use it

Open `index.html` in a browser, or serve this repo with GitHub Pages.

## Adding to the gallery

Gallery items are defined in the `GALLERY` array in `index.html` — add an entry with a title, a one-line description, and a self-contained animated SVG string, then push.
