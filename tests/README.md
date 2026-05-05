# tests/

This directory contains the verification layer for IATI Plus. It is where contributors prove that the ingestion pipeline, XML canonicalization logic, diff engine, graph transformations, Neo4j load processes, and reporting components behave correctly before changes are merged.

The `tests/` folder should be useful to both human contributors and AI coding assistants. It should make expected behavior explicit, capture important edge cases, and provide reusable fixtures that allow the project to be tested repeatedly and safely as the system evolves.

## Purpose

Use this folder to verify:

- XML parsing and canonicalization behavior
- Record extraction and identifier handling
- Snapshot hashing and change detection logic
- Transformation of IATI records into graph-ready structures
- Neo4j load and update behavior
- Error handling, validation, and recovery behavior
- End-to-end pipeline behavior on realistic sample inputs

## Testing principles

- Tests should be easy to run and easy to understand.
- Each test should have a clear purpose and expected result.
- Prefer small, focused tests over large opaque tests.
- Use realistic IATI samples whenever possible.
- Capture edge cases that are likely to recur in production.
- Keep fixtures stable so changes in behavior are intentional and reviewable.

## Subfolders

- `unit/` — Fast tests for individual functions, classes, and small modules.
- `integration/` — Tests that verify multiple components work correctly together, such as parsing plus diffing or transformation plus Neo4j loading.
- `fixtures/` — Stable sample files and expected outputs used by tests, including representative IATI XML examples, malformed files, and expected diff results.

## What belongs here

Examples of appropriate test coverage include:

- Parsing a single `iati-activity` correctly from a source XML file.
- Confirming canonicalization removes formatting noise without changing meaning.
- Verifying that logically identical XML produces identical hashes.
- Detecting create, update, unchanged, and delete cases across two snapshots.
- Confirming graph transformation preserves parent-child relationships from nested XML structures.
- Verifying Neo4j load logic creates or updates nodes and relationships as expected.
- Confirming invalid records are skipped or logged according to project standards.

## Suggested fixture categories

The `fixtures/` folder may eventually include subfolders such as:

- `xml/valid/` — Valid example IATI files and extracted records.
- `xml/invalid/` — Malformed or nonconforming XML samples.
- `canonical/` — Before-and-after canonicalization examples.
- `diff/` — Snapshot pairs and expected change outputs.
- `graph/` — Expected transformed outputs for graph-loading tests.
- `reports/` — Expected summary outputs for reporting tests.

## Guidance for contributors

- Add tests whenever you add or change behavior in `../src/`.
- Add a fixture when a bug, edge case, or ambiguous XML pattern needs to be preserved for future testing.
- Name tests clearly so both humans and AI assistants can infer the scenario being tested.
- Keep expected outputs explicit rather than hidden in complicated helper logic.
- Avoid fragile tests that depend on external services unless they are clearly marked and isolated.

## Relationship to the rest of the repository

- `docs/` explains intended behavior.
- `src/` implements behavior.
- `tests/` verifies behavior.
- `schemas/` helps define what valid structures should look like.
- `config/` and `scripts/` may support test execution in local or cloud environments.

This folder is the main safeguard against regressions and should make correctness visible, repeatable, and reviewable.
