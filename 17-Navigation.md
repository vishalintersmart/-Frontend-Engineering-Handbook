# 17 – Navigation Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every primary, secondary, desktop, mobile, and footer navigation system.
>
> **Related Chapters**
>
> - 06 HTML Standards
> - 13 JavaScript Standards
> - 14 Accessibility
> - 16 Header Standards
> - 19 Browser QA

---

# Purpose

Navigation is the primary method users use to move throughout the website.

Every navigation implementation should remain consistent, predictable, responsive, and reusable across the project.

Navigation should be treated as a shared architectural component rather than page-specific functionality.

---

# Objective

Navigation should provide:

- Clear navigation hierarchy
- Predictable behaviour
- Responsive adaptation
- Accessible interaction
- Consistent styling
- Reliable functionality

Every navigation system should match the approved design while remaining easy to maintain.

---

# Engineering Philosophy

Navigation belongs to the shared project architecture.

It should be implemented once and reused throughout the project.

Individual pages should not redefine navigation behaviour.

---

# Mandatory Rules

Every navigation implementation MUST:

- Reuse the shared navigation component.
- Match the approved Figma design.
- Support all approved responsive breakpoints.
- Ensure every navigation link functions correctly.
- Ensure the mobile menu functions correctly.
- Maintain consistent navigation styling.
- Preserve semantic HTML structure.

These rules are mandatory.

---

# Navigation Types

Projects may include:

- Primary Navigation
- Secondary Navigation
- Mobile Navigation
- Footer Navigation
- Utility Navigation
- Breadcrumb Navigation

Each navigation type should have a clearly defined responsibility.

---

# Navigation Structure

Navigation should use semantic HTML.

Typical structure:

```html
<nav>

    <ul>

        <li>

            <a>

```

Navigation should remain meaningful even without CSS.

---

# Desktop Navigation

Desktop navigation should:

- Match Figma.
- Maintain spacing.
- Preserve alignment.
- Display all required links.
- Maintain hover behaviour.
- Preserve active states.

Navigation should remain visually consistent across every page.

---

# Mobile Navigation

The mobile navigation should:

- Open correctly.
- Close correctly.
- Support touch interaction.
- Preserve layout.
- Prevent page-breaking behaviour.
- Match the approved responsive design.

The mobile menu should be validated on every supported mobile breakpoint.

---

# Hamburger Menu

The hamburger menu is part of the navigation system.

Verify:

- Opens correctly.
- Closes correctly.
- Toggle state updates correctly.
- Animations match the approved design.
- Navigation remains usable after repeated interactions.

The hamburger menu should not trap the interface in an unusable state.

---

# Navigation Links

Every navigation link should be verified.

Confirm:

- Correct destination.
- Correct label.
- Correct target.
- Active state (where applicable).

Broken navigation links are considered implementation defects.

---

# Dropdown Navigation

Where dropdown menus are present, verify:

- Opening behaviour.
- Closing behaviour.
- Hover behaviour (desktop, if applicable).
- Touch interaction (mobile).
- Alignment.
- Overflow handling.

Dropdowns should remain usable across all supported devices.

---

# Active States

Navigation should clearly indicate the current page where required by the design.

Active state styling should remain consistent across the project.

---

# Responsive Behaviour

Navigation should adapt across:

- Desktop
- Laptop
- Tablet
- Mobile

Verify:

- Alignment
- Menu behaviour
- Spacing
- Touch usability
- Overflow
- Readability

Responsive navigation should preserve usability rather than simply shrinking desktop layouts.

---

# JavaScript Responsibilities

Shared navigation behaviour belongs in the shared JavaScript architecture.

Examples include:

- Menu toggle
- Mobile menu
- Dropdown interaction
- Scroll state

Page-specific navigation logic should be avoided.

---

# Accessibility

Navigation should:

- Use semantic `<nav>` elements.
- Provide meaningful link text.
- Preserve logical reading order.
- Maintain predictable interaction.

Accessibility should be considered throughout implementation.

---

# Validation Checklist

Before approving navigation verify:

## Structure

- [ ] Semantic navigation used.
- [ ] Shared navigation reused.
- [ ] Correct hierarchy maintained.

---

## Links

- [ ] Every link functions.
- [ ] Labels verified.
- [ ] Active states verified.

---

## Mobile

- [ ] Hamburger menu works.
- [ ] Menu opens.
- [ ] Menu closes.
- [ ] Touch interaction verified.

---

## Responsive

- [ ] Desktop verified.
- [ ] Laptop verified.
- [ ] Tablet verified.
- [ ] Mobile verified.

---

## Behaviour

- [ ] Dropdowns verified.
- [ ] Hover states verified.
- [ ] Navigation animations verified.

---

# Common Mistakes

Avoid:

- Duplicate navigation implementations.
- Broken links.
- Non-semantic navigation markup.
- Inconsistent responsive behaviour.
- Hamburger menus that fail after repeated interaction.
- Page-specific navigation logic.
- Navigation overflow on smaller screens.

---

# Best Practices

- Build navigation as a shared component.
- Validate navigation on every breakpoint.
- Keep interaction behaviour predictable.
- Reuse existing navigation architecture.
- Test every navigation path before delivery.

---

# Engineering Acceptance Criteria

A navigation implementation complies with this standard when:

- The shared navigation is reused.
- Desktop and mobile navigation match the approved design.
- Every link functions correctly.
- The hamburger menu operates correctly.
- Responsive behaviour is validated.
- Navigation remains semantic, accessible, and maintainable.

---

# Chapter Summary

Navigation is a shared architectural component that provides the primary user pathway throughout the website.

Following these standards ensures navigation remains consistent, responsive, reliable, and fully integrated with the project's shared frontend architecture.

---