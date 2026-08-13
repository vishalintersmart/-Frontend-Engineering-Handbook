# 14 – Accessibility

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend page, component, layout, and CMS-generated content.
>
> **Related Chapters**
>
> - 03 Figma Standards
> - 06 HTML Standards
> - 11 Components
> - 12 CMS Development
> - 15 Performance

---

# Purpose

Accessibility is an essential part of frontend engineering.

The purpose of this chapter is to ensure that every implementation remains understandable, operable, and readable through proper semantic structure and consistent engineering practices.

Accessibility is not treated as a separate phase.

It is integrated throughout the development workflow.

---

# Objective

Every implementation should provide:

- Clear document structure
- Readable content
- Meaningful navigation
- Predictable interactions
- Semantic markup

Accessibility should be considered during implementation rather than after development is complete.

---

# Engineering Philosophy

Accessibility begins with correct HTML.

Well-structured semantic markup naturally improves:

- Readability
- Screen reader compatibility
- Search engine understanding
- Long-term maintainability

Accessibility should originate from good engineering rather than post-development fixes.

---

# Mandatory Rules

Every implementation MUST:

- Use semantic HTML5.
- Maintain proper heading hierarchy.
- Include one `<h1>` per page.
- Provide meaningful image `alt` text.
- Preserve logical reading order.
- Ensure buttons remain usable.
- Ensure links remain functional.
- Maintain readable typography.
- Validate accessibility during QA.

These rules are mandatory.

---

# Semantic HTML

Semantic HTML forms the foundation of accessibility.

Use appropriate landmark elements including:

- `<header>`
- `<nav>`
- `<main>`
- `<section>`
- `<article>`
- `<footer>`

Avoid replacing semantic elements with generic containers without valid reason.

---

# Heading Structure

Headings communicate document hierarchy.

Requirements:

- One `<h1>` per page.
- Logical progression through heading levels.
- No skipped levels without structural justification.

A clear heading structure improves navigation for both users and assistive technologies.

---

# Images

Every informative image must include meaningful alternative text.

Good alternative text describes the purpose of the image rather than simply stating that an image exists.

Decorative images should be treated appropriately according to the project's accessibility approach.

---

# Links

Links should clearly communicate their purpose.

Avoid vague link labels such as:

- Click Here
- Read More
- Learn More

when the surrounding context does not sufficiently describe the destination.

Where appropriate, link text should remain meaningful on its own.

---

# Buttons

Buttons should clearly communicate the action they perform.

Shared button components should maintain consistent:

- Labels
- Behaviour
- Visual states

Buttons should remain recognizable throughout the project.

---

# Forms

Forms should preserve a consistent structure.

Verify:

- Labels
- Required indicators
- Error presentation
- Field grouping

Shared form components should maintain predictable interaction patterns.

---

# Reading Order

The HTML structure should follow the natural reading order of the page.

Content should remain understandable without relying on CSS positioning.

The visual order and document order should not conflict.

---

# Readability

Readable content depends on:

- Appropriate typography
- Consistent spacing
- Logical hierarchy
- Sufficient visual separation

Responsive scaling should preserve readability across all supported devices.

---

# Interactive Elements

Interactive components should behave predictably.

Examples include:

- Navigation
- Buttons
- Accordions
- Tabs
- Sliders
- Forms

Every interactive element should remain usable after responsive adaptation.

---

# CMS Content

CMS-generated content should preserve:

- Semantic headings
- Paragraph structure
- Lists
- Links

Wrapper-based styling should not compromise document semantics.

---

# Accessibility Validation Workflow

Accessibility should be reviewed during implementation and again during quality assurance.

Validation should include:

1. Document structure.
2. Heading hierarchy.
3. Images.
4. Links.
5. Buttons.
6. Forms.
7. Responsive readability.
8. Interactive behaviour.

Accessibility validation is part of the engineering workflow rather than an independent task.

---

# Accessibility Checklist

Before completing a page verify:

## Document

- [ ] Semantic HTML used.
- [ ] One `<h1>` present.
- [ ] Heading hierarchy correct.
- [ ] Logical reading order preserved.

---

## Images

- [ ] Meaningful `alt` text provided.
- [ ] Decorative images handled appropriately.

---

## Navigation

- [ ] Navigation structure preserved.
- [ ] Links remain functional.
- [ ] Link text is meaningful.

---

## Components

- [ ] Buttons remain usable.
- [ ] Forms remain consistent.
- [ ] Interactive elements function correctly.

---

## Responsive

- [ ] Typography remains readable.
- [ ] Layout remains understandable.
- [ ] Interactive elements remain usable.

---

# Common Mistakes

Avoid:

- Multiple `<h1>` elements.
- Missing image `alt` text.
- Generic link labels without context.
- Broken heading hierarchy.
- Using non-semantic markup where semantic elements exist.
- Breaking reading order through implementation.

---

# Best Practices

- Build accessibility into the initial implementation.
- Use semantic HTML by default.
- Review accessibility throughout development.
- Preserve logical document structure.
- Keep interactive behaviour consistent.
- Validate accessibility during Browser QA and Final QA.

---

# Engineering Acceptance Criteria

A page complies with this accessibility standard when:

- Semantic HTML is used appropriately.
- Document hierarchy is logical.
- Images include meaningful alternative text.
- Heading hierarchy is correct.
- Navigation remains understandable.
- Interactive elements function predictably.
- Responsive layouts preserve readability.

---

# Chapter Summary

Accessibility is a natural outcome of good frontend engineering.

By following the standards defined throughout this handbook—semantic HTML, consistent components, logical structure, meaningful content, and responsive readability—projects become more accessible while remaining maintainable and consistent.

Accessibility should be considered a continuous engineering responsibility rather than a final compliance task.

---