---
name: new-mac
description: Set up Kai and Kai Bridge on another Mac. Use when Sir wants Kai on a second computer or asks what a fresh machine needs.
---

# Kai on a new Mac

Everything that identifies Kai lives in the account (claude.ai connectors, Synatyx memory) and in the `kai` folder shipped inside the Bridge, so a second Mac needs only the app and a logged-in Claude Code.

Hand Sir this order, or run the parts he asks for:

1. Install Claude Code and log in to the same account: `npm install -g @anthropic-ai/claude-code`, then `claude` once. Node 22, git and the GitHub CLI (`gh auth login` as `tanerincode`, SSH) are needed to build.
2. Clone and install the Bridge: `git clone git@github.com:tanerincode/kai-bridge.git ~/workspace/kai-console && ~/workspace/kai-console/kai/bin/kai-bridge-setup`. The setup script installs dependencies, builds for that Mac's chip and installs the app to `~/Applications`.
3. Add the Synatyx memory server with Sir's token (user scope, once per Mac): `claude mcp add --transport http synatyx <url> --header "Authorization: Bearer <token>"`. The URL and token are in Sir's hands; never store them.
4. Open the Bridge. Answer Claude Code's folder-trust prompt once. Project plugins listed in `.claude/settings.json` are offered for install on first start; accept.
5. Optional: Chrome extension for browser work; `bun` for the Telegram plugin; voice: run `.voice/setup.sh` inside the bundled kai folder (needs Python 3.12, downloads the Kokoro model). Without it, voice falls back to macOS `say`.
6. Run the `toolcheck` skill from the new bundle folder and compare with this Mac's list.

Only one Mac should run a session named `kai` at a time; the Remote Control name is shared across the account.
