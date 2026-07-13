---
name: auto-review-loop
description: Performs an autonomous self-review loop before opening a Pull Request. Analyzes local changes against use case specifications and project rules, auto-correcting any deviations until the code is merge-ready.
---

# Auto Review Loop

## Overview
This skill acts as a relentless, automated peer reviewer *before* code is submitted. It prevents logic gaps, architectural violations, and missing requirements from ever reaching a Pull Request.

## When to Use
- After implementing a feature (`/implement-*`) but before opening a PR.
- When you want to ensure the code adheres strictly to the Use Case (`docs/use_cases/`) and architectural guidelines.

## Process
This is a recursive loop that stops only when the code passes its own rigorous standards:

1. **Diff Analysis**: The agent runs `git diff` against the base branch (e.g., `main`) to see what was changed.
2. **Contextual Review**: The agent reads the relevant `UC-*.md`, `docs/requirements.md`, and any architectural rules (`.agents/AGENTS.md` or `rules/`).
3. **Critique**: The agent plays the role of a Senior Architect. Are all Alternative Flows handled? Are there any security risks? Is the Hexagonal Architecture respected? Are tests passing?
4. **Auto-Fix**: If the agent finds flaws, it does **not** just report them—it fixes them locally.
5. **Iteration**: After fixing, the agent re-evaluates the diff.
6. **Completion**: The loop terminates when the agent scores the changes 5/5 for completeness and adherence to standards, declaring the branch "Merge-Ready".
