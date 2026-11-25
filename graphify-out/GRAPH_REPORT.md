# Graph Report - Frontend-Engineering-Handbook  (2026-11-02)

## Corpus Check
- 37 files · ~52,548 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 195 nodes · 310 edges · 11 communities
- Extraction: 85% EXTRACTED · 15% INFERRED · 0% AMBIGUOUS · INFERRED: 45 edges (avg confidence: 0.83)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- Global Build Rules
- Handbook Principles
- CSS & Component Reuse
- HTML Standards
- Responsive & AI Rules
- Smooth-Scroll Script
- SASS & JS Architecture
- Lighthouse & Sticky Header
- Project Architecture
- Header & Navigation
- Reference & Decisions

## God Nodes (most connected - your core abstractions)
1. `31 Global Build Rules` - 17 edges
2. `01 Introduction` - 15 edges
3. `03 Figma Standards` - 12 edges
4. `06 HTML Standards` - 10 edges
5. `11 Components` - 10 edges
6. `14 Accessibility` - 10 edges
7. `30 Laravel Project Standards` - 10 edges
8. `16 Header Standards` - 10 edges
9. `08 SASS Architecture` - 9 edges
10. `09 Responsive System` - 9 edges

## Surprising Connections (you probably didn't know these)
- `Development Lifecycle (12 steps)` --semantically_similar_to--> `Standard Development Workflow (9 phases)`  [INFERRED] [semantically similar]
  01-Introduction.md → 02-Core-Workflow.md
- `SASS Layer Structure (0-abstracts to 5-pages)` --implements--> `08 SASS Architecture`  [INFERRED]
  27-Reference-Implementations.md → 08-SASS-Architecture.md
- `Layer 4 Layouts` --conceptually_related_to--> `16 Header Standards`  [INFERRED]
  08-SASS-Architecture.md → 16-Header-Standards.md
- `Image Attribute Decisions (never lazy-load hero)` --conceptually_related_to--> `24 AI Development Rules`  [INFERRED]
  28-Engineering-Decisions.md → 24-AI-Development-Rules.md
- `Figma is the Single Source of Truth` --semantically_similar_to--> `Figma as Engineering Specification`  [INFERRED] [semantically similar]
  01-Introduction.md → 03-Figma-Standards.md

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **PHP Page Assembly Flow (main.php, header.php, pageWrapper, footer.php)** — 04_project_architecture_main_php, 04_project_architecture_header_php, 04_project_architecture_pagewrapper, 04_project_architecture_footer_php [EXTRACTED 1.00]
- **SASS ITCSS Layer Stack** — 08_sass_architecture_abstracts_layer, 08_sass_architecture_base_layer, 08_sass_architecture_plugins_layer, 08_sass_architecture_modules_layer, 08_sass_architecture_layouts_layer, 08_sass_architecture_pages_layer [EXTRACTED 1.00]
- **Validation pipeline: Browser QA, Figma Validation, Final QA, Delivery** — 19_browser_qa, 20_figma_validation, 21_final_qa, 22_delivery [EXTRACTED 1.00]
- **Browser QA, Figma Validation, Final QA verification pipeline** — 23_new_project_checklist_startup_workflow, 20_figma_validation, frontend_qa_test, 19_browser_qa, 21_final_qa [INFERRED 0.85]
- **Consolidated reference chapters (Common Mistakes, Best Practices, Reference Implementations, Engineering Decisions)** — 25_common_mistakes, 26_best_practices, 27_reference_implementations, 28_engineering_decisions [INFERRED 0.85]
- **Scroll-driven motion rules** — 16_header_standards_sticky_header_animation, 31_global_build_rules_scroll_animations, 31_global_build_rules_statistics_counter, 31_global_build_rules_curved_object_keyframes [INFERRED 0.75]
- **QA workflow documents** — claude_qa_testing_trigger, frontend_qa_test, frontend_qa_test_qa_report, 31_global_build_rules_overlap_detection [INFERRED 0.85]

## Communities (11 total, 0 thin omitted)

### Community 0 - "Global Build Rules"
Cohesion: 0.09
Nodes (28): 31 Global Build Rules, Button and Link Hover, Keyframe Animation on Small Curved Objects, Accessible Dropdown Menu, Favicon Check, Flipped Images Rule, Hero Slider (video + image), Image Sizing and Cropping (+20 more)

### Community 1 - "Handbook Principles"
Cohesion: 0.10
Nodes (21): 01 Introduction, Development Lifecycle (12 steps), MUST / SHOULD / MAY Terminology, Pixel-Perfect Accuracy, Handbook Semantic Versioning, 02 Core Workflow, Phase 3 Asset Extraction, Delivery: stop after approved scope (+13 more)

### Community 2 - "CSS & Component Reuse"
Cohesion: 0.11
Nodes (25): Shared Component vs Page Component, Reusable HTML Patterns (buttons, forms, cards), 07 CSS Standards, Avoid !important, CSS Variables Reuse, No Duplicate CSS, 08 SASS Architecture, Layer 0 Abstracts (+17 more)

### Community 3 - "HTML Standards"
Cohesion: 0.15
Nodes (15): 06 HTML Standards, Heading Hierarchy (one H1), Image Alt Text Standard, Metadata and Favicon Standards, Semantic HTML5 and Landmarks, No Inline CSS, Component Independence, 12 CMS Development (+7 more)

### Community 4 - "Responsive & AI Rules"
Cohesion: 0.15
Nodes (16): Design-scale variable --u (one Figma px), Standard Breakpoints and Containers Table, 24 AI Development Rules, AI Instruction Priority Order, 29 Next.js Project Standards, Client boundaries: no use client on sections, Page-local local_data pattern, Mandatory Next.js Setup Rules (12) (+8 more)

### Community 5 - "Smooth-Scroll Script"
Cohesion: 0.23
Nodes (14): b(), C(), H(), j(), L(), M(), N(), p() (+6 more)

### Community 6 - "SASS & JS Architecture"
Cohesion: 0.13
Nodes (15): app.sass (shared bundle entry), Directory Index Files (import chain rule), pages.sass (page bundle entry), Two Bundle Strategy (app.css + pages.css), 13 JavaScript Standards, Page-specific JS scoped via pageWrapper, Shared logic in assets/js/app.js, 15 Performance (+7 more)

### Community 7 - "Lighthouse & Sticky Header"
Cohesion: 0.22
Nodes (11): Smooth Scrolling (smoothscroll.js, required), Lighthouse 100 Target, 19 Browser QA, 20 Figma Validation, Figma Validation Workflow (5 steps), 21 Final QA, Final QA Release Gate, 22 Delivery (+3 more)

### Community 8 - "Project Architecture"
Cohesion: 0.23
Nodes (11): 04 Project Architecture, AI Configuration Files (AGENTS.md, CLAUDE.md), includes/footer.php, includes/header.php, main.php (application shell), pageWrapper (scoped page class), Shared Layout Pattern (main, header, pageWrapper, footer), Standard Project Directory Structure (+3 more)

### Community 9 - "Header & Navigation"
Cohesion: 0.25
Nodes (9): 16 Header Standards, Header Positioning, Header-Hero Relationship, Shared Header Component, 17 Navigation Standards, Dropdown Navigation, Mobile Navigation and Hamburger Menu, Navigation Types (primary, secondary, mobile, footer, utility, breadcrumb) (+1 more)

### Community 10 - "Reference & Decisions"
Cohesion: 0.22
Nodes (9): 27 Reference Implementations, CMS Rich Text Wrapper Styling, Page Wrapper (main#pageWrapper), SASS Layer Structure (0-abstracts to 5-pages), 28 Engineering Decisions, Container Width Decisions (576-540 ... 1920-1680), Image Attribute Decisions (never lazy-load hero), Naming Decisions (kebab-case IDs, camelCase classes) (+1 more)

## Knowledge Gaps
- **53 isolated node(s):** `MUST / SHOULD / MAY Terminology`, `Handbook Semantic Versioning`, `Delivery: stop after approved scope`, `Design Inspection Workflow`, `Asset Format Hierarchy (SVG, AVIF, WebP, PNG, JPEG)` (+48 more)
  These have ≤1 connection - possible missing edges or undocumented components. (Counts symbols only; 62 node(s) total have ≤1 connection when file, concept and rationale nodes are included.)

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `16 Header Standards` connect `Header & Navigation` to `Project Architecture`, `Global Build Rules`, `CSS & Component Reuse`, `Lighthouse & Sticky Header`?**
  _High betweenness centrality (0.195) - this node is a cross-community bridge._
- **What connects `MUST / SHOULD / MAY Terminology`, `Handbook Semantic Versioning`, `Delivery: stop after approved scope` to the rest of the system?**
  _53 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Global Build Rules` be split into smaller, more focused modules?**
  _Cohesion score 0.08994708994708994 - nodes in this community are weakly interconnected._
- **Why does `17 Navigation Standards` connect `Header & Navigation` to `CSS & Component Reuse`, `HTML Standards`, `SASS & JS Architecture`?**
  _High betweenness centrality (0.142) - this node is a cross-community bridge._
- **Should `Handbook Principles` be split into smaller, more focused modules?**
  _Cohesion score 0.09538461538461539 - nodes in this community are weakly interconnected._
- **Why does `31 Global Build Rules` connect `Global Build Rules` to `Header & Navigation`, `Lighthouse & Sticky Header`?**
  _High betweenness centrality (0.140) - this node is a cross-community bridge._
- **Should `CSS & Component Reuse` be split into smaller, more focused modules?**
  _Cohesion score 0.11384615384615385 - nodes in this community are weakly interconnected._