---
name: talk-storyboard
description: "Maps how the audience should feel beat by beat through a talk outline, so the speaker can decide whether that outline is the one to keep. Starts from a locked outline file (`*-outline.md`) that names the audience, the Monday takeaway, and the talk blocks. Use when the user says storyboard this talk, map the emotional journey, how should the audience feel throughout, turn this outline into a storyboard, what beats should we hit, or 'is this the outline we want'. Do NOT load for writing the outline from scratch, slide design, a full speech, podcast guest prep, film or product storyboards, or a fundraising pitch deck."
---

# Talk storyboard

Lock the feeling of the talk before you lock the outline. The walk-away file is a storyboard of the energy and emotion the audience should move through. If that journey does not earn the Monday takeaway, the outline is not the one yet. Chat is a short read, not the file.

The talk is the job. The recording is the asset. The feeling in the room is the feeling in the transcript. Storyboard for the person in the seat, then check that the sentence you want quoted later still sits on a beat they will feel.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it. Use it only to make a Feel or Hit more specific to a story already in the outline. Do not add a story the outline does not use. If the file is missing, do not interview.
2. Find the outline. If they pointed at a file or folder, use that. Prefer `*-outline.md` or `outline.md`. If they pasted the outline, write it to disk in the directory they named (default: current directory) so the source is not only in chat: slug the talk title (`AI search in 2026` → `ai-search-in-2026-outline.md`), or `talk-outline.md` if there is no title. If more than one outline matches, ask which one. If there is no outline and they will not provide one, stop — see Refuse.
3. If they already pointed at an outline, write the storyboard next to it. If not, ask where files should live (default: the directory that holds the outline, or the current directory) in the same message as any missing Inputs. Do not ask the directory first and the outline second.
4. Write the storyboard stub in the same turn as any missing-input questions, even if the talk has no title yet. Do not wait for the outline to create the file. Sessions die. The file is the memory. Name it from the outline file: `foo-outline.md` → `foo-storyboard.md`. If the source is `outline.md` or a paste, slug the talk title (`AI search in 2026` → `ai-search-in-2026-storyboard.md`). If there is no title yet, use `talk-storyboard.md`. Do not fill Beats until an outline is on disk. If they ask for the storyboard only in chat, write the file anyway and keep chat short.
5. Read **Who this is for**, **What the audience gets**, **What I get**, and **Outline** from the source. Those headings are the usual shape. If the file uses different names, use the closest equivalents. Scratch rounds are not the source. If **Outline** is empty and they have not said which points to keep, stop and say the outline is not ready to storyboard. Do not invent blocks. Do not start outlining.
6. Write **The journey** before **Beats**. One paragraph: what the named audience believes or feels walking in, what they should feel walking out, and the change this talk is for. Take walking-in from Who this is for. Take walking-out from What the audience gets. If either box is mush, ask, then keep writing. Do not invent an audience or a Monday action.
7. Cut the outline into **beats**. A beat is a change in energy or emotion, not an outline heading. If two blocks feel the same, they are one beat. Do not force a three-act shape. Do not map every heading to its own beat. A twenty-minute talk is often five to eight beats. Honor `length` from the outline header when it is set. If length is unknown, do not invent a runtime; note it in Gaps and keep the beat count honest.
8. Fill **Energy map** as a numbered list: beat name, energy, feel. Someone late to the file should understand the whole talk from this list.
9. Fill **Beats**. For each beat use this shape:

   - **Place** — the outline block this sits on (heading or short paraphrase), so a later session can find it
   - **Energy** — the room, in words a speaker could direct to. Quiet lean-in, rising unease, laugh-release, peak, still. Not "high energy" and not "engaging"
   - **Feel** — the audience's emotion in their mouth ("that's me", "wait, we're the problem", "I can try this Monday"). Not "inspiring"
   - **Hit** — the one thing this beat must land. One sentence
   - **From the outline** — quote or tight paraphrase of the point or proof this beat uses. If you cannot point at the outline, the beat is invented: cut it or move it to Gaps

10. Write **Leave them**. One feeling and one idea they walk out holding. It must match What the audience gets. If the last beat does not earn that takeaway, say so here and in **Can we lock this outline**.
11. Write **Can we lock this outline**. `yes` or `not yet`, then one sentence. Yes only when the journey serves the named person, the Monday takeaway is earned by a beat they will feel, and the presenter ask can sit on the close without a new feeling appearing out of nowhere. Not yet when a box is mush, a load-bearing block has no feeling change, or the takeaway is only stated, not felt. Do not rewrite the outline. Name the mismatch.
12. Write **Gaps**. What the outline did not give you, and what you refused to invent.
13. Set `status: ready` and `resume: done` when a cold reader could run the feeling of the talk from the file. Ready is about the storyboard, not about locking the outline. If lock is `not yet`, the storyboard can still be ready.
14. In chat: the path, the journey in a few sentences, the beat names in order, and the lock line. Do not paste the file. If lock is `not yet`, say what the outline would need to change. Do not start that edit, slides, or a speech.

If they want a revision, change the storyboard, not the outline, unless they ask. Three passes is the cap: your first storyboard, then at most two revisions. If they accept earlier, stop. After the third pass, lock the storyboard anyway and leave leftover mush in Gaps.

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
## Energy map
## Beats
## Leave them
## Can we lock this outline
## Gaps
```

`status` is `in-progress` until a cold reader could run the feeling of the talk from the beats; then `ready`. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts (talk name, outline path, length, file path, journey already on disk, beats already written, lock verdict already made). If they come back with a changed outline, read both files and revise the storyboard. Do not restart.

The journey, Energy map, Leave them, and Can we lock this outline are skimmer zones. No outline recap, no "I considered…", no history of how you changed your mind. That belongs in Gaps or nowhere.

## Inputs

Need an outline of the talk, not a topic. The usual file is `<talk-slug>-outline.md` next to where they want the storyboard. A stranger can write the same shape by hand. The headings that matter:

- **Who this is for** — one person, their situation, what they already believe
- **What the audience gets** — what they can do or decide on a specific next day
- **What I get** — the presenter win, if present
- **Outline** — named or timed blocks, each with a point and a proof (a story or number)

From the user's message (ask only if missing and it would make the beats wrong), in one batch:

1. Path to the outline, if they did not point at one, did not paste one, and `*-outline.md` / `outline.md` is not in front of you.
2. Where to write, if no outline file already anchors the directory (default: current directory).
3. Which outline, if more than one matches.

Do not ask for brand stories, slide count, design tools, or a target number of beats. Do not fetch the topic on the web. Do not read other skills or the rest of the repo.

If brand context is missing, skip it. The outline is enough.

## Refuse

Stop in a few sentences if there is no outline and they will not provide one, if the file is only throwaway scratch with no Outline and they have not said which points to keep, or if they want a different job: writing the outline from a blank page, slide design or visual layout, a word-for-word speech, podcast guest prep, a film or product storyboard, or a fundraising pitch deck. Do not half-run those.
