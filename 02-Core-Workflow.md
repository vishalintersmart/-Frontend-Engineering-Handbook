# 02 – Core Workflow

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend implementation using this handbook.

---

# Purpose

The Core Workflow defines the mandatory implementation process that must be followed for every frontend development task.

Its purpose is to ensure every implementation follows the same engineering methodology from project analysis through final delivery.

Regardless of project size or complexity, the workflow described in this chapter should be followed without omission.

---

# Objective

The objective of this workflow is to produce frontend implementations that are:

- Pixel-perfect
- Responsive
- Accessible
- Performant
- Maintainable
- Consistent with the existing project architecture

Following a consistent workflow reduces implementation errors, improves maintainability, and ensures predictable project quality.

---

# Mandatory Rules

Every implementation MUST:

- Read and understand the approved Figma design.
- Treat Figma as the single source of truth.
- Reuse the existing project architecture.
- Build only the requested scope.
- Validate responsiveness.
- Perform Browser QA.
- Perform Final QA.
- Deliver only the requested assets.

No implementation should skip any stage of the workflow.

---

# Standard Development Workflow

Every frontend task should follow the sequence below.

## Phase 1 — Requirement Analysis

### Step 1 — Understand the Request

Identify:

- Requested page
- Requested section
- Requested functionality
- Required deliverables

Before writing code, ensure the implementation scope is fully understood.

---

### Step 2 — Review Project Architecture

Inspect the existing project before beginning implementation.

Review:

- HTML architecture
- CSS architecture
- JavaScript architecture
- Shared components
- Layouts
- Navigation
- Utilities
- Responsive system
- Naming conventions

Existing architecture should always be extended rather than replaced.

---

### Step 3 — Review the Approved Figma Design

Open the approved Figma file using Dev Mode.

Review:

- Layout
- Components
- Typography
- Spacing
- Assets
- Responsive behaviour (when available)

Design values must be extracted directly from the design rather than estimated visually.

---

## Phase 2 — Planning

Before implementation begins, determine:

- Which components already exist
- Which components should be reused
- Which assets are required
- Which page-specific files need to be created
- Which shared modules can be extended

Avoid unnecessary duplication whenever reusable solutions exist.

---
---

## Phase 3 — Asset Extraction

### Purpose

Before implementation begins, every required asset must be extracted from the approved Figma design.

Missing, recreated, or estimated assets introduce inconsistencies and reduce implementation accuracy.

---

### Asset Extraction Rules

Download every required asset directly from Figma.

This includes:

- Images
- SVGs
- Logos
- Illustrations
- Icons

Preferred asset formats:

1. SVG
2. WebP
3. AVIF (where supported)
4. PNG (only when transparency is required)

---

### Asset Rules

Never:

- Recreate logos.
- Redraw icons.
- Replace assets.
- Generate placeholder graphics.

Assets should only be replaced when explicitly instructed by the client or project requirements.

---

## Phase 4 — HTML Development

### Purpose

Create semantic, reusable, and accessible HTML that accurately reflects the approved design.

---

### HTML Development Process

1. Create the page wrapper.
2. Build semantic page structure.
3. Create reusable sections.
4. Apply unique IDs.
5. Apply unique section classes.
6. Implement headings correctly.
7. Add meaningful image alt text.
8. Verify metadata compatibility.

---

### HTML Requirements

Every page must include:

- One H1 element.
- Semantic HTML5 elements.
- SEO-friendly IDs.
- Stable anchor IDs.
- Reusable section structure.
- Consistent button structure.
- Consistent form structure.

Avoid:

- Duplicate IDs.
- Excessive nesting.
- Non-semantic markup.

---

## Phase 5 — Styling

### Purpose

Implement styling using the approved SASS architecture while maintaining consistency with the project design system.

---

### Styling Workflow

1. Apply global styles.
2. Reuse existing modules.
3. Create page-specific styles only when necessary.
4. Follow the approved SASS folder structure.
5. Use design tokens.
6. Implement responsive scaling.

---

### Styling Rules

Never:

- Write inline CSS.
- Use `!important` unless absolutely required.
- Duplicate CSS rules.
- Hardcode reusable values.

Prefer:

- CSS custom properties.
- Shared modules.
- Existing utilities.
- Reusable mixins.

---

## Phase 6 — JavaScript Development

### Purpose

Implement JavaScript only where required while maintaining the project's architecture.

---

### Workflow

1. Determine whether functionality already exists.
2. Extend existing JavaScript.
3. Place shared logic in `assets/js/app.js`.
4. Keep page-specific logic isolated to the current page.

---

### Rules

Avoid:

- Inline JavaScript.
- Duplicate event listeners.
- Duplicate business logic.

JavaScript should remain modular, maintainable, and reusable.

---

## Phase 7 — Responsive Development

### Purpose

Ensure the implementation functions consistently across all supported breakpoints.

---

### Validation

Verify:

- Desktop
- Large Laptop
- Laptop
- Tablet Landscape
- Tablet Portrait
- Large Mobile
- Mobile

Responsive behaviour should preserve the visual hierarchy defined by the design.

Typography, spacing, and layout should scale proportionally.

---

## Phase 8 — Quality Assurance

Quality assurance is an integral part of development.

No implementation should be considered complete without validation.

QA consists of three stages.

### Stage 1 — Browser QA

After completing each section:

1. Launch locally.
2. Capture Desktop screenshot.
3. Capture Tablet screenshot.
4. Capture Mobile screenshot.
5. Compare with Figma.
6. Fix all visual differences.

---

### Stage 2 — Figma Validation

Verify that the implementation matches:

- Section order
- Typography
- Font sizes
- Font weights
- Colors
- Border radius
- Shadows
- Images
- Icons
- Alignment
- Spacing
- Padding
- Margins
- Hover states
- Animations
- Cursor effects

No visual approximation is acceptable.

---

### Stage 3 — Final QA

Verify:

- No broken layouts.
- No overlapping content.
- Responsive behaviour.
- Mobile navigation.
- Interactive elements.
- JavaScript console.
- Accessibility.
- Performance.
- Pixel-perfect implementation.

Only after successful completion of all validation stages should development proceed to delivery.

---

## Phase 9 — Delivery

The delivery package should include only the requested implementation.

Deliverables may include:

- HTML
- CSS
- JavaScript
- Assets List
- Notes
- Validation Checklist

Stop after completing the approved scope and wait for further instructions.

---

# Workflow Summary

Every frontend implementation should follow this sequence:

1. Requirement Analysis
2. Project Review
3. Figma Review
4. Planning
5. Asset Extraction
6. HTML Development
7. Styling
8. JavaScript
9. Responsive Development
10. Browser QA
11. Figma Validation
12. Final QA
13. Delivery

Skipping any phase increases the risk of inconsistencies, regressions, or deviations from the engineering standard.

---