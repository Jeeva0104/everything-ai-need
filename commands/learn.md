---
name: learn
description: Extract patterns from session and create SKILL.md files for reusable knowledge.
user_invocable: true
---

# Learn Command

Extract valuable patterns from the current session and save them as skills for future use.

## Usage

```
/learn                          # Auto-detect patterns from session
/learn <pattern-name>           # Save with specific name
/learn --instincts              # Also generate instincts
```

## Output Format

Skill files are saved to `~/.claude/skills/learned/[pattern-name].md`:

```markdown
# [Descriptive Pattern Name]

**Extracted:** [Date]
**Context:** [Brief description of when this applies]

## Problem
[What problem this solves - be specific]

## Solution
[The pattern/technique/workaround]

## Example
[Code example if applicable]

## When to Use
[Trigger conditions - what should activate this skill]
```

## Process

1. Review the session for valuable, reusable insights
2. Identify error resolution patterns, debugging techniques, workarounds
3. Draft the skill file
4. Confirm with user before saving
5. Skip trivial fixes or one-off issues

## What to Extract

- Error resolution patterns
- Debugging techniques
- Workarounds for known issues
- Project-specific conventions
- Language/framework tricks

## Related

- `/skill-create` - Analyze git history to generate skills
- `/evolve` - Cluster instincts into skills
