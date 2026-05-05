![IATI Plus Logo](https://github.com/IATIPlus/Project/blob/main/Media/IATIPlus-Header.png)

# IATI Plus Project

**IATI Plus** is a versioned knowledge graph infrastructure built to modernize access to International Aid Transparency Initiative (IATI) data. The project maintains a comprehensive archive of daily IATI data snapshots for longitudinal research while operating a live Neo4j-based knowledge graph that tracks changes in humanitarian aid activities over time. This dual approach preserves the complete historical record of IATI's 32GB+ corpus while enabling researchers, developers, and AI systems to query both current state and change history through graph-native interfaces.

![Project Illustration](https://github.com/IATIPlus/iati-knowledge-graph/blob/main/media/IATIPlus_Overview.png)

## Mission

The core mission is to build a production-grade IATI platform with the architecture, capacity, and reliability to support high-volume traffic from AI applications running at scale. IATI Plus provides full schema exposure, multi-field filtering, nested querying across hierarchical aid activity structures, advanced analytical capabilities, and native support for XPath and XQuery operations on canonical XML representations. By combining immutable snapshot archives with a queryable temporal graph, the project creates an IATI infrastructure capable of powering the next generation of humanitarian aid analytics, AI-driven insights, and real-time monitoring tools.

IATI Plus is an open-source collaborative initiative bringing together student volunteers, researchers, AI experts, technology companies, and humanitarian organizations to tackle the complex challenges of making aid activity information natively accessible to AI agents. The project serves as an experimental testbed for next-generation data architectures, partnering with initiatives like MIT's Project NANDA—which is architecting foundational aspects of the agentic web—to explore how structured humanitarian data can be optimized for autonomous agent consumption, reasoning, and real-time decision support. By working at the intersection of knowledge graphs, temporal versioning, and agentic AI systems, IATI Plus aims to develop and validate capabilities that will define how AI systems discover, query, and act upon global development data at scale.

Learn more: [ABOUT.md](https://github.com/IATIPlus/iati-knowledge-graph/blob/main/docs/ABOUT.md)
Suggested Markdown Files: [README-inventory](https://github.com/IATIPlus/iati-knowledge-graph/tree/main/readme-inventory)

## Get Involved

IATI Plus is organized so volunteers can contribute effectively with the support of AI coding assistants. The repository separates project knowledge from implementation: the docs/ area contains the architecture, data model, workflow notes, standards, and prompt guidance that help humans and AI understand the project, while the src/ and related code folders contain the software used to ingest IATI XML, generate change histories, manage cloud storage and compute workflows, test the pipeline, and run the graph database environment.

Volunteers can contribute by refining prompts, improving project documentation, and working with AI coding assistants to generate, test, and iterate on the codebase. Contributions may include helping orchestrate cloud data storage, provisioning compute resources, building ingestion and diffing pipelines, preparing Neo4j load processes, validating outputs, and improving reliability as the system evolves toward a scalable platform for AI-ready humanitarian data.

Learn more: [CONTRIBUTING.md](https://github.com/IATIPlus/iati-knowledge-graph/blob/main/docs/CONTRIBUTING.md)

### Contact

The IATI Plus is managed by the **Humanitarian AI Meetup Community** linking eighteen local meetup groups across ten countries. To learn more about the project and to get involved, contact: team(at)humanitarianai.org  
