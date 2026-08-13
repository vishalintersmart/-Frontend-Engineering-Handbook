# 20 – Figma Validation

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every completed page, section, reusable component, and responsive layout.
>
> **Related Chapters**
>
> - 03 Figma Standards
> - 19 Browser QA
> - 21 Final QA

---

# Purpose

Figma Validation ensures that the implemented frontend accurately reproduces the approved Figma design.

It is a dedicated visual verification process focused on design fidelity rather than functionality.

Every completed implementation must pass Figma Validation before progressing to Final QA.

---

# Objective

Figma Validation confirms that the browser implementation matches the approved design without introducing visual approximations.

The objective is to preserve:

- Design intent
- Visual hierarchy
- Consistency
- User experience

---

# Engineering Philosophy

The approved Figma design is the single source of truth for visual implementation.

Developers should not make personal design decisions during implementation.

If uncertainty exists, return to the approved Figma design rather than estimating.

---

# Mandatory Rules

Every implementation MUST:

- Match the approved Figma design.
- Preserve layout proportions.
- Preserve typography.
- Preserve spacing.
- Preserve colors.
- Preserve imagery.
- Preserve interaction behaviour.
- Avoid visual approximations.

These rules are mandatory.

---

# Validation Workflow

Every completed page should follow this sequence.

## Step 1

Open the approved Figma design.

Confirm:

- Correct version
- Correct page
- Correct breakpoint
- Correct component state

---

## Step 2

Open the implemented page in the browser.

Use the matching viewport for comparison.

---

## Step 3

Compare the implementation against Figma section by section.

Do not compare only the overall appearance.

Every section should be reviewed individually.

---

## Step 4

Identify every visual difference.

Examples include:

- Incorrect spacing
- Incorrect typography
- Incorrect colors
- Missing icons
- Incorrect alignment

---

## Step 5

Correct every difference.

Repeat validation until the implementation matches the approved design.

---

# Figma Matching Checklist

Every implementation should verify the following.

## Layout

- [ ] Section order
- [ ] Grid structure
- [ ] Container width verified
- [ ] Content alignment
- [ ] White space

---

## Typography

- [ ] Font family
- [ ] Font weight
- [ ] Font size
- [ ] Line height
- [ ] Letter spacing
- [ ] Text alignment

---

## Colors

- [ ] Background colors
- [ ] Text colors
- [ ] Border colors
- [ ] Gradient colors

---

## Components

- [ ] Buttons
- [ ] Forms
- [ ] Cards
- [ ] Navigation
- [ ] Footer
- [ ] Hero section

---

## Visual Styling

- [ ] Border radius
- [ ] Borders
- [ ] Shadows
- [ ] Blur effects
- [ ] Glass effects

---

## Assets

- [ ] Images
- [ ] Icons
- [ ] SVG graphics
- [ ] Logos
- [ ] Illustrations

---

## Interactions

- [ ] Hover states
- [ ] Active states
- [ ] Animations
- [ ] Transitions
- [ ] Cursor effects

---

# Responsive Validation

Repeat Figma Validation for every supported breakpoint.

Validate:

- Desktop
- Large Laptop
- Laptop
- Tablet Landscape
- Tablet Portrait
- Large Mobile
- Mobile

Every breakpoint should preserve the approved design intent.

---

# Visual Accuracy

The implementation should preserve:

- Relative proportions
- Reading hierarchy
- Visual balance
- Alignment
- Component consistency

No intentional visual changes should be introduced without approval.

---

# Acceptance Rule

The implementation should not be described as:

- Close enough
- Similar
- Approximately correct

The objective is an accurate implementation of the approved design.

---

# Validation Checklist

Before approving a page verify:

## Layout

- [ ] Section order matches.
- [ ] Containers match.
- [ ] Alignment matches.

---

## Typography

- [ ] Fonts match.
- [ ] Sizes match.
- [ ] Weights match.
- [ ] Hierarchy preserved.

---

## Styling

- [ ] Colors verified.
- [ ] Border radius verified.
- [ ] Shadows verified.
- [ ] Spacing verified.

---

## Assets

- [ ] Images verified.
- [ ] Icons verified.
- [ ] Logos verified.

---

## Interaction

- [ ] Hover states verified.
- [ ] Animations verified.
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

- Estimating spacing.
- Guessing typography.
- Replacing approved assets.
- Ignoring responsive differences.
- Assuming plugin defaults match the design.
- Presenting work before completing Figma comparison.

---

# Best Practices

- Keep Figma open during implementation.
- Compare section by section.
- Validate after every completed section.
- Measure rather than estimate.
- Repeat validation after significant changes.

---

# Engineering Acceptance Criteria

A page complies with this standard when:

- It accurately matches the approved Figma design.
- Visual hierarchy is preserved.
- Every checklist item has been verified.
- Responsive implementations remain faithful to the design.
- No visual approximations remain.

---

# Chapter Summary

Figma Validation is the project's visual quality gate.

It ensures that every implementation faithfully reproduces the approved design and prevents subjective interpretation during development.

Combined with Browser QA and Final QA, it forms the complete engineering verification workflow defined by this handbook.

---