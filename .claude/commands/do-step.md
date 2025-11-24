---
description: Implement a given step
argument-hint: <step-number>
---

**IMPORTANT: Safety Checks**

1. **Check if plan/PLAN.md exists:**
   - If it does NOT exist, STOP and tell the user: "⚠️ No plan/PLAN.md found. Please run /plan first to create the main project plan before implementing steps."
   - If it exists, proceed to the next check.

2. **Determine the target step number:**
   - If no step number is provided as $1, check @plan/PLAN.md to find the next step (in sequential order) that is not marked as complete (checkbox not marked as `[x]`). Use that step number for implementation.
   - If a step number is provided, use that step number.

3. **Check @plan/PLAN.md to:**
   - Identify which phase contains the target step
   - Understand what the target step should accomplish

4. **Check if the detailed phase plan exists:**
   - Find the phase number for this step, then check if a detailed phase plan exists at /plan/phases/PHASE_X.md (with zero-padding for single digits, e.g., PHASE_01.md, PHASE_02.md).
   - If it does NOT exist, STOP and ask the user: "⚠️ No detailed plan found for Phase X (which contains Step Y) at /plan/phases/PHASE_0X.md. Would you like to:
     1. Continue without a detailed phase plan (I'll work from plan/PLAN.md only)
     2. Run /plan-phase X first to create a detailed plan for this phase"
   - Wait for the user's response before proceeding.

---

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
