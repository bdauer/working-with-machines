# Resource Map — Template

> Populate this file with your infrastructure details. The incident triage
> skill reads this file at the start of every investigation.

## Environments

List each environment with its region, container cluster, database
identifier and log location. Include all environments the skill may
need to investigate.

## Database Constraints

- **Query timeout:** configured statement timeout
- **Connection limit:** max connections for the readonly/investigation user
- **High-volume tables:** tables that require date or scope filters to
  avoid timeouts, with approximate row counts

## Service Baselines

Document normal-state metrics for comparison during investigation:
active database connections, container health (expected count, CPU/memory
baseline), queue depth per queue type.

## Repos

List local repos the code investigation subagent should search, with
the path, framework and what each contains.
