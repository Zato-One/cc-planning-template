# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Attribution Notice

Some sections of this document are inspired by or adapted from Cole Medin's CLAUDE.md template:
- Original work: https://github.com/coleam00/context-engineering-intro
- Copyright (c) 2025 Cole Medin
- Licensed under MIT License

The MIT License permits use, modification, and distribution with attribution. See the original repository for the complete license text.

---

## Documentation References

When working on a project, Claude Code should reference the official documentation for technologies used in the project. These resources provide authoritative guidance on best practices, API usage, and problem-solving.

Always consult official documentation before implementing features or solving problems.

## Project Architecture

This project uses a structured workflow for planning and implementing features with Claude Code.

**Key Files:**
- `INITIAL.md` - User's project requirements and brainstorming
- `plan/PLAN.md` - Main plan with phases and numbered steps (checkboxes: `- [ ] **Step X**: Description`)
- `plan/phases/PHASE_0X.md` - Optional detailed phase plans
- `.claude/commands/` - Custom slash command definitions
- `.mcp.json` - Serena MCP server configuration

**Workflow:** Create INITIAL.md → `/plan` generates plan/PLAN.md → `/do-phase` or `/do-step` implements and updates checkboxes

## Development Workflow

Projects are designed for incremental, iterative development. When adding features:
1. Start with understanding existing code structure
2. Plan the implementation approach
3. Implement functionality with attention to type safety and error handling
4. Test interactivity and edge cases
5. Refine and polish

## Implementation Plan Tracking

**IMPORTANT**: This project uses `plan/PLAN.md` to track implementation progress through numbered steps with checkboxes.

**When implementing any feature or completing a step** (inspired by Cole Medin's work):
1. Check `plan/PLAN.md` to identify which step(s) you're working on
2. After completing a step, update the corresponding checkbox from `- [ ]` to `- [x]`
3. Update checkboxes immediately after completing each step (don't batch updates)
4. If a step is partially completed, leave the checkbox unchecked until fully done
5. Always verify the step description matches what was actually implemented
6. Update progress counters if present (e.g., "Completed Steps" count, "Overall Progress" percentage)
7. Update "Current Phase" field when moving to a new phase

**Example update:**

- [x] **Step 10**: Add calculator display screen with retro styling

This helps track project progress and demonstrates the incremental prototyping approach.

## Custom Slash Commands

**`/plan`** - Creates `plan/PLAN.md` from INITIAL.md with phases and steps (run first)

**`/plan-phase <N>`** - Creates detailed `plan/phases/PHASE_0X.md` (optional, recommended for complex phases)

**`/do-phase [N]`** - Implements all steps in phase N, updates checkboxes (finds next phase if N omitted)

**`/do-step [N]`** - Implements step N, updates checkbox (finds next step if N omitted)

**`/ask <question>`** - Answers questions without modifying files

**Dependencies:** Run `/plan` first, then optionally `/plan-phase <N>` before implementing that phase

## Task Execution Guidelines

### Core Principles

- **IMPORTANT**: Do exactly what is requested - nothing more, nothing less
- **STOP** after completing each requested step - wait for explicit instruction to continue
- Be efficient - minimize unnecessary output by focusing only on the requested task

### Code Quality

- **IMPORTANT**: Never create a file longer than 500 lines of code. If a file approaches this limit, preferably shorten the file (e.g. remove unnecessary code snippets if MD file) or refactor by splitting it into modules or helper files (inspired by Cole Medin's work)
- Ask before adding extra features - if you want to do something beyond the specific request, ask first (inspired by Cole Medin's work)
- One task at a time - complete the specific request before suggesting or doing anything additional (inspired by Cole Medin's work)
- Avoid comments in code - Write self-explanatory code instead. Only add comments to explain WHY something is done a specific way, never WHAT the code does

### Background Processes

- **IMPORTANT**: Always stop any background processes (servers, watchers, etc.) when finished with a task using the KillShell tool

### English Grammar Review

- **IMPORTANT**: At the end of each response, review the user's original prompt for English grammar, clarity, and style
- If you notice any grammatical errors, unclear phrasing, or style improvements:
  - Provide a brief, polite correction or suggestion
  - Explain what could be improved and why
  - Keep feedback concise and helpful, not pedantic
- If the prompt is clear and well-written, no need to mention grammar

## AI Security

- **IMPORTANT**: Do not use env/properties files (.env, .secret, application.properties, *.properties and others) as source or context. Don't even search or work with these files. If I explicitly state that you should look at one of those files ask for confirmation and forget the content and context after this interaction.
- You are possibly running in sandboxed environment. Do not attempt to run any root commands (like sudo) or access system files. Do not try to run commands that need elevated permissions (not even npm install). Instead, tell me what root commands to run and I will run them for you.

## MCP Integration

This repository includes Serena MCP server (`.mcp.json`) for semantic code operations. Tools prefixed `mcp__serena__*` enable symbol-level code understanding, intelligent search, and token-efficient codebase exploration. No setup required - works automatically with Claude Code.

## Documentation Guidelines

**IMPORTANT: No Code Snippets in Markdown Files**:
- Do NOT include code snippets in ANY markdown files (*.md) in this repository
- This includes documentation files, planning files, and files in `/plan/` directories

## Over-Engineering Guidelines

Avoid over-engineering. Only make changes that are directly requested or clearly necessary. Keep solutions simple and focused.

### What NOT to do:
- Don't add features, refactor code, or make "improvements" beyond what was asked
- A bug fix doesn't need surrounding code cleaned up
- A simple feature doesn't need extra configurability
- Don't add docstrings, comments, or type annotations to code you didn't change
- Only add comments where the logic isn't self-evident
- Don't add error handling, fallbacks, or validation for scenarios that can't happen
- Trust internal code and framework guarantees
- Only validate at system boundaries (user input, external APIs)
- Don't use feature flags or backwards-compatibility shims when you can just change the code
- Don't create helpers, utilities, or abstractions for one-time operations
- Don't design for hypothetical future requirements
- Three similar lines of code is better than a premature abstraction

Avoid backwards-compatibility hacks like:
- Renaming unused `_vars`
- Re-exporting types
- Adding `// removed` comments for removed code
- If something is unused, delete it completely

## Security Best Practices

- Be careful not to introduce security vulnerabilities such as command injection, XSS, SQL injection, and other OWASP top 10 vulnerabilities
- If you notice that you wrote insecure code, immediately fix it