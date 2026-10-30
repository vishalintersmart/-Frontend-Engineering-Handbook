# CHANGELOG

> **Status:** Placeholder.

This chapter will be fully populated from the original engineering standard while preserving all explicit rules, checklists, examples, and code samples.

## 2026-10-31

- **09-Responsive-System.md** — added the mandatory *Figma Fidelity Floor (1280px)* rule: the implementation must be visually identical to Figma from the frame's own width down to 1280px, platform-agnostically (HTML, Laravel, Next.js, or any other stack), achieved via a single proportional design-scale CSS custom property (plain CSS, not a framework feature) rather than the discrete breakpoint table. Layout reorganization/reflow is reserved for below 1280px. Mandatory Rules, Responsive Layout Principles and the Validation Checklist updated; cross-referenced from **20-Figma-Validation.md**, **29-NextJS-Project-Standards.md** (Rule 12), and **30-Laravel-Project-Standards.md**.

## 2026-10-29

- **29-NextJS-Project-Standards.md** — added Mandatory Setup Rule 12, *Stepped Figma scale for the large tiers*: 3xl (≥1920) uses exact Figma values; 2xl / xl / lg use fixed ratios (0.85 / 0.72 / 0.6) via a single `--u` custom property driving `--spacing` and design-scale type tokens, capped by `100svh/1080` below 3xl; no growth above 1920; container left unscaled; below lg stays mobile. Mandatory Rules and Validation Checklist updated.

## 2026-10-24

- **29-NextJS-Project-Standards.md** — added the mandatory *Mandatory Next.js Setup Rules* section (11 rules): shared `heading.jsx` and `button.jsx` (premium hover) sized for 3xl/2xl/xl/lg/sm/base; page-local `local_data` with one object per section and arrays inside it (no data folder); wrapper-div sizing for small icons; lowercase component file names; Tailwind scale values instead of px, responsive; font variables named after the font; `--basecolor`, `--basecolor2`, … global colours; `.typography` class for editor content; a single flat `public/images/` folder; optional chaining everywhere. Structure tree, examples, Mandatory Rules and Validation Checklist updated to match.

## 2026-10-21

- **13-JavaScript-Standards.md** — added the required *Smooth Wheel Scrolling* section: a dependency-free `initSmoothScroll()` (trimmed from SmoothScroll.js, ≈80 lines) that every HTML / PHP build adds to `assets/js/app.js`. Eases mouse-wheel notches only; trackpads, touch, Firefox, ctrl-zoom, reduced motion and keyboard scrolling stay native; respects locked pages and nested scroll areas. Includes rules, drop-in code and a verification recipe; matching item added to the chapter's Validation Checklist and to **23-New-Project-Checklist.md**.

## 2026-10-10

- Added **FRONTEND-QA-TEST.md** — on-demand Senior QA audit workflow (code review, robots/indexing, performance, console, HTML validation, security, WCAG 2.2 accessibility, responsive, visual, functional, SEO, cross-browser), with execution phases, severity levels, the `FRONTEND-QA-REPORT.md` deliverable and Definition of Done. Triggered when the user says "run QA test"; registered in CLAUDE.md under *QA TESTING*.

- **29-NextJS-Project-Standards.md** — added the mandatory *Client Boundaries & shadcn Primitives* section, plus matching Mandatory Rules, Validation Checklist items, Known Pitfalls and Common Mistakes: (1) selects, modals/dialogs, drawers and accordions MUST use shadcn/ui, including how to add shadcn to an existing project without breaking its tokens (map the shadcn colour tokens, import `tw-animate-css`, set surfaces explicitly); (2) `"use client"` MUST NOT be placed on section components — only the interactive leaf (slider, toggle, filter) becomes a client component.

## 2026-10-08

- Added **30-Laravel-Project-Standards.md** — mandatory standard for Laravel + Blade (server-rendered, SASS-compiled, no SPA framework) projects. Extracted from hands-on delivery work building multiple Blade pages and reusable Blade components on a live Laravel project. Covers project structure (routes/controllers/views/components/compiled assets), the controller→view page pattern, Blade component conventions (`@props`, `$attributes->merge`, suffixed classes for repeated slider instances), how the existing Chapter 08 SASS architecture maps onto a Laravel asset pipeline, the Figma-to-code and PDF-design-comparison workflows, the browser-based verification workflow, and a table of known pitfall patterns with fixes — most importantly the "Golden Rule" that a Blade component's CSS must move into `3-modules/` in the same change that extracts its markup, or the component silently breaks on every other page that reuses it.

## 2026-09-28

- Added **29-NextJS-Project-Standards.md** — mandatory standard for Next.js App Router / Tailwind v4 / headless-primitive-based projects. Extracted from hands-on delivery work (Figma → production pages, modals, multi-step forms) on a live Next.js 16 project. Covers project structure, the page/data pattern, the Tailwind v4 `@theme inline` styling system, component conventions, the Figma-to-code workflow (including how to handle duplicated/mislabeled Figma frames), adding new shared UI primitives without duplicating an existing headless library, multi-step form conventions, the browser-based verification workflow, and a table of known pitfall patterns with fixes.
