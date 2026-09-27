---
skill: channel-funnel-map
path: skills/channel-funnel-map/SKILL.md
status: ready
resume: done
patched: 2026-09-27 (all patches applied and re-exercised)
---

# Audit — channel-funnel-map

## Verdict
Ship after patching one WEAK: the numbered steps ask before they look at
disk, which is the opposite of the order every sibling skill uses. No FAILs.

**Update 2026-09-27:** all four patches applied, plus a fifth from the
exercise pass. `exercise-channel-funnel-map.md` re-ran the failed
scenarios and cleared them. The check table below describes the
pre-patch file.

## Checks
| Check | Result | Evidence |
| ----- | ------ | -------- |
| A Frontmatter | PASS | `name: channel-funnel-map` matches the folder; description is a double-quoted 854-char third-person string that opens "Turns real buyer stories into a map of the buyer's journey", lists typed triggers ("'what stages should my CRM have', 'map my funnel'"), and excludes with "Do NOT load for configuring a specific CRM's settings, writing email sequences, picking channels when they have none today, or ad campaign reporting." |
| B Self-contained | PASS | No sibling skill required, no `allowed-tools` / `context: fork` / `model:` / subagent / slash-command mechanics (grep: none). Only external pointer is the documented brand file: "If `.agents/brand-context.md` (or `.claude/brand-context.md`) exists, take the business line from it and do not ask" — the same `.agents/` → `.claude/` pair used by all five sibling public skills. |
| C Artifact | PASS | Deliverable is a file: "The user walks away with `<business-slug>-channel-map.md`". Location is asked, not invented: step 1 asks "where the file should live (default: current directory)". Resume is specified: "If it already exists, read it, follow `resume`, and do not re-ask settled facts", with `resume: "<exact next step a cold session should do>"` in the template. Chat is bounded: "In chat: the path, the recommended stages as a short list... Do not paste the whole file." |
| D Tight context | PASS | Intake is one batch ("**Ask for stories, one batch.** In a single message ask:"), gap-filling too ("**Fill gaps with one batch of questions.** Only ask what the stories left open"). No repo crawl, no research tour, no web step. The glossary is not a lecture at the model — it is a user-facing instruction: "Define each of these in one sentence the first time you use it, then move on." Reinforced by "Do not lecture on funnel theory." |
| E Action-first | **WEAK** | Step 1 is "**Ask for stories, one batch.**" — the first action is a question. The two things it could read first are buried: the brand-context check is the last clause of step 1, and the existing-file check appears only in "Working files" ("If it already exists, read it, follow `resume`"), never in the numbered list. Step 2 then defers the stub: "**Write the stub** as soon as the first story arrives" — i.e. after the user answers. Siblings do the reverse: talk-outline step 1 is "Load brand context", step 3 is "Write `<talk-slug>-outline.md`... in the same turn as any missing-input questions. Do not wait for answers to create the stub. Sessions die."; talk-storyboard step 4 repeats "Write the storyboard stub in the same turn as any missing-input questions." |
| F Refuse | PASS | Concrete and bounded: "Stop in a few sentences if the user wants a different job: configuring a named CRM's settings or automations, writing the email sequence itself, choosing new channels when they have none today, or analyzing ad spend." |
| G Length and voice | PASS | 136 lines total, well under ~400. Plain words throughout; the sharpest lines are load-bearing, not decorative: "A step nobody can observe cannot be tracked", "This is not attribution. No channel gets 'credit'.", "Accept rough answers and tidy them yourself." |

## Patches

**1. E — look before asking (the one that matters).**
Reorder "Do this job" so the first numbered step reads disk. Split the
current step 1 into three:

- New step 1: check for an existing `*-channel-map.md` in the directory
  they pointed at. If one exists, read it, follow `resume`, and skip
  straight to the open step — do not re-ask the business line or settled
  stories.
- New step 2: check `.agents/brand-context.md`, then
  `.claude/brand-context.md`. If it exists, take the business line from
  it and do not ask. If it is missing, do not interview.
- New step 3: the one batch of questions (directory, business line, 3–6
  buyers, the Dana example) — asking only for what steps 1 and 2 did not
  already answer.

**2. E — write the stub in the same turn as the questions.**
Change step 2 from "as soon as the first story arrives" to: write
`<business-slug>-channel-map.md` with the section headings and
`status: in-progress` in the same turn as the intake questions, before
any answers come back. Add the house line: sessions die, the file is the
memory. Fall back to `channel-map.md` when the business line is not known
yet, and rename once it is.

**3. C nit — the slug has no derivation rule.**
`<business-slug>` is used twice and never defined. Siblings spell it out
(talk-outline: "slug the talk title (`AI search in 2026` →
`ai-search-in-2026-outline.md`)"). Add one clause: slug the business line
(`Rain gauges for vineyards` → `rain-gauges-for-vineyards-channel-map.md`),
or `channel-map.md` if there is no usable line.

**4. G nit — the Example drops a required column.**
"Recommending stages" requires "Name what each stage lets them compare"
and the template's table has four columns (`Stage | Entry signal | What it
lets you compare | Buyers here now`), but the worked Example table has
only three — it silently omits "What it lets you compare". A wielder
copying the Example will produce a table missing the column the rules
demand. Add the column to the Example, or cut the Example table to a
prose line so it cannot be mistaken for the output shape.

## Outside the checks

- **Catalog validation passes.** `npx skills add . --list` lists exactly
  `channel-funnel-map, podcast-prep, talk-adversary, talk-outline,
  talk-slides, talk-storyboard` and nothing else. Note the pinned Node
  24.19.0 in `.tool-versions` is not installed on this machine; the run
  needed `ASDF_NODEJS_VERSION=22.22.2`.
- **Catalog fit, not a house-rule check.** Every other public skill is
  about how a brand shows up in AI answers or on a stage. This one is a
  CRM pipeline design skill; nothing in it touches AI visibility. It is a
  coherent, well-built skill — the question is whether this catalog is
  where a stranger would look for it. Your call, not a finding.
