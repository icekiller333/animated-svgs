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
- **Guided flow:** four steps — Add an SVG → Pick parts → Add motion → Export — with one control panel at a time and a live preview throughout
- **Gallery:** curated shapes. The plain shape is the default for every item (copy or download as-is, or load it into the tool and animate it yourself); a shape with a unique/signature animation also offers that animated version

## Use it

Open `index.html` in a browser, or serve this repo with GitHub Pages.

## Adding to the gallery

Gallery items are defined in the `GALLERY` array in `index.html` — add an entry with a title, a one-line description, and a `shape` SVG string (the plain shape is required and is the default). If the shape has a signature animation, add `sigName` and a `sig` string with that self-contained animated version, then push.
