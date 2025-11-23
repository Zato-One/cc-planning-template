---
description: Implement a given phase
argument-hint: <phase-number>
---

If no phase number is provided as $1, check @plan/PLAN.md to find the next phase that has at least one uncompleted step (checkbox not marked as `[x]`). Use that phase number for implementation.

Check @plan/PLAN.md to identify all steps in the target phase.

Check if a detailed phase plan exists at /plan/phases/PHASE_X.md (with zero-padding for single digits, e.g., PHASE_01.md, PHASE_02.md) where X is the target phase number. If it exists, read it for detailed implementation guidance.

Implement all steps in the target phase according to the plan, following these guidelines:
- Complete each step sequentially (skips the ones that are marked as done)
- Update the corresponding checkbox in @plan/PLAN.md from `- [ ]` to `- [x]` immediately after completing each step
- Verify each step works before moving to the next
- Follow the project's architecture and coding standards from CLAUDE.md
- Be efficient and focused - implement exactly what's requested, nothing more

After completing all steps in the phase, verify all checkboxes for that phase are marked as complete in @plan/PLAN.md and update progress counters if present.
