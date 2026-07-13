---
name: prfaq
description: Use when you want to design a product using the "Working Backwards" methodology (PRFAQ) before generating technical requirements.
---

# PRFAQ (Press Release and FAQ)

## Overview
This skill implements the Amazon "Working Backwards" methodology. It generates a Press Release and FAQ to define the exact customer experience and solve business questions before any technical work begins.

## When to Use
- To clarify the value proposition of a new feature or product.
- As a highly customer-centric alternative to a standard product brief.

## Process
1. **Interview**: Ask the user about the core customer problem, the proposed solution, and the main benefit.
2. **Draft PR**: Write a 1-page hypothetical Press Release announcing the finished product.
3. **Draft FAQ**: Write an Internal and External FAQ covering common customer questions and internal business/technical risks.
4. **Review**: Present the PRFAQ to the user for refinement.
5. **Save**: Once approved, save the document to `docs/vision.md` (or `docs/prfaq.md` if the user prefers).
6. **Handoff**: Inform the user they can now run `/requirements` to extract technical requirements from this PRFAQ.
