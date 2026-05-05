# pipeline/

This directory contains workflow documentation for the IATI Plus processing pipeline. It explains how daily IATI data moves through the system step by step, from snapshot acquisition to canonicalization, change detection, transformation, graph loading, reporting, and operational validation.

The `pipeline/` folder should help both human contributors and AI coding assistants understand how the platform behaves as a sequence of processing stages. It should make the order of operations, the purpose of each stage, the inputs and outputs of each step, and the expected handoffs between components easy to understand.

## Purpose

Use this folder to document:

- The end-to-end daily processing workflow
- Stage-by-stage responsibilities in the pipeline
- Inputs, outputs, and side effects of each pipeline phase
- Dependencies and handoffs between stages
- Validation, retry, error-handling, and recovery expectations
- Scheduling, orchestration, and operational workflow patterns
- How raw IATI XML becomes archived data, change artifacts, and graph updates

## Scope

This folder focuses on **process flow and execution sequence**.

Examples of what belongs here:

- Ingestion workflow documentation
- Canonicalization and record extraction workflow descriptions
- Hashing and diff generation flow
- Transformation and graph load sequence documentation
- Daily run lifecycle documents
- Failure handling and reprocessing workflow descriptions
- Pipeline dependency and orchestration diagrams

Examples of what usually belongs elsewhere:

- `../architecture/` for high-level system structure
- `../data-model/` for the meaning of entities and record structures
- `../graph-model/` for Neo4j node and relationship design
- `../runbooks/` for operator procedures and incident response steps
- `../../src/` for the code that implements each stage

## What questions this folder should answer

A contributor or coding assistant should be able to use this folder to answer questions such as:

- What are the major stages of the daily IATI Plus workflow?
- In what order do stages run?
- What data enters and leaves each stage?
- Where are snapshots archived, where are diffs produced, and where are graph-ready outputs created?
- What happens when a stage fails?
- Which steps are safe to rerun, and which require caution?
- What conditions must be satisfied before data is loaded into Neo4j?

## Suggested documents in this folder

As this folder grows, it may contain files such as:

- `daily-run-overview.md` — A high-level walkthrough of the full daily processing cycle.
- `ingestion-workflow.md` — How source XML is discovered, downloaded, verified, and archived.
- `canonicalization-workflow.md` — How XML records are extracted and converted into stable canonical forms.
- `diff-workflow.md` — How hashes, comparisons, and change-event outputs are generated.
- `transform-workflow.md` — How parsed records are converted into graph-ready structures.
- `graph-load-workflow.md` — How current and historical graph updates are applied.
- `reprocessing-and-recovery.md` — How failed or historical runs are re-executed safely.
- `validation-checkpoints.md` — What must be checked before and after major stages.

## Typical pipeline stages

A typical IATI Plus daily workflow may include:

1. Acquire and archive the latest IATI snapshot.
2. Validate file presence, metadata, and integrity.
3. Parse XML and extract top-level records.
4. Canonicalize records for stable comparison.
5. Compute hashes and compare against the prior snapshot.
6. Generate change events and change summaries.
7. Transform records into graph-ready outputs.
8. Load or update the versioned Neo4j graph.
9. Generate reports, metrics, and validation outputs.
10. Record run metadata for audit and recovery.

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for overall project context.
2. `../architecture/` for system-level understanding.
3. `daily-run-overview.md` or equivalent overview in this folder.
4. The specific workflow document for the stage being modified.
5. `../data-model/` and `../graph-model/` when the pipeline step depends on record semantics or graph structure.
6. `../runbooks/` when operating or troubleshooting the workflow.

## Relationship to implementation

This folder should connect documented workflow stages to the code that implements them.

Typical relationships include:

- `../../src/ingest/` implements ingestion-related stages.
- `../../src/canonicalize/` implements parsing and canonicalization steps.
- `../../src/diff/` implements comparison and change-generation steps.
- `../../src/transform/` prepares graph-ready outputs.
- `../../src/neo4j/` applies updates to the graph.
- `../../src/reports/` generates summaries and quality outputs.
- `../../tests/` verifies stage behavior and end-to-end flow.

## Guidance for contributors

- Write workflows in the order they execute.
- Make stage boundaries explicit.
- Document inputs, outputs, dependencies, and failure conditions clearly.
- Call out which steps are idempotent and which are not.
- Update this folder when a stage is added, removed, reordered, or given a new responsibility.
- Keep operational procedures here at the workflow level; move step-by-step operator instructions to `../runbooks/`.

## Role in the repository

This folder is the process-execution layer of the documentation set. It should help contributors and coding assistants understand not only what the system is, but how it runs each day to turn raw IATI XML into a versioned archive, a change ledger, and a live knowledge graph.
