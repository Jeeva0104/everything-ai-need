---
name: resume-session
description: Load the most recent session file and resume work with full context.
user_invocable: true
---

# Resume Session Command

Load the last saved session state and orient fully before doing any work.

## When to Use

- Starting a new session to continue work from a previous day
- After starting a fresh session due to context limits
- When handing off a session file from another source
- Any time you have a session file and want Claude to fully absorb it

## Usage

```
/resume-session                                          # loads most recent
/resume-session 2024-01-15                               # loads date
/resume-session ~/.claude/sessions/2024-01-15-session.tmp # specific file
```

## Process

### Step 1: Find the session file
Check `~/.claude/sessions/` for most recent `*-session.tmp` file.

### Step 2: Read the entire session file
Read complete file without summarizing yet.

### Step 3: Confirm understanding
Respond with structured briefing including:
- PROJECT
- WHAT WE'RE BUILDING
- CURRENT STATE
- WHAT NOT TO RETRY
- OPEN QUESTIONS / BLOCKERS
- NEXT STEP

### Step 4: Wait for the user
Do NOT start working automatically. Wait for user direction.
