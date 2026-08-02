---
name: Create and track tasks
description: Create, list, update, and close units of work in Superset.
api: mcp/superset-mcp.yml
operations: [tasks_create, tasks_list, tasks_get, tasks_update, tasks_delete]
---

# Create and track tasks

Tasks are the units of work agents pick up in Superset. Use the MCP server at
`https://api.superset.sh/api/v2/agent/mcp`.

## Steps

1. **Create a task.** Call `tasks_create` with a title/description.
2. **List with filters.** Call `tasks_list` with filtering options to find work
   (by status, project, or team).
3. **Inspect.** Call `tasks_get` for a single task's detail.
4. **Update status.** Call `tasks_update` to move a task through its states
   (valid states come from `tasks statuses list` on the CLI).
5. **Delete.** Call `tasks_delete` to remove a task.

## Notes

- No idempotency key is documented; do not blind-retry `tasks_create`.
- CLI equivalents: `superset tasks create|list|get|update|delete`
  (`cli/superset-cli.yml`).
