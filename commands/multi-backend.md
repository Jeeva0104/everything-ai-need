---
name: multi-backend
description: Multi-model collaborative backend development with Codex and Gemini.
user_invocable: true
---

# Multi-Backend Command

Multi-model collaborative backend development orchestrating Codex (backend authority) and Gemini (frontend reference).

## Workflow Phases

1. **Prepare** (Optional) - Prompt enhancement if ace-tool MCP available
2. **Research** - Understand requirements, gather context
3. **Ideation** - Codex-led analysis with solution recommendations
4. **Plan** - File structure, function/class design, dependencies
5. **Execute** - Implementation following approved plans
6. **Optimize** - Codex-led review for security, performance
7. **Review** - Final quality evaluation

## Critical Rules

- Responses must start with `[Mode: X]` labels
- Codex opinions are authoritative; Gemini opinions are for reference only
- Claude handles all filesystem operations
- Session IDs must be saved and reused across phases

## Usage

```
/multi-backend <task-description>
```

## Communication Protocol

- Start with mode label (e.g., `[Mode: Research]`)
- Request user confirmation after each phase
- Use `TaskOutput` with 600000ms timeout for waiting on background tasks
