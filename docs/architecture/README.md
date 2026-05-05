# architecture/

This directory contains the high-level system architecture documentation for IATI Plus. It explains how the major parts of the platform fit together, what responsibilities belong to each subsystem, how data moves through the system, and what technical boundaries contributors should preserve as the project evolves.

The `architecture/` folder is intended for both human contributors and AI coding assistants. It should provide enough context for someone to understand the overall design before working on implementation details in `../../src/` or workflow details in neighboring documentation folders.

## Purpose

Use this folder to document:

- The overall system architecture of IATI Plus
- Major platform components and their responsibilities
- Data flow across storage, processing, diffing, graph loading, and query layers
- Boundaries between archive, processing, and serving systems
- External systems and integration points such as AWS S3 and Neo4j
- Reliability, scalability, and architectural tradeoffs
- Diagrams and narratives that help new contributors understand the whole system

## Scope

This folder should focus on **system-level design**, not line-by-line implementation detail.

Examples of what belongs here:

- Architecture overviews
- System context diagrams
- Component interaction diagrams
- Deployment and environment topology
- Data flow diagrams
- Explanations of subsystem boundaries and responsibilities

Examples of what usually belongs elsewhere:

- `../pipeline/` for step-by-step processing workflows
- `../data-model/` for entity definitions and XML-to-record structure
- `../graph-model/` for node, relationship, and temporal graph design
- `../standards/` for coding conventions and engineering rules
- `../decisions/` for formal ADRs documenting specific architectural choices

## What questions this folder should answer

A good reader should be able to use this folder to answer questions such as:

- What are the major subsystems of IATI Plus?
- How does daily IATI XML move from raw snapshot storage into a versioned graph?
- What responsibilities belong to the archive layer, processing layer, and graph layer?
- How do components communicate with one another?
- What external services does the platform depend on?
- What architectural constraints should contributors preserve?
- Where should a new feature or component logically belong?

## Suggested documents in this folder

As this folder grows, it may contain files such as:

- `system-overview.md` — A high-level explanation of the complete platform.
- `component-map.md` — The main subsystems and their boundaries.
- `data-flow.md` — End-to-end movement of data across the platform.
- `deployment-topology.md` — Infrastructure layout across storage, compute, and graph services.
- `query-architecture.md` — How graph queries, XML access, and API layers fit together.
- `reliability-and-scale.md` — Capacity, fault tolerance, and operational design considerations.

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for the project mission and high-level overview.
2. `system-overview.md` or the main overview document in this folder.
3. `component-map.md` and `data-flow.md` for structure and movement through the system.
4. `../pipeline/` for process details.
5. `../data-model/` and `../graph-model/` for data and graph structure.
6. `../decisions/` for important architectural rationale.

## Relationship to implementation

This folder should help contributors map architecture to code without replacing code-level documentation.

Typical relationships include:

- Architecture documents describe **what subsystems exist**.
- `../../src/` contains the code that implements those subsystems.
- `../../tests/` verifies that those implementations behave correctly.
- `../runbooks/` explains how operators use and maintain the architecture in practice.

## Guidance for contributors

- Write for someone who needs to understand the whole system before changing part of it.
- Prefer diagrams plus concise explanation over long, unstructured prose.
- Update architecture docs when subsystem boundaries, infrastructure patterns, or data flow change.
- Keep architecture documents stable and conceptual; move implementation detail to more specific folders.
- Use this folder to prevent confusion about where responsibilities begin and end.

## Role in the repository

This folder is the system-design layer of the documentation set. It should help both volunteers and coding assistants see the full shape of IATI Plus before they work on a specific parser, diff engine, graph loader, or infrastructure task.
