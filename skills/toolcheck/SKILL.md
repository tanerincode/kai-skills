---
name: toolcheck
description: Verify that Kai, launched from a given folder, has every MCP server, plugin and skill it should. Use after moving Kai's folder, on a new Mac, or when Sir says tools or skills are missing inside the Bridge.
---

# Tool check

Claude Code scopes three things to the folder it starts in: project-scoped plugins (registered in `~/.claude/plugins/installed_plugins.json` by `projectPath`), per-project MCP approvals (`enabledMcpServers` under `projects` in `~/.claude.json`), and the local memory folder under `~/.claude/projects/<folder key>/memory`. Everything else (claude.ai connectors, user-level MCP servers, plugin skills) follows the account or the user.

1. From the folder in question run `claude mcp list` and compare with the reference folder (the last place Kai ran). Sort the server names and diff them.
2. A plugin missing from the new folder: `cd <folder> && claude plugin install <name>@claude-plugins-official --scope project`. Expected project plugins are listed under `enabledPlugins` in `.claude/settings.json`.
3. An approval missing: add the server name to `projects["<folder>"].enabledMcpServers` in `~/.claude.json` (write atomically; Claude Code rewrites this file).
4. Memory: copy the `*.md` files from the old folder key's `memory/` to the new one without overwriting.
5. Report in one line: how many servers each folder sees, and what was fixed.

Kai has no project `.mcp.json`; the Synatyx server is user-level in `~/.claude.json` and must exist on each Mac (Sir adds it with his token, never store the token).
