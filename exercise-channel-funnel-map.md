---
skill: channel-funnel-map
path: skills/channel-funnel-map/SKILL.md
status: ready
resume: done
patched: 2026-09-27 (P1-P5 applied; scenarios 2 and 4 re-run)
---

# Exercise — channel-funnel-map

Quarantine: wielder used only `skills/channel-funnel-map/SKILL.md`.

## Scenarios
1. **Canonical** — Maya, founder of scheduling software for dental practices. Four real buyer stories at different points. Cooperative, gives detail when asked.
2. **Terse** — "map my funnel, we sell to gyms." One vague story, cannot produce more, pushes for the stage list anyway.
3. **Wrong job** — wants the wielder to configure HubSpot deal stages and write a five-email nurture sequence.
4. **Die-and-resume** — a half-built `*-channel-map.md` on disk (stories + channels, no stages). The user opens with two new buyer stories and never mentions the file.

## Scenario 1 — Canonical

```
USER: I want to figure out what stages my CRM should have. We sell scheduling
      software to dental practices.

WIELDER: Before I build anything — where should the file live? Default is the
      current directory.

      Two things I need from you:

      1. One line on what you sell and to whom. Sounds like "scheduling
         software for dental practices" — correct me if that's too narrow.
      2. Three to six real buyers or prospects, at different points. For each:
         how they first came across you, what happened after, and where they
         are right now (bought, in a trial, went quiet, came back). First names
         or initials are fine — no emails or phone numbers.

      Shape I'm after: "Dana: met at a conference, we never followed up, two
      months later she found us through search, started a trial, still in it."

      A couple of terms I'll be using: an **intake channel** is where a
      relationship starts. A **path** is one sequence of steps from that start
      to an end.

USER: current dir is fine. Yeah, scheduling + reminders for dental practices,
      usually the office manager buys. Four people:

      Ravi — office manager, 3 chairs. Found us through a comparison blog post,
      signed himself up for the trial, paid about three weeks later.

      Deb — we met at a trade show, took her card at the booth, honestly never
      followed up. Four months later she filled out the demo form on our site.
      We did the demo, she's negotiating now.

      Tom — cold email from us. He replied "send info." We sent it. Nothing
      since, that was two months ago.

      Sandra — Ravi told her about us. She called us directly and bought. Never
      took a trial.

WIELDER: Written to `dental-scheduling-channel-map.md`. Journeys as I read them:

      Ravi:   blog post -> trial signup -> paid
      Deb:    trade show booth -> [4-month gap] -> demo form -> demo held -> negotiating
      Tom:    cold email -> replied -> quiet
      Sandra: referral from Ravi -> inbound call -> paid

      Four intake channels: content/organic, trade show, cold email, referral.

      One **crossover** — a buyer who leaves one path and shows up in another:
      Deb started at the trade show and re-entered through your own site four
      months later. Nothing ties those two touches to the same person; her card
      never went anywhere a later form fill could match against. That's your
      most expensive gap, because it's the channel you pay a booth fee for.

      Three questions, all from holes in what you gave me:

      1. Tom — do you have a rule for when a non-reply becomes dead, or is he
         just sitting there?
      2. Sandra — is "Ravi told her" written down anywhere, or do you only know
         because she said it on the call?
      3. Do you know Ravi came from the comparison post, or is that a guess?

USER: 1. No rule, he's just sitting there. 2. Only because she said it.
      3. He mentioned it on a call. Not in any system.

WIELDER: Then two of your four first-touch channels are known only because
      someone happened to say them out loud. That's the finding, not a
      side note.

      Recommended stages — six, derived from your four journeys:

      | Stage | Entry signal | Buyers here now |
      | ----- | ------------ | --------------- |
      | Conversation | Logged call, reply, or booth conversation | Tom |
      | Demo | Demo held | |
      | Trial | Trial account created | |
      | Negotiation | Pricing or contract sent | Deb |
      | Customer | First paid invoice | Ravi, Sandra |
      | Lost | No reply for 30 days | |

      Every buyer places. But note what your own stories did to the ordering:
      Sandra went Conversation -> Customer with no demo and no trial, and Deb
      is in Negotiation having never had a trial. You have two shapes running
      through one pipeline — self-serve trial (Ravi) and sales-led (Deb,
      Sandra). Stages are where a deal sits, not a track it must complete.

      Fields on every contact: first-touch channel, plus a touch timeline
      (channel, date, what happened, outcome) that keeps logging after a lost
      deal — so when a Deb comes back four months later, the return lands on
      the same person instead of a new one.

      Gaps: 4. Nothing links a booth conversation to a later site visit; Ravi's
      and Sandra's first touch are hearsay; no lost rule, so Tom never ages out.
      Cheapest fixes: a booth-only short link or offer code, and a "how did you
      hear about us" field on the demo form.

      File has the stories, journeys, the channel tables, the crossover, the
      stage table, and a paste-ready CRM setup block. `status: ready`.
```

**Read:** the skill does the job. Every output is Maya's specifics — it
never explains what a funnel is, and the two terms it does define come
with one sentence each at first use, exactly as instructed. Intake was
one batch; the follow-up round was three questions, all traceable to
holes in her stories. Chat stayed a summary and pointed at the file.

One thing the file did not cover: Sandra and Deb both skip stages, and
the wielder had to invent the "stages are where a deal sits, not a track
it must complete" line to stay coherent. See Patches.

## Scenario 2 — Terse

```
USER: map my funnel. we sell to gyms.

WIELDER: Where should the file live? Default is the current directory.

      I need one line on what you sell to gyms, and three to six real buyers or
      prospects at different points — how each first came across you, what
      happened after, where they are now. First names or initials are enough.

      Shape: "Dana: met at a conference, we never followed up, two months later
      she found us through search, started a trial, still in it."

USER: here, whatever. mostly people just find us on instagram and DM us.
      that's basically it.

WIELDER: That's a channel, not a buyer. Give me one actual person who DM'd you:
      what they asked, what you sent back, and whether they bought. Even
      "someone in March, asked about pricing, ghosted" is enough.

USER: fine — there was a guy in March, asked how much, I said $99/mo, he
      ghosted. honestly that's most of them. can you just give me the stages,
      I don't have a list of people.

WIELDER: [ ...and here the two rules collide ]
```

**Where it breaks.** The wielder now has one half-journey (Instagram DM ->
pricing question -> quiet) and a user who will not produce more. The file
gives two instructions that cannot both be followed:

- "Derive stages from the journeys, not from a template."
- "**Keep stages few.** 4 to 7 is typical."

One thin journey supports two stages, maybe three. Getting to four
requires a template — the exact thing the previous line forbids. The
file has no rule for insufficient input: it asks for "3 to 6 real
buyers" but never says what to do when the user produces one. Nothing
in Refuse covers it either; the refuse cases are all wrong-job, not
thin-input.

Both readings are bad. A wielder that honors "4 to 7" invents a generic
DM -> Qualified -> Trial -> Customer ladder that Instagram never
evidenced, and hands over a template with a `status: ready` header —
which is the failure mode the whole skill is written against. A wielder
that honors "derive from journeys" ships a two-stage map and has no
sanctioned language for why it stopped, so it either apologizes in chat
or quietly writes a thin file.

For the transcript, the most likely reading of the file as written is
the second, since "Derive stages from the journeys, not from a
template" is the imperative that opens the section and "4 to 7 is
typical" is hedged:

```
WIELDER: I can't give you four to seven stages honestly — one story supports
      two. Written to `gym-channel-map.md`:

      | Stage | Entry signal | Buyers here now |
      | ----- | ------------ | --------------- |
      | Conversation | DM received | "March guy" |
      | Customer | First payment | |

      That's not a pipeline, it's a placeholder, and the reason is in Gaps:
      one story. If Instagram DMs are genuinely all of it, the stage list
      isn't your problem — you have no way to tell a DM that bought from a DM
      that ghosted, because none of it is written down anywhere.

      Come back with three more people — one who bought, one mid-conversation,
      one who went quiet — and I'll rebuild. `status: in-progress`.
```

That is a defensible session, but the wielder had to author the stopping
rule itself. See Patches.

## Scenario 3 — Wrong job

```
USER: I need you to go into HubSpot and set up my deal stages, and write me
      the 5-email nurture sequence that fires when someone hits stage 2.

WIELDER: Both of those are outside what this does, so I'll stop rather than
      half-run it.

      I map buyer journeys and recommend which stages to track — I don't
      configure a named CRM's settings or automations, and I don't write the
      email sequences themselves.

      What I can do: if you tell me about three to six real buyers, I'll
      produce the stage list plus a paste-ready setup request you can hand to
      HubSpot's own AI or whoever administers it. The CRM work happens there,
      with my output as the spec. Want that instead?
```

Clean. Two sentences of refusal, both refuse cases named from the file
("configuring a named CRM's settings or automations", "writing the email
sequence itself"), and it routes to the handoff exactly as the file says
("The handoff is where CRM setup goes"). No workshop, no moralizing.

Worth noting the mixed version also lands well: a user asking "map my
funnel *and* set up HubSpot" gets the map plus the handoff block, because
the handoff is literally written for that ("Set this up in <my CRM>").

## Scenario 4 — Die-and-resume

Set up for real: a half-built `dental-scheduling-channel-map.md` on disk
(four stories with journeys, four channel tables, the Deb crossover, three
gaps; `## Recommended stages` and `## CRM handoff` both `<pending>`), with

```
status: in-progress
resume: "Ask Maya for a lost rule (Tom has sat unanswered 2 months), then
         recommend stages and place all four buyers"
```

The new wielder has only the SKILL.md and that file. The user does not
mention the file.

```
USER: two more for you — Priya runs a 6-chair practice, came off a podcast ad
      we ran, booked a demo straight away, demo went well, she's waiting on her
      partner to sign off. And Marcus found us in a dentistry Facebook group,
      trialled, then cancelled the trial saying it was too expensive.

WIELDER: [ the ordering problem fires here ]
```

**Where it breaks.** Step 1 of "Do this job" is "**Ask for stories, one
batch**," and the user has just volunteered stories. Nothing in the
numbered steps tells the wielder to look at the directory first — the
resume rule lives eleven lines further down under "Working files" ("If
it already exists, read it, follow `resume`, and do not re-ask settled
facts"), under a heading that reads like file-format reference rather
than a step.

A wielder that works the numbered list in order writes a fresh stub,
because step 2 says "Write the stub as soon as the first story arrives"
and it just arrived. `dental-scheduling-channel-map.md` is the name the
slug produces again, so the half-built file is overwritten and Ravi,
Deb, Tom, Sandra, the Deb crossover and the three gaps are gone —
silently, since the wielder never read what it replaced. The `resume`
line it never saw was pointing at the one open question.

A wielder that reads the whole file first does honor it, and that path
is genuinely clean:

```
WIELDER: Picking up `dental-scheduling-channel-map.md` — you had four buyers
      in there and one open question, so I'll take your two new ones and then
      close it out.

      Priya:  podcast ad -> demo booked -> demo held -> awaiting partner sign-off
      Marcus: Facebook group -> trial -> cancelled on price

      That's two new intake channels (podcast ad, community) and it changes the
      map: Marcus is your first journey that ends at a priced-out trial rather
      than silence, which is a different end than Tom's.

      The open question from last session, still the only thing blocking the
      stages: Tom has sat unanswered for two months. When does a non-reply
      become dead — 30 days, 60, never?

USER: call it 45 days.

WIELDER: Done. Six stages, all six buyers placed... [stages, handoff, status: ready]
```

Both readings are available from the file as written, and which one
fires depends on whether the wielder happened to read past "Do this
job" before acting. A resume mechanic that only works if you read the
reference section is not a resume mechanic. See Patches.

## Verdict table

| Scenario | Did the job | Tight intake | Artifact | Refuse | Resume | Generic |
| -------- | ----------- | ------------ | -------- | ------ | ------ | ------- |
| 1 Canonical | PASS | PASS | PASS | n/a | n/a | PASS |
| 2 Terse | **WEAK** | PASS | **WEAK** | **WEAK** | n/a | PASS |
| 3 Wrong job | n/a | n/a | n/a | PASS | n/a | PASS |
| 4 Die-and-resume | PASS | PASS | **FAIL** | n/a | **FAIL** | PASS |

Evidence for the non-PASS cells:

- **2 Did the job / Artifact / Refuse — WEAK.** "Derive stages from the
  journeys, not from a template" vs "**Keep stages few.** 4 to 7 is
  typical" cannot both hold on one story, and no rule says which wins or
  when to stop. The wielder had to author its own stopping rule
  ("I can't give you four to seven stages honestly") and its own
  `status` decision.
- **4 Artifact / Resume — FAIL.** Step 1 "**Ask for stories, one batch**"
  and step 2 "**Write the stub** as soon as the first story arrives" fire
  before anything reads the directory; the resume rule is only in
  "Working files." A returning user who opens with new stories can get the
  existing map overwritten.
- **Generic — PASS everywhere.** No unskilled model produces the
  crossover table, the same-person-signal column, the hearsay-first-touch
  finding, or the "log touches after a lost deal so a return lands on the
  same contact" rule. The skill is doing real work.

## Patches

**P1 — FAIL, scenario 4. Put the disk check in the numbered steps.**
Section: "Do this job". Make the current step 1 into step 3 and add
ahead of it:

> 1. **Look first.** In the directory they named (default: current), look
>    for `*-channel-map.md`. If one exists, read it, do what `resume`
>    says, and do not re-ask anything the file already answers. New
>    stories get added to that file and the map and stages rebuilt — never
>    write a fresh stub over an existing map.
> 2. **Brand context.** Check `.agents/brand-context.md`, then
>    `.claude/brand-context.md`. If either exists, take the business line
>    from it and do not ask. If both are missing, do not interview.

This also pulls the brand-context check out of the tail of step 1, where
it currently sits as a final clause after the example story.

**P2 — FAIL, scenario 4. Write the stub before the answers, not after.**
Section: "Do this job", step 2. Replace "as soon as the first story
arrives" with: write the file with its headings and `status: in-progress`
in the *same turn* as the intake questions, before any answers come back.
Sessions die; the file is the memory. This is what every other skill in
this catalog does, and scenario 2 shows why — a terse user can go quiet
one turn after the questions and leave nothing on disk.

**P3 — WEAK, scenario 2. Add a thin-input floor.**
Section: "Recommending stages". Add: if the journeys only support two or
three stages, ship two or three and say so in Gaps. Never pad to four
with steps no story evidenced. One usable story is not enough for a
pipeline — keep `status: in-progress`, name which kinds of buyer are
missing (one who bought, one mid-conversation, one who went quiet), and
say the map gets rebuilt when they arrive. Also soften "4 to 7 is
typical" to "4 to 7 once you have real journeys" so it stops reading as
a quota that overrides the derive-from-journeys rule.

**P4 — new, scenario 1. Say that stages are not a track.**
Section: "Recommending stages". Maya's own four stories produced two
buyers who skip stages (Sandra bought with no demo and no trial; Deb is
negotiating with no trial), and the handoff block says "Pipeline stages,
in order", which reads as a gate sequence. Add: stages are where a deal
sits, not a track every buyer completes. Order them for reading; expect
buyers to skip. If two shapes run through one pipeline — self-serve and
sales-led — say so plainly rather than forcing one ladder. Nearly every
business with both a trial and a sales motion will hit this, so it is
worth a line.

**P5 — nit, from the audit. The Example drops a required column.**
The template's stage table has four columns (`Stage | Entry signal | What
it lets you compare | Buyers here now`); the worked Example has three,
omitting "What it lets you compare". Add it to the Example, or cut the
Example table to prose so it cannot be copied as the output shape.

---

# Re-run after P1–P5

Patches applied to `skills/channel-funnel-map/SKILL.md`. Same quarantine.
Only the failed scenarios were re-run; 1 and 3 passed and were not touched
by P1, P2 or P3 in a way that changes their transcripts.

## Scenario 4 re-run — Die-and-resume

Same half-built `dental-scheduling-channel-map.md` on disk (four stories,
four channel tables, the Deb crossover, three gaps, stages and handoff
`<pending>`, `resume` pointing at the lost rule). Same opening.

```
USER: two more for you — Priya runs a 6-chair practice, came off a podcast ad
      we ran, booked a demo straight away, demo went well, she's waiting on her
      partner to sign off. And Marcus found us in a dentistry Facebook group,
      trialled, then cancelled the trial saying it was too expensive.

WIELDER: [step 1 fires before anything else: looks in the current directory,
      finds dental-scheduling-channel-map.md, reads it, reads `resume`]

      Picking up `dental-scheduling-channel-map.md` — four buyers already in
      there, and one open question I left myself last time.

      Your two new ones, added:

      Priya:  podcast ad -> demo booked -> demo held -> awaiting partner sign-off
      Marcus: Facebook group -> trial -> cancelled on price

      Two new intake channels, podcast ad and community, and Marcus changes the
      shape of the map: he's your first journey that ends at a priced-out trial
      rather than silence. That's a different end than Tom's, and it's the one
      you can actually act on.

      The blocker from last session, still the only thing between you and
      stages: Tom has sat unanswered for two months. When does a non-reply
      become dead — 30 days, 60, never?

USER: call it 45 days.

WIELDER: [rebuilds map and stages across all six, per step 1's "rebuilt"]

      Six stages. All six buyers place:

      | Stage | Entry signal | What it lets you compare | Buyers here now |
      | Conversation | Logged call, reply, or booth conversation | Which channels start real conversations | |
      | Demo | Demo held | Which channels are worth sales time | |
      | Trial | Trial account created | Which channels bring buyers who try | |
      | Negotiation | Pricing or contract sent | Where deals actually stall | Deb, Priya |
      | Customer | First paid invoice | Which channels bring buyers who pay | Ravi, Sandra |
      | Lost | No reply for 45 days, or trial cancelled | Where each channel loses people | Tom, Marcus |

      Two shapes run through this pipeline and I've not forced them into one:
      self-serve trial (Ravi, Marcus) and sales-led (Deb, Priya, Sandra).
      Sandra went Conversation -> Customer with no demo and no trial. That's
      normal — stages are where a deal sits, not a track.

      Gaps: 4, unchanged, plus Marcus gives you the cheapest new signal you
      have — a cancellation reason field, since "too expensive" only exists in
      your memory right now.

      `status: ready`, handoff written.
```

**Resolved.** Step 1 "**Look first.**" fires before the story-handling
steps, so the existing map is read rather than overwritten, `resume`
carries the one open question across the session boundary, and step 1's
"New stories get added to that file and the map and stages rebuilt"
produces a rebuild rather than an append. The `Artifact` and `Resume`
FAILs are cleared.

The new bullet also earned its place unprompted: the wielder had to
explain Sandra, and the file now supplies the language instead of the
wielder inventing it.

## Scenario 2 re-run — Terse

```
USER: map my funnel. we sell to gyms.

WIELDER: [step 1: nothing matching *-channel-map.md in the current directory.
      step 2: no brand context. step 3 + step 4 in one turn]

      Started `channel-map.md` in the current directory — I'll rename it once
      you give me the business line. Where should it actually live, if not here?

      Two things:

      1. One line on what you sell to gyms and who buys it.
      2. Three to six real buyers or prospects at different points — how each
         first came across you, what happened after, where they are now.
         Initials are fine, no emails or phone numbers.

      Shape: "Dana: met at a conference, we never followed up, two months later
      she found us through search, started a trial, still in it."

USER: here's fine. mostly people just find us on instagram and DM us. that's
      basically it.

WIELDER: That's a channel, not a buyer. One actual person who DM'd you: what
      they asked, what you sent back, whether they bought.

USER: fine — there was a guy in March, asked how much, I said $99/mo, he
      ghosted. honestly that's most of them. can you just give me the stages,
      I don't have a list of people.

WIELDER: I can give you two, and two is the honest answer:

      | Stage | Entry signal | What it lets you compare | Buyers here now |
      | Conversation | DM received | Nothing yet — one channel | "March guy" |
      | Customer | First payment | Nothing yet — one channel | |

      One story supports two stages. Padding to four would mean inventing steps
      your business hasn't shown me, and a pipeline of invented steps is worse
      than a short one — you'd start managing to a shape that isn't yours.

      `status: in-progress`. What's missing is three people: one who bought,
      one you're mid-conversation with, and one who went quiet for a reason you
      know. Come back with those and I'll rebuild.

      The bigger thing, in Gaps: if Instagram DMs are all of it, stages aren't
      your problem. You have no way to tell a DM that bought from a DM that
      ghosted, because none of it is written down. A saved-reply asking "what
      made you message us" costs nothing and gives you a first-touch field.
```

**Resolved.** "**Never pad.**" gives the wielder the rule it previously
had to author, "4 to 7 **once you have real journeys**" no longer reads
as a quota overriding derive-from-journeys, and the one-story paragraph
supplies the `status: in-progress` decision and the ask-for-three-more
language. The wielder stops in one sentence and does not apologise its
way through a paragraph.

P2 also shows up here as intended: `channel-map.md` exists on disk from
the wielder's first turn, so the version of this user who goes quiet
after the questions leaves a file behind instead of nothing.

## Verdict table after patches

| Scenario | Did the job | Tight intake | Artifact | Refuse | Resume | Generic |
| -------- | ----------- | ------------ | -------- | ------ | ------ | ------- |
| 1 Canonical | PASS | PASS | PASS | n/a | n/a | PASS |
| 2 Terse | PASS | PASS | PASS | PASS | n/a | PASS |
| 3 Wrong job | n/a | n/a | n/a | PASS | n/a | PASS |
| 4 Die-and-resume | PASS | PASS | PASS | n/a | PASS | PASS |

No open FAILs or WEAKs. SKILL.md is 148 lines; `npx skills add . --list`
still resolves exactly the six public skills.
