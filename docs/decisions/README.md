# decisions/

This directory contains decision records for the IATI Plus project. It is the place to document important technical, architectural, data, infrastructure, and workflow decisions together with the context, rationale, alternatives considered, and consequences of each choice.

The `decisions/` folder should help both human contributors and AI coding assistants understand not only what the project currently does, but why certain approaches were chosen. It provides historical context that reduces repeated debate, makes tradeoffs visible, and helps future contributors evolve the system with a clear understanding of prior reasoning.

## Purpose

Use this folder to document:

- Significant architecture and infrastructure decisions
- Data storage and processing decisions
- Graph modeling and schema decisions
- Pipeline orchestration and operational decisions
- Tooling and platform choices
- AI-assistant workflow decisions that materially affect the project
- Reversals, supersessions, and deprecations of earlier decisions

## Scope

This folder focuses on **decisions that matter and the reasoning behind them**.

Examples of what belongs here:

- Choosing object storage for raw snapshots
- Choosing a strategy for XML canonicalization and diffing
- Choosing Neo4j constraints, indexing, and load patterns
- Choosing how provenance and temporal history should be represented
- Choosing cloud services, orchestration tools, or deployment boundaries
- Choosing standards for versioned graph updates or replayable runs
- Recording why one design option was accepted over another

Examples of what usually does not belong here:

- `../architecture/` for broad system design descriptions without a single explicit decision record
- `../pipeline/` for step-by-step workflow documentation
- `../graph-model/` for the shape and semantics of the graph itself
- `../standards/` for ongoing rules and conventions
- `../../src/` for implementation details that do not rise to the level of a durable project decision

## What questions this folder should answer

A contributor or coding assistant should be able to use this folder to answer questions such as:

- Why was this architecture or storage approach chosen?
- What alternatives were considered at the time?
- What constraints or decision drivers shaped the final choice?
- What tradeoffs did the project accept?
- Which decisions are still active, and which have been superseded?
- When should an existing decision be revisited?
- How should a new proposal be recorded and reviewed?

## Suggested contents

As this folder grows, it may contain files such as:

- `README.md` — An index explaining the purpose of the folder and how decisions are recorded.
- `template.md` — A standard template for new decision records.
- `001-record-decisions-in-repository.md` — A foundational decision to keep ADR-style records in version control.
- `002-store-raw-iati-snapshots-in-object-storage.md` — A decision about the raw data archive strategy.
- `003-use-record-level-hashing-for-change-detection.md` — A decision about diff generation.
- `004-model-provenance-explicitly-in-the-graph.md` — A decision about graph lineage design.
- `005-use-versioned-graph-loads.md` — A decision about temporal or historical graph behavior.

## Decision record format

Each decision record should usually capture one decision, not several. A useful record will typically include:

1. A short descriptive title.
2. The status, such as proposed, accepted, deprecated, or superseded.
3. The date of the decision or most recent update.
4. The context and problem statement.
5. The decision drivers or evaluation criteria.
6. The options considered.
7. The chosen decision and its rationale.
8. The expected consequences, including both benefits and downsides.
9. Links to related decisions, issues, or implementation documents.

## Naming convention

Use numbered, descriptive filenames so decisions can be read in order and referenced reliably.

Examples:

- `001-record-decisions-in-repository.md`
- `002-use-object-storage-for-raw-snapshots.md`
- `003-use-canonicalized-record-hashes-for-diffs.md`
- `004-represent-provenance-as-first-class-graph-structures.md`

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for the project mission and context.
2. `README.md` in this folder for decision-record conventions.
3. Foundational decisions with the lowest numbers.
4. Recent accepted decisions that affect the area being changed.
5. Related documents in `../architecture/`, `../pipeline/`, `../graph-model/`, and `../standards/` for implementation context.

## Relationship to implementation

This folder should connect reasoning to the parts of the repository that embody each decision.

Typical relationships include:

- `../architecture/` describes the system that results from accepted decisions.
- `../pipeline/` reflects execution choices captured in operational or ingestion-related decisions.
- `../graph-model/` reflects modeling decisions recorded here.
- `../standards/` may formalize recurring practices that originated as earlier decisions.
- `../../src/` and `../../tests/` implement and validate the accepted choices.

## Guidance for contributors

- Create a new decision record when a choice has lasting architectural, operational, data, or workflow impact.
- Record the tradeoffs honestly, including drawbacks.
- Prefer one decision per file.
- Supersede old decisions rather than silently rewriting history.
- Link related decisions together when one depends on or modifies another.
- Keep records concise, but detailed enough that a future contributor can understand the reasoning without reconstructing it from commits.

## Role in the repository

This folder is the reasoning and memory layer of the documentation set. It should help contributors and coding assistants understand the history of important choices, preserve the logic behind major design moves, and make it easier to propose changes in a disciplined and reviewable way.
