# IATI Plus high-level project outline

IATI Plus is organized as an automated daily pipeline with two connected parts: data aggregation and knowledge graph population. The project uses DigitalOcean for compute, workspace, orchestration, and object storage through Spaces, and it uses Neo4j AuraDB as the managed graph database for the live knowledge graph.

## Two-part workflow

### Part 1: Data aggregation

The first part of the project acquires and normalizes the daily IATI source snapshot. Each day, the pipeline downloads the IATI Bulk Download ZIP from the Bulk Data Service, stores the ZIP as the immutable raw acquisition artifact, unzips it, and inventories the extracted folder structure for downstream processing.

The extracted corpus is organized by reporting organisation, and each publisher folder may contain an organisation XML file plus one or more activity XML files. Organisation files follow the organisation standard and activity files follow the activity standard; activity files may contain multiple nested `iati-activity` records, so the pipeline must treat individual records rather than whole files as the main comparison unit.

At a high level, the aggregation workflow should:

- Download the latest daily bulk ZIP.
- Archive the ZIP and acquisition metadata.
- Unzip the snapshot into working storage.
- Inventory reporting-organisation folders and XML files.
- Parse organisation files and activity files separately.
- Split activity files into individual activity records.
- Canonicalize organisation and activity XML records.
- Generate stable record identifiers and hashes.
- Compare the current snapshot to the previous snapshot.
- Produce a structured daily change ledger.

The output of Part 1 is a set of normalized organization records, normalized activity records, daily manifests, record hashes, and structured change events that describe what changed from one day to the next.

### Part 2: Knowledge graph population

The second part of the project consumes the canonical records and daily change outputs from Part 1 and uses them to populate and maintain the knowledge graph in Neo4j AuraDB.

At a high level, the graph workflow should:

- Transform organization records into graph entities.
- Transform activity records into graph entities.
- Build relationships between organizations, activities, sectors, locations, transactions, and related entities described by the source XML.
- Attach provenance metadata so graph content can be traced back to the source snapshot, publisher folder, XML file, and pipeline run.
- Generate graph-ready load artifacts.
- Apply initial loads or incremental daily updates to Neo4j AuraDB.
- Validate graph integrity after each update cycle.
- Publish daily reports describing updates, anomalies, and validation results.

The output of Part 2 is a continuously updated knowledge graph together with operational reports and supporting graph-load artifacts.

### Daily automation

The project is intended to run as a recurring automated workflow so the graph remains current without requiring full manual intervention.

At a high level, the automation layer should run the following sequence every day:

1. Download the latest IATI bulk ZIP.
2. Archive the raw snapshot.
3. Unpack and inventory the extracted files.
4. Parse and canonicalize organization and activity records.
5. Compute hashes and generate change events.
6. Transform records into graph-ready structures.
7. Apply updates to Neo4j AuraDB.
8. Validate outputs and publish run reports.
9. Record enough metadata to support retries, debugging, and recovery.

## Data storage spaces

The project should use a set of DigitalOcean Spaces buckets that separate raw acquisitions, extracted working data, normalized records, daily diffs, graph-ready artifacts, and operational outputs. Separating storage by zone helps with retention, access control, and cleanup policy design.

| Space | Purpose | Typical contents |
|---|---|---|
| `iati-plus-{env}-raw-snapshots` | Immutable landing zone for source acquisitions | Daily bulk ZIP files, source URL metadata, download checksums |
| `iati-plus-{env}-unpacked-xml` | Extracted working copy of each daily snapshot | Reporting-organisation folders, organization XML files, activity XML files, extraction manifests |
| `iati-plus-{env}-manifests` | Inventory and tracking metadata | Snapshot manifests, file inventories, publisher listings, record counts, validation summaries |
| `iati-plus-{env}-canonical-records` | Normalized record-level storage | Canonical organization records, canonical activity records, record hashes |
| `iati-plus-{env}-change-ledger` | Structured record-level change outputs | Added, changed, and deleted records, diff payloads, change summaries |
| `iati-plus-{env}-graph-loads` | Graph-ready exports | Node files, relationship files, Cypher batches, load manifests |
| `iati-plus-{env}-reports` | Human-readable and machine-readable reports | Daily run reports, anomaly reports, validation outputs |
| `iati-plus-{env}-archive` | Longer-term retention | Older retained snapshots, retired outputs, historical packages |

A smaller first version could begin with the raw snapshot, unpacked XML, canonical records, change ledger, and graph-load Spaces, then add dedicated manifest, reporting, and archive Spaces as operations mature.

## Storage naming conventions

DigitalOcean bucket names should be globally unique, use lowercase letters, numbers, and dashes, and stay within the platform naming rules, so a simple predictable naming pattern is important.

A practical pattern is:

- `iati-plus-{env}-raw-snapshots`
- `iati-plus-{env}-unpacked-xml`
- `iati-plus-{env}-manifests`
- `iati-plus-{env}-canonical-records`
- `iati-plus-{env}-change-ledger`
- `iati-plus-{env}-graph-loads`
- `iati-plus-{env}-reports`
- `iati-plus-{env}-archive`

In this pattern, `{env}` should be replaced with an environment label such as `dev`, `staging`, or `prod` so environments remain isolated and easier to manage.

Within each Space, object paths should be date-partitioned and prefix-based so large collections of files remain understandable and efficient to list. A good pattern is `snapshots/2026/05/05/bulk-download.zip` or `canonical/2026/05/05/activities/{publisher}/{record_id}.xml`.

## Code layout and high-level file names

The codebase should mirror the two-part workflow plus the daily automation layer.

A high-level code layout could include the following modules:

| File or module | Role |
|---|---|
| `src/ingest/download_bulk_zip.py` | Download the daily IATI bulk ZIP |
| `src/ingest/archive_snapshot.py` | Store the raw ZIP and acquisition metadata |
| `src/ingest/unpack_snapshot.py` | Unzip the snapshot into working storage |
| `src/ingest/build_manifest.py` | Inventory extracted files and publisher folders |
| `src/parse/parse_organisation_files.py` | Parse organization XML files |
| `src/parse/parse_activity_files.py` | Parse activity XML files and split nested activities |
| `src/normalize/canonicalize_xml.py` | Normalize XML into canonical forms |
| `src/normalize/build_record_keys.py` | Generate stable organization and activity keys |
| `src/diff/hash_records.py` | Compute hashes for canonical records |
| `src/diff/compare_snapshots.py` | Compare current and prior records |
| `src/diff/write_change_ledger.py` | Persist daily added, changed, and deleted records |
| `src/graph/transform_to_graph.py` | Transform normalized records into graph-ready structures |
| `src/graph/build_graph_load_files.py` | Generate load artifacts for Neo4j AuraDB |
| `src/graph/load_to_neo4j_aura.py` | Apply graph updates to Neo4j AuraDB |
| `src/graph/validate_graph.py` | Run graph integrity and reconciliation checks |
| `src/reports/build_daily_report.py` | Create daily operational summaries |
| `src/orchestration/daily_pipeline.py` | Define the end-to-end daily workflow |
| `src/orchestration/retry_failed_run.py` | Support reruns and failure recovery |
| `src/config/settings.py` | Centralize configuration, endpoints, bucket names, and environment settings |

## Code naming conventions

Use lowercase snake_case file names for Python modules and prefer descriptive verb-based names such as `download_bulk_zip.py` or `compare_snapshots.py` rather than vague names like `processor.py`.

Generated artifacts should also use predictable names and date-based paths. Examples include `manifest.json`, `organization-records.parquet`, `activity-records.parquet`, `change-ledger.jsonl`, `graph-nodes.csv`, `graph-relationships.csv`, and `daily-report.md`, stored under date-partitioned folders in the appropriate DigitalOcean Space.

## Platform baseline

The documentation should assume the following platform model:

- DigitalOcean provides the project workspace, compute environment, automation runtime, and object storage through Spaces.
- DigitalOcean Spaces stores raw snapshots, extracted XML, manifests, canonical records, change artifacts, graph-load packages, and reports.
- Neo4j AuraDB is the managed graph database for the live IATI Plus knowledge graph.

In short, IATI Plus is an automated daily system that downloads the latest IATI bulk snapshot, normalizes organization and activity records, detects changes, prepares graph-ready outputs, and updates a managed Neo4j AuraDB knowledge graph using DigitalOcean as the storage and execution platform.
