# openclaw-control-console-skill

OpenClaw control-console AgentSkill for keeping the main window lightweight, moving heavy work to background sessions, standardizing kickoff/progress updates, and preventing silent long-running tasks.

## What it does

This skill helps an agent workspace behave like a **control console** instead of a cluttered worksite:

- keep the main/direct window short and operational
- move heavy work into background jobs, isolated sessions, or task-specific threads
- require a short kickoff card before heavy background tasks begin
- require progress updates on a fixed cadence
- default to token-efficient replies with conclusion-first, short-answer behavior
- allow multiple tasks in parallel while serializing write-heavy work on the same resource

## Included files

- `openclaw-control-console-skill/SKILL.md` — main skill instructions
- `openclaw-control-console-skill/references/rules.md` — detailed rule reference and wording
- `dist/openclaw-control-console-skill.skill` — packaged distributable skill

## Recommended use cases

Use this skill when you want an OpenClaw-style assistant to:

- keep the main window concise
- stop dumping long logs into chat
- report heavy-task progress predictably
- avoid long silent background work
- handle multiple tasks without cross-task interference

## Install

Copy the skill folder into your skills directory, or use the packaged `.skill` artifact from `dist/`.

## Suggested workspace policy outcomes

- main window = commands, status, decisions, closeout
- background threads = heavy execution and long evidence
- progress cadence = 5 min on new evidence / 10 min max silent interval / 15 min abnormal threshold
- parallelism = multi-task parallelism, single-resource serialization

## Versioning

This repository includes a Git tag and GitHub release for the initial public version.
