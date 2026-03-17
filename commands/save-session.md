---
name: save-session
description: Save current session state to resume later with full context.
user_invocable: true
---

# Save Session Command

Save current session state to a file for later resumption.

## Output Format

Session files saved to `~/.claude/sessions/YYYY-MM-DD-<short-id>-session.tmp`:

```markdown
# Session: YYYY-MM-DD

**Started:** [approximate time]
**Last Updated:** [current time]
**Project:** [project name or path]
**Topic:** [one-line summary]

---

## What We Are Building

[1-3 paragraphs describing the feature, bug fix, or task]

## What WORKED (with evidence)

- [thing that works] — confirmed by: [evidence]

## What Did NOT Work (and why)

- [approach tried] — failed because: [exact reason]

## What Has NOT Been Tried Yet

- [approach / idea]

## Current State of Files

| File | Status | Notes |
|------|--------|-------|
| `path/to/file.ts` | ✅ Complete | [notes] |

## Decisions Made

- [decision] — reason: [why]

## Blockers & Open Questions

- [blocker / question]

## Exact Next Step

[The single most important thing to do when resuming]

## Environment & Setup Notes

[Commands needed to run, env vars, services, etc.]
```

## Usage

```
/save-session
```

Creates timestamped file in `~/.claude/sessions/`.
