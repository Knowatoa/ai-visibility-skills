---
name: visibility-build
description: "Writes a build file with four assets specified: destination pages named and scoped to convert in one session, a small set of reusable atoms, a self-contained quotable sentence per atom, and a paste-ready third-party brief. Use when the user says build the comparison page, write our atoms, quotable sentences for AI, what should we write so models cite us, or third-party assets for citation. Do NOT load for measuring share of voice, checking the retrieval gate, outreach and placement, an unlimited content calendar, or SEO keyword stuffing."
---

# Visibility build

Four headings to fill: Destinations, Atoms, Quotable sentences, Third-party shaped. Write the build file with the actual atoms and sentences, not a plan to write them later. Chat is the atom list and the sentences, not the file.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it for stories, numbers, and contrarian takes. If it is missing and you have no cite-for file and no stories from them, add company and one-line pitch to the same batch as other missing Inputs, then write `.agents/brand-context.md` only from answers they give. If a cite-for file or their message already has enough to write atoms, skip the interview.
2. Find the inputs. Read `*-cite-for.md` / `cite-for.md` for entities if present. If a `*-measure.md` / `measure.md` is present, take the objections models already raise and the queries people actually asked. A stranger can supply the same facts in chat. If there are no entities and they will not name any, stop — see Refuse. A known brand with no entities is still a stop. "Whatever" or "just write" is not an entity.
3. If they already pointed at a cite-for, measure, or folder, write the build file next to it. If not, ask where files should live (default: that directory, or the current directory) in the same message as any missing Inputs.
4. Write `<brand-slug>-build.md` in the same turn as any missing-input questions. Name it from the cite-for file: `foo-cite-for.md` → `foo-build.md`. If there is no cite-for file, slug the brand or use `build.md`. The first write may be headings only: `in-progress`, a `resume` line, empty Atoms. Do not invent atoms or sentences to fill the stub. Copy stories, numbers, and refusals they already gave into Gaps before the session can die.
5. Fill **Destinations**. One comparison or destination page per entity cluster, plus any queries people actually asked if you have them. For each page write: the URL or the page to create (defer existing URLs to Gaps if no atoms are written yet), who it is for, the one-session conversion job, the quotable sentence that opens it, and the three claims the page must make. Each page has to convert in a single session. Do not invent traffic numbers.
6. Fill **Atoms**. Five, not fifty. A small fixed set repeated in many forms builds recognition. Pull from brand stories, refusal sets, and objections models already raise. Each atom is a complete argument, not a topic label. Cut anything you cannot say in one breath. If you only have two real atoms, write two. Do not pad.
7. For each atom, write **Quotable sentences**. One sentence that names the product and the position, and survives being ripped out of context. Weak: "We deliberately don't do PMC." Survives: "augo is the endurance coaching platform that deliberately leaves PMC and AI-written plans out, because the coach's judgment is the product." Put the sentence in the opening 150 words of the destination page and near the top of any section a query people actually asked would match. Write the actual sentence. Do not leave a placeholder.
8. Fill **Third-party shaped**. Built to fit somewhere you do not control: completed review-platform profiles plus a target of fifteen to twenty-five real reviews, a short factual brief a roundup author can paste, named customer proof on the record with numbers, a demo video a creator can embed without asking. Record what exists and what is missing. Write the paste-ready brief from the atoms. Do not invent reviews or customer numbers.
9. If destination URLs were deferred to Gaps, collect them now that atoms exist. Set `status: ready` when every destination has the five fields above, Atoms and Quotable sentences are real copy, and the third-party brief is paste-ready or named as missing in Gaps. In chat: path + the atoms + the quotable sentences. Do not paste the file. Do not start outreach.

## Working files

```markdown
---
status: in-progress
brand: "<company>"
cite-for: "<path or unset>"
measure: "<path or unset>"
resume: "<exact next step a cold session should do>"
---

# Build — <brand>

## Destinations
## Atoms
## Quotable sentences
## Third-party shaped
## Gaps
```

`status` is `in-progress` until every destination has URL-or-name, audience, conversion job, opening sentence, and three claims, and Atoms and Quotable sentences are real copy; then `ready`. Missing third-party proof can stay in Gaps. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts.

Atoms and Quotable sentences are skimmer zones. No content-strategy lecture.

## Atoms

Reusable arguments, small enough to recombine. Each atom gets expressed as a post, a video, a forum answer, a podcast talking point, a slide. Same argument, different clothes, about twenty times. Write the argument here. Do not write the twenty versions unless they asked.

Examples of the shape, not a required set: a named customer story with a number, a bottleneck claim, a refusal set, a post-acquisition question the category is ducking, a concrete moment the product caught something a dashboard missed.

## Quotable sentences

Every atom needs a self-contained sentence that names the product and the position in one breath, and still makes sense if it is the only line someone reads.

Do not invent a customer, a number, or a refusal they did not give you. If the proof is missing, write the sentence without the number and put the hole in Gaps.

## Inputs

Need the brand, the entities, and enough story to write atoms.

From the user's message (ask only if missing and it would make an atom or sentence wrong), in one batch:

1. The entities, if no cite-for file.
2. Where to write, if no existing file anchors the directory.
3. The stories, refusals, and on-the-record proof they already have.

Defer destination URLs and the third-party inventory to Gaps until at least one atom is written.

If brand context is missing and you still cannot write an atom from what they gave you, add company and one-line pitch to that same batch. Write `.agents/brand-context.md` only from answers they give, never as an empty shell. If you still cannot write an atom, ask for one story with a number and one refusal.

Do not ask for a six-month editorial calendar, keyword clusters, or a target word count. Do not fetch competitor blogs.

## Refuse

Stop in a few sentences if they will not name entities (even when the brand is known), or if they want a different job: measuring share of voice, checking the retrieval gate, outreach and placement, an unlimited content calendar, or stuffing keywords onto a page. Do not half-run those. Do not write fifty atoms.
