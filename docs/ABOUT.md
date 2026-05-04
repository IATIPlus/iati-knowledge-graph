# About IATI Plus

## What Is IATI Plus?

IATI Plus is a versioned knowledge graph infrastructure designed to modernize access to International Aid Transparency Initiative (IATI) data. The project maintains a comprehensive archive of daily IATI data snapshots for longitudinal research while operating a live Neo4j-based knowledge graph that tracks changes in humanitarian aid activities over time.

## The Challenge

The current IATI ecosystem provides valuable transparency into global development and humanitarian aid, but it lacks the architecture, capacity, and reliability needed to support high-volume traffic from AI applications running at scale. Existing IATI tools primarily expose current-state data through limited query interfaces, making it difficult for AI agents and researchers to:

- Access complete historical records of how aid activities evolve.
- Query nested relationships within complex activity structures.
- Filter across multiple fields simultaneously with advanced logic.
- Traverse semantic connections between organizations, sectors, and activities.
- Reconstruct the state of the aid landscape at any point in time.

## The IATI Plus Approach

IATI Plus addresses these limitations through a dual-layer architecture.

### 1. Immutable Snapshot Archive

Every day, the complete IATI corpus is downloaded, archived in AWS S3 with full metadata, and preserved as an immutable historical record. This creates a longitudinal dataset that researchers can use to study trends, track changes in reporting practices, and validate analyses over time.

### 2. Versioned Knowledge Graph

At the same time, the project maintains a live Neo4j graph database that represents IATI activities, organizations, transactions, sectors, and their relationships as a queryable knowledge graph. Unlike traditional databases that overwrite old data, IATI Plus preserves temporal versions:

- Each IATI activity exists as both a current node representing the latest state and a chain of versioned nodes representing historical states.
- Changes between daily snapshots are computed using canonical XML normalization and stored as structured change events.
- Relationships can be versioned with `valid_from` and `valid_to` timestamps, enabling point-in-time queries.
- The graph supports nested traversals, multi-hop relationship queries, and temporal analysis that flat data stores cannot provide.

## Core Capabilities

IATI Plus is designed to provide:

- **Full schema exposure** — Complete access to IATI standard fields and extensions.
- **Multi-field filtering** — Query across combinations of attributes simultaneously.
- **Nested querying** — Navigate hierarchical structures such as activity to transaction to sector while preserving relationship context.
- **Advanced filtering** — Use complex predicates, range filters, pattern matching, and aggregations.
- **XPath and XQuery support** — Query canonical XML representations using standard XML query languages.
- **Temporal versioning** — Access historical states, compare versions, and track change events.
- **Graph traversals** — Discover implicit connections through organizations, geographies, sectors, and funding flows.
- **AI-native APIs** — Return structured outputs optimized for autonomous agent use.

## The Mission

IATI Plus aims to build a production-grade IATI platform capable of supporting the next generation of humanitarian aid analytics, AI-driven insights, and real-time monitoring tools. By combining immutable snapshot archives with a queryable temporal graph, the project creates an infrastructure layer that positions IATI data as a first-class resource for agentic AI systems.

## Open Source and Collaborative

IATI Plus is an open-source initiative bringing together student volunteers, researchers, AI experts, technology companies, and humanitarian data practitioners. The project serves as an experimental testbed for next-generation data architectures, with the hope of partnering with initiatives such as MIT's Project NANDA, which is exploring foundational aspects of the agentic web, to examine how structured humanitarian data can be optimized for autonomous agent consumption, reasoning, and real-time decision support.

By working at the intersection of knowledge graphs, temporal versioning, and agentic AI systems, IATI Plus aims to develop and validate capabilities that will help define how AI systems discover, query, and act upon global development data at scale.

## Technology Stack

- **Storage**: AWS S3 for raw snapshot archives and processed outputs.
- **Graph Database**: Neo4j for the versioned knowledge graph.
- **Processing**: Python-based pipelines for XML parsing, canonicalization, diffing, and transformation.
- **Standards**: IATI XML Schema, XML Canonicalization (C14N), and XML patch approaches.
- **Query Languages**: Cypher for graph queries, plus XPath and XQuery for canonical XML access.

## Project Values

- **Preserving history** — Every version of every record is retained for future analysis.
- **AI-ready design** — Built from the ground up for autonomous agent access.
- **Open collaboration** — Code, documentation, and architectural decisions are public.
- **Incremental progress** — Small, tested improvements are preferred over large rewrites.
- **Quality over speed** — Reliable infrastructure that can scale sustainably.
