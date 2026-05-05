# scripts/

This directory contains operational and helper scripts for IATI Plus. These scripts support setup, maintenance, automation, environment preparation, one-off repair tasks, and other repeatable operational work that should not be embedded directly inside the main application modules.

The `scripts/` folder should be understandable to both human contributors and AI coding assistants. Each script should have a clear purpose, predictable inputs and outputs, and enough documentation that it can be used safely without guessing what it will do.

## Purpose

Use this folder for:

- Environment setup helpers
- Local development bootstrap scripts
- Cloud provisioning helpers
- Data migration or repair scripts
- Utility scripts for validation, cleanup, or maintenance
- Batch execution wrappers for common workflows
- One-time or infrequently used operational tasks that do not belong in the core application packages

## Design principles

- Keep scripts focused on a single operational job.
- Prefer idempotent behavior when practical.
- Make side effects explicit.
- Require clear parameters rather than hidden assumptions.
- Avoid placing core business logic here when it belongs in `../src/`.
- Document prerequisites, expected environment variables, and risks.

## Suggested subfolders

- `setup/` — Scripts for local environment setup, dependency installation, bootstrap steps, and initial project configuration.
- `infra/` — Helpers for cloud resources, storage setup, permissions, provisioning support, and deployment-related tasks.
- `maintenance/` — Cleanup, repair, migration, backfill, and other support tasks used during operations.
- `validation/` — Command-line helpers for checking configuration, schemas, manifests, outputs, or environment readiness.
- `dev/` — Convenience scripts for local development workflows, test runs, formatting, or repeated contributor tasks.

## What belongs here

Examples of appropriate scripts include:

- A script that creates expected local folders and environment templates.
- A helper that prepares S3 prefixes or checks bucket configuration.
- A backfill script that reprocesses historical snapshots.
- A validation script that confirms required schemas or config files exist.
- A maintenance script that removes stale temporary outputs or regenerates derived artifacts.
- A wrapper script that runs a common local development workflow in the correct order.

## What should not live here

The following usually belong elsewhere:

- Core parsing, canonicalization, diffing, or graph logic, which should live in `../src/`.
- Test cases, which should live in `../tests/`.
- Configuration templates, which should live in `../config/`.
- Long-form explanations, which should live in `../docs/`.

## Guidance for contributors

- Add a local `README.md` inside any subfolder that grows beyond a few scripts.
- Give scripts descriptive names that say what they do.
- Include usage examples at the top of the script or in the subfolder README.
- Note whether a script is safe to rerun.
- Mark scripts clearly if they are destructive, experimental, or one-time use.
- When a script becomes stable and central to the system, consider moving its logic into `../src/` and keeping only a thin execution wrapper here.

## Relationship to the rest of the repository

- `docs/` explains operational intent and procedures.
- `src/` contains core application logic.
- `scripts/` helps run, support, validate, or maintain that logic.
- `config/` provides the templates and settings many scripts depend on.
- `tests/` verifies behavior when scripts call into tested components.

This folder should make repeated operational tasks safer, clearer, and easier to automate.
