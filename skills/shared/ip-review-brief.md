# IP Review Brief

> Standing reference for independent IP review agents. Read this before
> reviewing any skill files for proprietary content.

## Context

Skills published on workingwithmachines.dev may originate from workflows
developed during employment. Before any skill content is committed to the
public repository, independent agents review it for proprietary content.
The author has final approval before anything is committed.

## Review structure

Two parallel reviewers, each with a distinct focus:

### Reviewer 1: Content reviewer

Read each file line by line. Flag:

- **Infrastructure identifiers** — cluster names, database identifiers,
  log group paths, queue names, service URLs, IAM role names, account IDs
- **Database schemas** — table names, column names, relationship structures
- **System-specific thresholds** — connection counts, baseline metrics,
  timeout values tied to specific infrastructure
- **Diagnostic sequences encoding incident history** — causality decision
  trees, known-pattern lists, or triage steps that reflect specific failure
  modes encountered at a specific organization rather than general
  diagnostic practice
- **Security-sensitive operational details** — how audit trails can be
  bypassed, specific vulnerability patterns, internal security architecture
- **Tool name specificity** — specific commercial tool names where a
  generic category ("error tracking service," "container orchestrator")
  would be equally clear. Individual widely-used tool names (PostgreSQL,
  Redis) are acceptable; combinations that identify a stack are not.
- **Template shape assumptions** — empty table rows, numbered placeholder
  slots, or structural scaffolding that implies a specific count or
  topology (e.g., exactly two repos, exactly four environments, exactly
  three primary resources)

For each finding: file, line range, what's flagged, why it's a concern,
recommended action (remove, generalize, or accept with justification).

**Report assumptions made** — places where you assumed something was
generic but could be wrong ("I assumed the six incident types are
industry-standard, but the specific combination might be identifying"),
or assumed something was proprietary but it might be standard practice.

### Reviewer 2: Architecture revelation reviewer

Read all files as a unit. Ignore individual names (assume those are
already caught by Reviewer 1). Instead ask: does the *combination* of
details — framework choices, queue topology, deployment patterns, failure
mode categories, the structure of the triage files, the shape of
templates — reveal enough to identify a specific organization?

Check for:

- **Combinatorial identification** — any three details that, taken
  together, would let someone familiar with the industry narrow down
  the employer. Each detail alone may be generic.
- **Workflow shape as fingerprint** — does the classification taxonomy,
  precedence ordering, or escalation logic reflect a specific
  architecture rather than general practice?
- **Template structure revealing architecture** — do the templates assume
  a deployment topology, monitoring stack, or service architecture that
  is specific rather than generic?
- **Implied failure history** — do edge cases, exceptions, or special
  handling in the workflow suggest the author encountered specific
  incidents? ("Data correctness override" suggests data issues were
  misclassified enough to warrant a special rule.)

For each finding: what combination of details is concerning, what it
reveals, and recommended action.

**Report assumptions made** — what architectural knowledge you're
bringing to the assessment, and where a different evaluator might
reach a different conclusion.

## The test

For each element: could a competent practitioner who has never seen the
author's internal systems independently arrive at this from published
industry resources (Google SRE book, PagerDuty incident response docs,
NIST SP 800-61, general SRE/DevOps community knowledge)? If yes, it's
general professional knowledge. If no, it encodes specific operational
experience and should be excluded or generalized.

## Findings format

Group findings by severity:

- **Must-fix** — clearly proprietary content, infrastructure identifiers,
  architecture-revealing combinations
- **Should-fix** — content that's borderline or could be generalized
  further without reducing utility
- **Acceptable** — flagged for transparency but assessed as safe.
  Include reasoning.
