---
name: talk-adversary
description: "Pressure-tests a talk against a recent transcript that will often disagree with the outline, storyboard, and slides. Surfaces talking points, holes that need backup, criticisms, and questions the room gets stuck on, then writes the ones worth keeping back into those files. Use when the user has a transcript plus outline.md, storyboard.md, or slides, says the spoken talk drifted from the deck, or asks to find holes, backup, pushback, or stuck questions before they present again. Also trigger for 'red-team this talk', 'what would a skeptic say', or 'address pushback in the deck.' Do NOT load for writing a talk from scratch with no source to attack, cleaning a transcript as the deliverable, podcast guest prep, illustrating slides, or a brand roast with no presentation attached."
---

# Talk adversary

Read the outline, storyboard, slides, and a recent transcript. The transcript will often be a different talk than the files. That is expected. After the deck exists, the spoken version moves. Do not treat that drift as a defect and do not "fix" the transcript to match the plan.

Surface the talking points, the holes in them, what needs backup and what does not, criticisms of the talk or the transcript, and questions people get stuck on. Write the ones worth keeping back into the outline, the storyboard, and the slides. Chat stays short.

## Do this job

1. Find the inputs. If the user pointed at a folder, look there for `outline.md` or `*-outline.md`, `storyboard.md` / `storyboar.md` / `*-storyboard.md`, `slides.md` / `*-slides.md` / `*.pptx`, and a transcript (`.md`, `.txt`, `.vtt`, `.srt`). Use any paths they gave. Content pasted in chat counts. If more than one file matches a role, ask which one. If a file is missing, ask once, in one batch, for the paths. If they say they do not have it, proceed with what exists and record the hole in Gaps. Do not invent a talk. Do not search the web for the topic, competitors, or "what critics say." The files you were given are the corpus.

2. Ask where this talk's files should live before creating any, unless an input file already anchors the location. Default: the directory that holds the outline, storyboard, or slides. If location and input paths are both unknown, ask for them in the same batch. Do not ask where to write, wait, then ask for the transcript.

3. The working file is the outline you will write back to. If `outline.md` or a `*-outline.md` already exists, that file is it: read it, honor `adversary-resume`, do not blank it. If they pointed at a differently named outline, edit that file. If there is no outline, write `outline.md` in the working directory as soon as the talk is identified, before the first finding. Sessions die. The outline is the memory.

4. Read the outline, then the storyboard, then the slides plan, then the transcript, in that order. Then, if it exists, `.agents/brand-context.md` (fallback `.claude/brand-context.md`). Brand context is only so you do not treat a take they already own as a hole. If it is missing, do not interview. The talk files are enough.

5. Extract talking points from every source you have. Tag each one planned or spoken. Include the named audience, takeaway, or presenter win when the outline has those boxes. A point that exists in the transcript and not in the files is a candidate to write back, not a problem. A point that exists in the files and vanished from the transcript is a hole or a drop, not a crime. Do not summarize the transcript.

6. For each talking point, decide: hole, needs backup, already backed, criticism, or stuck question. A hole is a load-bearing claim with no story, number, or slide cue. "Already backed" means the files or the transcript already carry the proof; leave it alone. A criticism is what a smart person in the room would actually say. A stuck question is the thing they turn over instead of hearing the next beat.

7. Keep a finding only when you can point at a talking point or a transcript moment. It must use nouns from the files (a named claim, slide, story, or number). If you could paste it onto a different talk and it would still read true, drop it. Do not invent the missing number, customer, or competitor. If a claim needs a fact you do not have, put it in Gaps.

8. Cap write-backs at five. Rank by whether a smart person in the room would actually get stuck or push back, and whether leaving it unsaid makes the recording weaker. That is "within reason." Do not turn the talk into a FAQ. Fold each write-back into the matching outline block as a normal beat (point and proof), not as Attack/Patch commentary. Then patch the matching storyboard beat and slides row. Preserve headings already in those files. Create **Holes**, **Leave it**, and **Gaps** at the end of the outline if they are missing. Real findings that would derail, are already owned, or cannot be handled in this talk go in Leave it. Do not pad Leave it with hypotheticals.

9. Apply the write-backs. Do not wait to be asked, and do not stop at the outline. See **Write back**. After the files are `ready`, stop. Do not start a new outline, a new storyboard, or a full slide rebuild beyond the rows you patched.

10. In chat: the paths plus the talking points you wrote back and the holes you left. Do not paste the files.

## Working files

The outline is the resume file, not a chat essay. Ask where this talk's files should live before creating any (default: the current directory). If they already pointed at a folder or an existing outline, use that directory. Do not ask this again in Inputs.

`adversary-resume` is the only progress pointer for adversary work. Do not also keep a Status heading in the body. (The `resume` field belongs to `talk-outline` and should not be touched.)

If the outline already has talk sections, keep them. Add only what is missing:

```markdown
---
status: in-progress
talk: "<title>"
storyboard: "<path or unset>"
slides: "<path or unset>"
transcript: "<path or unset>"
adversary-resume: "<exact next step a cold session should do>"
---

# Outline: <talk>

## Outline
## Holes
## Leave it
## Gaps
```

`status` is `in-progress` until a cold reader could give the talk from the Outline and the write-backs are in the storyboard and slides you have. Then `ready`. If the file already exists, read it, honor `adversary-resume`, and do not re-ask settled facts (paths, talk title, which inputs were missing). Keep header fields the outline already has (`event`, `when`, `length`, `pace`, `resume`). Do not touch Scratch rounds.

**Outline.** Skimmer zone. Timed or named blocks with the point, the proof, and any write-back written as a sentence they can say. No research diary, no "which cuts against," no history of how you changed your mind.

**Holes.** Talking point, what is missing, backup needed or not, criticism or stuck question, and where you wrote it back (outline block, storyboard beat, slide N) or why you did not.

**Leave it.** One line, then why it stays out (derail, already owned, already backed, not this talk).

**Gaps.** Missing input, truncated transcript, claim with no evidence, number you refused to invent, pptx left stale.

## Write back

Do the outline first, then the storyboard, then the slides. Same five findings. Do not invent a second list.

**Storyboard** (`storyboard.md`, `storyboar.md`, or `*-storyboard.md`). Usual beat shape: Place, Energy, Feel, Hit, From the outline. If the headings differ, use the closest equivalents. Update Hit and From the outline on the beat whose Place matches the outline block. Add a beat only when a stuck question needs a feeling the journey does not have. Do not theatricalize. Do not rewrite The journey unless the Monday takeaway changed. If there is no storyboard, put that in Gaps and keep going.

**Slides** (`slides.md` or `*-slides.md`). Usual row shape: On screen, Visual, Seconds, Beat, Outline, Notes. On screen stays a cue: a word, a number, or one claim. Do not put the spoken line on the slide. Put the backup or the answer to the stuck question in Notes. Add a look only when the room needs to see something that was a hole. Do not add a slide per criticism. If there is no slides plan, put that in Gaps.

If a `.pptx` sits next to the plan, rebuild it from the updated plan after the markdown is ready. Use python-pptx. 16:9, on-screen cue large, notes in speaker notes. Do not generate images. If render fails or the package is missing, leave the markdown ready and put the pptx in Gaps.

## Inputs

Need a transcript and some version of the planned talk (outline, storyboard, or slides). File location is asked once, in Working files / step 2.

Ask only if missing and it matters, in one batch:

1. Path or paste for the existing outline, if they have one.
2. Path or paste for the storyboard.
3. Path or paste for the slides plan or deck.
4. Path or paste for the recent transcript.

If you also do not know where to write, include that here. Do not drip.

Do not ask for audience size, slide tool, brand story, or a target number of findings.

## Refuse

Stop in a few sentences if there is no talk content and they will not provide any, or if they want a different job: writing the talk from scratch with nothing to pressure-test, cleaning or publishing a transcript as the deliverable, visual slide design or illustration with no argument to attack, podcast guest prep for a show they are appearing on, or a brand roast with no presentation attached. Do not attack the speaker as a person. Do not half-run those.
