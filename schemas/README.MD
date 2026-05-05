# schemas/

This directory contains the structural contracts used by IATI Plus. It defines the external standards the project consumes and the internal schemas the project produces or relies on during processing, validation, transformation, and graph loading.

The `schemas/` folder should help both human contributors and AI coding assistants understand what shapes of data are expected, what versions of standards are in use, and how compatibility should be managed as the project evolves.

## Purpose

Use this folder to store and document:

- Official IATI schemas and related reference files
- Internal schemas for intermediate or output data structures
- JSON schemas, CSV layouts, or similar machine-readable contracts
- Versioned definitions for records exchanged between project components
- Validation rules that help keep pipeline behavior stable and predictable

## Why this folder matters

This project depends on stable data contracts. The XML being ingested must be interpreted against known IATI structures, and internal outputs such as parsed records, change-event payloads, graph import files, and reports should follow documented formats so that downstream code remains reliable.

Keeping these definitions in one place helps contributors avoid ambiguity and gives coding assistants a clear source of truth for what inputs and outputs should look like.

## Subfolders

- `iati/` — Official IATI schemas, versions, and supporting reference files used for validation and interpretation of source XML.
- `internal/` — Project-specific schemas for parsed records, canonical forms, change events, graph-ready files, reports, and other internal data contracts.

## What belongs in `iati/`

Examples include:

- Official IATI XSD files by version
- Schema bundles used for validation
- Reference files or notes about how specific versions are used in the project
- Documentation about known quirks, assumptions, or compatibility considerations for IATI schema handling

## What belongs in `internal/`

Examples include:

- JSON schemas for parsed activity records
- Schemas for canonicalized activity representations
- Contracts for change-event or diff outputs
- CSV column definitions for Neo4j import files
- Validation schemas for reports or intermediate pipeline artifacts
- Versioned definitions of internal exchange formats between modules

## Schema management principles

- Keep schemas versioned when formats may evolve.
- Prefer machine-readable formats wherever possible.
- Document breaking changes clearly.
- Keep internal schemas aligned with the implementation in `../src/` and the explanations in `../docs/`.
- Use schema definitions to support testing, validation, and CI checks whenever practical.

## Guidance for contributors

- Add or update a schema when you introduce a new structured input or output.
- Do not silently change field names, required fields, or types without documenting the change.
- When an internal format changes, update the corresponding tests and relevant documentation.
- If a schema has multiple versions, make the active and deprecated versions explicit.
- Use this folder as the source of truth for data shape, not scattered assumptions in code comments.

## Relationship to the rest of the repository

- `docs/` explains why the contracts exist and how they are used.
- `src/` reads from and writes to structures governed by these schemas.
- `tests/` uses schemas to verify correctness and compatibility.
- `schemas/` defines the structural expectations that keep the pipeline consistent.

This folder should remain the canonical home for data contracts used across the project.
