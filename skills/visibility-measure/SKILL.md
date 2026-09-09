---
name: visibility-measure
description: "Measures AI visibility with two instruments that must not be mixed: a short daily structured prompt per entity, and a monthly qualitative research pass. Records presence, ordinal position, citation share, mention share, and a blended share of voice. Use when the user says measure our AI visibility, run the daily prompt, share of voice, research pass on what models cite, Instrument A, Instrument B, or what domains keep showing up in grounding. Do NOT load for checking the retrieval gate, writing pages or atoms, placing citations, monitoring GPTBot logs, or turning personalized prompts into a chart."
---

# Visibility measure

Two instruments, two jobs. Instrument A is the daily number. Instrument B is the research pass. Do not mix them into one number. Write the measurement file. Chat is the headline share of voice and the domain head, not the log.

Everything here assumes the brand can be retrieved. If a gate file next to this one says `fail` and they have not asked to record a run anyway, stop and say it is still a ranking problem.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it for brand name and buyer role. If it is missing, do not interview.
2. Find the entities. If they pointed at a `*-cite-for.md` or `cite-for.md`, read **Entities** and the buyer role. A stranger can write the same shape by hand. If they named the entities in chat, use those. If there are no entities and they will not name any, stop — see Refuse.
3. If a `*-gate.md` or `gate.md` sits next to the cite-for file or the path they named, read **Verdict**. If it is `fail` and they have not asked to record a run anyway, stop. If it is `blocked` or missing, note that in Gaps and keep going. Only `fail` stops, unless they asked to record anyway.
4. If they already pointed at a cite-for, gate, or folder, write the measure file next to it. If not, ask where files should live (default: that directory, or the current directory) in the same message as any missing Inputs.
5. Write `<brand-slug>-measure.md` in the same turn as any missing-input questions. Name it from the cite-for file: `foo-cite-for.md` → `foo-measure.md`. If there is no cite-for file, slug the brand or use `measure.md`.
6. Write **Instrument A prompts**: one short prompt per entity, same wording every time, with web search on.

   > A <buyer> is looking for <entity>. Recommend some brands.

   Not "list ten." The bottom of a forced list is filler.
7. If they have a run to record, fill **Instrument A log** and **Share of voice**. If they asked to measure and you can run the A prompt this sitting, run it once per entity and log it. Only stop and set `resume` to wait for a run when you cannot reach a model and they brought no answers. Do not invent presence, position, or shares. Leave Share of voice empty until a real run exists.
8. If this sitting is a research pass, or they pasted realistic-prompt answers, fill **Instrument B**. Otherwise leave it and do not fake a domain list.
9. Fill **Supporting** only from numbers they gave or that you can read from a file they pointed at (Search Console branded queries, AI-referrer sessions, signup attribution, a poll). Skip GPTBot or server-log crawler counts. Those are not this job.
10. Set `status: ready` when a cold reader can see the prompts and any real runs, and `resume` says the next sitting (next daily A, next weekly review, or next monthly B). In chat: path + share of voice if you have a real run + the domain head if B was run. Do not paste the file.

## Working files

```markdown
---
status: in-progress
brand: "<company>"
cite-for: "<path or unset>"
gate: "<path or unset>"
resume: "<exact next step a cold session should do>"
---

# Measure — <brand>

## Entities
## Instrument A prompts
## Instrument A log
## Share of voice
## Instrument B
### Prompts
### Cited domains
### Objections
### Fan-out
## Supporting
## Gaps
```

`status` is `in-progress` until the prompts are written and any run they brought is recorded; then `ready`. Ready does not mean the research pass is done. Ready with no A run is fine only when `resume` says to wait for a run. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts. Append new A runs. Do not restart the log.

Share of voice, Cited domains, and Objections are skimmer zones. No methodology lecture.

## Instrument A

Daily. Reviewed weekly. One prompt per entity. Deliberately plain. Same wording every time. Keep it short.

Log each run as one row: date, model, entity, presence (yes/no), ordinal (`3 of 8` or `absent`), citation share, mention share. Do not invent any of them.

| Metric | Question it answers |
| --- | --- |
| Presence frequency | What share of runs name us at all |
| Ordinal position | Third of eight, or eighth of eight |
| Citation share | Of all sources cited, what share are ours |
| Mention share | Of all brands named, what share is us |

**Share of voice** is the mean of citation share and mention share for that run. Treat a missing share as 0. That is the headline number. The other three live underneath it. Do not write a share of voice until the row exists.

## Instrument B

Once per cycle, not on a chart. Monthly. Fifteen to thirty prompts written the way the buyer would type them, personal details included. Write them from the buyer role plus the entity list already in this file. Mix three shapes: a problem they are in ("my athletes ignore the plan"), a trigger that started the search ("we just got acquired"), and the entity frames themselves.

Harvest:

- **Every cited domain.** Rank by frequency. Expect twenty to forty, with a head of six to ten that appear in most answers. That head list is the input for placement work.
- **The objections the model raises.** When it reaches for a competitor, note what triggered it. That is a positioning gap.
- **The fan-out queries.** Record them in this file's Instrument B Fan-out section. Do not copy them into the gate file — gate uses a different prompt set and copying would invalidate its Positions and Verdict.

A personalized prompt is more revealing than a clean one. It is not something you chart. Do not average B into the daily share of voice.

If they want prompts written and have not run them, write the fifteen to thirty and stop. Do not invent answers.

## Supporting

Record only what you have:

- Branded search volume in Search Console. Trailing, but honest.
- AI referrer traffic. Sessions from chatgpt.com, perplexity.ai, claude.ai, copilot. Which pages models send people to.
- Self-reported attribution on signup.
- Polling. Ten to fifteen people in the ICP: when you started looking, where did you look, what did you type.

Cadence: A daily, reviewed weekly. B monthly. Polling quarterly.

Skip server-log bot monitoring. A crawler fetch is not a grounding hit.

## Inputs

Need the entities and the buyer role. The usual file is `<brand-slug>-cite-for.md`.

From the user's message (ask only if missing and it would make the log wrong), in one batch:

1. The entities and buyer role, if no cite-for file and they did not name them.
2. Where to write, if no existing file anchors the directory.
3. Any Instrument A or B runs they already have (answers, cited URLs, fan-out).
4. Any supporting numbers they already have.

Do not ask for GPTBot logs, a keyword tool export, or a competitor teardown. Do not fetch extra market research.

## Refuse

Stop in a few sentences if there are no entities and they will not name any, if a gate file in front of you says `fail` and they have not said to record a run anyway, or if they want a different job: checking the retrieval gate from scratch, writing pages or atoms, placing citations, monitoring GPTBot or server logs, or charting personalized prompts as if they were Instrument A. Do not mix A and B into one number. Do not invent a share of voice.
