# data-model/

This directory contains the conceptual and structural data model documentation for IATI Plus. It explains what the core entities are, how they are identified, how they relate to one another, and how source IATI XML structures are interpreted before they are transformed into graph-ready representations.

The `data-model/` folder should help both human contributors and AI coding assistants understand the shape of the data before they work on parsing, canonicalization, change detection, transformation, or graph loading. It is the place to document the meaning of the data, not just its storage format.

## Purpose

Use this folder to document:

- Core IATI entities and their meanings
- Stable identifiers and key fields
- How XML structures map to internal records
- Parent-child relationships in nested IATI data
- Assumptions used when interpreting ambiguous or irregular source data
- Internal record structures used before graph loading
- Data semantics that should remain consistent across the pipeline

## Scope

This folder focuses on **data structure and meaning**.

Examples of what belongs here:

- Definitions of activities, organizations, transactions, sectors, locations, and other core entities
- Explanations of identifiers such as `iati-identifier` and other keys used for matching or deduplication
- XML-to-record mapping documentation
- Rules for representing nested structures in intermediate forms
- Notes about field interpretation, normalization, and entity boundaries

Examples of what usually belongs elsewhere:

- `../architecture/` for system-wide component design
- `../pipeline/` for processing workflow steps
- `../graph-model/` for Neo4j-specific node and relationship design
- `../schemas/` for formal machine-readable structural contracts in the repository root
- `../decisions/` for ADRs documenting major modeling choices

## What questions this folder should answer

A contributor or coding assistant should be able to use this folder to answer questions such as:

- What are the primary entities represented in IATI Plus?
- Which identifiers are stable enough to use across snapshots?
- How should nested XML structures be interpreted before transformation?
- What fields belong to an activity versus a transaction versus an organization?
- How should repeated elements, optional elements, and extensions be handled conceptually?
- What internal record shapes are expected before graph loading begins?

## Suggested documents in this folder

As this folder grows, it may contain files such as:

- `entities.md` — Definitions of major entities and their meanings.
- `identifiers.md` — Stable keys, matching logic, and identifier rules.
- `xml-mapping.md` — How IATI XML structures map into internal records.
- `nested-structures.md` — Treatment of parent-child and repeated XML elements.
- `normalization-rules.md` — Data interpretation and normalization conventions.
- `extensions-and-edge-cases.md` — Handling of namespaces, extensions, and irregular publisher data.

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for project context.
2. `../architecture/` for overall system design.
3. `entities.md` and `identifiers.md` in this folder.
4. `xml-mapping.md` and `nested-structures.md` for representation details.
5. `../pipeline/` for how these data structures move through processing.
6. `../graph-model/` for how the interpreted data is represented in Neo4j.

## Relationship to implementation

This folder should help contributors connect the meaning of the data to the code that handles it.

Typical relationships include:

- `../../src/canonicalize/` uses these definitions to interpret XML records correctly.
- `../../src/diff/` relies on stable identifiers and normalized record meaning.
- `../../src/transform/` converts these conceptual records into graph-ready structures.
- `../../src/neo4j/` maps the interpreted records into nodes, relationships, versions, and events.
- `../../tests/fixtures/` should include examples that reflect the modeling rules described here.

## Guidance for contributors

- Write clearly enough that a new volunteer can understand the data without reverse-engineering code.
- Document the meaning of fields and structures, not just their names.
- Make assumptions explicit when the source XML is ambiguous, inconsistent, or publisher-specific.
- Update this folder when a change affects entity interpretation, identifiers, or XML-to-record mapping.
- Keep conceptual modeling here and move graph-specific modeling detail to `../graph-model/`.

## Role in the repository

This folder is the semantic interpretation layer of the documentation set. It should explain what the project believes the data means and how that meaning is preserved as IATI XML is parsed, normalized, compared, and transformed into a versioned knowledge graph.
