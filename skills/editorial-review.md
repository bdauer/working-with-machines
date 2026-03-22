---
title: Editorial Review
parent: Skills
nav_order: 6
---

# Editorial Review

Run parallel editorial reviewers against site content, each with a focused brief and calibrated against the author's actual voice samples. Catches voice drift, structural issues and agentic writing patterns that the drafting agent introduced.

This skill is personalized to the author's editorial guide, voice samples and doc-type system. It is published as a demonstration of what a personalized review skill looks like. Use [personalize-skill](personalize-skill.md) to adapt it to your own editorial standards, voice and content types.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/editorial-review)
{: .btn }

## When to use

- **Reviewing agentically generated content** — content drafted by an agent that needs checking against editorial standards and the author's voice
- **Full-site editorial pass** — reviewing all published pages as a unit for cross-cutting consistency
- **Pre-publication check** — invoked automatically by the article-drafting skill before presenting a draft

## When not to use

- Code review or technical review of non-editorial content
- Reviewing content for a different site or editorial standard (run personalize-skill first)

## How it works

1. **Scope** — determine what to review: specific files, all published pages, recent changes or a draft from article-drafting
2. **Classify** — identify each file's doc type (method/reference, article, background, skill summary) to apply the right voice rules
3. **Parallel review** — spin up focused reviewers:
   - **Voice and tone** — inflation, performed hedging, significance claims, sections that don't sound like the author
   - **Structure and flow** — cross-references, redundancy, absence (concepts that belong but aren't covered), readability
   - **Agentic tics** — triadic lists, contrast constructions, em dash overuse, mechanical rhythm, summative verdicts
   - **Cold reader** (optional) — a senior practitioner reading fresh, reporting where interest dies
4. **Consolidate** — deduplicate findings, group by priority, note disagreements
5. **Feedback loop** — rejected edits reveal calibration gaps; accepted edits confirm what works. Each run sharpens the next.

## What it assumes

- **Editorial guide** — `.editorial-guide.md` defining voice rules, doc types and structure principles
- **Voice samples** — `.voice-samples.md` with the author's actual writing across registers for positive calibration
- **Doc-type system** — files classified by path and frontmatter into voice categories
