---
name: create-architecture
description: Use after generating AIUP requirements or entity models to define the technical spine, tech stack, and API patterns before implementation.
---

# Create Architecture

## Overview
AIUP defines the *what* (requirements, use cases, entity models). This skill defines the *how* by creating a high-level technical architecture document (`architecture.md`).

## When to Use
- After running `/requirements` or `/entity-model`.
- Before running `/implement` on any use cases.
- Whenever major architectural decisions (e.g., choosing a framework, database, or API style) need to be documented.

## Process
1. **Read Context**: Read the existing `docs/requirements.md` and `docs/entity_model.md` if available.
2. **Propose Architecture**: Define the following in a structured document:
   - **Tech Stack**: Frontend, Backend, Database.
   - **System Architecture**: High-level diagram (using Mermaid).
   - **Folder Structure**: Where different types of files will live.
   - **API Patterns**: E.g., RESTful conventions, GraphQL.
   - **Data Access Patterns**: E.g., jOOQ, Hibernate, direct SQL.
3. **Save**: Save this document to `docs/architecture.md`.
4. **Handoff**: Instruct the user to continue with AIUP `/use-case-spec` or `/implement`. The `/implement` skill will now have clear architectural guidelines to follow.
