---
name: visibility-gate
description: "Checks whether the brand can be retrieved at all before anyone measures what models say. Harvests the fan-out queries a model actually searches, then checks Google, Bing, and Brave plus index coverage. Use when the user says check the gate, are we even in the index, harvest fan-out queries, do we rank for the queries models search, check Bing Brave and Google for retrieval, or a model does not read the web when it answers. Do NOT load for daily share of voice, writing pages or atoms, SEO audits that are not about retrieval, keyword research with no fan-out, or measuring answers as if retrieval were already proven."
---

# Visibility gate

Before measuring what models say, check whether you can be retrieved at all. A model rewrites a prompt into three to six shorter search queries, runs those against a conventional index, and picks from what comes back. ChatGPT leans on Bing, Gemini on Google, Claude on Brave. If you do not rank in that index for those queries, nothing downstream can work. The walk-away is a gate file. Chat is the verdict, not the SERP dump.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it for the brand name only. If it is missing, do not interview.
2. Find the entities. If they pointed at a `*-cite-for.md` or `cite-for.md`, read **Entities** from it. A stranger can write the same shape by hand: one to five specific frames, plus who types the query. If they named the entities in chat, use those. If more than one cite-for file matches, ask which one. If there are no entities and they will not name any, stop — see Refuse.
3. If they already pointed at a cite-for file or folder, write the gate file next to it. If not, ask where files should live (default: the directory that holds the cite-for file, or the current directory) in the same message as any missing Inputs. Do not ask the directory first and the entities second.
4. Write `<brand-slug>-gate.md` in the same turn as any missing-input questions. Name it from the cite-for file: `foo-cite-for.md` → `foo-gate.md`. If there is no cite-for file, slug the brand (`acme-gate.md`) or use `gate.md`. Do not wait for Webmaster access to create the stub.
5. Fill **Prompts** with five to ten realistic buyer prompts, grounding on, written from the entities and the buyer role. These are the prompts you will run, or the ones they already ran.
6. Fill **Fan-out**. For each prompt, record the three to six searches the model actually ran. Most tools expose them. If you cannot see the searches, ask them to paste. Do not invent fan-out queries from the prompt text. The prompt is not the query.
7. For each distinct fan-out query, fill **Positions**: brand rank on Google, Bing, and Brave, or `not present`. Brave is required. If you can run the searches, do. If they pasted SERPs, use those. Do not invent a rank. A missing engine goes in Gaps, not as a guessed position.
8. Fill **Coverage** from Search Console and Bing Webmaster Tools if they provided it: indexed, excluded, duplicate, missing sitemap, wrong canonical. If they have no access, write that in Gaps and keep going. Do not invent coverage.
9. Write **Verdict**. `pass` only when the brand appears on at least one fan-out query in at least one of the three indexes. `fail` when it ranks nowhere for the harvested queries. `blocked` when you have prompts but no real fan-out and no positions. Fail means a ranking problem. Do not start measuring, building, or placing.
10. Set `status: ready` when Verdict is filled from real fan-out and positions, or when Verdict is `blocked` and Gaps say exactly what is missing. In chat: path + verdict + the queries you are on or missing from. Do not paste the file.

## Working files

```markdown
---
status: in-progress
brand: "<company>"
cite-for: "<path or unset>"
resume: "<exact next step a cold session should do>"
---

# Gate — <brand>

## Entities
## Prompts
## Fan-out
## Positions
## Coverage
## Verdict
## Gaps
```

`status` is `in-progress` until Verdict is set from evidence or from a named hole; then `ready`. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts (brand, entities, file path, prompts already written, fan-out already pasted, positions already recorded).

Verdict and Positions are skimmer zones. No SEO lecture. Missing access belongs in Gaps.

## Inputs

Need one to five entities and a buyer role. The usual file is `<brand-slug>-cite-for.md` next to where they want the gate file.

From the user's message (ask only if missing and it would make the verdict wrong), in one batch:

1. The entities, if they did not point at a cite-for file and did not name them.
2. Where to write, if no cite-for file already anchors the directory (default: current directory).
3. Fan-out searches the model actually ran, if they already have a grounding run.
4. Search Console or Bing Webmaster coverage, if they have it.

Do not ask for keyword tools, a full SEO audit, or daily share of voice. Do not crawl the rest of the repo. Do not fetch "whatever else seems useful."

If you can search Google, Bing, or Brave for a harvested query, do that instead of asking them to. Still do not invent a rank for an engine you did not search.

## Refuse

Stop in a few sentences if there are no entities and they will not name any, or if they want a different job: daily share of voice or a research pass, writing pages or atoms, a general SEO audit with no fan-out, keyword research that skips what the model searched, or measuring answers as if retrieval were already proven. Do not half-run those. Do not skip the gate to be helpful.
