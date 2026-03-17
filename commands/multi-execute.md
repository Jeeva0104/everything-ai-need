---
name: multi-execute
description: Multi-model collaborative execution - get prototype, refactor, implement, audit.
user_invocable: true
---

# Multi-Execute Command

Multi-model collaborative execution: Get prototype from plan → Claude refactors and implements → Multi-model audit and delivery.

## Workflow Phases

- **Phase 0**: Read Plan - Identify task type, route to appropriate model
- **Phase 1**: Quick Context Retrieval - Gather project context
- **Phase 2**: Prototype Acquisition - Gemini for frontend, Codex for backend
- **Phase 3**: Code Implementation - Claude refactors "dirty prototype" to production-grade code
- **Phase 4**: Audit and Delivery - Parallel Codex + Gemini review

## Critical Rules

- Claude has sole filesystem write access
- External model outputs must be refactored before implementation
- Backend follows Codex recommendations; frontend follows Gemini
- Mandatory multi-model audit after changes

## Usage

```
/multi-execute .claude/plan/feature-name.md
```
