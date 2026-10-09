---
name: tasks
description: Keep the person's to-do list: capture, prioritise, answer "what's on my list", close items. Use whenever something to do later is mentioned, finished or dropped, or the list is asked for.
---

# Tasks

The list lives in the Synatyx task list for project `kai` when Synatyx is configured (`context_task_add`, `context_task_list`, `context_task_update`), else in `tasks.md` in this folder, one line per task: `- [ ] <date if any> <title> (<owner>, <priority>)`.

- **Capture at once.** The moment the person mentions something to do later, add it, then say so in a few words. Title in their words, the date in the title when there is one, the owner in the description (them or Kai), priority high, normal or low.
- **Never hold a task in your head.** If it is not on the list, it does not exist after this session.
- **Answer "what's on my list"** from the list, highest priority first, dated items before undated, one line each. Do not pad.
- **Close the same turn.** When something is finished or dropped, mark it `done` or `cancelled` immediately, and say which.
- **Kai's own tasks** go on the same list with Kai as owner, so the person sees what is in flight.
- **Review** when asked, or when the list exceeds about twenty items: propose what to drop, in one line each. Never delete without the person's word.

Project work is not tracked here: that lives in the project's issues and pull requests.
