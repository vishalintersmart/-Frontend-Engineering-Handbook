# 19 – Browser QA

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every completed section, page, component, and layout before presentation or delivery.
>
> **Related Chapters**
>
> - 03 Figma Standards
> - 14 Accessibility
> - 15 Performance
> - 16 Header Standards
> - 17 Navigation
> - 18 Slider Standards
> - 20 Figma Validation
> - 21 Final QA

---

# Purpose

Browser QA is the continuous engineering validation process performed throughout development.

It is not reserved for the end of the project.

Every completed section should pass Browser QA before development proceeds.

---

# Objective

Browser QA ensures that completed work is:

- Functionally correct
- Visually accurate
- Responsive
- Stable
- Ready for review

Defects should be corrected immediately rather than accumulating until the end of the project.

---

# Engineering Philosophy

Quality assurance is part of implementation.

A section is not considered complete until it has passed Browser QA.

Developers should verify their own work before requesting design review or client feedback.

---

# Mandatory Rules

Every completed section MUST undergo Browser QA before being presented.

Every Browser QA cycle MUST include:

- Local launch
- Responsive validation
- Screenshot comparison
- Functional verification
- Visual verification
- Defect correction

These rules are mandatory.

---

# Browser QA Workflow

Every completed section should follow this sequence.

## Step 1

Launch the project locally.

Verify:

- Page loads correctly.
- Resources load correctly.
- No missing assets.
- No obvious rendering issues.

---

## Step 2

Capture a Desktop screenshot.

Verify:

- Layout
- Typography
- Images
- Icons
- Alignment
- Section spacing

---

## Step 3

Capture a Tablet screenshot.

Verify:

- Responsive layout
- Navigation
- Typography scaling
- Spacing
- Images

---

## Step 4

Capture a Mobile screenshot.

Verify:

- Mobile layout
- Hamburger menu
- Forms
- Buttons
- Touch interactions

---

## Step 5

Compare every screenshot against the approved Figma design.

Verify:

- Section order
- Typography
- Colors
- Spacing
- Icons
- Images
- Components
- Animations

No visual approximations are permitted.

---

## Step 6

Correct every identified difference.

Repeat Browser QA until no significant differences remain.

Only then should the section be considered complete.

---

# Functional Verification

Verify:

- Links
- Buttons
- Forms
- Navigation
- Sliders
- Accordions
- Tabs
- Interactive components

Every interactive element should function correctly.

---

# Responsive Verification

Validate:

- Desktop
- Large Laptop
- Laptop
- Tablet Landscape
- Tablet Portrait
- Large Mobile
- Mobile

Verify:

- Layout
- Typography
- Images
- Navigation
- Components
- Container width verified

---

# Visual Verification

Confirm:

- Alignment
- White space
- Container widths
- Colors
- Typography
- Borders
- Shadows
- Border radius
- Images
- Icons

The browser implementation should accurately reproduce the approved design.

---

# Console Verification

Verify:

- No JavaScript errors.
- No failed resource requests.
- No unnecessary warnings introduced by the implementation.

A clean browser console is part of successful Browser QA.

---

# Performance Spot Check

During Browser QA verify:

- Hero media loads correctly.
- Images display correctly.
- No unexpected layout shifts.
- Initial rendering remains stable.

Detailed performance validation is covered in Chapter 15.

---

# Browser QA Checklist

Before approving a completed section verify:

## Visual

- [ ] Layout verified.
- [ ] Typography verified.
- [ ] Colors verified.
- [ ] Spacing verified.
- [ ] Images verified.
- [ ] Icons verified.

---

## Functional

- [ ] Links work.
- [ ] Buttons work.
- [ ] Navigation works.
- [ ] Forms work.
- [ ] Sliders work.

---

## Responsive

- [ ] Desktop verified.
- [ ] Laptop verified.
- [ ] Tablet verified.
- [ ] Mobile verified.

---

## Technical

- [ ] Console clean.
- [ ] Assets loaded.
- [ ] No rendering defects.

---

# Common Mistakes

Avoid:

- Waiting until project completion before testing.
- Ignoring responsive issues.
- Presenting work before screenshot comparison.
- Leaving console errors unresolved.
- Skipping functional verification.

---

# Best Practices

- Perform Browser QA after every completed section.
- Fix defects immediately.
- Compare against Figma frequently.
- Validate responsiveness throughout development.
- Keep Browser QA integrated into the implementation workflow.

---

# Engineering Acceptance Criteria

A section complies with Browser QA when:

- It launches correctly.
- Visual implementation matches the approved design.
- Functional behaviour is correct.
- Responsive behaviour is verified.
- Browser console is clean.
- Identified defects have been corrected before presentation.

---

# Chapter Summary

Browser QA is a continuous engineering process performed throughout development.

By validating each completed section before moving forward, defects are identified early, visual quality remains high, and the final delivery becomes significantly more reliable.

Browser QA should be treated as an integral part of implementation rather than a separate phase at the end of the project.

---