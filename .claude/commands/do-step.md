---
description: Implement a given step
argument-hint: <step-number>
---

If no step number is provided as $1, check @plan/PLAN.md to find the next step (in sequential order) that is not marked as complete (checkbox not marked as `[x]`). Use that step number for implementation.

Check @plan/PLAN.md to:
1. Identify which phase contains the target step
2. Understand what the target step should accomplish

Find the phase number for this step, then check if a detailed phase plan exists at /plan/phases/PHASE_X.md (with zero-padding for single digits, e.g., PHASE_01.md, PHASE_02.md). If it exists, read it for detailed implementation guidance for the target step.

Implement the target step according to the plan, following these guidelines:
- Focus on completing only this specific step
- Follow the detailed instructions from the phase plan if available
- Update the checkbox in @plan/PLAN.md from `- [ ]` to `- [x]` immediately after completing the step
- Update progress counters if present (e.g., "Completed Steps" count, "Overall Progress" percentage)
- Verify the step works as expected
- Follow the project's architecture and coding standards from CLAUDE.md
- Be efficient and focused - implement exactly what's requested, nothing more

After completing the step, confirm the checkbox for the target step is marked as `[x]` in @plan/PLAN.md.
