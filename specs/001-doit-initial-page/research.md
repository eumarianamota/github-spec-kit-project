# research.md

## Decisions

- Storage: `localStorage` (key: `doit:goals:v1`). Rationale: simple, available offline, no backend required for single-user v1. Downsides: synchronous API and limited capacity; acceptable for MVP with hundreds of small objects.

- UI: `shadcn/ui` primitives for accessible components (modal, checkbox, buttons). Rationale: accelerates implementation of accessible patterns and pairs well with Tailwind.

- Styling: Tailwind CSS using `@theme` tokens for color variables. Rationale: maintainable tokens enable consistent pastel theme and easy future theme swaps.

- Dates: `date-fns` for parsing, difference-in-days, formatting. Rationale: small footprint, functional API, good TypeScript support.

## Alternatives Considered

- IndexedDB: more robust storage, async and larger capacity. Rejected for v1 due to implementation complexity and delivery speed; can migrate later.
- Custom components: building all components in-house. Rejected to save time and ensure accessibility via `shadcn/ui`.

## Rationale Summary

These choices prioritize delivering a polished, accessible MVP quickly while keeping future migration paths (IndexedDB, remote sync) open.
