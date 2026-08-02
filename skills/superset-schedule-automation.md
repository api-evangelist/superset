---
name: Schedule and run an automation
description: Configure a recurring agent automation, set its prompt, and trigger it on demand.
api: mcp/superset-mcp.yml
operations: [automations_list, automations_get, automations_set_prompt, automations_run]
---

# Schedule and run an automation

Automations schedule agent runs as recurring jobs with prompt version history.
Use the Superset MCP server at `https://api.superset.sh/api/v2/agent/mcp`.

## Steps

1. **List automations.** Call `automations_list` to see existing scheduled runs.
2. **Inspect one.** Call `automations_get` for its schedule, prompt, and logs.
3. **Set the prompt.** Call `automations_set_prompt` to update the instruction
   the agent runs (prompt versions are retained).
4. **Run on demand.** Call `automations_run` to trigger a run immediately rather
   than waiting for the schedule.

## Notes

- Filter automation listings by team/project rather than paging.
- CLI equivalents: `superset automations list|update|run|logs`
  (`cli/superset-cli.yml`).
