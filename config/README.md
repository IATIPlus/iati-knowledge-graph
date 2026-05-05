# config/

This directory contains configuration templates and environment-specific settings guidance for IATI Plus. It is the place where contributors define how the system connects to services, chooses runtime options, and controls operational behavior without hardcoding those settings directly into application code.

The `config/` folder should help both human contributors and AI coding assistants understand what settings the project expects, which values are safe to commit, and how configuration should be separated from secrets.

## Purpose

Use this folder to store:

- Configuration templates for local development and deployment
- Environment-specific example settings files
- Sample connection settings for services such as AWS and Neo4j
- Pipeline runtime options such as batch size, retry policies, timeouts, and paths
- Documentation of required environment variables and configuration conventions

## Design principles

- Keep secrets out of version control.
- Commit templates and examples, not live credentials.
- Prefer explicit configuration over hidden defaults.
- Make environment-specific differences visible and documented.
- Keep configuration separate from business logic in `../src/`.
- Ensure configuration names are stable and descriptive.

## Suggested subfolders

- `templates/` — Safe example configuration files that contributors can copy and adapt for local or deployed environments.
- `environments/` — Environment-specific non-secret settings patterns, such as local, development, staging, or production examples.
- `services/` — Configuration references for external services such as AWS, Neo4j, storage paths, or queue settings.
- `pipeline/` — Settings related to ingestion, parsing, diffing, transformation, reporting, and operational scheduling.

## What belongs here

Examples of appropriate files include:

- `.env.example` or equivalent non-secret environment templates.
- Example YAML, TOML, JSON, or INI configuration files.
- Non-secret Neo4j connection templates.
- Sample AWS profile or bucket-structure configuration examples.
- Pipeline configuration templates that define tunable runtime parameters.
- Documentation that explains expected variables and allowed values.

## What should not live here

The following should not be committed here:

- Real API keys, passwords, tokens, certificates, or private keys.
- Machine-specific files that only make sense on one contributor's system.
- Business logic that belongs in `../src/`.
- Long operational instructions that belong in `../docs/runbooks/`.

## Guidance for contributors

- Add templates, not secrets.
- Use clear names such as `.env.example`, `neo4j.local.example.yml`, or `pipeline.defaults.example.toml`.
- Document required fields and expected value formats.
- Update this folder when new services, environment variables, or runtime options are introduced.
- Keep committed examples aligned with what the code in `../src/` actually expects.
- Reflect configuration changes in tests or validation scripts when appropriate.

## Relationship to the rest of the repository

- `docs/` explains how configuration is used and how environments should be set up.
- `src/` consumes configuration values at runtime.
- `scripts/` may read from configuration templates during setup or maintenance tasks.
- `tests/` may use test-specific configuration or examples derived from this folder.
- `config/` should remain the safe, documented home for committed configuration patterns.

This folder should make environment setup clearer, safer, and more reproducible for both volunteers and automated tools.
