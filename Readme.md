# AI Visibility Skills

AI skills for getting your brand into AI answers.

[![skills.sh](https://skills.sh/b/Knowatoa/ai-visibility-skills)](https://skills.sh/Knowatoa/ai-visibility-skills)

Built by [Knowatoa](https://knowatoa.com?ref=github), the AI search visibility platform. We analyze how ChatGPT, Claude, Perplexity, Google AI Overviews, Google's AI Mode, Gemini, and Meta AI see and recommend brands. These skills are the manual versions of workflows we run every day.

## Why podcast prep is an AI visibility skill

Podcast episodes get transcribed. Show notes get published. That content gets crawled and cited by AI assistants. When someone asks ChatGPT about your category, the stories you told on a podcast two years ago are part of what it draws on.

Guesting is earned media that compounds in AI answers. So prep matters: walking into an episode with the right stories and concrete numbers isn't just a better interview, it's better training data on your brand.

## Available skills

| Skill | What it does |
| ----- | ------------ |
| [podcast-prep](skills/podcast-prep) | Researches a podcast before you guest on it: recent episode threads, show evolution, host profiles, and your stories mapped onto what the show cares about right now. |

More coming. This repo will grow into a full AI search visibility toolkit.

## How the skills work

Skills are markdown files that give your AI of choice specialized workflows. Once installed, the AI recognizes when you're working on a matching task and follows the skill.

Every skill in this repo reads a shared context file first: `.agents/brand-context.md`. It holds your company, your story bank, and your positioning. The first skill you run will interview you and create it. After that, every skill already knows who you are.

## Installation

```
npx skills add Knowatoa/ai-visibility-skills
```

That installs every skill in this repo into the agents you have locally: Claude Code, Cursor, Codex, Windsurf, and [70+ others](https://github.com/vercel-labs/skills#supported-agents). Preview what it will install with `npx skills add Knowatoa/ai-visibility-skills --list`.

This is also how the skills show up on [skills.sh](https://skills.sh). There is no submit form. The directory indexes public GitHub repos from `npx skills add` telemetry, so the first install is what creates the listing.

**Claude.ai or ChatGPT:** open [skills/podcast-prep/SKILL.md](skills/podcast-prep/SKILL.md), copy the contents, and paste it into a project's instructions (in Claude.ai you can also add it as a skill in settings).

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

Found a way to improve a skill? PRs and issues welcome. New skills belong at `skills/<skill-name>/SKILL.md` with the frontmatter above.
 
## License
 
[MIT](LICENSE). Use these however you want.

Knowatoa is a product of Wafris LLC.
