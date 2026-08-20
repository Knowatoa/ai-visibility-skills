# This repo

A catalog of Agent Skills for AI visibility (how a brand shows up in
ChatGPT, Claude, Perplexity, and the rest).

This is not the Knowatoa product app. There is no Rails test suite.

## Two kinds of skill

| Kind | Where | `npx skills add` | Job |
| ---- | ----- | ---------------- | --- |
| Public | `skills/<name>/` | Yes — this is the only tree it installs | A job for a stranger who copied one folder. |
| Repo-only | `dev-skills/<name>/` | No | Author, review, and ship work **in this repo**. |

Repo-only skills are symlinked into `.cursor/skills/`, `.agents/skills/`,
and `.claude/skills/` so agents working in this clone load them. The
skills CLI does not follow those symlinks.

Public visibility skills may read `.agents/brand-context.md`. Repo-only
skills do not.

Validate a change with `npx skills add . --list`. It must list every
`skills/*/SKILL.md` and **nothing else**. Today that is `podcast-prep`,
`presentation-outline`, and `talk-storyboard`.
Also check frontmatter (`name` matches the folder; `description` ≤ 1024
chars) on any skill you touched, including repo-only ones.

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

When writing a new **public** skill, or changing how one behaves, run
`audit-skill` first. If that audit has FAILs, patch those before
`exercise-skill`. Skip both for typo or one-line copy edits.
Use `create-skill` to start a new public skill. Those three commands
are repo-only.

## Git

Never work on `main`. Feature branch → PR. `/issue-pr` prepares the
current branch; `/pr-review` walks open PRs. Neither squash-merges
unless the user says to merge. Details: `dev-skills/cursor-guidance`.
