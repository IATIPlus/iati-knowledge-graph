# Contributing to IATI Plus

Welcome! IATI Plus is designed for collaborative development where volunteers work alongside AI coding assistants to build a production-grade knowledge graph infrastructure for humanitarian aid data.

## Your Role as a Volunteer

As a contributor, you'll help build and improve the IATI Plus platform by:

1. **Refining project documentation** — Clarifying architecture decisions, data models, and workflow specifications that guide both human developers and AI assistants.
2. **Crafting and testing prompts** — Developing effective prompts that help AI coding assistants generate correct, efficient code for specific pipeline components.
3. **Generating code with AI assistance** — Using tools like GitHub Copilot, Claude, or ChatGPT to implement parsers, diff engines, graph loaders, and validation logic.
4. **Orchestrating cloud infrastructure** — Setting up and configuring AWS S3 storage, compute resources, and data processing workflows.
5. **Testing and validation** — Running generated code against real IATI data, identifying edge cases, and improving reliability.
6. **Improving the graph model** — Refining how IATI activities, organizations, and relationships are represented in Neo4j.

You do not need to be an expert in every technology. The role is to understand the requirements, work with AI to generate solutions, test results, and iterate until the system works correctly.

## How This Repository Is Organized

The repository follows a clear separation between **knowledge** and **implementation**:

```text
iati-graph-tracker/
├── docs/              # Project knowledge for humans and AI
├── src/               # Implementation code
├── tests/             # Validation and test fixtures
├── schemas/           # Data contracts and standards
├── config/            # Configuration templates
├── scripts/           # Operational and setup scripts
└── examples/          # Sample inputs and outputs
```

### The `docs/` Directory — Project Knowledge

This is where the "why" and "what" live. AI assistants read these files to understand project context before generating code.

**Structure:**
- `docs/architecture/` — System design, component interactions, data flow diagrams.
- `docs/data-model/` — How IATI XML maps to graph nodes and relationships.
- `docs/pipeline/` — Daily ingestion workflow, canonicalization rules, diff generation logic.
- `docs/graph-model/` — Neo4j schema, versioning strategy, temporal queries.
- `docs/standards/` — Coding conventions, naming rules, error handling patterns.
- `docs/decisions/` — Architectural Decision Records (ADRs) explaining key choices.
- `docs/runbooks/` — Step-by-step operational procedures.
- `docs/prompts/` — Reusable prompt templates for common AI-assisted tasks.

When contributing, update docs whenever you make an architectural decision, discover an edge case, or clarify how something should work. Well-maintained docs make AI assistants far more effective.

### The `src/` Directory — Implementation

This is where the executable code lives, organized by pipeline stage:

- `src/ingest/` — Download IATI data from the registry and manage snapshots.
- `src/canonicalize/` — Parse XML, apply C14N normalization, and extract activities.
- `src/diff/` — Hash records, compare snapshots, and generate change events.
- `src/transform/` — Convert XML to graph-ready CSV or JSON formats.
- `src/neo4j/` — Load data into Neo4j, manage versions, and create relationships.
- `src/reports/` — Generate quality metrics, validation summaries, and change statistics.
- `src/common/` — Shared utilities, logging, and configuration helpers.

When contributing, generate or modify code in the appropriate stage directory. Each module should have a clear single responsibility.

### The `tests/` Directory — Validation

- `tests/unit/` — Fast, isolated tests for individual functions.
- `tests/integration/` — Tests that verify components work together correctly.
- `tests/fixtures/` — Sample IATI XML files, expected outputs, and edge cases.

Always include tests with new code. Use fixtures to demonstrate what the code should handle.

### The `schemas/` Directory — Data Contracts

- `schemas/iati/` — Official IATI XSD schemas by version.
- `schemas/internal/` — JSON schemas or CSV contracts for pipeline outputs.

Reference these schemas when writing parsers or validators. Update internal schemas when data formats change.

### The `config/` Directory — Configuration Templates

This folder stores configuration templates such as AWS settings, Neo4j connection settings, and pipeline parameters. Never commit real credentials or secrets.

### The `scripts/` Directory — Operational Tools

This folder stores setup scripts, cloud provisioning helpers, and one-off migration or repair utilities.

## Working With AI Coding Assistants

### Effective Workflow

1. Read the relevant docs first.
2. Write or refine a prompt.
3. Generate code with an AI assistant.
4. Test immediately against fixtures or real data.
5. Iterate until the behavior is correct.
6. Update documentation with any new decisions or edge cases.
7. Commit with clear messages that explain what changed and why.

### Good Prompts Include

- **Context:** What part of the pipeline is being built.
- **Requirements:** What the code must do.
- **Constraints:** File size limits, performance expectations, failure handling, and dependencies.
- **Expected output:** Exact return values, files, or side effects.
- **References:** Relevant files in `docs/` or `schemas/`.

Example:

> Build a Python function for the daily IATI diff engine. Parse each `<iati-activity>` element, canonicalize it using XML C14N, compute a SHA-256 hash, and return a dictionary keyed by `iati-identifier`. It must handle large XML files, skip invalid activities, and log errors. See `docs/pipeline/` for normalization rules.

### Code Quality Standards

- **Readable** — Clear variable names and logical structure.
- **Tested** — Include unit tests and use fixtures for edge cases.
- **Documented** — Add docstrings for public functions and concise comments where needed.
- **Reliable** — Handle failures gracefully and log informative errors.
- **Idiomatic** — Follow the conventions of the language being used.

## Project Governance

- **Open collaboration** — Major decisions should be documented in `docs/decisions/`.
- **AI-assisted development** — AI accelerates development, but human review remains essential.
- **Incremental progress** — Small, tested changes are better than large, untested rewrites.
- **Quality over speed** — The goal is a reliable platform, not just working code.

## Getting Started

1. Clone the repository.
2. Read the architecture and pipeline docs first.
3. Review prompt examples and open issues.
4. Choose a task or propose one.
5. Update docs as needed before or alongside code changes.
6. Generate and test code carefully.
7. Open a pull request with a clear description of the work.

## Questions

Open an issue or discussion when something is unclear. Questions help improve the repository for both future volunteers and the AI assistants that support them.
