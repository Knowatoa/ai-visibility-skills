---
name: exercise-skill
description: "Role-plays realistic users through a SKILL.md and judges whether the wielder actually does the job: writes the artifact, stays tight, refuses the wrong request. Use when the user says /exercise-skill, wants a wind-tunnel, simulated use, or to see if a skill works in conversation. Do NOT load for a static checklist (that is audit-skill), for podcast prep, or for authoring a new skill from scratch (that is create-skill)."
---

# Exercise a skill

A skill can read well and still wield badly: it lectures instead of
doing the job, asks for context it does not need, or never writes the
file. The only way to see that is to watch it get used.

This wind-tunnel is inspired by Jason Cohen's `exercise-asb-skill` in
[asb-skills](https://github.com/asmartbear/asb-skills) (CC BY 4.0).
The rubric below is ours. Attribution: `NOTICE.md`.

## 1. Target and quarantine

Resolve the `SKILL.md` (`podcast-prep` → `skills/podcast-prep/SKILL.md`,
or a path they give). Read it once, fully.

Then **quarantine**: for every role-play, the wielder side may use
only that file. No `AGENTS.md`, no forging chat, no "we usually also…".
If the wielder needs a rule that is not in the file, that absence is
a finding. Say the quarantine in one line before the first transcript.

Ask where to write the report. Default: `./exercise-<slug>.md` in the
current directory. Do not put it inside `skills/<slug>/`.

## 2. Scenarios

Write 3–5 scenarios for this skill's domain. Required mix:

1. **Canonical** — a realistic user, enough input, right job.
2. **Terse** — two lines, most context missing. Tests whether the
   skill asks for the missing piece or invents it.
3. **Wrong job** — something that should hit the skill's refuse
   cases (or its "Do NOT load" line).
4. **Die-and-resume** (required if the skill keeps a working file) —
   session dies mid-work; a new wielder has only the SKILL.md and
   the file on disk. They must pick up, not re-interview.

One line each: who they are, what they paste, how they behave under
a question. Show the list, then run. If they said "just run it," run.

## 3. Transcripts

For each scenario, play both sides for as many turns as it takes to
answer the test (usually 4–10):

```
USER: …
WIELDER: …
```

Rules:

- The user is realistic. Sometimes vague. Sometimes they try to skip
  the file and take a chat dump.
- The wielder follows the SKILL.md literally. Where the file is
  ambiguous, take the most likely reading and flag it.
- Stop a transcript once the verdict is obvious. You do not need a
  finished brief to know it never created the file.
- Do not play an idealized wielder who "would have" followed a rule
  that never fired.

## 4. Rubric

Each criterion: **PASS / WEAK / FAIL** plus a quoted wielder line.
Skip with n/a if the scenario cannot speak to it.

| Criterion | Question |
| --------- | -------- |
| **Did the job** | Did it run the steps on this user's specifics, or lecture the skill back? |
| **Tight intake** | Missing facts: one batch / ask-if-missing? Or a drip, or a tour of extra context? |
| **Artifact** | File created at the right time, right place, resume header honest? Chat short? |
| **Refuse** | Wrong-job scenario: stopped for the right reason, briefly? |
| **Resume** | Die-and-resume: picked up from disk, did not re-ask settled facts? |
| **Generic** | Could a model with no skill loaded have produced this conversation? If yes, FAIL. |

## 5. Report and patches

Write the report as soon as scenario 1 has a verdict. Append as you go.

```markdown
---
skill: <slug>
path: <path>
status: in-progress | ready
resume: <next scenario or "done">
---

# Exercise — <slug>

Quarantine: wielder used only `<path>`.

## Scenarios
<the list you ran>

## Verdict table
<scenarios × criteria>

## Patches
<each FAIL/WEAK → SKILL.md section → one concrete rule to add or
 move earlier. If the file already says the right thing and the
 wielder still drifted, the rule is too late or too soft: strengthen
 it at the point of use.>
```

Then:

- If they are forging a new skill and asked you to patch: edit
  `SKILL.md`, re-run only the failed scenarios.
- If the skill is already public: show the patches, wait for a yes
  before editing.

If everything passes, say so and stop. Do not invent findings.

## Refuse

- No skill file to exercise.
- They want a static checklist only — `audit-skill`.
- They want you to exercise an asb-* skill from Jason's repo. Send
  them there. Do not load his files into this catalog.
