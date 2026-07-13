---
name: retrospective
description: Use after completing a batch of AIUP Use Cases to analyze the bugs encountered and update the project context for future use cases.
---

# Retrospective

## Overview
Agents should learn from their mistakes. This skill analyzes the code written during the recent implementation phase and updates the project's rules to prevent recurring issues.

## When to Use
- At the end of an AIUP implementation sprint.
- After running `/qa` or resolving a particularly difficult batch of bugs.

## Process
1. **Gather Data**: Ask the user what went well and what went wrong during the last `/implement` cycles. If the user isn't sure, scan recent git commits for bug fixes.
2. **Identify Learnings**: Distill the problems into actionable rules. (e.g., "We kept failing because jOOQ required X configuration.")
3. **Update Context**: Add these new rules to the `docs/project-context.md` file.
4. **Handoff**: Explain how these new rules will help the next AIUP `/implement` phase go smoother.
