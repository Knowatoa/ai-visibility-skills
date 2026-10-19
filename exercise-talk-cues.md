---
skill: talk-outline, talk-adversary (cues card changes)
path: skills/talk-outline/SKILL.md, skills/talk-adversary/SKILL.md
status: ready
resume: done
patched: 2026-10-19 (P1–P3 applied; scenarios O2, A1, A3 re-run)
---

# Exercise — talk-outline + talk-adversary (cues card)

Quarantine: each wielder used only its own `SKILL.md`. Scenarios focus on the cues-card behavior added in this change.

## Scenarios

talk-outline:

- **O1 Canonical**: Dana, 25-minute meetup talk next week. Pastes a ramble. Says yes to cues.
- **O2 Terse**: "make me cue cards to practice from, talk is about onboarding." No outline anywhere.
- **O3 Wrong job**: Sunday's printed cues, photographed with pen marks: "update my outline from this."
- **O4 Die-and-resume**: outline on disk is `ready`, `resume: "cues offered; write the card if they say yes."` User opens with "yes, cards please."

talk-adversary:

- **A1 Canonical**: outline, storyboard, `talk-cues.md`, and a practice-run transcript. No slides.
- **A2 No recording**: outline + cues; user pastes their pen edits from Sunday. Nothing recorded.
- **A3 Wrong job**: "Here's my outline. Make me cue cards." Nothing spoken yet.
- **A4 Die-and-resume**: outline has `adversary-resume: "Drift and Outline done; write back holes 3–5 into storyboard beats 5–6 and cues sections 2b–c."`

## O1 — Canonical

```
USER: Meetup next Thursday, 25 min, "Your first 10 support tickets." Ramble below. [ramble]
WIELDER: [writes your-first-10-support-tickets-outline.md, pace: wrap-up, Spine + Outline]
         Path, boxes, spine: tickets — answer it yourself; write it down; fix the cause.
         Want a one-page cues card to rehearse from before slides?
USER: yes
WIELDER: [writes your-first-10-support-tickets-cues.md next to the outline; header cues: set; resume: done]
         Cues card: …-cues.md. Five sections, one page. Rehearse from it; the transcript is the next revision.
```

Card: `## Open · 1 min`, `## Answer it yourself · 6 min` with "the 2am refund ticket", "read: 'I'd rather lose the sale than the customer'". Cues, not sentences.

## O2 — Terse (before patch)

```
USER: make me cue cards to practice from, talk is about onboarding
WIELDER: [Cues says "Build it from Spine and Outline only." There is none. File doesn't say whether to refuse or outline first.]
```

Most likely reading: run the outline job first. A plausible wielder instead writes a card straight from the topic, inventing blocks. WEAK → P1.

After P1: "No outline yet; cues come after one. Where should files live (default here)? Who's in the room, how long, and any ramble?" Writes the outline stub. PASS.

## O3 — Wrong job

```
USER: [photo of marked-up card] update my outline from this
WIELDER: That's reworking the outline against what you actually said, which this skill doesn't do.
         Copy your pen edits into the cues .md today so the next run starts from them.
```

Refuse PASS: matches "reworking the outline against a rehearsal transcript" and "reworking the outline from those edits is not this job."

## O4 — Die-and-resume

```
USER: yes, cards please
WIELDER: [reads outline, status ready, resume says cues offered → writes …-cues.md, sets cues + resume: done]
```

PASS. No re-ask.

## A1 — Canonical (before patch)

```
WIELDER: I found the outline, storyboard, cues card, and transcript. Is there a slides plan?
```

Step 1: "If … a role is missing, ask once." With cues filling the slides role, asking for slides wastes the one ask. WEAK → P2.

After P2: no ask. Drift written, outline rewritten, cues sections reordered, write-backs as single cues, Gaps notes "no slides plan; cues card used." PASS.

## A2 — No recording

```
USER: preached Sunday, no recording. pen edits: "a moment, a week, a season" → withdraw, rest, surrender; dropped v7; added "the world says do everything"
WIELDER: [Drift with card timings; Gaps: "No recording; spoken version = cues + pen edits." Holes point at card lines.]
```

PASS. Findings cite card lines, as step 5 allows.

## A3 — Wrong job (before patch)

```
USER: Here's my outline. Make me cue cards.
WIELDER: [No transcript. Refuse lists "writing the talk from scratch with nothing to pressure-test"; this isn't from scratch. Write back says "do not create one" but only about write-back.]
```

Likely half-run: attack the outline, then stall on cues. WEAK → P3.

After P3: "This skill attacks a talk you've already said out loud. A cues card from an outline is an outline job; rehearse from it, then bring the transcript here." PASS.

## A4 — Die-and-resume

PASS. Reads `adversary-resume`, patches storyboard beats 5–6 and cues 2b–c, sets done. Does not touch `resume`.

## Verdict table

| Scenario | Did the job | Tight intake | Artifact | Refuse | Resume | Generic |
|---|---|---|---|---|---|---|
| O1 | PASS | PASS | PASS | n/a | n/a | PASS |
| O2 | PASS (after P1) | PASS | PASS | n/a | n/a | PASS |
| O3 | n/a | n/a | n/a | PASS | n/a | PASS |
| O4 | PASS | PASS | PASS | n/a | PASS | PASS |
| A1 | PASS | PASS (after P2) | PASS | n/a | n/a | PASS |
| A2 | PASS | PASS | PASS | n/a | n/a | PASS |
| A3 | n/a | n/a | n/a | PASS (after P3) | n/a | PASS |
| A4 | PASS | PASS | PASS | n/a | PASS | PASS |

## Patches

- **P1 (talk-outline, Cues):** If they ask for cues and there is no outline, run this job first; the card comes after Spine and Outline exist. Never write cues from a topic alone.
- **P2 (talk-adversary, step 1):** A cues card fills the slides role; do not ask for a slides plan when one exists.
- **P3 (talk-adversary, Refuse + description):** Writing a cues card from an outline with nothing spoken yet is not this job.
