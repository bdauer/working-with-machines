---
title: Article Drafting
parent: Skills
nav_order: 3
---

# Article Drafting

Draft articles from raw input — samples, ideas or single pieces to expand. Handles mode selection, structural planning, voice calibration against author samples, assumption tracking and internal editorial review before presenting the draft.

This skill is personalized to the author's workflow, including employer IP filtering and voice calibration against specific writing samples. It is published as a demonstration of what a personalized drafting skill looks like. Use the [personalize](personalize.md) skill to adapt it to your own voice, editorial standards and publication context.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/article-drafting)
{: .btn }

## When to use

- **Drafting from multiple samples** — several pieces of writing that need to be synthesized into a single article
- **Developing an idea through conversation** — the author has a concept but hasn't written it out yet
- **Expanding a fragment** — a single piece of writing that needs to become a full article

## When not to use

- Reference documentation, method pages or other non-article content
- Editing an existing published article (use editorial review directly)

## How it works

1. **Mode selection** — determine the starting point: synthesis (multiple samples), conversation (unwritten idea) or expansion (single fragment)
2. **Input processing** — map threads across samples, draw out the idea through questions, or identify gaps in the fragment. Capture raw phrases as potential blockquote material.
3. **Structure** — propose sections, ordering and where the author's raw voice fits. Iterate until approved.
4. **Draft** — write against the approved structure with voice calibrated from samples. Track assumptions (author intent, audience knowledge, connections drawn, gaps filled).
5. **Internal review** — run editorial review against the draft before presenting. Integrate findings, flag items needing author judgment.
6. **Present** — deliver the draft with assumption report, structure reference and inline flags
7. **Iterate** — author feedback can loop back to any phase

## What it assumes

- **Editorial guide and voice samples** — `.editorial-guide.md` and `.voice-samples.md` in the project root for voice calibration
- **Editorial review skill** — invoked internally for pre-presentation review
- **Employer IP awareness** — scans input for proprietary content and generalizes before drafting (personalization point: adapt to your own IP boundaries)
