# Flores — Design Spec (2026-07-15, revised)

## Purpose
Single-page website gift. On every visit, a small bouquet of glowing yellow
flowers grows and blooms, styled after the "Flores Amarillas" animation the
user referenced (https://gmpsankalpa.github.io/Flower-animation/FLORES.html).
No text, no sound, no backend.

## Approach
One self-contained `index.html` (inline CSS + JS), vanilla JS drawing on a
full-viewport `<canvas>`. No dependencies, no build step. Hostable anywhere
(GitHub Pages, Netlify) or opened as a local file. Own implementation, not
copied from the reference.

## Scene
- Background: near-black with a dark green radial glow behind the bouquet.
- Faint green/white star-dots twinkling across the whole frame.
- Centered composition: three yellow flowers (tall center, two flanking),
  fern fronds at the base, tall grass clusters left / right / center.

## Flowers
- Five fat rounded petals per flower, yellow gradient (golden base to pale
  tip), white ring + golden heart at the core, soft pulsing glow halo.
- Green gradient stems with alternating teardrop leaves.
- Sizes and slight angles randomized per visit.

## Animation timeline
1. 0–2.6 s: grass blades and ferns grow upward (staggered).
2. 0.9–3.6 s: flower stems rise, leaves unfurl as the stem passes them,
   green bud at the tip.
3. 3.4–5 s: petals bloom open with a slight overshoot, glow ramps up.
4. From ~4.6 s: yellow sparkles fade in, drifting and blinking around the
   flower heads. Idle: gentle sway, glow pulse, star twinkle.

## Responsiveness
- Canvas resizes with the window; scene rebuilds fully grown on resize
  (growth replays only on a fresh page load).
- devicePixelRatio-aware rendering; scales to phone and desktop.

## Accessibility
`prefers-reduced-motion: reduce` renders a static fully-bloomed scene with
no animation.

## Out of scope
Persistence, visit counters, text, music, interactivity beyond watching.

## Verification
Verified via headless Chromium screenshots: growth sequence at 2.5 s, full
bloom at 7 s, mobile viewport 390×844, zero console errors.
