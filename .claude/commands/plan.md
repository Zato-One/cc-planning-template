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
7. **Phase Validation**: Each phase MUST include validation as the last step(s) to verify successful delivery

## Phase Description Requirements

Each phase description must clearly state:
- **What the phase brings**: New functionality, features, or capabilities delivered
- **How it's validated**: Specific validation method(s) to verify successful delivery

**Prefer manual UI validation when possible** - if the phase adds visible changes, manual testing is the simplest and most effective validation.

## Phase Validation Requirements

**IMPORTANT**: Each phase MUST end with validation step(s) as the final step(s) of that phase.

Validation options (choose what makes sense for the phase):
1. **Manual UI Testing** (preferred when applicable): Clear instructions for manually testing visible changes
2. **Integration Tests**: Automated tests covering new backend functionality, database structures, or API endpoints
3. **Other Validation**: Any other appropriate method that clearly verifies the phase delivers what it promises

Guidelines:
- Keep validation simple - one validation type is usually enough, but use more if needed
- Validation should cover just what's needed to verify the phase is successful
- Make validation steps clear and actionable
- Validation must be the LAST step(s) of each phase

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

**What this phase brings**: Description of new functionality/features delivered in this phase

**Validation**: Manual UI testing of the new feature/functionality OR integration tests covering the new backend changes

- [ ] **Step 1**: Description of first step
- [ ] **Step 2**: Description of second step
- [ ] **Step 3**: Description of third step
- [ ] **Step 4**: Validate Phase 1 - [specific validation instructions, e.g., "Manual test: Verify login form displays correctly and accepts input" OR "Run integration tests for new user authentication endpoints"]

---

## Phase 2: Another Phase Name

**What this phase brings**: Description of what this phase adds

**Validation**: How this phase will be validated

- [ ] **Step 5**: Description continuing unique numbering
- [ ] **Step 6**: Next step description
- [ ] **Step 7**: Validate Phase 2 - [specific validation instructions]

---

## Notes

- Important notes about the implementation approach
- Reminders about updating checkboxes as steps complete
- Each phase must end with validation step(s)
```

## Important

- The plan should reflect the incremental, prototyping-focused approach described in the project documentation
- Steps should be granular enough to show progress but not so small that they become tedious
- Each step completion should be immediately visible to users or developers
- **Each phase MUST include validation step(s) as the final step(s) to verify successful delivery**
- **Each phase description MUST clearly state what it brings and how it will be validated**
- **Prefer manual UI validation when the phase includes visible changes**
- Make sure the CLAUDE.md file contains instructions for updating checkboxes after completing steps
