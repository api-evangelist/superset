---
name: Create a workspace and run an agent
description: Provision an isolated Git-worktree workspace on a Superset host and launch a coding agent in it.
api: mcp/superset-mcp.yml
operations: [hosts_list, projects_list, workspaces_create, agents_create, terminals_create]
---

# Create a workspace and run an agent

Use the Superset hosted Agent API (MCP server at
`https://api.superset.sh/api/v2/agent/mcp`, HTTP transport). Authenticate with
OAuth 2.1 or an API key (`sk_live_*`) — see `authentication/superset-authentication.yml`.

## Steps

1. **Pick a host.** Call `hosts_list` to find a registered machine to run on.
2. **Pick a project.** Call `projects_list` to get the checked-out repository to
   base the workspace on.
3. **Create the workspace.** Call `workspaces_create` with the project and a
   branch name — Superset creates an isolated Git worktree so parallel agents
   never collide.
4. **Launch an agent.** Call `agents_create` against the new workspace, choosing
   the agent (Claude Code, Cursor, OpenCode, Gemini, Copilot, Mistral Vibe, or a
   custom terminal agent) and prompt.
5. **Attach a terminal (optional).** Call `terminals_create` to open a PTY
   session inside the workspace for interactive work.

## Notes

- Each workspace is a branch-scoped Git worktree; run many in parallel.
- No idempotency key is documented — avoid blind retries of `workspaces_create`.
- The same flow is available on the CLI: `superset workspaces create` then
  `superset agents create` (`cli/superset-cli.yml`).
