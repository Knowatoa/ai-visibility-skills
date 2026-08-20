---
name: audit-skill
description: "Reads a SKILL.md and writes a pass/fail audit against this repo's house rules: self-contained, working-directory artifact, tight context, action-first, portable frontmatter. Use when the user says /audit-skill, asks to interrogate, lint, or pressure-test a skill's text, or wants to know if a draft is tight enough. Do NOT load for using podcast-prep, reviewing a product PR, or role-playing a user through a skill (that is exercise-skill)."
---

# Audit a skill

Interrogate one `SKILL.md` as text. Do not role-play a user. Do not
rewrite the skill unless they ask.

The idea of a skill whose job is to pressure-test other skills comes
from Jason Cohen's authoring tools in
[asb-skills](https://github.com/asmartbear/asb-skills) (CC BY 4.0).
This checklist is ours. Attribution: `NOTICE.md`.

## 1. Target

Need a path or slug (`podcast-prep` → `skills/podcast-prep/SKILL.md`).
If they named nothing, list `skills/*/SKILL.md` and ask which one.

Read that file once, fully. Also read `AGENTS.md` if you have not this
session. Do not read asb-skills, other catalogs, or sibling skills
"for comparison." The audit is against house rules, not against Jason's
prose.

Ask where to write the report. Default: `./audit-<slug>.md` in the
current directory. Do not write inside `skills/<slug>/` — that folder
is what installers copy.

## 2. Checks

For each check: **PASS**, **WEAK**, or **FAIL**, plus a quoted line
from the skill (or "missing"). No quote, no finding.

### A. Frontmatter

- `name` is kebab-case and matches the folder.
- `description` is a double-quoted string, third person, ≤ 1024
  characters.
- Description says what it does, when to load it (phrases a human
  would type), and what it must not steal (Do NOT / exclusions).

### B. Self-contained

- A stranger with only this folder can run it.
- No required sibling skill. Optional "if installed" is FAIL unless
  the same step is fully specified inline.
- No Claude-Code-only fields or talk: `allowed-tools`, `context: fork`,
  `model:`, `$ARGUMENTS`, `$0`, "subagent", "slash command" as a
  required mechanic.
- No pointers to files that do not ship with the skill, except the
  documented shared brand file (`.agents/brand-context.md`) for
  visibility skills.

### C. Artifact (skip with n/a if the skill is truly chat-only)

- The deliverable is a file on disk, not a long chat paste.
- The skill asks where files live before creating them, or writes next
  to an input file the user already pointed at. Silent path invention
  is FAIL.
- Resume is specified: read the existing file, do not re-ask settled
  facts, in-progress status says where to pick up.
- Chat is told to stay short.

### D. Tight context

- Intake is one batch or "ask only if missing."
- No step that says "read the rest of the repo," "gather whatever
  might help," or "also check related skills."
- Research, if any, is a short ordered fallback list — not an open
  crawl.
- The body does not lecture on facts the model already has (what an
  RSS feed is, how GitHub PRs work) unless this repo's convention
  differs.

### E. Action-first

- Step 1 does work (read a file, fetch a feed, run a command), not
  "make a plan and wait."
- The wielder is not told to confirm every micro-step.
- If the skill forges a list, it does not dump the whole list in the
  first message.

### F. Refuse

- Concrete cases where the skill must stop.
- Refusal is a few sentences, not a consolation workshop.

### G. Length and voice

- Body under ~400 lines. Over that is WEAK unless every section is
  an instruction the wielder would miss.
- Plain words. If a sentence is there to sound smart, FAIL it.

## 3. Write the report

Create the audit file as soon as the first check is judged. Update it
as you go so a dead session still has findings.

```markdown
---
skill: <slug>
path: <path>
status: in-progress | ready
resume: <next check or "done">
---

# Audit — <slug>

## Verdict
<one sentence: ship / patch these FAILs / rewrite>

## Checks
| Check | Result | Evidence |
| ----- | ------ | -------- |
| A Frontmatter | | |
| B Self-contained | | |
| C Artifact | | |
| D Tight context | | |
| E Action-first | | |
| F Refuse | | |
| G Length and voice | | |

## Patches
<each FAIL/WEAK → the section to change → the replacement rule
 in one or two sentences. Not a rewritten SKILL.md unless they asked.>
```

When finished, set `status: ready`, point them at the path, and stop.
Offer `exercise-skill` on the same target. Do not run it unless they
said to.

## Refuse

- No `SKILL.md` in scope (they pasted a blog post, a PR, a brand
  brief). Point them at the right skill if there is one.
- They want a simulated user session. That is `exercise-skill`.
- They want you to "make it more like asb-rude-qa." We do not copy
  his skills. Audit against `AGENTS.md` only.
