# 30 – Laravel Project Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project built with Laravel + Blade (server-rendered HTML, SASS compiled to CSS, no SPA framework).
>
> **Related Chapters**
>
> - 02 Core Workflow
> - 03 Figma Standards
> - 04 Project Architecture
> - 05 PHP Architecture
> - 08 SASS Architecture
> - 09 Responsive System
> - 11 Components
> - 19 Browser QA
> - 20 Figma Validation
> - 24 AI Development Rules

---

# Purpose

Chapter 05 describes this handbook's vanilla-PHP architecture (`main.php` / `includes/header.php` / `includes/footer.php`, flat page files). A Laravel project does not use that architecture — there is no `main.php`, no raw `include`, no `includes/` directory. Routing, request handling, and template assembly are all framework-owned.

This chapter is the Laravel-specific equivalent: it defines the mandatory folder structure, routing/controller conventions, Blade templating and component conventions, how the Chapter 08 SASS architecture maps onto a Laravel project, and the verification workflow for any project built on Laravel with Blade views.

It was extracted from hands-on delivery work (Figma → production Blade pages, reusable Blade components, SASS-driven multi-breakpoint layouts, Swiper/select2-based interactive sections) and captures the methods that produced pixel-accurate, non-duplicated, framework-correct pages.

Chapters 08 (SASS Architecture) and 11 (Components) remain fully applicable to Laravel projects as written — their layer responsibilities and component principles are framework-agnostic. This chapter adds the Laravel-specific mechanics (routes, controllers, Blade) that Chapter 05 does not cover, and the concrete lessons for applying Chapters 08/11 inside a Blade codebase.

---

# Objective

A developer or AI agent starting a new Laravel page in an existing project should never have to invent conventions. This chapter defines:

- Where files belong (routes, controllers, views, components, compiled assets).
- How a page is assembled from a controller's view data + shared Blade layouts/components.
- How the Chapter 08 SASS architecture is wired into a Laravel asset pipeline.
- How to build a reusable Blade component that behaves correctly on every page that includes it.
- How to turn a Figma frame or a design PDF into a Blade page without guessing.
- How to verify the result before calling it done.

---

# Engineering Philosophy

- **Reuse the project's existing architecture before inventing a new one.** If a project already has a working layout, a Blade component, a SASS module, extend it — do not start a parallel system.
- **The approved design (Figma or an exported PDF) is the source of truth for visuals — but design files contain production mistakes.** Duplicated frames, inconsistent layer order, placeholder content, and missing sections are common. Reproducing an obvious mistake is not fidelity, it is copying a bug. Use engineering judgment and **tell the user what you changed and why**.
- **A component is not reusable until its CSS is shared too.** Extracting a Blade component's markup into `resources/views/components/` while leaving its styling in a page-scoped SASS partial produces a component that silently breaks on every other page that uses it. This is the single most common architectural mistake in Laravel/Blade projects and is covered in depth below.
- **Verify visually, not by assumption.** A page is not "done" because the Blade markup looks right — it is done after the compiled page has been checked in a browser against the design at more than one breakpoint.

---

# Stack Baseline (Laravel + Blade projects)

Unless a project's own `CLAUDE.md`/`AGENTS.md` says otherwise, expect and preserve:

- **Laravel** (current LTS or newer) with **Blade** templates — no SPA framework, no client-side router. Pages are server-rendered HTML.
- Routing in `routes/web.php`, mapped to `App\Http\Controllers\*` classes. No business logic in Blade files.
- **SASS** (indented `.sass` syntax, per Chapter 08) compiled to CSS, served from `public/`. Two bundles: a shared bundle (abstracts → base → plugins → modules → layouts) and a page-specific bundle, matching the Two Bundle Strategy in Chapter 08.
- Blade component files (`resources/views/components/*.blade.php`) using `@props([...])` for their public API — the project's equivalent of a reusable UI primitive.
- jQuery-era interactive libraries are common in this stack (Swiper/Splide for carousels, select2 for enhanced selects) rather than a modern JS framework — treat each as a Chapter 08 "Layer 2 — Plugins" concern: isolate their overrides, never fight their internal DOM with page-specific hacks.
- Literal, non-mixin `@media (min-width: …)` breakpoints, per this handbook's global responsive-development rule — never a SASS breakpoint mixin, never a stored breakpoint variable.

Before writing a single line of a new page, read the project's own `CLAUDE.md`/`AGENTS.md` if present — it documents concrete deviations from this baseline. Project-specific instructions always win over this chapter's generic defaults.

---

# Standard Project Structure

```text
app/
└── Http/
    └── Controllers/
        └── <Area>Controller.php     # one controller per page/feature area; returns a view + data array

routes/
└── web.php                          # route → controller@method mapping, named routes

resources/
└── views/
    ├── layouts/
    │   └── app.blade.php            # document shell: <head>, shared CSS/JS, @yield('content')
    ├── components/
    │   ├── header.blade.php
    │   ├── footer.blade.php
    │   └── <component-name>.blade.php   # one Blade component per shared UI piece, @props-driven
    └── <page-name>.blade.php        # one Blade view per page/route, @extends('layouts.app')

public/
└── frontend/
    ├── sass/                        # source — see Chapter 08 for the full 0-abstracts → 5-pages layout
    │   ├── app.sass
    │   ├── pages.sass
    │   ├── lang.sass
    │   ├── 0-abstracts/
    │   ├── 1-base/
    │   ├── 2-plugins/
    │   ├── 3-modules/
    │   ├── 4-layouts/
    │   └── 5-pages/
    ├── css/                         # compiled output — app.min.css, pages.min.css (+ .map files)
    ├── js/
    └── images/
```

Rules:

- One controller method per page/route. The controller's only job is to gather data and `return view('<name>', [...])` — no markup, no styling decisions.
- One Blade view per route under `resources/views/`, named to match the page/feature it renders.
- Anything rendered on **two or more pages** (a header, a footer, a card slider, a reviews carousel, a filter form) belongs in `resources/views/components/` as a Blade component — never copy-pasted markup into a second view.
- The compiled CSS/JS output lives under `public/frontend/` (or the project's established equivalent); SASS **source** lives alongside it under `public/frontend/sass/`, following the Chapter 08 layer structure exactly. Never hand-edit the compiled `.min.css`/`.min.css.map` files — always edit the `.sass` source and recompile.

---

# The Page Pattern

Every route follows the same shape: route → controller → Blade view extending the shared layout.

```php
// routes/web.php
Route::get('/listing', [ListingController::class, 'index'])->name('listing');
```

```php
// app/Http/Controllers/ListingController.php
class ListingController extends Controller
{
    public function index()
    {
        $items = Item::query()->latest()->get();

        return view('listing', [
            'items' => $items,
        ]);
    }
}
```

```blade
{{-- resources/views/listing.blade.php --}}
@extends('layouts.app')

@push('css')
    {{-- page-specific <link> tags only, if any --}}
@endpush

@section('content')
    <main id="pageWrapper" class="listingPage">
        <x-page-header :title="'Listing'" />

        @foreach ($items as $item)
            <x-item-card :item="$item" />
        @endforeach
    </main>
@endsection

@push('js')
    {{-- page-specific <script> tags only, if any --}}
@endpush
```

- The controller passes data as a plain array; the view never queries the database directly.
- `layouts/app.blade.php` owns `<head>`, the shared `app.min.css`/`app.js` references, `@stack('css')`/`@stack('js')` push targets, and the header/footer components — a page view never redeclares any of this.
- When two pages need the same query/listing logic, extract it into a model scope or a shared service — do not copy the query into two controllers.

---

# Blade Component Convention

A Blade component is this stack's reusable UI primitive — the direct equivalent of a shadcn-style component in a React stack. It must be genuinely reusable, which means **both its markup and its CSS** travel together conceptually, even though Blade and SASS keep them in separate files.

```blade
{{-- resources/views/components/item-card.blade.php --}}
@props([
    'item' => [],
])

@php
    $title = $item['title'] ?? '';
    $price = $item['price'] ?? null;
@endphp

<div {{ $attributes->merge(['class' => 'itemCard']) }}>
    <h3>{{ $title }}</h3>
    @if ($price)
        <span class="price">{{ $price }}</span>
    @endif
</div>
```

- `@props([...])` defines the component's public API with typed/array defaults — never read undeclared variables from the parent scope.
- Use a `@php` block immediately after `@props` only when a single array/object prop needs field extraction for readability inside the template — do not scatter `$item['x'] ?? ''` fallbacks throughout the markup.
- `$attributes->merge(['class' => 'baseClass'])` lets a calling page add a modifier class (`<x-item-card :item="$item" class="itemCard--featured" />`) without the component needing a dedicated `variant` prop for every situation.
- **Multiple instances of the same slider/carousel component on one page** (e.g. the same card-slider component used twice in different sections) need a per-usage suffixed class in addition to the shared base class, so JS initialization (Swiper/Splide) can target each instance independently without one config clobbering the other:

```blade
<x-card-slider :items="$featured" class="cardSlider--featured" />
<x-card-slider :items="$related" class="cardSlider--related" />
```

```js
document.querySelectorAll('.cardSlider--featured, .cardSlider--related').forEach((el) => {
    new Swiper(el.querySelector('.swiper'), { /* ... */ });
});
```

The base class (`cardSlider`) carries the shared CSS; the suffixed class exists purely so JS and (if ever needed) a one-off style override can disambiguate instances.

---

# The Golden Rule: Shared Component CSS Lives in Modules, Not Pages

This is the single most important, most frequently violated rule when building Blade components, and it is worth stating on its own.

**If a Blade component's markup lives in `resources/views/components/`, its CSS must live in `public/frontend/sass/3-modules/`, never in `public/frontend/sass/5-pages/`.**

Why this happens: a component is often built for and first used on one page. It is easy — and seems harmless — to write its styles directly into that page's `5-pages/_somePage.sass` partial, because it works and looks correct on that page. The failure only appears the moment the component is reused on a *second* page, because `pages.sass` only compiles each page's own partial into `pages.min.css` — a second page's bundle never includes the first page's partial, so the component renders completely unstyled there.

```text
WRONG                                           RIGHT
resources/views/components/item-card.blade.php  resources/views/components/item-card.blade.php
public/frontend/sass/5-pages/_listingPage.sass  public/frontend/sass/3-modules/_itemCard.sass
    .itemCard { ... }   ← only on listingPage       .itemCard { ... }   ← in app.min.css, every page
```

Rule of thumb: **the moment a component's Blade file moves into `resources/views/components/`, its SASS partial moves into `3-modules/` in the same change.** Don't wait for the second page that breaks to notice.

---

# Styling System

The Chapter 08 SASS architecture applies to Laravel projects exactly as written — the 6-layer `0-abstracts` → `5-pages` structure, the two-bundle (`app.sass` / `pages.sass`) strategy, and the directory-index-file import rule are all unchanged. The Laravel-specific additions are:

- SASS source lives under `public/frontend/sass/` (or the project's established equivalent path) rather than a generic `assets/sass/`; compiled output lives alongside it in `public/frontend/css/`. Check the project's existing `app.sass`/`pages.sass` for the actual compile target before assuming a path.
- `layouts/app.blade.php` is the only place that links `app.min.css`; individual page views only ever add a page's own entry inside `pages.min.css` (already compiled in) — never a second `<link>` for shared styling.
- Breakpoints are written as **literal inline `@media (min-width: …)` queries** per this handbook's global rule — never a SASS mixin, never a stored breakpoint variable — even though SASS's `@mixin`/`@include` facility would make a breakpoint helper technically easy to write. This keeps every breakpoint value grep-able and auditable directly in the partial that uses it.
- Third-party plugin styling (Swiper, Splide, select2, date pickers) belongs in `2-plugins/`, isolated from `3-modules/`. Do not manually set `overflow` on a slider library's own track element (e.g. Splide's `.splide__track`) — let the plugin's core CSS handle clipping; only override properties the approved design actually requires changing.
- A plugin's default visual affordance (e.g. a `<select>` enhancement library's dropdown arrow) is frequently tuned for a light background and invisible/wrong on a dark one. Fix with a CSS-drawn replacement scoped to the plugin's own override partial (e.g. a `border-right`/`border-bottom` chevron rotated via `::after`, with the library's own icon suppressed via `background-image: none`) rather than fighting the library's internal markup.

---

# Figma-to-Code Workflow

1. **Fetch the Figma node's structured data** *and* **export a full-frame screenshot** of the same node. Large frames can exceed a single tool response — save the raw dump to a file and search it rather than guessing from a truncated view.
2. **Cross-reference the structured layer order against the screenshot's actual visual (Y-coordinate) order.** A design tool's raw layer/node order does not reliably match the order sections appear on screen — trust vertical position, not list order, when reconstructing section sequence.
3. **Don't attempt to losslessly reconstruct a vector icon that was exported as dozens of decomposed path fragments.** Hand-author a clean, simple SVG that matches the visual intent, or reuse an existing consistent icon from the project — pixel-for-pixel fragment reconstruction is not a productive use of time.
4. **Download every real asset you'll use** into the project's existing asset convention (`public/frontend/images/`, etc.) — never hot-link back to the design tool's CDN.
5. **Build using the project's existing Blade layout/component patterns**, not a new pattern per page.
6. **Verify against the screenshot at more than one breakpoint** (see Verification Workflow below) before calling the page done.

---

# Comparing a Page Against an Exported Design PDF

Design references are sometimes delivered as a single long export PDF (one continuous full-page frame) rather than live Figma access. If the environment has no PDF-rendering tool available (e.g. no `pdftoppm`/poppler, and the OS package manager can't reach its registry), render the PDF to image slices with a Python one-off instead of giving up on visual comparison:

```python
import fitz  # pip install pymupdf

doc = fitz.open(r'path/to/design.pdf')
page = doc[0]
h, w = page.rect.height, page.rect.width
slice_h, zoom = 1000, 0.6   # points per slice; zoom balances detail vs. image size
mat = fitz.Matrix(zoom, zoom)
i, y = 0, 0
while y < h:
    clip = fitz.Rect(0, y, w, min(y + slice_h, h))
    page.get_pixmap(matrix=mat, clip=clip).save(f'{out_dir}/slice_{i:02d}.png')
    y += slice_h
    i += 1
```

`pip` frequently has working network access in locked-down environments even when a system package manager does not — prefer it over retrying the OS package manager. Save slices to a scratch directory, view them in order, then delete them once the comparison is done — they are not a deliverable.

---

# Verification Workflow

A page is not complete until it has been checked live, not just read as Blade/SASS source.

1. Recompile SASS to CSS before testing — a stale compiled bundle will hide real changes or show phantom ones.
2. Serve the app (the project's existing local dev server/virtual host) and navigate to the new route in a real browser.
3. **Check the browser console for errors before screenshotting.** Distinguish *new* problems from *pre-existing* ones on other pages.
4. Screenshot at the design's native width and compare crops against the Figma/PDF export.
5. Re-check at a laptop width and a mobile width — confirm the responsive scaling holds up and nothing overlaps, per this handbook's standard container/breakpoint table.
6. For any shared Blade component, **verify it on every page that uses it**, not just the page you were actively building — this is the only reliable way to catch the Modules-vs-Pages CSS mistake described above.
7. For interactive sections (carousels, accordions, enhanced selects, filter forms), actually interact with them — don't assume a handler works because the markup looks right.
8. Clean up any scratch screenshots/temp files created for comparison — they are not part of the deliverable.

---

# Git & Delivery Workflow

- Compiled CSS artifacts (`*.min.css`, `*.min.css.map`) are the most common source of merge conflicts on a multi-developer Laravel/SASS project, because two branches both regenerate the same bundle from different SASS source. **Resolve these by taking either side's SASS source changes, then recompiling fresh** — never hand-merge the minified output or its source map; a hand-merged compiled file will not match its own map and will desync from the SASS source on the next build.
- Keep SASS source changes and their recompiled output in the same commit — a commit with SASS edits but no corresponding compiled-CSS update (or vice versa) leaves the working tree in a state that doesn't match what either file claims.
- Only commit files relevant to the task. Leave unrelated stray/uncommitted changes from before your session started untouched unless the user asks about them.
- Write commit messages that explain *why*, and call out any deliberate deviation from the literal design (see the Figma-mistake-handling note above) so reviewers aren't surprised later.

---

# Known Pitfall Patterns (and fixes)

| Symptom | Cause | Fix |
|---|---|---|
| A shared Blade component renders unstyled on a second page but fine on the first | Component's CSS was written into that first page's `5-pages/_xPage.sass` partial instead of `3-modules/` | Move the CSS into a `3-modules/_componentName.sass` partial, imported through the Modules directory index |
| Two instances of the same slider component on one page animate/behave identically or one breaks the other | Both instances share only the base class; the slider JS selects by that class and binds to the first match (or binds the same config to both) | Add a per-usage suffixed class (e.g. `cardSlider--featured`, `cardSlider--related`) and initialize JS per suffixed selector |
| A dark-background `<select>` shows a barely-visible or mismatched dropdown arrow | Plugin's default arrow asset/markup was tuned for a light background | Draw a CSS chevron on `::after` scoped to the plugin override partial, suppress the library's own icon |
| Design comparison looks visually "out of order" vs. the structured Figma data | Figma/PDF layer order doesn't match true on-screen (Y-coordinate) order | Cross-reference Y-coordinates from the screenshot, not the raw layer list |
| PDF design reference can't be opened/rendered in the dev environment | No `pdftoppm`/poppler installed, OS package manager has no network access | `pip install pymupdf`, render to PNG slices with a short script |
| A Blade component's slider track clips oddly or scrolls where it shouldn't | Page-specific SASS manually set `overflow` on the plugin's own track element | Remove the manual `overflow` override; let the plugin's core CSS handle clipping |

---

# Mandatory Rules

Every Laravel page/feature built under this standard MUST:

- Keep controllers thin: gather data, return a view — no markup, no styling decisions, no inline queries inside a Blade file.
- Extract any markup used on two or more pages into a Blade component in `resources/views/components/`.
- Move a Blade component's CSS into `3-modules/` **in the same change** that extracts its markup — never leave it in a page-scoped partial "for now."
- Use `@props([...])` to define every Blade component's public API; never read undeclared parent-scope variables inside a component.
- Give every repeated instance of the same slider/carousel component a per-usage suffixed class for JS targeting.
- Write every breakpoint as a literal inline `@media (min-width: …)` query — never a SASS mixin, never a stored variable.
- Cross-check structured Figma data against a rendered screenshot (Y-coordinate order, not layer-list order) before trusting either alone.
- Verify a shared component on **every** page that uses it before calling a change complete, not only the page you were actively building.
- Recompile SASS→CSS, and resolve any compiled-CSS merge conflict by recompiling from merged SASS source — never by hand-editing the minified output.

---

# Validation Checklist

Before marking a Laravel page/feature complete, verify:

## Architecture
- [ ] Controller only gathers data and returns a view (no markup/styling decisions, no inline business logic in Blade).
- [ ] Any markup used on 2+ pages is a Blade component in `resources/views/components/`, not copy-pasted.
- [ ] Shared query/data logic extracted to one place if used by more than one controller.

## Styling
- [ ] Every shared Blade component's CSS lives in `3-modules/`, not a page-scoped `5-pages/` partial.
- [ ] Breakpoints written as literal `@media (min-width: …)` queries, matching this handbook's standard table.
- [ ] Plugin styling (sliders, enhanced selects) isolated in `2-plugins/`, no manual `overflow` on a slider library's own track element.
- [ ] SASS recompiled; compiled `.min.css`/`.map` matches the current source.

## Figma / Design Fidelity
- [ ] Structured design data cross-checked against a rendered screenshot (true Y-order, not layer-list order).
- [ ] All real assets downloaded into the project's asset convention (no hot-linking).
- [ ] Any duplicated/mislabeled design content identified and corrected with judgment, not copied as-is.

## Verification
- [ ] Console checked for new errors/warnings (vs. pre-existing ones on other pages).
- [ ] Screenshot comparison done at desktop, laptop, and mobile widths.
- [ ] Every shared component checked on **all** pages that use it, not only the page just built.
- [ ] Interactive elements (sliders, selects, filter forms) actually exercised, not just visually inspected.

---

# Common Mistakes

Avoid:

- Writing a shared Blade component's CSS into a page-scoped `5-pages/` partial instead of `3-modules/`.
- Reusing the same slider/carousel component twice on one page without a suffixed class for JS targeting.
- Reading undeclared parent-scope variables inside a Blade component instead of declaring them via `@props`.
- Putting database queries or business logic directly inside a Blade view.
- Trusting a design tool's raw layer order as true visual page order.
- Hand-editing compiled `.min.css`/`.map` files, or hand-merging them during a git conflict, instead of recompiling from SASS source.
- Manually overriding `overflow` on a slider plugin's own track element.
- Declaring a page "done" after checking only the page you built, when the change touched a shared component used elsewhere.

---

# Best Practices

- Read the project's own `CLAUDE.md`/`AGENTS.md` before this chapter's generic defaults — project-specific instructions win.
- Treat "does this markup appear on a second page?" as the trigger to promote it into a Blade component, and promote its CSS into `3-modules/` in the same change.
- Keep controllers and Blade views thin; push data-shaping logic into the model/service layer.
- Cross-reference structured design data against a rendered screenshot rather than trusting either alone.
- Recompile and visually re-check every page that consumes a shared component whenever that component changes.
- Clean up scratch/comparison files (screenshots, PDF slices) before finishing; they are not deliverables.

---

# Chapter Summary

Laravel + Blade projects replace this handbook's vanilla-PHP include architecture (Chapter 05) with framework-owned routing and controllers, but keep the Chapter 08 SASS architecture and Chapter 11 component principles fully intact. The one Laravel-specific failure mode worth internalizing above all others is the Modules-vs-Pages CSS split: a Blade component's markup and its CSS must be promoted to shared layers together, in the same change, or the component will silently break the next time it's reused.

Combined with Chapter 03 (Figma Standards), Chapter 08 (SASS Architecture), Chapter 11 (Components), and Chapter 24 (AI Development Rules), it forms the complete workflow for delivering a Laravel/Blade page from an approved design to a verified, framework-correct implementation.

---
