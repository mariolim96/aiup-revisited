---
name: sprint-planning
description: Use when you have multiple AIUP Use Cases ready for development and need to organize them into an actionable, tracked sprint.
---

# Sprint Planning

## Overview
AIUP generates functional Use Case Specifications (`UC-*.md`), but it doesn't track their execution. This skill bridges the gap by creating an Agile sprint board to manage implementation progress.

## When to Use
- After generating a batch of use cases via `/use-case-spec` or `/reverse-engineer`.
- Before diving into `/implement` for the first time on a new milestone.

## Process
1. **Discover Use Cases**: Scan the `docs/use_cases/` directory for available `UC-*.md` files.
2. **Estimate Effort**: Read the use cases and provide a rough complexity estimate (Low/Medium/High) for each.
3. **Generate Board**: Create a tracking file (e.g., `sprint-status.yaml` or a markdown table) that lists:
   - Use Case ID and Title
   - Estimate
   - Status (Pending / In Progress / Blocked / Done)
   - Assigned Agent/Dev
4. **Save**: Save the sprint board to the root or `docs/` folder.
5. **Handoff**: Tell the user to pick a pending use case and run `/implement` on it, reminding them to update the board when they finish.
