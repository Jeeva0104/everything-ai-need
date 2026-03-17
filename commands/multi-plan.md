---
name: multi-plan
description: Multi-model collaborative planning with parallel Codex and Gemini analysis.
user_invocable: true
---

# Multi-Plan Command

Multi-model collaborative planning with mandatory parallel execution.

## Core Protocols

- **Language**: All outputs in English (mandatory)
- **Parallel Execution**: Codex + Gemini must run simultaneously
- **Code Sovereignty**: Claude makes final implementation decisions
- **Stop-Loss**: Quality score < 7 triggers halt

## Execution Workflow

1. **Context Retrieval** - Gather requirements and project context
2. **Multi-Model Collaborative Analysis**
   - Parallel calls to Codex (backend) and Gemini (frontend)
   - Synthesize into unified plan
3. **Plan Delivery** - Save to `.claude/plan/<feature-name>.md`

## Usage

```
/multi-plan <feature-description>
```

## Output Format

Plans saved with structured sections for implementation handoff.
