# 31 – Global Build Rules

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every HTML, PHP and Laravel project (Next.js projects follow Chapter 29 and use the equivalent Tailwind / React implementation).
>
> **Related Chapters**
>
> - 09 Responsive System
> - 13 JavaScript Standards
> - 15 Performance
> - 16 Header Standards
> - 17 Navigation
> - 18 Slider Standards
> - FRONTEND-QA-TEST.md

These rules come from recurring review findings. Each one is checked before delivery.

---

# Global Rules

## 1. Overlap Detection (QA)

Every QA run includes an **automated overlap detector** (see FRONTEND-QA-TEST.md, section I-2). It compares text, images and buttons against each other at every ~40px width from 320 to 1920 (plus the breakpoint edges). Zero unexplained overlaps; decorative layers are the only exception and must be marked.

## 2. Flipped Images

If an image is flipped horizontally in Figma, the build must show it flipped too. Apply `transform: scaleX(-1)` to the image (or flip the exported file), never both. Compare against Figma at every breakpoint.

## 3. Laptop Fit (up to 1200px)

Up to the 1200px laptop view, fit each section inside the visible screen as far as the design allows. Size section height and media with `svh` / `vh`-aware clamps instead of fixed pixel heights, and keep the hero and first-fold sections free of vertical scrolling on 1024-1200px wide, 600-800px tall screens. Never shrink type below the readable minimum to achieve this.

## 4. Scroll Animations

Add reveal-on-scroll animations to sections, headings, cards and images.

- Use one shared `IntersectionObserver` in `assets/js/app.js` that adds `is-visible` to `[data-animate]` elements once.
- Animate only `opacity` and `transform`.
- Content must stay visible without JavaScript (add the hidden state from JS, or under `.js`) and under `prefers-reduced-motion: reduce`.
- Never animate the LCP / hero heading in a way that delays it.

## 5. Dropdown Menu

Whenever the design has (or implies) sub-pages, the navigation includes an accessible dropdown: a real `<button aria-expanded>` plus `<ul>`, hover and keyboard support on desktop, an accordion in the mobile menu, `Esc` closes it, and it never overflows the viewport. See Chapter 17.

## 6. Hero Slider (video + image)

The hero is a slider that supports **both video and simple image slides**.

- Follow Chapter 18; do not set `overflow` on the library's track.
- Video slides: `muted`, `playsinline`, `loop`, a `poster` image, `preload="metadata"`; they pause when off-screen or not active, and are replaced by the poster under `prefers-reduced-motion`.
- The first slide is never lazy-loaded (LCP). Later slides are lazy.
- Provide pause / play, previous / next and pagination controls with accessible names.

## 7. Sticky Header (scroll-up only)

The sticky header appears **only when scrolling up**. Scrolling down hides it; scrolling up past the top slides it in. Full implementation: Chapter 16.

## 8. Statistics Counter

Numeric statistics count up from 0 when they enter the viewport.

- Triggered once by `IntersectionObserver`; ~1.5-2s ease-out; uses `requestAnimationFrame`.
- Keep prefix / suffix / separators (`+`, `%`, `,`) exactly as designed.
- The final value is in the HTML, so it is correct without JavaScript and for `prefers-reduced-motion`.
- Reserve width (e.g. `font-variant-numeric: tabular-nums`) so counting causes no layout shift.

## 9. Favicon

Always confirm the favicon exists and loads before delivery: `<link rel="icon">` (plus `apple-touch-icon` where provided) in the shared head, the file present at the referenced path, and no 404 in the network panel. A missing favicon is a QA defect.

## 10. Button and Link Hover

Buttons and plain links must have working, visible hover **and** `focus-visible` states.

- Buttons: premium hover (fill sweep, lift or arrow slide) with `transition`; link: colour / underline change.
- Verify on the real element: nothing covering it (`pointer-events`, overlays, pseudo-elements), `cursor: pointer`, no hover rules overridden by later CSS or specificity.
- Wrap hover rules in `@media (hover: hover)` so touch devices do not stick.
- Respect `prefers-reduced-motion`.

## 11. Image Sizing and Cropping

Match the Figma crop, not just the file.

- If Figma shows only a cropped part of an image, reproduce the visible frame: fixed `aspect-ratio` on the wrapper, `object-fit: cover` and the Figma `object-position`, or export the cropped asset.
- Do not drop in the full-size original and let it overflow or rescale.
- Always set `width` / `height` to the displayed ratio, and serve a file no larger than needed (Chapter 15).

---

# HTML and Laravel Projects Only

## 12. Minified CSS Output

The compiled output files are `app.min.css` and `pages.min.css`, not `app.css` / `pages.css`.

- Link only the `.min.css` files (Laravel: from `layouts/app.blade.php`, Chapter 30).
- Configure the SASS build to output the `.min.css` names (compressed) and update every `<link>`.
- Do not ship or reference unminified copies. Check the network panel for the `.min.css` requests.

## 13. Keyframe Animation on Small Curved Objects

Small decorative curved shapes (swooshes, arcs, blobs, dots) get a subtle keyframe animation: slow float, rotate or draw, 6-12s, `ease-in-out`, `infinite`.

- Animate only `transform` / `opacity`.
- Mark them `aria-hidden="true"` and `pointer-events: none`.
- Disable under `prefers-reduced-motion: reduce`.
- Keep them off the critical path (no effect on LCP / CLS / TBT).

---

# Validation Checklist

- [ ] Overlap detector run (320-1920, ~40px steps) - zero unexplained overlaps.
- [ ] Flipped Figma images flipped in the build.
- [ ] Sections fit the visible screen up to 1200px where practical.
- [ ] Scroll animations added; content visible without JS / with reduced motion.
- [ ] Dropdown menu present and keyboard accessible.
- [ ] Hero slider handles video and image slides.
- [ ] Sticky header shows only on scroll up.
- [ ] Statistics counters animate once.
- [ ] Favicon present, no 404.
- [ ] Button and link hover / focus verified.
- [ ] Image crops match Figma.
- [ ] `app.min.css` / `pages.min.css` used (HTML / Laravel).
- [ ] Keyframe animation on small curved objects (HTML / Laravel).
- [ ] Lighthouse still 100 (Chapter 15) after the animations are added.
