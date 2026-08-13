# 23 – New Project Checklist

> **Status:** Mandatory Engineering Workflow
>
> **Applies To:** Every new frontend project before implementation begins.
>
> **Related Chapters**
>
> - Chapters 01–22

---

# Purpose

This chapter defines the official project startup workflow for every frontend project.

Rather than introducing new engineering standards, it provides the correct sequence for applying the standards already established throughout this handbook.

Every new project should begin by following this checklist.

---

# Objective

The objective is to ensure that every project starts with:

- A clear understanding of requirements
- A consistent architecture
- Proper planning
- Reduced implementation mistakes
- Predictable development workflow

Good planning reduces engineering defects later in the project.

---

# Engineering Philosophy

Most implementation mistakes occur before development begins.

Proper preparation is therefore considered part of the engineering process.

No development should begin until the planning phase has been completed.

---

# Project Startup Workflow

Every project should follow the same sequence.

```text
Project Received

↓

Requirement Review

↓

Figma Review

↓

Architecture Setup

↓

Asset Preparation

↓

CMS Planning

↓

Development

↓

Browser QA

↓

Figma Validation

↓

Final QA

↓

Delivery
```

This workflow should remain consistent across all projects.

---

# Phase 1 — Requirement Review

Before opening the design:

Verify:

- [ ] Project scope received.
- [ ] Required pages identified.
- [ ] Required functionality understood.
- [ ] Third-party integrations identified.
- [ ] CMS requirements discussed (if applicable).

Do not begin implementation until the project scope is understood.

---

# Phase 2 — Figma Review

Review the approved Figma design.

Verify:

- [ ] Correct design file.
- [ ] Correct page.
- [ ] Responsive designs available.
- [ ] Shared components identified.
- [ ] Header behaviour reviewed.
- [ ] Navigation reviewed.
- [ ] Slider behaviour reviewed.
- [ ] Animation requirements reviewed.

Do not estimate missing design details.

Clarify uncertainties before implementation.

---

# Phase 3 — Asset Preparation

Identify and prepare all required assets.

Verify:

- [ ] Logos exported.
- [ ] Icons exported.
- [ ] Images exported.
- [ ] SVGs exported.
- [ ] Background graphics exported.
- [ ] Assets optimized.
- [ ] Folder structure prepared.

---

# Phase 4 — Project Architecture

Create the approved project structure.

Verify:

- [ ] Root structure created.
- [ ] Includes directory created.
- [ ] Assets directory created.
- [ ] SASS architecture created.
- [ ] JavaScript structure created.
- [ ] Documentation added (if required).

---

# Phase 5 — Page Planning

Before coding each page:

Verify:

- [ ] Shared components identified.
- [ ] Page-specific components identified.
- [ ] Section order confirmed.
- [ ] Heading hierarchy planned.
- [ ] Page wrapper defined.

---

# Phase 6 — CMS Planning

If the project uses a CMS:

Verify:

- [ ] Editable fields confirmed.
- [ ] Rich Text fields confirmed.
- [ ] Repeater fields confirmed.
- [ ] Wrapper-based styling planned.
- [ ] Decorative icons implemented with pseudo-elements.

If the project does not use a CMS, this phase may be skipped.

---

# Phase 7 — Responsive Planning

Before writing CSS:

Verify:

- [ ] Standard container system confirmed
- [ ] Breakpoint system confirmed
- [ ] Typography scale available.
- [ ] Spacing scale available.
- [ ] Responsive strategy understood.

---

# Phase 8 — Performance Planning

Before implementation:

Verify:

- [ ] Hero media identified.
- [ ] Lazy-load strategy planned.
- [ ] Image dimensions available.
- [ ] Performance goals understood.
- [ ] Lighthouse target acknowledged.

Performance planning should occur before coding begins.

---

# Phase 9 — Development

During implementation verify:

- [ ] Shared architecture reused.
- [ ] Components reused.
- [ ] Design Tokens reused.
- [ ] JavaScript architecture followed.
- [ ] CMS standards followed (if applicable).

Development should follow the engineering standards defined throughout this handbook.

---

# Phase 10 — Continuous Validation

After completing every section:

- [ ] Browser QA completed.
- [ ] Desktop screenshot captured.
- [ ] Tablet screenshot captured.
- [ ] Mobile screenshot captured.
- [ ] Compared against Figma.
- [ ] Differences corrected.

Do not continue until the completed section passes validation.

---

# Phase 11 — Project Verification

Before release verify:

- [ ] Browser QA passed.
- [ ] Figma Validation passed.
- [ ] Final QA passed.
- [ ] Performance reviewed.
- [ ] Accessibility reviewed.
- [ ] Responsive validation completed.

---

# Phase 12 — Delivery

Before handover verify:

- [ ] Project approved.
- [ ] Critical defects resolved.
- [ ] Console clean.
- [ ] Navigation verified.
- [ ] Mobile menu verified.
- [ ] All links verified.
- [ ] Delivery checklist completed.

---

# Master Startup Checklist

## Planning

- [ ] Requirements reviewed.
- [ ] Figma reviewed.
- [ ] Assets prepared.
- [ ] Architecture created.

---

## Development

- [ ] Shared components identified.
- [ ] CMS reviewed.
- [ ] Responsive planned.
- [ ] Performance planned.

---

## Validation

- [ ] Browser QA completed.
- [ ] Figma Validation completed.
- [ ] Final QA completed.

---

## Delivery

- [ ] Delivery checklist completed.
- [ ] Project approved.
- [ ] Ready for handover.

---

# Common Mistakes

Avoid:

- Starting development before reviewing Figma.
- Creating folders during implementation instead of planning them.
- Ignoring CMS planning.
- Delaying responsive planning.
- Waiting until the end for Browser QA.
- Skipping Final QA before delivery.

---

# Best Practices

- Follow the same startup workflow for every project.
- Complete each phase before moving to the next.
- Validate continuously.
- Resolve questions before implementation.
- Use this checklist as the project's startup SOP.

---

# Engineering Acceptance Criteria

A project satisfies this standard when:

- Every startup phase has been completed.
- Project architecture follows the handbook.
- Implementation proceeds according to the defined workflow.
- Validation is integrated throughout development.
- Delivery occurs only after all engineering standards have been satisfied.

---

# Chapter Summary

The New Project Checklist is the operational entry point into the engineering handbook.

Rather than defining new rules, it organizes the existing engineering standards into a repeatable project startup workflow.

Following this chapter ensures every project begins with the same planning, architecture, validation, and quality processes, reducing implementation mistakes and improving long-term consistency.

---