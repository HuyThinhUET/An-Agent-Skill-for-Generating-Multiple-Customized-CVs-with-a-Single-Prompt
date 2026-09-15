# Project-summary cache

Use `input/projects-information/summary/` as a reusable evidence cache. It reduces repeated reading of large reports, notebooks, and linked materials; it is not a source of new facts.

## Inventory and refresh

Before creating tailored CVs, inventory the project folders and their readable artifacts. Treat a project folder as one project unless its content clearly represents several distinct projects. For each project, create `summary/<project-slug>.md` if none exists.

Reuse a summary only when it identifies its source artifacts and none have changed since the summary was written. Refresh it when a source is newer, a source is missing from its inventory, or the current JD needs a detail the summary cannot support. Do not read large artifacts again merely because a second JD is being processed if the relevant summary is current.

Read artifacts in the least expensive useful order: README and metadata first, then concise reports or repository files, then notebooks or long PDFs only for needed verification. Treat URLs as evidence only after actually opening and inspecting them; a URL's title or path is not proof of a claim.

## Required summary contents

Write summaries in Markdown with these sections:

```markdown
# <project name>

## Sources reviewed
- relative path or URL — artifact type and review date

## Verified CV facts
- Scope, personal role/contribution, methods/technologies, and verified outputs or metrics.

## CV-ready angles
- Short, truthful role-specific bullet candidates, each tied to a source.

## Limits and wording cautions
- Ambiguous ownership, unofficial metrics, missing outcomes, or claims that must not be made.

## Relevance tags
- e.g. ML, backend, data engineering, algorithms, research, teamwork
```

Separate verified facts from interpretations. Preserve qualifiers such as “unofficial”, “prototype”, “team project”, or “second author”. Give exact numeric results only if a source supports them. Do not copy long passages from reports, notebooks, or external material.

## Using the cache in a CV

Use a summary to shortlist projects against the JD. Before making an unusually important, technical, quantified, or potentially ambiguous claim, check the cited source directly. If a summary lacks enough evidence, do not elevate the claim simply for keyword coverage.
