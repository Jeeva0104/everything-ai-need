---
name: multi-workflow
description: 6-phase multi-model collaborative development workflow.
user_invocable: true
---

# Multi-Workflow Command

Complete 6-phase multi-model development workflow.

## Phases

1. **Research** - Enhance prompts, gather context, score requirements (≥7 to proceed)
2. **Ideation** - Parallel analysis via Codex (backend) and Gemini (frontend)
3. **Plan** - Collaborative architecture planning
4. **Execute** - Code implementation following approved plans
5. **Optimize** - Parallel security/performance review
6. **Review** - Final quality verification

## Key Technical Elements

- **Orchestration**: Claude coordinates Codex and Gemini
- **Session Management**: `resume <SESSION_ID>` for multi-phase collaboration
- **Parallel Execution**: Background tasks with `TaskOutput` synchronization
- **Quality Gates**: Score <7 or user rejection triggers force stop

## Usage

```
/multi-workflow <project-description>
```

## MCP Integration

Uses ace-tool MCP services for enhanced context retrieval and prompt improvement.
