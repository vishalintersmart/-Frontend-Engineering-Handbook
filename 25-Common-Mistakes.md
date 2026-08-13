# 25 – Common Mistakes

> **Status:** Engineering Reference Manual
>
> **Applies To:** Every frontend project developed using this handbook.
>
> **Related Chapters**
>
> - Chapters 01–24

---

# Purpose

This chapter consolidates the most common frontend engineering mistakes identified throughout this handbook.

Rather than repeating the same warnings in multiple chapters, this document provides a single reference that developers can consult before implementation, during development, and before delivery.

The objective is prevention rather than correction.

---

# Engineering Philosophy

Most engineering defects are repetitive.

Projects become more consistent when common mistakes are identified early and consciously avoided.

Every mistake listed in this chapter has been collected from the engineering standards defined throughout this handbook.

---

# 1. Project Architecture

Avoid:

- Creating custom folder structures without approval.
- Mixing shared and page-specific files.
- Placing assets in inconsistent locations.
- Ignoring the approved architecture.
- Bypassing the page wrapper.
- Creating duplicate modules.
- Creating duplicate layouts.
- Mixing responsibilities between architectural layers.

---

# 2. Figma Implementation

Avoid:

- Estimating spacing.
- Guessing font sizes.
- Guessing colors.
- Replacing icons.
- Replacing images.
- Changing alignment.
- Ignoring responsive designs.
- Using visual approximations.
- Assuming plugin defaults match the design.

---

# 3. HTML

Avoid:

- Multiple `<h1>` elements.
- Duplicate IDs.
- Missing section IDs.
- Missing section classes.
- Poor heading hierarchy.
- Non-semantic HTML.
- Excessive nesting.
- Empty heading tags.
- Missing image `alt` attributes.
- Decorative markup inside editable CMS content.

---

# 4. CSS

Avoid:

- Duplicate CSS.
- Inline styles.
- `!important`.
- Hardcoded reusable values.
- Inconsistent spacing.
- Inconsistent typography.
- Page-specific overrides for shared modules.
- Ignoring Design Tokens.

---

# 5. SASS

Avoid:

- Importing individual partials directly.
- Skipping directory index files.
- Changing layer order.
- Creating unnecessary folders.
- Mixing Modules with Pages.
- Global rules inside page partials.
- Duplicate partials.

---

# 6. Responsive

Avoid:

- Random breakpoints.
- Device-specific hacks.
- Multiple container systems.
- Arbitrary spacing changes.
- Inconsistent typography scaling.
- Horizontal scrolling.
- Component overflow.
- Ignoring tablet layouts.

---

# 7. Components

Avoid:

- Duplicate components.
- Component-specific architecture.
- Copy-paste components.
- Page-specific shared modules.
- Inconsistent button styles.
- Inconsistent form controls.
- Hardcoded content.
- Tight coupling between components.

---

# 8. CMS

Avoid:

- Styling CMS elements directly.
- Adding classes to Rich Text output.
- Decorative HTML inside editable fields.
- Assuming fixed content lengths.
- Assuming fixed image sizes.
- Ignoring empty states.
- Ignoring repeater growth.

---

# 9. JavaScript

Avoid:

- Duplicate event listeners.
- Duplicate initialization.
- Inline JavaScript.
- Page-specific logic inside shared scripts.
- Global selectors for page-only behaviour.
- Assuming DOM elements always exist.
- Ignoring console errors.

---

# 10. Accessibility

Avoid:

- Missing `alt` text.
- Broken heading hierarchy.
- Generic link labels.
- Non-semantic markup.
- Poor reading order.
- Unusable interactive elements.

---

# 11. Performance

Avoid:

- Lazy-loading hero images.
- Lazy-loading hero video.
- Missing image dimensions.
- Large layout shifts.
- Excessive DOM nesting.
- Duplicate CSS.
- Duplicate JavaScript.
- Oversized assets.
- Ignoring Core Web Vitals.

---

# 12. Header

Avoid:

- Incorrect positioning.
- Artificial spacing compensation.
- Incorrect hero overlap.
- Missing scroll behaviour.
- Inconsistent responsive behaviour.
- Page-specific header implementations.

---

# 13. Navigation

Avoid:

- Broken links.
- Broken hamburger menu.
- Incorrect dropdown behaviour.
- Navigation overflow.
- Duplicate navigation implementations.
- Missing active states.

---

# 14. Sliders

Avoid:

- Default autoplay timing.
- Incorrect loop configuration.
- Broken touch drag.
- Missing pagination.
- Incorrect navigation buttons.
- Duplicate initialization.
- Untested responsive behaviour.

---

# 15. Browser QA

Avoid:

- Skipping local testing.
- Skipping screenshots.
- Ignoring console warnings.
- Presenting work before Browser QA.
- Delaying responsive testing.

---

# 16. Figma Validation

Avoid:

- Comparing only the homepage.
- Estimating measurements.
- Ignoring typography.
- Ignoring spacing.
- Ignoring hover states.
- Ignoring animations.

---

# 17. Final QA

Avoid:

- Delivering with known defects.
- Skipping Final QA.
- Ignoring Browser QA.
- Ignoring Figma Validation.
- Delivering with console errors.
- Delivering without responsive verification.

---

# 18. Delivery

Avoid:

- Delivering unfinished work.
- Delivering without approval.
- Delivering before performance review.
- Delivering with broken interactions.

---

# 19. AI Usage

Avoid:

- Allowing AI to invent architecture.
- Accepting AI output without review.
- Letting AI duplicate components.
- Letting AI ignore Design Tokens.
- Letting AI ignore CMS rules.
- Letting AI replace handbook standards.

---

# Universal Engineering Mistakes

The following mistakes should never occur in any project:

- Duplicate code.
- Duplicate components.
- Duplicate architecture.
- Hardcoded reusable values.
- Broken responsive layouts.
- Broken navigation.
- Missing image `alt` text.
- Multiple `<h1>` elements.
- Duplicate IDs.
- Inline CSS.
- Inline JavaScript.
- `!important`.
- Missing Browser QA.
- Missing Figma Validation.
- Missing Final QA.
- Visual approximations.
- Unresolved console errors.
- Unoptimized media.
- Poor DOM structure.
- Ignoring the handbook.

---

# Engineering Self-Review

Before considering a task complete, ask:

1. Did I reuse the existing architecture?
2. Did I duplicate anything?
3. Does this match Figma exactly?
4. Is it responsive?
5. Is it CMS-safe?
6. Is it accessible?
7. Is it performant?
8. Is the console clean?
9. Has Browser QA been completed?
10. Is this ready for Final QA?

If the answer to any question is **No**, the implementation is not complete.

---

# Chapter Summary

This chapter serves as the handbook's master engineering reference for recurring implementation mistakes.

By reviewing these mistakes before and during development, engineers can prevent the majority of frontend defects before they reach Browser QA, Final QA, or client review.

Avoiding these mistakes consistently is one of the simplest ways to improve engineering quality, maintainability, and delivery confidence.

---