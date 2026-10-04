---
name: talk-adversary
description: "Pressure-tests a talk against a recent rehearsal or live transcript that will often disagree with the outline, storyboard, and slides. Maps the drift, rewrites the outline to the talk that was actually spoken, then surfaces up to five holes, criticisms, and stuck questions and writes them back into the outline, storyboard, and slides plan. Ends with what to do differently when outlining the next talk. Use when the user has a transcript plus an outline, storyboard, or slides, says the spoken talk drifted from the deck, or asks to find holes, backup, pushback, or stuck questions before they present again. Also trigger for 'red-team this talk', 'what would a skeptic say', 'update the outline from my rehearsal', or 'address pushback in the deck.' Do NOT load for writing a talk from scratch with no source to attack, cleaning a transcript as the deliverable, podcast guest prep, illustrating slides, or a brand roast with no presentation attached."
---

# Talk adversary

Read the outline, storyboard, slides plan, and a recent transcript. The transcript will often be a different talk than the files. That is expected and usually good: the spoken version is what the speaker can actually carry.

**The spoken talk wins by default.** Rewrite the files to match it, then attack it. Restore a planned element only when the plan's version is clearly stronger, and say why in one line. Do not drag the talk back toward the plan for its own sake.

Chat stays short. The files are the work.

## Do this job

1. **Find the inputs.** Look where the user pointed for `*-outline.md` / `outline.md`, `*-storyboard.md`, `*-slides.md` / `slides.md`, and a transcript (`.md`, `.txt`, `.vtt`, `.srt`). Pasted content counts. If more than one file matches a role, or a role is missing, ask once in one batch. If they have no file for a role, go on without it and note it in Gaps. If no input anchors a directory, ask where files live in that same batch (default: current directory). Do not search the web.

2. **Read** the outline, then the storyboard, then the slides plan, then the transcript. Then `.agents/brand-context.md` (fallback `.claude/brand-context.md`) if it exists, only so you do not flag a take they already own. If the outline already has `adversary-resume`, honor it and do not re-ask settled facts.

3. **Map the drift.** Write `## Drift` in the outline first: one row per planned block and per new spoken section, in spoken order.

   | Planned block (min) | Spoken (timestamp, ~min) | Verdict |
   |---|---|---|

   Verdict is one of `kept`, `moved`, `replaced`, `new`, `dropped`, with a few words on what changed. Use transcript timestamps when they exist. Note total planned vs. spoken time. This table is the most useful thing in the pass; write it before any finding.

4. **Rewrite the Outline to the spoken talk.** Rebuild `## Outline` blocks in spoken order with spoken timings: point and proof, written as sentences the speaker can say, using the speaker's own strongest lines from the transcript. If the speaker used a different organizing idea than the outline (for example a new noun or three moves in place of a list of patterns), the spoken one becomes the **Spine**. Move planned material that was not spoken to `## Cut (planned, not spoken)`, one line each, so nothing is lost. Do not append "run-through notes" next to the old blocks; one outline, one talk. Keep the header fields and the three boxes. Update **What the audience gets** only if the spoken takeaway clearly changed, using the speaker's words.

5. **Find up to five write-backs.** For each spoken talking point, decide: hole (a load-bearing claim with no story, number, or cue), needs backup, already backed, criticism (what a smart person in the room would say), or stuck question (what they turn over instead of hearing the next beat). Keep a finding only if it uses nouns from this talk and points at a transcript moment. If it would read true on any other talk, drop it. Rank by whether someone in the room would actually push back, and whether leaving it unsaid weakens the recording. Cap at five. Do not turn the talk into a FAQ.

6. **Apply them.** Fold each write-back into its outline block as a normal sentence (point and proof), not as Attack/Patch commentary. Label each in **Holes** as `adopt-spoken` (sharpens something the speaker said) or `restore-plan` (brings back a planned element, with the one-line reason). Then patch the matching storyboard beat and slides row (see Write back). Findings that would derail, are already owned, or cannot be handled in this talk go in **Leave it**, one line each.

7. **Write `## Next time`**: two to five lines on what the planning files got wrong that the spoken talk fixed, phrased as advice for outlining and storyboarding the next talk. Example: "Proof from a tweet was dropped on stage; this week's lived stories replaced it. Next outline: lived proof only." Only lessons the drift map shows. No generic speaking tips.

8. Set `status: ready` and `adversary-resume: done` once the outline, storyboard, and slides plan you have are patched. In chat: the paths, the drift in three or four lines, the write-backs, and the Next time lines. Do not paste the files. Stop. Do not start a new storyboard or a full slide rebuild.

## Working files

The outline is the resume file. If none exists, write `outline.md` as soon as the talk is identified, before the first finding. Sessions die.

`adversary-resume` is the only progress pointer for this skill. Do not touch `resume`; it belongs to whatever wrote the outline. Keep header fields the outline already has. Do not touch Scratch rounds.

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

## Spine
## Outline
## Drift
## Holes
## Leave it
## Cut (planned, not spoken)
## Next time
## Gaps
```

**Outline** and **Spine** are skimmer zones: what the speaker says, in order. No research diary, no history of changes. The history lives in Drift and Cut.

**Holes.** Talking point, what is missing, criticism or stuck question, `adopt-spoken` or `restore-plan`, and where you wrote it back (outline block, storyboard beat, slide N).

**Gaps.** Missing input, truncated transcript, a claim with no source, a number you refused to invent, a stale pptx.

## Write back

Outline first, then storyboard, then slides. Same findings, no second list.

**Storyboard.** Usual beat shape: Place, Energy, Feel, Hit, Stands alone. Repoint each beat's Place at the rewritten outline block. If a planned beat's block was dropped, delete the beat and list it under the storyboard's Gaps; if a new spoken section carries a feeling no beat has, add one short beat. Update Hit where a write-back changes what the beat must land. Do not rewrite The journey unless the takeaway changed. Do not theatricalize. If there is no storyboard, note it in Gaps.

**Slides plan.** Usual row shape: On screen, Visual, Seconds, Beat, Outline, Notes. On screen stays a cue: a word, a number, or one claim. Put backup and stuck-question answers in Notes. Add a look only when the room needs to see something that was a hole (a source line under a number, a screenshot the speaker referenced). If the speaker presented looks the plan does not have, add rows for them. If there is no slides plan, note it in Gaps.

Do not rebuild a `.pptx`. If one sits next to the plan, note in Gaps that it is stale and needs a regeneration from the updated plan.

## Examples

`examples/` in this skill's folder, if present, shows a real drift map, a rewritten block, a Cut entry, and Next time lines from one talk. Read it only if you are unsure of the shape.

## Refuse

Stop in a few sentences if there is no talk content and they will not provide any, or if they want a different job: writing the talk from scratch with nothing to pressure-test, cleaning or publishing a transcript as the deliverable, visual slide design or illustration, podcast guest prep, or a brand roast with no presentation attached. Do not attack the speaker as a person. Do not half-run those.
