---
name: visibility-cite
description: "Picks one to five entities a model should name the brand for. Entities are specific frames, not themes or keyword clusters. Use when the user says what should we be cited for, name the entities we want models to recommend, pick our citation frames, or what do we want to show up for in ChatGPT. Do NOT load for measuring what models say, checking whether you rank or harvesting fan-out queries, writing comparison pages or atoms, SEO keyword clustering, or general brand positioning with no citation target."
---

# Visibility cite

Pick one to five entities you want a model to name you for. Not themes. Not keyword clusters. The specific frames a buyer types when they start looking. Get this wrong and everything downstream optimizes toward a phrase nobody types. The walk-away is a file. Chat is the entity list, not the research.

## Do this job

1. Load brand context. Check `.agents/brand-context.md`, then `.claude/brand-context.md`. If it exists, read it. Use it for the company name, the one-line pitch, and any frames already declared. Do not treat a category label in that file as an entity.
2. If they already pointed at a folder or an existing cite-for file, use that directory. If not, ask where files should live (default: the current directory) in the same message as any missing Inputs or brand questions. Do not ask the directory first and the brand second.
3. Write `<brand-slug>-cite-for.md` as soon as the brand has a name, in the same turn as any missing-input questions. If the brand is unnamed, use `cite-for.md`. Do not wait for Search Console or call notes to create the stub. Sessions die. The file is the memory.
4. Fill **Sources** before locking **Entities**. Work the three sources in this order. A later source does not override an earlier one when they disagree; the earlier source wins and the later phrase goes in Rejected or Gaps.
5. Propose one to five entities. Each entity is a frame a person would type, not a market category. Reject "coaching software," "AI visibility," "the category we compete in." Accept "alternative to TrainingPeaks" or "coach-owned plans, not AI-written plans" when that is the language buyers use. Each locked entity must quote or paraphrase a line from Sources. If Customer language, Search Console, and titles/H1s are all Gaps, do not propose entities from the pitch. Leave Entities empty, keep `status: in-progress`, and put the ask in `resume`. If you have more than five candidates, cut to the ones the sources actually support. Do not pad to five.
6. Write **Rejected** for every theme, cluster, or category you threw out, and why. If you cannot name a reject, you have not been strict enough.
7. Set `status: ready` when a cold reader could write a retrieval prompt from the entity list without guessing the frame. In chat: path + the entities + one line on which source carried the most weight. Do not paste the file.

## Working files

```markdown
---
status: in-progress
brand: "<company>"
buyer: "<role who types the query, or unknown>"
resume: "<exact next step a cold session should do>"
---

# Cite for — <brand>

## Entities
## Sources
### Customer language
### Search Console
### Site titles and H1s
## Rejected
## Gaps
```

`status` is `in-progress` until Entities has one to five locked frames; then `ready`. `resume` is the only progress pointer. Do not also keep a Status heading in the body.

If the file already exists, read it, honor `resume`, and do not re-ask settled facts (brand, buyer, file path, sources already captured, entities already locked, rejects already listed).

Entities and Rejected are skimmer zones. No research diary. Source notes stay under Sources. Mush and missing access go in Gaps.

## Sources

Collect in this order. Ask only if the source would change the entity list and you do not have it. Do not invent customer language, queries, or H1s.

1. **Customer language.** The words buyers use when they describe the moment they started looking. Call notes, interview quotes, support tickets, the user's own recap. This is the heaviest source. If they have files, read those. Do not go hunting a CRM.
2. **Search Console queries.** Impressions you already get, brand name filtered out. If they paste a query list or export, use it. If they do not have access, note it in Gaps and keep going. Do not invent impression counts.
3. **Site titles and H1s.** What the site already declared it is about. If they gave a URL, fetch the homepage and the obvious product or comparison URLs they named. Do not crawl the whole site. If they pasted titles, use those.

If two sources conflict, keep the customer language and put the other phrase in Rejected.

## Inputs

From the user's message (ask only if missing and it would make the entity list wrong), in one batch:

1. What is the company called, and who is the person who types the query?
2. Any customer-call language, quotes, or notes about the moment they started looking.
3. A Search Console query list with the brand filtered out, if they have one.
4. The site URL, or the titles and H1s they already use.

File location is asked once, in the same batch, when the path is unset.

If brand context is missing, add these to that same batch, then write `.agents/brand-context.md`:

1. What's your current company, and how do you describe it in one sentence?
2. What did you build before this that comes up in conversation?
3. What are 2-3 stories you tell well, with real numbers attached?
4. What's one opinion you hold that most people in your space disagree with?

Do not ask for competitor lists, keyword tools, or a target number of entities. Do not fetch extra market research.

## Refuse

Stop in a few sentences if there is no brand and they will not name one, if they will not give any buyer language, query list, or site titles/URL, or if they want a different job: measuring what models say, checking rank or harvesting fan-out queries, writing comparison pages or atoms, clustering keywords, or brand positioning with no citation target. Do not half-run those. Do not turn a category label into an entity to be helpful.
