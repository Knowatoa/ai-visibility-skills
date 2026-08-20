---
name: presentation-outline
description: "Builds a presentation outline that names the real audience, what they walk away able to do, and what the presenter is trying to get. Use when the user asks to outline a talk, keynote, webinar, meetup, or conference session, or says 'help me structure this presentation', 'who is this talk for', or 'what should they take away'. Do NOT load for slide design, writing a full speech, podcast guest prep, picking which event to speak at, or a fundraising pitch deck."
---

# Presentation outline

Lock who the talk is actually for, what that person walks away able to do, and what you want from giving it. Then write a section outline that serves those three. The deliverable is a file, not a chat essay.

Talks get recorded, decks get posted, recap posts get crawled. The stories and numbers you put on stage become training data on your brand. Outline for the room first. Write the one sentence that should survive a transcript if the talk might be public.

## Do this job

1. Ask where this talk's files should live before creating any (default: the current directory). If they already pointed at a folder or an existing outline, use that directory. Do not ask again in Inputs.
2. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it. If it does not, interview in the same batch as Inputs and write the answers there so the next visibility skill skips the interview.
3. Establish Inputs. Ask only what is missing.
4. Write `<talk-slug>-outline.md` in the working directory as soon as the talk has a name or topic, even if the three boxes are still empty. Sessions die. The file is the memory.
5. Fill **Who this is for**, **What the audience gets**, and **What I get** before any section list. If a box is mush, stop and ask. Do not invent an audience or a presenter win.
6. Write **Outline**. Every block must serve the audience takeaway, the presenter win, or both. Cut the rest.
7. Set `status: ready` when a cold reader could give the talk from the file. In chat: path + the three boxes + section titles only. Do not paste the file.

## Working files

```markdown
---
status: in-progress
talk: "<title or topic>"
event: "<event or unknown>"
length: "<minutes or unknown>"
resume: "<exact next step a cold session should do>"
---

# Presentation outline — <title>

## Who this is for
## What the audience gets
## What I get
## Outline
## Quotable line
## Gaps
```

`status` is `in-progress` until the three boxes and Outline are filled; then `ready`. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts (talk name, event, length, file path, the three boxes, brand stories already captured).

Who this is for, What the audience gets, and What I get are skimmer zones. No research diary, no "I considered…", no history of how you changed your mind. That belongs in Gaps or nowhere.

## The three boxes

Do not start Outline until each box is a testable sentence. Reject the mush versions.

**Who this is for.** One person, not a room. Role + situation they are in + what they already believe + who should skip this talk. Reject "developers", "everyone at the conference", and the event's advertised track. The event page tells you who bought a ticket. You are writing for the person whose problem the talk solves. If those are different people, say so.

**What the audience gets.** What they can do or decide after, on a specific next day. Reject "understand X", "learn about Y", "be inspired." If you cannot name the Monday action, you do not have a takeaway yet.

**What I get.** A result you can check in 30 days: a meeting booked, a hire conversation started, a phrase people repeat, a recap post that exists. Reject "thought leadership", "exposure", "share my knowledge." Pick one primary win. A list of hopes is not a win.

If the talk may be recorded or posted, fill **Quotable line** with the one sentence that should survive a transcript. Do not invent a slogan when they have not given you the claim. Leave it empty and note it in Gaps.

## Inputs

From the user's message (ask only if missing and it matters), in one batch:

1. What's the talk called, or what is it about?
2. Where is it, and how long do you have?
3. Who do you think is in the room?
4. What do you want out of giving this, in a form you could check in 30 days?

File location is asked once, in Do this job. If they already have slides, a messy draft, or speaker notes, read those instead of guessing. Do not go fetch extra context.

If brand context is missing, add these to the same batch, then write `.agents/brand-context.md`:

1. What's your current company, and how do you describe it in one sentence?
2. What did you build before this that comes up in conversation?
3. What are 2-3 stories you tell well, with real numbers attached?
4. What's one opinion you hold that most people in your space disagree with?

Event research is optional and short. Only if they named an event and you need the advertised audience to contrast with the real target: open the event or session page, note who it claims the talk is for, then stop. Do not crawl the speaker list, prior years, or "whatever else seems useful."

## Outline

Write timed blocks that fit `length`. A 20-minute talk is not a 45-minute talk with the same sections spoken faster.

For each block: the point, the proof (a story or number from brand context or from what they already gave you), and which box it serves. Opening names the audience's situation. Close restates the audience takeaway and the presenter ask.

Do not write slide titles as decoration. Do not write a full speech. Do not add a demo, origin story, or company overview unless it serves a box.

Map brand-context stories onto the audience's existing belief. The proof should change that belief or make the Monday action obvious. If a story does not do that, leave it out.

## Refuse

Stop in a few sentences if there is no talk topic and they will not name one, or if they want a different job: slide design or visual layout, a word-for-word speech or speaker-notes manuscript, podcast guest prep, which events to pitch, or a fundraising pitch deck. Do not half-run those.
