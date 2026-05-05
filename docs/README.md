# docs/

This directory contains the project knowledge base for IATI Plus. It is written for both human contributors and AI coding assistants so they can understand the purpose, architecture, standards, workflows, and design decisions behind the project before generating or modifying code.

The `docs/` folder should explain **what the system is**, **how it is supposed to work**, **why key decisions were made**, and **where to look next**. In general, contributors should read the relevant documentation here before working in `src/`, `tests/`, `schemas/`, or cloud infrastructure.

## Purpose

Use this folder to document:

- Project architecture and system design
- Data models and XML-to-graph mappings
- Daily ingestion, canonicalization, diffing, and graph update workflows
- Neo4j graph modeling and temporal versioning strategy
- Standards, conventions, and coding expectations
- Architectural decisions and rationale
- Operational runbooks and setup instructions
- Prompt templates and guidance for AI-assisted development

## Audience

This folder is intended for:

- Student volunteers learning the project
- Maintainers coordinating the build
- Researchers trying to understand the system
- AI coding assistants that need project context before generating code

## Subfolders

- `architecture/` — High-level system design, component boundaries, data flow, and infrastructure patterns.
- `data-model/` — Definitions of core entities, identifiers, XML structures, and graph mappings.
- `pipeline/` — Documentation for ingestion, canonicalization, hashing, diffing, transformation, and update workflows.
- `graph-model/` — Neo4j schema, node and relationship design, temporal versioning rules, and query patterns.
- `standards/` — Coding conventions, naming rules, validation expectations, logging patterns, and quality standards.
- `decisions/` — Architectural Decision Records (ADRs) documenting important technical choices and tradeoffs.
- `runbooks/` — Operational procedures for setup, deployment, maintenance, troubleshooting, and recovery.
- `prompts/` — Reusable prompts and prompt-writing guidance for AI-assisted coding and documentation tasks.

## Suggested reading order

A new contributor or coding assistant should usually start with:

1. `../ABOUT.md` for a high-level overview of IATI Plus.
2. `architecture/` for system context.
3. `pipeline/` and `data-model/` for implementation understanding.
4. `graph-model/` for how IATI is represented in Neo4j.
5. `standards/` and `decisions/` before writing or changing code.
6. `runbooks/` when setting up infrastructure or operating the system.
7. `prompts/` when using AI coding assistants to implement tasks.

## Guidance for contributors

- Keep documents focused and specific.
- Prefer short files with clear headings over long unstructured notes.
- Update documentation whenever the system design, workflow, or assumptions change.
- Record important decisions in `decisions/` instead of leaving them only in issues or chat threads.
- Write with enough clarity that a new volunteer or coding assistant can understand the folder without additional context.

## Relationship to the rest of the repository

- `docs/` explains the system.
- `src/` implements the system.
- `tests/` verifies the system.
- `schemas/` defines external and internal data contracts.
- `config/` and `scripts/` help operate the system.

This folder should remain the main source of truth for project intent, design, and operating guidance.
