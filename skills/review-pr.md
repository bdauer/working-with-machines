---
title: PR Review
parent: Skills
nav_order: 1
---

# PR Review

Comprehensive pull request review combining narrative impact analysis with code-level correctness, security and refactoring review. Produces a written analysis covering what changed, why it matters, how it fits into ongoing work and what to do about it.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/review-pr)
{: .btn }

## When to use

- **Understanding someone else's PR** — the PR touches areas outside your expertise and the diff alone doesn't tell the story
- **Cross-referencing against a roadmap** — assessing how a PR aligns with, accelerates or complicates tickets or initiatives in an issue tracker

## When not to use

- Small, self-contained PRs where the diff tells the whole story

## How it works

1. **Clarify** — ask the user about knowledge gaps, cross-references (tickets, other repos), usage paths and focus areas before starting any research
2. **Gather** — fetch PR metadata, diff, issue tracker tickets, cross-reference repos and the local before-state
3. **Draft** — write a structured analysis to a file, grouping changes by theme with before/after framing, key files to read and impact across usage paths
4. **Review** — parallel reviewers examine the PR and the draft:
   - **Correctness** — bugs, logic errors, edge cases, incorrect assumptions about data or state
   - **Security** — injection vectors, credential exposure, insecure defaults (when the PR touches relevant areas)
   - **Design** — leaky abstractions, coupling, inconsistency with existing patterns (when the PR introduces architectural changes)
   - **Refactoring** — low-risk improvement opportunities adjacent to the PR's changes (dead code, duplication, resolved TODOs, test coverage gaps)
   - **Tech writer** — reviews the draft analysis for clarity, framing accuracy and actionability
5. **Integrate and deliver** — consolidate all findings into the analysis document and share

## What it assumes

- **GitHub CLI (`gh`)** installed and authenticated
- **Issue tracker access** optional but recommended (Jira MCP, GitHub Issues, Linear or similar)
- **Cross-reference repos** checked out locally if comparison across repos is needed
