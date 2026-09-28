# 29 – Next.js Project Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project built with Next.js (App Router) — React, Tailwind CSS, and headless-UI-primitive based stacks.
>
> **Related Chapters**
>
> - 02 Core Workflow
> - 03 Figma Standards
> - 04 Project Architecture
> - 09 Responsive System
> - 11 Components
> - 19 Browser QA
> - 20 Figma Validation
> - 24 AI Development Rules

---

# Purpose

Chapters 04, 05, 08, and 13 describe this handbook's PHP + SASS architecture. That architecture does not apply literally to a Next.js project — there is no `main.php`, no SASS partials, no `includes/` directory.

This chapter is the Next.js-specific equivalent: it defines the mandatory folder structure, styling system, component conventions, Figma-to-code workflow, and verification workflow for any project built on Next.js App Router with Tailwind CSS.

It was extracted from hands-on delivery work (Figma → production pages, modals, multi-step forms, on a Next.js 16 / Tailwind v4 / `@base-ui/react` stack) and captures the methods that produced pixel-accurate, non-duplicated, build-clean pages.

---

# Objective

A developer or AI agent starting a new Next.js page in an existing project should never have to invent conventions. This chapter defines:

- Where files belong.
- How a page is assembled from data + shared components.
- How Tailwind is configured and used in v4 projects (no `tailwind.config.js`).
- How to turn a Figma frame into code without guessing.
- How to add a new shared primitive (dialog, accordion, stepper) without duplicating an existing one.
- How to verify the result before calling it done.

---

# Engineering Philosophy

- **Reuse the project's existing architecture before inventing a new one.** If a project already has a working pattern (a page-data shape, a card component, a primitive wrapper), extend it — do not start a parallel system.
- **The approved Figma design is the source of truth for visuals — but Figma files contain production mistakes.** Duplicated frames, mislabeled tabs, copy-pasted content, and stray leftover layers are common in real Figma files. Reproducing an obvious mistake is not fidelity, it is copying a bug. Use engineering judgment, and **tell the user what you changed and why** — never silently diverge without saying so.
- **Never touch code outside the current task's scope**, including pre-existing lint warnings, unrelated hydration errors, or stray files you didn't create. Note them; don't fix them unless asked.
- **Verify visually, not by assumption.** A page is not "done" because the JSX looks right — it is done after a live screenshot has been compared against the Figma export at more than one breakpoint.

---

# Stack Baseline (Next.js App Router projects)

Unless a project's own `CLAUDE.md` / `AGENTS.md` says otherwise, expect and preserve:

- **Next.js App Router**, plain **JS/JSX** (not TypeScript) unless the project has `.ts`/`.tsx` files already.
- **Tailwind CSS v4** via `@tailwindcss/postcss` — **no `tailwind.config.js`**. Theme (colors, breakpoints, radii, fonts, keyframes) lives in `globals.css` under `@theme inline`. Check that file first; do not assume Tailwind v3 defaults.
- A **shadcn-style `components/ui/`** folder, built on a headless primitives library (`@base-ui/react`, or Radix in older projects) + `cva()` for variants + a `cn()` helper (`twMerge(clsx(...))`).
- **Path alias `@/*` → `./src/*`** (check `jsconfig.json`/`tsconfig.json`).
- Icon library: `lucide-react` (or whatever is already imported — do not introduce a second icon set).

Before writing a single line of a new page, read the project's own `CLAUDE.md`/`AGENTS.md` if present — it documents the concrete deviations from this baseline for that project. Project-specific instructions always win over this chapter's generic defaults.

---

# Standard Project Structure

```text
src/
├── app/
│   └── <route>/
│       ├── page.js            # route entry — local_data + composed sections
│       └── [slug]/page.js     # dynamic route, same pattern
├── components/
│   ├── layout/
│   │   ├── header.jsx
│   │   ├── footer.jsx
│   │   └── common/             # shared cross-page pieces (hero, cards, floating widgets)
│   ├── sections/
│   │   └── <page-area>/        # one folder per page/feature area
│   │       └── <Component>.jsx # one component per page section
│   └── ui/                     # shadcn-style primitives (button, dialog, accordion, select, ...)
├── lib/
│   └── utils.js                 # cn() and friends
└── app/globals.css              # @theme inline — breakpoints, colors, fonts, keyframes
```

Rules:

- One route folder per page. `page.js` stays thin: it defines `local_data` and composes section components in order.
- One component per page section under `components/sections/<area>/`.
- Anything used by **two or more page areas** (a floating contact rail, a shared card, a hero) belongs in `components/layout/common/`, not duplicated per-area. If you discover mid-project that a page-specific component is now needed elsewhere, **promote it** to `layout/common/` and update both callers in the same change — do not leave a second copy behind.
- Never invent a second "data" pattern alongside an existing one (e.g. a project may have an old, unused Strapi-shaped `src/data/` folder next to the real pattern — follow the pattern actually wired into pages, not the one that merely exists).

---

# The Page Pattern

Every route file follows the same shape:

```jsx
import InnerHero from "@/components/layout/common/InnerHero";
import SectionA from "@/components/sections/<area>/section-a";
import SectionB from "@/components/sections/<area>/section-b";

const local_data = {
  hero: { title: "...", breadcrumb: [{ label: "Home", href: "/" }, { label: "..." }] },
  sectionA: { /* ... */ },
  sectionB: { /* ... */ },
};

export default function page() {
  return (
    <>
      <InnerHero data={local_data.hero} />
      <SectionA data={local_data.sectionA} />
      <SectionB data={local_data.sectionB} />
    </>
  );
}
```

- `local_data` is scaffolding shaped like a future CMS response (flat objects, arrays of items with stable `id`s). This is intentional — it is not "fake data to delete later," it is the shape the real API response should match.
- When two pages need the same list of records (e.g. a listing page and a detail/apply flow reading the same items by slug), **extract the data into a shared module** (`jobs-data.js`, etc.) that both import — do not copy the array into two files.
- Every field a component reads must be accessed defensively (`data?.field?.sub`, `data?.list?.map(...)`) so a missing/late field never crashes the page.

---

# Styling System (Tailwind v4, no config file)

- Breakpoints and the `.container` class are defined once, in `globals.css` under `@theme inline` / `@layer components`. **Read that file before assuming any breakpoint number.** Different Next.js/Tailwind-v4 projects define genuinely different breakpoint sets — do not import a breakpoint table from a previous project or from this handbook's generic PHP-era table (Chapter 09) without checking whether the current project already defines its own.
- Reuse existing utility classes (title/heading classes, text classes, brand-gradient classes) before writing new arbitrary-value Tailwind. If two components need the same 55px-bold-heading treatment, that is a signal a shared class already exists — grep for it before inventing a duplicate.
- Prefer normal Tailwind specificity or `cn()`-based class merging over the `!important` modifier. The one accepted exception: overriding a **shared UI primitive's own conditional classes** (e.g. a default chevron icon's `hidden`/`inline` toggle classes baked into a shared `Accordion`/`Select` component) where plain specificity does not reliably win. When you do reach for `!`, keep it scoped to that one override, matching whatever precedent already exists in the project for the same problem.
- Dark mode: if the project uses a `.dark` class strategy (`next-themes`), give every new custom color an explicit `dark:` counterpart — do not ship a component that only looks right in light mode.

---

# Component Conventions

- Functional components, default export, props destructured as `{ data }` (or a more specific name for sub-components, e.g. `{ item }`, `{ job }`).
- `"use client"` only on components that actually need state, effects, or browser APIs (interactive sections, anything with `useState`/`useEffect`/`usePathname`/`useSearchParams`). Everything else stays a server component by default.
- `next/image` for all images: fixed `width`/`height` **or** `fill` inside a `position:relative` parent with a defined size; `priority` only on the hero/LCP image. Never mix `w-full h-auto` styling with fixed `width`/`height` props on the same `<Image>` — that combination trips Next's aspect-ratio warning. Either let both dimensions be fixed, or wrap the image in an `aspect-[w/h]` container and use `w-full h-full object-cover`.
- Reusable UI primitives (`components/ui/*`) use `cva()` for variants and `cn()` to merge classes — follow this exact pattern for any new primitive rather than hand-rolling conditional class strings.

---

# Figma-to-Code Workflow

1. **Fetch the Figma node's structured data** (via the Figma MCP tool or equivalent) *and* **export a full-frame screenshot** of the same node. Large frames often exceed a single tool response — save the raw dump to a file and read it in chunks rather than guessing from a truncated view.
2. **Cross-reference text/data nodes against the screenshot.** Structured data can mis-group visually distinct icons/images under one repeated "template" reference — always download and open the actual icon/image asset when its identity matters (don't assume two visually different icons are the same just because the export collapsed them together).
3. **Identify duplicated or mislabeled frames before building.** Common patterns seen in real design files:
   - Two list entries with byte-identical placeholder content (design filler, not intentional duplication of real content).
   - A stray leftover layer bleeding into an unrelated section (visible partially behind other content) — usually safe to omit.
   - A multi-step flow where a later step's tab label doesn't match the fields shown under it (a step frame duplicated from the previous step and never updated). Building this literally produces a broken, confusing product. Pair tab labels with their **semantically correct** field set, and say so explicitly in the summary you give the user.
4. **Download every real asset you'll use** (images by node id + `imageRef`, icons as SVG) into the project's existing asset convention (usually `public/images/`) — never hot-link back to Figma's CDN.
5. **Build using the project's existing component/page patterns**, not a new pattern per page.
6. **Verify against the screenshot at more than one breakpoint** (see Verification Workflow below) before calling the page done.

---

# Adding a New Shared UI Primitive

When a design needs a primitive the project doesn't have yet (a centered modal, a stepper, a date picker):

1. **Check what the project already has built on the same headless library.** If `components/ui/sheet.jsx` is built on `@base-ui/react/dialog` (a slide-out panel), a new centered-modal `dialog.jsx` should be built on the **same** `@base-ui/react/dialog` package, following the same Root/Trigger/Portal/Backdrop/Popup/Close composition — not a different modal library. This keeps bundle size flat and behavior consistent (focus trap, escape-to-close, animation timing all already solved once).
2. **Match the existing wrapper's shape**: same `data-slot` attributes, same `cn()`-based className merging, same named exports pattern (`Dialog`, `DialogTrigger`, `DialogContent`, `DialogHeader`, `DialogTitle`, ...).
3. **Check default styling against the actual background you're placing it on.** A shared `Button` component's `ghost`/`outline` variant may default to white text (tuned for a dark/colored context elsewhere in the app) — invisible on a light modal background. Override with an explicit color on your usage; don't change the shared button's default (that would affect every other consumer).

---

# Multi-Step Forms / Wizards

- Keep step content in **separate components** (`step-one.jsx`, `step-two.jsx`, ...) and a single **parent wizard component** owning `currentStep` state and the combined `formData` object, passed down as `{ formData, setFormData }`.
- Each step's field updates go through small `update(field, value)` helpers using the **functional form of `setState`** (`setFormData(prev => ({...prev, field: value}))`) — this avoids stale-closure bugs when multiple fields update in quick succession.
- Conditionally render only the current step's fields (unmount the others) rather than hiding them with CSS — simpler to reason about, and avoids native HTML5 `required` validation firing on invisible fields from other steps.
- "Next"/"Previous" are `type="button"` (they just change `currentStep`); only the final step's submit control is `type="submit"`.
- A route reading a query param to pre-fill the form (e.g. `?job=<slug>`) needs the component using `useSearchParams()` wrapped in a `<Suspense>` boundary at the page level — Next.js requires this for static/SSR compatibility.
- Derived/computed fields (an auto-calculated total, a formatted summary) belong in a `useMemo` keyed on the relevant slice of `formData`, rendered into a `disabled`/`readOnly` input — never written by the user directly.

---

# Verification Workflow

A page is not complete until it has been checked live, not just read as JSX.

1. Start the project's existing dev server (don't start a second one if one is already running on the expected port).
2. Navigate to the new route in a real browser (Playwright or equivalent browser automation).
3. **Check the console for errors/warnings before screenshotting.** Distinguish *new* problems (caused by your change) from *pre-existing* ones (reproduce the same error on an existing, unrelated page — if it's already there, it's not yours to fix).
4. Screenshot at the design's native width (commonly 1920px) and compare crops against the Figma export.
5. Re-check at a laptop width (≈1440px) and a mobile width (≈390px) — confirm the responsive scaling holds up and nothing overlaps.
6. For interactive elements (accordions, modals, multi-step forms, filters), **actually click through them** — take an accessibility snapshot or screenshot after the interaction, don't assume the state changed correctly just because the handler looks right.
7. When simulating form input via low-level browser automation (not a real click/type), be aware that directly setting a native input's `.value` and dispatching a bare `input` event **does not reliably trigger React's controlled-input change detection**. Use the browser tool's proper `type`/`fill` action (which drives real key/input events) before concluding a computed/derived value is broken — a "bug" that disappears under real interaction is a test-methodology artifact, not a code defect.
8. Clean up any scratch screenshots/temp files created for comparison — they are not part of the deliverable.

---

# Known Pitfall Patterns (and fixes)

| Symptom | Cause | Fix |
|---|---|---|
| Next.js `<Image>` aspect-ratio console warning | `width`/`height` props set, but only one of `w-full`/`h-auto` overridden via className | Wrap in an `aspect-[w/h]` container, use `w-full h-full object-cover`, or set both dimensions consistently |
| A shared `Accordion`/`Select` trigger shows a leftover default chevron next to your custom `+`/`-` indicator | The shared primitive renders its own icon unconditionally; a plain Tailwind override loses the specificity race | `[&>svg]:!hidden` scoped to your trigger usage (matches existing precedent for the same problem elsewhere in the project) |
| A modal/dialog close icon (or similar `ghost`/`outline` button) is invisible | Shared `Button` variant defaults to white text for a different (dark) context | Add an explicit text color className on that specific usage; never edit the shared variant |
| A computed/derived form value never appears to update during automated testing | Native `.value =` + dispatched `input` event bypasses React's change tracking | Use the browser tool's real `type`/`fill` action; re-verify before treating it as a bug |
| Two adjacent multi-step-form tabs show identical field sets | A Figma step frame was duplicated from the previous step and never updated | Pair each tab's fields by what makes sense for its label, not by which frame the content happened to be copied into; tell the user what you corrected |

---

# Git & Delivery Workflow

- A framework-regenerated file (e.g. an agent-rules block Next.js rewrites into `AGENTS.md` on every `next dev` start) that reappears as a diff after running the dev server is expected — commit it alongside real work rather than reverting it, unless the project's own docs say otherwise.
- Only commit files relevant to the task. Leave unrelated stray/duplicate files (an accidental `*.md` copy, an unrelated uncommitted change from before your session started) untouched and untracked unless the user asks about them.
- Run the project's lint script and, for a substantial multi-file change, its production build before considering the work done. A page that "looks right" in dev but fails `next build` is not finished.
- Write commit messages that explain *why*, and call out any deliberate deviation from the literal design/spec (see the Figma-mislabeling case above) so reviewers aren't surprised later.

---

# Mandatory Rules

Every Next.js page/feature built under this standard MUST:

- Reuse the project's existing route, component, and data-shape patterns instead of inventing a parallel one.
- Read `globals.css`'s `@theme inline` (or the project's own docs) for the real breakpoint/color/font tokens before writing styles.
- Cross-check Figma's structured data against a rendered screenshot before trusting either alone.
- Flag — not silently fix or silently reproduce — any Figma content that looks like a production mistake (duplicated frames, mismatched tab/content pairing, stray layers).
- Verify visually in a real browser at 1920px, ~1440px, and ~390px before calling the work done.
- Leave pre-existing, unrelated issues (lint warnings, hydration errors, stray files) untouched and merely noted.

---

# Validation Checklist

Before marking a Next.js page/feature complete, verify:

## Architecture
- [ ] Route file only composes `local_data` + section components (no inline business logic).
- [ ] Shared data extracted to one module if used by more than one route.
- [ ] New shared UI built on the project's existing headless-primitive library, not a new one.

## Styling
- [ ] Breakpoints/colors/fonts read from the project's actual `@theme inline`, not assumed.
- [ ] Existing utility/heading/text classes reused where they match.
- [ ] Dark-mode variants added for any new custom color.

## Figma Fidelity
- [ ] Structured Figma data cross-checked against a rendered screenshot.
- [ ] Any duplicated/mislabeled Figma content identified and corrected with judgment, not copied as-is.
- [ ] All real assets downloaded into the project's asset convention (no hot-linking).

## Verification
- [ ] Console checked for new errors/warnings (vs. pre-existing ones on other pages).
- [ ] Screenshot comparison done at desktop, laptop, and mobile widths.
- [ ] Interactive elements actually clicked/typed through, not just visually inspected.
- [ ] Lint (and, for larger changes, production build) run clean.

---

# Common Mistakes

Avoid:

- Assuming Tailwind v3 defaults or another project's breakpoint table apply without checking `globals.css`.
- Building a second modal/accordion/stepper library on top of a different headless package when one is already in use.
- Reproducing an obviously duplicated or mislabeled Figma frame instead of pairing content with its correct label.
- Trusting a low-level JS-simulated input event as proof of a bug without retesting via a real type/fill action.
- Editing a shared component's default variant to fix a one-off visibility issue.
- Fixing unrelated pre-existing lint/console errors while doing a scoped task.
- Leaving a component duplicated across two page areas instead of promoting it to a shared location.

---

# Best Practices

- Read the project's own `CLAUDE.md`/`AGENTS.md` before this chapter's generic defaults — project-specific instructions win.
- Grep for an existing utility class or component before writing a new one.
- Keep a running mental (or literal) list of every Figma discrepancy found, and report it plainly at the end rather than silently "fixing" the design's intent.
- Prefer `useMemo`/derived state for computed values over storing them redundantly in `formData`.
- Clean up scratch/comparison files before finishing; they are not deliverables.

---

# Chapter Summary

Next.js App Router projects on Tailwind v4 replace this handbook's PHP/SASS architecture (Chapters 04/05/08/13) with a data-driven page pattern, a `@theme inline`-based styling system, and shadcn-style primitives built on a headless UI library. The engineering principles carry over unchanged — reuse over invention, one shared implementation per concern, verify against the approved design rather than approximate it — but the concrete mechanics differ, and this chapter is the reference for those mechanics.

Combined with Chapter 03 (Figma Standards), Chapter 20 (Figma Validation), and Chapter 24 (AI Development Rules), it forms the complete workflow for delivering a Next.js page from an approved Figma design to a verified, build-clean implementation.

---
