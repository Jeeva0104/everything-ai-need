---
name: devfleet
description: Multi-agent orchestration for complex projects.
user_invocable: true
---

# DevFleet Command

Multi-agent orchestration for complex projects. Plans missions, dispatches agents in isolated worktrees, and monitors progress.

## Workflow

1. **Plan**: Break project into missions with dependencies
2. **Approve**: Review plan and approve missions
3. **Dispatch**: Start first mission in isolated worktree
4. **Monitor**: Track mission status and auto-dispatch next

## Commands

- `/devfleet plan <project-description>` - Create mission plan
- `/devfleet dispatch <mission-id>` - Start a mission
- `/devfleet status` - Check all mission statuses
- `/devfleet report` - Get completion report

## Tools

- `plan_project` - Create mission structure
- `dispatch_mission` - Launch agent in worktree
- `get_mission_status` - Check progress
- `get_report` - Read structured report

## Guidelines

- Always get user approval before dispatching
- Handle errors by pausing for user decision
- Support concurrent missions when no dependencies
- Reports are structured markdown with completion status
