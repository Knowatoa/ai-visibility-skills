# AI Visibility Skills

AI skills for getting your brand into AI answers.

[![skills.sh](https://skills.sh/b/knowatoa/ai-visibility-skills)](https://skills.sh/knowatoa/ai-visibility-skills)

Built by [Knowatoa](https://knowatoa.com?ref=github), the AI search visibility platform. We analyze how ChatGPT, Claude, Perplexity, Google AI Overviews, Google's AI Mode, Gemini, and Meta AI see and recommend brands. These skills are the manual versions of workflows we run every day.

## Why podcast prep is an AI visibility skill

Podcast episodes get transcribed. Show notes get published. That content gets crawled and cited by AI assistants. When someone asks ChatGPT about your category, the stories you told on a podcast two years ago are part of what it draws on.

Guesting is earned media that compounds in AI answers. So prep matters: walking into an episode with the right stories and concrete numbers isn't just a better interview, it's better training data on your brand.

## Why presentation outline is an AI visibility skill

Talks get recorded. Decks get posted. Recap posts get crawled. The sentence you repeat on stage is the sentence assistants will quote later. That outline is usually a few throwaway bullet lists over a few weeks, not a one-sitting deck. A real audience and a Monday takeaway beat a generic "problem / solution / demo" that trains the model on nothing specific.

## Available skills

### AI visibility

| Skill | What it does |
| ----- | ------------ |
| [podcast-prep](skills/podcast-prep) | Researches a podcast before you guest on it: recent episode threads, show evolution, host profiles, and your stories mapped onto what the show cares about right now. Writes a `<show-slug>-prep.md` in a directory you name. |
| [presentation-outline](skills/presentation-outline) | Locks who a talk is actually for, what they walk away able to do, and what the presenter wants. Starts from an abstract and throwaway bullet rounds, or wraps the outline in one sitting when the talk is about a week away. Writes a `<talk-slug>-outline.md` in a directory you name. |

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

Visibility skills read a shared context file first: `.agents/brand-context.md`. It holds your company, your story bank, and your positioning. The first visibility skill you run will interview you and create it. After that, those skills already know who you are. Repo-only skills do not use that file.

When a skill produces something you will keep (a podcast brief, an audit), it writes a markdown file in a directory you name — default is the current directory — and resumes from that file if you come back later. Chat stays short. That file-as-memory behavior is also inspired by asb-skills; the files and the wording here are ours.

## Installation

```
npx skills add Knowatoa/ai-visibility-skills
```

That installs the **public** skills (`skills/` — today, `podcast-prep` and `presentation-outline`) into the agents you have locally: Claude Code, Cursor, Codex, Windsurf, and [70+ others](https://github.com/vercel-labs/skills#supported-agents). Preview what it will install with `npx skills add Knowatoa/ai-visibility-skills --list`. Repo-only skills in `dev-skills/` are not in that list.

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
"I'm going on the Bootstrapped Founder podcast next week, help me prep"
→ Uses podcast-prep

"What has Startups for the Rest of Us been talking about lately?"
→ Uses podcast-prep

"I have a 30-minute talk at SaaStr, help me outline it"
→ Uses presentation-outline

"Who is this presentation actually for, and what should they take away?"
→ Uses presentation-outline

"I have an abstract and some rough bullets for a talk in two months"
→ Uses presentation-outline

"The talk is next week and I have not thought about it. Wrap up the outline."
→ Uses presentation-outline

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
