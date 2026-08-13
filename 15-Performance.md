# 15 – Performance

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project developed using this handbook.
>
> **Related Chapters**
>
> - 03 Figma Standards
> - 06 HTML Standards
> - 07 CSS Standards
> - 08 SASS Architecture
> - 09 Responsive System
> - 13 JavaScript Standards

---

# Purpose

Performance is a mandatory engineering requirement.

A visually accurate implementation is not considered complete unless it also performs efficiently.

Performance should be considered during development rather than after implementation.

---

# Objective

Every implementation should provide:

- Fast loading
- Stable layouts
- Responsive interactions
- Efficient rendering
- Minimal unnecessary resources

Performance should be built into the engineering workflow from the beginning.

---

# Engineering Philosophy

Performance is part of frontend architecture.

Good performance is achieved through good engineering decisions rather than post-development optimization.

Every implementation should minimize unnecessary work performed by:

- The browser
- The network
- The rendering engine

---

# Mandatory Rules

Every project MUST:

- Lazy-load non-critical images.
- Lazy-load non-critical media.
- Never lazy-load above-the-fold hero media.
- Specify image width and height.
- Prevent layout shifts.
- Optimize DOM depth.
- Optimize LCP.
- Optimize CLS.
- Optimize INP.
- Target Lighthouse Performance scores of **90 or above**.

These rules are mandatory.

---

# Core Web Vitals

Performance optimization should prioritize the following metrics.

## Largest Contentful Paint (LCP)

Optimize the loading speed of the largest visible content element.

Typical examples include:

- Hero image
- Hero banner
- Primary heading
- Hero video poster

LCP should receive priority during implementation.

---

## Cumulative Layout Shift (CLS)

Prevent unexpected movement of page content.

Common causes include:

- Images without dimensions
- Media loading after layout
- Dynamic content insertion
- Unstable layouts

Layouts should remain visually stable during loading.

---

## Interaction to Next Paint (INP)

Interactive elements should respond promptly.

Examples include:

- Navigation
- Buttons
- Forms
- Menus
- Sliders

JavaScript should not introduce unnecessary delays that negatively affect user interaction.

---

# Image Optimization

Images should be optimized before deployment.

Guidelines:

- Use optimized image formats where appropriate.
- Preserve visual quality.
- Avoid unnecessarily large files.
- Specify intrinsic width and height.
- Serve images appropriate to the layout.

Images should balance quality with efficient loading.

---

# Lazy Loading

Lazy loading should be used for:

- Images below the fold
- Galleries
- Secondary media
- Deferred visual content

Lazy loading reduces unnecessary network activity during initial page load.

---

# Above-the-Fold Content

Hero content should load immediately.

Never lazy-load:

- Hero image
- Hero background media
- Primary hero illustration

Above-the-fold content contributes directly to the perceived loading experience and LCP.

---

# Layout Stability

Stable layouts improve both user experience and Core Web Vitals.

Developers should:

- Reserve space for media.
- Avoid unexpected layout changes.
- Maintain predictable component dimensions.

Layout stability should be verified during Browser QA.

---

# DOM Optimization

The document structure should remain efficient.

Avoid:

- Excessive nesting
- Unnecessary wrapper elements
- Duplicate structural markup

A simpler DOM improves rendering performance and maintainability.

---

# JavaScript Performance

JavaScript should initialize only the functionality required by the current page.

Shared scripts should:

- Avoid unnecessary execution.
- Prevent repeated initialization.
- Handle optional components safely.

Performance should be considered when organizing shared and page-specific JavaScript.

---

# CSS Performance

Styling architecture should support efficient rendering.

Developers should:

- Reuse shared styles.
- Avoid duplicated CSS.
- Keep page-specific styles isolated.
- Maintain the approved SASS architecture.

Efficient CSS contributes to maintainability and predictable rendering.

---

# Responsive Performance

Responsive implementations should remain performant across all supported breakpoints.

Responsive behaviour should not introduce:

- Layout instability
- Unnecessary resource loading
- Duplicate assets
- Excessive styling overrides

---

# Performance Validation Workflow

Performance should be reviewed throughout development.

Validation should include:

1. Resource loading.
2. Layout stability.
3. Image optimization.
4. JavaScript execution.
5. Responsive performance.
6. Browser QA.
7. Lighthouse review.

Performance validation is part of the implementation workflow rather than a final optimization task.

---

# Performance Checklist

Before approving a page verify:

## Images

- [ ] Non-critical images lazy-loaded.
- [ ] Hero media not lazy-loaded.
- [ ] Width specified.
- [ ] Height specified.
- [ ] Images optimized.

---

## Layout

- [ ] No layout shifts.
- [ ] Stable rendering.
- [ ] DOM depth reviewed.

---

## JavaScript

- [ ] Shared scripts reused.
- [ ] Page-specific initialization isolated.
- [ ] No unnecessary execution.

---

## CSS

- [ ] Shared styles reused.
- [ ] Duplicate styling avoided.
- [ ] Architecture respected.

---

## Core Web Vitals

- [ ] LCP reviewed.
- [ ] CLS reviewed.
- [ ] INP reviewed.

---

## Lighthouse

- [ ] Target performance score of 90+ achieved where practical.

---

# Common Mistakes

Avoid:

- Lazy-loading hero media.
- Images without dimensions.
- Excessive DOM nesting.
- Duplicate CSS.
- Duplicate JavaScript.
- Unnecessary page resources.
- Ignoring Core Web Vitals until the end of development.

---

# Best Practices

- Optimize performance during implementation.
- Prioritize Core Web Vitals.
- Reserve space for media.
- Reuse existing architecture.
- Validate Lighthouse regularly during development.
- Treat performance as a continuous engineering responsibility.

---

# Engineering Acceptance Criteria

A page complies with this performance standard when:

- Non-critical media is lazy-loaded.
- Above-the-fold media loads immediately.
- Layout shifts are prevented.
- Images define intrinsic dimensions.
- DOM structure remains efficient.
- LCP, CLS, and INP have been reviewed.
- The implementation targets a Lighthouse Performance score of **90 or above**.

---

# Chapter Summary

Performance is a core engineering requirement, not a post-development enhancement.

By following these standards, projects remain fast, stable, responsive, and maintainable while delivering a high-quality user experience and meeting the performance objectives defined in this engineering handbook.

---