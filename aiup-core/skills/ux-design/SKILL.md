---
name: ux-design
description: Use after generating AIUP use case specifications to design the UI layouts, components, and user flows before frontend implementation.
---

# UX Design

## Overview
This skill bridges the gap between functional Use Case Specifications (`UC-*.md`) and actual UI implementation by designing wireframes and component structures.

## When to Use
- After generating `/use-case-spec`.
- Before running `/implement` for front-end or full-stack features.

## Process
1. **Read the Use Case**: Ask the user which use case they want to design (e.g., `UC-001.md`).
2. **Analyze Flow**: Extract the user interactions from the Main Success Scenario and Alternative Flows.
3. **Design the UI**: 
   - Propose a layout structure (e.g., Grid, Sidebar, Forms).
   - List the required UI components (e.g., "Submit Button", "Data Grid", "Confirmation Modal").
   - Draft a text-based wireframe or visual hierarchy.
4. **Save**: Save the design to a new file, e.g., `docs/ux/UX-001.md`.
5. **Handoff**: The user can now use this UX spec alongside the functional Use Case Spec when running `/implement`.
