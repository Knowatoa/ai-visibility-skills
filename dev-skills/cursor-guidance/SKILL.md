---
name: cursor-guidance
metadata:
  internal: true
description: "How to work with Cursor in this repo: feature branches, never main, PRs not direct pushes, and when to suggest /issue-pr or /pr-review. Use when the user asks how to use Cursor here, which slash command to run, how git/PRs should work, or says 'follow the project workflow'. Also use before opening or merging a PR on a non-trivial change."
---

# Cursor guidance

How to collaborate in this repo. Pair with `issue-pr` and `pr-review` for the actual PR mechanics.

## Git (always)

- Never commit or push to `main`. Never check out `main` to do work.
- Never merge, open a PR, or push without the user asking. Exception: they invoked `/issue-pr` (that is approval to push the **feature branch** and open/update the PR, not to squash-merge).
- Flow: branch → commit → push **feature branch** → PR → squash-merge to main (only after they say merge).
- Identify PRs with `gh pr view` on the current branch. Do not parse issue numbers out of directory names.
- Do not create git worktrees unless this repo has `bin/worktree-*` / `bin/pr-worktree`.
- Do not force-push or skip hooks unless they asked.

## Commands to suggest (do not auto-run)

Before a non-trivial implementation, mention if relevant:

- `/architect` (or an architecture pass) when the change is design-heavy or ambiguous
- `/how` when ownership, runtime flow, or "where should this live" is the question
- `/poteto-mode` only if they asked for that end-to-end routing style

Before creating, reviewing, or preparing a PR, suggest a review pass unless the diff is trivial. For risky diffs (auth, data, deletions), suggest a blast-radius check before calling the work done.

When they are ready to ship: `/issue-pr`. When they want to walk open PRs: `/pr-review`.

## `/issue-pr` vs `/pr-review`

| They want | Run |
| --------- | --- |
| Tests + PR for **this branch**, then merge if they approve | `issue-pr` |
| Inbox of open PRs, review one at a time | `pr-review` |

`/pr-review` never merges. Merge is `/issue-pr` from the PR branch after they pick "merge now."

## This repo

This is a skills catalog, not the Knowatoa Rails app. There is no `bin/rails test`. `npx skills add . --list` must show only public skills under `skills/` (today: `podcast-prep` and `talk-adversary`). Repo-only skills live in `dev-skills/` and load in this clone via symlinks; they are not installed. Visibility skills may read `.agents/brand-context.md`; these workflow skills do not.

New public skills: `create-skill`. For a new public skill or a behavior change: `audit-skill` first, then `exercise-skill` if the audit is clean. Skip both for typos. House rules: `AGENTS.md`. Do not copy text from [asb-skills](https://github.com/asmartbear/asb-skills); we took behavior, not prose (`NOTICE.md`).

Knowatoa-only slash commands (`/issue-fix`, Honeybadger, Playwright QA, newsletters, Buffer) stay in that product repo. Do not invent them here.
