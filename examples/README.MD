# examples/

This directory contains illustrative examples for IATI Plus. It is intended to help contributors, researchers, and AI coding assistants quickly understand how the system is supposed to behave by showing concrete sample inputs, outputs, prompts, query patterns, and workflow demonstrations.

The `examples/` folder should make the project easier to learn. Instead of only describing concepts in abstract terms, this directory should show representative examples of how IATI XML is parsed, how changes are detected, how records are transformed for graph loading, and how the resulting graph or APIs may be queried.

## Purpose

Use this folder to provide:

- Example inputs and outputs for major pipeline stages
- Sample prompts for AI-assisted coding or documentation tasks
- Example graph queries and expected results
- Demonstrations of canonicalization, diffing, and graph loading behavior
- Small end-to-end walkthroughs that help new contributors understand the system

## Design principles

- Keep examples small, focused, and easy to understand.
- Prefer realistic examples over toy placeholders when possible.
- Make each example self-explanatory with a short note about what it shows.
- Keep examples aligned with the current implementation and documentation.
- Use examples to clarify edge cases and expected behavior.

## Suggested subfolders

- `xml/` — Example IATI XML files, extracted activity snippets, and before-or-after canonicalization examples.
- `diffs/` — Snapshot comparison examples that show create, update, unchanged, and delete scenarios.
- `graph/` — Example node and relationship outputs, graph-ready CSV layouts, or visualization-friendly samples.
- `queries/` — Sample Cypher, XPath, and XQuery queries with brief notes about expected results.
- `prompts/` — Example prompts contributors can use with AI coding assistants for common project tasks.
- `workflows/` — End-to-end examples showing how a task flows through multiple stages of the system.

## What belongs here

Examples of appropriate content include:

- A small XML activity and its canonicalized form.
- A pair of daily snapshots showing how a single activity change is detected.
- A sample change-event record generated from a diff.
- Example graph import files for a tiny activity-to-organization network.
- A Cypher query that returns the version history of an activity.
- A prompt template for generating a parser, validator, or transformation module.
- A mini walkthrough that demonstrates how a raw XML file becomes graph-ready output.

## What should not live here

The following usually belong elsewhere:

- Production fixtures used by automated tests, which should live in `../tests/fixtures/`.
- Long design explanations, which should live in `../docs/`.
- Core implementation code, which should live in `../src/`.
- Sensitive or proprietary data, which should never be committed.

## Guidance for contributors

- Add examples when a concept is difficult to explain with prose alone.
- Update examples when the implementation or data contracts change.
- Keep filenames descriptive so humans and AI assistants can infer what each example demonstrates.
- Prefer a few excellent examples over a large pile of unlabeled samples.
- Include short notes or companion markdown files when an example needs context.

## Relationship to the rest of the repository

- `docs/` explains how the system should work.
- `src/` implements that behavior.
- `tests/` verifies correctness.
- `examples/` makes expected behavior easier to understand and reuse.
- `schemas/` helps define the shapes that many examples should follow.

This folder should help contributors learn the project faster and give coding assistants concrete reference material for generating better code and documentation.
