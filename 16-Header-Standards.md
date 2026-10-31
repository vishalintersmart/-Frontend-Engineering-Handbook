# 16 – Header Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every project header and global navigation container.
>
> **Related Chapters**
>
> - 03 Figma Standards
> - 04 Project Architecture
> - 06 HTML Standards
> - 08 SASS Architecture
> - 17 Navigation
> - 19 Browser QA

---

# Purpose

The header is a shared structural component that provides branding, navigation, and global user access throughout the website.

Every page should use a consistent header implementation that matches the approved design and integrates with the shared project architecture.

---

# Objective

The header should:

- Match the approved Figma design.
- Behave consistently across pages.
- Adapt correctly across responsive breakpoints.
- Remain reusable.
- Integrate with shared navigation.
- Preserve layout stability.

---

# Engineering Philosophy

The header is part of the shared application layout.

It should be implemented once and reused throughout the project.

Page-specific layouts should adapt to the shared header rather than replacing or duplicating it.

---

# Mandatory Rules

Every header implementation MUST:

- Match the approved Figma design.
- Reuse the shared header component.
- Preserve the approved positioning behaviour.
- Preserve responsive behaviour.
- Maintain consistent navigation structure.
- Avoid page-specific header duplication.
- Be validated at every supported breakpoint.

These rules are mandatory.

---

# Header Positioning

Before implementation, determine the header behaviour defined in the approved design.

Possible behaviours include:

- Fixed
- Sticky
- Absolute
- Transparent

The implementation must match the approved behaviour.

Do not substitute one positioning method for another.

---

# Hero Relationship

The relationship between the header and the hero section must match the design.

Examples include:

- Header overlays hero
- Header sits above hero
- Transparent header over hero
- Solid header before hero

Never compensate for positioning differences by introducing arbitrary spacing.

---

# Scroll Behaviour

If the approved design defines scroll behaviour, it must be implemented consistently.

Examples include:

- Header remains visible.
- Header becomes fixed.
- Background changes.
- Blur activates.
- Shadow appears.
- Size changes.

Behaviour should match the design rather than relying on default patterns.

---

# Visual Effects

Verify all visual effects defined for the header.

Typical effects include:

- Blur
- Glass effect
- Background transition
- Shadow
- Opacity transition

Effects should remain consistent across all pages.

---

# Sticky Header Animation (Required)

Every project header gets a sticky scroll animation in addition to the approved positioning: once the user scrolls past the top of the page the header stays pinned, slides in, and gains a solid background and shadow. If the approved design defines a different scroll behaviour, the design wins and this section is adapted to it.

## Rules

- Toggle one class, `is-stuck`, on the shared `<header>`. Use an `IntersectionObserver` on a 1px sentinel - no `scroll` listener.
- Animate only `transform`, `opacity`, `background-color` and `box-shadow`. Never animate `height`, `padding` or `top` (causes CLS and janky INP).
- Header stays `position: sticky; top: 0` (or the design's `fixed` with reserved space) so it never shifts content.
- Respect `prefers-reduced-motion: reduce` (no slide, colour change only).
- The logic lives once in the shared `assets/js/app.js`; no per-page copies.

## Markup

```html
<span class="header-sentinel" aria-hidden="true"></span>
<header class="header" id="siteHeader">...</header>
```

## CSS

```css
.header-sentinel {
    position: absolute;
    top: 0;
    left: 0;
    width: 1px;
    height: 1px;
    pointer-events: none;
}

.header {
    position: sticky;
    top: 0;
    z-index: 100;
    background-color: transparent;
    transition: background-color 0.3s ease, box-shadow 0.3s ease;
}

.header.is-stuck {
    background-color: #fff;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
    animation: header-slide-in 0.35s ease both;
}

@keyframes header-slide-in {
    from {
        transform: translateY(-100%);
    }
    to {
        transform: translateY(0);
    }
}

@media (prefers-reduced-motion: reduce) {
    .header,
    .header.is-stuck {
        animation: none;
        transition: none;
    }
}
```

## JavaScript

```javascript
function initStickyHeader() {
    const header = document.getElementById('siteHeader');
    const sentinel = document.querySelector('.header-sentinel');
    if (!header || !sentinel || !('IntersectionObserver' in window)) return;

    new IntersectionObserver(([entry]) => {
        header.classList.toggle('is-stuck', !entry.isIntersecting);
    }).observe(sentinel);
}
```

Call `initStickyHeader()` from the boot `init()` in `app.js`.

## Verification

- Scrolling past the top pins the header with the slide-in; scrolling back to the top removes `is-stuck`.
- No layout shift (CLS 0) when the class toggles.
- Works with the mobile menu open and at every breakpoint.

---

# Layout Integration

The header should integrate naturally with the project layout.

It should not require:

- Artificial top margins.
- Hardcoded spacing compensation.
- Page-specific positioning hacks.

The shared layout should account for the header correctly.

---

# Responsive Behaviour

The header should adapt consistently across:

- Desktop
- Laptop
- Tablet
- Mobile

Verify:

- Alignment
- Logo placement
- Navigation behaviour
- Spacing
- Header height
- Scroll behaviour

Responsive adaptations should preserve usability and design intent.

---

# Shared Architecture

The header belongs to the shared architecture.

It should remain inside the project's shared layout rather than being recreated for individual pages.

Shared modifications should affect every page consistently.

---

# Validation Checklist

Before approving a header verify:

## Structure

- [ ] Shared header reused.
- [ ] Semantic HTML maintained.
- [ ] Navigation integrated.

---

## Behaviour

- [ ] Correct positioning used.
- [ ] Scroll behaviour verified.
- [ ] Hero relationship verified.
- [ ] Sticky header animation (`is-stuck`) verified.

---

## Visual Design

- [ ] Blur verified.
- [ ] Glass effect verified.
- [ ] Shadows verified.
- [ ] Transitions verified.

---

## Responsive

- [ ] Desktop verified.
- [ ] Laptop verified.
- [ ] Tablet verified.
- [ ] Mobile verified.

---

# Common Mistakes

Avoid:

- Duplicating the header.
- Mixing page-specific logic into the shared header.
- Artificial spacing to compensate for positioning.
- Changing positioning behaviour without design approval.
- Inconsistent responsive behaviour.
- Breaking navigation during responsive adaptation.

---

# Best Practices

- Build the header as a shared component.
- Validate positioning before implementation.
- Test scroll behaviour early.
- Keep the header independent of page content.
- Review the header on every supported breakpoint.

---

# Engineering Acceptance Criteria

A header implementation complies with this standard when:

- The shared header is reused.
- Positioning matches the approved design.
- Hero integration is correct.
- Scroll behaviour matches the design.
- Responsive behaviour is consistent.
- Visual effects are accurately implemented.
- No layout compensation hacks are required.

---

# Chapter Summary

The header is a shared architectural component that defines the entry point to every page.

Correct implementation requires consistent positioning, responsive behaviour, shared architecture, and faithful reproduction of the approved design.

Following these standards ensures that the header remains reusable, maintainable, and visually consistent throughout the project.

---