---
name: check-pr
description: Automates GitHub Pull Request management. Reads PR comments and status checks using the GitHub CLI (gh), fixes the code to address reviewer feedback, pushes the changes, and resolves the comment threads.
---

# Check PR

## Overview
This skill automates the resolution of code review feedback on a Pull Request. Instead of manually fixing reviewer comments, the agent acts as the developer to address them.

## Requirements
- The GitHub CLI (`gh`) must be installed and authenticated.
- You must be on the branch associated with the Pull Request.

## Process
1. **Fetch PR State**: The agent runs `gh pr view --comments` and `gh pr checks` to gather all open threads, requested changes, and CI failures.
2. **Analyze Feedback**: The agent maps each comment to the specific file and line of code.
3. **Implement Fixes**: The agent edits the local codebase to satisfy the reviewer's requests or fix failing tests.
4. **Commit & Push**: The agent commits the changes with a descriptive message (e.g., `fix: address PR feedback`) and pushes to the remote branch.
5. **Resolve Threads**: (Optional/Suggested) The agent can use `gh api` or suggest commands to resolve the comment threads that were addressed.
6. **Report**: The agent provides a summary of what was fixed and what (if anything) still requires human attention or discussion.
