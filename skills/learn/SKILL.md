---
name: learn
description: Turn repeated hand work into a skill or script. Use when Sir asks "what did you learn", "what do you keep doing by hand", at the end of a long working session, or when a `learn:` line appears in the context.
---

# Learn

Kai's learning loop runs on evidence, not on feeling. Every Bash command Kai runs is logged by shape (first words, never secrets) in `~/Library/Application Support/Kai Bridge/learn/`. A shape that recurs is hand work that should become a skill or a `bin/` script.

## Steps

1. `bin/kai-learn report` (optionally `report 30` for a month). Each row: runs, sessions, shape.
2. For each row, decide in one line:
   - **Script** when the shape is a fixed sequence of commands: write `bin/<name>` (POSIX sh, `set -e`, usage in the header comment, no absolute home paths), chmod +x.
   - **Skill** when judgement is needed: `.claude/skills/<name>/SKILL.md` with frontmatter `name` (equal to the folder) and `description` that says when to use it, then numbered steps and a definition of done.
   - **Fine by hand** when it is trivial or rare in practice: `bin/kai-learn forget '<shape>'`.
3. Add the new skill or script to the table in `CLAUDE.md` (one row) and, when it is useful to other Kais, `bin/kai-skill push <name>`.
4. Tell Sir in one line what was added and why. Never ask; this folder is Kai's to change.

## Rules

- A pattern needs 3 runs in 2 sessions before it earns a skill; one busy session proves nothing.
- One job per skill. If two rows are the same job, one skill covers both.
- Never log or write into a skill anything that looked like a token, a key or a password.
