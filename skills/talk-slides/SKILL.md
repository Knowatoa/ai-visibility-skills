---
name: talk-slides
description: "Builds a sparse PowerPoint deck from a talk storyboard: about 15-30 seconds per slide, a cue not the spoken line on screen, a visual note for a later pass, and speaker notes that tie each slide back to the outline and the beats. Approves the markdown before the pptx: a sorter grouped by beat and Hit/why for merge and move, plus one look at a time (previous, this, next). Use when the user says build the slides, make the deck, turn this storyboard into PowerPoint, generate the pptx, walk through the slides, show the slide sorter, merge these slides, move this slide, approve this slide, review the slides markdown, do not generate the pptx yet, I want build-style slides, keep each slide to a sentence, these slides read like a script, or 'visually engaging slides that move fast'. Do NOT load for writing the outline, mapping the emotional journey from scratch, a word-for-word speech, illustrating the deck, podcast guest prep, Keynote or Google Slides as the only output, or a fundraising pitch deck."
---

# Talk slides

Cut the talk into a deck people can watch without reading a paragraph. The walk-away is a PowerPoint, after they approve the slides markdown. The plan is the deck they can still move around. Each look is a cue, about 15 to 30 seconds, a visual note for a later pass, speaker notes that point at the storyboard beat and the outline block. Chat is the sorter or one frame, not the plan and not the deck.

The recording is the asset. A slide that stays up while you talk for two minutes trains the room to read instead of listen. Keep the click moving. A slide that is the sentence you are about to say trains you to read. You say the sentence. The slide does not. Someone who only has the deck should still follow the argument. That is the leave-behind. It is not a reason to paste the talk onto the slides.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it. Use it for a palette already on disk and to keep on-screen wording in their voice. Do not add a story the storyboard does not use. If the file is missing, do not interview for company lore.
2. Find the storyboard. If they pointed at a file or folder, use that. Prefer `*-storyboard.md` or `storyboard.md`. If they pasted the storyboard, write it to disk in the directory they named (default: current directory) so the source is not only in chat: slug the talk title (`AI search in 2026` → `ai-search-in-2026-storyboard.md`), or `talk-storyboard.md` if there is no title. If more than one storyboard matches, ask which one. If there is no storyboard and they will not provide one, stop — see Refuse.
3. If they already pointed at a storyboard, write the slide files next to it. If not, ask where files should live (default: the directory that holds the storyboard, or the current directory) in the same message as any missing Inputs. Do not ask the directory first and the storyboard second.
4. Write the plan stub in the same turn as any missing-input questions, even if the talk has no title yet. Do not wait for the storyboard or the palette to create the file. Sessions die. The file is the memory. Name it from the storyboard file: `foo-storyboard.md` → `foo-slides.md`. If the source is `storyboard.md` or a paste, slug the talk title (`AI search in 2026` → `ai-search-in-2026-slides.md`). If there is no title yet, use `talk-slides.md`. The deck is the same slug with a `.pptx` suffix. If they ask for the slides only in chat, write the files anyway and keep chat short.
5. Read **The journey**, **Energy map**, **Beats**, and **Leave them** from the storyboard. Those headings are the usual shape. If the file uses different names, use the closest equivalents. If **Beats** is empty, stop and say the storyboard is not ready to cut into slides. Do not invent beats. Do not start storyboarding.
6. If the storyboard header names an outline file, read that outline. Use it to make the notes' Outline line precise. If the outline is missing, use each beat's **Place** and **From the outline**. Do not fetch a new outline. Do not rewrite the outline or the storyboard.
7. Resolve **Palette** before filling Slides. If the plan file, brand context, or their message already has background, text, and accent colors, copy them into the plan and keep going. If any of those three is missing, ask once in the same batch as other missing Inputs. Do not invent a brand palette. Hex values. A logo file they pointed at is optional and only goes on a title slide if they asked.
8. Set `pace` from what they said. Default `20`. Allowed range is 15-30 unless they overrode it. Honor `length` from the storyboard or outline header. Guide slide count is `length minutes * 60 / pace`, rounded to a whole number. A 20-minute talk at 20 seconds is about 60 slides. That number is a guide, not a quota. If length is unknown, do not invent a runtime. Cut from the beats at the default pace and note the missing length in Gaps.
9. Fill **Slides** in the plan before you ask them to approve it. One row per look. A beat is a run of slides, not one slide. Split when the look changes: a new number, a turn, a claim the room must see. Do not split just to park the next spoken sentence on its own slide. If reading the On screen column would give the talk, rewrite each line to the word, number, or fragment they need to see while you say the rest. A bullet list is one slide per idea, or throw the list away. Title and close are short runs, not a paragraph bio. One slide per beat is almost always a merge: if that beat's Hit has more than one thing the room should see, split it. Do not invent a fragment to hit the guide. Do not pad, merge, or refuse because the count is off the guide. Write the actual count next to the guide in Pace. They decide during approval whether to split, merge, or reorder. Do not change pace unless they named a new pace.
10. For each slide use this shape in the plan:

    - **On screen** — a cue. One sentence max, and only when that sentence is the claim the room should read. A fragment, a number, or a single word is better. No bullets. No clause pile. No story. No connective tissue.
    - **Visual** — the look besides type. `empty`, or `number|photo|diagram|quote — <what it is>`. Examples: `empty`, `number — the 3%`, `photo — screenshot of the 404 they already have`, `diagram — crawl loop, later`. Do not generate the image. Do not pick a stock photo. If they did not give a file, the asset stays in Gaps.
    - **Seconds** — 15-30, or their override. Default 20.
    - **Beat** — the storyboard beat name
    - **Outline** — the outline block this sits on (heading or short paraphrase)
    - **Notes** — beat name, outline place, the beat's Hit, and one line for why this look exists. Not a speech. Not a paragraph you would read aloud.

    If you cannot point at a beat, the slide is invented: cut it or move it to Gaps.
11. Write **Gaps**. What the storyboard or palette did not give you, visuals you named without an asset, and what you refused to invent.
12. Approve the plan. See **Approve the plan**. Do not render until `plan` is `approved`.
13. Render `<same-slug>-slides.pptx` from the approved plan. See **Build the pptx**. Do not add slides that are not in the plan. Do not call the plan the deck.
14. Set `status: ready` and `resume: done` when the pptx exists, the slide count matches the approved plan, the On screen column is not the talk, and a cold reader could click the deck with only the notes. Ready is about the deck, not about locking the outline. Missing visuals do not block ready.
15. In chat after the pptx exists: the plan path, the pptx path, slide count vs the pace guide, the palette in a few words, the first and last on-screen lines, and how many Visual rows still need an asset. Do not paste the plan. Do not paste slide text. If they want a change, edit the plan, then rebuild the pptx. Do not start a new walkthrough unless the storyboard journey changed. Do not start illustrating.

## Working files

```markdown
---
status: in-progress
talk: "<title from the storyboard, or unknown>"
storyboard: "<path to the storyboard file>"
outline: "<path from the storyboard header, or unknown>"
length: "<minutes from the storyboard or outline, or unknown>"
pace: 20
palette: missing
plan: draft
cursor: unset
deck: "<path to the pptx once written, or unset>"
resume: "<exact next step a cold session should do>"
---

# Slides — <title>

## Palette
- background: <#hex or unset>
- text: <#hex or unset>
- accent: <#hex or unset>

## Pace
<seconds per look, guide count, actual count, how you got there>

## Slides
### 1. <first words of on-screen text>
- On screen:
- Visual:
- Seconds:
- Beat:
- Outline:
- Notes:

## Gaps
```

`palette` in the header is `set` or `missing`. `plan` is `draft` until they approve from the sorter or the walk, or they skip; then `approved`. `cursor` is `sorter` during the sorter, the slide number during the walk, or `unset` before approval starts and after the plan is approved. `status` is `in-progress` until the pptx exists and matches the approved plan; then `ready`. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts (talk name, storyboard path, outline path, length, pace, palette, file paths, slides already planned, approval view, walkthrough place, plan approval, deck path). If `resume` is wait for the sorter, show the sorter and wait. If `resume` is wait for approval of slide N, show the previous / this / next frame for that slide and wait. Do not recut. Do not restart the approval. Do not paste the plan. Do not render. If `resume` is render from the approved plan, render. If they come back with a changed storyboard, read both files, revise the plan, set `plan: draft` and `cursor: unset`, and return to **Approve the plan**. If they say the deck reads like a script, or they want visual notes (not illustrations), rewrite On screen to cues and fill Visual. After a pptx already exists, rebuild. During approval, stay on `draft`. Do not generate images.

Palette, Pace, and the on-screen lines are skimmer zones. No storyboard recap, no "I considered…", no history of how you changed your mind. That belongs in Gaps or nowhere.

## Approve the plan

The plan is the deck they can still move around. The pptx is the hard work. Do not render until the plan is approved.

After Slides and Gaps are filled, show the **sorter**. Do not paste the plan. Set `cursor` to `sorter` and `resume` to wait for the sorter of `<count>`. If they already asked to walk one look, start that walk instead.

Two views. One per turn. Do not show both.

### Sorter

The whole deck, so they can merge, move, and see the grouping. No Previous / Next.

Chat only this:

- `<count>` looks. Guide count if length is known, and that the guide is not a quota
- Grouped by **Beat**, then by **Hit / why**. Consecutive looks that share a Beat stay under that Beat. Consecutive looks that share a Hit / why stay under that Hit / why. Do not invent a shared why to collapse them
- Stamps, four per row, in a fenced code block so the columns line up. Each stamp is two lines: `N <On screen>` and the Visual as written (`empty`, or `number|photo|diagram|quote — <what it is>`). If Visual is unset, write `empty`. Shorten either line so the stamp fits; do not wrap onto a third line. No Seconds. No letter codes. Blank line after the Beat name and after each Hit / why. Blank line between stamp rows. A `----` line between Hit / why groups. A blank line, a `----` line, and a blank line between Beats.
- One ask: merge a run, move a look, rewrite a cue, drop a look, walk a look, or approve

Wait. Do not render. Do not paste Outline, Notes, or Gaps. The sorter is the ask.

They are deciding order and grouping: which looks are the same look, where a look belongs. If they start dictating the talk onto a slide, keep On screen as a cue and put the point in Notes. Do not write a speech.

### Walk

When they walk a look, set `cursor` to that number and `resume` to wait for approval of slide N of `<count>`. Chat only this frame:

- `N of <count>`. Guide count if length is known, and that the guide is not a quota
- **Previous** — On screen of N-1, or `none` on slide 1
- **This** — On screen, Visual, Beat, Seconds, and the Notes Hit / why this look exists
- **Next** — On screen of N+1, or `none` on the last slide
- One ask: keep this look, combine it with next, rewrite the cue, drop it, or show the sorter

Wait. Do not render. Do not paste the rest of the file. Do not ask a second question in the same turn (count, palette, the spoken paragraph). The frame is the ask.

They are deciding what the room should see, and whether this look and the next one are the same look. If they start dictating the talk onto the slide, keep On screen as a cue and put the point in Notes. Do not write a speech.

### Apply

If they name more than one edit in one turn, resolve every number against the current numbering before any edit, then apply in the order they said, then renumber.

Then:

- **Merge A through B** — merge those rows into one look. Keep the cue that is the claim the room should read. Fold leftover Hits into Notes. Renumber. Set `cursor` to `sorter` and `resume` to wait for the sorter of `<count>`. Show it
- **Move N between A and B / after K / before K** — take look N and place it after A and before B (or after / before K). Renumber. Set `cursor` to `sorter` and `resume` to wait for the sorter of `<count>`. Show it
- **Drop N / drop A through B** — delete those rows. Renumber. Set `cursor` to `sorter` and `resume` to wait for the sorter of `<count>`. Show it
- **Rewrite N** — change On screen, Visual, or Notes as they said. Stay on the view they were in. Show it
- **Walk N / go to N / this look** — show the walk frame for N
- **Sorter / show the sorter / slide sorter** — set `cursor` to `sorter` and `resume` to wait for the sorter of `<count>`. Show it
- **Keep** (walk) — advance `cursor` to N+1 and show that frame, unless that was the last slide
- **Combine with next** (walk) — merge this row and the next into one look. Keep the cue that is the claim the room should read. Fold the leftover Hit into Notes. Renumber. Stay on this number (it is now the merged look) and show the new frame
- **Rewrite** (walk, this look) — change On screen, Visual, or Notes as they said. Stay on N. Show the frame again
- **Drop** (walk, this look) — delete this row, renumber, stay on this number (old next). Show the frame
- **Go to K / back** (walk) — set `cursor` to that number. Show that frame
- **Approve / looks good / Approve the rest / skip the review / just generate** — set `plan: approved`, set `cursor: unset`, and render. A skip mid-approval only when they said it now

When they keep the last slide, or approve from either view, set `plan: approved`, set `cursor: unset`, and render.

Skip the whole approval only when they already said to skip the review, not to workshop the plan, or to generate without looking at the markdown, or `plan` is already `approved` on disk. Naming the job (build the slides, generate the pptx, make the deck) is not a skip. Showing the sorter is not a skip. Do not skip because you think the count looks right.

One approval. They can bounce between the sorter and the walk. After they approve, render. Do not ask "one more?" If they ask to review again before the pptx, show the sorter once (or the walk if they asked for that), then render anyway. Leftover mush goes in Gaps.

`resume` during the sorter: wait for the sorter of `<count>`.
`resume` during the walk: wait for approval of slide N of `<count>`.

## Palette

Need three hex colors: background, text, accent. That is the whole system.

Look in this order, then stop:

1. The existing slides plan, if `palette` is `set`
2. Brand context, if it already names colors
3. Their message (hex, a named pair they spelled out, or a file they pointed at)
4. One ask

Do not scrape their website for a vibe. Do not invent "a professional blue." If they give two colors, ask for the third or use text as the missing contrast only when they said the background and you still need readable type. If you had to pick a contrast color they did not name, say so in Gaps.

Write the three hex values into **Palette** and set `palette: set`. If brand context exists and has no colors, add the same three there so the next deck run can skip the ask. If brand context does not exist, do not create it just for colors.

## Build the pptx

The approved plan is the source. The deck is `<same-slug>-slides.pptx` next to it. Do not render a `draft` plan.

Use Python and `python-pptx`. If the package is missing, `pip install python-pptx`. Do not switch to Keynote, Google Slides, HTML, Markdown-as-slides, or a PDF and call that done.

For every slide in the plan:

1. Add a blank 16:9 slide (13.333 in by 7.5 in).
2. Fill the background with the palette background.
3. Put **On screen** in one text box, large type (about 40-60 pt), high contrast against the background. Lots of empty space. No bullets, no footer, no page numbers, no logo unless they gave one and asked for it on the title slide. Accent is for a single word or number, not a rainbow. Do not draw the Visual. If Visual is a photo and they pointed at a file for that slide, place that file. Otherwise the slide is type on the background.
4. Write **Notes** into the PowerPoint speaker notes, in this order: Beat, Outline, Hit, why this look exists, Visual.

Save when every plan row has a slide. Confirm the slide count matches the plan. If render fails, leave `status: in-progress` and set `resume` to the render step. Do not paste the deck into chat.

Prefer a new slide over an on-click build. The point is a new look every 15-30 seconds, not a paragraph that reveals itself. Visual is the checklist for a later pass, not a reason to invent clipart.

## Inputs

Need a storyboard of the talk, not a topic. The usual file is `<talk-slug>-storyboard.md` next to where they want the deck. A stranger can write the same shape by hand. The headings that matter:

- **The journey** — walking in, walking out, the change
- **Beats** — each with Place, Energy, Feel, Hit, and From the outline
- **Leave them** — the feeling and idea they walk out holding
- Header `length` and `outline` when present

From the user's message (ask only if missing and it would make the deck wrong), in one batch:

1. Path to the storyboard, if they did not point at one, did not paste one, and `*-storyboard.md` / `storyboard.md` is not in front of you.
2. Where to write, if no storyboard file already anchors the directory (default: current directory).
3. Which storyboard, if more than one matches.
4. Background, text, and accent hex colors, if those are not already in the plan, brand context, or this message.

Do not ask for brand stories, a font, a logo, a target slide count, a design tool, or images. Do not fetch the topic on the web. Do not read other skills or the rest of the repo. Do not ask them to approve a plan you have not written yet.

If they name a pace, use it. If they do not, use 20 seconds and do not ask.

## Refuse

Stop in a few sentences if there is no storyboard and they will not provide one, if Beats is empty and they have not given a beat map, or if they want a different job: writing the outline from a blank page, storyboarding the feeling from scratch, a word-for-word speech, illustrating the deck or generating images, podcast guest prep, Keynote or Google Slides as the only file, or a fundraising pitch deck. Do not half-run those.
