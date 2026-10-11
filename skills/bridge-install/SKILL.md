---
name: bridge-install
description: Rebuild and install Kai Bridge, the macOS app Kai runs inside. Use when Sir asks to install, rebuild, update or reinstall the Bridge, or after Bridge code changes are verified.
---

# Install Kai Bridge

The app is built from `~/workspace/kai-console` and installed to `~/Applications/Kai Bridge.app`. A pristine copy of Kai's folder ships inside it at `Contents/Resources/kai` (sealed, never written); Kai lives and writes in `~/Library/Application Support/Kai Bridge/kai`; the source copy is `kai-console/kai`.

1. Verify first: in `~/workspace/kai-console` run `npm test` and `npm run typecheck`, read the output. Never install red.
2. Say in one line that installing quits the Bridge and therefore ends the running Kai session, then run:
   - `bin/kai-bridge-install` for a fresh build, or
   - `bin/kai-bridge-install --no-build` to install the last build in `release/`.
   The script copies what Kai changed in the live folder back to `kai-console/kai`, builds, swaps the app, sets up the voice runtime if missing, reopens it, and ends with `== seal ok` (or the codesign failure: report it). The app merges the new build into the live folder at launch; Kai's changes stay. It re-executes from a temporary copy because it deletes its own folder mid-run.
3. The next Bridge launch resumes Kai's last conversation from the live folder. A new folder shows Claude Code's folder-trust prompt once in the terminal; answer Yes.
4. After an install, run the `toolcheck` skill if the kai folder's path changed.

If Sir must run it himself (Kai cannot quit its own host and keep reporting), give the exact command from an outside terminal.
