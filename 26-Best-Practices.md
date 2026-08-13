# 26 – Best Practices

> **Status:** Engineering Reference Manual
>
> **Applies To:** Every frontend project developed using this handbook.
>
> **Related Chapters**
>
> - Chapters 01–25

---

# Purpose

This chapter consolidates the engineering best practices defined throughout this handbook into a single reference.

Rather than introducing new standards, it summarizes the practices that consistently lead to maintainable, scalable, performant, and production-ready frontend projects.

---

# Engineering Philosophy

Great frontend projects are rarely the result of one brilliant decision.

They are the result of hundreds of small, consistent engineering decisions made correctly every day.

Engineering quality is built through habits.

---

# 1. Project Planning

Always:

- Review the entire Figma file before coding.
- Understand project requirements before implementation.
- Identify reusable components first.
- Plan page structure before writing HTML.
- Clarify uncertainties instead of making assumptions.
- Follow the approved project workflow.

---

# 2. Architecture

Always:

- Follow the approved folder structure.
- Keep architectural responsibilities separate.
- Reuse existing project architecture.
- Extend architecture rather than replacing it.
- Maintain consistent naming.
- Keep shared resources centralized.

---

# 3. HTML

Always:

- Use semantic HTML5.
- Maintain a proper heading hierarchy.
- Use one `<h1>` per page.
- Give every section a unique ID.
- Give every section a unique class.
- Write clean, readable markup.
- Minimize unnecessary nesting.
- Use meaningful image `alt` text.

---

# 4. CSS

Always:

- Reuse shared styles.
- Use Design Tokens.
- Avoid duplicate CSS.
- Keep selectors focused.
- Write maintainable styles.
- Keep styling modular.
- Follow the approved SASS architecture.

---

# 5. SASS

Always:

- Respect architectural layers.
- Use directory index files.
- Keep shared styles in shared layers.
- Keep page styles isolated.
- Follow the approved import order.
- Maintain consistent folder organization.

---

# 6. Responsive Design

Always:

- Follow the global breakpoint system.
- Validate every supported breakpoint.
- Preserve layout hierarchy.
- Preserve typography hierarchy.
- Keep spacing consistent.
- Build responsiveness into the implementation process.

---

# 7. Components

Always:

- Build reusable components.
- Reuse existing components before creating new ones.
- Give each component one responsibility.
- Keep components independent.
- Reuse shared behaviour.
- Maintain consistent structure.

---

# 8. CMS Development

Always:

- Confirm editable fields.
- Style through wrappers.
- Test long content.
- Test empty content.
- Test repeaters.
- Keep editors responsible only for content.
- Keep frontend responsible for presentation.

---

# 9. JavaScript

Always:

- Centralize shared logic.
- Isolate page-specific logic.
- Validate DOM elements before use.
- Prevent duplicate initialization.
- Reuse existing utilities.
- Keep scripts organized by responsibility.

---

# 10. Accessibility

Always:

- Use semantic HTML.
- Preserve reading order.
- Use meaningful `alt` text.
- Build predictable navigation.
- Keep interactive elements usable.
- Review accessibility during implementation.

---

# 11. Performance

Always:

- Optimize images.
- Specify image dimensions.
- Prevent layout shifts.
- Lazy-load non-critical media.
- Load hero media immediately.
- Review Core Web Vitals throughout development.

---

# 12. Header

Always:

- Reuse the shared header.
- Match positioning to the design.
- Verify scroll behaviour.
- Maintain responsive consistency.
- Keep header behaviour predictable.

---

# 13. Navigation

Always:

- Verify every link.
- Test the mobile menu.
- Validate dropdowns.
- Keep navigation semantic.
- Reuse the shared navigation system.

---

# 14. Sliders

Always:

- Configure behaviour explicitly.
- Validate autoplay.
- Test mouse interaction.
- Test touch interaction.
- Verify responsive layouts.
- Compare behaviour with Figma.

---

# 15. Browser QA

Always:

- Test locally.
- Capture screenshots.
- Review Desktop.
- Review Tablet.
- Review Mobile.
- Compare against Figma.
- Fix issues immediately.

---

# 16. Figma Validation

Always:

- Keep Figma open during development.
- Compare section by section.
- Measure rather than estimate.
- Verify spacing.
- Verify typography.
- Verify component behaviour.

---

# 17. Final QA

Always:

- Complete Browser QA first.
- Complete Figma Validation first.
- Verify architecture.
- Verify responsiveness.
- Verify performance.
- Verify functionality.

---

# 18. Delivery

Always:

- Deliver only approved work.
- Resolve defects before release.
- Review the delivery checklist.
- Keep engineering quality consistent.

---

# 19. AI Development

Always:

- Treat AI as an assistant.
- Review AI-generated code.
- Preserve project architecture.
- Preserve component reuse.
- Preserve handbook standards.
- Validate AI output before accepting it.

---

# Universal Engineering Principles

Every engineering decision should prioritize:

- Reusability
- Maintainability
- Consistency
- Simplicity
- Performance
- Accessibility
- Scalability
- Readability
- Predictability
- Quality

---

# Senior Engineer Mindset

Before completing any task, ask:

- Does this follow the handbook?
- Can this be reused?
- Is there a simpler solution?
- Will another developer understand this?
- Does this match the approved design?
- Will this still be maintainable in six months?

If the answer to any question is **No**, improve the implementation before continuing.

---

# Daily Engineering Checklist

Before starting work:

- [ ] Review project requirements.
- [ ] Review Figma.
- [ ] Review reusable components.
- [ ] Review architecture.

During development:

- [ ] Follow the handbook.
- [ ] Reuse existing solutions.
- [ ] Validate responsiveness.
- [ ] Review Browser QA.

Before finishing:

- [ ] Compare with Figma.
- [ ] No broken layouts
- [ ] All text readable
- [ ] No overlapping elements
- [ ] Mobile hamburger menu works
- [ ] All links and buttons function
- [ ] No JavaScript console errors
- [ ] Review performance.
- [ ] Check accessibility.
- [ ] Complete Final QA.

---

# Engineering Culture

The purpose of this handbook is not simply to define rules.

Its purpose is to create a consistent engineering culture where every project follows the same architecture, quality standards, and validation workflow regardless of who builds it.

Consistency is more valuable than individual coding preferences.

---

# Chapter Summary

This chapter serves as the handbook's master engineering playbook.

By consistently applying these practices, developers produce frontend projects that are easier to maintain, easier to scale, more predictable to review, and more reliable to deliver.

Engineering excellence is achieved through disciplined, repeatable practices rather than isolated technical decisions.

---