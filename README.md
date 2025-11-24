# Claude Code Planning Template

A GitHub template repository that provides a structured planning and development infrastructure for Claude Code projects.

## Overview

This template enables developers to plan projects in detail and let Claude Code implement them incrementally, phase by phase and step by step. It includes pre-configured guidance files, custom slash commands, and MCP integration for semantic code operations.

## Features

- **Structured Planning Workflow**: From initial brainstorming to detailed implementation plans
- **Custom Slash Commands**: Automation for planning and implementation tasks
- **Claude Code Guidance**: Pre-configured CLAUDE.md with best practices and instructions
- **Serena MCP Integration**: Semantic code understanding and manipulation tools
- **Incremental Development**: Phase-based and step-based implementation tracking

## Getting Started

### 1. Use This Template

Click "Use this template" on GitHub to create a new repository.

### 2. Initial Setup

**IMPORTANT**: Before starting development:
- Either remove this README.md or rewrite it for your specific project
- Update the LICENSE file with your name/organization or choose a different license

Create an `INITIAL.md` file with all your project details:
- Brainstorming notes and ideas
- Technology stack decisions
- Planned project structure
- Feature requirements
- Architecture decisions
- Any other planning information

You can also use README.md for initial planning if you prefer.

### 3. Generate Implementation Plan

Run the `/plan` command in Claude Code:

This analyzes your INITIAL.md (and README.md if modified) and creates a comprehensive `plan/PLAN.md` file with:
- Logical phases grouping related work
- Numbered steps with checkboxes for tracking
- Incremental, prototyping-focused approach

### 4. Optional: Create Detailed Phase Plans

Run `/plan-phase <phase-number>` to create detailed implementation guidance:

This generates `plan/phases/PHASE_0X.md` with granular implementation details for the specified phase.

### 5. Implement Your Project

Choose your implementation approach:

**Implement an Entire Phase:**

This completes all steps in the phase sequentially and updates checkboxes automatically.

**Implement Individual Steps:**

Or implement the next uncompleted step:

**Ask Questions Without Making Changes:**

## Custom Slash Commands

### `/plan`
Creates a comprehensive implementation plan at `plan/PLAN.md`
- Analyzes README.md, CLAUDE.md, and INITIAL.md
- Divides project into logical phases
- Creates numbered steps with checkboxes
- Focuses on incremental, visible progress

### `/plan-phase <phase-number>`
Creates detailed phase plan at `plan/phases/PHASE_0X.md`
- Optional but recommended for complex phases
- Provides granular implementation guidance
- Referenced by `/do-phase` and `/do-step` commands

### `/do-phase <phase-number>`
Implements all steps in a given phase
- Completes steps sequentially
- Updates checkboxes in PLAN.md automatically
- Skips already completed steps
- Verifies each step before proceeding

If no phase number provided, finds and implements the next phase with uncompleted steps.

### `/do-step <step-number>`
Implements a single step from the plan
- Focuses on one specific step
- Updates checkbox immediately after completion
- Updates progress counters if present

If no step number provided, finds and implements the next uncompleted step.

### `/ask <your question>`
Answers questions without modifying files
- Information-only mode
- No code or file changes
- Useful for understanding codebase or clarifying approaches

## Claude Code Hooks

This template includes a pre-configured Stop hook in `.claude/settings.json`.

### Stop Hook
Automatically reviews user prompts when the Stop event is triggered:
- Analyzes English grammar, clarity, and style
- Outputs the original prompt
- Provides a corrected version with explanations of changes
- Helps improve communication with Claude Code

## CLAUDE.md Guidance File

The `CLAUDE.md` file provides Claude Code with:
- Development workflow guidelines
- Implementation plan tracking instructions
- Task execution principles
- Code quality standards
- Security best practices
- Documentation guidelines
- Over-engineering avoidance rules

Claude Code automatically reads and follows these instructions when working in this repository.

## Serena MCP Integration

This template includes Serena MCP server configuration (`.mcp.json`) for:
- Semantic code understanding
- Symbol-based code operations
- Intelligent code search and navigation
- Token-efficient codebase exploration

Serena enables Claude Code to work with your codebase at a semantic level, understanding relationships between code symbols rather than just text patterns.

## Project Structure

After setup, your project will have:

- `INITIAL.md` - Your initial project planning and requirements
- `CLAUDE.md` - Claude Code guidance and instructions
- `plan/PLAN.md` - Comprehensive implementation plan with checkboxes
- `plan/phases/PHASE_0X.md` - Optional detailed phase plans
- `.claude/commands/` - Custom slash command definitions
- `.mcp.json` - MCP server configuration

## Attribution

Some sections of this template are inspired by or adapted from Cole Medin's context engineering work:
- Original work: https://github.com/coleam00/context-engineering-intro
- Copyright (c) 2025 Cole Medin
- Licensed under MIT License

## License

MIT License - See LICENSE file for details

Copyright (c) 2025 David Savič