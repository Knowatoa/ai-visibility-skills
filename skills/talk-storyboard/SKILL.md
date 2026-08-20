---
name: talk-storyboard
description: "Turns a talk draft (usually output.md) into a storyboard of the audience's energy, emotions, and beats. Use when the user says storyboard this talk, create a storyboard from output.md, map the emotional journey of this talk, or asks what beats we should hit. Do NOT load for film or product storyboards, designing slides, writing a full speech from a blank page, podcast appearance prep, or brand positioning with no talk attached."
---

# Talk storyboard

The goal of this skill is to convey the energy and emotions we want to take the audience through. The journey they are taking as we present this talk. What are the beats we want to hit.

The source is `output.md` (or another talk draft they point at). The walk-away file is `storyboard.md` next to that source. Chat is a short read of the journey and the beat names, not the file.

## Working files

If they pointed at a talk file, write `storyboard.md` next to it. If they said "storyboard" and `output.md` is in the current directory, use that. Otherwise ask once where the talk file lives and where to write (default: current directory, source name `output.md`).

Create `storyboard.md` as soon as the source is identified, even if the beats are still empty. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

```markdown
---
status: in-progress
source: "<path to output.md or the talk draft>"
talk: "<title from the source, or unknown>"
resume: "<exact next step a cold session should do>"
---

# Storyboard — <talk>

## The journey
## Energy map
## Beats
## Leave them
## Gaps
```

`status` is `in-progress` until a cold reader could run the talk from the beats. Then `ready`. If the file already exists, read it, honor `resume`, and do not re-ask the source path or talk title.

In chat: the path, the journey in a few sentences, and the beat names in order. Do not paste the file. If they ask for the storyboard only in chat, write the file anyway and keep chat short.

## Do this job

1. Read the source. Do not open other repo files, other skills, or a research tour. The storyboard comes from this talk, not from extra lore.

2. Name the talk from the source's title or first heading. Write the working-file header and the empty section headings.

3. Write **The journey**. One paragraph. What the audience believes or feels walking in, what they should feel walking out, and the change this talk is for. This is a skimmer zone: no outline recap, no diary of how you read the source.

4. Cut the source into **beats**. A beat is a change in energy or emotion, not a heading. If two sections feel the same, they are one beat. Do not force a three-act shape the source does not support. Do not map every heading to its own beat. A twenty-minute talk is often five to eight beats. Do not pad.

5. Fill **Energy map** as a numbered list: beat name, energy, feel. Someone late to the file should understand the whole talk from this list.

6. Fill **Beats**. For each beat use this shape:

   - **Place** — where this sits in the source (heading or short paraphrase), so a later session can find it
   - **Energy** — the room, in words a speaker could direct to. Quiet lean-in, rising unease, laugh-release, peak, still. Not "high energy" and not "engaging"
   - **Feel** — the audience's emotion in their mouth ("that's me", "wait, we're the problem", "I can try this Monday"). Not "inspiring"
   - **Hit** — the one thing this beat must land. One sentence
   - **From the source** — quote or tight paraphrase of the material this beat uses. If you cannot point at the source, the beat is invented: cut it or move it to Gaps

7. Write **Leave them**. One feeling and one idea they walk out holding. If that is not the last beat, say why.

8. Write **Gaps**. What the source did not give you (duration, room, a missing turn) and what you refused to invent.

9. Set `status: ready` and `resume: done` when the beats cover every major turn in the source and nothing important is left only in chat.

## Inputs

Need a talk source. Default filename: `output.md`.

Ask only if missing and it would make the beats wrong, in one batch:

1. Path to the talk draft, if `output.md` is not in front of you and they did not paste the talk.
2. Rough duration or room (lightning / 20 min / keynote) if the source is silent and beat count would be wrong without it.

If they paste the talk in chat, write it to `output.md` in the directory they named (default: current directory), then storyboard. Do not leave the source only in chat.

Do not ask for brand stories, slide count, or design tools. Do not fetch the topic on the web.

## Refuse

Stop in a few sentences if there is no talk source and they will not provide one, or if they want a different job: a film or product storyboard, slide design, a full speech written from a blank page, podcast appearance prep, or brand positioning with no talk attached. Do not half-run those.
