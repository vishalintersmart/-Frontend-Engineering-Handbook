# 06 – HTML Standards

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every HTML document, page, component, module, and CMS-generated content.
>
> **Related Chapters**
>
> - 04 Project Architecture
> - 05 PHP Architecture
> - 09 SASS Architecture
> - 12 CMS Development
> - 14 Accessibility

---

# Purpose

HTML provides the structural foundation of every frontend project.

The purpose of this chapter is to define the mandatory standards for writing semantic, accessible, maintainable, reusable, and scalable HTML.

Every HTML document produced under this handbook must follow these standards regardless of project size.

---

# Objective

HTML should communicate structure rather than presentation.

CSS controls appearance.

JavaScript controls behaviour.

HTML defines meaning.

Every developer should produce predictable, semantic markup that is easy to maintain, accessible, SEO-friendly, and reusable.

---

# Engineering Philosophy

Good HTML should remain understandable without CSS or JavaScript.

A developer reading the markup should immediately understand:

- Page hierarchy
- Section hierarchy
- Content relationships
- Interactive elements
- Landmark regions

The HTML structure should accurately represent the information architecture of the page.

---

# Mandatory Rules

Every implementation MUST:

- Use semantic HTML5.
- Maintain a correct heading hierarchy.
- Include one `<h1>` per page.
- Provide meaningful `alt` text for images.
- Assign a unique ID to every major section.
- Assign a unique section class to every major section.
- Avoid duplicate IDs.
- Use SEO-friendly IDs.
- Use stable anchor IDs.
- Build reusable HTML structures.
- Avoid unnecessary nesting.
- Maintain consistent button markup.
- Maintain consistent form markup.
- Support metadata requirements.
- Support favicon configuration.

These rules are mandatory across every project.

---

# HTML Engineering Principles

Every HTML document should satisfy the following principles.

## Semantic First

Always choose the most appropriate HTML element.

Examples:

```html
<header>

<nav>

<main>

<section>

<article>

<aside>

<footer>
```

Avoid replacing semantic elements with generic `<div>` elements unless no semantic alternative exists.

---

## Structure Before Styling

HTML should describe the structure of the content.

Never introduce elements solely for visual styling when the same result can be achieved through CSS.

The document structure should remain meaningful even when stylesheets are removed.

---

## Accessibility by Default

Every interactive element should be implemented with accessibility in mind from the beginning.

Semantic HTML is the first layer of accessibility.

Accessibility enhancements are covered in detail in Chapter 14.

---

## Reusability

HTML structures that appear repeatedly throughout the project should follow a consistent markup pattern.

Examples include:

- Cards
- Buttons
- Forms
- Navigation
- Hero sections
- Feature grids
- CTA sections

Developers should not invent new HTML structures for identical components.

---

# HTML Document Hierarchy

Every page should follow a predictable document hierarchy.

```
<html>

↓

<head>

↓

<body>

↓

<header>

↓

<main>

↓

<section>

↓

<footer>
```

This hierarchy should remain consistent across the project.

---

# Semantic Elements

Use semantic elements wherever appropriate.

Recommended landmark elements include:

- `<header>`
- `<nav>`
- `<main>`
- `<section>`
- `<article>`
- `<aside>`
- `<footer>`

Avoid overusing generic containers when semantic alternatives exist.

---

# Page Hierarchy

Every page should have:

- One primary heading (`<h1>`)
- Logical heading progression
- Clearly separated sections
- Consistent landmark regions

Heading levels should never be skipped without valid structural justification.

---
---

# Section Standards

## Purpose

Every page should be divided into logical, independent sections.

A section represents a meaningful block of content that can be maintained, styled, reused, tested, and navigated independently.

Each section should have a clear responsibility within the page.

---

## Mandatory Requirements

Every section MUST include:

- A unique ID
- A unique section class

Example:

```html
<section id="AboutSection" class="aboutSection">

    ...

</section>
```

These identifiers provide:

- Styling scope
- JavaScript targeting
- SEO anchor links
- Accessibility landmarks
- Reusability

---

## Section IDs

### Purpose

Section IDs uniquely identify each major content block.

They are used for:

- Anchor navigation
- JavaScript targeting
- Accessibility
- Browser navigation
- Deep linking

---

### Rules

Every section ID must be:

- Unique
- Stable
- Human-readable
- SEO-friendly
- Descriptive

Good examples:

```text
HeroSection

AboutSection

ServicesSection

TestimonialsSection

ContactSection

Footer
```

Avoid:

```text
section1

box

content

abc

newSection

temp

test
```

Never use duplicate IDs.

---

## Section Classes

Classes describe reusable styling.

Unlike IDs, classes may be reused where appropriate.

Section classes should clearly describe the purpose of the section.

Examples:

```text
heroSection

aboutSection

servicesSection

ctaSection

faqSection
```

Class names should remain consistent throughout the project.

---

# Heading Hierarchy

## Purpose

Headings communicate the information structure of the page.

Correct heading hierarchy improves:

- Accessibility
- SEO
- Readability
- Screen reader navigation

---

## Rules

Every page must contain:

Exactly one:

```
<h1>
```

Subsections should use:

```
<h2>

↓

<h3>

↓

<h4>
```

Heading levels should follow the logical structure of the content.

Avoid skipping heading levels unless there is a valid structural reason.

---

## Good Example

```html
<h1>About Us</h1>

<h2>Our Story</h2>

<h3>Company History</h3>
```

---

## Avoid

```html
<h1>About</h1>

<h4>History</h4>
```

---

# Image Standards

Every image should provide meaningful alternative text.

Purpose:

- Accessibility
- SEO
- Screen readers
- Better semantics

---

## Rules

Images must include:

```html
<img
    src="..."
    alt="Meaningful description">
```

Avoid:

```html
alt="image"

alt="photo"

alt=""
```

unless the image is purely decorative.

Decorative images should be handled appropriately according to accessibility requirements.

---

# Button Standards

Buttons should remain visually and structurally consistent throughout the project.

Consistency includes:

- Height
- Padding
- Border radius
- Typography
- Icon size
- Hover behaviour
- Focus behaviour

Every reusable button should share a common HTML structure.

Avoid creating multiple markup variations for identical button types.

---

# Form Standards

Form controls should remain consistent.

Maintain:

- Input height
- Border radius
- Font size
- Label positioning
- Icon positioning
- Error messaging
- Required indicators

Every form should follow the same markup structure throughout the project.

---

# Metadata Standards

Every page should support proper metadata.

Typical metadata includes:

- Page title
- Description
- Charset
- Viewport
- Theme color (if applicable)
- Open Graph tags (when required)
- Canonical URL (when required)

Metadata should be managed centrally whenever possible.

---

# Favicon Standards

Every project should include a properly configured favicon.

Recommended formats include:

- PNG
- ICO
- SVG (where supported)

Favicons should be referenced from the shared document shell rather than individual pages.

---

# Reusable HTML Patterns

Repeated UI structures should follow identical markup.

Examples include:

- Cards
- Buttons
- Feature lists
- CTA sections
- Navigation items
- Form groups

Consistency in markup simplifies:

- Styling
- JavaScript
- Maintenance
- Component reuse

Do not create different HTML structures for components that serve the same purpose.

---

# HTML Validation Checklist

Before completing a page verify:

## Document

- [ ] Semantic HTML5 used.
- [ ] One `<h1>` present.
- [ ] Correct heading hierarchy.
- [ ] `<main>` present.
- [ ] Landmark elements used appropriately.

---

## Sections

- [ ] Every section has a unique ID.
- [ ] Every section has a unique class.
- [ ] IDs are SEO-friendly.
- [ ] IDs are stable.
- [ ] No duplicate IDs.

---

## Images

- [ ] All images include meaningful `alt` text.
- [ ] Decorative images handled appropriately.
- [ ] Image markup remains consistent.

---

## Buttons

- [ ] Shared button structure used.
- [ ] Consistent sizing.
- [ ] Consistent typography.
- [ ] Accessible interaction states.

---

## Forms

- [ ] Consistent markup.
- [ ] Labels correctly associated.
- [ ] Inputs follow project standards.

---

## Metadata

- [ ] Page title verified.
- [ ] Meta description verified.
- [ ] Viewport present.
- [ ] Favicon configured.

---

# Common Mistakes

Avoid:

- Multiple `<h1>` elements.
- Duplicate IDs.
- Generic section names.
- Empty `alt` text for informative images.
- Deeply nested `<div>` structures.
- Styling-driven HTML.
- Multiple button markup patterns.
- Inconsistent form structures.
- Page-specific metadata duplicated across pages.

---

# Best Practices

- Write HTML for meaning, not appearance.
- Keep section structures predictable.
- Reuse established markup patterns.
- Prefer semantic elements over generic containers.
- Keep markup shallow and readable.
- Maintain consistency across every page.
- Validate HTML before beginning CSS.
- Build components with reuse in mind.

---

# Chapter Progress

Completed:

- ✅ Purpose
- ✅ Objective
- ✅ Engineering Philosophy
- ✅ Mandatory Rules
- ✅ Semantic HTML
- ✅ Document Hierarchy
- ✅ Page Hierarchy
- ✅ Section Standards
- ✅ Unique IDs
- ✅ Section Classes
- ✅ Heading Hierarchy
- ✅ Image Standards
- ✅ Button Standards
- ✅ Form Standards
- ✅ Metadata Standards
- ✅ Favicon Standards
- ✅ Reusable HTML Patterns
- ✅ HTML Validation Checklist
- ✅ Common Mistakes
- ✅ Best Practices

---
---

# HTML Architecture Principles

## Purpose

HTML architecture defines how markup should be organized to ensure every page remains maintainable, scalable, readable, and reusable.

HTML should communicate the structure of the page before CSS or JavaScript are considered.

Well-structured HTML simplifies:

- Styling
- JavaScript development
- Accessibility
- SEO
- CMS integration
- Long-term maintenance

---

# Structural Principles

Every HTML document should satisfy the following principles.

## Clear Hierarchy

The relationship between parent and child elements should be obvious.

Avoid deeply nested structures that make the document difficult to read.

Good hierarchy improves:

- Readability
- Maintainability
- Debugging

---

## Logical Grouping

Group related content together.

Examples:

- Hero content
- Card content
- Form controls
- Navigation items
- Footer links

Each group should represent a meaningful unit of information.

---

## Separation of Structure and Presentation

HTML defines meaning.

CSS defines appearance.

JavaScript defines behaviour.

Avoid introducing HTML elements solely for visual styling.

---

# Content Organization

Every page should present content in a logical reading order.

Recommended sequence:

```
Header

↓

Primary Navigation

↓

Hero

↓

Main Content

↓

Supporting Content

↓

Call To Action

↓

Footer
```

The reading order should remain meaningful even when CSS is disabled.

---

# Landmark Structure

Every page should provide recognizable landmark regions.

Typical landmarks include:

- Header
- Navigation
- Main Content
- Footer

Additional landmarks should only be introduced when they improve document semantics.

---

# Readability Standards

HTML should be written for developers as well as browsers.

Guidelines:

- Keep indentation consistent.
- Use meaningful element ordering.
- Group related markup.
- Avoid excessive nesting.
- Remove unnecessary wrapper elements.

Readable HTML reduces maintenance effort and improves collaboration.

---

# Reusability Standards

When a structure appears repeatedly throughout the project, reuse the established markup pattern.

Do not create alternative HTML structures for:

- Buttons
- Cards
- Feature items
- Navigation items
- Form controls
- CTA sections

Consistent markup enables:

- Shared styling
- Shared JavaScript
- Easier maintenance
- Faster development

---

# Scalability

HTML should support future project growth.

When creating new sections:

- Follow existing naming conventions.
- Follow existing structural patterns.
- Extend existing components whenever possible.
- Avoid introducing incompatible markup structures.

Every new page should integrate naturally into the existing project architecture.

---

# Maintainability

Future developers should be able to understand the document structure quickly.

Maintainability is improved by:

- Predictable hierarchy
- Consistent naming
- Reusable structures
- Minimal nesting
- Clear separation of concerns

---

# HTML Quality Assurance

Before considering a page complete, verify:

## Structure

- [ ] Semantic HTML5 used.
- [ ] Document hierarchy correct.
- [ ] Landmark elements used.
- [ ] Reading order preserved.

---

## Sections

- [ ] Unique IDs verified.
- [ ] Unique classes verified.
- [ ] Stable anchors verified.
- [ ] Section hierarchy verified.

---

## Accessibility

- [ ] Heading hierarchy correct.
- [ ] Images include meaningful `alt` text.
- [ ] Interactive elements use semantic HTML.

---

## Consistency

- [ ] Shared markup reused.
- [ ] Button structure consistent.
- [ ] Form structure consistent.
- [ ] Section structure consistent.

---

## Maintainability

- [ ] Markup is readable.
- [ ] No unnecessary nesting.
- [ ] Naming conventions followed.
- [ ] Reusable patterns preserved.

---

# Engineering Acceptance Criteria

A page satisfies the HTML standard only when:

- The document is semantic.
- Section hierarchy is logical.
- Landmark regions are correctly defined.
- Heading hierarchy is valid.
- Images provide appropriate alternative text.
- IDs are unique and stable.
- Reusable structures remain consistent.
- HTML is maintainable and scalable.

Meeting only some of these requirements is not sufficient.

Compliance with the complete HTML standard is required.

---

# Related Chapters

This chapter should be used together with:

- Chapter 04 – Project Architecture
- Chapter 05 – PHP Architecture
- Chapter 07 – CSS Standards
- Chapter 09 – SASS Architecture
- Chapter 12 – CMS Development
- Chapter 14 – Accessibility

These chapters collectively define the complete frontend implementation methodology.

---

# Chapter Summary

HTML is the structural foundation of every frontend project.

This chapter establishes the mandatory standards for creating semantic, reusable, accessible, and maintainable markup.

Following these standards ensures that every page remains:

- Predictable
- Scalable
- Consistent
- Readable
- Accessible
- Easy to maintain

These principles apply to every page, section, module, and component developed under this engineering handbook.

---