# Control Console Rules Reference

## Purpose

Use this skill to convert an assistant workspace into a predictable control-console model:

- main window = command, status, decision, closeout
- heavy work = background, isolated session, or project thread
- long evidence = files, not chat

## Policy blocks

### 1. Main-window lightweight mode

Recommended wording:

- Main window: short commands, short answers, status, decisions
- Heavy work: move to background, isolated sessions, or project-specific threads
- Do not paste long tool output, long logs, long file dumps, or long audit text unless explicitly asked
- Prefer writing detailed evidence to `reports/`, `memory/`, or project files, then reply with the conclusion and path
- If the main window context is already bloated, prefer `/new` or a fresh work thread instead of piling on

### 2. Background-task kickoff card

Required fields:

- `task_id`
- goal
- current step
- next report ETA
- how the user can query progress

Example:

- task_id: `mx2-seo-20260318-01`
- goal: verify status read chain and patch wrong mapping
- current step: locating API read/write anchors
- next report ETA: 8 minutes
- query: `进度 mx2-seo-20260318-01`

### 3. Background-task reporting cadence

Recommended wording:

- Report within 5 minutes when new evidence appears
- Even without new evidence, report status within 10 minutes
- More than 15 minutes without a report counts as abnormal and must be explained before silent work continues

### 4. Compact status format

Default 4-line update:

- `状态`
- `task_id`
- `已完成`
- `下一次回报`

### 5. Standard progress query phrases

- `进度`
- `进度 task_id`
- `当前卡点`
- `停止当前任务`

### 6. Parallelism safety rule

Recommended wording:

- Multiple tasks may run in parallel
- The same project/repo/service/database/deploy target must not have more than one write-heavy task at the same time
- Prefer multi-task parallelism with single-resource serialization

## Workspace-update checklist

When applying this skill to a real workspace:

1. Update workspace notes (`TOOLS.md`) with operational phrasing.
2. Update higher-priority behavior rules (`AGENTS.md`) with the same constraints.
3. Keep the two files aligned.
4. If the user has multiple workspaces, sync the rule set across them.
5. Recommend a fresh session or `/new` so the new behavior starts with clean thread context.
