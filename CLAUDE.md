# Global Frontend Engineering Instructions

These instructions apply to every project.

## Coding Standards

Read and follow the guidance from:

"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\01-Introduction.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\02-Core-Workflow.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\03-Figma-Standards.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\04-Project-Architecture.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\05-PHP-Architecture.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\06-HTML-Standards.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\07-CSS-Standards.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\08-SASS-Architecture.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\09-Responsive-System.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\10-Design-Tokens.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\11-Components.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\12-CMS-Development.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\13-JavaScript-Standards.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\14-Accessibility.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\15-Performance.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\16-Header-Standards.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\17-Navigation.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\18-Slider-Standards.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\19-Browser-QA.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\20-Figma-Validation.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\21-Final-QA.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\22-Delivery.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\23-New-Project-Checklist.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\24-AI-Development-Rules.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\25-Common-Mistakes.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\26-Best-Practices.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\27-Reference-Implementations.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\28-Engineering-Decisions.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\29-NextJS-Project-Standards.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\CHANGELOG.md"
"D:\wamp\www\AI_Build\Frontend-Engineering-Handbook\README.md"

Always:

- Produce production-ready code.
- Prioritize performance and accessibility.
- Follow semantic HTML.
- Preserve existing project architecture.
- Avoid unnecessary dependencies.


# RESPONSIVE DEVELOPMENT

Every implementation must follow the project's standard responsive container system.

Use the following breakpoints and container widths unless the project explicitly defines a different system.

## Breakpoints & Containers

| Breakpoint | Container Max Width |
|------------|--------------------:|
| 0px        | Fluid (100%)        |
| 576px      | 540px               |
| 768px      | 720px               |
| 992px      | 960px               |
| 1200px     | 1140px              |
| 1440px     | 1320px              |
| 1600px     | 1480px              |
| 1920px     | 1680px              |

Reference CSS:

```css
.container {
    width: 100%;
    margin-inline: auto;
    padding-inline: 16px;
}

@media (min-width: 576px) {
    .container {
        max-width: 540px;
    }
}

@media (min-width: 768px) {
    .container {
        max-width: 720px;
    }
}

@media (min-width: 992px) {
    .container {
        max-width: 960px;
    }
}

@media (min-width: 1200px) {
    .container {
        max-width: 1140px;
    }
}

@media (min-width: 1440px) {
    .container {
        max-width: 1320px;
    }
}

@media (min-width: 1600px) {
    .container {
        max-width: 1480px;
    }
}

@media (min-width: 1920px) {
    .container {
        max-width: 1680px;
    }
}
```

Rules:

- Use the standard `.container` class throughout the project.
- Do not create multiple container systems unless explicitly required.
- Keep horizontal padding consistent across all pages.
- Build responsive layouts around these breakpoints.
- Do not introduce arbitrary breakpoint values without project approval.
- Validate layouts on Desktop, Laptop, Tablet, and Mobile before considering a task complete.
- Implement breakpoints and the container system using plain, literal
  `@media (min-width: …)` queries written directly wherever needed — exactly
  as shown in the reference CSS above. Do not wrap them in a SASS
  breakpoint mixin (e.g. `@include respond(...)`) and do not store the
  breakpoint/container pixel values in SASS variables. Write the numbers
  inline every time.

# SLIDERS / CAROUSELS

- Do not manually set `overflow` on a slider library's track element (e.g.
  Splide's `.splide__track`). Let the plugin's own core CSS handle clipping;
  only override plugin styles for properties the approved design actually
  requires changing.

# SECTION SPACING

Maintain consistent vertical rhythm throughout the project.

- Reuse the project's section spacing system.
- Adjacent sections should use consistent spacing.
- Avoid assigning unique spacing values to individual sections unless required by the design.
- Section spacing should scale proportionally across responsive breakpoints.