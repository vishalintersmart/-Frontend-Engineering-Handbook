# 09 – Responsive System

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project developed using this handbook.
>
> **Related Chapters**
>
> - 03 Figma Standards
> - 07 CSS Standards
> - 08 SASS Architecture
> - 10 Design Tokens
> - 11 Components

---

# Purpose

This chapter defines the responsive engineering system used throughout the project.

Responsive development is not limited to media queries.

It defines how every layout, typography scale, spacing system, container, and component should adapt across supported devices.

Every project must follow a single responsive methodology to ensure consistency throughout the entire application.

---

# Objective

The objective of the responsive system is to create layouts that preserve the original design intent across every supported breakpoint.

Responsive behaviour should:

- maintain hierarchy
- preserve readability
- preserve spacing relationships
- preserve component proportions
- avoid layout shifts
- improve usability

Every breakpoint should feel like a carefully designed experience rather than a compressed desktop layout.

---

# Engineering Philosophy

Responsive design is a design system.

It is not a collection of random media queries.

Every responsive adjustment should originate from predefined global rules.

Developers should never create arbitrary breakpoint values for individual components unless explicitly required by the project architecture.

---

# Mandatory Rules

Every project MUST:

- Use the approved global breakpoints.
- Use the approved container widths.
- Follow the global typography scale.
- Follow the global spacing scale.
- Preserve the visual hierarchy.
- Validate every supported breakpoint.
- Avoid component-specific breakpoint values unless justified.
- Scale consistently across the project.

These rules apply to every page and every reusable component.

---

# Responsive Design Principles

Responsive implementation should be based on systems rather than isolated fixes.

The responsive system is composed of:

- Global Breakpoints
- Global Containers
- Typography Scale
- Spacing Scale
- Component Scaling
- Layout Adaptation

Each subsystem works together to create a predictable responsive experience.

---

# Supported Breakpoints

Every project should use a consistent breakpoint system.

Typical responsive validation includes:

- Desktop
- Large Laptop
- Laptop
- Tablet Landscape
- Tablet Portrait
- Large Mobile
- Mobile

All supported breakpoints should be validated during development.

Avoid introducing one-off breakpoint values unless they become part of the global responsive system.

---

# Breakpoint Strategy

Breakpoints should be driven by layout requirements rather than device names.

Responsive changes should occur when the design requires them—not simply because a particular device exists.

The project should maintain a centralized breakpoint system shared across all components.

---

# Global Containers

Containers define the maximum readable width of page content.

Container widths should remain consistent across the entire project.

Containers are responsible for:

- Layout alignment
- Content width
- Horizontal spacing
- Grid consistency

Individual sections should not redefine container behaviour without architectural justification.

---

# Container Scaling

As viewport width decreases, containers should scale predictably while maintaining appropriate horizontal padding.

Container scaling should preserve:

- Reading comfort
- Alignment
- Visual rhythm

Avoid creating multiple container systems within the same project.

---

# Standard Breakpoints & Containers

Every project must use the following responsive container system unless the project explicitly defines a different one.

| Breakpoint | Container |
|------------|----------:|
| 0px        | Fluid |
| 576px      | 540px |
| 768px      | 720px |
| 992px      | 960px |
| 1200px     | 1140px |
| 1440px     | 1320px |
| 1600px     | 1480px |
| 1920px     | 1680px |

Reference CSS:

```css
.container{
    width:100%;
    margin-inline:auto;
    padding-inline:16px;
}

@media(min-width:576px){.container{max-width:540px;}}
@media(min-width:768px){.container{max-width:720px;}}
@media(min-width:992px){.container{max-width:960px;}}
@media(min-width:1200px){.container{max-width:1140px;}}
@media(min-width:1440px){.container{max-width:1320px;}}
@media(min-width:1600px){.container{max-width:1480px;}}
@media(min-width:1920px){.container{max-width:1680px;}}
```
---

# Responsive Layout Principles

Layouts should adapt by reorganizing content—not by shrinking everything proportionally.

Examples include:

- Multi-column layouts becoming single-column.
- Horizontal groups becoming vertical stacks.
- Navigation adapting for smaller screens.
- Images resizing without distortion.

The responsive layout should remain intentional at every breakpoint.

---

# Responsive Typography

Typography should scale according to the project's global typography system.

Responsive typography should preserve:

- Readability
- Hierarchy
- Proportion

Avoid arbitrary font-size changes within individual components.

Typography scaling should remain centralized.

---

# Responsive Spacing

Spacing should also follow a global system.

Examples include:

- Section spacing
- Component spacing
- Grid gaps
- Internal padding

Spacing relationships should remain visually balanced across all supported viewport sizes.

Avoid inconsistent spacing adjustments between pages.

---

# Component Scaling

Reusable components should respond consistently to viewport changes.

Examples include:

- Buttons
- Cards
- Navigation
- Hero sections
- Forms
- Sliders

Component scaling should follow the same responsive rules throughout the project.

---

# Aspect Ratio Rule

Images and videos should preserve aspect ratio.

Avoid stretching media.

Reserve layout space to prevent CLS.

---

# Responsive Validation Workflow

Every page should be validated in the following order:

1. Desktop
2. Laptop
3. Tablet
4. Mobile

At each breakpoint verify:

- Layout
- Typography
- Containers
- Spacing
- Components
- Navigation
- Images
- Forms
- Interactive elements

Responsive validation should occur throughout development rather than only after implementation.

---

# Engineering Rules

Developers should not:

- Create random breakpoint values.
- Hardcode responsive fixes.
- Override the global responsive system.
- Create multiple container implementations.
- Scale typography inconsistently.
- Introduce page-specific responsive behaviour that conflicts with the global system.

---

# Validation Checklist

Before completing a page verify:

## Layout

- [ ] Layout adapts correctly.
- [ ] Grid remains consistent.
- [ ] Containers align correctly.

## Typography

- [ ] Heading hierarchy preserved.
- [ ] Font scaling verified.
- [ ] Readability maintained.

## Spacing

- [ ] Section spacing verified.
- [ ] Component spacing verified.
- [ ] Gap values verified.

## Components

- [ ] Buttons scale correctly.
- [ ] Forms remain usable.
- [ ] Cards adapt correctly.
- [ ] Navigation functions correctly.

## Behaviour

- [ ] No horizontal scrolling.
- [ ] No overlapping content.
- [ ] No layout collapse.
- [ ] Responsive hierarchy preserved.

---

# Common Mistakes

Avoid:

- Device-specific styling.
- Random breakpoint values.
- Inconsistent typography scaling.
- Multiple container widths.
- Arbitrary spacing changes.
- Responsive overrides that conflict with the global system.
- Treating responsive design as an afterthought.

---

# Best Practices

- Build mobile responsiveness as part of the implementation process.
- Use centralized breakpoint definitions.
- Keep containers consistent.
- Scale typography and spacing through the global system.
- Validate each breakpoint before progressing to the next.
- Reuse responsive patterns across the project.

---