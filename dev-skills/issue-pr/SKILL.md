---
name: issue-pr
metadata:
  internal: true
description: "Run tests, merge main into the current branch, do a quality pass, then create or update the PR for this branch. Use when the user says /issue-pr, asks to open a PR, ship this branch, merge this PR, or squash-merge. Never run on main. Identify the PR with gh pr view on the current branch, not directory names. Do not squash-merge until the user explicitly approves."
---

# Issue PR

Prepare the **current branch** for review: merge latest main, simplify the diff, run tests, then create or update the pull request. Squash-merge only after the user says to merge.

The PR is the one for the checked-out branch (`gh pr view`), not a number parsed from a worktree path. A worktree can host many branches; each branch has its own PR.

## Do not

- Work on `main`, push to `main`, or merge to `main` without an explicit "merge" / "squash merge" from the user. `/issue-pr` is approval to push the **feature branch** and open/update the PR. It is not approval to squash-merge unless they also said merge.
- Create git worktrees unless this repo has `bin/worktree-*` (or equivalent) scripts.
- Force-push or skip hooks unless the user asked.

## Pre-flight

```bash
BRANCH=$(git rev-parse --abbrev-ref HEAD)
```

Stop if `BRANCH` is `main`.

## 1. Merge main into this branch first

```bash
git fetch origin main
git merge origin/main
```

On conflicts: `git status` and `git diff --name-only --diff-filter=U`. Resolve simple ones; for the rest, show the files and wait. After resolution:

```bash
git add .
git commit -m "Resolve merge conflicts with main"
```

## 2. Simplify review

Diff: `git diff HEAD` if there are unstaged changes, otherwise `git diff origin/main...HEAD`.

Run four review passes in parallel on that diff (separate agents if available):

1. **Reuse** — existing helpers that would replace new code; duplicated logic.
2. **Quality** — redundant state, parameter sprawl, copy-paste variation, leaky abstractions, stringly-typed APIs.
3. **Efficiency** — extra work, N+1, missed concurrency, hot-path bloat.
4. **Security** — injection, XSS, mass assignment, IDOR / missing authz, CSRF, secrets in logs, unsafe file handling. In a Rails app, inspect params, Arel/SQL, and controller authorization.

Fix real issues; skip false positives. Commit those fixes before tests.

## 3. Tests

Use this repo's test runner if it has one. Otherwise the project's normal command (`bin/rails test`, `bin/ptest`, `npm test`, etc.).

For this skills repo (no app test suite):

```bash
npx skills add . --list
```

Confirm it lists every `skills/*/SKILL.md` and nothing from `dev-skills/`. Today that is `podcast-prep`, `talk-outline`, `talk-storyboard`, and `talk-slides`. `name` must match the folder. If you changed a skill (public or repo-only), also check frontmatter (`name`, `description` ≤ 1024 chars).

On failure: show the error, fix merge-caused failures, then re-run. Do not open or merge a PR on a red suite.

## 4. Find or create the PR

```bash
gh pr view --json number,state,url,headRefName
```

If none exists and tests passed: commit remaining work, push the feature branch, create the PR (`gh pr create` or this environment's PR tool). If the body or commits say `Closes #N`, note that issue (and any parent) in the PR summary.

If a PR exists: push the feature branch so the PR is current. Recheck that the merge with main is clean.

## 5. Learnings (before merge, after the PR exists)

If this session turned up a gotcha, a missing permission, or a pattern worth documenting, ask before writing more files:

1. Permanent permissions for commands we kept re-approving?
2. Project docs for the gotcha?
3. A note for similar future issues?
4. A helper script for a repeated operation?

Only implement what they pick, then commit.

## 6. Merge (explicit approval only)

If tests passed and they said to merge (any of: merge, squash merge, squash-merge):

- Do **not** pass `--delete-branch` unless they asked to delete it.
- `gh pr merge --squash` (or the repo's equivalent).
- Pull `main` in the main working tree, not a worktree checkout:

```bash
MAIN_REPO="$(cd "$(git rev-parse --git-common-dir)/.." && pwd)"
cd "$MAIN_REPO"
git pull origin main
```

Leave worktrees in place. If this PR closed a sub-issue, comment on the parent.

If tests or checks failed: keep the PR open, show the failures, do not merge.

## Worktrees

Skip this section unless the repo actually uses worktrees. `--show-toplevel` is the worktree path. The shared repo root is `"$(cd "$(git rev-parse --git-common-dir)/.." && pwd)"`.
