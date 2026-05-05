# standards/

This directory contains the standards that guide how IATI Plus is designed, built, documented, tested, and operated. It defines the shared rules and expectations that keep contributions consistent across architecture, data processing, graph modeling, infrastructure, documentation, and AI-assisted development.

The `standards/` folder should help both human contributors and AI coding assistants understand how work should be done across the repository. It is the place to document conventions, guardrails, quality thresholds, naming rules, and review expectations so that the project evolves coherently even when many contributors are working in parallel.

## Purpose

Use this folder to document:

- Engineering conventions used across the repository
- Documentation standards and file organization rules
- Coding standards and style expectations
- Testing expectations and quality gates
- Data handling and validation standards
- Graph modeling conventions and naming patterns
- Infrastructure and deployment conventions
- Security, reliability, and operational expectations
- Standards for working with AI coding assistants

## Scope

This folder focuses on **how work should be performed and evaluated**.

Examples of what belongs here:

- Naming conventions for files, directories, datasets, and graph entities
- Documentation quality standards
- Code style and formatting expectations
- Branching, review, and contribution rules
- Test coverage expectations and acceptance criteria
- Rules for idempotent pipeline stages and safe reprocessing
- Standards for logging, observability, and error reporting
- Prompt-writing and AI-collaboration guidelines for contributors

Examples of what usually belongs elsewhere:

- `../architecture/` for system design decisions
- `../pipeline/` for execution flow and workflow stages
- `../graph-model/` for graph semantics and structure
- `../runbooks/` for operational procedures and incident response steps
- `../../src/` for implementation code

## What questions this folder should answer

A contributor or coding assistant should be able to use this folder to answer questions such as:

- What coding and documentation conventions should be followed in this repository?
- How should new files, modules, and documents be named and organized?
- What tests are expected before code is considered ready?
- What level of validation is required for ingestion, diffing, and graph loading work?
- What standards govern reliability, reproducibility, and safe reruns?
- How should volunteers use AI coding assistants responsibly and consistently?
- What constitutes an acceptable pull request or contribution?

## Suggested documents in this folder

As this folder grows, it may contain files such as:

- `coding-standards.md` — Language-specific style, formatting, and implementation conventions.
- `documentation-standards.md` — How docs should be written, named, linked, and maintained.
- `testing-standards.md` — Expectations for unit, integration, and end-to-end validation.
- `data-quality-standards.md` — Rules for source validation, canonicalization quality, and change accuracy.
- `graph-modeling-standards.md` — Naming and modeling conventions for labels, relationships, and properties.
- `infrastructure-standards.md` — Rules for cloud resources, environments, secrets, and deployment patterns.
- `logging-and-observability.md` — Standards for metrics, traces, structured logs, and run metadata.
- `ai-assistant-guidelines.md` — How contributors should craft prompts, review AI output, and verify generated code.
- `contribution-standards.md` — Pull request quality expectations and review checklist.

## Typical standards concerns

A healthy standards layer for IATI Plus should usually clarify:

1. What consistency means across code, docs, data, and graph structures.
2. Which checks are mandatory before code is merged or run in production.
3. How to keep daily data processing reproducible and auditable.
4. How to design changes so they are observable, testable, and reversible.
5. How to use AI assistance productively without weakening review discipline.
6. How to reduce ambiguity for volunteers joining the project for the first time.

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for overall mission and project context.
2. `../../README.md` for repository-level setup and contribution guidance.
3. `documentation-standards.md` and `coding-standards.md` for baseline working conventions.
4. `testing-standards.md` and `data-quality-standards.md` before changing pipeline or graph logic.
5. `ai-assistant-guidelines.md` when using prompt-driven workflows.
6. The domain-specific documentation in `../pipeline/`, `../graph-model/`, and `../architecture/` as needed.

## Relationship to implementation

This folder should shape how the rest of the repository is maintained and reviewed.

Typical relationships include:

- `../../src/` should reflect the coding, testing, and observability standards documented here.
- `../../tests/` should implement the quality expectations described here.
- `../pipeline/` should align with reliability and rerun standards documented here.
- `../graph-model/` should align with naming, identity, and modeling conventions documented here.
- Root contribution files such as `README.md`, `CONTRIBUTING.md`, and issue templates should be consistent with this folder.

## Guidance for contributors

- Treat these standards as shared project agreements, not optional preferences.
- Keep standards specific enough to guide decisions and light enough to remain usable.
- Update this folder when repeated review comments reveal an undocumented rule.
- Prefer explicit examples over vague statements whenever possible.
- Document both the rule and the reason behind it.
- Add standards for AI-assisted work wherever generated code, prompts, or automation patterns need consistent oversight.

## Role in the repository

This folder is the consistency and quality layer of the documentation set. It should help contributors and coding assistants produce work that is easier to review, safer to operate, more reproducible over time, and more aligned with the long-term goals of the IATI Plus project.
