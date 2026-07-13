---
name: generate-project-context
description: Use when starting an AIUP project on an existing legacy codebase to scan and establish persistent project rules for the implementation phase.
---

# Generate Project Context

## Overview
When bringing AIUP to an existing codebase, you want `/implement` to follow the project's existing conventions. This skill scans the repository and outputs a `project-context.md` file to act as persistent memory for your agents.

## When to Use
- When onboarding AIUP to a legacy project.
- Before running `/implement` on any use cases in an existing repository.
- Periodically to refresh the agent's understanding of codebase patterns.

## Process
1. **Scan the Codebase**: Analyze the existing code for:
   - File structures and naming conventions.
   - Core libraries, frameworks, and versions.
   - Testing patterns.
   - Linting or style rules.
2. **Draft the Context**: Compile these findings into a concise reference document.
3. **Save**: Save it to `docs/project-context.md` (or `_bmad-output/project-context.md`).
4. **Handoff**: Instruct the user that future agents running `/implement` or `/code-review` will automatically read this context to stay aligned with the team's standards.
