# graph-model/

This directory contains documentation for the IATI Plus graph model. It explains how humanitarian aid data is represented in the graph, including the major node types, relationship types, identifying properties, modeling conventions, and the design choices that make the graph useful for exploration, analysis, and AI-powered applications.

The `graph-model/` folder should help both human contributors and AI coding assistants understand how source data is translated into a connected property graph. It should make the structure of the graph explicit so contributors can reason about schema changes, ingestion logic, query design, indexing, and model evolution with confidence.

## Purpose

Use this folder to document:

- The conceptual structure of the graph
- Node labels and their meanings
- Relationship types and their meanings
- Required, optional, and derived properties
- Identity and deduplication rules for graph entities
- How source IATI concepts map into graph structures
- Modeling tradeoffs made for traversal, analytics, and AI use cases
- Versioning and evolution rules for the graph model over time

## Scope

This folder focuses on **how the knowledge graph is shaped and interpreted**.

Examples of what belongs here:

- Node and relationship inventories
- Entity-to-entity mapping rules
- Canonical identity strategies for graph entities
- Documentation of labels, properties, and constraints
- Modeling examples that show how real IATI records appear in the graph
- Query-oriented explanations for why certain structures were chosen
- Rules for representing time, provenance, status, geography, and hierarchy in the graph

Examples of what usually belongs elsewhere:

- `../data-model/` for source record semantics before graph transformation
- `../pipeline/` for workflow sequencing and graph load stages
- `../architecture/` for system-wide technical design
- `../runbooks/` for operational instructions and maintenance steps
- `../../src/transform/` and `../../src/neo4j/` for code that implements the model

## What questions this folder should answer

A contributor or coding assistant should be able to use this folder to answer questions such as:

- What are the main node types in the IATI Plus graph?
- What relationships connect activities, organizations, sectors, locations, transactions, and reporting artifacts?
- Which properties are required for each node or relationship type?
- What is treated as an entity, and what is treated as a property?
- How is provenance represented?
- How are historical versions, temporal validity, and snapshot context represented?
- How should new concepts be added without degrading query clarity or graph performance?

## Suggested documents in this folder

As this folder grows, it may contain files such as:

- `overview.md` — A high-level explanation of the graph design and core principles.
- `node-types.md` — Definitions of each node label and its required properties.
- `relationship-types.md` — Definitions of each relationship type and how it should be used.
- `identity-and-deduplication.md` — Rules for stable identifiers, canonical entities, and merges.
- `provenance-model.md` — How source lineage, publishers, snapshots, and evidence are represented.
- `temporal-model.md` — How dates, versions, and change history are expressed in the graph.
- `query-patterns.md` — Common traversal and analysis patterns that the model is designed to support.
- `examples.md` — Small worked examples showing how XML records become connected graph structures.

## Typical graph model concerns

A well-documented graph model for IATI Plus should usually clarify:

1. Which real-world concepts deserve first-class nodes.
2. Which concepts should remain properties rather than separate nodes.
3. How organizations, activities, sectors, locations, and transactions connect.
4. How to represent many-to-many relationships cleanly.
5. How to attach provenance and source references without cluttering the core graph.
6. How to support both operational lookups and analytical traversals.
7. How to evolve the model safely as new use cases emerge.

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for the project mission and context.
2. `../architecture/` for the broader system structure.
3. `../data-model/` to understand source concepts before graph transformation.
4. `overview.md` or the main graph model summary in this folder.
5. `node-types.md` and `relationship-types.md` for detailed model rules.
6. `query-patterns.md` and `examples.md` when building transformations, Cypher queries, or AI features.

## Relationship to implementation

This folder should connect graph design documentation to the code that implements it.

Typical relationships include:

- `../../src/transform/` maps parsed and canonicalized records into graph-ready structures.
- `../../src/neo4j/` creates constraints, indexes, and load/update logic.
- `../../src/diff/` may influence temporal and version-aware graph structures.
- `../../tests/` validates that the implemented graph conforms to the documented model.
- `../pipeline/` explains when and how graph updates are executed during each run.

## Guidance for contributors

- Document the graph from the perspective of both meaning and query behavior.
- Prefer simple, direct structures over unnecessary modeling complexity.
- Explain why a node or relationship exists, not just that it exists.
- Make identity rules explicit whenever duplicate or overlapping entities are possible.
- Add worked examples whenever a modeling rule is subtle or easy to misinterpret.
- Update this folder whenever labels, relationships, constraints, or key traversal patterns change.

## Role in the repository

This folder is the semantic structure layer of the documentation set. It should help contributors and coding assistants understand how IATI Plus turns raw aid data into an intelligible, queryable, and extensible graph that can support search, analysis, reasoning, and new AI applications.
