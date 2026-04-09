# Feature Specification: Doit — Initial Page Setup

**Feature Branch**: `001-doit-initial-page`  
**Created**: 2026-04-09  
**Status**: Draft  
**Input**: User description: "initial page setup - this application should be a goal tracking web app called \"doit\". There should be two columns - a left one where current goals are shown, along with how many days left the user has to achieve the goal, and a right one where completed goals are. Each goal can be \"checked\" using a checkbox, and the either moved to the completed column or permanently deleted. To add new goals, a user can click on a button to open a new goal form in a modal (title and end date fields). Goals reaching their end date (within 3 days) are highlighted. Lets use a modern light theme with fun pastel colors."

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Create and complete a goal (Priority: P1)

As a user I want to add a new goal with a title and end date so I can track progress and mark it complete when done.

**Why this priority**: Core value — allows users to capture and complete goals.

**Independent Test**: Open the app, click the "Add Goal" button, submit a title and future end date; new goal appears in left column with days remaining; checking its checkbox moves it to the right column.

**Acceptance Scenarios**:

1. **Given** the main page is open, **When** the user clicks "Add Goal" and submits a valid title and end date, **Then** the new goal appears in the left (current) column with the correct days-left displayed.
2. **Given** a goal in the left column, **When** the user checks its checkbox, **Then** the goal is moved to the right (completed) column and marked completed.

---

### User Story 2 - Permanently delete a completed goal (Priority: P2)

As a user I want to permanently delete goals I no longer need from the completed column so my completed list stays tidy.

**Why this priority**: Keeps completed list manageable; secondary to create/complete flow.

**Independent Test**: Move a goal to completed, then use the delete action; the goal is removed and no longer shown.

**Acceptance Scenarios**:

1. **Given** a goal in the completed column, **When** the user activates the delete action and confirms, **Then** the goal is permanently removed from the UI and persistent store.

---

### User Story 3 - Visual urgency for ending goals (Priority: P3)

As a user I want goals that are within 3 days of their end date highlighted so I can prioritize what to work on.

**Why this priority**: Improves awareness and encourages timely action.

**Independent Test**: Create or view goals with end dates within 3 days; they appear highlighted in the current column.

**Acceptance Scenarios**:

1. **Given** a goal with an end date 3 days or fewer away, **When** the page renders, **Then** that goal is visually highlighted (distinct background or border) in the current column.

---

### Edge Cases

- Expired goals (end date past): mark as Expired — show in the active column with distinct "expired" styling and allow user actions (delete, archive, or mark complete).  
- Large number of goals: columns should remain scrollable and usable.  
- Missing title or invalid date input: form shows inline validation and prevents submission.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: The UI MUST provide an "Add Goal" button that opens a modal form with `title` and `end date` fields.  
  - Acceptance: Modal opens on click; form validates non-empty title and a parsable end date.
- **FR-002**: The system MUST display active goals in a left column and completed goals in a right column.  
  - Acceptance: New goals default to active and appear in left column; completed goals appear in right column.
- **FR-003**: Each goal item MUST display the number of days left until `end date` (rounded down to whole days) and the formatted end date.  
  - Acceptance: Days-left calculation matches expectations for multiple sample dates.
- **FR-004**: Goals with end dates within 3 days MUST be visually highlighted in the active column.  
  - Acceptance: Given sample goals, those with <=3 days show the highlight; others do not.
- **FR-005**: Checking a goal's checkbox MUST mark it completed and move it to the completed column.  
  - Acceptance: After checking, the item appears in completed column and retains title and end date.
- **FR-006**: Users MUST be able to permanently delete completed goals via an explicit delete action and confirmation.  
  - Acceptance: Delete flow removes the goal from UI and persistent store after confirmation.
- **FR-007**: The add-goal modal MUST prevent submission of invalid input (empty title or invalid date) and show inline validation messages.  
  - Acceptance: Attempting to submit invalid data shows validation and does not close modal.

### Key Entities *(include if feature involves data)*

- **Goal**: Represents a tracked goal. Key attributes: `id`, `title`, `end_date` (ISO date), `status` (active|completed), `created_at`, `completed_at` (optional).

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Users can add a new goal and see it in the active column within 30 seconds (end-to-end).  
- **SC-002**: Checking a goal's checkbox moves it to completed in under 2 seconds (perceptible instant).  
- **SC-003**: Goals with <=3 days remaining are highlighted and noticeable to users in default view (qualitative validation via quick user check).  
- **SC-004**: 95% of basic flows (add → complete → delete) succeed in manual acceptance tests without errors.

## Assumptions

- This initial feature targets a single-user view (no multi-user sync or authentication).  
 - Persistence for v1 is implemented using the browser's `localStorage` (keyed JSON). Cross-device sync is out of scope for v1.  
- Mobile/responsive optimizations are out of scope for v1 unless they are trivial to include.  
- Dates and days-left are calculated in the user's local timezone.

- Completed goals are retained indefinitely (no automatic archival or deletion) unless the user explicitly removes them.

## Notes

- Design: Use a modern light theme with fun pastel colors. Highlight urgency using a contrasting pastel accent.  
- Accessibility: Ensure checkbox and delete actions are keyboard accessible and labeled for screen readers.
## Clarifications

### Session 2026-04-09

- Q: For v1 persistence, which storage should we use? → A: A (localStorage)
- Q: For expired goals (end date past), how should they be handled? → A: B (Mark as Expired — show in active column with expired styling; allow delete/archive/mark complete)
- Q: For completed goals retention, which option should we use? → A: A (Keep completed goals indefinitely)