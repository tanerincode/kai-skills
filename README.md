# kai-skills

Shared skills for Kai, a personal assistant built on Claude Code. One folder per skill under `skills/<name>/`,
each with a `SKILL.md` whose frontmatter `name` matches the folder.

- Install into your Kai: `bin/kai-skill pull <name>`
- Publish from your Kai: `bin/kai-skill push <name>` (write access), or fork this repository and open a pull request
- Move a skill as a file: `bin/kai-skill export <name>` then `bin/kai-skill import <file>` on the other side

Skills are instructions. Read a skill before using it, and never put secrets in one.
