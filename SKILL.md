---
name: linear-mcp-tracker
description: Enforce project-specific Linear workflow rules from a `LINEAR_MCP.md` file. Use when working inside a repository or project folder that defines `LINEAR_MCP.md`, especially for implementation, bug fixing, reviews, refactors, or any task that should be tracked in Linear. The skill requires Codex to read `LINEAR_MCP.md`, follow its issue-writing rules, create or find the correct issue, keep statuses and assignees in sync, and leave progress comments as work advances.
---

# Linear MCP Tracker

## Overview

Use this skill whenever the current project contains a `LINEAR_MCP.md` file. Treat that file as the authoritative process contract for how work must be represented in Linear during the task.

## Core Rule

Find `LINEAR_MCP.md` before doing substantial work. Read it and follow it strictly.

If multiple `LINEAR_MCP.md` files exist, use the nearest one that governs the files or folder being changed. If scope is ambiguous, say so and use the closest project-level file.

If no `LINEAR_MCP.md` exists, this skill does not apply.

## Required Workflow

### 1. Load project tracking rules

- Locate `LINEAR_MCP.md`.
- Read it before planning, coding, reviewing, or shipping.
- Extract the required rules for:
  - issue naming
  - issue creation
  - status transitions
  - assignee handling
  - comments and progress updates
  - project, label, cycle, or milestone placement
  - completion criteria

### 2. Map the user request to Linear

- Check whether an existing Linear issue already matches the requested work.
- If the request references an issue explicitly, use that issue unless `LINEAR_MCP.md` says otherwise.
- If no matching issue exists, create one before substantial implementation.
- Write the issue in the format required by `LINEAR_MCP.md`.

### 3. Sync at work start

- Move the issue to the correct starting status from `LINEAR_MCP.md`.
- Assign the issue if `LINEAR_MCP.md` requires assignment.
- Add a short start comment when required.

Default start comment shape if the file requires progress comments but does not define a template:

```md
Начал работу над задачей.

План:
- <step 1>
- <step 2>
```

### 4. Sync during execution

- When a meaningful part of the task is finished, update Linear instead of waiting until the very end.
- Add a comment describing what changed, what remains, and any blocker if relevant.
- Update status when the task has clearly moved to the next phase.
- If scope expands, create follow-up issues or sub-issues when `LINEAR_MCP.md` requires that.

Use progress comments for:
- completed implementation chunks
- discovered blockers or scope changes
- partial delivery that is usable but not fully complete
- validation or review milestones

Avoid noisy comments for trivial edits or micro-steps unless the file explicitly requires them.

Default progress comment shape if the file requires comments but gives no template:

```md
Обновление по задаче:

- Сделано: <done>
- Проверено: <verification>
- Дальше: <next>
```

### 5. Sync at completion

- When the requested work is complete, leave a final comment if required.
- Update the issue to the correct final status from `LINEAR_MCP.md`.
- Reassign or unassign only if the file explicitly requires it.
- If the work only partially completes the issue, do not mark it done; leave a clear partial-progress comment instead.

Default completion comment shape if the file requires comments but gives no template:

```md
Завершил работу по задаче.

- Сделано: <summary>
- Проверка: <tests / manual verification / review>
- Остаточные риски: <risks or none>
```

## Operating Rules

- Prefer updating the existing issue over creating duplicates.
- Do not silently skip Linear sync steps that `LINEAR_MCP.md` requires.
- If project instructions conflict with the user request, surface the conflict explicitly.
- If a required Linear action cannot be completed, say what failed and continue the main task when safe.
- Keep comments concise and factual.
- Match the project language. If `LINEAR_MCP.md` is in Russian, write issues and comments in Russian unless the file says otherwise.

## Execution Checklist

Run this checklist for every applicable task:

1. Find and read `LINEAR_MCP.md`.
2. Identify or create the Linear issue.
3. Set the correct starting status and assignee.
4. Implement or review the work.
5. Post progress comments at meaningful milestones.
6. Update status as the task moves.
7. Post a final comment or partial-progress comment.
8. Leave Linear in a state that accurately reflects the current reality.

## Good Triggers

- "Сделай задачу в этом репозитории"
- "Почини баг и обнови Linear"
- "Реализуй фичу по проекту"
- "Сделай review и отметь прогресс в Linear"
- any coding task in a project that contains `LINEAR_MCP.md`

## Bad Triggers

- tasks outside a project context
- projects without `LINEAR_MCP.md`
- requests that only ask to inspect Linear without doing project work
