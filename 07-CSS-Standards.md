# 07 – CSS Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** All project stylesheets.
>
> **Related Chapters**
>
> - 04 Project Architecture
> - 06 HTML Standards
> - 08 SASS Architecture
> - 09 Responsive System
> - 10 Design Tokens

---

# Purpose

This chapter defines the mandatory CSS engineering standards for all frontend projects.

Its purpose is to ensure styling remains:

- Consistent
- Reusable
- Maintainable
- Scalable
- Performant

Every stylesheet written for the project should follow the standards defined within this chapter.

---

# Objective

CSS should describe presentation while remaining independent from document structure.

A well-organized styling architecture reduces:

- duplicated code
- maintenance effort
- specificity conflicts
- inconsistent styling

The objective is to build a styling system rather than isolated CSS rules.

---

# Mandatory Rules

Every implementation MUST:

- Reuse existing project CSS.
- Avoid inline CSS.
- Avoid `!important`.
- Avoid duplicated CSS.
- Reuse project variables.
- Follow the approved styling architecture.
- Use design tokens where available.

These rules are mandatory for every project.

---

# CSS Responsibilities

CSS is responsible only for presentation.

Examples include:

- Layout
- Typography
- Colors
- Spacing
- Borders
- Shadows
- Animations
- Responsive styling

CSS should never be used to replace proper HTML structure or JavaScript behaviour.

---

# Styling Philosophy

Styling should be written once and reused whenever possible.

Developers should prefer:

- Shared modules
- Shared utilities
- Shared variables
- Shared design tokens

instead of duplicating declarations throughout the project.

---

# Reuse Existing CSS

Before creating a new selector, developers should determine whether an equivalent styling solution already exists.

Always inspect:

- Global styles
- Shared modules
- Utility classes
- Existing components

before introducing new CSS.

Creating duplicate styling increases maintenance complexity and should be avoided.

---

# Inline CSS

Inline styles are not permitted.

Avoid:

```html
<div style="margin-top:40px">
```

Instead:

```css
.sectionSpacing
```

Inline styles reduce maintainability and bypass the established styling architecture.

---

# !important

The use of `!important` should be avoided.

`!important` often indicates:

- specificity problems
- architecture problems
- selector conflicts

Instead of using `!important`, resolve the underlying selector hierarchy.

Use of `!important` should only occur when there is no practical alternative and should be documented.

---

# Duplicate CSS

Duplicate declarations should not exist.

Bad:

```css
.heroTitle {
    color: #111;
}

.aboutTitle {
    color: #111;
}
```

Preferred:

```css
.sectionTitle {
    color: var(--clr-heading);
}
```

Shared styling should exist once.

---

# CSS Variables

Projects should reuse existing CSS custom properties wherever available.

Variables provide:

- consistency
- maintainability
- centralized updates

Avoid hardcoding values that already exist as shared variables.

---

# Design Tokens

Visual values should originate from the project's design token system.

Typical tokens include:

Typography

- Font size
- Line height
- Letter spacing

Spacing

- Section spacing
- Component spacing
- Gap values

Colors

- Primary
- Secondary
- Heading
- Body
- White

Design tokens become the single source of truth for styling values.

---

# Styling Consistency

Every reusable component should share the same styling language.

Examples include:

Buttons

Forms

Cards

Navigation

Footer

Hero

Spacing

Typography

The same component should not appear visually different across pages unless intentionally overridden.

---

# Selector Responsibilities

Selectors should clearly represent their responsibility.

Selectors should not attempt to solve multiple unrelated problems.

Each selector should have a focused purpose.

---

# CSS Architecture Goals

A successful stylesheet should be:

- Readable
- Predictable
- Modular
- Reusable
- Scalable
- Maintainable

These goals should guide every styling decision throughout the project.

---