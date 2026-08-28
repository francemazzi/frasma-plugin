---
name: frasma-kanban
description: Use the Frasma Kanban as the source of truth for project work. Apply when analyzing a project, creating or updating tasks, checking a suspected bug, or deciding whether work already exists on the board.
---

# frasma-kanban

Frasma is the source of truth for project work. Prefer MCP tools over guessing, and act as the signed-in user (same RBAC, optimistic locking, and commercial policy as the web app).

## When analyzing a project

1. Call `list_projects` if the project name is ambiguous.
2. Call `get_project_workboard` for open work.
3. Prioritize URGENT, then HIGH, then production or customer-visible bugs, then the rest.
4. For a suspected bug, read `get_task` and `list_task_conversations`, then `search_project_knowledge`. In Cursor, also verify against the local repository.
5. After implementing, `update_task` with a reason and the current `expectedVersion`. Create a new task only when the outcome is distinct.

Never invent task IDs. Always re-read version before a patch.

## Task policy

- Greetings, thanks, and informational questions with no requested work are `NO_ACTION`. Do not create a card.
- Search existing tasks in the same project before proposing a new one.
- Do not silently reopen or edit a `DONE` task. Propose an explicit reopen update or a distinct regression card, linked to the previous task.
- Do not mix unrelated outcomes into one card. Independent results belong on separate tasks.
- Mutations need a `reason`. MCP revisions use `source = AI` and a `mcp:` reason prefix on the server; still pass a clear human reason.
- Suggest priority; do not overwrite it automatically. Do not infer urgency from tone alone.
- `create_task` requires `title`, `description`, and `reason`. Title names the area and the outcome. Description is never a paraphrase of the title: include the reported fact, expected behavior, and a reproduction or acceptance criterion. If those are missing, ask instead of creating a thin card.

## Tools

`list_projects`, `get_project`, `get_project_workboard`, `list_tasks`, `get_task`, `list_task_conversations`, `search_project_knowledge`, `create_task`, `update_task`, `move_task`.
