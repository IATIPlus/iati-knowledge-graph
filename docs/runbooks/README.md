# runbooks/

This directory contains operational runbooks for the IATI Plus project. It is the place to document repeatable procedures for operating, validating, troubleshooting, recovering, and maintaining the platform so that contributors can perform important tasks safely and consistently.

The `runbooks/` folder should help both human contributors and AI coding assistants understand how to carry out operational tasks in practice. It should translate architecture and pipeline design into concrete step-by-step procedures for common maintenance tasks, routine checks, incident response, recovery actions, and controlled changes.

## Purpose

Use this folder to document:

- Routine operational procedures
- Environment setup and maintenance steps
- Data validation and recovery procedures
- Incident response and troubleshooting workflows
- Safe rerun, rollback, and replay instructions
- Verification steps for ingestion, diffing, and graph loading
- On-call or responder guidance for common failure modes
- Preconditions, permissions, and escalation paths for sensitive tasks

## Scope

This folder focuses on **how to perform important operational tasks step by step**.

Examples of what belongs here:

- Re-running a failed daily pipeline
- Validating snapshot completeness after ingestion
- Recovering from a failed graph load
- Rebuilding indexes or refreshing constraints in Neo4j
- Investigating missing change artifacts
- Verifying object storage contents for a specific run date
- Restoring a known-good state after a bad deployment or load
- Rotating credentials or updating environment configuration with approved procedures

Examples of what usually belongs elsewhere:

- `../pipeline/` for workflow design and stage sequencing
- `../architecture/` for system structure and component descriptions
- `../standards/` for quality rules and operating conventions
- `../decisions/` for why a particular operational strategy was chosen
- `../../src/` for implementation code and automation scripts

## What questions this folder should answer

A contributor or coding assistant should be able to use this folder to answer questions such as:

- How do you safely rerun a failed ingest or graph load?
- What checks should be performed before and after a daily run?
- How do you diagnose common failures in parsing, diffing, or loading?
- What commands, permissions, and environment variables are required for a given task?
- What does successful output look like?
- When should a responder stop and escalate rather than continue?
- How do you recover service safely without damaging data integrity?

## Suggested documents in this folder

As this folder grows, it may contain files such as:

- `daily-operations-checklist.md` — A routine checklist for normal system operation.
- `rerun-failed-pipeline.md` — Step-by-step recovery for a failed daily workflow.
- `validate-ingestion-output.md` — How to confirm that raw snapshots and manifests are correct.
- `investigate-diff-anomalies.md` — How to inspect unexpected change counts or missing artifacts.
- `recover-graph-load.md` — What to do when graph ingestion fails partway through.
- `neo4j-maintenance.md` — Procedures for indexes, constraints, backups, and performance checks.
- `restore-previous-state.md` — How to roll back to a known-good dataset or graph state.
- `credentials-and-access.md` — Approved procedures for handling access-sensitive tasks.
- `incident-escalation.md` — When and how to escalate a problem.

## What a good runbook should include

A strong runbook should usually include:

1. The purpose of the procedure.
2. Preconditions and required permissions.
3. Required tools, systems, and environment variables.
4. Clear step-by-step instructions.
5. Expected outputs or health checks after major steps.
6. Decision points for common failure cases.
7. Stop conditions and escalation guidance.
8. References to related code, dashboards, or documentation.
9. The owner or maintainer of the runbook.

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for project context.
2. `../architecture/` and `../pipeline/` to understand the system being operated.
3. This folder’s `README.md` for runbook conventions.
4. The specific runbook for the task being performed.
5. `../standards/` for operational and safety expectations.
6. `../decisions/` when the rationale behind a procedure matters for troubleshooting or change planning.

## Relationship to implementation

This folder should connect practical procedures to the systems and code they operate.

Typical relationships include:

- `../../src/` contains automation and services referenced by these runbooks.
- `../../tests/` may provide validation commands used during operational checks.
- `../pipeline/` explains the workflow that the runbooks operate and recover.
- `../standards/` defines safety, logging, and quality expectations that procedures should follow.
- Monitoring dashboards, cloud consoles, and Neo4j admin tools may be referenced from the relevant runbooks.

## Guidance for contributors

- Write runbooks so that another contributor can follow them under time pressure.
- Prefer explicit commands, expected outcomes, and branch points over vague prose.
- Document when to stop and escalate.
- Keep procedures close to the code and systems they support, and update them whenever the workflow changes.
- Test runbooks in practice whenever possible; an untested runbook should be treated as incomplete.
- Separate durable operational procedures from background explanation, which belongs in architecture or pipeline docs.

## Role in the repository

This folder is the operations layer of the documentation set. It should help contributors and coding assistants translate system knowledge into reliable action, reduce recovery time during failures, support safe day-to-day operations, and make the platform easier to maintain as it grows.
