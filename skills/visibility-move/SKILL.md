---
name: visibility-move
description: "Places built AI-visibility assets on three tracks with different clocks: a same-week test loop on pages that already get grounded, third-party placements over 8 to 16 weeks, and owned repetition that compounds. Use when the user says run the test loop, move the citation work, outreach to roundup authors, Track A Track B Track C, place our atoms, or get listed on the domains models already cite. Do NOT load for writing the assets from scratch, measuring share of voice as the only job, checking the retrieval gate, Reddit astroturf, averaging the three tracks into one timeline, or promising broad citation movement inside a month."
---

# Visibility move

Three tracks, three clocks. Do not average them into one timeline. The walk-away is a move file: the test log, the domain outreach list, and the owned rotation. Chat is which track moved, not the file.

Track A is the fast feedback. Track B is the compounding. Track C is what makes Track B possible.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it for the brand name and any proof already on disk. If it is missing, do not interview.
2. Find the inputs. Read `*-build.md` / `build.md` for destinations, atoms, quotable sentences, and third-party-shaped assets. Read `*-measure.md` / `measure.md` for the Instrument B domain head and fan-out. A stranger can paste the same lists. If there are no assets and no domain list and they will not provide either, stop — see Refuse.
3. If they already pointed at a build, measure, or folder, write the move file next to it. If not, ask where files should live (default: that directory, or the current directory) in the same message as any missing Inputs.
4. Write `<brand-slug>-move.md` in the same turn as any missing-input questions. Name it from the build file: `foo-build.md` → `foo-move.md`. If there is no build file, slug the brand or use `move.md`.
5. Fill the three tracks. Do not collapse them into one calendar.
6. If this sitting is a Track A run, do **Track A** now. Write the exact sentence or heading you are changing on a page that already appears in grounding sources. Re-run the structured prompt they already use, or write that prompt from the entities if they have no measure file. Record whether presence, position, or framing moved. Keep or revert. Do not invent the result.
7. If this sitting is Track B, work the head of the domain list. Name the actual domains. Draft the brief and the outreach list. Do not write "find roundups" as the next action. Do not invent a yes. Do not count Reddit as a citation lever.
8. If this sitting is Track C, set the rotation from the existing atoms: one atom per week, cycle the set roughly every five weeks. Do not start a new atom set.
9. Write **Loop**. Re-run the research pass at 30, 60, and 90 days. Expect Track A movement by day 30 and nothing from Track B. Anyone promising broad citation movement inside a month is wrong.
10. Set `status: ready` when a cold reader could run this week's A test and see the B list and C rotation. In chat: path + this week's A change + how many B outreaches are queued + which atom is on C. Do not paste the file.

## Working files

```markdown
---
status: in-progress
brand: "<company>"
build: "<path or unset>"
measure: "<path or unset>"
resume: "<exact next step a cold session should do>"
---

# Move — <brand>

## Track A
## Track B
## Track C
## Loop
## Gaps
```

`status` is `in-progress` until each track has a next action a cold reader could take; then `ready`. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts. Append A tests. Do not restart.

Track A results and the B domain list are skimmer zones.

## Track A: the test loop (days)

The only lever with same-week feedback. Edit a page that already ranks and already gets grounded.

1. Take a page that appears in the Instrument B grounding sources. If you cannot point at such a page, stop A and say so in Gaps. Do not pick a random blog post.
2. Change one thing. Usually a quotable sentence, sometimes a heading that matches a fan-out query. Write the exact before and after in the file.
3. Re-run the structured prompt from Instrument A (one short prompt per entity, grounding on, not "list ten").
4. Record whether presence, position, or framing moved.
5. Keep the change or revert it. Repeat.

Run this weekly. First signal in days. Full effect in 2 to 4 weeks.

## Track B: places you do not control (8 to 16 weeks)

This is what moves citation. Work the head of the domain list from Instrument B.

- **Roundups that already rank.** Find the author, send the brief, ask to be considered. Expect twenty to thirty percent yes. Ten outreaches gets two or three placements. Use the factual brief from the build file, or write one from the atoms if they have no build file.
- **Review platforms.** Twenty-plus real reviews changes whether you appear in category listings models read. Do not write the reviews.
- **Creators.** Three to five buyers with audiences doing honest comparisons. Give them the product and the freedom to say what is missing. A review that names a real gap gets cited more than one that does not.

**Reddit:** worth doing for human demand and branded search. Do not count it as a citation lever. When Reddit appears in grounding sources it gets rejected most of the time. Real customers answering real questions only. Never the company account. Never astroturf. In a small niche it gets caught and the reputational cost is permanent.

First signal around 8 weeks. Full effect 8 to 16 weeks, sometimes longer.

## Track C: places you control (quarters)

Socials, newsletter, podcasts, stage. Run the atoms on repeat, one per week, cycling the set roughly every five weeks.

This does not get you cited directly. It makes Track B easier, because people say yes to a name they recognize, and it drives branded search.

Founders quit at week four because they feel repetitive. The audience is hearing it for the first time.

**Thin categories.** The usual claim is that you cannot influence what a model learned in pretraining, because your contribution disappears in a huge corpus. That holds for large categories. If the total writing about you and your competitors is dozens of pages, not millions, marginal additions carry more weight. Run Track C harder in a thin category. Do not expect fast results from it.

First signal in a quarter. Compounds indefinitely.

## Loop

| Track | First signal | Full effect |
| --- | --- | --- |
| A: test loop | Days | 2 to 4 weeks |
| B: third-party | 8 weeks | 8 to 16 weeks, sometimes longer |
| C: owned | One quarter | Compounds indefinitely |

The gate tells you whether you can be retrieved. Measurement tells you where the corpus stands. The build file gives you something worth putting into it. This skill puts it there.

Do not average the tracks. Do not promise citation movement inside a month.

## Inputs

Need built assets and, for Track B, a cited-domain head list.

From the user's message (ask only if missing and it would make a track wrong), in one batch:

1. Path or paste for the build file (destinations, atoms, quotable sentences, third-party brief).
2. Path or paste for the measure file, or the domain head and the structured prompt.
3. Which page already appears in grounding sources, if they know it.
4. Where to write, if no existing file anchors the directory.

Do not ask for a single launch date that covers all three tracks. Do not fetch a media list from the open web unless they named a domain to work.

## Refuse

Stop in a few sentences if there are no assets and no domain list and they will not provide either, or if they want a different job: writing the atoms and destination pages from scratch, measuring share of voice as the only job, checking the retrieval gate, posting from the company account on Reddit, averaging the three tracks into one timeline, or a plan that promises broad citation movement inside a month. Do not write fake reviews. Do not half-run those.
