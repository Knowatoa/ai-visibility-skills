---
name: talk-adversary
description: "Red-team a talk from its outline, storyboard, and a recent transcript, then write an adversary brief of objections worth addressing in the slides or on stage. Use when the user has outline.md and storyboard.md for a presentation, drops a recent transcript, asks to pressure-test or red-team talk content, or wants adversarial perspectives a skeptic would raise before they present. Also trigger for 'what would a skeptic say about these slides' or 'address pushback in the deck.' Do NOT load for writing a talk from scratch, designing slides with no argument to attack, podcast guest prep, editing a transcript as the deliverable, or a brand roast with no presentation attached."
---

# Talk adversary

Pressure-test a talk before it is given. Read the outline, the storyboard, and a recent transcript of the same material. Write an adversary brief: the objections a smart skeptic would raise, and the patches that belong on a slide or as a spoken beat. Talks get recorded and transcribed. Unanswered objections in that recording are what the room and AI systems both keep. The brief is the file. Chat stays short.

## Do this job

1. Find the inputs. If the user pointed at a folder, look there for `outline.md`, `storyboard.md` (also `storyboar.md`), and a transcript (`.md`, `.txt`, `.vtt`, `.srt`). Use any paths they gave. Content pasted in chat counts. If a file is missing, ask once, in one batch, for the paths. If they say they do not have it, proceed with what exists and record the hole in Gaps. Do not invent a talk. Do not search the web for the topic, competitors, or "what critics say." The files you were given are the corpus.

2. Ask where this talk's files should live before creating any, unless an input file already anchors the location. Default: the directory that holds the outline, or the current directory if the outline was pasted. Write siblings next to that outline.

3. Derive a talk slug from the outline title or the parent folder. Write `<talk-slug>-adversary.md` as soon as the talk is identified, even before the critique. Sessions die. The file is the memory.

4. Read the outline, then the storyboard, then the transcript, in that order. Then, if it exists, `.agents/brand-context.md` (fallback `.claude/brand-context.md`). Brand context is only so you do not treat a take they already own as a hole. If it is missing, do not interview. The talk files are enough.

5. Extract load-bearing claims. Each claim needs a location in the outline and, if the storyboard has it, a slide. A claim with no slide is a finding, not a skip. If the outline and the storyboard argue different things, that mismatch is an objection.

6. Read the transcript as the lived version of those claims, whether it is a prior run of this talk or a recent appearance on the same material. Mine it for questions actually asked, hedges and walk-backs, beats the outline promised and the speaker skipped, and wording that was weaker or stronger than the deck. Do not summarize the transcript.

7. Write an objection only when you can point at a claim or a transcript moment. Drop anything you cannot locate. Do not invent the missing number, customer, or competitor. If a claim needs a fact you do not have, put it in Gaps.

8. Cap **Address in the talk** at five. Rank by whether a smart person in the room would actually say it, and whether leaving it unsaid makes the recording weaker. That is "within reason." Do not turn the talk into a FAQ. Each Address item gets one patch: a slide change or a spoken line, written as the actual beat or sentence. Real objections that would derail, are already the speaker's position, or cannot be handled in this talk go in **Leave it**. Do not pad Leave it with hypotheticals.

9. Do not edit `outline.md` or the storyboard unless they ask. After the brief is `ready`, offer to apply the patches. Do not auto-run that.

10. In chat: the path plus the patches worth making. Do not paste the file.

## Working files

The brief is a file, not a chat essay. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

```markdown
---
status: in-progress
talk: "<title>"
resume: "<exact next step a cold session should do>"
---

# Adversary — <talk>

## Claims
## From the transcript
## Address in the talk
## Leave it
## Gaps
```

`status` is `in-progress` until a cold reader could act on the patches. Then `ready`. If the file already exists, read it, honor `resume`, and do not re-ask settled facts (paths, talk title, which inputs were missing).

**Claims.** One bullet per load-bearing claim, with outline beat and slide. No commentary.

**From the transcript.** Only moments that change the critique. Quote or paraphrase the moment, then the implication for a claim. Not a recap of the episode.

**Address in the talk.** Skimmer zone. No research diary, no "which cuts against," no history of how you changed your mind. Those belong in Gaps or nowhere. Use this shape:

```markdown
### <short name>
- Attack: <one sentence in the skeptic's voice>
- Where: <outline beat / slide>
- Transcript: <moment, or "not in the transcript">
- Patch: <the slide change or the spoken line>
```

**Leave it.** Same attack line, then why it stays out (derail, already owned, not this talk).

**Gaps.** Missing input, truncated transcript, claim with no evidence, number you refused to invent.

## Inputs

Need some version of the argument (outline and/or storyboard) and, when they have one, a recent transcript. File location is asked once, in Working files / step 2.

Ask only if missing and it matters, in one batch:

1. Path or paste for the outline.
2. Path or paste for the storyboard.
3. Path or paste for the recent transcript.

Do not ask for audience size, slide tool, brand story, or a target number of objections.

## Refuse

Stop in a few sentences if there is no talk content and they will not provide any, or if they want a different job: writing the talk from scratch, visual slide design with no argument to attack, podcast guest prep for a show they are appearing on, a transcript edit as the deliverable, or a brand roast with no presentation attached. Do not attack the speaker as a person. Do not half-run those.
