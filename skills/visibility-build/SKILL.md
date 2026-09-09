---
name: visibility-build
description: "Builds the four assets AI visibility work actually needs: one converting destination page per major query cluster, a small set of reusable atoms, a self-contained quotable sentence per atom, and third-party-shaped proofs other people can paste or embed. Use when the user says build the comparison page, write our atoms, quotable sentences for AI, what should we write so models cite us, third-party assets for citation, or the model never sees your page. Do NOT load for measuring share of voice, checking the retrieval gate, outreach and placement, an unlimited content calendar, or SEO keyword stuffing."
---

# Visibility build

Four kinds of asset. The fourth is the one most processes miss. The walk-away is a build file with the actual atoms and sentences, not a plan to write them later. Chat is the atom list and the sentences, not the file.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it for stories, numbers, and contrarian takes. If it is missing and you have no cite-for file and no stories from them, add the brand questions to the same batch as other missing Inputs, then write `.agents/brand-context.md`. If a cite-for file or their message already has enough to write atoms, skip the interview.
2. Find the inputs. Read `*-cite-for.md` / `cite-for.md` for entities if present. Read `*-measure.md` / `measure.md` for Instrument B objections and cited-domain context if present. A stranger can supply the same facts in chat. If there are no entities and they will not name any, stop — see Refuse.
3. If they already pointed at a cite-for, measure, or folder, write the build file next to it. If not, ask where files should live (default: that directory, or the current directory) in the same message as any missing Inputs.
4. Write `<brand-slug>-build.md` in the same turn as any missing-input questions. Name it from the cite-for file: `foo-cite-for.md` → `foo-build.md`. If there is no cite-for file, slug the brand or use `build.md`.
5. Fill **Destinations**. One comparison or destination page per major query cluster from the entities and, if you have them, the fan-out queries. Each page has to convert in a single session. Name the URL if it exists. If it does not, name the page to write and the one-session conversion job. Do not invent traffic numbers.
6. Fill **Atoms**. Five, not fifty. A small fixed set repeated in many forms builds recognition. Pull from brand stories, refusal sets, and Instrument B objections. Cut anything you cannot say in one breath. If you only have two real atoms, write two. Do not pad.
7. For each atom, write **Quotable sentences**. One sentence that names the product and the position, and survives being ripped out of context. Weak: "We deliberately don't do PMC." Survives: "augo is the endurance coaching platform that deliberately leaves PMC and AI-written plans out, because the coach's judgment is the product." Put the sentence in the opening 150 words of the destination page and near the top of any section a fan-out query would match. Write the actual sentence. Do not leave a placeholder.
8. Fill **Third-party shaped**. Built to fit somewhere you do not control: completed review-platform profiles plus a target of fifteen to twenty-five real reviews, a short factual brief a roundup author can paste, named customer proof on the record with numbers, a demo video a creator can embed without asking. Record what exists and what is missing. Write the paste-ready brief from the atoms. Do not invent reviews or customer numbers.
9. Set `status: ready` when a cold reader could write the pages and send the outreach packet from the file. In chat: path + the atoms + the quotable sentences. Do not paste the file. Do not start outreach.

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

`status` is `in-progress` until Destinations, Atoms, and Quotable sentences are filled with real copy; then `ready`. Missing third-party proof can stay in Gaps. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts.

Atoms and Quotable sentences are skimmer zones. No content-strategy lecture.

## Atoms

Reusable arguments, small enough to recombine. Each atom gets expressed as a post, a video, a forum answer, a podcast talking point, a slide. Same argument, different clothes, about twenty times. Write the argument here. Do not write the twenty versions unless they asked.

Examples of the shape, not a required set: a named customer story with a number, a bottleneck claim, a refusal set, a post-acquisition question the category is ducking, a concrete moment the product caught something a dashboard missed.

## Quotable sentences

The model never sees your page. The index compresses it into an extractive summary: verbatim chunks pulled from the page, joined with ellipses, scored against the fan-out query. Only what survives that compression represents you. You do not control the chunking.

Every atom needs a self-contained sentence that names the product and the position in one breath.

Do not invent a customer, a number, or a refusal they did not give you. If the proof is missing, write the sentence without the number and put the hole in Gaps.

## Inputs

Need the brand, the entities, and enough story to write atoms.

From the user's message (ask only if missing and it would make an atom or sentence wrong), in one batch:

1. The entities, if no cite-for file.
2. Where to write, if no existing file anchors the directory.
3. Existing destination URLs, if any.
4. The stories, refusals, and on-the-record proof they already have.
5. What third-party profiles, reviews, briefs, or demo videos already exist.

If brand context is missing and you still cannot write an atom from what they gave you, add these to that same batch, then write `.agents/brand-context.md`:

1. What's your current company, and how do you describe it in one sentence?
2. What did you build before this that comes up in conversation?
3. What are 2-3 stories you tell well, with real numbers attached?
4. What's one opinion you hold that most people in your space disagree with?

Do not ask for a six-month editorial calendar, keyword clusters, or a target word count. Do not fetch competitor blogs.

## Refuse

Stop in a few sentences if there is no brand and no entities and they will not name either, or if they want a different job: measuring share of voice, checking the retrieval gate, outreach and placement, an unlimited content calendar, or stuffing keywords onto a page. Do not half-run those. Do not write fifty atoms.
