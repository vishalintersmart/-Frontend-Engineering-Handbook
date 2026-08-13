# 27 – Reference Implementations

> **Status:** Engineering Reference Manual
>
> **Applies To:** Every frontend project using this handbook.
>
> **Related Chapters**
>
> - Chapters 01–26

---

# Purpose

This chapter provides canonical reference implementations for the engineering standards defined throughout this handbook.

The examples demonstrate how architecture, HTML, SASS, JavaScript, CMS integration, responsive behaviour, and quality assurance should be implemented in practice.

These examples are references—not templates that must be copied verbatim.

Developers should adapt them while preserving the engineering standards defined throughout this handbook.

---

# Contents

1. Project Structure

2. PHP Structure

3. HTML Template

4. Page Wrapper

5. Section Template

6. Hero Section

7. Button Component

8. Form Component

9. Card Component

10. CMS Wrapper

11. Rich Text Wrapper

12. Header Structure

13. Footer Structure

14. Navigation Structure

15. SASS Structure

16. app.sass

17. pages.sass

18. Directory Index Files

19. Design Tokens

20. Responsive Mixins

21. Container System

22. JavaScript Structure

23. Shared JS

24. Page JS

25. Browser QA Template

26. Figma Validation Template

27. Final QA Template

28. New Project Template

---

# 1. Standard Project Structure

```text
project/

│

├── assets/

│   ├── css/

│   ├── js/

│   ├── sass/

│   ├── fonts/

│   ├── images/

│   └── icons/

│

├── includes/

│

├── pages/

│

├── index.php

│

└── README.md
```

---

# 2. Standard PHP Structure

```php
<?php

$page = "home";

include('includes/header.php');

?>

<main id="pageWrapper" class="homePage">

</main>

<?php

include('includes/footer.php');

?>
```

---

# 3. Standard HTML Section

```html
<section
    id="AboutUs"
    class="aboutSection">

    <div class="container">

        <div class="sectionContent">

        </div>

    </div>

</section>
```

---

# 4. Page Wrapper

```html
<main
    id="pageWrapper"
    class="aboutPage">

</main>
```

Page-specific JavaScript and SASS should scope from this wrapper.

---

# 5. Hero Structure

```html
<section
    id="home-hero"
    class="heroSection">

    <div class="container">

        <div class="heroContent">

        </div>

    </div>

</section>
```

---

# 6. Button Component

```html
<a
    href="#"
    class="btnPrimary">

    Learn More

</a>
```

Shared styling belongs inside Modules.

---

# 7. Form Component

```html
<form>

    <input>

    <textarea>

    <button>

</form>
```

Maintain shared sizing and spacing throughout the project.

---

# 8. Card Component

```html
<article class="card">

    <figure>

    </figure>

    <div class="cardContent">

    </div>

</article>
```

---

# 9. CMS Wrapper

```html
<div class="ContentWrp">

    {{ Rich Text }}

</div>
```

---

# 10. Rich Text Styling

```sass
.content-wrp

    p

    h2

    h3

    ul

    ol

    li
```

Never style CMS-generated elements directly.

---

# 11. Header Structure

```html
<header>

</header>
```

The header should remain part of the shared layout.

---

# 12. Navigation

```html
<nav>

    <ul>

        <li>

            <a>

```

Maintain semantic navigation.

---

# 13. Footer

```html
<footer>

</footer>
```

---

# 14. Standard SASS Structure

```text
sass/

0-abstracts/

1-base/

2-plugins/

3-modules/

4-layouts/

5-pages/

app.sass

pages.sass
```

---

# 15. app.sass

```sass
@use "0-abstracts/abstracts-dir"

@use "1-base/base-dir"

@use "2-plugins/plugins-dir"

@use "3-modules/modules-dir"

@use "4-layouts/layouts-dir"
```

---

# 16. pages.sass

```sass
@use "5-pages/pages-dir"
```

---

# 17. Directory File

```sass
@forward "buttons"

@forward "cards"

@forward "forms"
```

---

# 18. Design Tokens

```sass
$clr-primary

$clr-heading

$space-section

$radius-md

$shadow-card
```

---

# 19. Responsive Mixins

```sass
@include tablet

@include mobile
```

Use the project's approved responsive system.

---

# 20. Container

```html
<div class="container">

</div>
```

---

# 21. Shared JavaScript

```javascript
assets/js/app.js
```

Shared functionality belongs here.

---

# 22. Page JavaScript

```javascript
if(pageWrapper.classList.contains('aboutPage'))
{

}
```

---

# 23. Browser QA Template

```text
Launch

↓

Desktop

↓

Tablet

↓

Mobile

↓

Compare

↓

Fix

↓

Approve
```

---

# 24. Figma Validation Template

```text
Section

↓

Typography

↓

Spacing

↓

Colors

↓

Images

↓

Components

↓

Approve
```

---

# 25. Final QA Template

```text
Architecture

↓

Implementation

↓

Performance

↓

Browser QA

↓

Figma Validation

↓

Delivery
```

---

# 26. New Project Workflow

```text
Requirements

↓

Figma

↓

Assets

↓

Architecture

↓

Development

↓

QA

↓

Delivery
```

---

# Universal Engineering Principles

Every implementation should:

- Follow the handbook.
- Preserve architecture.
- Match Figma.
- Reuse components.
- Reuse Design Tokens.
- Remain responsive.
- Remain performant.
- Remain maintainable.
- Remain CMS-safe.
- Pass Browser QA.
- Pass Final QA.

---

# Engineering Reference

Whenever uncertainty exists:

1. Follow the handbook.

2. Follow the existing architecture.

3. Follow the approved Figma design.

4. Prefer reuse over duplication.

5. Validate before delivery.

---

# Chapter Summary

The Reference Implementations chapter serves as the practical companion to the engineering standards defined throughout this handbook.

Rather than introducing new engineering rules, it demonstrates how those rules should be applied consistently across real frontend projects.

Together with the previous chapters, it completes the Frontend Engineering Handbook and provides developers with a complete reference for planning, implementing, validating, and delivering production-ready frontend applications.

---