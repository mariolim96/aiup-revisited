---
name: atdd-backend
description: Use before backend implementation to write a failing JUnit 5 integration test against the inbound domain ports (Hexagonal Architecture) based on a use case.
---

# ATDD Backend

## Overview
Reverses the typical workflow by writing tests *before* writing code (Acceptance Test-Driven Development). This skill focuses purely on the Backend track of a Hexagonal Architecture, testing the inbound Use Case ports.

## When to Use
- Before `/implement-backend`.
- When the backend team starts working on a new Use Case.

## Process
1. **Read Specifications**: Read the requested `UC-*.md` from `docs/use_cases/` and the entity model from `docs/entity_model.md`.
2. **Identify the Port**: Determine the Java interface (inbound port) that will satisfy this use case (e.g., `SottomissioneUseCase`).
3. **Write Failing Test**: Generate a JUnit 5 test under `src/test/java/` that:
   - Injects the port interface.
   - Sets up required test data using Flyway migrations (or directly via jOOQ in setup).
   - Calls the port methods to simulate the Main Success Scenario and Alternative Flows.
   - Asserts the expected state/exceptions.
4. **Handoff**: The test should intentionally fail to compile or execute since the implementation doesn't exist yet. Instruct the user to run `/implement-backend` next to make the test pass.
