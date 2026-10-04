---
name: talk-outline
description: "Builds a talk outline that names the real audience, what they walk away able to do, and what the presenter is trying to get, based on a outline (also referred to as spine,of at most three points the speaker can say without slides. Starts from an abstract, throwaway bullet rounds, or a rough spoken ramble, or wraps the outline in one sitting when the talk is about a week away. Use when the user asks to outline a talk, keynote, webinar, meetup, or conference session, or says 'help me structure this presentation', 'I have some rough bullets', 'here's my abstract', 'here's me talking it through', 'the talk is next week', 'wrap up this outline', 'who is this talk for', or 'what should they take away'. Do NOT load for slide design, writing a full speech, podcast guest prep, picking which event to speak at, a fundraising pitch deck, or reworking an outline against a rehearsal transcript."
---

# Talk outline

Lock who the talk is for, what that person walks away able to do, and what you want from giving it. Then hang the talk on a outline the speaker can carry without notes. The deliverable is a file, not a chat essay.

The outline is a starting point, not a contract. The spoken talk will drift from it on the first rehearsal, and that is healthy. Write an outline that is cheap to drift from: few named parts, lived stories, short blocks. Do not spend the sitting perfecting structure that a run-through will rewrite.

Giving the talk is the job. If you record it and publish it, you leave with an asset that can be clipped, recapped, posted, and indexed. Outline for the room first. Write the one sentence that should survive a transcript if the talk might be public.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it.
2. If they already pointed at a folder or an existing outline, use that directory. If not, ask where files should live (default: the current directory) in the same message as any missing Inputs.
3. Write `<talk-slug>-outline.md` as soon as the talk has a name or topic, in the same turn as any missing-input questions. Sessions die. The file is the memory.
4. Fill **Who this is for**, **What the audience gets**, and **What I get**. If a box is mush, ask. Do not invent an audience or a presenter win.
5. Put their abstract in **Abstract**. Put their bullets or ramble in **Scratch** as Round 1.
6. Set `pace`. Default `scratch`. Use `wrap-up` when `when` is about a week or less, they asked to finish now, or they already know the talk. Do not ask which pace.
7. Find the **Outline** (see below) before writing blocks.
8. Run **Scratch** or **Wrap-up**.
9. Set `status: ready` when a cold reader could give the talk from the file. In chat: path, the three boxes, the spine, section titles. Do not paste the file. When ready, stop. Do not start slides, a speech, or another skill.

## Working files

```markdown
---
status: in-progress
talk: "<title or topic>"
event: "<event or unknown>"
when: "<date or unknown>"
length: "<minutes or unknown>"
pace: scratch
resume: "<exact next step a cold session should do>"
---

# Talk outline — <title>

## Abstract
## Who this is for
## What the audience gets
## What I get
## Spine
## Scratch
### Round 1, <date>
### What survived
## Outline
## Quotable line
## Gaps
```

`status` is `in-progress` until the boxes, Spine, and Outline are filled; then `ready`. `resume` is the only progress pointer.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts. If an older file lacks a section, add it and keep going. Do not restart.

Who this is for, What the audience gets, What I get, and Spine are skimmer zones. No research diary, no "I considered…". That belongs in Gaps or nowhere.

## The three boxes

Each box is a testable sentence. Reject the mush versions.

**Who this is for.** One person in **the next room the speaker will stand in**. Role + situation + what they already believe + who should skip this talk. Reject "developers" and the event's advertised track. If a later room is the real target, note it in Gaps and outline for that room in its own file later. Do not interleave variants for two rooms in one outline; speakers talk to the faces in front of them.

**What the audience gets.** One to three lines the speaker would put on a "what you'll take away" slide, in the speaker's own words. Each names something they can do or decide on a specific next day. Reject "understand X", "learn about Y", "be inspired." Read the lines aloud as the speaker. If they would not say it that way, rewrite it until they would.

**What I get.** One result checkable in 30 days: a meeting booked, a phrase repeated, a recap post that exists. Reject "thought leadership" and "exposure." One primary win.

If the talk may be recorded, fill **Quotable line** with the one sentence that should survive a transcript. Do not invent a slogan when they have not given you the claim; leave it empty and note it in Gaps.

## Spine

Before blocks, find the speaker's organizing word: the noun they keep reaching for when they explain the topic (jobs, habits, mistakes, rooms). Ask once: "When you explain this to a friend, what word do you keep coming back to?" If they gave you a ramble, take the most repeated noun from it.

Then write the spine: **that word plus at most three moves**, each a short verb phrase. Example: *jobs — own the most important one; hand AI everything else; let AI work off the clock.* The core of the talk hangs on these moves. A taxonomy of four pairs or eight named patterns is too many to carry on stage; it will collapse into three moves in the first rehearsal anyway. Extra ideas become examples under a move or go to Scratch.

## Inputs

From the user's message (ask only if missing and it matters), in one batch:

1. What's the talk called, or what is it about?
2. Where is it, when is it, and how long do you have?
3. Who is in the next room you'll give it to?
4. What do you want out of giving this, in a form you could check in 30 days?
5. Any abstract, rough bullets, or a transcript of you talking it through (a phone voice memo is fine).

A spoken ramble is the fastest source. If they have none and the talk is soon, offer once: "Talk it through for five minutes into your phone and paste the transcript. I'll outline from that." Do not insist.

If brand context is missing, add these to that same batch, then write `.agents/brand-context.md`:

1. What's your current company, and how do you describe it in one sentence?
2. What did you build before this that comes up in conversation?
3. What are 2-3 stories you tell well, with real numbers attached?
4. What's one opinion you hold that most people in your space disagree with?

Do not research the event, the speaker list, or the topic.

## Scratch

Default pace. About ten short bullets per sitting. Not slide titles, not a speech.

Their bullets or ramble are Round 1. If they have none and at least one box is a testable sentence, write ~10 candidate points from the abstract, the boxes, and brand stories. If every box is mush, ask the boxes instead.

After you write a round, stop. `resume` says the next sitting asks what is still in their head, then either writes a new ~10 that does not repeat discarded bullets or locks. The forgetting is the filter.

On return, ask what stuck. Put keepers under **What survived**. If they are ready, write Spine and Outline from What survived. Two rounds is usually enough; if they have two rounds and no keepers, ask once what is still in their head, then lock from that.

## Wrap-up

Same sitting. Write Spine and Outline as one pass from their keepers, ramble, abstract, boxes, and brand stories. Chat the spine and block titles. Take one round of reaction, revise once, then lock. Leftover mush goes in Gaps.

If the reaction is "this doesn't feel right" without specifics, do not trade more passes in chat. Ask them to talk the talk for five minutes and paste the transcript, and outline from that. Arguing over an outline in chat is slower than one rough run-through.

When `status` is `ready`, stop. The first rehearsal transcript is the next revision, not another chat pass.

## Outline

Timed blocks that fit `length`. Plan for about **85% of the slot**; first-hand stories run long, and the core block grows most. Name the Q&A buffer. If length is unknown, write untimed blocks and note it in Gaps.

Always include:

- **Open** (about a minute): who it's for, the takeaway lines, the shape of the talk. Speakers reach for an agenda slide anyway; plan it.
- **Core**: one block per spine move.
- **Close**: restate the takeaway lines, the presenter ask, and answer the title. A talk titled as a question ends by answering it.

Each block, about 80 words or less:

- **Point** — one sentence.
- **Proof** — a story or number. Tag it `lived` (the speaker did it or saw it) or `secondhand` (a tweet, a video, an article). Lived proof survives the stage; secondhand proof gets dropped or garbled. Use secondhand only when it is sourced and the point needs it, and put the source in Gaps. Leave room in the core for "this week's story": the speaker will bring a fresher one than you can.
- **Serves** — which box.

Resolve tension locally. If a block raises a fear, question, or setup, pay it off in the same block or the next one. Allow at most one long-range callback, and the title is the natural one. Plans that spread payoffs across the whole talk do not survive delivery.

State points and proof flatly. What the room feels belongs to the storyboard. Do not write slide titles, a speech, or a company overview unless it serves a box. Map brand stories onto the audience's existing belief; if a story does not move that belief or make the Monday action obvious, leave it out.

## Examples

`examples/` in this skill's folder, if present, shows a real outline next to what was actually said on stage. Read it only if you are unsure what a spine, a lived proof, or a local payoff looks like. Everything you need to run the job is above.

## Refuse

Stop in a few sentences if there is no talk topic and they will not name one, or if they want a different job: slide design, a word-for-word speech, podcast guest prep, which events to pitch, a fundraising pitch deck, or reworking the outline against a rehearsal transcript (that is a pressure-test against the spoken talk, not an outline from scratch). Do not half-run those.
