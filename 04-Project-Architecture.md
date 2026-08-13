# 04 – Project Architecture

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** Every frontend project built using this handbook.
>
> **Related Chapters**
>
> - 02 Core Workflow
> - 05 PHP Architecture
> - 07 HTML Standards
> - 09 SASS Architecture
> - 11 Components

---

# Purpose

Project Architecture defines the structural foundation of every frontend project.

A well-defined architecture ensures that every developer organizes files, components, assets, layouts, and page structures consistently across the entire project.

Consistency in architecture improves:

- Maintainability
- Scalability
- Code reuse
- Team collaboration
- Future development
- Debugging
- Performance optimization

This chapter establishes the mandatory folder structure, project organization, and architectural principles that every project must follow.

---

# Objective

Every new project should begin with a predictable structure.

Developers should never invent their own project organization.

Instead, projects should follow the standardized architecture defined within this handbook.

This allows every developer to immediately understand:

- where files belong
- how pages are built
- where reusable code lives
- where page-specific code lives
- how assets are organized

---

# Engineering Philosophy

Project architecture should remain stable throughout the lifetime of the project.

A stable architecture reduces:

- duplicated code
- inconsistent file placement
- maintenance effort
- onboarding time
- regression risks

Architecture should evolve only when there is a clear engineering benefit.

Individual developer preference should never determine project structure.

---

# Architectural Principles

Every project should be designed around the following principles.

## Reusability

Shared functionality should exist only once.

Examples include:

- Header
- Footer
- Navigation
- Buttons
- Cards
- Shared Sections
- Shared JavaScript
- Shared Styling

Duplicating shared components across pages is not permitted.

---

## Separation of Responsibilities

Each file should have a clearly defined responsibility.

Examples:

main.php

Responsible for:

- document shell
- head
- shared resources
- body initialization

header.php

Responsible for:

- site header
- navigation
- opening layout structure

footer.php

Responsible for:

- footer
- global scripts
- closing document structure

Page files

Responsible only for:

- page content

No page should redefine shared project architecture.

---

## Scalability

The architecture should support:

- additional pages
- new layouts
- new modules
- CMS integration
- future redesigns

without requiring structural changes.

---

## Predictability

Every developer should be able to locate project files without searching the repository.

The location of every major resource should be obvious from the architecture itself.

---

# Standard Project Structure

Every project should follow the same high-level organization.

```text
project-root/

main.php

includes/

assets/

pages/

404.php

configuration

documentation
```

The exact project may contain additional folders, but the overall architecture should remain consistent.

---

# Root Directory

The project root contains the files required to initialize the application.

Typical contents include:

- application entry files
- shared templates
- assets
- configuration
- documentation

The root should remain uncluttered.

Temporary files should never be stored here.

---

# Includes Directory

The Includes directory contains reusable structural templates.

Examples include:

- Header
- Footer
- Navigation
- Shared Layout Fragments

Files inside this directory should never contain page-specific content.

---

# Assets Directory

The Assets directory contains all frontend resources.

Typical categories include:

- SASS
- CSS
- JavaScript
- Images
- Fonts
- Videos
- Icons
- Favicons

Assets should be organized into logical subdirectories.

---

# Page Files

Each page should exist as an individual entry file.

Page files should remain lightweight.

Their responsibility is to assemble reusable project components and define page-specific content.

They should never duplicate:

- Header
- Footer
- Shared navigation
- Shared modules
- Shared scripts

---

# Shared Architecture

Every reusable element should exist in one location only.

Shared architecture includes:

- layouts
- navigation
- global styles
- shared JavaScript
- reusable modules
- utilities

Shared architecture should be extended rather than duplicated.

---

# Architecture Goals

A successful architecture should provide:

- consistency
- scalability
- maintainability
- reusability
- readability
- modularity
- predictable organization

These goals should guide every architectural decision throughout the project.

---
---

# Standard Project Directory Structure

Every frontend project should follow a predictable directory structure.

The objective is to separate responsibilities, maximize reusability, and minimize maintenance effort.

```text
project-root/
│
├── main.php
├── includes/
│   ├── header.php
│   └── footer.php
│
├── [page-name].php
├── 404.php
│
├── assets/
│   ├── sass/
│   ├── css/
│   ├── js/
│   ├── images/
│   ├── fonts/
│   ├── videos/
│   └── favicon.png
│
├── .agents/
│   └── AGENTS.md
│
├── CLAUDE.md
└── site.webmanifest
```

The structure should remain consistent across every project.

Do not reorganize folders based on personal preference.

---

# Root Level Responsibilities

The project root contains only files required to initialize or configure the application.

Allowed:

- Main application entry
- Shared configuration
- Shared templates
- Documentation
- Manifest files

Avoid placing:

- Random images
- Temporary files
- Downloads
- Backups
- Experimental code

The project root should remain clean and predictable.

---

# main.php

## Purpose

`main.php` acts as the application shell.

Every page begins here.

---

## Responsibilities

main.php is responsible for:

- Document declaration
- HTML opening
- `<head>`
- Global meta tags
- Shared CSS
- Shared JavaScript references
- Global resources
- Opening `<body>`
- Loading the shared header
- Opening the application layout

---

## main.php SHOULD NOT

Contain:

- Page-specific content
- Page-specific JavaScript
- Page-specific styling
- Business logic

Its purpose is to provide a common shell shared by every page.

---

# Includes Directory

## Purpose

The `includes/` directory contains reusable structural templates shared across the project.

Typical files include:

```text
includes/

header.php

footer.php
```

Additional shared fragments may also exist when required.

---

# header.php

Responsible for:

- Header markup
- Desktop navigation
- Mobile navigation
- Shared announcement bars
- Search UI
- Global navigation components

Should not contain:

- Page-specific hero sections
- Page-specific banners
- Page-specific JavaScript

---

# footer.php

Responsible for:

- Footer markup
- Footer navigation
- Copyright
- Global JavaScript
- Closing wrappers
- Closing HTML tags

Should not contain:

- Page-specific components
- Page-specific scripts
- Inline page functionality

---

# Page Files

Every page should remain lightweight.

Example:

```php
<?php include "main.php"; ?>

<div id="pageWrapper" class="aboutPage">

    <!-- Page Content -->

</div>

<?php include "./includes/footer.php"; ?>
```

Each page exists only to assemble:

- Shared layout
- Shared components
- Page-specific content

Nothing more.

---

# Page Responsibilities

Each page file is responsible only for:

- Page wrapper
- Page content
- Page-specific stylesheet reference (if required)
- Page-specific JavaScript initialization (if required)

Everything else belongs to shared architecture.

---

# pageWrapper

Every page must contain a single wrapper.

Example:

```html
<div id="pageWrapper" class="contactPage">
```

Purpose:

- Scope page styles
- Scope page JavaScript
- Prevent CSS leakage
- Prevent component conflicts

Every page receives its own wrapper class.

Examples:

```text
homePage

aboutPage

contactPage

legalPage

errorPage
```

Page wrapper classes should follow a predictable naming convention.

---

# Shared Layout Pattern

Every page follows the same assembly pattern.

```text
main.php

↓

header.php

↓

pageWrapper

↓

page content

↓

footer.php
```

No page should bypass this sequence.

---

# 404 Page

The 404 page follows the same project architecture.

It may introduce:

- Different wrapper class
- Simplified layout
- Unique styling

However, it should still reuse:

- Shared header (if applicable)
- Shared footer (if applicable)
- Shared resources
- Shared CSS architecture

---

# Assets Responsibilities

The Assets directory contains all frontend resources.

Responsibilities are divided by category.

## SASS

Source styling.

---

## CSS

Compiled styling.

---

## JavaScript

Shared and page-specific scripts.

---

## Images

Raster graphics.

---

## Fonts

Project fonts.

---

## Videos

Optimized media.

---

## Favicons

Browser icons.

Each asset category should remain isolated from the others.

---

# AI Configuration Files

Projects may contain documentation files used by AI development assistants.

Examples:

```text
.agents/

AGENTS.md

CLAUDE.md
```

These documents define project-specific engineering rules for AI-assisted development.

They are part of the development workflow and should remain synchronized with this handbook whenever applicable.

---

# Architectural Validation Checklist

Before development begins verify:

- [ ] Folder structure created.
- [ ] Includes directory configured.
- [ ] Assets directory organized.
- [ ] main.php created.
- [ ] header.php created.
- [ ] footer.php created.
- [ ] Page wrapper implemented.
- [ ] Page naming conventions followed.
- [ ] Shared architecture identified.
- [ ] Project documentation available.

---

# Common Mistakes

Avoid:

- Duplicating header markup.
- Duplicating footer markup.
- Mixing shared and page-specific code.
- Storing page assets in shared folders without purpose.
- Creating multiple page wrappers.
- Placing business logic inside templates.
- Overloading main.php with page-specific functionality.
- Breaking the include hierarchy.
- Inconsistent page naming.
- Adding unrelated files to the project root.

---

# Best Practices

- Keep page files as small as possible.
- Centralize shared functionality.
- Isolate responsibilities.
- Extend the existing architecture rather than replacing it.
- Keep the root directory clean.
- Organize assets consistently.
- Scope every page using a dedicated wrapper class.
- Review architecture before creating new folders or components.

---

# Chapter Summary

Project Architecture defines the structural backbone of every frontend project.

Following this architecture ensures:

- Consistency
- Scalability
- Reusability
- Predictability
- Easier onboarding
- Reduced maintenance effort
- Cleaner separation of responsibilities

Every subsequent chapter in this handbook builds upon the architectural principles established here.

---