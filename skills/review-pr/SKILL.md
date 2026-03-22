---
name: review-pr
description: >-

  Comprehensive PR review combining narrative impact analysis with code-level review.
  Produces a written analysis covering what changed, why it matters, how it fits into
  ongoing work, correctness issues, edge cases, and recommended actions. Frontloads
  clarifying questions, gathers all sources in parallel, drafts analysis with parallel
  code reviewers, runs a tech writer review agent, integrates feedback, and delivers.
  Use when asked to "review this PR", "analyze this PR", "summarize this PR",
  "what does this PR do", or given a GitHub PR URL with a request to understand it.
user-invocable: true
argument-hint: "<PR URL or repo/number> [optional focus areas]"
---

# PR Review

Comprehensive PR review: narrative impact analysis plus code-level correctness review.

## Process

### Phase 1: Clarify (before any research)

Ask all applicable questions in a single message:

1. **Knowledge gaps** — "Areas touched by this PR where you'd like extra explanation?" Tailor depth to stated gaps.
2. **Cross-references** — "Tickets, epics, or initiatives to compare against? Other repos whose code is affected?"
3. **Usage paths** — "How do you and the team interact with the code this PR changes? (e.g., VS Code, CLI, CI, scripts)" Ensures analysis covers all relevant workflows, not just the PR author's assumed path.
4. **Focus** — "Anything specific to watch for? (security, performance, breaking changes, alignment with a plan)"
5. **Output** — "Markdown file with Mermaid charts, or inline? Length constraint?"

Skip questions the user's prompt already answers. After the user responds, confirm the plan in one sentence before starting research.

### Phase 2: Gather (parallel, no analysis yet)

Fetch all sources in parallel:

- **PR metadata** — `gh pr view <number> --repo <owner/repo> --json title,body,files,additions,deletions,author,baseRefName,headRefName,commits`
- **PR diff** — `gh pr diff <number> --repo <owner/repo>`
- **Cross-reference repos** — read relevant files from other repos the user identified
- **Issue tracker tickets** — fetch each ticket via available tooling (Jira MCP, `gh issue view`, Linear CLI, etc.); for initiatives/epics, also fetch children
- **Local codebase context** — read files the PR modifies (the *before* state)

Do NOT analyze during this phase. Collect all raw material first.

### Phase 3: Draft

Write to `pr-<number>-analysis.md` in the repo root.

#### Required sections

1. **What This PR Does (Plain English)** — conceptual explanation using analogies for knowledge-gap areas. Lead with the *problem*, then the approach. State which usage paths are affected.

2. **Key Changes, Explained** — group by theme, not by file. For each:
   - **Before / After**
   - **Key files to read** — specific files + line ranges + *why*
   - **Why this matters** — connect to cross-references and ongoing work
   - Impact across usage paths integrated inline (no separate CLI/GUI/CI section)

3. **Impact on cross-referenced work** — if tickets/epics provided. For each: how the PR affects it (accelerates, blocks, complicates, no impact). Table for >3 items. Mermaid chart only if 3+ cross-refs with non-trivial relationships — include only nodes the PR directly affects; caption explains scope.

4. **Comparison** — if comparing against another repo/reference. Table format. Add "where defined" column when config-layer distinction matters.

5. **What to Read Closely** — 2-5 files, prioritized. Lead with "if you read only N things."

6. **Recommended Actions** — 3-5 concrete steps. Always actionable.

7. **Summary** — 2-3 sentences framing the PR relative to ongoing work.

#### Guidelines

- Explain jargon on first use within stated knowledge gaps. Don't explain what they already know.
- Distinguish "what the PR does" vs. "what it doesn't do" vs. "what it enables."
- Flag regressions prominently — if the PR moves opposite to a stated goal in cross-referenced work, call it out (not buried in a table cell).
- When relevant (e.g., Docker, IaC), note which changes apply universally vs. only through specific tooling. State this distinction once when introducing it and once in the comparison table — no more.

### Phase 4: Review (parallel)

Spawn these reviewers as parallel agents. Each reads the PR diff and relevant source files directly.

#### 4a. Code reviewers

Spin up 2-3 parallel code review agents, each with a focused brief. Select from:

**Correctness reviewer:**
```
Review the PR diff for bugs, logic errors, edge cases, off-by-one errors, null/undefined handling,
race conditions, and incorrect assumptions about data or state. Read the before-state of modified
files for context. For each finding: file, line range, what's wrong, severity (bug/edge case/nit),
and a concrete fix suggestion. Report findings only.
```

**Security reviewer** (when the PR touches auth, permissions, user input, network config, credentials, or infrastructure):
```
Review the PR diff for security issues: injection vectors, credential exposure, permission
escalation, insecure defaults, missing validation at system boundaries. Check for OWASP top 10
categories relevant to the changes. For each finding: file, line range, the vulnerability class,
severity, and remediation. Report findings only.
```

**Design reviewer** (when the PR introduces new patterns, APIs, or architectural changes):
```
Review the PR diff for design issues: leaky abstractions, coupling introduced, inconsistency
with existing patterns in the codebase, missing error handling at integration boundaries,
naming that will confuse future readers. Read surrounding code for context on existing patterns.
For each finding: file, line range, the concern, and an alternative. Report findings only.
```

**Refactoring reviewer** (always include):
```
Review the PR diff with the perspective: leave the campsite better than you found it. Look for
nearby opportunities the PR author was in a position to improve but didn't. Dead code adjacent
to changes, inconsistent naming in the same file, duplicated logic that the PR adds a third
instance of, TODOs that the PR's changes now resolve, test coverage gaps for the new code paths.
Only flag opportunities that are low-risk and directly adjacent to the PR's changes — not
sweeping refactors. For each finding: file, line range, the opportunity, effort level
(trivial/small/medium), and what the improvement would look like. Report findings only.
```

Select reviewers based on what the PR touches. Always include the correctness and refactoring reviewers. Add security and design reviewers when the changes warrant them.

#### 4b. Tech writer reviewer

Spawn in parallel with the code reviewers. Reviews the draft analysis document (not the PR diff):

```
You are a technical writer reviewing a document. The reader is [audience description from Phase 1].

Read [file path] and review for:
1. Clarity for stated audience — jargon explained? analogies helpful?
2. Structure — can the reader skip to sections they care about?
3. Framing accuracy — clearly distinguishes does/doesn't do/enables?
4. Actionability — does the reader know what to do after reading?
5. Density — anything redundant or missing?
6. Charts — helpful or confusing?

Return specific, actionable feedback. Quote relevant text. Focus on substantive issues.
```

### Phase 5: Integrate and deliver

Consolidate all reviewer findings:

1. Integrate tech writer feedback into the draft (fix contradictions, missing explanations, buried findings, structural improvements; skip pure style preferences).
2. Add a **Code Review Findings** section to the analysis document, after "Key Changes, Explained." Group by severity (bugs, edge cases, security, design, nits). Include file, line range, the issue, and recommended fix for each.
3. Update **Recommended Actions** to include any high-severity code findings.

Share the final file path and a bullet summary covering both the impact analysis and code review findings.

## Anti-patterns

- Don't analyze inline in the conversation — always write to a file.
- Don't start analyzing before all sources are gathered.
- Don't create separate "CLI impact" sections — integrate across usage paths inline.
- Don't include unaffected nodes in Mermaid charts.
- Don't restate layer distinctions (compose vs. devcontainer, etc.) more than twice.
