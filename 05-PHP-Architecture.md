# 05 – PHP Architecture

> **Status:** Mandatory Engineering Standard
>
> **Applies To:** PHP-based frontend projects following this handbook.
>
> **Related Chapters**
>
> - 02 Core Workflow
> - 04 Project Architecture
> - 07 HTML Standards
> - 09 SASS Architecture

---

# Purpose

This chapter defines the PHP architecture used to assemble frontend pages.

PHP is **not** used as the application layer.

Instead, PHP acts as the page assembly engine responsible for composing reusable frontend components into complete pages.

The objective is to maximize reuse while minimizing duplicated markup.

---

# Objective

Every page should be assembled using shared templates.

Developers should never duplicate:

- Header
- Footer
- Navigation
- Global resources
- Document shell

Only page-specific content should exist inside page files.

---

# Engineering Philosophy

Pages should remain extremely lightweight.

PHP exists to assemble reusable frontend components.

Business logic should not be mixed with presentation.

Every page should follow the same predictable lifecycle.

---

# Page Lifecycle

Every request should follow the same sequence.

```
Browser Request

↓

Page File

↓

main.php

↓

<header>

↓

Page Wrapper

↓

Page Content

↓

footer.php

↓

Response
```

Every page follows this identical lifecycle.

---

# Page Assembly Pattern

The standard page assembly sequence is:

```
Page Request

↓

Load main.php

↓

Load Shared Header

↓

Open Page Wrapper

↓

Render Page Content

↓

Load Shared Footer

↓

Close Document
```

No page should bypass this sequence.

---

# main.php

## Purpose

`main.php` provides the common application shell shared across all pages.

It should be considered the bootstrap template for frontend rendering.

---

## Responsibilities

`main.php` is responsible for:

- HTML document declaration
- Opening `<html>`
- Opening `<head>`
- Global meta tags
- Shared stylesheets
- Shared JavaScript references
- Opening `<body>`
- Loading `header.php`

It prepares the environment required by every page.

---

## Prohibited Responsibilities

`main.php` must not contain:

- Page-specific HTML
- Page-specific styles
- Page-specific JavaScript
- Individual page layouts
- Business logic

Its responsibility is infrastructure—not content.

---

# header.php

## Purpose

Provides the reusable site header.

---

## Responsibilities

Includes:

- Desktop navigation
- Mobile navigation
- Header utilities
- Shared branding
- Opening layout wrappers (if required)

Every page should receive the same header implementation.

---

## Should Not Contain

- Hero banners
- Page titles
- Breadcrumbs
- Page-specific components
- Page-specific JavaScript

---

# footer.php

## Purpose

Provides the reusable site footer and closes the application layout.

---

## Responsibilities

Includes:

- Footer markup
- Footer navigation
- Global scripts
- Closing layout wrappers
- Closing `body`
- Closing `html`

---

## Should Not Contain

- Page-specific content
- Page-specific scripts
- Temporary debugging code

---

# Page Files

Each page exists only to provide its own content.

Example:

```php
<?php include "main.php"; ?>

<div id="pageWrapper" class="aboutPage">

    <!-- Page Content -->

</div>

<?php include "./includes/footer.php"; ?>
```

The page should remain as small as possible.

---

# Page Wrapper

Every page must contain one wrapper.

```html
<div id="pageWrapper" class="contactPage">
```

Purpose:

- Scope CSS
- Scope JavaScript
- Prevent style leakage
- Prevent selector conflicts
- Enable page-specific overrides

Every page receives a unique wrapper class.

---

# Page Responsibilities

Each page is responsible only for:

- Wrapper
- Page sections
- Page-specific stylesheet (if required)
- Page-specific JavaScript initialization (if required)

Everything else belongs to shared architecture.

---

# Include Hierarchy

Always follow:

```
main.php

↓

header.php

↓

pageWrapper

↓

Page Content

↓

footer.php
```

Changing this hierarchy is not permitted unless the project architecture explicitly requires it.

---

# Reusability Principles

Shared content belongs inside:

- includes/
- layouts/
- modules/

Page files should never duplicate shared markup.

If multiple pages require identical content, convert it into a reusable include or shared module.

---

# Validation Checklist

Before implementation verify:

- [ ] main.php exists.
- [ ] header.php exists.
- [ ] footer.php exists.
- [ ] Include hierarchy followed.
- [ ] Single page wrapper used.
- [ ] Unique page class applied.
- [ ] Shared templates reused.
- [ ] Page remains lightweight.

---

# Common Mistakes

Avoid:

- Multiple page wrappers.
- Duplicating headers.
- Duplicating footers.
- Inline business logic.
- Page-specific code inside shared templates.
- Shared code inside page files.
- Breaking the include sequence.
- Inconsistent wrapper classes.

---

# Best Practices

- Keep page files extremely small.
- Centralize shared markup.
- Reuse templates.
- Scope page-specific behaviour through `pageWrapper`.
- Keep responsibilities isolated.
- Preserve predictable architecture.

---