---
name: correct-course
description: Use when you hit a roadblock during AIUP implementation and need to pivot requirements or use cases without breaking traceability.
---

# Correct Course

## Overview
AIUP relies on traceability (Vision -> Requirements -> Entity Model -> Use Cases -> Code). If you encounter an issue during `/implement` that invalidates the original design, you cannot just hack the code. This skill safely updates the upstream planning documents to reflect the new reality.

## When to Use
- During `/implement` when a technical limitation or new discovery forces a change in scope.
- When you realize a use case is missing critical steps or edge cases.

## Process
1. **Analyze the Pivot**: Ask the user what went wrong or what needs to change.
2. **Identify Dependencies**: Determine which AIUP documents are affected (e.g., `requirements.md`, `entity_model.md`, `UC-001.md`).
3. **Propose Updates**: Present a detailed plan showing how the upstream documents will change to support the new technical reality.
4. **Update**: Once approved, safely rewrite the affected documents.
5. **Resume**: Instruct the user to resume their `/implement` run now that the specifications are up-to-date and traceability is maintained.
