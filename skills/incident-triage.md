---
title: Incident Triage
parent: Skills
nav_order: 6
---

# Incident Triage

Structured investigation of production incidents using parallel subagents. Classifies the problem first, then selectively queries only the monitoring and infrastructure tools relevant to that problem type.

This skill separates generic orchestration logic from environment-specific configuration. The SKILL.md provides the investigation framework; the reference files are templates to populate with your own infrastructure details, diagnostic sequences and known failure patterns.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/incident-triage)
{: .btn }

## When to use

- **Production incident with multiple possible causes** — the symptom could be application code, infrastructure, a recent deploy or a data integrity problem, and the investigation needs to be directed efficiently
- **Reducing investigation cost** — querying every monitoring tool for every incident wastes tokens and attention. Classification-first routing queries only relevant sources.

## When not to use

- Known, recurring issues with established fixes (a runbook is more appropriate)
- Incidents where the cause is already identified and the need is remediation, not investigation

## How it works

1. **Classify** — categorize the problem into one of six types (app-error, performance, queue-backlog, deploy-failure, infra-down, data-issue) based on input signals before making any tool calls
2. **Extract diagnostic signals** — pull workarounds, scope markers and version references from the report as hypotheses to prioritize investigation
3. **Load context** — read the resource map and the triage file for the classified type
4. **Investigate** — spawn parallel subagents for primary resources, each with focused investigation steps and safety instructions. Check for recent deployments across all types.
5. **Verify causality** — apply the triage file's decision tree: timestamp ordering, symptom-vs-cause distinction, single-source confidence cap
6. **Escalate if needed** — query secondary sources only if primary findings warrant it. If evidence points to a different problem type, escalate once with cycle prevention.
7. **Output** — structured report with assessment, evidence, alternatives, falsification checks and proposed solutions

## What it assumes

- **Monitoring tools accessible via MCP or CLI** — error tracking, log aggregation, infrastructure metrics, database access. The skill is tool-agnostic; specific tools are configured in the triage template files.
- **Local codebase access** — for the code investigation conditional, application and infrastructure repos should be checked out locally

## Setup

Before using this skill, populate the template reference files with your infrastructure details:

- **`references/resource-map.md`** — environments, database constraints, service baselines, local repo paths
- **`references/triage-*.md`** (one per incident type) — which monitoring tools to query, investigation steps for subagents, causality decision trees, known failure patterns specific to your system
