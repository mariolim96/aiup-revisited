---
name: create-tickets
description: >-
  Use when you have a completed AIUP use case specification and need to create an implementation ticket (e.g., Jira, GitHub Issues) before starting development.
  Covers title conventions, description templates, acceptance criteria, and specific mapping from AIUP use cases to tickets.
tags:
  - developer
  - planning
  - agile
---

# Create Tickets

## Overview
This skill bridges the gap between the AI Unified Process (AIUP) Elaboration phase and your Agile Sprint execution by converting a detailed Use Case Specification (`UC-*.md`) into a structured, ready-to-work ticket.

## When to Use
- After generating use cases (via `/use-case-spec` or `/reverse-engineer`).
- Before starting the implementation of a use case (`/implement`).
- When breaking down a project for sprint planning.

## Guiding Principles
1. **Any engineer can pick it up cold** — The ticket must be self-contained. No oral lore required.
2. **One clear outcome** — A ticket should answer: "How will I know when this is done?"
3. **Right size** — A story should take 1–5 days. Split anything larger. Combine anything smaller.
4. **Outcome over activity** — Describe the result, not the steps to get there.
5. **User language for stories, system language for tasks** — Stories frame user value; tasks frame technical work.
6. **Dependencies are explicit** — Blocks, is-blocked-by, and relates-to links are set before the ticket enters the sprint.

## Ticket Type Reference

| Type | Purpose | Size target |
|------|---------|-------------|
| **Epic** | A complete user-facing capability or large Use Case | Quarter |
| **Story** | A user-facing feature or behavior change | 1–5 days |
| **Task** | Internal technical work (infra, tooling, refactor, data migration) | 1–3 days |
| **Bug** | A defect in existing, shipped functionality | 1–2 days |
| **Spike** | Time-boxed investigation to reduce uncertainty before implementing a Use Case | Fixed: 1–2 days max |
| **Sub-task** | A unit of work within a story, tracked by the same engineer or pair | Hours |

## Process

1. **Locate the Use Case**: Ask the user which Use Case they want to ticket (e.g., `UC-001`). Locate the corresponding file (usually in `docs/use_cases/UC-*.md`) and read its contents. If you need further information go read the guidelines for tech stack, architecture or functional analysis.
2. **Extract Ticket Fields**:
   - **Title**: Map the Use Case ID and Name to the ticket title.
   - **User Story**: Format the primary actor and goal as a user story ("As a [Actor], I want to [Goal], so that [Benefit]").
   - **Acceptance Criteria**: Convert the Main Success Scenario and Postconditions into a checklist.
   - **Edge Cases**: Convert the Alternative Flows into a checklist of edge cases to test.
3. **Create the Ticket**:
   - If an MCP tool or CLI (like `gh issue create`) is available for the user's tracking system, invoke it to create the ticket automatically.
   - If the user asks to save the ticket as a file, write the formatted ticket as a Markdown file in the `docs/tickets/` folder (e.g., `docs/tickets/UC-001-add-pagination.md`).
   - By default, if no tracking tool is available and no file is requested, output the formatted ticket in Markdown so the user can easily copy and paste it into Jira, Linear, or Azure DevOps.

## Title Conventions

A good title is search-friendly, imperative, and specific — no jargon, no vagueness.

**Format**: `[UC-XXX] [Verb] [object] [qualifying context if needed]`

| Good | Bad |
|------|-----|
| `[UC-001] Add pagination to the activity feed API` | `Activity feed work` |
| `[UC-002] Fix 500 error when user submits empty search query` | `Search bug` |
| `[UC-003] Spike: evaluate DynamoDB vs Aurora for audit log storage` | `Research DB options` |

**Rules**:
- Start with a verb: Add, Fix, Refactor, Migrate, Remove, Update, Implement, Spike, Document
- Avoid acronyms unless universally known in your org
- Do not include sprint numbers or dates in the title
- Do not use "we should…" or "need to…" — write the action directly

## Description Templates

Pick the template for the ticket type. Fill every section. Delete none.

### Story Template

```markdown
## Context

[1–3 sentences on why this work matters. What problem does it solve for the user?
Link to the parent epic, use case specification (e.g., UC-001), and any relevant design doc.]

## User Story

As a [Primary Actor],
I want to [specific action],
So that [concrete benefit].

## Acceptance Criteria

- [ ] [Specific, testable, binary condition from Main Success Scenario]
- [ ] [Specific, testable, binary condition]
- [ ] [Postcondition is met]

## Edge Cases to Handle (Alternative Flows)

- [ ] [Alternative Flow 1]
- [ ] [Alternative Flow 2]

## Out of Scope

- [Anything explicitly NOT covered by this ticket]

## Notes / Open Questions

- [Any ambiguity or decision needed before work starts]
```

### Task Template

```markdown
## Context

[1–3 sentences on why this technical work is needed. What breaks or degrades without it?
Link to the driving story, use case, or epic.]

## Work to Be Done

1. [Concrete implementation step]
2. [Concrete implementation step]
3. [Add tests / validation]

## Definition of Done

- [ ] [Specific, verifiable completion condition]
- [ ] Tests written and passing
- [ ] PR reviewed and merged

## Out of Scope

- [Anything explicitly not included]

## Notes / Open Questions

- [Unknowns, design constraints, or reference links]
```

### Spike Template

```markdown
## Question to Answer

[The single, specific question this spike must answer. If you have more than one question, split into separate spikes.]

## Why This Matters

[What decision or work is blocked until this question is answered?]

## Time Box

**Maximum**: [1 day / 2 days] — Hard stop regardless of outcome.

## Success Criteria

By the end of this spike, we will have:
- [ ] A written recommendation (with rationale) for [question]
- [ ] Identified risks or unknowns for the recommended approach
- [ ] Updated [design doc / Use Case Spec] with findings

## Approaches to Investigate

- Option A: [brief description]
- Option B: [brief description]

## Out of Scope

- Actual implementation (this is research only)
```

## Writing Good Acceptance Criteria

Acceptance criteria (AC) define "done." Each criterion must be:

- **Binary** — Pass or fail, no judgment calls
- **Testable** — An engineer or QA can verify it without asking the author
- **Specific** — No vague words like "fast," "correct," or "appropriate"
- **Scoped** — Covers exactly this ticket, not adjacent functionality

### Bad vs. Good AC

| Bad (vague, untenable) | Good (specific, testable) |
|------------------------|---------------------------|
| `The page loads quickly` | `The activity feed loads within 2s at P95 under normal load` |
| `Errors are handled gracefully` | `A 503 from the upstream API returns a user-facing error message and logs a structured error with request ID` |
| `The form works correctly` | `Submitting the form with an empty email field shows a validation error and does not submit` |
| `Alternative flows work` | `Entering an invalid VAT number shows "Invalid VAT format" inline error and disables the submit button` |

## Common Mistakes

- **Copying the whole file verbatim**: Do not just dump the raw `UC-*.md` text into the ticket. Issue trackers need checklists and concise formatting.
- **Skipping Alternative Flows**: Developers need to know the edge cases. Always include alternative flows as testable checklist items.
