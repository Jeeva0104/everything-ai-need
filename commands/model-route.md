---
name: model-route
description: Recommend the best model tier for the current task by complexity and budget.
user_invocable: true
---

# Model Route Command

Recommend the best model tier for the current task by complexity and budget.

## Usage

```
/model-route [task-description] [--budget low|med|high]
```

## Routing Heuristic

- `haiku`: deterministic, low-risk mechanical changes
- `sonnet`: default for implementation and refactors
- `opus`: architecture, deep review, ambiguous requirements

## Required Output

- Recommended model
- Confidence level
- Why this model fits
- Fallback model if first attempt fails

## Arguments

$ARGUMENTS:
- `[task-description]` optional free-text
- `--budget low|med|high` optional
