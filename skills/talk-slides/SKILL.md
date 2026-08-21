---
name: talk-slides
description: "Builds a sparse PowerPoint deck from a talk storyboard: about 15-30 seconds per slide, one sentence max on screen, speaker notes that tie each slide back to the outline and the beats. Use when the user says build the slides, make the deck, turn this storyboard into PowerPoint, generate the pptx, I want build-style slides, keep each slide to a sentence, or 'visually engaging slides that move fast'. Do NOT load for writing the outline, mapping the emotional journey from scratch, a word-for-word speech, podcast guest prep, Keynote or Google Slides as the only output, or a fundraising pitch deck."
---

# Talk slides

Cut the talk into a deck people can watch without reading a paragraph. The walk-away is a PowerPoint: one sentence or less on each slide, about 15 to 30 seconds a look, speaker notes that point at the storyboard beat and the outline block. Chat is a short status, not the deck.

The recording is the asset. A slide that stays up while you talk for two minutes trains the room to read instead of listen. Keep the click moving.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it. Use it for a palette already on disk and to keep on-screen wording in their voice. Do not add a story the storyboard does not use. If the file is missing, do not interview for company lore.
2. Find the storyboard. If they pointed at a file or folder, use that. Prefer `*-storyboard.md` or `storyboard.md`. If they pasted the storyboard, write it to disk in the directory they named (default: current directory) so the source is not only in chat: slug the talk title (`AI search in 2026` → `ai-search-in-2026-storyboard.md`), or `talk-storyboard.md` if there is no title. If more than one storyboard matches, ask which one. If there is no storyboard and they will not provide one, stop — see Refuse.
3. If they already pointed at a storyboard, write the slide files next to it. If not, ask where files should live (default: the directory that holds the storyboard, or the current directory) in the same message as any missing Inputs. Do not ask the directory first and the storyboard second.
4. Write the plan stub in the same turn as any missing-input questions, even if the talk has no title yet. Do not wait for the storyboard or the palette to create the file. Sessions die. The file is the memory. Name it from the storyboard file: `foo-storyboard.md` → `foo-slides.md`. If the source is `storyboard.md` or a paste, slug the talk title (`AI search in 2026` → `ai-search-in-2026-slides.md`). If there is no title yet, use `talk-slides.md`. The deck is the same slug with a `.pptx` suffix. If they ask for the slides only in chat, write the files anyway and keep chat short.
5. Read **The journey**, **Energy map**, **Beats**, and **Leave them** from the storyboard. Those headings are the usual shape. If the file uses different names, use the closest equivalents. If **Beats** is empty, stop and say the storyboard is not ready to cut into slides. Do not invent beats. Do not start storyboarding.
6. If the storyboard header names an outline file, read that outline. Use it to make the notes' Outline line precise. If the outline is missing, use each beat's **Place** and **From the outline**. Do not fetch a new outline. Do not rewrite the outline or the storyboard.
7. Resolve **Palette** before filling Slides. If the plan file, brand context, or their message already has background, text, and accent colors, copy them into the plan and keep going. If any of those three is missing, ask once in the same batch as other missing Inputs. Do not invent a brand palette. Hex values. A logo file they pointed at is optional and only goes on a title slide if they asked.
8. Set `pace` from what they said. Default `20`. Allowed range is 15-30 unless they overrode it. Honor `length` from the storyboard or outline header. Target slide count is `length minutes * 60 / pace`, rounded to a whole number. A 20-minute talk at 20 seconds is about 60 slides. If length is unknown, do not invent a runtime. Cut from the beats at the default pace and note the missing length in Gaps.
9. Fill **Slides** in the plan before you render the deck. One row per look. A beat is a run of slides, not one slide. Split when the next sentence, number, or turn would otherwise sit on screen too long. Two sentences is two slides. A bullet list is one slide per bullet, or better, one slide per idea and throw the list away. Title and close are short runs, not a paragraph bio. If length is known and the plan is under about 80% of the target count, you merged looks. Split again before you render. Do not ship a 12-slide deck for a 20-minute talk.
10. For each slide use this shape in the plan:

    - **On screen** — one sentence max. A fragment, a number, or a single word is better. No bullets. No clause pile.
    - **Seconds** — 15-30, or their override. Default 20.
    - **Beat** — the storyboard beat name
    - **Outline** — the outline block this sits on (heading or short paraphrase)
    - **Notes** — beat name, outline place, the beat's Hit, and one line for why this look exists. Not a speech. Not a paragraph you would read aloud.

    If you cannot point at a beat, the slide is invented: cut it or move it to Gaps.
11. Write **Gaps**. What the storyboard or palette did not give you, and what you refused to invent.
12. Render `<same-slug>-slides.pptx` from the plan. See **Build the pptx**. Do not add slides that are not in the plan. Do not call the plan the deck.
13. Set `status: ready` and `resume: done` when the pptx exists, the slide count matches the plan, and a cold reader could click the deck with only the notes. Ready is about the deck, not about locking the outline.
14. In chat: the plan path, the pptx path, slide count vs the target from length and pace, the palette in a few words, and the first and last on-screen lines. Do not paste the plan. Do not paste slide text. If they want a revision, change the plan, then rebuild the pptx. Three passes is the cap: your first deck, then at most two revisions. If they accept earlier, stop. After the third pass, lock the deck anyway and leave leftover mush in Gaps.

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
deck: "<path to the pptx once written, or unset>"
resume: "<exact next step a cold session should do>"
---

# Slides — <title>

## Palette
- background: <#hex or unset>
- text: <#hex or unset>
- accent: <#hex or unset>

## Pace
<seconds per look, target count, how you got there>

## Slides
### 1. <first words of on-screen text>
- On screen:
- Seconds:
- Beat:
- Outline:
- Notes:

## Gaps
```

`palette` in the header is `set` or `missing`. `status` is `in-progress` until the pptx exists and matches the plan; then `ready`. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts (talk name, storyboard path, outline path, length, pace, palette, file paths, slides already planned, deck path). If they come back with a changed storyboard, read both files and revise the plan, then rebuild the pptx. Do not restart from slide 1 unless the journey changed.

Palette, Pace, and the on-screen lines are skimmer zones. No storyboard recap, no "I considered…", no history of how you changed your mind. That belongs in Gaps or nowhere.

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

The plan is the source. The deck is `<same-slug>-slides.pptx` next to it.

Use Python and `python-pptx`. If the package is missing, `pip install python-pptx`. Do not switch to Keynote, Google Slides, HTML, Markdown-as-slides, or a PDF and call that done.

For every slide in the plan:

1. Add a blank 16:9 slide (13.333 in by 7.5 in).
2. Fill the background with the palette background.
3. Put **On screen** in one text box, large type (about 40-60 pt), high contrast against the background. Lots of empty space. No bullets, no footer, no page numbers, no logo unless they gave one and asked for it on the title slide. Accent is for a single word or number, not a rainbow.
4. Write **Notes** into the PowerPoint speaker notes, in this order: Beat, Outline, Hit, why this look exists.

Save when every plan row has a slide. Confirm the slide count matches the plan. If render fails, leave `status: in-progress` and set `resume` to the render step. Do not paste the deck into chat.

Prefer a new slide over an on-click build. The point is a new look every 15-30 seconds, not a paragraph that reveals itself.

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

Do not ask for brand stories, a font, a logo, a target slide count, or a design tool. Do not fetch the topic on the web. Do not read other skills or the rest of the repo.

If they name a pace, use it. If they do not, use 20 seconds and do not ask.

## Refuse

Stop in a few sentences if there is no storyboard and they will not provide one, if Beats is empty and they have not given a beat map, or if they want a different job: writing the outline from a blank page, storyboarding the feeling from scratch, a word-for-word speech, podcast guest prep, Keynote or Google Slides as the only file, or a fundraising pitch deck. Do not half-run those.
