# 03 – Figma Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project developed using this handbook.
>
> **Related Chapters**
>
> - 02 Core Workflow
> - 04 Project Architecture
> - 07 HTML Standards
> - 09 SASS Architecture
> - 21 Figma Validation

---

# Purpose

The purpose of this chapter is to establish a standardized methodology for translating approved Figma designs into production-ready frontend implementations.

Every visual decision made during development must originate from the approved Figma design.

This chapter defines:

- How Figma should be used.
- What information must be extracted.
- How design values should be interpreted.
- How assets should be collected.
- How implementation accuracy should be validated.

Following these standards ensures consistency, predictability, and pixel-perfect implementation across every project.

---

# Objective

The objective of this chapter is to eliminate subjective implementation decisions.

Every developer working on the project should produce nearly identical results when following this handbook.

Implementation should be driven by design specifications rather than personal judgement.

---

# Mandatory Rules

Every frontend implementation MUST:

- Use the approved Figma design.
- Use Figma Dev Mode whenever available.
- Treat Figma as the single source of truth.
- Extract values directly from the design.
- Never estimate measurements visually.
- Never redesign approved layouts.
- Never change typography.
- Never replace assets.
- Never approximate spacing.
- Never introduce undocumented styles.

Failure to follow these rules may result in inconsistent implementations and unnecessary redesign work.

---

# Engineering Philosophy

Figma is not a design reference.

Figma is the engineering specification.

Developers should think of Figma in the same way backend developers think about API documentation.

Everything implemented in code should originate from the approved design.

The implementation process should translate design specifications into code rather than reinterpret them.

---

# Single Source of Truth

The approved Figma file is the only authoritative source for visual implementation.

Every implementation decision should originate from the design.

This includes:

- Typography
- Layout
- Components
- Auto Layout
- Constraints
- Spacing
- Colors
- Effects
- Shadows
- Border Radius
- Icons
- SVGs
- Images
- Responsive behaviour
- Component variants

No visual property should be guessed.

---

# Approved Workflow

Every project should begin by reviewing the approved Figma design before writing any code.

Implementation should never begin from screenshots.

Implementation should never begin from exported images.

The live Figma document should always be inspected.

---

# Figma Dev Mode

Whenever available, Figma Dev Mode must be used.

Developers should inspect every required element directly from Dev Mode.

Never estimate values manually.

---

## Information That Must Be Extracted

The following properties should always be extracted directly from Figma.

### Typography

- Font Family
- Font Size
- Font Weight
- Line Height
- Letter Spacing
- Text Transform
- Text Alignment

---

### Colors

Extract:

- Primary Colors
- Secondary Colors
- Text Colors
- Background Colors
- Border Colors
- Overlay Colors
- Gradient Definitions

Do not recreate colors manually.

---

### Layout

Extract:

- Width
- Height
- Padding
- Margin
- Gap
- Auto Layout
- Constraints
- Alignment
- Distribution

Never estimate spacing.

---

### Borders

Extract:

- Border Width
- Border Radius
- Border Style
- Border Color

---

### Effects

Extract:

- Shadows
- Blur
- Opacity
- Background Blur
- Layer Effects

---

### Components

Inspect:

- Variants
- States
- Nested Components
- Component Properties

Always reuse existing project components where appropriate.

---

### Assets

Collect:

- Images
- SVGs
- Icons
- Logos
- Illustrations

Assets should be downloaded directly from Figma.

---

# Design Inspection Workflow

Every page should follow this inspection sequence.

Step 1

Understand the purpose of the page.

Step 2

Identify reusable sections.

Step 3

Identify shared components.

Step 4

Inspect typography.

Step 5

Inspect spacing.

Step 6

Inspect layout.

Step 7

Inspect responsive behaviour.

Step 8

Collect assets.

Step 9

Plan implementation.

Only after these steps are complete should HTML development begin.

---

# Engineering Checklist

Before beginning development verify:

- [ ] Approved Figma file received.
- [ ] Correct page selected.
- [ ] Dev Mode available.
- [ ] Typography inspected.
- [ ] Colors inspected.
- [ ] Layout inspected.
- [ ] Components inspected.
- [ ] Auto Layout inspected.
- [ ] Constraints inspected.
- [ ] Images identified.
- [ ] Icons identified.
- [ ] SVGs identified.
- [ ] Responsive behaviour reviewed.
- [ ] Shared components identified.

---

# Common Mistakes

Avoid:

- Measuring from screenshots.
- Guessing spacing.
- Guessing typography.
- Ignoring Auto Layout.
- Ignoring Constraints.
- Recreating icons manually.
- Exporting low-quality assets.
- Replacing approved illustrations.
- Using approximate colors.
- Introducing undocumented spacing.

---

# Best Practices

- Inspect the design before opening the code editor.
- Review the complete page before implementing the first section.
- Understand the page hierarchy before building components.
- Identify reusable components early.
- Build from the design, not from memory.
- Validate measurements before coding.

---
---

# Asset Extraction Standards

## Purpose

Assets form the visual foundation of every frontend implementation.

To ensure visual accuracy, consistency, and optimal performance, all graphical assets must be extracted directly from the approved Figma design.

Assets must never be recreated, approximated, or substituted without explicit approval.

This standard applies to every frontend project regardless of technology stack.

---

# Asset Extraction Workflow

Every asset should follow the same extraction process.

## Step 1 — Identify Required Assets

Before exporting anything, identify all assets used within the page.

This includes:

- Logos
- Icons
- Images
- Illustrations
- SVG graphics
- Background graphics
- Decorative elements
- UI graphics
- Social icons
- Brand assets

Avoid exporting unnecessary assets.

---

## Step 2 — Determine Asset Type

Every asset should be categorized before export.

### Vector Assets

Includes:

- Logos
- Icons
- UI graphics
- Simple illustrations
- Shapes
- Decorative vectors

Preferred format:

```
SVG
```

---

### Raster Assets

Includes:

- Photography
- Textured graphics
- Marketing imagery
- Large illustrations

Preferred format hierarchy:

```
AVIF
↓

WebP
↓

PNG (Transparency Only)

↓

JPEG (Photography Only)
```

Always choose the smallest format that preserves visual quality.

---

## Step 3 — Verify Export Settings

Before exporting verify:

- Correct scale
- Correct dimensions
- Transparency
- Background removal
- Retina quality if required

Never upscale exported assets.

---

# Asset Categories

## Images

Images should be exported at the dimensions required by the design.

Rules

- Maintain aspect ratio.
- Avoid unnecessary enlargement.
- Preserve original quality.
- Compress only after export.
- Never crop differently from the approved design.

---

## SVG Assets

SVG should always be preferred whenever possible.

Ideal for:

- Logos
- Icons
- UI graphics
- Shapes
- Decorative vectors

Benefits:

- Resolution independent
- Small file size
- Easily styled
- Scalable without quality loss

Do not convert SVG assets into PNG unless required.

---

## Icons

Icons must be exported directly from Figma.

Never:

- Redraw icons.
- Trace icons manually.
- Replace icon styles.
- Mix icon families.

Every icon should remain visually consistent with the design system.

---

## Logos

Company logos are protected visual assets.

Never:

- Recreate logos.
- Modify proportions.
- Change colors.
- Simplify shapes.
- Redraw vector paths.

Always use the approved logo provided within the design.

---

## Illustrations

Illustrations should remain identical to the approved design.

Never:

- Replace illustrations.
- Simplify artwork.
- Change colors.
- Remove visual details.

Use the original exported asset.

---

## Background Graphics

Background graphics should be exported separately whenever practical.

Avoid flattening backgrounds into larger images unless required.

This improves:

- Maintainability
- Performance
- Future updates

---

# Asset Optimization Standards

Optimization should reduce file size without introducing visible quality loss.

Preferred optimization strategy:

1. Export original asset.
2. Verify quality.
3. Optimize.
4. Validate visually.
5. Replace optimized version.

Never optimize blindly.

Always compare the optimized asset against the original.

---

# Asset Naming Convention

Use clear and predictable filenames.

Recommended examples:

```
logo-primary.svg

logo-white.svg

icon-search.svg

icon-phone.svg

hero-image.webp

about-banner.webp

team-photo-01.webp

illustration-process.svg

bg-pattern.svg
```

Avoid:

```
image1.png

new-logo.svg

final2.png

test.webp

export.png
```

Filenames should describe the asset rather than its export history.

---

# Asset Folder Structure

Recommended organization:

```
assets/

images/

logos/

icons/

illustrations/

backgrounds/

social/

favicons/
```

Separate asset categories improve maintainability.

---

# Asset Validation Checklist

Before implementation verify:

- [ ] Every required asset exported.
- [ ] Correct format selected.
- [ ] Correct dimensions.
- [ ] SVG used where appropriate.
- [ ] Images optimized.
- [ ] Transparency verified.
- [ ] Logos unchanged.
- [ ] Icons unchanged.
- [ ] Illustrations unchanged.
- [ ] Background graphics exported correctly.
- [ ] File naming follows conventions.
- [ ] Assets organized into correct folders.

---

# Common Mistakes

Avoid:

- Exporting screenshots.
- Upscaling images.
- Mixing icon styles.
- Rasterizing SVG graphics.
- Renaming files inconsistently.
- Compressing assets excessively.
- Recreating logos.
- Exporting unused assets.
- Using PNG where SVG is available.
- Leaving temporary filenames.

---

# Best Practices

- Export only what is required.
- Keep original source exports.
- Optimize after export.
- Prefer vector graphics whenever possible.
- Maintain consistent naming.
- Group assets by category.
- Validate every exported asset before implementation.

---
---

# Pixel-Perfect Implementation Standards

## Purpose

The purpose of this standard is to ensure that every frontend implementation is visually indistinguishable from the approved Figma design.

Pixel-perfect implementation does **not** mean matching only the general appearance of a design. It means reproducing every measurable visual characteristic defined in Figma while respecting the existing project architecture.

Every implementation must preserve the visual hierarchy, proportions, spacing, and interaction behaviour defined by the design.

---

# Engineering Principle

Pixel-perfect implementation is an engineering requirement, not a visual preference.

Developers must implement the approved design exactly as specified.

Personal interpretation should never replace documented design values.

Whenever uncertainty exists, return to the Figma source rather than estimating.

---

# Mandatory Rules

Every implementation MUST:

- Match the approved Figma design.
- Preserve the visual hierarchy.
- Preserve layout proportions.
- Preserve spacing relationships.
- Preserve typography.
- Preserve imagery.
- Preserve iconography.
- Preserve component sizing.
- Preserve interaction behaviour.

Developers must never intentionally alter the approved design unless instructed by the client or design team.

---

# Visual Accuracy Requirements

The following properties must match the approved design exactly.

## Layout

Verify:

- Section order
- Grid structure
- Container alignment
- Content alignment
- Section widths
- Element positioning
- Column structure

---

## Typography

Verify:

- Font family
- Font size
- Font weight
- Line height
- Letter spacing
- Text alignment
- Text casing

Typography must never be approximated.

---

## Spacing

Verify:

- Margins
- Padding
- Gap values
- Section spacing
- Component spacing
- Internal spacing
- External spacing

Spacing relationships are just as important as individual spacing values.

---

## Colors

Verify:

- Primary colors
- Secondary colors
- Background colors
- Border colors
- Overlay colors
- Gradient colors
- Text colors

Never replace colors with visually similar alternatives.

---

## Borders

Verify:

- Border width
- Border style
- Border radius
- Border color

---

## Shadows

Verify:

- Shadow position
- Shadow blur
- Shadow spread
- Shadow opacity
- Multiple shadow layers

---

## Media

Verify:

- Images
- SVG graphics
- Logos
- Icons
- Illustrations

Media assets should exactly match those provided in the approved design.

---

## Effects

Verify:

- Blur
- Opacity
- Glass effects
- Overlay effects
- Layer effects

---

# Visual Hierarchy

Every page should preserve the hierarchy established by the designer.

This includes:

- Heading emphasis
- Reading order
- Call-to-action prominence
- Content grouping
- White space distribution
- Relative component sizing

The visual hierarchy must remain intact across all supported devices.

---

# Responsive Verification

## Purpose

Responsive implementation should adapt the layout while preserving the design intent.

Scaling should never distort the hierarchy or create cramped layouts.

---

## Required Breakpoints

Every implementation must be validated for:

- Desktop
- Large Laptop
- Laptop
- Tablet Landscape
- Tablet Portrait
- Large Mobile
- Mobile

No supported breakpoint may be skipped.

---

## Responsive Scaling Rules

Responsive implementation should:

- Preserve proportional spacing.
- Preserve visual hierarchy.
- Prevent oversized typography.
- Prevent cramped layouts.
- Maintain balanced whitespace.
- Use the project's design tokens for scaling.

Do not blindly interpolate values between breakpoints.

Responsive adjustments should be guided by the approved design.

---

# Header Validation

Before implementing any page, verify the header behaviour.

Inspect whether the header is:

- Fixed
- Sticky
- Absolute
- Transparent

Also verify:

- Blur effects
- Glass effects
- Hero overlap
- Scroll behaviour
- State transitions

Never introduce artificial top margins to compensate for header positioning.

Header behaviour should match the approved design exactly.

---

# Slider Validation

Every slider should be inspected before implementation.

Verify:

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

Do not rely on default plugin settings.

Every slider should be configured according to the approved design.

---

# Engineering Validation Workflow

Before considering a section complete:

1. Compare against the approved Figma design.
2. Verify measurements.
3. Verify typography.
4. Verify spacing.
5. Verify colors.
6. Verify media.
7. Verify interactions.
8. Verify responsiveness.
9. Verify animations.
10. Verify accessibility.
11. Verify performance.

Only after all validation steps are complete should the implementation move to Browser QA.

---

# Pixel-Perfect Checklist

Before marking a section complete:

## Layout

- [ ] Matches approved design.
- [ ] Correct section order.
- [ ] Correct alignment.
- [ ] Correct container width.

## Typography

- [ ] Font family verified.
- [ ] Font size verified.
- [ ] Font weight verified.
- [ ] Line height verified.
- [ ] Letter spacing verified.

## Spacing

- [ ] Padding verified.
- [ ] Margins verified.
- [ ] Gap values verified.
- [ ] Section spacing verified.

## Visual Styling

- [ ] Colors verified.
- [ ] Border radius verified.
- [ ] Shadows verified.
- [ ] Effects verified.

## Components

- [ ] Images verified.
- [ ] Icons verified.
- [ ] SVGs verified.
- [ ] Buttons verified.
- [ ] Forms verified.

## Behaviour

- [ ] Header verified.
- [ ] Navigation verified.
- [ ] Sliders verified.
- [ ] Animations verified.

## Responsive

- [ ] Desktop verified.
- [ ] Laptop verified.
- [ ] Tablet verified.
- [ ] Mobile verified.

---

# Common Implementation Errors

Avoid:

- Estimating spacing.
- Guessing typography.
- Ignoring Auto Layout spacing.
- Ignoring Constraints.
- Changing the visual hierarchy.
- Replacing approved assets.
- Using default slider settings.
- Introducing inconsistent spacing.
- Compensating for header positioning with artificial margins.
- Skipping responsive validation.

---

# Best Practices

- Compare frequently against Figma throughout development.
- Validate one section at a time rather than the entire page at the end.
- Measure before coding.
- Reuse existing components whenever possible.
- Keep responsive behaviour consistent with the design.
- Treat Browser QA as part of implementation, not an afterthought.

---
---

# Figma Matching Checklist

## Purpose

The Figma Matching Checklist is the final visual verification process performed before Browser QA and Final QA.

Its purpose is to ensure that the completed implementation accurately represents the approved Figma design without visual approximation.

This checklist should be completed for every page and every major section.

---

# Layout Verification

Verify:

- [ ] Section order matches the approved design.
- [ ] Overall page structure matches Figma.
- [ ] Container widths are correct.
- [ ] Grid alignment is correct.
- [ ] Content alignment is correct.
- [ ] Section hierarchy is preserved.
- [ ] White space distribution matches the design.

---

# Typography Verification

Verify:

- [ ] Font family.
- [ ] Font size.
- [ ] Font weight.
- [ ] Line height.
- [ ] Letter spacing.
- [ ] Text transform.
- [ ] Text alignment.
- [ ] Heading hierarchy.

---

# Color Verification

Verify:

- [ ] Primary colors.
- [ ] Secondary colors.
- [ ] Background colors.
- [ ] Text colors.
- [ ] Border colors.
- [ ] Overlay colors.
- [ ] Gradient colors.

---

# Border & Effect Verification

Verify:

- [ ] Border width.
- [ ] Border radius.
- [ ] Border color.
- [ ] Shadows.
- [ ] Blur effects.
- [ ] Glass effects.
- [ ] Layer effects.

---

# Spacing Verification

Verify:

- [ ] Margins.
- [ ] Padding.
- [ ] Gap values.
- [ ] Internal spacing.
- [ ] External spacing.
- [ ] Section spacing.

Spacing relationships should match the approved design and maintain proportional balance across breakpoints.

---

# Asset Verification

Verify:

- [ ] Images.
- [ ] SVG graphics.
- [ ] Logos.
- [ ] Icons.
- [ ] Illustrations.

All visual assets must be identical to those supplied in the approved Figma file.

---

# Component Verification

Verify:

- [ ] Buttons.
- [ ] Forms.
- [ ] Cards.
- [ ] Shared modules.
- [ ] Navigation.
- [ ] Footer.
- [ ] Hero section.

Components should remain visually and functionally consistent throughout the project.

---

# Responsive Verification

Verify every supported breakpoint:

- [ ] Desktop
- [ ] Large Laptop
- [ ] Laptop
- [ ] Tablet Landscape
- [ ] Tablet Portrait
- [ ] Large Mobile
- [ ] Mobile

At each breakpoint confirm:

- Layout integrity
- Typography scaling
- Spacing
- Navigation
- Component behaviour
- White space
- Visual hierarchy

---

# Animation & Interaction Verification

Verify:

- [ ] Hover states.
- [ ] Active states.
- [ ] Focus states.
- [ ] Slider behaviour.
- [ ] Navigation behaviour.
- [ ] Scroll behaviour.
- [ ] Animation timing.
- [ ] Transition timing.
- [ ] Cursor behaviour.

---

# Design Acceptance Criteria

An implementation is considered visually approved only when:

- No measurable visual differences exist between the implementation and the approved Figma design.
- Layout proportions remain consistent across all supported breakpoints.
- Typography, spacing, colors, and imagery are identical to the approved design.
- Responsive behaviour preserves the intended design hierarchy.
- No visual approximations or undocumented design decisions have been introduced.

---

# Implementation Readiness Checklist

Before coding begins:

- [ ] Project requirements understood.
- [ ] Existing architecture reviewed.
- [ ] Approved Figma file available.
- [ ] Dev Mode accessible.
- [ ] Required assets identified.
- [ ] Shared components identified.
- [ ] Responsive behaviour reviewed.
- [ ] Implementation plan prepared.

---

# Pre-Delivery Checklist

Before handing work to QA or the client:

- [ ] Pixel-perfect verification completed.
- [ ] Browser QA completed.
- [ ] Final QA completed.
- [ ] Responsive validation completed.
- [ ] Accessibility reviewed.
- [ ] Performance reviewed.
- [ ] Assets optimized.
- [ ] No console errors.
- [ ] No layout regressions.
- [ ] Requested scope completed.

Only after every item has been verified should the implementation be considered ready for delivery.

---

# Related Chapters

This chapter should be read together with:

- 02 – Core Workflow
- 04 – Project Architecture
- 07 – HTML Standards
- 09 – SASS Architecture
- 15 – Performance
- 20 – Browser QA
- 21 – Final QA

These chapters collectively define the complete implementation and validation process.

---

# Chapter Summary

This chapter establishes the engineering standards for using Figma as the authoritative source for frontend implementation.

It defines:

- The role of Figma in the development process.
- The use of Dev Mode.
- Asset extraction requirements.
- Pixel-perfect implementation standards.
- Responsive validation.
- Header and slider verification.
- Design acceptance criteria.
- Engineering checklists.
- Readiness for implementation and delivery.

Compliance with this chapter ensures that frontend implementations remain faithful to the approved design while maintaining consistency with the broader engineering methodology defined throughout this handbook.

---