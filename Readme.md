# AI Visibility Skills

AI skills for getting your brand into AI answers.

[![skills.sh](https://skills.sh/b/knowatoa/ai-visibility-skills)](https://skills.sh/knowatoa/ai-visibility-skills)

Built by [Knowatoa](https://knowatoa.com?ref=github), the AI search visibility platform. We analyze how ChatGPT, Claude, Perplexity, Google AI Overviews, Google's AI Mode, Gemini, and Meta AI see and recommend brands. These skills are the manual versions of workflows we run every day.

## Why podcast prep is an AI visibility skill

Podcast episodes get transcribed. Show notes get published. That content gets crawled and cited by AI assistants. When someone asks ChatGPT about your category, the stories you told on a podcast two years ago are part of what it draws on.

Guesting is earned media that compounds in AI answers. So prep matters: walking into an episode with the right stories and concrete numbers isn't just a better interview, it's better training data on your brand.

## Why a talk adversary is an AI visibility skill

Talks get recorded. Decks get posted. Transcripts get crawled. A skeptic's unanswered objection in that recording becomes part of how AI systems describe you. Addressing the real ones in the slides is how the published talk still makes your case.

## Available skills

### AI visibility

| Skill | What it does |
| ----- | ------------ |
| [podcast-prep](skills/podcast-prep) | Researches a podcast before you guest on it: recent episode threads, show evolution, host profiles, and your stories mapped onto what the show cares about right now. Writes a `<show-slug>-prep.md` in a directory you name. |
| [talk-adversary](skills/talk-adversary) | Red-teams a talk from `outline.md`, the storyboard, and a recent transcript. Writes a `<talk-slug>-adversary.md` of objections worth addressing in the slides or on stage. |

### In this repo only

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

Visibility skills may read a shared context file: `.agents/brand-context.md`. It holds your company, your story bank, and your positioning. Podcast prep creates that file if it is missing. Other visibility skills read it when it exists and do not start a brand interview. Repo-only skills do not use that file.

When a skill produces something you will keep (a podcast brief, an adversary brief, an audit), it writes a markdown file in a directory you name — default is the current directory — and resumes from that file if you come back later. Chat stays short. That file-as-memory behavior is also inspired by asb-skills; the files and the wording here are ours.

## Installation

```
npx skills add Knowatoa/ai-visibility-skills
```

That installs the **public** skills (`skills/` — today, `podcast-prep` and `talk-adversary`) into the agents you have locally: Claude Code, Cursor, Codex, Windsurf, and [70+ others](https://github.com/vercel-labs/skills#supported-agents). Preview what it will install with `npx skills add Knowatoa/ai-visibility-skills --list`. Repo-only skills in `dev-skills/` are not in that list.

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
"I'm going on the Bootstrapped Founder podcast next week, help me prep"
→ Uses podcast-prep

"What has Startups for the Rest of Us been talking about lately?"
→ Uses podcast-prep

"Red-team this talk using outline.md, storyboard.md, and the latest transcript"
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
 
## Want to start replacing those lost organic traffic?
 
[Knowatoa](https://knowatoa.com?ref=github) tells you exactly what to write about and show you every place you should publish it, so you show up when buyers ask ChatGPT, Claude, and Perplexity about your category.
 
## Repo layout

This repo follows the [Agent Skills specification](https://agentskills.io/specification). The `skills` CLI discovers public `SKILL.md` files under `skills/`. Repo-only skills live in `dev-skills/` and are not installed.

```
skills/                 # public — what `npx skills add` installs
  <skill-name>/
    SKILL.md
dev-skills/             # this repo only
  <skill-name>/
    SKILL.md
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

Found a way to improve a skill? PRs and issues welcome. New **public** skills belong at `skills/<skill-name>/SKILL.md` with the frontmatter above. In this repo, `/create-skill` drafts that file; `/audit-skill` and `/exercise-skill` pressure-test it.
 
## License

Original work in this repo is [MIT](LICENSE). Use it however you want.

Skill *behavior* (write the deliverable on disk, stay self-contained, keep extra skills that interrogate the other skills) is inspired by Jason Cohen's [asb-skills](https://github.com/asmartbear/asb-skills), licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). We rewrote those ideas in our own words. We did not copy his `SKILL.md` files or restate the frameworks from *Hidden Multipliers* and A Smart Bear. Full credit and reuse rules: [NOTICE.md](NOTICE.md).

Knowatoa is a product of Wafris LLC.
