# 13 – JavaScript Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every JavaScript file used within the project.
>
> **Related Chapters**
>
> - 04 Project Architecture
> - 05 PHP Architecture
> - 06 HTML Standards
> - 08 SASS Architecture
> - 11 Components

---

# Purpose

This chapter defines the engineering standards for organizing and implementing JavaScript throughout the project.

The objective is to create a predictable, maintainable, and reusable JavaScript architecture that integrates cleanly with the project's HTML, SASS, and component systems.

JavaScript should enhance behaviour—not define document structure or visual presentation.

---

# Objective

JavaScript should remain:

- Modular
- Maintainable
- Reusable
- Predictable
- Page-independent where possible

Every script should have a clearly defined responsibility.

---

# Engineering Philosophy

JavaScript should extend the frontend architecture rather than compete with it.

The project architecture already separates:

- HTML → Structure
- CSS/SASS → Presentation
- JavaScript → Behaviour

Each layer should remain independent while working together.

---

# Mandatory Rules

Every JavaScript implementation MUST:

- Reuse existing project JavaScript before creating new functionality.
- Keep shared logic inside `assets/js/app.js`.
- Keep page-specific logic scoped to the current page.
- Avoid duplicate event listeners.
- Avoid duplicate business logic.
- Keep JavaScript independent of page-specific markup whenever possible.
- Follow the existing project architecture.

These rules are mandatory.

---

# JavaScript Responsibilities

JavaScript is responsible for behaviour.

Typical responsibilities include:

- User interaction
- Navigation behaviour
- Slider initialization
- Form interaction
- Modal behaviour
- Tabs
- Accordions
- Animation triggers
- AJAX requests (when applicable)

JavaScript should not replace proper HTML or CSS.

---

# Shared JavaScript

## Purpose

Shared JavaScript contains behaviour reused across multiple pages.

Typical examples include:

- Navigation
- Mobile menu
- Header behaviour
- Shared sliders
- Utility functions
- Scroll interactions
- Global event handlers

Shared functionality belongs inside:

```text
assets/js/app.js
```

---

# Page-Specific JavaScript

## Purpose

Page-specific JavaScript supports functionality unique to a single page.

Examples include:

- Landing page animations
- Campaign-specific interactions
- One-off calculators
- Page-only sliders

Page-specific logic should remain scoped to that page and should not be moved into shared scripts unless reused elsewhere.

---

# Scope Through pageWrapper

Page-specific JavaScript should target the page wrapper rather than relying on global selectors.

Example:

```javascript
const page = document.getElementById('pageWrapper');

if (page && page.classList.contains('contactPage')) {
    // Contact page logic
}
```

This prevents unnecessary execution on unrelated pages.

---

# Event Listeners

Attach event listeners responsibly.

Avoid:

- Duplicate listeners
- Nested listeners
- Repeated initialization

Where appropriate:

- Initialize once
- Reuse handlers
- Remove listeners when no longer needed

---

# DOM Queries

Prefer reusable, predictable selectors.

Avoid relying on fragile DOM structures.

JavaScript should target stable elements such as:

- IDs
- Component wrappers
- Page wrapper
- Shared component classes

Avoid selectors that depend on element position alone.

---

# Component Behaviour

Reusable components should encapsulate reusable behaviour.

Examples:

- Accordions
- Tabs
- Dropdowns
- Sliders
- Modals

If multiple pages require identical interaction, the behaviour belongs in shared JavaScript.

---

# Progressive Enhancement

Pages should remain usable even when JavaScript is unavailable wherever practical.

JavaScript should enhance functionality rather than being the only means of presenting core content.

---

# Performance Considerations

JavaScript should:

- Minimize unnecessary DOM queries.
- Avoid repeated calculations.
- Reuse cached selectors where appropriate.
- Initialize only required functionality.
- Avoid blocking page rendering.

Performance optimization should support the broader performance standards defined in this handbook.

---

# Error Handling

Before interacting with the DOM:

- Verify required elements exist.
- Handle optional components gracefully.
- Avoid runtime errors caused by missing elements.

Shared JavaScript should never fail because a page does not contain a particular component.

---

# Validation Checklist

Before approving JavaScript verify:

## Architecture

- [ ] Shared functionality located in `assets/js/app.js`.
- [ ] Page-specific logic isolated.
- [ ] No duplicate functionality.

---

## Behaviour

- [ ] Event listeners initialized correctly.
- [ ] Shared components behave consistently.
- [ ] Page wrapper scoping used where appropriate.

---

## Performance

- [ ] No unnecessary DOM queries.
- [ ] No repeated initialization.
- [ ] Only required scripts executed.

---

## Stability

- [ ] Missing elements handled safely.
- [ ] No console errors.
- [ ] No JavaScript conflicts.

---

# Common Mistakes

Avoid:

- Duplicating shared behaviour.
- Inline JavaScript.
- Page-specific logic inside shared scripts.
- Global selectors for page-only functionality.
- Duplicate event listeners.
- Assuming elements always exist.
- Initializing every component on every page.

---

# Best Practices

- Reuse before creating.
- Scope page-specific logic through the page wrapper.
- Keep shared behaviour centralized.
- Validate DOM elements before use.
- Organize code by responsibility.
- Review existing JavaScript before introducing new functionality.

---

# Engineering Acceptance Criteria

A JavaScript implementation complies with this standard when:

- Shared behaviour remains centralized.
- Page-specific behaviour remains isolated.
- No duplicate logic exists.
- Components initialize predictably.
- Runtime errors are prevented through defensive checks.
- JavaScript integrates cleanly with the project architecture.

---

# Chapter Summary

JavaScript is responsible for behaviour within the frontend architecture.

Following these standards ensures that scripts remain modular, reusable, maintainable, and consistent across the project while respecting the separation of responsibilities established by the project's HTML, SASS, and component architecture.

---