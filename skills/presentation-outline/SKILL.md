---
name: presentation-outline
description: "Builds a presentation outline that names the real audience, what they walk away able to do, and what the presenter is trying to get. Starts from an abstract and throwaway bullet rounds. Use when the user asks to outline a talk, keynote, webinar, meetup, or conference session, or says 'help me structure this presentation', 'I have some rough bullets', 'here's my abstract', 'who is this talk for', or 'what should they take away'. Do NOT load for slide design, writing a full speech, podcast guest prep, picking which event to speak at, or a fundraising pitch deck."
---

# Presentation outline

Lock who the talk is actually for, what that person walks away able to do, and what you want from giving it. An outline is usually weeks of throwing lists away, not one sitting. Capture the abstract and any bullets they already have, dump about ten more, and leave them. Whatever still sounds true after a few of those rounds is the outline. The deliverable is a file, not a chat essay.

Talks get recorded, decks get posted, recap posts get crawled. The stories and numbers you put on stage become training data on your brand. Outline for the room first. Write the one sentence that should survive a transcript if the talk might be public.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it.
2. If they already pointed at a folder or an existing outline, use that directory. If not, ask where files should live (default: the current directory) in the same message as any missing Inputs or brand questions. Do not ask the directory first and the talk second.
3. Write `<talk-slug>-outline.md` in that directory as soon as the talk has a name or topic, in the same turn as any missing-input questions. Do not wait for answers to create the stub. Sessions die. The file is the memory.
4. Fill **Who this is for**, **What the audience gets**, and **What I get** before **Outline**. Scratch can start while a box is still mush. If a box is mush, ask. Do not invent an audience or a presenter win.
5. Put their abstract in **Abstract**. Put their existing bullets in **Scratch** as Round 1. If they have none, write one ~10-bullet dump this sitting from the abstract, the boxes you can fill, and brand stories. Do not copy that list into Outline.
6. Stop after one scratch round unless they ask for another now. Set `resume` to the next sitting: ask what stuck, write a new ~10 that does not repeat discarded rounds. The forgetting is the filter. Same-day extra rounds do not test it.
7. Write **Outline** only from **What survived**, or this sitting if they name the keepers, ask for the locked outline, or the talk is about a week away. Every block must serve the audience takeaway, the presenter win, or both. Cut the rest.
8. Set `status: ready` when a cold reader could give the talk from the file. In chat while scratching: path + the three boxes + which round is in the file + that the list is disposable. Come back when they have forgotten it. Do not paste the bullets. Once Outline is locked: path + the three boxes + section titles only. Do not paste the file.

## Working files

```markdown
---
status: in-progress
talk: "<title or topic>"
event: "<event or unknown>"
when: "<date or unknown>"
length: "<minutes or unknown>"
resume: "<exact next step a cold session should do>"
---

# Presentation outline — <title>

## Abstract
## Who this is for
## What the audience gets
## What I get
## Scratch
### Round 1, <date>
### What survived
## Outline
## Quotable line
## Gaps
```

`status` is `in-progress` until the three boxes and Outline are filled from what survived; then `ready`. A first dump in Scratch is not enough. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts (talk name, event, when, length, file path, the three boxes, abstract, scratch rounds already on disk, brand stories already captured). If an older file has no Abstract or Scratch heading, add them and keep going. Do not restart.

Who this is for, What the audience gets, and What I get are skimmer zones. No research diary, no "I considered…", no history of how you changed your mind. Scratch holds the thrown-away rounds. Everything else like that belongs in Gaps or nowhere.

## The three boxes

Do not start Outline until each box is a testable sentence. Reject the mush versions. Scratch does not need the boxes to be done.

**Who this is for.** One person, not a room. Role + situation they are in + what they already believe + who should skip this talk. Reject "developers", "everyone at the conference", and the event's advertised track. The event page tells you who bought a ticket. You are writing for the person whose problem the talk solves. If those are different people, say so.

**What the audience gets.** What they can do or decide after, on a specific next day. Reject "understand X", "learn about Y", "be inspired." If you cannot name the Monday action, you do not have a takeaway yet.

**What I get.** A result you can check in 30 days: a meeting booked, a hire conversation started, a phrase people repeat, a recap post that exists. Reject "thought leadership", "exposure", "share my knowledge." Pick one primary win. A list of hopes is not a win.

If the talk may be recorded or posted, fill **Quotable line** with the one sentence that should survive a transcript. Do not invent a slogan when they have not given you the claim. Leave it empty and note it in Gaps.

## Inputs

From the user's message (ask only if missing and it matters), in one batch:

1. What's the talk called, or what is it about?
2. Where is it, when is it, and how long do you have?
3. Who do you think is in the room?
4. What do you want out of giving this, in a form you could check in 30 days?
5. Paste any abstract or CFP blurb, and any rough bullets you already have, including lists you already threw away.

File location is asked once, in the same batch as these questions when the path is unset. If they already have an abstract, bullets, slides, a messy draft, or speaker notes, read those instead of guessing. Do not go fetch extra context.

If brand context is missing, add these to that same batch, then write `.agents/brand-context.md`:

1. What's your current company, and how do you describe it in one sentence?
2. What did you build before this that comes up in conversation?
3. What are 2-3 stories you tell well, with real numbers attached?
4. What's one opinion you hold that most people in your space disagree with?

Event research is optional and short. Only if they named an event and you need the advertised audience to contrast with the real target: open the event or session page, note who it claims the talk is for, then stop. Do not crawl the speaker list, prior years, or "whatever else seems useful."

## Scratch

This is how the talk is found. About ten short bullets per sitting. Not slide titles, not a speech, not timed sections.

Paste their abstract into **Abstract**. Do not rewrite it into a better CFP. If they have no abstract, leave the section empty and note it in Gaps. Do not invent one.

Their bullets, if any, are Round 1. Label whose they are. They are still disposable unless they say these are the ones that stuck.

If they have no bullets and at least one box is a testable sentence, write ~10 candidate points from the abstract, that box, and brand stories. If they have no bullets and every box is mush, do not invent a dump. Ask the boxes.

After you write a round, leave it. Do not promote it. Do not generate Round 2 in the same sitting unless they ask. `resume` must say the next sitting asks what is still in their head, then writes a new ~10 that does not repeat discarded bullets.

On return, read Scratch first. Ask what stuck. That is the only question if the rest is settled. Put keepers under **What survived**. Then another dump, or Outline if they are ready to lock.

Two or more rounds on disk and they have not named keepers: ask once what is still in their head. Do not drip "another round?" after every list.

## Outline

Write timed blocks that fit `length`. A 20-minute talk is not a 45-minute talk with the same sections spoken faster. If length is still unknown, write untimed blocks and note it in Gaps. Do not invent a runtime.

Source blocks from **What survived**, not from the latest scratch dump. If they asked to lock now and What survived is empty, have them mark keepers first. Do not promote a list they have not stood behind.

For each block: the point, the proof (a story or number from brand context or from what they already gave you), and which box it serves. Opening names the audience's situation. Close restates the audience takeaway and the presenter ask.

Do not write slide titles as decoration. Do not write a full speech. Do not add a demo, origin story, or company overview unless it serves a box.

Map brand-context stories onto the audience's existing belief. The proof should change that belief or make the Monday action obvious. If a story does not do that, leave it out.

## Refuse

Stop in a few sentences if there is no talk topic and they will not name one, or if they want a different job: slide design or visual layout, a word-for-word speech or speaker-notes manuscript, podcast guest prep, which events to pitch, or a fundraising pitch deck. Do not half-run those.
