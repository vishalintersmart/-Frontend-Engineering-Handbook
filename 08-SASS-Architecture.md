# 08 – SASS Architecture

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project using the project's SASS architecture.
>
> **Related Chapters**
>
> - 04 Project Architecture
> - 07 CSS Standards
> - 09 Responsive System
> - 10 Design Tokens
> - 11 Components

---

# Purpose

This chapter defines the mandatory SASS architecture used throughout the project.

The objective is to establish a scalable styling system that remains consistent across all pages while minimizing duplication and improving maintainability.

Rather than treating stylesheets as individual files, the project organizes styling into architectural layers, each with a clearly defined responsibility.

This architecture should be followed for every frontend project.

---

# Objective

The styling system should:

- remain modular
- remain scalable
- minimize duplicated code
- separate shared styling from page styling
- encourage reuse
- simplify maintenance
- reduce stylesheet size

Every stylesheet should belong to a specific architectural layer.

---

# Engineering Philosophy

SASS is used as an architectural system rather than simply a CSS preprocessor.

Every partial exists for a specific purpose.

Developers should never create new folders or layers without understanding the responsibility of the existing architecture.

Architecture should be extended—not replaced.

---

# Mandatory Rules

Every project MUST:

- Use the approved folder hierarchy.
- Use indented `.sass` syntax.
- Follow the ITCSS layer order.
- Keep shared styles separate from page styles.
- Import through directory index files only.
- Reuse shared modules.
- Scope page-specific styling through the page wrapper.
- Keep architectural responsibilities isolated.

These rules are mandatory for every project.

---

# Styling Architecture

The styling architecture is divided into ordered layers.

Each layer has one responsibility.

```
0 Abstracts

↓

1 Base

↓

2 Plugins

↓

3 Modules

↓

4 Layouts

↓

5 Pages
```

Each layer depends only on the layers above it.

The order must never be changed.

---

# Why Layered Architecture?

Separating styling into layers provides:

- predictable cascade
- easier maintenance
- reusable styling
- reduced duplication
- cleaner overrides
- simpler debugging

Every layer should solve one type of problem.

---

# Layer Responsibilities

## Layer 0 — Abstracts

Purpose

Provide reusable resources.

Contains:

- Variables
- Mixins
- Functions
- Global helpers

This layer produces **no CSS output**.

Its only responsibility is to support the remaining layers.

---

## Layer 1 — Base

Purpose

Define the global styling foundation.

Contains:

- Font declarations
- Browser resets
- Global typography
- Body styling
- Element defaults

Base styling should affect the project globally.

---

## Layer 2 — Plugins

Purpose

Provide styling for third-party libraries.

Typical examples include:

- Slider plugins
- Select components
- Date pickers
- Animation libraries

Plugin styling should remain isolated from project modules.

---

## Layer 3 — Modules

Purpose

Provide reusable UI components.

Examples include:

- Buttons
- Cards
- Hero modules
- CTA sections
- Shared banners
- Shared grids

Modules should never contain page-specific styling.

If the same component appears on multiple pages, it belongs here.

---

## Layer 4 — Layouts

Purpose

Define the structural framework of the website.

Typical contents include:

- Header
- Footer
- Global layout
- Home layout
- Shared navigation

Layouts define the overall skeleton of the website.

---

## Layer 5 — Pages

Purpose

Provide styling specific to a single page.

Each page should have one dedicated partial.

Examples:

```
_aboutPage.sass

_contactPage.sass

_servicesPage.sass
```

Page partials should never redefine shared modules.

Instead, page-specific overrides should be scoped using the page wrapper.

---

# Folder Structure

Every project should follow this structure.

```text
assets/

sass/

app.sass

pages.sass

lang.sass

0-abstracts/

1-base/

2-plugins/

3-modules/

4-layouts/

5-pages/
```

The folder hierarchy should remain consistent across projects.

---

# Architectural Responsibilities

Each folder exists for a specific purpose.

Developers should not move files between layers simply because they "work."

Correct architectural placement is part of the engineering standard.

---

# Engineering Benefits

Following this architecture provides:

- scalable projects
- smaller CSS bundles
- cleaner overrides
- reusable modules
- easier onboarding
- faster development
- predictable maintenance

These benefits depend upon strict adherence to the layer responsibilities defined above.

---
---

# Standard SASS Directory Structure

Every project must follow a consistent SASS directory structure.

The directory structure is part of the engineering standard and should remain unchanged unless the project architecture is formally revised.

```text
assets/
└── sass/
    │
    ├── app.sass                 // Main frontend bundle
    ├── pages.sass              // Page-specific bundle
    ├── lang.sass               // RTL/LTR or language overrides (if applicable)
    │
    ├── 0-abstracts/
    │   ├── _variables.sass
    │   ├── _functions.sass
    │   ├── _mixins.sass
    │   ├── _helpers.sass
    │   └── _abstracts-dir.sass
    │
    ├── 1-base/
    │   ├── _reset.sass
    │   ├── _typography.sass
    │   ├── _fonts.sass
    │   ├── _global.sass
    │   └── _base-dir.sass
    │
    ├── 2-plugins/
    │   ├── _splide.sass
    │   ├── _swiper.sass
    │   ├── _select2.sass
    │   └── _plugins-dir.sass
    │
    ├── 3-modules/
    │   ├── _buttons.sass
    │   ├── _forms.sass
    │   ├── _cards.sass
    │   ├── _hero.sass
    │   ├── _cta.sass
    │   └── _modules-dir.sass
    │
    ├── 4-layouts/
    │   ├── _header.sass
    │   ├── _footer.sass
    │   ├── _navigation.sass
    │   ├── _layout.sass
    │   └── _layouts-dir.sass
    │
    └── 5-pages/
        ├── _homePage.sass
        ├── _aboutPage.sass
        ├── _contactPage.sass
        ├── _servicesPage.sass
        └── _pages-dir.sass
```

---

# Folder Responsibilities

Each folder has a single engineering responsibility.

Developers must place files in the correct layer rather than wherever they appear to work.

Moving files between layers without architectural justification is not permitted.

---

# app.sass

## Purpose

`app.sass` is the primary stylesheet entry point.

It assembles every shared styling layer into a single compiled CSS bundle.

---

## Responsibilities

`app.sass` imports only directory index files.

Example:

```sass
@use "0-abstracts/abstracts-dir"
@use "1-base/base-dir"
@use "2-plugins/plugins-dir"
@use "3-modules/modules-dir"
@use "4-layouts/layouts-dir"
```

`app.sass` should **not** import individual partials directly.

---

# pages.sass

## Purpose

`pages.sass` compiles page-specific styling.

Only page-level partials should be included.

Example:

```sass
@use "5-pages/pages-dir"
```

Shared modules should not be imported here.

---

# lang.sass

## Purpose

Provides language-specific styling where required.

Examples include:

- RTL adjustments
- Language-specific typography
- Locale-specific overrides

Projects without multilingual requirements may omit this bundle.

---

# Directory Index Files

Each architectural layer contains a single directory index file.

Examples:

```text
_abstracts-dir.sass
_base-dir.sass
_plugins-dir.sass
_modules-dir.sass
_layouts-dir.sass
_pages-dir.sass
```

These files act as aggregation points for the layer.

---

# Import Chain Rule

## Mandatory Rule

Every import must flow through the directory index file.

Correct:

```text
app.sass
        ↓
_base-dir.sass
        ↓
_typography.sass
```

Incorrect:

```text
app.sass
        ↓
_typography.sass
```

Direct imports bypass the architecture and make long-term maintenance more difficult.

---

# Layer Import Order

The import order must never change.

```text
0 Abstracts

↓

1 Base

↓

2 Plugins

↓

3 Modules

↓

4 Layouts

↓

5 Pages
```

Changing this order can introduce dependency issues and inconsistent styling behaviour.

---

# Two Bundle Strategy

The styling architecture separates shared styling from page-specific styling.

Bundle 1:

```text
app.css
```

Contains:

- Abstracts
- Base
- Plugins
- Modules
- Layouts

---

Bundle 2:

```text
pages.css
```

Contains only:

- Page-specific styling

This separation reduces unnecessary CSS on pages that do not require page-specific rules.

---

# Why Two Bundles?

Separating shared and page-specific CSS provides:

- Smaller initial downloads
- Better browser caching
- Faster page rendering
- Improved maintainability
- Cleaner architecture

Shared styles change less frequently than page styles and therefore benefit from long-term caching.

---

# Compilation Flow

The compilation process follows a predictable sequence.

```text
SASS Partials

↓

Directory Index Files

↓

Entry Files

↓

Compiled CSS

↓

Browser
```

Every stylesheet follows this pipeline.

---

# Architectural Rules

Developers must not:

- Import partials directly into page files.
- Skip directory index files.
- Move modules into page layers.
- Duplicate shared styling.
- Place global rules inside page partials.
- Override architectural responsibilities.

---

# Validation Checklist

Before compiling verify:

- [ ] Folder structure matches the standard.
- [ ] Every layer contains a directory index file.
- [ ] `app.sass` imports only directory index files.
- [ ] `pages.sass` imports only page styles.
- [ ] Layer order is correct.
- [ ] Shared modules remain in the Modules layer.
- [ ] Layout styling remains in the Layouts layer.
- [ ] Page styling remains in the Pages layer.
- [ ] No direct imports bypass the architecture.

---

# Common Mistakes

Avoid:

- Importing individual partials into `app.sass`.
- Mixing page styles with shared modules.
- Creating duplicate components in multiple layers.
- Changing the layer order.
- Writing global styles inside page partials.
- Bypassing directory index files.
- Creating new architectural layers without approval.

---

# Best Practices

- Keep every layer focused on a single responsibility.
- Use directory index files consistently.
- Keep shared styling truly shared.
- Scope page-specific rules through the page wrapper.
- Review the architecture before adding new partials.
- Prefer extending existing modules over creating new ones.

---