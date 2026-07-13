---
name: create-tickets
description: Use when you have a completed AIUP use case specification and need to create an implementation ticket (e.g., Jira, GitHub Issues) before starting development.
---

# Create Tickets

## Overview
This skill bridges the gap between the AI Unified Process (AIUP) Elaboration phase and your Agile Sprint execution by converting a detailed Use Case Specification (`UC-*.md`) into a structured ticket.

## When to Use
- After generating use cases (via `/use-case-spec` or `/reverse-engineer`).
- Before starting the implementation of a use case (`/implement`).
- When breaking down a project for sprint planning.

## Process

1. **Locate the Use Case**: Ask the user which Use Case they want to ticket (e.g., `UC-001`). Locate the corresponding file (usually in `docs/use_cases/UC-*.md`) and read its contents.
2. **Extract Ticket Fields**:
   - **Title**: Map the Use Case ID and Name to the ticket title.
   - **User Story**: Format the primary actor and goal as a user story ("As a [Actor], I want to [Goal], so that [Benefit]").
   - **Acceptance Criteria**: Convert the Main Success Scenario and Postconditions into a checklist.
   - **Edge Cases**: Convert the Alternative Flows into a checklist of edge cases to test.
3. **Create the Ticket**:
   - If an MCP tool or CLI (like `gh issue create`) is available for the user's tracking system, invoke it to create the ticket automatically.
   - If no tool is available, output the formatted ticket in Markdown so the user can easily copy and paste it into Jira, Linear, or Azure DevOps.

## Ticket Template (Markdown)

```markdown
**Use Case**: [UC-XXX] [Name]

**User Story**:
As a [Primary Actor], I want to [Goal]

**Acceptance Criteria**:
- [ ] [Step 1 from Main Success Scenario]
- [ ] [Step 2 from Main Success Scenario]
- [ ] [Postcondition 1 is met]

**Edge Cases to Handle (Alternative Flows)**:
- [ ] [Alternative Flow 1]
- [ ] [Alternative Flow 2]
```

## Common Mistakes
- **Copying the whole file verbatim**: Do not just dump the raw `UC-*.md` text into the ticket. Issue trackers need checklists and concise formatting.
- **Skipping Alternative Flows**: Developers need to know the edge cases. Always include alternative flows as testable checklist items.
