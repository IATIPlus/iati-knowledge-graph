# src/

This directory contains the application source code for IATI Plus. It is the implementation layer of the project: the code here downloads IATI data, parses and canonicalizes XML, detects daily changes, transforms records into graph-ready structures, loads data into Neo4j, and generates reports and operational outputs.

The `src/` folder should be understandable to both human contributors and AI coding assistants. Each subfolder should have a focused responsibility, a local `README.md`, and code that matches the architecture and standards documented in `../docs/`.

## Purpose

Use this folder to implement:

- Daily snapshot ingestion from IATI sources
- XML parsing and canonicalization
- Record hashing and snapshot comparison
- Change detection and diff generation
- Transformation from XML records into graph-ready structures
- Neo4j load and update logic
- Shared internal utilities and support code
- Reporting, validation summaries, and operational outputs

## Design principles

- Organize code by pipeline responsibility.
- Keep modules small and focused.
- Prefer explicit names over generic names like `utils` when a more specific name is possible.
- Keep business logic separate from orchestration code.
- Align implementation with the contracts and workflows defined in `../docs/` and `../schemas/`.
- Add tests for new behavior in `../tests/`.

## Subfolders

- `ingest/` — Download daily IATI source files, create manifests, verify integrity, and register snapshots.
- `canonicalize/` — Parse XML, extract top-level records such as activities, and generate canonical forms for stable comparison.
- `diff/` — Compute hashes, compare records across snapshots, classify creates or updates or deletes, and generate change artifacts.
- `transform/` — Convert parsed and versioned records into structures suitable for graph loading, analysis, or export.
- `neo4j/` — Create and update nodes, relationships, version records, and change-event structures in the graph database.
- `reports/` — Generate summaries, validation reports, quality metrics, and operational outputs for maintainers and researchers.
- `common/` — Shared internal helpers such as logging, configuration access, path handling, identifiers, and reusable low-level utilities.

## Expected folder pattern

Each major subfolder should ideally include:

- `README.md` — What this part of the code is responsible for.
- Implementation modules — The actual code files.
- Optional subfolders for domain-specific components when the module grows.
- Clear imports and boundaries so contributors can understand where to place new code.

## Suggested reading order

Before editing code in this folder, contributors and coding assistants should usually read:

1. `../ABOUT.md` for the project overview.
2. `../docs/architecture/` for system context.
3. `../docs/pipeline/` for workflow logic.
4. `../docs/data-model/` and `../docs/graph-model/` for structure and graph design.
5. The local `README.md` in the subfolder being edited.

## Guidance for contributors

- Put code in the most specific folder that matches its responsibility.
- Avoid mixing parsing logic, diff logic, graph logic, and deployment logic in the same module.
- Document assumptions when handling ambiguous IATI structures or edge cases.
- Keep side effects explicit, especially when writing files, updating Neo4j, or interacting with cloud services.
- Make code easy to test with small inputs and predictable outputs.

## Relationship to the rest of the repository

- `docs/` explains what the code should do.
- `src/` contains the code that does it.
- `tests/` verifies that the code behaves correctly.
- `schemas/` defines external and internal structure expectations.
- `config/` provides configuration templates.
- `scripts/` helps run, set up, or maintain the system.

This folder is the core implementation surface of the repository and should remain closely aligned with the documented architecture.
