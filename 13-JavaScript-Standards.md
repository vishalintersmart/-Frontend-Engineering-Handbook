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

# Smooth Wheel Scrolling (Required)

## Purpose

Every HTML / PHP build ships eased mouse-wheel scrolling as part of the shared behaviour in `assets/js/app.js`. It is a trimmed rewrite of SmoothScroll.js (≈80 lines instead of ≈440, no dependency): each wheel notch eases over 400ms with a "pulse" ease-out and acceleration on fast repeated notches.

It deliberately stays **native** for trackpads, touch devices, Firefox (no `wheelDeltaY`; already smooth), `ctrl` + wheel zoom and `prefers-reduced-motion: reduce`. Keyboard scrolling is **not** intercepted — browsers already scroll arrow / Page / Space keys smoothly, and hijacking them hurts keyboard users.

## Rules

- Add `initSmoothScroll()` to `app.js` and call it from the boot `init()`.
- Do not add a smooth-scroll library (Lenis, Locomotive, SmoothScroll.js) on top of it.
- Keep `scroll-behavior: smooth` on `html` (for anchor links) — the script scrolls with `behavior: 'instant'` so the two never fight.
- A page locked with `overflow: hidden` on `html` or `body` (mobile menu, lightbox) is never scrolled by it.
- Nested scroll areas (`overflow-y: auto | scroll` with overflowing content) are eased on their own; the page stays put.
- Not for Next.js / React projects (Chapter 29) unless the project asks for it.

## Implementation

Drop-in, self-contained (inside the `app.js` IIFE; reuse the file's existing `reduceMotion` / `root` constants if they already exist):

```javascript
/* ------------------------------------------------------------ Smooth wheel scrolling
   Trimmed from SmoothScroll.js: each mouse-wheel notch eases over 400ms with acceleration.
   Trackpads, touch, Firefox (no wheelDeltaY; already smooth), ctrl+zoom and reduced motion stay native. */
function initSmoothScroll() {
    const root = document.documentElement;
    const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    if (reduceMotion || !window.matchMedia('(hover: hover) and (pointer: fine)').matches) return;

    const DURATION = 400;
    const STEP = 100;
    const ACCEL_WINDOW = 50;
    const ACCEL_MAX = 3;

    // "pulse" ease-out, normalised so pulse(1) === 1
    const rawPulse = (x) => {
        x *= 4;
        return x < 1 ? x - (1 - Math.exp(-x)) : Math.exp(-1) + (1 - Math.exp(1 - x)) * (1 - Math.exp(-1));
    };
    const pulseOne = rawPulse(1);
    const pulse = (x) => rawPulse(x) / pulseOne;

    let queue = [];
    let target = null;
    let running = false;
    let direction = 0;
    let lastWheel = 0;

    const isLocked = (el) => getComputedStyle(el).overflowY === 'hidden';

    // nearest element that can scroll vertically; null when the page is locked (menu, lightbox)
    const scrollTarget = (el) => {
        for (; el && el !== document.body && el !== root; el = el.parentElement) {
            const overflow = getComputedStyle(el).overflowY;
            if ((overflow === 'auto' || overflow === 'scroll') && el.scrollHeight > el.clientHeight + 10) return el;
        }
        return isLocked(root) || isLocked(document.body) ? null : document.scrollingElement;
    };

    const step = () => {
        const now = performance.now();
        let delta = 0;
        queue = queue.filter((item) => {
            const progress = Math.min((now - item.start) / DURATION, 1);
            const move = Math.round(item.y * pulse(progress)) - item.applied;
            item.applied += move;
            delta += move;
            return progress < 1;
        });

        // 'instant' bypasses the CSS scroll-behavior: smooth on <html>
        if (target === document.scrollingElement) window.scrollBy({ top: delta, behavior: 'instant' });
        else target.scrollTop += delta;

        if (queue.length) requestAnimationFrame(step);
        else running = false;
    };

    window.addEventListener('wheel', (event) => {
        // notch detection via wheelDeltaY % 120 — a trackpad flick that lands on a multiple of 120 gets eased too
        const notch = event.wheelDeltaY && event.wheelDeltaY % 120 === 0;
        if (event.defaultPrevented || event.ctrlKey || !notch || Math.abs(event.deltaX) > Math.abs(event.deltaY)) return;

        const el = scrollTarget(event.target);
        if (!el) return;

        const now = performance.now();
        let y = -event.wheelDeltaY * STEP / 120;
        if (Math.sign(y) !== direction || el !== target) {
            direction = Math.sign(y);
            target = el;
            queue = [];
        } else if (now - lastWheel < ACCEL_WINDOW) {
            y *= Math.min((1 + ACCEL_WINDOW / (now - lastWheel || 1)) / 2, ACCEL_MAX);
        }
        lastWheel = now;

        queue.push({ y, applied: 0, start: now });
        event.preventDefault();
        if (!running) {
            running = true;
            requestAnimationFrame(step);
        }
    }, { passive: false });
}
```

## Verification

Test with **real** wheel input (Playwright `page.mouse.wheel(0, 100)`; a synthetic `new WheelEvent()` has no `wheelDeltaY` and is ignored):

- One notch moves the page ~100px, eased over ~400ms (sample `scrollY` each frame).
- A scrollable inner box scrolls while the page does not move.
- With the mobile menu / lightbox open the page does not move.
- Reduced motion, touch emulation and Firefox scroll natively.
- No console errors.

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
- [ ] Smooth wheel scrolling (`initSmoothScroll()`) included and verified (HTML / PHP builds).

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