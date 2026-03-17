---
name: update-docs
description: Automate documentation updates from source-of-truth files.
user_invocable: true
---

# Update Docs Command

Automate documentation updates from source-of-truth files.

## Process Overview

1. **Identify Sources of Truth** - Map source files to doc outputs
2. **Generate Script Reference** - Extract commands from package.json/Makefile
3. **Generate Environment Documentation** - Parse .env.example files
4. **Update Contributing Guide** - Auto-generate setup, testing sections
5. **Update Runbook** - Auto-generate deployment, health checks
6. **Staleness Check** - Flag docs not modified in 90+ days
7. **Show Summary** - Display update results

## Key Rules

- Always generate from code, never manually edit generated sections
- Preserve hand-written prose in manual sections
- Use `<!-- AUTO-Generated -->` markers
- Only create new doc files when explicitly requested

## Usage

```
/update-docs
/update-docs --check-stale
/update-docs --generate-ref
```
