---
skill: talk-outline, talk-adversary (cues changes)
status: ready
resume: done
---

# Audit — talk-outline + talk-adversary (cues card)

## Verdict
Ship. No FAILs; three WEAKs patched before commit.

## Checks
| Check | talk-outline | talk-adversary |
| ----- | ------------ | -------------- |
| A Frontmatter | PASS: name matches, 984 chars, Do NOT kept | PASS: name matches, 1010 chars, Do NOT kept |
| B Self-contained | PASS: cues spec is inline; no sibling required | PASS: cues card shape specified inline in Write back |
| C Artifact | PASS after patch: `<talk-slug>-cues.md` next to the outline; resume now records "cues offered" | PASS: cues card patched in place; stale printed cues go to Gaps |
| D Tight context | PASS: built from Spine and Outline only | PASS: no new reads beyond the user's files |
| E Action-first | PASS: one offer, in the ready message | PASS |
| F Refuse | PASS: unchanged; WEAK fixed — card markup rework was drifting into the adversary's job | PASS: unchanged |
| G Length and voice | PASS: 158 lines | PASS: 90 lines |

## Patches applied
- talk-outline: pen-edit rework handed back to the speaker, not done by this skill.
- talk-outline: `resume` set while the cues offer is pending.
- talk-adversary: findings may point at a card line when there is no recording.
