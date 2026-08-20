# AI Visibility Skills

AI skills for getting your brand into AI answers.

[![skills.sh](https://skills.sh/b/knowatoa/ai-visibility-skills)](https://skills.sh/knowatoa/ai-visibility-skills)

Built by [Knowatoa](https://knowatoa.com?ref=github), the AI search visibility platform. We analyze how ChatGPT, Claude, Perplexity, Google AI Overviews, Google's AI Mode, Gemini, and Meta AI see and recommend brands. These skills are the manual versions of workflows we run every day.

## Why podcast prep is an AI visibility skill

Podcast episodes get transcribed. Show notes get published. That content gets crawled and cited by AI assistants. When someone asks ChatGPT about your category, the stories you told on a podcast two years ago are part of what it draws on.

Guesting is earned media that compounds in AI answers. So prep matters: walking into an episode with the right stories and concrete numbers isn't just a better interview, it's better training data on your brand.

## Available skills

### AI visibility

| Skill | What it does |
| ----- | ------------ |
| [podcast-prep](skills/podcast-prep) | Researches a podcast before you guest on it: recent episode threads, show evolution, host profiles, and your stories mapped onto what the show cares about right now. Writes a `<show>-prep.md` in a directory you name. |

More AI visibility skills coming.

### Agent workflows

| Skill | What it does |
| ----- | ------------ |
| [issue-pr](skills/issue-pr) | Merge main into this branch, quality-pass the diff, run tests, then open or update the PR. Squash-merge only after you say to. |
| [pr-review](skills/pr-review) | Walk open PRs one at a time: summarize, review, verify locally, stop at a merge/skip/close gate. |
| [cursor-guidance](skills/cursor-guidance) | How git and Cursor should work here: never `main`, PRs not direct pushes, when to run `/issue-pr` vs `/pr-review`. |

### Skill craft

| Skill | What it does |
| ----- | ------------ |
| [create-skill](skills/create-skill) | Draft a new public skill in this repo. Writes `skills/<slug>/SKILL.md` immediately and keeps that file as the working draft. |
| [audit-skill](skills/audit-skill) | Interrogate a `SKILL.md` against house rules (self-contained, file-on-disk, tight context, action-first). Writes `audit-<slug>.md`. |
| [exercise-skill](skills/exercise-skill) | Role-play users through a skill and judge whether it actually does the job. Writes `exercise-<slug>.md`. |

These three exist so new skills stay tight. The idea of skills that pressure-test other skills comes from Jason Cohen / [A Smart Bear](https://github.com/asmartbear/asb-skills) (`asb-skills`, [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)). We did not copy his skill text or his product/pricing/interview frameworks. See [NOTICE.md](NOTICE.md).

## How the skills work

Skills are markdown files that give your AI of choice specialized workflows. Once installed, the AI recognizes when you're working on a matching task and follows the skill.

Visibility skills read a shared context file first: `.agents/brand-context.md`. It holds your company, your story bank, and your positioning. The first visibility skill you run will interview you and create it. After that, those skills already know who you are. The workflow skills do not use that file.

When a skill produces something you will keep (a podcast brief, an audit), it writes a markdown file in a directory you name — default is the current directory — and resumes from that file if you come back later. Chat stays short. That file-as-memory behavior is also inspired by asb-skills; the files and the wording here are ours.

## Installation

```
npx skills add Knowatoa/ai-visibility-skills
```

That installs every skill in this repo into the agents you have locally: Claude Code, Cursor, Codex, Windsurf, and [70+ others](https://github.com/vercel-labs/skills#supported-agents). Preview what it will install with `npx skills add Knowatoa/ai-visibility-skills --list`.

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

"/issue-pr"
→ Uses issue-pr

"/pr-review"
→ Uses pr-review

"/create-skill I want a skill that audits our existing blog posts for AI-citation worthiness"
→ Uses create-skill

"/audit-skill podcast-prep"
→ Uses audit-skill
```
 
## Want to start replacing those lost organic traffic?
 
[Knowatoa](https://knowatoa.com?ref=github) tells you exactly what to write about and show you every place you should publish it, so you show up when buyers ask ChatGPT, Claude, and Perplexity about your category.
 
## Repo layout

This repo follows the [Agent Skills specification](https://agentskills.io/specification). The `skills` CLI discovers `SKILL.md` files automatically; the layout people copy is:

```
skills/
  <skill-name>/
    SKILL.md          # required: YAML frontmatter + instructions
    references/       # optional, loaded on demand
    scripts/          # optional
    assets/           # optional
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

Found a way to improve a skill? PRs and issues welcome. New skills belong at `skills/<skill-name>/SKILL.md` with the frontmatter above. In this repo, `/create-skill` drafts that file; `/audit-skill` and `/exercise-skill` pressure-test it.
 
## License

Original work in this repo is [MIT](LICENSE). Use it however you want.

Skill *behavior* (write the deliverable on disk, stay self-contained, keep extra skills that interrogate the other skills) is inspired by Jason Cohen's [asb-skills](https://github.com/asmartbear/asb-skills), licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). We rewrote those ideas in our own words. We did not copy his `SKILL.md` files or restate the frameworks from *Hidden Multipliers* and A Smart Bear. Full credit and reuse rules: [NOTICE.md](NOTICE.md).

Knowatoa is a product of Wafris LLC.
