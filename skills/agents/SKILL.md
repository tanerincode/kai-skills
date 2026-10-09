---
name: agents
description: Spawn, brief, review and retire agent sessions for a project. Use when work needs more hands than Kai's own session, when a project gets its first builder, or when something must run on a server.
---

# Agents

Two kinds of hands, chosen by the length of the job:

- **Subagents** (the `Agent` tool, roles in `.claude/agents/`): one bounded task, inside Kai's own session, gone when done. `builder` for a change, `tester` to verify it, `reviewer` to read a diff, `shipper` for commit and PR, `scout` to map code, `researcher` for facts from outside. Give the goal, the files, what is already ruled out, and the definition of done.
- **Sessions** (`bin/kai-agent spawn <project> <role> [--worktree]`): a long-lived named Claude Code session in Kai Bridge, with Remote Control so the person can reach it from the phone. Named `<project>-<role>`. One per project at first (`builder`); one per parallel feature, each in its own worktree; one `ops` per project with a server, the only agent that touches production.

Rules:
1. Check `ListAgents` before spawning; one name, one job; never two sessions with one name. `bin/kai-agent list` shows the Bridge's sessions.
2. A session's brief lives in `projects/<project>/briefs/<name>.md`, written before the spawn: goal, definition of done, what it may not touch. The agent reads notes by absolute path and copies nothing into the repository.
3. Every change by a session is a pull request from its worktree; another agent reviews; Kai runs the tests and merges.
4. Hand tasks with `SendMessage`, one clear goal each; subscribe to idle notices rather than polling; relay outcomes in one line.
5. Retire a session when its job is done (`bin/kai-agent stop <name>`) and remove its worktree; idle sessions cost the person usage.
6. Never hand an agent an action that was blocked in Kai's own session; route it to the person with the exact command.

`bin/kai-agent roles` installs the role definitions into `~/.claude/agents` once per Mac so `claude --agent <role>` finds them.
