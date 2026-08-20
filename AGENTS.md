# This repo

A catalog of Agent Skills for AI visibility (how a brand shows up in
ChatGPT, Claude, Perplexity, and the rest) plus a few workflow skills
for shipping work in this repo.

This is not the Knowatoa product app. There is no Rails test suite.
Validate with `npx skills add . --list` and by checking `SKILL.md`
frontmatter (`name` matches the folder; `description` ≤ 1024 chars).

## Two kinds of skill

| Kind | Where | Installed by `npx skills add` | Job |
| ---- | ----- | ----------------------------- | --- |
| Public | `skills/<name>/` except the three craft skills below | Yes | Do a job for a stranger who copied one folder. |
| Craft | `skills/create-skill`, `skills/audit-skill`, `skills/exercise-skill` | Yes, grouped separately | Author and pressure-test skills in this repo. |

Public visibility skills may read `.agents/brand-context.md`. Workflow
and craft skills do not.

## How a public skill should behave

These rules are house style. They were inspired by Jason Cohen's
[asb-skills](https://github.com/asmartbear/asb-skills) (CC BY 4.0) —
see `NOTICE.md`. The wording here is ours.

1. **Self-contained.** A user may copy one `SKILL.md`. Do not require
   sibling skills, repo-internal files, or Claude-Code-only frontmatter
   (`allowed-tools`, `context: fork`, `$ARGUMENTS`, slash-command talk).
   Optional "if this other skill is installed" is fine only when the
   same step is fully specified inline.
2. **The file is the work.** If the user walks away with a brief, audit,
   or plan, write it to disk. Ask where the files should live before
   creating anything (default: the current directory). Chat is the
   short version, not the deliverable.
3. **Resume from disk.** If the file already exists, read it and
   continue. Do not re-ask settled facts. An in-progress file must say
   exactly where the last session stopped.
4. **Tight context.** Do not go hunting for extra repo lore, adjacent
   skills, or a 24-hour research tour. Use what the user said, what is
   already in the working files, and the next source that unblocks the
   deliverable.
5. **Action first.** Do the next useful step. Ask only when a missing
   fact would make the output wrong. One batch of questions, not a drip.
   One ask per message when you must ask.
6. **Refuse cleanly.** If the request is the wrong job for this skill,
   say so in a few sentences and stop. Do not half-run it.

When writing or revising a skill, run `audit-skill` on the draft, then
`exercise-skill`. Use `create-skill` to start a new public skill.

## Git

Never work on `main`. Feature branch → PR. `/issue-pr` prepares the
current branch; `/pr-review` walks open PRs. Neither squash-merges
unless the user says to merge. Details: `skills/cursor-guidance`.
