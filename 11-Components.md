# 11 – Components

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every reusable UI component developed for the project.
>
> **Related Chapters**
>
> - 04 Project Architecture
> - 06 HTML Standards
> - 07 CSS Standards
> - 08 SASS Architecture
> - 10 Design Tokens
> - 12 CMS Development

---

# Purpose

This chapter defines the engineering standards for building reusable frontend components.

Components are the primary building blocks of every page.

A well-designed component should be:

- Reusable
- Maintainable
- Predictable
- Scalable
- Consistent

Every reusable UI element should follow the standards defined in this chapter.

---

# Objective

Components should be written once and reused throughout the project.

Developers should extend existing components before creating new ones.

Identical UI should never be implemented using multiple component structures.

---

# Engineering Philosophy

A component represents a single UI responsibility.

It should encapsulate:

- Structure
- Styling
- Behaviour

without depending on page-specific implementation.

Shared components belong to the shared architecture.

Page-specific implementations belong to the page layer.

---

# Mandatory Rules

Every reusable component MUST:

- Follow the approved HTML structure.
- Follow the approved SASS architecture.
- Reuse Design Tokens.
- Remain independent of page-specific styling.
- Be reusable across multiple pages.
- Avoid duplicated markup.
- Avoid duplicated styling.
- Avoid duplicated JavaScript.

These rules are mandatory.

---

# What Is a Component?

A component is a reusable UI block that can appear in one or more locations throughout the project.

Examples include:

- Buttons
- Cards
- Forms
- Hero sections
- Navigation
- CTA blocks
- Accordions
- Sliders
- Feature lists
- Breadcrumbs

If a UI pattern appears repeatedly, it should be treated as a component.

---

# Component Categories

Components generally fall into two categories.

## Shared Components

Shared components are reused across multiple pages.

Examples:

- Primary Button
- Navigation
- Footer
- Form Controls
- Cards
- CTA Modules

Shared components belong in the **Modules** layer of the SASS architecture.

---

## Page Components

Page components exist only on a single page.

Examples:

- Campaign-specific banner
- One-off timeline
- Landing page infographic

These belong in the **Pages** layer and should not be promoted to shared modules unless reused elsewhere.

---

# Component Responsibilities

Every component should have one clearly defined responsibility.

Examples:

A button triggers an action.

A card presents related content.

A form collects user input.

A navigation component provides page navigation.

Avoid creating components that solve multiple unrelated problems.

---

# Component Structure

Every component should follow a predictable internal structure.

Typical composition includes:

- Wrapper
- Content
- Media (if applicable)
- Actions (if applicable)

The structure should remain consistent wherever the component is reused.

---

# Component Independence

Reusable components should not depend on:

- Page-specific selectors
- Page-specific layout assumptions
- Inline styles
- Hardcoded content

Components should function correctly wherever they are placed within the approved architecture.

---

# Component Styling

Styling should:

- Reuse Design Tokens.
- Live in the appropriate SASS layer.
- Follow shared naming conventions.
- Avoid duplication.
- Avoid page-specific overrides unless explicitly required.

---

# Component Behaviour

If JavaScript is required:

- Shared behaviour belongs in shared JavaScript.
- Page-specific behaviour remains scoped to the page.

Avoid embedding page-specific logic into reusable components.

---

# Buttons

Buttons should maintain a common implementation across the project.

Consistency includes:

- Height
- Padding
- Typography
- Border radius
- Icon sizing
- Hover states
- Focus states
- Disabled states

The visual style may vary, but the structural pattern should remain consistent.

---

# Forms

Form components should remain consistent.

Examples include:

- Text Input
- Textarea
- Select
- Checkbox
- Radio Button
- Submit Button

Shared form controls should reuse the same HTML structure and styling.

---

# Cards

Cards should share:

- Layout
- Spacing
- Border radius
- Typography
- Action placement

Card variants should extend the shared component rather than introducing entirely new structures.

---

# Component Lifecycle

Every component should follow the same engineering lifecycle.

1. Identify reuse opportunity.
2. Check existing shared components.
3. Extend if possible.
4. Create only when necessary.
5. Validate.
6. Reuse.

---

# Component Validation Checklist

Before approving a component verify:

## Structure

- [ ] Semantic HTML used.
- [ ] Consistent markup.
- [ ] Minimal nesting.

---

## Styling

- [ ] Design Tokens reused.
- [ ] Shared styling reused.
- [ ] No duplicate CSS.

---

## Behaviour

- [ ] Shared JavaScript reused.
- [ ] No duplicate logic.

---

## Architecture

- [ ] Correct SASS layer.
- [ ] Correct folder placement.
- [ ] Page independence maintained.

---

# Common Mistakes

Avoid:

- Creating duplicate components.
- Page-specific shared components.
- Copying component markup.
- Inline styling.
- Hardcoded design values.
- Component-specific Design Tokens.
- Mixing page logic into reusable components.

---

# Best Practices

- Build for reuse first.
- Keep components focused.
- Reuse before creating.
- Extend rather than duplicate.
- Maintain predictable markup.
- Validate every component before reuse.

---

# Engineering Acceptance Criteria

A reusable component complies with this standard when:

- It has a single responsibility.
- It follows the shared HTML structure.
- It reuses shared styling.
- It consumes Design Tokens.
- It remains independent of page-specific implementation.
- It can be reused without modification.

---

# Chapter Summary

Components are the reusable building blocks of the frontend architecture.

Following these standards ensures every reusable UI element remains:

- Consistent
- Maintainable
- Scalable
- Reusable
- Predictable

The component system should grow by extending existing patterns rather than creating new, isolated implementations.

---