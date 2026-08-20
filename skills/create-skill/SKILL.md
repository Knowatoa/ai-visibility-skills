---
name: create-skill
description: "Authors a new public skill in this repo: names it, writes SKILL.md as the working file, and stops when the draft is ready for audit-skill and exercise-skill. Use when the user says /create-skill, wants a new AI visibility skill, or asks to forge, draft, or add a skill. Do NOT load for podcast prep, brand research, PR work, or editing an existing skill (edit the file and run audit-skill)."
---

# Create a skill

Turn one job into one public `SKILL.md` in this repo. The draft on disk
is the work. Chat is only for the few facts you cannot invent.

This authoring loop is inspired by Jason Cohen's `create-asb-skill` in
[asb-skills](https://github.com/asmartbear/asb-skills) (CC BY 4.0). His
skill interviews an expert across many phases against his own corpus.
This one does not. Write our skill, in our words, for AI visibility.
Do not copy his frameworks or his skill text. Attribution: `NOTICE.md`.

## What you are building

A **public** skill at `skills/<slug>/SKILL.md`. A stranger will install
that folder and nothing else. So:

- Self-contained. No required sibling skills. No Claude-Code-only
  frontmatter (`allowed-tools`, `context: fork`, `$ARGUMENTS`).
- If the skill produces a brief, audit, or plan, it writes a file in a
  directory the user names (default: current directory) and resumes from
  that file later.
- Tight. It does not go looking for extra context. It asks once, then
  works.
- Action-oriented. The wielder does the job instead of narrating a plan
  or camping in chat.

House rules (also in `AGENTS.md` when you are in this repo): self-contained; the deliverable is a file; resume from disk; do not hunt extra context; act first; refuse the wrong job. Spec: [agentskills.io](https://agentskills.io/specification).

## Do not

- Invent a skill the user did not ask for.
- Copy text from asb-skills or any other catalog. Steal *behavior*
  (file on disk, tight intake, a later audit/exercise), not prose.
- Open a long interview. Missing facts: one batch, then write the file.
- Write a website wrapper, plugin manifest, or marketing page. This repo
  has none of those.
- Touch `issue-pr`, `pr-review`, or `cursor-guidance` unless the user
  named them.

## 1. Intake — one batch

If the user already named the job, skip questions you can answer from
that. Otherwise ask all of these in one message:

1. **Job** — what the wielder does, in one sentence.
2. **Trigger** — 3 phrases a user would actually say. 1 phrase that
   looks related but must not load this skill.
3. **Walk-away** — the file the user keeps (name + one-line shape), or
   "chat only" if there is no artifact. Prefer a file.
4. **Slug** — kebab-case, matches the folder. Propose one. Do not pick
   silently if they already have a name.

Do not ask about voice, archetypes, workshops, or adjacent frameworks.
If they say "just draft it," draft it.

## 2. Write the file immediately

```
mkdir -p skills/<slug>
```

Create `skills/<slug>/SKILL.md` as soon as you can fill the frontmatter
and the first working sections. If they might abort after intake, still
write the file — that is the resumption point.

### Frontmatter

```
---
name: <slug>
description: "<does X. Use when … Do NOT load for …>"
---
```

`name` matches the folder. `description` is a double-quoted string,
third person, ≤ 1024 characters, and includes natural phrasing plus
exclusions.

### Body shape

```
# <title>

<one paragraph: when this matters and what file the user gets>

## Do this job

<numbered steps the wielder runs. Commands, sources, order.>

## Working files

<where the artifact lives, when to create it, header schema,
how to resume, what must not appear in the skimmer section>

## Inputs

<what you need. What you must not go fetch. One-batch interview
only if the shared brand file is missing.>

## Refuse

<concrete cases this skill should not run>
```

Drop a section that does not apply. Do not add a lecture on the market
category. The wielder already knows what a podcast is.

### Working-file rules to bake in (when there is an artifact)

- Ask where the method's files should live before creating any. Default:
  the current directory. If an input file already anchors the location,
  write siblings next to it.
- Create the file when the first real section is ready, not at the end.
- Header includes `status: in-progress | ready` and a one-line
  `resume:` that a cold session can follow.
- Chat: short status + path. Do not paste the whole file.
- Shared identity for visibility skills lives at
  `.agents/brand-context.md` (fallback `.claude/brand-context.md`).
  Per-show or per-task output does **not** go there.

## 3. Distill in the file, not in chat

After the first draft exists, tighten it on disk:

1. **Core job** — one sentence at the top. If you cannot say it, the
   skill is two skills. Stop and split.
2. **Trigger vs refuse** — the description and the Refuse section must
   agree.
3. **Lazy output** — what is the least the wielder could do while
   technically following the steps? Patch that (usually: "write the
   file" and "do not invent the missing number").
4. **Context grab** — delete any step that reads extra repo files,
   other skills, or "whatever else seems useful."

Show the user the path and a 5-line summary of what you wrote. Ask
whether to run `audit-skill` next. Do not auto-run it unless they said
to go through the whole loop.

## 4. Hand off

When the draft has no `TODO` markers:

1. Add the slug to the right group in `skills.sh.json` (usually
   "AI visibility").
2. Add a one-line row to the skills table in `Readme.md`.
3. Tell them the next commands: `audit-skill` on this path, then
   `exercise-skill`. Do not pretend those ran.

If this session dies mid-draft, put one HTML comment at the top of the
body so the next session can continue from disk. Do not invent a second
progress scheme:

`<!-- status: in-progress resume: <exact next step> -->`

## Refuse

- The request is "make our skills more like asb-skills" with no new
  job — that is an edit to house rules, not a new skill.
- They want Jason's Carol / pricing / interview method encoded here.
  Point at [asb-skills](https://github.com/asmartbear/asb-skills) and
  stop. We do not restate his frameworks.
- They want a Claude-Code plugin, website, or ZIP pipeline. Out of
  scope for this repo.
