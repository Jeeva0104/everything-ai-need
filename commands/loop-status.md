---
name: loop-status
description: Inspect active loop state, progress, and failure signals.
user_invocable: true
---

# Loop Status Command

Inspect active loop state, progress, and failure signals.

## Usage

```
/loop-status [--watch]
```

## What to Report

- Active loop pattern
- Current phase and last successful checkpoint
- Failing checks (if any)
- Estimated time/cost drift
- Recommended intervention (continue/pause/stop)

## Watch Mode

When `--watch` is present, refresh status periodically and surface state changes.

## Arguments

$ARGUMENTS:
- `--watch` optional
