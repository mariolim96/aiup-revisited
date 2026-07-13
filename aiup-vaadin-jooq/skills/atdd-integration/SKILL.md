---
name: atdd-integration
description: Use to generate a full Playwright End-to-End test that validates both frontend and backend integration for a use case.
---

# ATDD Integration

## Overview
Writes a full Playwright integration test that validates the complete vertical slice of a Use Case (Frontend + Backend + Real Database).

## When to Use
- After both `/implement-frontend` and `/implement-backend` have been completed.
- To verify that the isolated pieces work correctly when integrated.

## Process
1. **Read Specifications**: Read the `UC-*.md`.
2. **Review Existing Tests**: Look at the `/atdd-backend` and `/atdd-frontend` tests to understand the expected behavior and UI elements.
3. **Write E2E Test**: Generate a Playwright test using Drama Finder that starts the application, interacts with the browser, and validates the final state (optionally querying the database or verifying the UI changes).
4. **Run and Verify**: Run the Playwright test. If it fails, there is an integration bug. Instruct the user to fix the bug (either in BE or FE) and re-run the test.
