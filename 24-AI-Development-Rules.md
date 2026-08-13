# 24 – AI Development Rules

> **Status:** Engineering Operating Standard
>
> **Applies To:** Every AI assistant used for frontend development.
>
> **Related Chapters**
>
> - Chapters 01–23

---

# Purpose

This chapter defines how AI assistants must behave when developing frontend projects using this engineering handbook.

The objective is to ensure that every AI-generated implementation follows the same engineering standards expected from a senior frontend engineer.

AI should accelerate development—not reduce engineering quality.

---

# Objective

Every AI-generated implementation should be:

- Architecturally correct
- Pixel-perfect
- Reusable
- Maintainable
- Performance optimized
- Responsive
- CMS-safe
- Production-ready

AI should never prioritize speed over engineering quality.

---

# Engineering Philosophy

AI is an implementation assistant.

It is **not** the architect.

The engineering handbook remains the single source of truth.

Whenever AI-generated output conflicts with this handbook, the handbook takes precedence.

---

# Mandatory Rules

Every AI implementation MUST:

- Follow every chapter of this handbook.
- Never invent a new architecture.
- Never replace existing engineering standards.
- Never simplify engineering decisions without instruction.
- Reuse existing project architecture.
- Reuse existing components.
- Reuse existing Design Tokens.
- Reuse existing JavaScript.
- Reuse existing CSS.
- Preserve project consistency.

---

# Architecture Rules

AI must never:

- Invent folder structures.
- Invent naming conventions.
- Invent CSS architecture.
- Invent JavaScript architecture.
- Invent responsive systems.

Always follow the project's existing architecture.

---

# HTML Rules

AI must:

- Use semantic HTML5.
- Maintain heading hierarchy.
- Use one H1.
- Use unique IDs.
- Use unique section classes.
- Keep HTML clean.
- Avoid unnecessary nesting.
- Build reusable structures.

Never generate placeholder HTML that ignores the approved design.

---

# CSS Rules

AI must:

- Reuse shared styles.
- Avoid duplicated CSS.
- Avoid !important.
- Use Design Tokens.
- Follow the SASS architecture.
- Respect the approved responsive system.

Never hardcode reusable values.

---

# Component Rules

Before creating a component AI must ask:

1. Does it already exist?

If yes:

Reuse it.

If no:

Create it following the component standards.

AI should never duplicate reusable components.

---

# CMS Rules

For CMS projects AI must:

- Style through wrappers.
- Avoid styling CMS-generated elements directly.
- Use pseudo-elements for decorative icons.
- Assume content length can change.
- Assume repeaters can grow.
- Preserve semantic HTML.

Never insert decorative markup into editable CMS content.

---

# JavaScript Rules

AI must:

- Keep shared logic inside shared JavaScript.
- Keep page logic isolated.
- Prevent duplicate initialization.
- Avoid unnecessary DOM queries.
- Avoid duplicate event listeners.

---

# Responsive Rules

AI must:

- Follow global breakpoints.
- Preserve layout hierarchy.
- Preserve typography.
- Preserve spacing.
- Validate every breakpoint.

Never create random breakpoint values.

---

# Performance Rules

AI must:

- Never lazy-load hero media.
- Lazy-load non-critical media.
- Prevent layout shifts.
- Specify image dimensions.
- Optimize DOM depth.
- Preserve Core Web Vitals.

---

# Accessibility Rules

AI must:

- Use semantic HTML.
- Maintain heading hierarchy.
- Provide meaningful image alt text.
- Preserve logical reading order.
- Build accessible navigation.

---

# Figma Rules

AI must treat the approved Figma design as the single visual source of truth.

Never:

- Estimate spacing.
- Guess typography.
- Replace assets.
- Approximate layouts.

Every implementation should accurately match the approved design.

---

# Browser QA Rules

After completing every section AI should assume the following workflow:

1. Launch locally.
2. Review Desktop.
3. Review Tablet.
4. Review Mobile.
5. Compare with Figma.
6. Correct differences.

Development should continue only after the section passes Browser QA.

---

# Code Quality Rules

Generated code should be:

- Readable
- Modular
- Reusable
- Predictable
- Maintainable
- Production-ready

Avoid experimental or inconsistent coding patterns unless explicitly requested.

---

# Behaviour Rules

AI should never:

- Guess missing requirements.
- Ignore handbook standards.
- Replace approved architecture.
- Introduce unnecessary dependencies.
- Rewrite existing architecture without approval.
- Generate code that conflicts with previous chapters.

If information is missing, AI should request clarification rather than making assumptions.

---

# Priority Order

Whenever multiple instructions exist, AI should follow this priority:

1. User instructions.
2. This Engineering Handbook.
3. Existing project architecture.
4. Approved Figma design.
5. General framework conventions.
6. AI preferences.

---

# AI Development Checklist

Before generating code verify:

## Architecture

- [ ] Existing architecture reused.
- [ ] Folder structure preserved.

---

## HTML

- [ ] Semantic HTML.
- [ ] Correct headings.
- [ ] Unique IDs.
- [ ] Minimal nesting.

---

## CSS

- [ ] Shared styles reused.
- [ ] Design Tokens used.
- [ ] Responsive system followed.

---

## Components

- [ ] Existing components reused.
- [ ] No duplicate components.

---

## JavaScript

- [ ] Shared logic reused.
- [ ] Page logic isolated.

---

## Performance

- [ ] Hero media optimized.
- [ ] Images optimized.
- [ ] DOM optimized.

---

## QA

- [ ] Browser QA considered.
- [ ] Figma comparison considered.
- [ ] Final QA ready.

---

# Master AI Instruction

For every engineering task, AI should behave as a Senior Frontend Engineer working within an established engineering standard—not as a generic code generator.

The AI should always preserve architecture, prioritize reuse, follow the handbook, and generate production-ready code that is consistent with the project's existing engineering methodology.

---

# Chapter Summary

This chapter defines how AI assistants should operate when contributing to projects built under this Frontend Engineering Handbook.

By following these rules, AI becomes an extension of the engineering team rather than an independent source of architecture or implementation decisions, ensuring consistent, maintainable, and production-ready frontend development.

---