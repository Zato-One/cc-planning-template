---
description: Implement a given phase
argument-hint: <phase-number>
---

**IMPORTANT: Safety Checks**

1. **Check if plan/PLAN.md exists:**
   - If it does NOT exist, STOP and tell the user: "⚠️ No plan/PLAN.md found. Please run /plan first to create the main project plan before implementing phases."
   - If it exists, proceed to the next check.

2. **Determine the target phase number:**
   - If no phase number is provided as $1, check @plan/PLAN.md to find the next phase that has at least one uncompleted step (checkbox not marked as `[x]`). Use that phase number for implementation.
   - If a phase number is provided, use that phase number.

3. **Check if the detailed phase plan exists:**
   - Check if /plan/phases/PHASE_X.md exists (with zero-padding for single digits, e.g., PHASE_01.md, PHASE_02.md) where X is the target phase number.
   - If it does NOT exist, STOP and ask the user: "⚠️ No detailed plan found for Phase X at /plan/phases/PHASE_0X.md. Would you like to:
     1. Continue without a detailed phase plan (I'll work from plan/PLAN.md only)
     2. Run /plan-phase X first to create a detailed plan for this phase"
   - Wait for the user's response before proceeding.

---

Check @plan/PLAN.md to identify all steps in the target phase.

Check if a detailed phase plan exists at /plan/phases/PHASE_X.md (with zero-padding for single digits, e.g., PHASE_01.md, PHASE_02.md) where X is the target phase number. If it exists, read it for detailed implementation guidance.

Implement all steps in the target phase according to the plan, following these guidelines:
- Complete each step sequentially (skips the ones that are marked as done)
- Update the corresponding checkbox in @plan/PLAN.md from `- [ ]` to `- [x]` immediately after completing each step
- Verify each step works before moving to the next
- Follow the project's architecture and coding standards from CLAUDE.md
- Be efficient and focused - implement exactly what's requested, nothing more

After completing all steps in the phase, verify all checkboxes for that phase are marked as complete in @plan/PLAN.md and update progress counters if present.
