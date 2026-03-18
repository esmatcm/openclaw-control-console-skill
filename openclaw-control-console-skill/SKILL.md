---
name: openclaw-control-console-skill
description: Enforce lightweight main-window behavior and disciplined background-task execution for OpenClaw-style assistant workspaces. Use when creating or improving an AgentSkill that should keep the main/direct window short, move heavy work into background or isolated sessions, standardize kickoff cards and progress updates, prevent silent long-running tasks, or allow multi-task parallelism with single-resource serialization.
---

# OpenClaw Control Console Skill

Keep the direct or main window as a control console, not a worksite.

## Core workflow

1. Treat the main window as the place for commands, status, decisions, and final summaries.
2. Move heavy work into background jobs, isolated sessions, or task-specific threads.
3. Send a short kickoff card before a heavy background task starts.
4. Keep progress reports compact and time-bounded.
5. Allow multiple tasks in parallel, but serialize write-heavy work that touches the same resource.

## Main-window rules

Apply these defaults unless the user explicitly asks for full detail:

- Keep replies short and operational.
- Do not paste long tool output, long logs, long file dumps, or long audit text into the main window.
- Put detailed evidence into files such as `reports/`, `memory/`, or project artifacts, then reply with the conclusion and path.
- If the current thread is already bloated, prefer a fresh thread or `/new` rather than continuing to pile on.

## Background-task rules

Before a heavy task goes into the background, send a short kickoff card with:

- `task_id`
- goal
- current step
- next report ETA
- how the user can query progress

Default progress cadence:

- Report within 5 minutes when new evidence appears.
- Even without new evidence, send a status update within 10 minutes.
- More than 15 minutes without a status update is abnormal; explain the blockage or current state before continuing silent work.

Default compact progress format:

- `状态`
- `task_id`
- `已完成`
- `下一次回报`

Default progress query phrases:

- `进度`
- `进度 task_id`
- `当前卡点`
- `停止当前任务`

## Parallelism rules

Permit multiple tasks in parallel only when they do not compete for the same write target.

Use this rule:

- multiple tasks may run in parallel
- the same project, repo, service, database, or deploy target must not have more than one write-heavy task at the same time
- prefer multi-task parallelism with single-resource serialization

## Reference

Load `references/rules.md` when you need the full rule set, rationale, or example wording for workspace policy updates.
