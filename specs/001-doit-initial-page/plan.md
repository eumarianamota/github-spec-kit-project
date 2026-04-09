# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit.plan` command. See `.specify/templates/plan-template.md` for the execution workflow.

## Summary

Doit initial-page: a single-user, frontend-first goal-tracking page built with Next.js + React. Primary requirements: add goals (title + end date), show active and completed columns, highlight urgency (<=3 days), allow check-to-complete and permanent delete. Technical approach: client-side UI with Tailwind (using `@theme` tokens for colors), shadcn UI primitives for accessible components, `date-fns` for date calculations/formatting, and `localStorage` for v1 persistence.

## Technical Context

**Language/Version**: TypeScript + Next.js 16.2.2, React 19.2.4
**Primary Dependencies**: Next.js, React, Tailwind CSS (v4+), shadcn/ui (for accessible primitives), `date-fns` (date calculations/formatting)
**Storage**: Browser `localStorage` with a single JSON key `doit:goals:v1` containing an array of Goal objects
**Testing**: None (per project constitution — no automated tests)
**Target Platform**: Web (Next.js frontend, client-side interactive components)
**Project Type**: Frontend web application (single-page/route within Next.js app)
**Performance Goals**: snappy UI interactions (<200ms for goal actions on typical desktop), minimal bundle overhead for first load
**Constraints**: Single-user local persistence; small bundle size preference; accessibility and keyboard operability required
**Scale/Scope**: MVP for a single-user client app; storage expected to hold hundreds of small goal objects without degradation

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

Constitution highlights:
- Non-negotiable: No automated tests allowed — this plan includes no tests and therefore complies.
- Minimal dependencies: `shadcn/ui` and `date-fns` are intentionally included to provide accessible UI primitives and robust date handling; trade-offs are discussed in `research.md`.

Result: PASS — no constitution gate violations detected.

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Source Code (repository root)

```text
app/
├── doit/                      # Feature route for Doit
│   ├── page.tsx               # Main page route for the Doit UI
│   └── components/
│       ├── GoalList.tsx
│       ├── GoalItem.tsx
│       ├── AddGoalModal.tsx
│       └── index.ts
components/
├── ui/                        # shadcn/ui wrappers and shared primitives
│   ├── Button.tsx
│   └── Modal.tsx
lib/
├── storage.ts                 # localStorage helpers (doit:goals:v1)
├── date.ts                    # date-fns helpers (daysLeft, isWithinDays)
styles/
├── tailwind/                  # theme token files and tailwind snippets
└── globals.css
```

**Structure Decision**: Frontend-first, single Next.js route implemented within the existing `app/` layout. Components live under `app/doit/components/`. Persistence helpers live under `lib/` (e.g., `lib/storage.ts`, `lib/date.ts`). Tailwind theme tokens under `styles/tailwind/`.

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., 4th project] | [current need] | [why 3 projects insufficient] |
| [e.g., Repository pattern] | [specific problem] | [why direct DB access insufficient] |
