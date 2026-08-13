# 18 – Slider Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every slider, carousel, and scrolling content component used within the project.
>
> **Related Chapters**
>
> - 03 Figma Standards
> - 11 Components
> - 13 JavaScript Standards
> - 15 Performance
> - 19 Browser QA

---

# Purpose

This chapter defines the engineering standards for implementing and validating sliders.

Every slider should behave consistently, match the approved design, and integrate with the project's shared architecture.

Sliders should never rely on default library behaviour without verification.

---

# Objective

Every slider should provide:

- Correct functionality
- Predictable interaction
- Responsive behaviour
- Stable performance
- Consistent user experience

---

# Engineering Philosophy

A slider is a reusable UI component.

The JavaScript library used to build it is an implementation detail.

The engineering standard defines **behaviour**, not a specific library.

---

# Mandatory Rules

Every slider implementation MUST:

- Match the approved Figma design.
- Reuse the approved project slider architecture.
- Validate all interaction states.
- Support responsive behaviour.
- Preserve accessibility where applicable.
- Be tested during Browser QA.

---

# Slider Validation

Before implementation verify:

- Autoplay
- Autoplay speed
- Pause on hover
- Pause on focus
- Mouse drag
- Touch drag
- Swipe support
- Navigation controls
- Pagination controls
- Loop behaviour
- Animation speed

Do not assume library defaults match the approved design.

Every behaviour should be explicitly verified.

---

# Autoplay

If autoplay exists in the approved design, verify:

- Starts correctly.
- Uses the correct timing.
- Stops when required.
- Resumes correctly (if applicable).

---

# Mouse Interaction

Desktop interaction should verify:

- Drag behaviour
- Cursor behaviour
- Navigation controls
- Hover states

---

# Touch Interaction

Mobile interaction should verify:

- Swipe responsiveness
- Touch drag
- Gesture stability
- No accidental scrolling conflicts

---

# Navigation Controls

Verify:

- Previous button
- Next button
- Disabled states
- Positioning
- Visual styling

Navigation controls should match the approved design.

---

# Pagination

Where pagination exists, verify:

- Active state
- Interaction
- Position
- Styling
- Synchronization with slide changes

---

# Loop Behaviour

Confirm whether looping is:

- Enabled
- Disabled

The implementation must match the approved design exactly.

---

# Animation

Verify:

- Animation speed
- Transition smoothness
- Timing consistency

Animation should feel intentional and remain consistent across breakpoints.

---

# Responsive Behaviour

Validate the slider on:

- Desktop
- Laptop
- Tablet
- Mobile

Verify:

- Visible slides
- Alignment
- Touch interaction
- Navigation controls
- Pagination
- Spacing

---

# Performance

Sliders should:

- Initialize only when required.
- Avoid unnecessary DOM manipulation.
- Avoid duplicate initialization.
- Integrate with the shared JavaScript architecture.

---

# Validation Checklist

Before approving a slider verify:

## Behaviour

- [ ] Autoplay verified.
- [ ] Timing verified.
- [ ] Pause behaviour verified.
- [ ] Loop behaviour verified.

---

## Interaction

- [ ] Mouse drag verified.
- [ ] Touch drag verified.
- [ ] Swipe verified.

---

## Controls

- [ ] Navigation buttons verified.
- [ ] Pagination verified.
- [ ] Active states verified.

---

## Responsive

- [ ] Desktop verified.
- [ ] Laptop verified.
- [ ] Tablet verified.
- [ ] Mobile verified.

---

## Performance

- [ ] No duplicate initialization.
- [ ] Shared JavaScript reused.
- [ ] Smooth rendering verified.

---

# Common Mistakes

Avoid:

- Using library defaults without validation.
- Incorrect autoplay timing.
- Broken touch interaction.
- Duplicate slider initialization.
- Inconsistent responsive layouts.
- Navigation controls that do not match the design.

---

# Best Practices

- Configure every behaviour explicitly.
- Validate against Figma.
- Test with mouse and touch.
- Keep initialization centralized.
- Review performance during implementation.

---

# Engineering Acceptance Criteria

A slider implementation complies with this standard when:

- Every interaction matches the approved design.
- Autoplay and timing are correct.
- Navigation and pagination function correctly.
- Responsive behaviour is verified.
- Performance remains stable.
- Browser QA passes without defects.

---

# Chapter Summary

Sliders are interactive components that require consistent engineering validation.

Following these standards ensures every slider behaves predictably, performs efficiently, and accurately reflects the approved design while remaining fully integrated with the project's frontend architecture.

---