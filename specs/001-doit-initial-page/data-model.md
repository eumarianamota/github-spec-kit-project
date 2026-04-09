# data-model.md

## Entities

- **Goal**
  - `id`: string (UUID)
  - `title`: string (non-empty)
  - `end_date`: string (ISO 8601 date)
  - `status`: enum `active | completed | expired`
  - `created_at`: string (ISO 8601 datetime)
  - `completed_at`: string | null (ISO 8601 datetime)
  - `archived`: boolean (optional)

## Validation Rules

- `title` must be non-empty and max length 256.
- `end_date` must be a valid date in the future for newly created goals (past dates are allowed only if user explicitly sets them and then marked as `expired`).
- `status` transitions:
  - `active` -> `completed` when user checks the goal
  - `active` -> `expired` when current date > end_date
  - `completed` may be `archived` or deleted by user

## Storage Schema (localStorage)

- Key: `doit:goals:v1`
- Value: JSON array of `Goal` objects (compact representation)
