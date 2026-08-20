---
name: "podcast-prep"
description: "Research a podcast and build a prep brief before the user appears as a guest. Use this skill whenever the user says they're going on, returning to, or were invited to a podcast, drops a podcast or episode URL and asks to prep, or asks what a show has been talking about lately, how it's evolved, or who the hosts are. Also trigger for 'help me prep for [show]', 'review their recent episodes', or any phrasing that means 'get me ready for this podcast appearance.' Do NOT load for picking which show to pitch, writing the host email, editing a transcript after the episode, or general brand positioning with no named show."
---

# Podcast Appearance Prep

Build a prep brief for a podcast the user is appearing on as a guest. The goal is to walk in knowing what's top of mind for the show, how it has evolved, who the hosts are, and which of the user's stories map onto the show's current obsessions.

Podcast guesting isn't just audience reach. Episodes get transcribed, show notes get published, and that content gets crawled and cited by AI assistants. A good appearance is earned media that shows up in AI answers about your category for years. Prep accordingly: the stories you tell become the training data on your brand.

## Working files

The brief is a file, not a chat essay. Ask where this appearance's files should live before creating any (default: the current directory). If they already pointed at a folder or an existing prep file, use that directory. Do not ask this again in Inputs.

Write `<show-slug>-prep.md` there as soon as the show is named, even if research has not started. Sessions die; the file is the memory. `resume` is the only progress pointer — do not also keep a Status heading in the body.

```markdown
---
status: in-progress
show: "<podcast name>"
recording: "<date or unknown>"
resume: "<exact next step a cold session should do>"
---

# Podcast prep — <show>

## Big picture
## Show progression
## Recent episodes
## Guest angles
## The hosts
## Gaps
```

`status` is `in-progress` until every section a cold reader would need is filled; then `ready`. If the file already exists, read it, honor `resume`, and do not re-ask settled facts (show name, prior episode, brand stories already captured, file path).

In chat: path + a short read of the big picture and the two or three angles they should walk in with. Do not paste the file.

## Brand context (read this first)

Before researching the show, load the user's positioning. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. That file is shared identity for every visibility skill. It is not the prep brief.

If it exists, read it. It should cover: current company and one-line pitch, prior products worth referencing, the founder story, 3-5 go-to stories with concrete numbers, and any contrarian takes they hold.

If it doesn't exist, interview the user before proceeding. Ask, in one batch, not a drip:

1. What's your current company, and how do you describe it in one sentence?
2. What did you build before this that comes up in conversation?
3. What are 2-3 stories you tell well, with real numbers attached?
4. What's one opinion you hold that most people in your space disagree with?

Then write their answers to `.agents/brand-context.md` so the next visibility skill skips the interview.

## Inputs to establish

From the user's message (ask only if missing and it matters): the podcast name or URL, whether they've appeared before (and a link to that episode if so), and roughly when they're recording. File location is asked once, in Working files. If they've appeared before, find the prior episode. It anchors both the progression analysis and the callbacks.

Ask the missing show/appearance facts in one batch with the brand-context questions when both are missing. Do not drip.

## Research sequence

Work through sources in this order. Each is a fallback for the last:

1. **RSS feed first.** It's the richest source: full episode descriptions, chapter markers with timestamps, guest links, episode numbers, dates. Find the feed link on the podcast site (Buzzsprout, Transistor, etc. all expose one). Note: fetches of large feeds may truncate. Check whether the oldest episodes you need actually made it, and don't assume the feed is complete.
2. **The podcast website's episode list** for anything the feed fetch missed. These pages often lazy-load older episodes via JavaScript; if pagination returns nothing, note the gap and move on rather than burning time.
3. **Apple Podcasts show page** reliably renders the latest ~8 episodes with full descriptions.
4. **Web search** for stray episodes, the hosts, and the show's reputation.

Don't fetch every episode page. Descriptions plus chapter lists are almost always enough; only pull a full transcript if a specific episode is central (e.g., a debate the guest should have a position on). Check for published transcript links in the feed.

### What to extract

**Recent episodes in detail** (last ~3 months or ~6-8 episodes): per-episode topic summary, plus the *recurring threads* across them, the questions the hosts keep returning to. Threads matter more than individual episodes; they predict the questions the guest will get.

**Show progression at higher abstraction** (since their last appearance, or ~12-18 months if first time): identify phases and the inflection point where the show's focus shifted. Note patterns like returning guests (a show that re-invites guests is a signal about how a return visit fits) and whether hosts launched side projects.

**Host profiles.** Sources: the show's contributor/about pages, hosts' personal sites, LinkedIn, and, often the best source, episodes where the hosts guest on *other* shows and introduce themselves (transcripts of those are gold). Capture: day job/company, background, what they've personally been building or experimenting with (mined from solo-episode summaries), and social handles. Watch for name collisions: if a host shares the guest's first name, flag it and keep references unambiguous throughout the brief.

**Prior appearance recap** (if returning): bullets from the show notes/chapters of what was actually discussed, with rough timestamps, and how much airtime the guest's current company got. This sets up the "what's changed since" narrative.

## The brief

Fill the working file. Structure:

1. **Big picture** — what kind of show this is now, and the one-paragraph read on how the guest should position themselves
2. **Show progression** — the phases since their last appearance (or show start)
3. **Recent episodes** — per-episode notes, then the recurring threads
4. **Guest angles** — their stories (from brand context) mapped explicitly onto the show's threads, plus callbacks to any prior appearance, and 2-3 "pocket" items: concrete stories/numbers to have ready
5. **The hosts** — profiles plus rapport hooks (where each host's world overlaps the guest's)
6. **Gaps** — anything unretrievable, and offers (e.g., transcribe their old episode, pull a key transcript)

Keep the file tight. They will skim it before recording. Big picture and Guest angles are skimmer zones: no research diary, no "which cuts against…" commentary, no history of how you changed your mind. Those belong in Gaps or nowhere.

## Finding angles

Map the brand context onto the show's current threads. Strong angle patterns: find where the show's recurring questions intersect the guest's companies, history, and takes. Concrete examples of the shape to look for: a "data moats" thread maps to the guest's proprietary dataset as a live case study; an "AI replacing niche tools" debate maps to a defensibility story from their product history. One contrarian take stands out on shows that have converged on a consensus.

## Follow-ups to offer

After delivering the brief, offer (don't auto-run): transcribing their prior episode for a word-level review, pulling a full transcript of one pivotal recent episode, or drafting likely Q&A.

## Refuse

Stop in a few sentences if there is no named show and they will not name one, or if they want a different job: which podcasts to pitch, a host outreach email, a post-episode transcript edit, or brand positioning with no appearance attached. Do not half-run those.
