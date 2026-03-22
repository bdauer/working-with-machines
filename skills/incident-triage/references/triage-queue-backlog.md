# Triage: Queue Backlog — Template

> Populate this file with your investigation steps for queue-backlog incidents.
> The incident triage skill reads this file when a problem is classified
> as `queue-backlog`.

## Resource Selection

List your monitoring and infrastructure tools. For each, mark as
primary (always query), conditional (query if triggered), or skip.
The orchestrator spawns parallel subagents for primary resources and
waits for all to complete before evaluating conditional triggers.

## Subagent Steps

For each primary resource, describe the investigation steps a subagent
should follow. Include: what to query, what to look for, how to filter
results. Create a subsection per resource. Each subagent runs
independently and reports raw findings without diagnosing root cause.

## Conditional Triggers

Describe when to query conditional resources and what to look for.
Conditions should reference specific findings from primary resources.
The orchestrator evaluates these only after all primary subagents
complete, since triggers may depend on combined results.

## Causality Decision Tree

List diagnostic patterns the orchestrator uses to reason about cause.
For each pattern, describe: the finding (what the evidence looks like),
the likely cause, how to confirm or rule it out, and the confidence
level if confirmed. The orchestrator evaluates ALL patterns — it does
not stop at the first match. It reports all and assesses which explains
the most evidence, using timestamp ordering as the primary signal.

## Known Patterns

Document recurring failure patterns specific to your system that the
subagent should recognize immediately. These short-circuit investigation
when a known signature is found.
