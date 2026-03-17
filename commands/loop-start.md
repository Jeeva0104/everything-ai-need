---
name: loop-start
description: Start an autonomous agent loop for long-running tasks with checkpoints and failure recovery.
user_invocable: true
---

# Loop Start Command

Start an autonomous agent loop for long-running tasks with checkpointing and failure recovery.

## Usage

```
/loop-start <task-description> [--max-iterations N] [--checkpoint-interval M]
```

## Process

1. **Initialize Loop State**
   - Create loop session ID
   - Set up checkpoint storage
   - Initialize progress tracking

2. **Execute Iterations**
   - Run agent on task
   - Check for completion criteria
   - Create checkpoint on success
   - Handle failures with retry logic

3. **Recovery**
   - On failure: restore from last checkpoint
   - On stall: alert user for intervention
   - On success: report completion

## Options

- `--max-iterations N` - Maximum loop iterations (default: 50)
- `--checkpoint-interval M` - Minutes between checkpoints (default: 10)
- `--auto-recover` - Automatically retry on recoverable failures

## Monitoring

Use `/loop-status` to check active loop state and progress.
