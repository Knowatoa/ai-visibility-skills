---
name: channel-funnel-map
description: "Turns real buyer stories into a map of the buyer's journey and a recommended set of CRM stages to track. The user describes actual people at different points (met at a conference then came back organically, cold call that went quiet, trial that converted) and gets every intake channel, every path to a purchase, where buyers cross from one path into another, and the stages, fields, and signals to track. Built for founders and marketers who know marketing funnels but have not set up a sales pipeline. Use when the user says 'what stages should my CRM have', 'map my funnel', 'here are some of our buyers, what should we track', 'how do leads get to a purchase', or 'I want to see which channels work'. Do NOT load for configuring a specific CRM's settings, writing email sequences, picking channels when they have none today, or ad campaign reporting."
---

# Channel funnel map

Start from real buyers, not theory. The user describes actual people and where each one is today. You turn those stories into a map of the buyer's journey and tell them which CRM stages to track. The user walks away with `<business-slug>-channel-map.md`: the buyer stories, every intake channel and path, where buyers cross from one path into another, the gaps, and the recommended stages.

The goal: capture the buyer's journey across every way the business touches a buyer, so the user can see which channels work and where to put more time and money. This is not attribution. No channel gets "credit". A buyer who did not buy after a cold call and later came back through an organic visit is a journey worth recording. A step nobody can observe cannot be tracked, so the map also surfaces those gaps.

The user knows marketing funnels (traffic, signups, email). They may not know sales pipeline terms. Define each of these in one sentence the first time you use it, then move on:

- **Intake channel:** where a relationship starts.
- **Path:** one sequence of steps from that start to an end.
- **Stage:** a step in a CRM pipeline that a deal sits in until something moves it.
- **Signal:** the thing you can see that proves a step happened.
- **Crossover:** a buyer leaves one path and later shows up in another, with or without a nudge from you.

## Do this job

1. **Look first.** In the directory they named (default: current), look for `channel-map.md` or `*-channel-map.md`. If one exists, read it, do what `resume` says, and do not re-ask anything the file already answers. New stories get added to that file and the map and stages rebuilt. Never write a fresh stub over an existing map.
2. **Brand context.** Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If either exists, take the business line from it and do not ask. If both are missing, do not interview.
3. **Ask for stories, one batch.** In a single message ask only for what steps 1 and 2 did not already answer: where the file should live (default: current directory), what the business sells and to whom (one line), and 3 to 6 real buyers or prospects at different points. For each: how they first came across you, what happened after, and where they are right now (bought, in a trial, went quiet, came back). First names or initials are enough. No emails or phone numbers. Give one example story so they know the shape: "Dana: met at a conference, we never followed up, two months later she found us through search, started a trial, still in it."
4. **Write the stub in the same turn as those questions,** before any answers come back. Headings from **Working files**, `status: in-progress`, and a `resume` line saying you are waiting on the stories. Sessions die. The file is the memory. Name it by slugging the business line (`Scheduling software for dental practices` -> `dental-scheduling-channel-map.md`); if you do not have that line yet, write `channel-map.md` and rename once you do. As each story arrives, put it in the file in the user's own words.
5. **Turn each story into a journey.** A journey is the ordered list of touches: channel, what happened, who acted (buyer or you), and the signal. If the story does not say how the user would know a step happened, write `unknown`. Do not invent a signal.
6. **Build the map from the journeys.** Group touches by the channel where each relationship started. Each distinct sequence is a path. Each path ends at purchase, trial, demo, drops off, or joins another path. Any journey that moves between channels is a crossover. Record where it left, where it joined, the cause if known, and the signal that ties both touches to the same person. That signal is usually missing. Common ones: the same email address, a "how did you hear about us" field, a channel-specific link or offer code.
7. **Fill gaps with one batch of questions.** Only ask what the stories left open: a channel they mentioned with no story, a path with no end, a signal that is unknown. Ask about a missing channel with a prompt like: "Tell me about one person who came in through cold calls." If they cannot answer, list it under Gaps and move on.
8. **Recommend stages.** See below.
9. **Place every buyer.** Put each story's buyer in the stage they are in today. If a buyer does not fit any stage, the stages are wrong. Fix them before you finish.
10. **Write the handoff** and set `status: ready`.

Accept rough answers and tidy them yourself. Do not lecture on funnel theory.

## Recommending stages

Derive stages from the journeys, not from a template.

- **Keep stages few.** 4 to 7 once you have real journeys. A step becomes a stage only if a buyer can sit in it for a while and the user would act differently depending on it. "Trial started" is a stage. "Opened an email" is not.
- **Every stage needs an entry signal.** State what must be true for a buyer to enter it. If the signal is unknown, say so and name the cheapest way to create one.
- **Everything else is a field or tag.** Always recommend these:
  - First-touch channel.
  - Touch timeline on the contact: channel, date, what happened, outcome. Include touches after a lost deal, so a later return shows up on the same person.
- **Lost is not the end.** A buyer marked lost who comes back re-enters the pipeline on the same contact, with the new touch added to the timeline. Do not create a new person.
- **Name what each stage lets them compare.** Example: "Trial started, by first-touch channel, shows which channels bring buyers who try the product."
- **Stages are where a deal sits, not a track.** Order them so the list reads in sequence, then expect buyers to skip. Someone who buys with no demo and no trial is normal, not a modelling error. If two shapes run through one pipeline — self-serve trial and sales-led — say that plainly instead of forcing one ladder.
- **Never pad.** If the journeys only support two or three stages, ship two or three and say why in Gaps. A stage no story evidenced is a template, and a template is what this skill exists to avoid.

One usable story is not enough for a pipeline. Say so, keep `status:
in-progress`, and name which kinds of buyer are missing: one who bought,
one mid-conversation, one who went quiet. Tell them the map gets rebuilt
when those arrive. Say it once and move on. Do not fill the
hole with plausible stages.

## Working files

Write `<business-slug>-channel-map.md` in the chosen directory. If it already exists, read it, follow `resume`, and do not re-ask settled facts. New stories can be added later. Rebuild the map and stages when they are.

```markdown
---
status: in-progress
business: "<what they sell, to whom>"
resume: "<exact next step a cold session should do>"
---

# Channel map: <business>

## Buyer stories
### <Name>
<story in their words>
Journey: <touch> -> <touch> -> <where they are now>

## Channels
### <Channel>
| Path | Step | What happens | Who acts | Signal |
| ---- | ---- | ------------ | -------- | ------ |

## Crossovers
| Buyer | From | Joins | Cause | Same-person signal |
| ----- | ---- | ----- | ----- | ------------------ |

## Recommended stages
| Stage | Entry signal | What it lets you compare | Buyers here now |
| ----- | ------------ | ------------------------ | --------------- |

Fields to keep on every contact:
- First-touch channel
- Touch timeline (channel, date, what happened, outcome)

## Gaps
- <unknown signals, open path ends, untraceable crossovers, channels with no story>

## CRM handoff
<copy-ready block, below>
```

The handoff block, for the user to paste into their AI or give to whoever sets up the CRM:

```
CRM SETUP REQUEST
Business: <one line>

Pipeline stages, in order:
  1. <stage>. Enter when: <signal>
  ...

Contact fields:
  - First-touch channel: <list of channels>
  - Touch timeline: channel, date, what happened, outcome

Rules:
  - Stages are where a deal sits, not a sequence every buyer must complete.
    Buyers skip stages. Do not gate one stage behind another.
  - A lost buyer who returns re-enters on the same contact.
  - Log every touch, including after a lost deal.
  - This is for seeing buyer journeys, not assigning credit.

Gaps to fix: <list>

Set this up in <my CRM>. Tell me what to create and in what order.
```

`status` stays `in-progress` until every story is placed in a stage and the handoff is written. Then `ready`.

In chat: the path, the recommended stages as a short list, how many buyers each holds now, and the gap count. Do not paste the whole file.

## Example

Stories:
- **Dana:** met at a conference, no follow-up. Two months later found the site through search, started a trial. Still in trial.
- **Luis:** cold call, took a demo, went quiet. Came back through an organic visit three months later with the same email and bought.
- **Priya:** found a blog post, subscribed for a free resource, got the email sequence, started a trial, bought.

Stages this produces:

| Stage | Entry signal | What it lets you compare | Buyers here now |
| ----- | ------------ | ------------------------ | --------------- |
| Conversation | Logged conversation or call | Which channels start real conversations | |
| Demo | Demo held | Which channels are worth sales time | |
| Trial | Trial account created | Which channels bring buyers who try the product | Dana |
| Customer | First paid invoice | Which channels bring buyers who pay | Luis, Priya |
| Lost | Marked lost after no reply for 30 days | Where each channel stalls | |

Crossovers: Dana (conference to organic, signal unknown), Luis (cold call to organic, same email). Gap: nothing ties a conference conversation to a later site visit. Cheapest fix: a conference-only link or offer code.

## Refuse

Stop in a few sentences if the user wants a different job: configuring a named CRM's settings or automations, writing the email sequence itself, choosing new channels when they have none today, or analyzing ad spend. The handoff is where CRM setup goes.
