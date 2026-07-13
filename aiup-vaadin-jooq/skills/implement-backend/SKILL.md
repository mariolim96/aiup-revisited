---
name: implement-backend
description: Use to implement the domain logic, inbound/outbound ports, and jOOQ adapters for a use case to make the backend ATDD tests pass.
---

# Implement Backend

## Overview
Implements the backend slice of a Use Case in a Hexagonal Architecture (Domain model, Use Case Services, and jOOQ adapters). It does NOT write any Vaadin UI code.

## When to Use
- After running `/atdd-backend`.
- When you need to implement business logic and database access for a use case.

## Process
1. **Read Specifications**: Read the `UC-*.md` and `docs/entity_model.md`.
2. **Review Failing Tests**: Check the tests created by `/atdd-backend` to understand the exact expected behavior and API contract.
3. **Implement Domain**: Write/Update the core domain entities.
4. **Implement Ports**: Write the inbound and outbound port interfaces.
5. **Implement Adapters**: Write the jOOQ database adapters mapping to the outbound ports.
6. **Implement Services**: Write the Application service implementing the inbound ports.
7. **Verify**: Ensure the code compiles and that the previously failing `/atdd-backend` tests now pass.
