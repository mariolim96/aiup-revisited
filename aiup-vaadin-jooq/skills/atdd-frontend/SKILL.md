---
name: atdd-frontend
description: Use before frontend implementation to write a failing Vaadin Browserless test for a use case, mocking the backend domain ports.
---

# ATDD Frontend

## Overview
Writes a failing Vaadin server-side unit test using the Browserless testing framework. This test isolates the UI by mocking the backend inbound ports (e.g., using `@MockBean`).

## When to Use
- Before `/implement-frontend`.
- When the frontend team starts working on a new Use Case UI.

## Process
1. **Read Specifications**: Read the `UC-*.md` and any UX wireframes (`docs/ux/`).
2. **Write Failing Test**: Generate a JUnit 5 Browserless test for the Vaadin View.
3. **Mock the Backend**: Use Spring's `@MockBean` to mock the inbound port (e.g., `SottomissioneUseCase`) so the UI can be tested without a real database.
4. **Simulate Interactions**: Use the Browserless `$view()` and `test()` APIs to click buttons, fill forms, and assert UI state.
5. **Handoff**: The test will fail because the Vaadin view doesn't exist. Instruct the user to run `/implement-frontend`.
