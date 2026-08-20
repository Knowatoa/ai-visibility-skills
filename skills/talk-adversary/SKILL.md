---
name: talk-adversary
description: "Red-team a talk from its storyboard, a recent transcript, and any existing outline, then write outline.md with the objections worth addressing folded into the talk. Use when the user has outline.md and storyboard.md for a presentation, drops a recent transcript, asks to pressure-test or red-team talk content, or wants adversarial perspectives a skeptic would raise before they present. Also trigger for 'what would a skeptic say about these slides' or 'address pushback in the deck.' Do NOT load for writing a talk from scratch with no source to attack, designing slides with no argument to attack, podcast guest prep, editing a transcript as the deliverable, or a brand roast with no presentation attached."
---

# Talk adversary

Pressure-test a talk before it is given. Read the storyboard, a recent transcript, and any existing outline. Write `outline.md`: the talk, with the objections a smart skeptic would raise already answered in the beats, within reason. Talks get recorded and transcribed. Unanswered objections in that recording are what the room and AI systems both keep. The outline is the file. Chat stays short.

## Do this job

1. Find the inputs. If the user pointed at a folder, look there for `outline.md` or `*-outline.md`, `storyboard.md` / `storyboar.md` / `*-storyboard.md`, and a transcript (`.md`, `.txt`, `.vtt`, `.srt`). Use any paths they gave. Content pasted in chat counts. If more than one outline or storyboard matches, ask which one. If a file is missing, ask once, in one batch, for the paths. If they say they do not have it, proceed with what exists and record the hole in Gaps. Do not invent a talk. Do not search the web for the topic, competitors, or "what critics say." The files you were given are the corpus.

2. Ask where this talk's files should live before creating any, unless an input file already anchors the location. Default: the directory that holds the existing outline or storyboard, or the current directory if the material was pasted. The working file is always `outline.md` in that directory. If location and input paths are both unknown, ask for them in the same batch. Do not ask where to write, wait, then ask for the storyboard.

3. Write `outline.md` as soon as the talk is identified, before the first objection. If `outline.md` already exists, it is the file: read it, honor `resume`, do not blank it. If they pointed at a differently named outline, read that as source and write `outline.md`. Do not overwrite the source unless it is already `outline.md`. Sessions die. The file is the memory.

4. Read the existing outline (if any), then the storyboard, then the transcript, in that order. Then, if it exists, `.agents/brand-context.md` (fallback `.claude/brand-context.md`). Brand context is only so you do not treat a take they already own as a hole. If it is missing, do not interview. The talk files are enough.

5. Extract load-bearing claims. Include the talk's named audience, takeaway, or presenter win when the outline has those boxes. Each claim needs a location in the outline and, if the storyboard has it, a slide. A claim with no slide is a finding, not a skip. If the outline and the storyboard argue different things, that mismatch is an objection.

6. Read the transcript as the lived version of those claims, whether it is a prior run of this talk or a recent appearance on the same material. Mine it for questions actually asked, hedges and walk-backs, beats the outline promised and the speaker skipped, and wording that was weaker or stronger than the deck. Do not summarize the transcript.

7. Keep an objection only when you can point at a claim or a transcript moment. It must use nouns from the files (a named claim, slide, story, or number). If you could paste it onto a different talk and it would still read true, drop it. Do not invent the missing number, customer, or competitor. If a claim needs a fact you do not have, put it in Gaps.

8. Cap addresses at five. Rank by whether a smart person in the room would actually say it, and whether leaving it unsaid makes the recording weaker. That is "within reason." Do not turn the talk into a FAQ. Fold each address into the matching outline block as a normal beat the speaker can say or put on a slide, not as Attack/Patch commentary. Preserve headings and boxes already in the file. Create **Leave it** and **Gaps** at the end if they are missing. Real objections that would derail, are already the speaker's position, or cannot be handled in this talk go in Leave it. Do not pad Leave it with hypotheticals.

9. Do not edit the storyboard unless they ask. After `outline.md` is `ready`, offer to apply matching storyboard changes. Do not auto-run that.

10. In chat: the path plus the beats folded in. Do not paste the file.

## Working files

The outline is a file, not a chat essay. Ask where this talk's files should live before creating any (default: the current directory). If they already pointed at a folder or an existing outline, use that directory and write `outline.md` there. Do not ask this again in Inputs.

`resume` is the only progress pointer. Do not also keep a Status heading in the body.

If `outline.md` already has talk sections, keep them. Add only what is missing:

```markdown
---
status: in-progress
talk: "<title>"
resume: "<exact next step a cold session should do>"
---

# Outline: <talk>

## Outline
## Leave it
## Gaps
```

`status` is `in-progress` until a cold reader could give the talk from the Outline, including the folded-in addresses. Then `ready`. If the file already exists, read it, honor `resume`, and do not re-ask settled facts (paths, talk title, which inputs were missing).

**Outline.** Skimmer zone. Timed or named blocks with the point, the proof, and any address beat written as a sentence they can say. No research diary, no "which cuts against," no history of how you changed your mind. Those belong in Gaps or nowhere.

**Leave it.** One attack line, then why it stays out (derail, already owned, not this talk).

**Gaps.** Missing input, truncated transcript, claim with no evidence, number you refused to invent, source outline path if it was not already `outline.md`.

## Inputs

Need some version of the argument (outline and/or storyboard) and, when they have one, a recent transcript. File location is asked once, in Working files / step 2.

Ask only if missing and it matters, in one batch:

1. Path or paste for the existing outline, if they have one.
2. Path or paste for the storyboard.
3. Path or paste for the recent transcript.

If you also do not know where to write `outline.md`, include that here. Do not drip.

Do not ask for audience size, slide tool, brand story, or a target number of objections.

## Refuse

Stop in a few sentences if there is no talk content and they will not provide any, or if they want a different job: writing the talk from scratch with nothing to pressure-test, visual slide design with no argument to attack, podcast guest prep for a show they are appearing on, a transcript edit as the deliverable, or a brand roast with no presentation attached. Do not attack the speaker as a person. Do not half-run those.
