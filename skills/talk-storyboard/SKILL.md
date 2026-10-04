---
name: talk-storyboard
description: "Maps how the audience should feel beat by beat through a talk outline, flags the beats that only work if the speaker delivers the plan exactly, and says whether that outline is the one to keep. Starts from a locked outline file (`*-outline.md`) that names the audience, the Monday takeaway, and the talk blocks. Use when the user says storyboard this talk, map the emotional journey, how should the audience feel throughout, turn this outline into a storyboard, what beats should we hit, or 'is this the outline we want'. Do NOT load for writing the outline from scratch, slide design, a full speech, podcast guest prep, film or product storyboards, or a fundraising pitch deck."
---

# Talk storyboard

Lock the feeling of the talk before you lock the outline. The walk-away file is a short storyboard of the emotion the audience should move through. If that journey does not earn the Monday takeaway, the outline is not the one yet. Chat is a short read, not the file.

Storyboard what the speaker will actually say, not the cleverest version of the outline. Beats that stand on their own story survive the stage. Beats that need a held-back payoff, a callback from 20 minutes earlier, or an exact running order usually do not. Name those as fragile so the speaker knows which beats can drift and which cannot.

Understate throughout. If a line would be embarrassing to read aloud to the audience, flatten it.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. Use it only to make a Feel or Hit more specific to a story already in the outline. If missing, do not interview.
2. Find the outline. If they pointed at a file or folder, use that. Prefer `*-outline.md` or `outline.md`. If they pasted it, write it to disk next to where the storyboard will go (slug the title, or `talk-outline.md`). If more than one matches, ask which. If there is none, stop — see Refuse.
3. Write the storyboard next to the outline: `foo-outline.md` → `foo-storyboard.md`. If there is no anchor, ask where files should live (default: current directory) in the same message as any missing Inputs. Create the stub in that same turn. Sessions die. The file is the memory.
4. Read **Who this is for**, **What the audience gets**, **What I get**, **Spine** if present, and **Outline**. Scratch rounds are not the source. If Outline is empty, stop and say it is not ready to storyboard. Do not start outlining.
5. Write **The journey**: one plain paragraph. What the named person believes walking in (from Who this is for), what they feel walking out (from What the audience gets), and the change this talk is for.
6. Cut the outline into **beats**. A beat is a change in feeling, not an outline heading. Merge blocks that feel the same; two "take notes" beats in a row are one beat. A 20–45 minute talk is usually five to eight beats. Do not force a three-act shape.
7. Fill **Beats** (shape below).
8. Write **Leave them**: one feeling and one idea, matching What the audience gets.
9. Write **Can we lock this outline** (rule below).
10. Write **Gaps**: what the outline did not give you, and what you refused to invent.
11. Run **Lint** on the file. Fix what it finds.
12. Set `status: ready` and `resume: done`. In chat: path, the journey in two sentences, beat names in order with fragile ones marked, and the lock line. Do not paste the file. Do not start an outline edit, slides, or a speech.

If they want a revision, change the storyboard, not the outline, unless they ask. One revision, then lock and leave leftover mush in Gaps. The next real input is a rehearsal, not another chat pass.

## Beats

Each beat:

- **Place** — the outline block it sits on, so a later session can find it.
- **Energy** — the room, plainly: attentive, relaxed, a laugh, quiet, taking notes.
- **Feel** — what one person in the seat would mutter. One short, flat sentence, under about 15 words.
- **Hit** — the one thing this beat must land. One sentence.
- **Stands alone** — `yes`, or `fragile: <what it depends on>` when it needs an earlier setup held back, a callback more than one block away, or a contrast with a specific neighboring beat. A beat with no story or proof of its own in the outline is fragile too.

If a beat has no outline block under it, it is invented: cut it or move it to Gaps.

## Can we lock this outline

`yes` or `not yet`, then one sentence.

Yes only when the journey serves the named person, the takeaway is earned by a beat they will feel, the presenter ask sits on the close without a new feeling appearing from nowhere, **and** the Leave-them beat still lands if every fragile beat is cut or reordered. If the takeaway depends on a fragile beat, the answer is `not yet`: name the dependency and suggest the self-contained version in one sentence. Do not rewrite the outline.

## Lint

Before `ready`, read the file once and fix:

- Cinematic or hype words in Energy or Feel: "the floor drops," "the room exhales," "peak," "electric," "goosebumps," "high energy," "engaging," "inspiring."
- Feel lines over about 15 words, staged monologues, or em-dash reveals.
- Two neighboring beats with the same Energy. Merge them.
- Outline text pasted into beats. Place points at the block; do not quote it back.
- More than eight beats for a talk under 45 minutes.

## Working files

```markdown
---
status: in-progress
talk: "<title from the outline, or unknown>"
outline: "<path to the outline file>"
length: "<minutes from the outline, or unknown>"
resume: "<exact next step a cold session should do>"
---

# Storyboard — <title>

## The journey
## Beats
### 1. <beat name>
## Leave them
## Can we lock this outline
## Gaps
```

`status` is `in-progress` until a cold reader could run the feeling of the talk from the beats; then `ready`. Ready is about the storyboard, not about locking the outline. `resume` is the only progress pointer.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts. If they come back with a changed outline, read both and revise the storyboard. Do not restart.

The journey, Leave them, and Can we lock this outline are skimmer zones. No outline recap, no history of how you changed your mind.

## Inputs

Need an outline, not a topic. Ask only if missing and it would make the beats wrong, in one batch: path to the outline, where to write, which outline if several match.

Do not ask for brand stories, slide count, design tools, or a target number of beats. Do not fetch the topic on the web. Do not read other skills or the rest of the repo.

## Examples

`examples/` in this skill's folder, if present, shows a real storyboard checked against what was said on stage, including which beats were fragile. Read it only if you are unsure how to judge fragility or apply the lint.

## Refuse

Stop in a few sentences if there is no outline and they will not provide one, if the file is only throwaway scratch with no Outline, or if they want a different job: writing the outline from a blank page, slide design, a word-for-word speech, podcast guest prep, a film or product storyboard, or a fundraising pitch deck. Do not half-run those.
