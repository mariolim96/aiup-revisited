---
name: implement-frontend
description: Use to implement the Vaadin UI views and components for a use case, hooking them up to the backend domain ports.
---

# Implement Frontend

## Overview
Implements the frontend slice of a Use Case using Vaadin. It focuses entirely on the UI layout, components, and binding to the inbound ports, completely isolated from jOOQ or database concerns.

## When to Use
- After running `/atdd-frontend`.
- When you need to build the UI for a use case.

## Process
1. **Read Specifications**: Read the `UC-*.md` and any UX wireframes (`docs/ux/`).
2. **Review Failing Tests**: Check the tests created by `/atdd-frontend` to understand the expected UI component IDs and behaviors.
3. **Implement UI**: Create the Vaadin `@Route` classes, forms, and grids.
4. **Wire to Backend**: Inject the inbound port interface (e.g., `SottomissioneUseCase`) into the Vaadin view to handle business logic. Do not write direct database queries in the UI.
5. **Verify**: Ensure the code compiles and the `/atdd-frontend` tests pass.
