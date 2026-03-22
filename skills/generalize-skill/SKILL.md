---
name: generalize-skill
description: >-
  Prepare a skill for sharing by removing personal and proprietary content.
  Two modes: internal (portability within an organization — decouple from personal
  setup, no IP review needed) and public (full IP review before publishing externally).
  Use when asked to "generalize this skill", "make this shareable", "prepare for
  publishing", or when moving a skill from personal use to team or public use.
user-invocable: true
argument-hint: "<path to skill directory> [--mode internal|public]"
---

# Generalize Skill

Prepare a skill for sharing. Complement to personalize-skill — personalize-skill adapts a skill to your workflow; generalize-skill prepares your skill for others.

## Modes

**Internal** — portable within an organization. Remove personal tool preferences, hardcoded paths, local conventions. No IP review.

**Public** — external publication. Full IP review with independent agents. Infrastructure details templated. Proprietary reasoning generalized to industry-standard practice.

Default to **internal** unless the user specifies public or mentions publishing externally, sharing on a site, or open-sourcing.

## Process

### Phase 1: Analyze

Read the entire skill directory. Produce a **generalization map** classifying every element:

- **Structural** — workflow phases, decision points, anti-patterns, output structure. Preserved in both modes.
- **Personal** — author's tool preferences, file paths, naming conventions, team terminology, reviewer perspectives tuned to a specific codebase. Addressed in both modes.
- **Proprietary** — infrastructure identifiers, database schemas, diagnostic sequences encoding incident history, thresholds tied to specific systems, architecture-revealing combinations. Addressed in public mode only.

For each personal/proprietary element: note the file, what it is, what action is needed (remove, generalize, template, or flag).

**Generalize-in-place vs collapse-to-template.** For each file with proprietary content, decide:
- **Generalize in place** when the structural reasoning stands on its own with placeholders substituted. The diagnostic logic is clear even with "[your table here]" replacing specific table names.
- **Collapse to template** when the file's value IS the specific details and the remaining structural skeleton would be incoherent without them. If >70% of a file is proprietary and removing it leaves disconnected fragments, replace the entire file with a template describing what to populate.

**Earned competence expressed through proprietary examples.** Some content (causality trees, investigation steps, failure pattern lists) encodes professional competence using specific infrastructure as examples. If the competence can be expressed using only public technology references (database engine features, standard APIs, published frameworks), preserve it with specifics replaced by generic references. If it requires knowledge of the specific system's architecture to make sense, template it.

**File naming.** If file names contain environment-specific or organizational suffixes (e.g., `resource-map.core.md`), rename to generic equivalents and update all internal references.

### Phase 2: Present the map

Show the classification grouped by action:

1. **Will generalize** — elements with clear generic equivalents
2. **Will template** — elements needing adopter-provided values
3. **Will preserve** — structural elements unchanged
4. **Needs discussion** — uncertain classification or context-dependent

Wait for confirmation before proceeding.

### Phase 3: IP review (public mode only)

Skip for internal mode.

Spawn two parallel independent sub-agents following the process in `shared/ip-review-brief.md`:

- **Content reviewer** — line-by-line review for identifiers, schemas, thresholds, diagnostic sequences, security details, tool specificity, template shape
- **Architecture revelation reviewer** — document-level review for combinatorial identification, workflow fingerprinting, template structure, implied failure history

Each agent reads `shared/ip-review-brief.md` for its full brief, then reviews the skill files independently. Neither agent sees the other's findings.

After both complete, reconcile: merge findings, group by severity (must-fix, should-fix, acceptable), present to user. User has final approval.

### Phase 4: Generalize

Apply confirmed changes:

**Personal elements (both modes):**
- Tool references → generic categories or parameterized values
- Hardcoded paths → relative paths or documented conventions
- Personal reviewer perspectives → neutral defaults, noted as customization points
- Author-specific conventions → removed or noted as examples

**Proprietary elements (public mode only):**
- Infrastructure config → template files describing what to populate and expected structure
- Diagnostic sequences → generalized to industry-standard practice. Remove branches that only make sense given specific architecture; note as customization points.
- Tool combinations → individual generic references
- Thresholds → removed or replaced with "[configure per environment]"

**Output templates:** Example values in output structures (e.g., `ECS running 4/4, CPU 23%`) may reveal infrastructure shape. Replace with generic descriptions (`[source] <what was checked, what normal looks like>`).

**Preserve in all cases:**
- Workflow phase structure and ordering
- Anti-patterns and tool-agnostic guidelines
- Specificity of reviewer briefs, checklists, decision criteria — earned competence, not proprietary knowledge
- Output structure and format requirements (with example values generalized per above)

### Phase 5: Review (sub-agent)

Spawn a review sub-agent with a fresh perspective. The reviewing agent has not seen the generalization map or the author's decisions — it evaluates the output on its own merits.

Brief for the review agent:

```
You are reviewing a skill that has been generalized for [internal/public] sharing.
Read the entire skill directory. Check:

1. Coherence — do phases connect? Do later phases reference output from earlier phases correctly?
2. Residue — any personal tool names, hardcoded paths, team-specific terminology remaining?
3. Usefulness — is the skill still specific enough to be useful? Over-generalization strips value.
   "Use your issue tracker" everywhere is less useful than demonstrating a concrete integration.
4. [Public only] Proprietary residue — infrastructure identifiers, architecture-revealing
   combinations, diagnostic sequences encoding specific incident history?
5. [Public only] Template quality — do templates describe what to populate without implying
   specific counts, topologies, or shapes?

Report findings with file, location, what's wrong, and suggested fix.
```

Integrate findings. Flag judgment calls for the user.

### Phase 6: Deliver

Write the generalized skill to the user's specified location.

Summary:
- What was generalized and why (grouped by category)
- What was preserved
- Templates created (public mode) with setup instructions
- Any remaining flags

For public mode: the skill should not be committed until the user has reviewed and approved.

## Principles

### Generalization is lossy — be intentional about what's lost

Some specificity is personal or proprietary. But some is *earned competence* — reviewer checklists, edge case handling, industry-standard diagnostic sequences. Preserve earned competence. Strip personal and proprietary.

### Templates describe, they don't scaffold

Say what information is needed and why. Don't provide empty rows or numbered slots implying a specific shape. Templates should also explain how the orchestrator uses the populated content, so adopters can write content that integrates correctly. If the main SKILL.md says "each triage file specifies primary vs conditional resources," the template should explain what those categories mean and how they're used.

### The audience determines the mode

Internal: colleagues share employer context. Remove personal preferences.
Public: practitioners elsewhere. Remove personal preferences *and* proprietary details.

## Dependencies

- **`shared/ip-review-brief.md`** — required for public mode IP review. Located in the skills repository's `shared/` directory, or at `~/.claude/skills/shared/ip-review-brief.md` for standalone use.
