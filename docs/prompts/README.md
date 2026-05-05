# prompts/

This directory contains reusable prompts, prompt templates, prompt workflows, and prompt-related guidance for the IATI Plus project. It is the place to document how contributors can work with AI coding assistants and language models in a disciplined, repeatable way to design, build, test, document, and operate the platform.

The `prompts/` folder should help both human contributors and AI coding assistants understand which prompt assets exist, what each one is for, what inputs they expect, what outputs they should produce, and how they fit into the broader repository workflow. It should make prompt-driven work more reviewable, reusable, and easier to improve over time.

## Purpose

Use this folder to document:

- Reusable prompts for common project tasks
- Prompt templates for coding, documentation, testing, and operations
- Multi-step prompt workflows for larger implementation tasks
- Prompt inputs, output expectations, and guardrails
- Versioned prompt iterations and refinements
- Evaluation notes for prompt quality and drift
- Guidance for how volunteers should use prompts with AI assistants

## Scope

This folder focuses on **prompt assets as reusable tools for project work**.

Examples of what belongs here:

- Prompts for generating ingestion code
- Prompts for building diff logic and validation tests
- Prompts for graph-model implementation and Cypher generation
- Prompts for infrastructure setup and deployment planning
- Prompts for documentation generation and repo organization
- Prompt chains for end-to-end tasks such as “design, implement, test, and document a pipeline stage”
- Prompt evaluation examples showing good and bad outputs

Examples of what usually belongs elsewhere:

- `../standards/` for project-wide AI-assistant policies and contribution rules
- `../decisions/` for major choices about prompt strategy or workflow design
- `../runbooks/` for operational procedures rather than reusable prompt assets
- `../../src/` for the code generated or maintained with the help of prompts
- Root-level contribution docs for general onboarding that is not prompt-specific

## What questions this folder should answer

A contributor or coding assistant should be able to use this folder to answer questions such as:

- What prompts already exist for this repository?
- Which prompt should be used for a given task?
- What input context should be supplied to each prompt?
- What output format should the prompt produce?
- What are the review expectations for AI-generated output?
- How should prompt variants be tested and improved over time?
- How can a volunteer use prompts to contribute safely and effectively?

## Suggested contents

As this folder grows, it may contain files such as:

- `README.md` — An index explaining the purpose and organization of the prompt library.
- `coding/` — Prompts for implementation tasks such as parsers, transforms, and loaders.
- `testing/` — Prompts for generating tests, fixtures, and validation logic.
- `documentation/` — Prompts for README sections, folder docs, and design summaries.
- `operations/` — Prompts for diagnostics, runbook drafting, and troubleshooting assistance.
- `graph/` — Prompts for Cypher, graph modeling, and query design.
- `templates/` — General prompt patterns and reusable scaffolds.
- `examples/` — Sample prompt inputs and expected output shapes.
- `evaluations/` — Notes or fixtures for comparing prompt revisions.

## How prompt assets should be organized

A useful prompt library should usually make the following explicit for each prompt or prompt set:

1. What the prompt is for.
2. When it should be used.
3. What inputs or repository context it expects.
4. What output format it should produce.
5. What good output looks like.
6. What guardrails, exclusions, or review requirements apply.
7. How prompt revisions should be versioned or tested.

## Suggested reading order

A new contributor or coding assistant should usually read in this order:

1. `../../ABOUT.md` for project purpose and context.
2. `../../README.md` for general contribution guidance.
3. `../standards/` for repository rules on AI-assisted work.
4. `README.md` in this folder for prompt-library organization.
5. The specific prompt or prompt template relevant to the task.
6. Related docs in `../pipeline/`, `../graph-model/`, `../runbooks/`, or `../architecture/` to provide domain context before using the prompt.

## Relationship to implementation

This folder should connect prompt assets to the work products they are meant to support.

Typical relationships include:

- `../../src/` contains code that may be generated, refined, or reviewed with these prompts.
- `../../tests/` may include tests created or expanded with prompt assistance.
- `../documentation/`-style folders may contain materials drafted using documentation prompts.
- `../standards/` defines the quality and review expectations for outputs produced with these prompts.
- `../runbooks/`, `../pipeline/`, and `../graph-model/` provide the domain context that many prompts need in order to work well.

## Guidance for contributors

- Treat prompts as maintainable project assets, not disposable chat text.
- Keep prompts specific, testable, and tied to clear output contracts.
- Store examples near prompts whenever possible.
- Record major prompt revisions rather than silently overwriting successful variants.
- Review AI-generated output as carefully as handwritten output.
- Update this folder whenever a prompt becomes a repeated part of the project workflow.

## Role in the repository

This folder is the AI-collaboration layer of the documentation set. It should help contributors and coding assistants work from reusable, improvable prompt assets so that AI-assisted development becomes more consistent, transparent, and effective across the IATI Plus project.
