---
name: product-brief
description: Use when you have a well-defined product idea and need to generate a structured product brief (docs/vision.md) to kick off the AIUP requirements phase.
---

# Product Brief

## Overview
This skill generates a robust `docs/vision.md` document from your high-level product idea. This serves as the critical starting point for the AI Unified Process (AIUP).

## When to Use
- Before running AIUP's `/requirements`.
- When you know what you want to build and need to formalize it into a structured vision document.
- To outline target users, core features, and out-of-scope items.

## Process
1. **Gather Input**: Ask the user for the high-level idea, target audience, and primary goals.
2. **Draft the Brief**: Create a structured product brief containing:
   - **Product Name & Elevator Pitch**
   - **Target Audience**
   - **Problem Statement**
   - **Core Features**
   - **Non-Goals (Out of Scope)**
3. **Save**: Save this document directly to `docs/vision.md`.
4. **Handoff**: Inform the user they can now run `/requirements` to begin the AIUP workflow.
