---
description: Create detailed project implementation plan
---

Check README.md, CLAUDE.md, INITIAL.md (if any of them exist) to understand the project structure, goals, and requirements.

Create a comprehensive PLAN.md file at plan/PLAN.md with a detailed implementation plan for the entire project.

Follow these guidelines:

## Structure

1. **Divide into Phases**: Group related work into logical phases (e.g., "Foundation & Setup", "Core Features", "Polish & Testing")
2. **Break into Steps**: Each phase should contain multiple numbered steps
3. **Unique Step Numbers**: Steps must be numbered uniquely across the ENTIRE plan (not restarting in each phase)
4. **Add Checkboxes**: Each step must have a checkbox in the format `- [ ] **Step X**: Description`
5. **Prototyping Focus**: Each step should deliver something visible or testable - use placeholders initially if needed
6. **Incremental Progress**: Design steps so each one builds on the previous and shows clear progress

## Step Characteristics

Each step should:
- Be specific and actionable
- Deliver visible functionality or UI changes when possible
- Use placeholders for content that will be detailed later
- Be completable in a reasonable timeframe
- Follow the project's architecture and design principles

## Format Example

```markdown
# PLAN.md

## Project Implementation Plan

Brief description of the plan's purpose.

---

## Phase 1: Phase Name

- [ ] **Step 1**: Description of first step
- [ ] **Step 2**: Description of second step
- [ ] **Step 3**: Description of third step

---

## Phase 2: Another Phase Name

- [ ] **Step 4**: Description continuing unique numbering
- [ ] **Step 5**: Next step description

---

## Notes

- Important notes about the implementation approach
- Reminders about updating checkboxes as steps complete
```

## Important

- The plan should reflect the incremental, prototyping-focused approach described in the project documentation
- Steps should be granular enough to show progress but not so small that they become tedious
- Each step completion should be immediately visible to users or developers
- Make sure the CLAUDE.md file contains instructions for updating checkboxes after completing steps
