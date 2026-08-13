# 10 – Design Tokens

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project using the approved styling architecture.
>
> **Related Chapters**
>
> - 07 CSS Standards
> - 08 SASS Architecture
> - 09 Responsive System
> - 11 Components

---

# Purpose

Design Tokens provide the single source of truth for all reusable visual values throughout the project.

Rather than hardcoding design values repeatedly, every reusable visual property should originate from a centralized token system.

This ensures:

- Consistency
- Scalability
- Easier maintenance
- Faster global updates
- Predictable styling

---

# Objective

Every reusable visual value should exist once.

Developers should consume design tokens rather than creating new values during implementation.

Tokens should represent the design language—not individual components.

---

# Engineering Philosophy

Design Tokens are architectural resources.

They define the visual language shared across every page, component, layout, and module.

Changing a token should update every dependent component without requiring individual edits.

---

# Mandatory Rules

Every project MUST:

- Centralize reusable values.
- Reuse existing tokens.
- Avoid hardcoded reusable values.
- Maintain consistent naming.
- Keep tokens independent of individual pages.
- Use tokens throughout shared modules.

These rules apply to every frontend implementation.

---

# Token Categories

The project token system is organized into reusable categories.

Typical categories include:

- Colors
- Typography
- Spacing
- Containers
- Border Radius
- Shadows
- Z-Index
- Motion
- Opacity

Each category represents one aspect of the design language.

---

# Color Tokens

Color tokens define the project's reusable color palette.

Examples include:

- Primary
- Secondary
- Accent
- Heading
- Body Text
- White
- Black
- Surface
- Border
- Success
- Warning
- Error

Components should reference tokens rather than hardcoded color values.

---

# Typography Tokens

Typography tokens define reusable text values.

Typical tokens include:

- Font Family
- Font Weight
- Font Size
- Line Height
- Letter Spacing
- Text Transform

Typography should remain consistent throughout the project.

---

# Spacing Tokens

Spacing tokens define reusable spacing values.

Examples:

- Section spacing
- Component spacing
- Grid gap
- Internal padding
- Margin scale

Spacing relationships should remain consistent across all pages.

---

# Border Radius Tokens

Border radius should be centralized.

Examples include:

- Small
- Medium
- Large
- Pill
- Circular

Components with similar visual styles should reuse the same radius tokens.

---

# Shadow Tokens

Shadow tokens define reusable elevation styles.

Typical categories:

- Level 1
- Level 2
- Level 3
- Focus Shadow
- Hover Shadow

Avoid creating new shadows for individual components without design approval.

---

# Motion Tokens

Motion tokens define reusable animation values.

Examples include:

- Transition Duration
- Transition Delay
- Animation Duration
- Timing Functions

Animation behaviour should remain consistent across the project.

---

# Opacity Tokens

Opacity values should also be centralized.

Examples include:

- Disabled
- Overlay
- Hover
- Glass Effects

Avoid arbitrary opacity values throughout the project.

---

# Token Naming Standards

Token names should describe purpose rather than appearance.

Good examples:

```text
$clr-primary

$clr-heading

$space-section-lg

$radius-md

$shadow-card

$container-xl
```

Avoid:

```text
$blue

$red

$size1

$margin2

$boxShadowNew
```

---

# Token Usage Rules

Before introducing a new value:

1. Check existing tokens.
2. Determine whether an equivalent token already exists.
3. Reuse the existing token whenever possible.
4. Create a new token only when the value represents a new design decision.

Duplicate tokens should not exist.

---

# Validation Checklist

Before completing implementation verify:

## Colors

- [ ] Shared color tokens reused.
- [ ] No duplicate color definitions.

---

## Typography

- [ ] Font tokens reused.
- [ ] Typography remains consistent.

---

## Spacing

- [ ] Shared spacing tokens used.
- [ ] No arbitrary spacing values.

---

## Layout

- [ ] Shared container tokens used.

---

## Components

- [ ] Shared radius tokens reused.
- [ ] Shared shadow tokens reused.

---

## Motion

- [ ] Shared transition values reused.

---

# Common Mistakes

Avoid:

- Hardcoding colors.
- Hardcoding spacing.
- Duplicate typography values.
- Component-specific tokens.
- Inconsistent naming.
- Arbitrary border radius values.
- New shadow definitions for existing component types.

---

# Best Practices

- Treat tokens as the project's design language.
- Reuse tokens before creating new ones.
- Keep token names descriptive and consistent.
- Organize tokens by category.
- Review token usage before introducing new visual values.
- Keep token definitions centralized.

---

# Engineering Acceptance Criteria

A project complies with the Design Token standard when:

- All reusable visual values originate from centralized tokens.
- Duplicate token definitions do not exist.
- Components consistently reuse shared tokens.
- New tokens represent genuine design decisions rather than implementation convenience.

---

# Chapter Summary

Design Tokens form the visual foundation of the frontend architecture.

They centralize the project's reusable visual language and ensure that every page, layout, module, and component shares the same design system.

Following this standard improves consistency, maintainability, scalability, and long-term project quality.

---