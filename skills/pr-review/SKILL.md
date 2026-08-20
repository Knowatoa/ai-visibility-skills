---
name: pr-review
description: "Walk open GitHub PRs one at a time: summarize the diff, review correctness/security/quality, verify locally, then stop at a decision gate. Use when the user says /pr-review, asks to review PRs, walk the PR inbox, review PR #<n>, or 'review this PR'. Do not merge unless they explicitly pick merge."
---

# PR Review

Inbox walker. Stops after review and local verify. Merge is a separate `/issue-pr` step.

## Do not

- Merge without explicit approval (option A below, or they clearly say merge / squash-merge). `/issue-pr` by itself opens or updates the PR; it is not merge approval.
- Make code changes on `main`. If you are on `main`, check out the PR branch first.
- Force-push unless they asked.
- Create worktrees unless this repo has `bin/pr-worktree` / `bin/worktree-*`.
- Skip hooks or bypass CI unless they asked.

## Arguments

- Empty — list open PRs, ask which to start with (or walk all if they said "all").
- A PR number — start there.
- `all` — every open PR, one decision gate each.

## 1. Pre-flight

Prefer the main checkout, not a leftover feature worktree:

```bash
MAIN_REPO="$(cd "$(git rev-parse --git-common-dir)/.." && pwd)"
cd "$MAIN_REPO"
```

## 2. Inbox

```bash
gh pr list --state open --json number,title,headRefName,url,author,isDraft,statusCheckRollup \
  --limit 30
```

Prefer non-draft PRs, ones from this user or cloud agents if the list is noisy, and green checks when `statusCheckRollup` is present. Show a numbered list.

## 3. Checkout

If this repo has `bin/pr-worktree` (or `bin/worktree-*`), use that and `cd` into the printed path. Otherwise `gh pr checkout <n>`. Confirm with `git branch --show-current`.

## 4. Understand

```bash
gh pr view <n> --json title,body,files,commits,url
git log --oneline origin/main..HEAD
git diff origin/main...HEAD --stat
```

Summarize: problem, files, risk (auth, billing, migrations, jobs, secrets).

## 5. Review

Triage each finding:

- **Fix now** — bugs, security, clear regressions.
- **Fix before merge** — important; confirm with the user.
- **Note only** — nits, style, false positives.

Apply approved fixes on the PR branch. Push with the branch from GitHub, not a guessed name:

```bash
git push origin HEAD:$(gh pr view <n> --json headRefName -q .headRefName)
```

## 6. Local verify

Run the project's test suite. For this skills repo: `npx skills add . --list`. Manual QA when the diff is user-facing.

## 7. Decision gate

```
1. What next for PR #<n>?
   A. Merge now (/issue-pr from this branch) — only if they explicitly approve
   B. Push fixes and leave open
   C. Skip — next PR
   D. Close PR — explain why
```

Do not merge unless they pick A (or clearly say merge / squash-merge). For A: stay on the PR branch and run the `issue-pr` skill, which still asks before squash-merge unless they already said merge.

## 8. Next PR

Return to the main repo before checking out another PR. Repeat from checkout until the inbox is done or they stop. Leave worktrees intact.
