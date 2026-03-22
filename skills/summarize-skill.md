---
title: Summarize Skill
parent: Skills
nav_order: 5
---

# Summarize Skill

Generate a human-readable summary page for a Claude Code skill. Reads the skill directory, produces a Jekyll page following the site's skill summary voice and structure, including a GitHub download link.

This skill is personalized to the Working With Machines site structure (Jekyll frontmatter, GitHub repo path, editorial voice). It is published as a demonstration of what a personalized operational skill looks like. Use the [personalize](personalize.md) skill to adapt it to your own site, repo and editorial conventions.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/summarize-skill)
{: .btn }

## When to use

- **Publishing a skill to the site** — a new skill needs a summary page for human readers
- **Updating a summary after skill changes** — the skill evolved and the summary page is stale

## When not to use

- Writing SKILL.md itself (that's the skill author's job)
- Reviewing or editing existing summary pages (use editorial review)

## How it works

1. **Read the skill** — SKILL.md plus any references, scripts and assets
2. **Generate the summary** — one paragraph on what it does, when to use / not use, how it works (phases only, not implementation) and what it assumes (specific tools and integrations)
3. **Handle personal skills** — if the skill is tailored to a specific author's workflow, note this and frame it as a starting point for personalization
4. **Write the page** — Jekyll frontmatter, GitHub link, structured sections

## What it assumes

- **Site repo structure** — skills live in `skills/<name>/` with summary pages at `skills/<name>.md`
- **GitHub repo** — `bdauer/working-with-machines` on the `main` branch for download links
- **Jekyll** — summary pages use Jekyll frontmatter with `parent: Skills`
- **Editorial guide** — skill summary voice rules in `.editorial-guide.md`
