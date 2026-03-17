---
name: sessions
description: List and manage Claude Code sessions with metadata.
user_invocable: true
---

# Sessions Command

Manage session history - list, load, alias, and inspect sessions.

## Commands

- `/sessions list` - Display sessions with metadata (branch, worktree, date)
- `/sessions load <id|alias|date>` - Retrieve session content
- `/sessions alias <id> <name>` - Create memorable name for session
- `/sessions unalias <name>` - Remove an alias
- `/sessions info <id>` - Show detailed statistics
- `/sessions aliases` - Display all configured aliases

## Key Locations

- Sessions: `~/.claude/sessions/`
- Aliases: `~/.claude/session-aliases.json`

## Features

- Sessions persist project, branch, and worktree metadata
- Filter by date, search patterns, pagination
- Session IDs can be shortened to 4-8 characters

## Usage Examples

```
/sessions list
/sessions load 2024-01-15
/sessions alias abc123 today-work
/sessions info today-work
```
