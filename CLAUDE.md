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

This is a GitHub template repository for planning and implementing projects with Claude Code. It provides structured planning workflows and custom slash commands to enable incremental, phase-based development.

### Core Components

**Planning Files:**
- `INITIAL.md` - User-created file containing project requirements, brainstorming notes, and initial planning
- `plan/PLAN.md` - Main implementation plan with phases and numbered steps with checkboxes
- `plan/phases/PHASE_0X.md` - Optional detailed plans for specific phases

**Configuration:**
- `CLAUDE.md` - This file, providing guidance to Claude Code
- `.mcp.json` - Serena MCP server configuration for semantic code operations
- `.claude/commands/` - Custom slash command definitions

**Automation:**
- `.github/workflows/template-cleanup.yml` - Automatically cleans up template-specific content on first push to main branch

### Planning Workflow Architecture

The template follows a structured workflow:

1. **Initial Planning**: User creates `INITIAL.md` with project requirements and goals
2. **Plan Generation**: `/plan` command analyzes requirements and creates `plan/PLAN.md` with phases and numbered steps
3. **Optional Detailed Planning**: `/plan-phase <N>` creates detailed implementation guidance for specific phases
4. **Implementation**: `/do-phase <N>` or `/do-step <N>` implements work and automatically updates checkboxes
5. **Progress Tracking**: Checkboxes in `plan/PLAN.md` track completion status across all phases

### Directory Structure

After setup, projects will have:
- `plan/PLAN.md` - Master plan with all phases and steps
- `plan/phases/PHASE_01.md`, `PHASE_02.md`, etc. - Detailed phase plans (optional)
- Step numbers are unique across the entire plan (not reset per phase)
- Checkboxes format: `- [ ] **Step X**: Description`

### Template Initialization

This is a GitHub template repository. When users create a new repository from this template:
- The cleanup workflow automatically replaces README.md and LICENSE on first push to main
- CLAUDE.md, custom commands, and MCP configuration remain intact
- Users should create INITIAL.md with their project requirements to begin

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

This repository includes custom slash commands to automate planning and implementation workflows. These commands are defined in `.claude/commands/` and are available when working in this repository.

### Available Commands

**`/plan`** - Create comprehensive implementation plan
- Analyzes `INITIAL.md`, `README.md`, and `CLAUDE.md` to understand project requirements
- Creates `plan/PLAN.md` with phases and numbered steps with checkboxes
- Must be run first before other planning/implementation commands
- Focuses on incremental, prototyping-focused approach

**`/plan-phase <phase-number>`** - Create detailed phase plan
- Creates `plan/phases/PHASE_0X.md` with granular implementation details
- Optional but recommended for complex phases
- Requires `plan/PLAN.md` to exist (run `/plan` first)
- Referenced by `/do-phase` and `/do-step` for implementation guidance

**`/do-phase [phase-number]`** - Implement entire phase
- Implements all steps in the specified phase sequentially
- If no phase number provided, finds and implements next phase with uncompleted steps
- Skips already completed steps (marked with `[x]`)
- Updates checkboxes in `plan/PLAN.md` automatically after each step
- Verifies each step before proceeding to next

**`/do-step [step-number]`** - Implement single step
- Implements one specific step from the plan
- If no step number provided, finds and implements next uncompleted step
- Updates checkbox immediately after completion
- Updates progress counters if present in plan

**`/ask <your question>`** - Ask questions without modifications
- Information-only mode - no code or file changes
- Useful for understanding codebase or clarifying approaches before implementation

### Command Dependencies

**IMPORTANT**: Commands have dependencies that must be respected:
1. Run `/plan` before any other commands
2. Run `/plan-phase <N>` before `/do-phase <N>` or `/do-step` in that phase (optional but recommended)
3. The `/do-*` commands will prompt if required files are missing

### Automatic Step Finding

Both `/do-phase` and `/do-step` can operate without arguments:
- They will automatically find the next uncompleted work in sequential order
- Useful for continuing implementation without tracking which step is next
- Simply run `/do-step` repeatedly to work through the plan incrementally

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

This repository includes pre-configured Serena MCP (Model Context Protocol) server integration for semantic code understanding and manipulation.

### What is Serena MCP?

Serena is an MCP server that provides semantic code operations, enabling Claude Code to:
- Understand code at the symbol level (functions, classes, variables) rather than just text
- Navigate codebases efficiently using semantic relationships
- Perform token-efficient exploration of large codebases
- Execute intelligent code search and operations

### Configuration

The `.mcp.json` file is pre-configured with Serena MCP server settings:
- Uses `uvx` to run Serena from its GitHub repository
- Configured for "ide-assistant" context
- No additional setup required - works out of the box with Claude Code

### Available MCP Tools

Serena provides tools prefixed with `mcp__serena__*`:
- `mcp__serena__list_dir` - List directory contents semantically
- `mcp__serena__get_symbols_overview` - Get overview of code symbols
- `mcp__serena__activate_project` - Activate project for semantic operations
- `mcp__serena__find_file` - Find files by name or pattern
- `mcp__serena__find_symbol` - Find symbols (functions, classes) in codebase
- `mcp__serena__search_for_pattern` - Search for code patterns semantically
- `mcp__serena__think_about_collected_information` - Analyze collected code information
- `mcp__serena__insert_after_symbol` - Insert code after specific symbols

### Usage

Claude Code automatically has access to these MCP tools when working in this repository. The tools enable more intelligent code exploration and manipulation compared to text-based search alone.

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