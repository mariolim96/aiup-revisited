---
name: resolve-ticket
description: Drives the end-to-end execution of a development ticket using incremental implementation principles. Reads the ticket, maps it to Use Cases, builds in test-driven vertical slices, and closes the ticket.
---

# Resolve Ticket

## Overview
This skill bridges the gap between project management and code construction. Instead of trying to implement an entire feature in one massive step, this skill forces the developer (or agent) to work in **vertical, test-driven slices**. It ensures atomic commits, rigorous scope discipline, and continuous verification.

## When to Use
- When you pick up a new ticket created by `/create-tickets`.
- When starting work on an issue assigned to you in Jira/GitHub.

## Process: The Incremental Loop

1. **Context Initialization**:
   - The agent reads the Ticket ID or description.
   - It cross-references the ticket with the originating Use Case (`docs/use_cases/UC-*.md`), the entity model, and the `docs/requirements.md`.
   - It checks `docs/tasks.md` or the issue tracker for the specific acceptance criteria.

2. **Task Breakdown & Slicing**:
   - The agent refuses to do all the work in one pass.
   - It breaks the ticket into 2-4 "Vertical Slices" (e.g., *Slice 1: Persistence/Ports*, *Slice 2: Domain Logic*, *Slice 3: UI/Controller*).

3. **Incremental Implementation (The Core Engine)**:
   For each Slice:
   - **Implement**: Write the minimal code needed for this slice.
   - **Test**: Run unit/integration tests (`npm test`, `mvn verify`). If they fail, fix them immediately. Do not move forward with a broken build.
   - **Commit**: Create an atomic Git commit specifically for this slice (e.g., `feat: implement user repository for ticket #123`).

4. **Scope Discipline (Red Flags)**:
   - Do NOT refactor code outside the scope of the ticket.
   - Do NOT write more than ~100 lines of code without running tests.
   - Do NOT mix different concerns in a single commit.

5. **Ticket Closure**:
   - Once all slices are complete and all acceptance criteria from the ticket are met, the agent verifies the whole suite.
   - The agent uses the GitHub CLI (`gh issue close`) or another appropriate tool to mark the ticket as resolved.

## Relationship with other skills
If your project uses split teams, `resolve-ticket` acts as the orchestrator that will eventually invoke `/implement-backend` or `/implement-frontend` for the specific slices.
