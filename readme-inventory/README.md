# README inventory

This document lists the recommended README files for the IATI Plus repository, organized by folder and subfolder.

## Root

- `README.md`
- `ABOUT.md`
- `CONTRIBUTING.md`

## docs/

- `docs/README.md`

### docs/architecture/

- `docs/architecture/README.md`
- `docs/architecture/system-context/README.md`
- `docs/architecture/components/README.md`
- `docs/architecture/storage/README.md`
- `docs/architecture/compute/README.md`
- `docs/architecture/graph-stack/README.md`
- `docs/architecture/integrations/README.md`

### docs/data-model/

- `docs/data-model/README.md`
- `docs/data-model/activities/README.md`
- `docs/data-model/organizations/README.md`
- `docs/data-model/transactions/README.md`
- `docs/data-model/sectors/README.md`
- `docs/data-model/locations/README.md`
- `docs/data-model/results/README.md`
- `docs/data-model/codelists/README.md`
- `docs/data-model/provenance/README.md`

### docs/pipeline/

- `docs/pipeline/README.md`
- `docs/pipeline/ingestion/README.md`
- `docs/pipeline/validation/README.md`
- `docs/pipeline/canonicalization/README.md`
- `docs/pipeline/hashing/README.md`
- `docs/pipeline/diffing/README.md`
- `docs/pipeline/transformation/README.md`
- `docs/pipeline/graph-load/README.md`
- `docs/pipeline/reporting/README.md`
- `docs/pipeline/orchestration/README.md`
- `docs/pipeline/recovery/README.md`

### docs/graph-model/

- `docs/graph-model/README.md`
- `docs/graph-model/nodes/README.md`
- `docs/graph-model/relationships/README.md`
- `docs/graph-model/properties/README.md`
- `docs/graph-model/identity/README.md`
- `docs/graph-model/provenance/README.md`
- `docs/graph-model/temporal/README.md`
- `docs/graph-model/constraints/README.md`
- `docs/graph-model/indexing/README.md`
- `docs/graph-model/query-patterns/README.md`
- `docs/graph-model/examples/README.md`

### docs/standards/

- `docs/standards/README.md`
- `docs/standards/coding/README.md`
- `docs/standards/documentation/README.md`
- `docs/standards/testing/README.md`
- `docs/standards/data-quality/README.md`
- `docs/standards/graph-modeling/README.md`
- `docs/standards/infrastructure/README.md`
- `docs/standards/observability/README.md`
- `docs/standards/security/README.md`
- `docs/standards/ai-assistants/README.md`

### docs/decisions/

- `docs/decisions/README.md`
- `docs/decisions/templates/README.md`
- `docs/decisions/architecture/README.md`
- `docs/decisions/pipeline/README.md`
- `docs/decisions/graph/README.md`
- `docs/decisions/storage/README.md`
- `docs/decisions/infrastructure/README.md`
- `docs/decisions/ai-workflows/README.md`

### docs/runbooks/

- `docs/runbooks/README.md`
- `docs/runbooks/daily-operations/README.md`
- `docs/runbooks/ingestion/README.md`
- `docs/runbooks/diffing/README.md`
- `docs/runbooks/graph-load/README.md`
- `docs/runbooks/neo4j/README.md`
- `docs/runbooks/storage/README.md`
- `docs/runbooks/incidents/README.md`
- `docs/runbooks/recovery/README.md`
- `docs/runbooks/access/README.md`

### docs/prompts/

- `docs/prompts/README.md`
- `docs/prompts/templates/README.md`
- `docs/prompts/coding/README.md`
- `docs/prompts/coding/ingestion/README.md`
- `docs/prompts/coding/canonicalization/README.md`
- `docs/prompts/coding/diffing/README.md`
- `docs/prompts/coding/transformation/README.md`
- `docs/prompts/coding/neo4j/README.md`
- `docs/prompts/graph/README.md`
- `docs/prompts/graph/modeling/README.md`
- `docs/prompts/graph/cypher/README.md`
- `docs/prompts/graph/query-analysis/README.md`
- `docs/prompts/pipeline/README.md`
- `docs/prompts/pipeline/orchestration/README.md`
- `docs/prompts/pipeline/testing/README.md`
- `docs/prompts/pipeline/diagnostics/README.md`
- `docs/prompts/docs/README.md`
- `docs/prompts/docs/folder-readmes/README.md`
- `docs/prompts/docs/adr-drafts/README.md`
- `docs/prompts/docs/runbook-drafts/README.md`
- `docs/prompts/runbooks/README.md`
- `docs/prompts/runbooks/troubleshooting/README.md`
- `docs/prompts/runbooks/incident-response/README.md`
- `docs/prompts/evaluations/README.md`
- `docs/prompts/evaluations/accepted/README.md`
- `docs/prompts/evaluations/experimental/README.md`
- `docs/prompts/evaluations/archived/README.md`

## src/

- `src/README.md`
- `src/ingest/README.md`
- `src/ingest/fetch/README.md`
- `src/ingest/manifests/README.md`
- `src/ingest/archive/README.md`
- `src/canonicalize/README.md`
- `src/canonicalize/parsing/README.md`
- `src/canonicalize/normalization/README.md`
- `src/canonicalize/record-splitting/README.md`
- `src/diff/README.md`
- `src/diff/hashing/README.md`
- `src/diff/compare/README.md`
- `src/diff/change-events/README.md`
- `src/transform/README.md`
- `src/transform/entities/README.md`
- `src/transform/relationships/README.md`
- `src/transform/provenance/README.md`
- `src/neo4j/README.md`
- `src/neo4j/constraints/README.md`
- `src/neo4j/loaders/README.md`
- `src/neo4j/queries/README.md`
- `src/neo4j/maintenance/README.md`
- `src/reports/README.md`
- `src/reports/daily/README.md`
- `src/reports/validation/README.md`
- `src/reports/change-summaries/README.md`

## tests/

- `tests/README.md`
- `tests/unit/README.md`
- `tests/integration/README.md`
- `tests/end-to-end/README.md`
- `tests/fixtures/README.md`
- `tests/fixtures/sample-xml/README.md`
- `tests/fixtures/canonical-records/README.md`
- `tests/fixtures/expected-diffs/README.md`
- `tests/performance/README.md`

## infrastructure/

- `infrastructure/README.md`
- `infrastructure/storage/README.md`
- `infrastructure/compute/README.md`
- `infrastructure/orchestration/README.md`
- `infrastructure/networking/README.md`
- `infrastructure/monitoring/README.md`
- `infrastructure/environments/README.md`
- `infrastructure/environments/dev/README.md`
- `infrastructure/environments/staging/README.md`
- `infrastructure/environments/prod/README.md`

## scripts/

- `scripts/README.md`
- `scripts/bootstrap/README.md`
- `scripts/maintenance/README.md`
- `scripts/diagnostics/README.md`
- `scripts/helpers/README.md`
