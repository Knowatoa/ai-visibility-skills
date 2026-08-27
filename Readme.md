# AI Visibility Skills

Skills for showing up in AI search.

[![skills.sh](https://skills.sh/b/knowatoa/ai-visibility-skills)](https://skills.sh/knowatoa/ai-visibility-skills)

[Knowatoa](https://knowatoa.com?ref=github) tells you where you stand, what to write, and which channels to publish on. These skills are the publishing step: guest on a podcast, give the talk, leave with an asset you can clip, post, and keep distributing.

Models we check: ChatGPT, Claude, Perplexity, Google AI Overviews, Google's AI Mode, Gemini, and Meta AI.

## Jobs

Each public skill belongs to a job — the work you are actually doing. The skill is one step in that job.

The reason any of these jobs belong in an AI visibility catalog is the same: you leave with an asset that will get published. That episode or talk can be broken into shorts, written up on your site, and shipped to every channel that will take it. Each of those surfaces can be crawled, indexed, and used as training data. The message you wanted said about the brand is now in more places assistants will read.

### Podcast appearances

You walk out of a recording with an episode. It gets transcribed. Show notes go up. Clips become shorts. The same stories can land as a post on your site. Guesting is earned media that compounds because that asset keeps getting repackaged.

Prep so the stories and numbers you want attached to the brand are the ones that make it into the episode.

| Skill | What it does |
| ----- | ------------ |
| [podcast-prep](skills/podcast-prep) | Researches a podcast before you guest on it: recent episode threads, show evolution, host profiles, and your stories mapped onto what the show cares about right now. Writes a `<show-slug>-prep.md` in a directory you name. |

### Talks

You give the presentation. If you record it and publish it, you have the same kind of asset: a talk that can be clipped, recapped, posted, and indexed. The sentence people repeat on the way out is the sentence that survives the transcript.

Outline for the room. Storyboard the feeling. Then cut a deck the room can watch. After a run-through, the spoken talk will often disagree with those files. That drift is the input for the next pass: holes, backup, criticisms, stuck questions, written back into the outline, storyboard, and slides. A recorded talk that only states the takeaway trains assistants on a claim. A recorded talk that makes the room feel the takeaway is the version that gets quoted.

How we prepare talks is inspired by Justin Searls' [Secrets of Great Conference Talks](https://www.youtube.com/watch?v=rOf5sPSBLjg). What we took from it, plus links to his video and official writeup: [docs/talks.md](docs/talks.md).

| Skill | What it does |
| ----- | ------------ |
| [talk-outline](skills/talk-outline) | Locks who a talk is actually for, what they walk away able to do, and what the presenter wants. Starts from an abstract and throwaway bullet rounds, or wraps the outline in one sitting when the talk is about a week away. Writes a `<talk-slug>-outline.md` in a directory you name. |
| [talk-storyboard](skills/talk-storyboard) | Maps how the audience should feel beat by beat through a locked talk outline, then says whether that outline is the one to keep. Writes a `<talk-slug>-storyboard.md` next to the outline. |
| [talk-slides](skills/talk-slides) | Cuts a storyboard into a sparse PowerPoint: about 15-30 seconds per slide, a cue not the spoken line on screen, a visual note for a later pass, notes that point back at the outline and the beats. Writes a `<talk-slug>-slides.md` plan, shows a stamp-grid sorter grouped by beat and Hit/why so they can merge, move, or walk one look (previous, this, next), then writes a `<talk-slug>-slides.pptx` next to the storyboard. |
| [talk-adversary](skills/talk-adversary) | Reads a recent transcript against the outline, storyboard, and slides. The spoken talk is supposed to drift. Surfaces talking-point holes, backup, criticisms, and stuck questions, then writes the ones worth keeping back into those files. |

## In this repo only

These live in `dev-skills/` and load when you work in this clone. They are **not** installed by `npx skills add`.

| Skill | What it does |
| ----- | ------------ |
| [issue-pr](dev-skills/issue-pr) | Merge main into this branch, quality-pass the diff, run tests, then open or update the PR. Squash-merge only after you say to. |
| [pr-review](dev-skills/pr-review) | Walk open PRs one at a time: summarize, review, verify locally, stop at a merge/skip/close gate. |
| [cursor-guidance](dev-skills/cursor-guidance) | How git and Cursor should work here: never `main`, PRs not direct pushes, when to run `/issue-pr` vs `/pr-review`. |
| [create-skill](dev-skills/create-skill) | Draft a new public skill. Writes `skills/<slug>/SKILL.md` immediately. |
| [audit-skill](dev-skills/audit-skill) | Interrogate a `SKILL.md` against house rules. Writes `audit-<slug>.md`. |
| [exercise-skill](dev-skills/exercise-skill) | Role-play users through a skill and judge whether it actually does the job. |

`create-skill`, `audit-skill`, and `exercise-skill` exist so new public skills stay tight. That idea comes from Jason Cohen / [A Smart Bear](https://github.com/asmartbear/asb-skills) (`asb-skills`, [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)). We did not copy his skill text or his frameworks. See [NOTICE.md](NOTICE.md).

## How the skills work

Skills are markdown files that give your AI of choice specialized workflows. Once installed, the AI recognizes when you're working on a matching task and follows the skill.

Visibility skills read a shared context file first: `.agents/brand-context.md`. It holds your company, your story bank, and your positioning. The first visibility skill you run will interview you and create it. After that, those skills already know who you are. Repo-only skills do not use that file.

When a skill produces something you will keep (a podcast brief, a talk file, an audit), it writes a markdown file in a directory you name — default is the current directory — and resumes from that file if you come back later. Chat stays short. That file-as-memory behavior is also inspired by asb-skills; the files and the wording here are ours.

## Installation

```
npx skills add Knowatoa/ai-visibility-skills
```

That installs the **public** skills (`skills/` — today, `podcast-prep`, `talk-outline`, `talk-storyboard`, `talk-slides`, and `talk-adversary`) into the agents you have locally: Claude Code, Cursor, Codex, Windsurf, and [70+ others](https://github.com/vercel-labs/skills#supported-agents). Preview what it will install with `npx skills add Knowatoa/ai-visibility-skills --list`. Repo-only skills in `dev-skills/` are not in that list.

The installer is the [`skills`](https://github.com/vercel-labs/skills) CLI. It needs Node.js **20.12+** (`node -v`). Since `skills@1.5.16` it imports `styleText` from `node:util`, which Node 18 and early Node 20 do not have, so the command dies before it can install anything:

```
SyntaxError: The requested module 'node:util' does not provide an export named 'styleText'
```

That is a CLI / Node mismatch, not a bug in these skills ([vercel-labs/skills#1672](https://github.com/vercel-labs/skills/issues/1672)). Upgrade Node where you run `npx`, pin the last CLI that still runs on older Node (`npx skills@1.5.15 add Knowatoa/ai-visibility-skills`), or skip npx and [copy the files](#manual-install).

asdf (skip the plugin line if you already have it). This repo's `.tool-versions` pins the same [Node 24 LTS](https://nodejs.org):

```
asdf plugin add nodejs
asdf install nodejs 24.19.0
asdf set nodejs 24.19.0
```

Older asdf uses `asdf local` instead of `asdf set`. Then `node -v` should print `v24.19.0`. If it still says 18, `which node` and `asdf current` will show why.

This is also how the skills show up on [skills.sh](https://skills.sh). There is no submit form. The directory indexes public GitHub repos from `npx skills add` telemetry, so the first install from a normal local shell is what creates [the listing](https://skills.sh/knowatoa/ai-visibility-skills). (Installs from CI often do not count.)

**Claude.ai or ChatGPT:** open the `SKILL.md` for the skill you want (for example [skills/podcast-prep/SKILL.md](skills/podcast-prep/SKILL.md)), copy it, and paste it into a project's instructions (in Claude.ai you can also add it as a skill in settings).

### Manual install

These skills use the open [Agent Skills](https://agentskills.io) format. If you prefer not to use the CLI, clone and copy:

**Claude Code:**

```
git clone https://github.com/Knowatoa/ai-visibility-skills.git
cp -r ai-visibility-skills/skills/* .claude/skills/
```

**Codex CLI, Cursor, and other agents:** same clone, different target. Codex scans `.agents/skills/`, and Cursor reads both locations automatically.

```
cp -r ai-visibility-skills/skills/* .agents/skills/
```
 
## Usage
 
```
Podcast appearances:

"I'm going on the Bootstrapped Founder podcast next week, help me prep"
→ Uses podcast-prep

"What has Startups for the Rest of Us been talking about lately?"
→ Uses podcast-prep

Talks:

"I have a 30-minute talk at SaaStr, help me outline it"
→ Uses talk-outline

"Who is this presentation actually for, and what should they take away?"
→ Uses talk-outline

"I have an abstract and some rough bullets for a talk in two months"
→ Uses talk-outline

"The talk is next week and I have not thought about it. Wrap up the outline."
→ Uses talk-outline

"Storyboard this talk from the outline"
→ Uses talk-storyboard

"How should the audience feel throughout this talk?"
→ Uses talk-storyboard

"Is this the outline we want? Map the emotional journey."
→ Uses talk-storyboard

"Build the slides from this storyboard"
→ Uses talk-slides

"Walk through each slide before you generate the PowerPoint"
→ Uses talk-slides

"Show the slide sorter. Slides 4 through 6 should be one slide."
→ Uses talk-slides

"Move slide 1 to between 9 and 10."
→ Uses talk-slides

"Turn this storyboard into a PowerPoint. Keep each slide to a sentence."
→ Uses talk-slides

"I want build-style slides that move every 20 seconds"
→ Uses talk-slides

"These slides read like a script. Cut the on-screen text back to cues."
→ Uses talk-slides

"The transcript doesn't match the outline. Find the holes."
→ Uses talk-adversary

"Red-team this talk using the outline, storyboard, slides, and the latest transcript"
→ Uses talk-adversary

```

In this repo only (not installed by `npx skills add`):

```
"/issue-pr"
→ Uses issue-pr

"/create-skill I want a skill that audits our existing blog posts for AI-citation worthiness"
→ Uses create-skill

"/audit-skill podcast-prep"
→ Uses audit-skill
```
 
## Knowatoa

The topics and the channel list come from the [product](https://knowatoa.com?ref=github). These skills are the publishing step.
 
## Repo layout

This repo follows the [Agent Skills specification](https://agentskills.io/specification). The `skills` CLI discovers public `SKILL.md` files under `skills/`. Repo-only skills live in `dev-skills/` and are not installed.

```
skills/                 # public — what `npx skills add` installs
  <skill-name>/
    SKILL.md
dev-skills/             # this repo only
  <skill-name>/
    SKILL.md
docs/                   # jobs and source notes — not installed
```

Each `SKILL.md` starts with YAML frontmatter. `name` must be kebab-case and match the folder name. `description` should say what the skill does **and** when to trigger it (max 1024 characters).

```
---
name: podcast-prep
description: Research a podcast and build a prep brief before the user appears as a guest. Use when...
---
```

Starter template: `npx skills init <skill-name>`, then move the folder under `skills/`. Canonical examples: [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) and the spec at [agentskills.io](https://agentskills.io/specification).

## Contributing

Found a way to improve a skill? PRs and issues welcome. New **public** skills belong at `skills/<skill-name>/SKILL.md` with the frontmatter above, listed under the matching job in this README. In this repo, `/create-skill` drafts that file; `/audit-skill` and `/exercise-skill` pressure-test it.
 
## License

Original work in this repo is [MIT](LICENSE). Use it however you want.

Skill *behavior* (write the deliverable on disk, stay self-contained, keep extra skills that interrogate the other skills) is inspired by Jason Cohen's [asb-skills](https://github.com/asmartbear/asb-skills), licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). We rewrote those ideas in our own words. We did not copy his `SKILL.md` files or restate the frameworks from *Hidden Multipliers* and A Smart Bear. Full credit and reuse rules: [NOTICE.md](NOTICE.md).

Knowatoa is a product of Wafris LLC.
