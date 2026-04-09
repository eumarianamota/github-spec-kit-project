# Project Constitution

## Purpose
This document declares the project-wide principles for code quality, UX, responsiveness, and dependency management. It also records the required framework versions for this repository and a non-negotiable constraint regarding testing.

## Core Principles

- **Clean Code:** Favor clarity over cleverness. Write self-explanatory functions, small components, and deliberate naming. Keep functions/components single-responsibility, avoid deep nesting, and prefer composition over inheritance. Prefer explicitness: small, well-named abstractions beat generic frameworks.

- **Simple UX:** Design for the common path first. Reduce cognitive load: clear affordances, predictable patterns, accessible defaults, and minimal configuration. Use progressive disclosure for advanced features and prefer clear microcopy over modals or complex flows.

- **Responsive Design:** Mobile-first layouts, fluid grids, and utility-first responsive rules. Visual hierarchy must adapt across breakpoints; touch targets, spacing, and typography scale appropriately. Test layouts at common viewport sizes manually during design reviews.

- **Minimal Dependencies:** Add libraries only when they clearly reduce long-term maintenance or add essential capability. Prefer platform-provided APIs and small, well-maintained packages. Evaluate trade-offs for bundle size, maintenance burden, and security surface.

## Non-negotiable Constraint

- **No Automated Tests Allowed:** Under this constitution, absolutely no automated testing is to be added or required for this project — this includes unit tests, integration tests, and end-to-end tests. This rule supersedes any other guidance in this document.

## Technology Versions (from package.json)

- **Next.js:** 16.2.2
- **React:** 19.2.4 (react-dom: 19.2.4)
- **Tailwind CSS:** ^4 (devDependency `tailwindcss`)

These versions are authoritative for the project and should be used when scaffolding or upgrading features.

## Development Guidance

- Keep pages and components small and focused. Break large pages into composable components.
- Use Tailwind utility classes for rapid, consistent styling and to keep CSS surface minimal.
- Prefer server-side rendering or hybrid rendering (Next.js patterns) for content-critical pages; keep client-side state localized and minimal.
- Document non-obvious decisions in short README sections adjacent to major modules.

## Governance

- This constitution supersedes informal practices. Amendments require a documented rationale and an explicit ratification date.
- Compliance checks are manual: reviewers should ensure PRs follow these principles (except the testing prohibition, which is absolute).

**Version**: 1.0.0 | **Ratified**: 2026-04-08 | **Last Amended**: 2026-04-08
