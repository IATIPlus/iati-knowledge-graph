# IATI Plus: A Comprehensive Guide
### Understanding IATI, the Infrastructure Gap, and Why We Are Building IATI Plus

*This document is written for humans, AI interfaces and coding assistants. It provides the full context needed to understand what IATI is, why it matters, what its current limitations are, and what the IATI Plus project is building and why.*

---

**About This Project**

IATI Plus is an all-volunteer, open-source research initiative. The project approaches its goals as a structured research and development programme — iterating through a set of technically demanding challenges in order to understand how they can be solved, establish proof-of-concept implementations, and build a documented foundation for further development by the IATI community, partner organizations and the wider open-source ecosystem. Contributors should expect the project to be exploratory in character: we are mapping territory, not delivering a finished product. That is by design.

The problems IATI Plus is working on — graph-native knowledge graph construction from heterogeneous XML at scale, temporal versioning and change detection across a distributed publisher network, agentic protocol integration and publisher agent frameworks — do not have established playbooks. Solving them requires the kind of open, iterative, multi-disciplinary collaboration that a volunteer research community is uniquely well-suited to provide.

The knowledge graph IATI Plus is building serves a dual purpose: it is both the infrastructure layer IATI needs to become AI-ready, and a **data sandbox** upon which a wide range of experimental AI applications, analytical tools and reporting use cases can be prototyped and tested against real, production-scale humanitarian data. The extensible nature of the IATI XML standard — which allows publishers to report information well beyond the core schema using namespace extensions — means the boundaries of what can be explored on this platform are themselves an open and expanding research frontier. As publishers push the limits of what IATI can express, the sandbox grows with them.

---

## Table of Contents

1. [What Is IATI?](#1-what-is-iati)
2. [IATI's Scale and Institutional Weight](#2-iatis-scale-and-institutional-weight)
3. [The IATI Data Standard: Structure and Depth](#3-the-iati-data-standard-structure-and-depth)
4. [IATI Among the Sector's Data Landscape](#4-iati-among-the-sectors-data-landscape)
5. [The Infrastructure Problem](#5-the-infrastructure-problem)
6. [Why AI Cannot Simply "Figure It Out"](#6-why-ai-cannot-simply-figure-it-out)
7. [The Agentic Web and Why It Changes Everything](#7-the-agentic-web-and-why-it-changes-everything)
8. [IATI as an Agent Ecosystem](#8-iati-as-an-agent-ecosystem)
9. [New Use Cases Enabled by an Agentic IATI](#9-new-use-cases-enabled-by-an-agentic-iati)
10. [What IATI Plus Is Building](#10-what-iati-plus-is-building)
11. [The Technical Challenges IATI Plus Is Tackling](#11-the-technical-challenges-iati-plus-is-tackling)
12. [Reference: The Sector's Data Landscape](#12-reference-the-sectors-data-landscape)
13. [IATI's 2030 Strategic Plan and Its Relationship to IATI Plus](#13-iatis-2030-strategic-plan-and-its-relationship-to-iati-plus)

---

## 1. What Is IATI?

Launched in 2008 at the Third High Level Forum on Aid Effectiveness in Accra, Ghana, the **International Aid Transparency Initiative (IATI)** is the world's largest open data standard for development and humanitarian information. Now in its seventeenth year, IATI is a global open data publishing framework used by humanitarian, development, environmental and other organizations to share granular, structured information about their activities, financial transactions, results and organizational data.

IATI is built around an **XML data standard** — a formally defined schema that specifies how information about aid activities, organizations, transactions and results should be structured and published. Publishers produce XML files conforming to this schema and register them with the IATI Registry, which serves as the central index of all published data. The data itself is hosted on publishers' own websites and systems; the Registry provides the catalogue.

The IATI Standard is designed to capture information at multiple levels of granularity and across a wide range of reporting contexts. A single IATI activity record can contain:

- Project titles, descriptions and status
- Funding organization and implementing organization details
- Geographic location data (country, region, sub-national coordinates)
- Sector and thematic classifications (using DAC codes, SDG tags and others)
- Budget information and forward-looking financial projections
- Individual financial transactions (commitments, disbursements, expenditures)
- Results frameworks and reported outcomes
- Linked documents such as reports, evaluations and country plans
- Conditions, policy markers and tied-aid status
- Participating organizations at every stage of the delivery chain

The standard encompasses **hundreds of elements and attributes** and is explicitly **designed to be extensible** — meaning organizations can publish additional information beyond the core schema using namespace extensions. This makes the range of information that can be expressed through IATI virtually limitless in scope and depth.

IATI is not a database. It is a **publishing standard and open data framework** — a common language that enables any organization, anywhere in the world, to describe its development and humanitarian work in a structured, machine-readable, interoperable format.

---

## 2. IATI's Scale and Institutional Weight

IATI is not a marginal or experimental data channel. It is the sector's **de facto transparency infrastructure**, backed by seventeen years of institutional investment and a growing network of mandatory reporting requirements.

**Scale:**
- More than **1,650 organizations** publish to the IATI standard as of 2024, an increase of 106 from the previous year
- Publishers include donor governments, multilateral agencies, UN bodies, foundations, NGOs, development finance institutions and private sector organizations
- The combined published corpus exceeds **32 gigabytes** of XML data
- Publisher data covers **USD 269 billion** in disbursements and expenditure reported for 2024, and USD 147 billion in forward-looking budget data for 2025
- Over **106,000 humanitarian activities** are published to the standard

**Institutional mandates and endorsements:**
- The **Grand Bargain** — agreed at the 2016 World Humanitarian Summit in Istanbul by leading donor governments, UN agencies and NGO networks — explicitly identified IATI as the common standard for humanitarian financial transparency, committing signatories to publish timely, open data on humanitarian funding
- **Government mandates** in the United Kingdom, Netherlands, Belgium and elsewhere require organizations receiving official development assistance to publish to IATI as a condition of funding
- The **OECD DAC** has aligned its reporting frameworks with IATI
- Multiple **UN agencies** including UNHCR, WFP and OCHA publish to IATI and have formally endorsed it as a transparency standard
- The **European Commission** has launched programs to strengthen IATI publication across EU member states

This institutional depth means IATI's publisher network and corpus will continue to grow. The question is not whether IATI matters — seventeen years of mandates, commitments and publisher growth answer that. The question is whether the infrastructure exists to make that investment useful.

---

## 3. The IATI Data Standard: Structure and Depth

Understanding IATI's technical architecture is essential to understanding both its potential and its limitations.

### XML Foundation

IATI data is published in **XML (Extensible Markup Language)** — a structured, hierarchical data format that supports deeply nested information, rich attribute sets and formal schema validation. This is fundamentally different from flat data formats like CSV or JSON arrays. An IATI activity record is not a row in a spreadsheet; it is a tree of interconnected elements, each of which can contain child elements, attributes and narrative text in multiple languages.

This hierarchical structure is intentional. Aid activities are themselves hierarchical and relational: a donor commits funds to an implementing organization, which sub-grants to local partners, which deliver activities in specific locations, which produce results against defined indicators, all of which are linked to organizational identifiers that connect to other published records. XML can hold this web of relationships; flat formats cannot.

### Schema, Codelists and Extensions

The IATI Standard is formally defined through:

- **The IATI Activity Standard** — the schema for describing individual development and humanitarian activities
- **The IATI Organisation Standard** — the schema for describing the organizations involved in development cooperation
- **Codelists** — controlled vocabularies for fields that have a finite set of valid values (currencies, countries, sectors, transaction types, aid types, and dozens more)
- **Rulesets** — formal validation rules that define what constitutes a valid IATI XML file
- **Namespace extensions** — mechanisms for publishers to include information beyond the core schema without breaking standard compliance

The standard is governed and versioned, with the current version being 2.03. Changes to the standard go through a formal consultation process involving the IATI membership.

### Relational Depth

What makes IATI particularly powerful — and particularly difficult to work with — is its relational depth. A single query that sounds simple in natural language ("show me all health activities funded by European donors in Sub-Saharan Africa and their reported results") requires:

- Filtering activities by sector classification across multiple codelist vocabularies
- Identifying funding organizations by their IATI organization identifiers and matching those to a list of European donor codes
- Filtering by recipient country or region codes
- Traversing into result elements nested within each matching activity
- Handling the fact that the same activity may appear in multiple publishers' data (donor reporting and implementer reporting)
- Normalizing currency values and transaction dates across records

No simple API filter or keyword search can answer this question from raw IATI XML. It requires a properly indexed, relational, graph-aware query layer.

---

## 4. IATI Among the Sector's Data Landscape

IATI is sometimes described as one of several competing data channels in the humanitarian and development sector. This framing misunderstands what IATI actually is and how it relates to the other major platforms.

### The Major Data Sources and What They Actually Do

**OCHA Financial Tracking Service (FTS)** — `fts.unocha.org`
Tracks humanitarian funding flows in real time. Covers contributions from government donors, UN agencies and NGOs against humanitarian response plans. Its scope is deliberately narrow: it focuses on humanitarian (not development) funding, covers flows rather than activities, and does not capture results, locations or implementing chain detail. FTS publishes its own data to the IATI standard, reflecting IATI's role as the broader framework.

**OECD DAC Creditor Reporting System (CRS)** — `data-explorer.oecd.org`
The authoritative source for Official Development Assistance (ODA) statistics. The 28 DAC member governments and European institutions are required to report their aid flows to the CRS annually. Coverage is broad but shallow: it captures aggregate flows and basic activity descriptions at the donor level, with a significant annual reporting lag. It does not capture sub-national locations, implementing organization detail, results, or the full transaction lifecycle. It also covers only official government donors, not the broader universe of NGOs, foundations and multilateral agencies that publish to IATI.

**Humanitarian Data Exchange (HDX)** — `data.humdata.org`
Managed by OCHA's Centre for Humanitarian Data, HDX is the sector's primary open data repository — a place where organizations can upload and share datasets of any kind. It hosts over 20,000 datasets from nearly 1,900 sources. But HDX is a repository, not a publishing standard. It defines no common schema, no required field structure and no obligation on publishers about what information to include or how to structure it. Data on HDX is as heterogeneous as the organizations that upload it.

**AidData** — `aiddata.org`
A research and innovation lab at the College of William & Mary specializing in geocoded development finance data, aid effectiveness research, and tracking non-traditional donors — particularly China's overseas development finance. AidData produces curated, research-grade datasets, not a real-time publishing framework.

### What Only IATI Does

IATI is the only framework that:

- Covers the **full activity lifecycle** — from planning and budget commitment through individual financial transactions, implementing partner chains, sub-national locations, and reported results
- Is used by the **full spectrum** of development and humanitarian actors — not just official government donors, but UN agencies, NGOs, foundations, development finance institutions and private sector organizations
- Operates on a **common, formal schema** that enables true cross-publisher comparison and aggregation
- Supports **real-time or near-real-time publication** — publishers update their IATI data continuously, not on an annual cycle
- Is **natively extensible** to capture information beyond the core standard

IATI is not competing with FTS, CRS or HDX. It occupies a different and broader lane — one that, with the right infrastructure, subsumes and connects what those other sources do.

---

## 5. The Infrastructure Problem

Despite its depth and institutional weight, IATI's current infrastructure does not match its potential.

### Built as a Publishing Standard, Not a Query Platform

IATI was designed to solve the problem of data publishing — getting organizations to share their information in a common format. It was not designed to solve the problem of data consumption — enabling applications to query that information in complex, relational, nested ways.

The IATI Datastore — the official tool for accessing published IATI data — is explicitly called a *datastore*, not a database. As its own documentation states, it cannot be used as a single integrated dataset because IATI is a publishing standard, not an integral information system. Its query capabilities are limited to basic field filters. Its CSV export format flattens hierarchical data in ways that lose relational information. Users of the Datastore are required to have technical competency and understand the basic structure and elements of the IATI Standard simply to retrieve data.

### The Scale of the Problem

The published IATI corpus exceeds 32 gigabytes of XML distributed across thousands of individual files published by 1,650+ organizations. Each publisher maintains their own files on their own servers. Data quality, schema interpretation and update frequency vary enormously across publishers. The same activity is frequently reported by multiple organizations (the donor and the implementer, for example), creating duplication that must be resolved rather than simply aggregated.

There is no single, unified, queryable representation of the IATI corpus. There is no temporal versioning system that tracks how individual activities have changed over time. There is no graph-native index that preserves and exposes the relational structure of the data. There is no API designed for the kind of complex, multi-field, nested queries that meaningful humanitarian analysis requires.

### The Consequence

This infrastructure gap means that IATI's 32+ gigabytes of rich, hierarchical, semantically structured data about global development and humanitarian work is functionally inaccessible to most applications. Researchers download bulk XML and process it themselves. Developers build one-off integrations. Consumer-grade applications that could put IATI data in the hands of government officials, journalists, community organizations or AI systems simply cannot be built on top of the current infrastructure. The sector's largest, richest, most institutionally supported open dataset is sitting in unmarked boxes.

---

## 6. Why AI Cannot Simply "Figure It Out"

A common assumption — particularly among those unfamiliar with IATI's technical reality — is that modern AI systems are capable enough to read and reason over any data source, including IATI's raw XML, without requiring infrastructure investment. This assumption is incorrect, and understanding why is important for anyone building AI applications in the humanitarian sector.

### What AI Systems Are Good At

Large language models are genuinely powerful at synthesizing narratives, translating between formats, summarizing documents, answering questions about well-structured inputs, and generating plausible text. They are excellent tools for working with information that is already organized, indexed and retrievable.

### What AI Systems Cannot Do

What AI systems cannot do reliably is **retrieve, aggregate and reason over** tens of gigabytes of raw XML distributed across thousands of disconnected files, published by 1,650 different organizations with varying interpretations of the schema, varying data quality levels and varying update schedules — without a structured query layer underneath.

The problems are specific and concrete:

- **Retrieval**: An AI system cannot efficiently search 32GB of raw XML to find the 847 activities that match a specific combination of sector, geography, funding organization type and date range. That requires an index. Indexes require infrastructure.
- **Aggregation**: Adding up all disbursements to health activities in a specific country across all publishers requires normalizing currencies, resolving duplicate reporting, filtering by transaction type, and joining across thousands of separate files. This is a data engineering problem, not an intelligence problem.
- **Grounding**: An AI system that cannot reliably retrieve the correct data will hallucinate plausible-sounding but incorrect answers — a particularly serious failure mode in contexts where the answers inform funding decisions, crisis response, or accountability reporting.
- **Temporal reasoning**: Understanding how an activity has changed over time — whether a budget was increased, a result was updated, a partner was added — requires a versioned history of the data. IATI currently maintains no such history.

The gap between AI capability and AI performance on IATI data is not a problem of intelligence. It is a problem of access, structure and grounding. Expecting AI to "magically" understand IATI without infrastructure investment confuses language capability with data infrastructure. They are entirely separate problems. A brilliant analyst with no filing system cannot tell you what is in the files.

---

## 7. The Agentic Web and Why It Changes Everything

The infrastructure challenge facing IATI extends beyond improving API access for human developers. It now encompasses a fundamentally different kind of consumer: **autonomous AI agents**.

### The Internet of AI Agents

MIT's **Project NANDA** (Networked Agents and Decentralized AI), led by Prof. Ramesh Raskar at the MIT Media Lab, is architecting the foundational infrastructure for what it describes as a true "Internet of AI Agents" — an emerging agentic web in which billions of specialized AI agents discover, verify and collaborate with each other and with external data sources in real time, operating autonomously across decentralized networks on behalf of organizations and individuals. NANDA envisions agents that perform discrete functions while communicating seamlessly, navigating autonomously, learning, and transacting on behalf of their deployers — drawing the analogy that just as the early web required DNS and HTTP protocols to scale, the agentic web requires its own foundational infrastructure layer.

### The Emerging Protocol Stack

The protocol layer underpinning the agentic web is already consolidating:

**Model Context Protocol (MCP)** — developed by Anthropic in November 2024 and now under the Linux Foundation's Agentic AI Foundation (AAIF) alongside contributions from Google, Microsoft, OpenAI and AWS — standardizes how an AI agent connects to external tools, data sources and services. It provides a universal interface between an AI system and the external resources it needs to act. MCP adoption has accelerated rapidly, with support now across all major AI platforms.

**Agent-to-Agent Protocol (A2A)** — developed by Google in April 2025 and also donated to the AAIF — standardizes how independent AI agents discover each other, establish secure communication and delegate tasks. Where MCP handles the agent-to-tool layer (vertical), A2A handles agent-to-agent coordination (horizontal).

**Micropayment protocols** — including Coinbase's **x402** (launched May 2025, which revives the dormant HTTP 402 "Payment Required" status code to embed payments directly into HTTP interactions) and Stripe/Tempo's **Machine Payments Protocol (MPP)** — make it economically viable for the first time to charge fractions of a cent per API call or data query. x402 processed over 100 million transactions in its first six months, with transaction fees below $0.0001. This makes agent-to-agent micropayments practical at scale.

Together, MCP, A2A and the emerging micropayment rails are becoming the consensus architecture for how agents interact with the world's information infrastructure.

### What This Means for IATI

Upgrading IATI for the agentic web means more than supporting complex API queries from human-directed applications. It means building infrastructure capable of receiving and correctly serving **populations of autonomous agents** arriving via MCP and A2A — agents that will expect to:

- Discover IATI's capabilities through agent registries (such as NANDA's AgentFacts index)
- Authenticate and establish secure sessions
- Execute precise multi-field, nested queries across hierarchical data
- Retrieve temporally versioned results that show how data has changed over time
- Pass structured, machine-readable outputs to other agents downstream
- Pay for data access and agent interactions via micropayment protocols
- All of this without human intermediation, at machine speed and scale

An IATI that cannot speak the protocols of the agentic web will be invisible to the next generation of humanitarian AI applications — not because the data isn't there, but because the infrastructure cannot answer the knock at the door.

---

## 8. IATI as an Agent Ecosystem

The agentic web opens a more ambitious possibility than simply making IATI queryable by outside agents. It creates the conditions for IATI to become an **active participant in the agent ecosystem** — not just a data source, but a platform that hosts, curates and operates its own agents.

### Platform-Native IATI Agents

IATI could develop and host its own platform-native agents — agents that understand the structure, history and semantics of the IATI corpus deeply, that can engage with incoming agent requests intelligently, proactively surface relevant information, and reach out to other agents across the agentic web on behalf of the humanitarian sector. These agents would serve as the authoritative interface between the world's humanitarian AI applications and the IATI knowledge graph — handling query translation, data validation, duplication resolution and result formatting automatically.

### A Publisher Agent Library

Equally important is the role of IATI's publisher community. The organizations that publish to IATI — donor governments, UN agencies, major NGOs and development finance institutions — each have their own operational data, domain expertise and user communities. In an agentic IATI ecosystem, these publishers could build and contribute their own **custom agents** to a shared IATI agent library:

- A **USAID agent** optimized to answer questions about US foreign assistance, structured around USAID's specific activity taxonomy and reporting practices
- A **UNHCR agent** with deep knowledge of refugee programme data, operational geographies and protection outcome indicators
- A **national government agent** that surfaces country-level aid coordination information, government budget alignment and recipient country priorities
- A **development bank agent** that understands multi-tranche financing structures, co-financing arrangements and project cycle stages
- A **sector specialist agent** — for health, education, food security or climate — that can interpret sector-specific results frameworks and cross-reference them with thematic benchmarks

Outside agents arriving at IATI would browse this library, select the agents most relevant to their task, and interface with them directly — combining the breadth of IATI's universal data infrastructure with the specialized knowledge of the organizations that generated the data in the first place.

### A Self-Sustaining Knowledge Economy

Through micropayment protocols, this agent library becomes economically self-sustaining. Publisher organizations receive micropayments each time their agent is selected and engaged — creating a direct financial incentive to build high-quality, well-maintained agents and to publish high-quality, comprehensive data. IATI's infrastructure development and data quality programs could be funded by query revenue rather than grants and membership fees alone. This is a fundamentally new economic model for humanitarian data infrastructure — one that aligns the incentives of data publishers with the needs of data consumers for the first time.

---

## 9. New Use Cases Enabled by an Agentic IATI

The combination of graph-native infrastructure, agentic protocol support and a publisher agent ecosystem opens an entirely new category of applications. What follows is a map of the use cases that become possible — none of which are achievable on top of IATI's current datastore architecture.

### 9.1 Metered Access and Micropayments for Data and Agent Services

Emerging micropayment protocols (x402, AP2, MPP) make it viable to charge fractions of a cent per API call or data query. Outside agents querying IATI's graph infrastructure could pay per query, per dataset or per agent interaction. Proceeds fund infrastructure, data quality programs and publisher agent development — creating a sustainable economic foundation that IATI currently lacks.

### 9.2 Real-Time Aid Coordination and Gap Detection

Coordination agents could continuously monitor incoming activity and transaction data across all publishers, cross-reference it against humanitarian response plan requirements, and proactively flag underfunded sectors, geographies or population groups — without waiting for a human analyst to run the query. Alerts push to donor agents, cluster coordination agents and government planning agents in real time.

### 9.3 Anticipatory Action and Predictive Funding Triggers

IATI agents could interface with early warning systems — flood models, drought indices, conflict forecasting tools — and automatically surface which organizations have activities and funding pipelines in affected areas, what their historical disbursement speeds look like, and which funding gaps are likely to emerge. Donor agents could use this to trigger pre-approved funding commitments autonomously, compressing the gap between warning and response from weeks to hours.

### 9.4 Automated Due Diligence and Partner Vetting

An IATI agent with access to the full activity history of any publishing organization — past projects, disbursement patterns, results reported, co-implementing partners, geographic footprint — could conduct structured preliminary due diligence autonomously. Outside agents representing donors could query IATI partner agents, receive structured AgentFacts-style profiles, and pass those to their own decision-support systems — dramatically reducing the time and cost of partner assessment.

### 9.5 Supply Chain Verification and Aid Delivery Confirmation

As humanitarian supply chains become increasingly instrumented — with IoT sensors, satellite tracking and digital payments — IATI agents could serve as a trusted verification layer, cross-referencing reported disbursements and activity completions against real-world delivery signals from logistics systems. Discrepancies are flagged for human review automatically.

### 9.6 Automated Reporting and Publishing Assistance

Publisher-side agents could monitor an organization's project management systems, financial databases and results frameworks, automatically translate that information into valid IATI XML, validate it against the schema and publish it to the registry — reducing the compliance burden to near zero. These agents could also benchmark publication quality against peer organizations and suggest improvements.

### 9.7 Cross-Standard Data Harmonization

IATI harmonization agents could autonomously map activities and transactions across standards (IATI, FTS, CRS, World Bank, country aid management platforms), resolve duplicate reporting, normalize currency and classification differences, and produce a unified picture of aid flows that no single source currently provides.

### 9.8 Natural Language Query Interfaces for Non-Technical Users

IATI-native conversational agents could receive natural language questions from government officials, journalists, researchers and community organizations — translate them into precise graph queries, and return structured, verified answers in plain language. This democratizes access to IATI data in ways the current Datastore and d-portal cannot.

### 9.9 Agent-to-Agent Negotiation for Resource Matching

IATI could host matching agents that connect organizations with unfunded activities to donors with unallocated budget — autonomously brokering resource matches based on thematic alignment, geographic focus, track record and donor priorities. This is the agentic equivalent of a funding marketplace, operating continuously at a scale no human matchmaking process can replicate.

### 9.10 Immutable Audit Trails and Accountability Verification

Every agent interaction with IATI data generates a structured log. Combined with temporal versioning, IATI could maintain an immutable, timestamped audit trail — recording which agents queried what, when commitments were reported, when results were updated and when discrepancies were flagged. This creates a verifiable accountability record that donors, governments, oversight bodies and the public can query.

### 9.11 Continuous Donor Portfolio Monitoring

Donor agents operating on behalf of bilateral agencies, foundations or institutional investors could maintain continuous awareness of their entire portfolio — tracking disbursement progress, results reporting, partner performance and budget versus actual spend across all implementing organizations simultaneously, surfacing anomalies and delays in real time.

### 9.12 SDG Progress Attribution and Impact Mapping

IATI agents could continuously aggregate and attribute reported results across the full publisher network — building a real-time, organization-level and country-level picture of contributions to specific SDG targets. Outside agents representing UN agencies, national governments and research institutions could query this attribution map to understand where investment is concentrated, where gaps remain, and which combinations of interventions are associated with the strongest reported results.

### 9.13 Knowledge Pricing and Specialized Data Markets

As the agentic web matures, specialized, high-quality data will command market prices in agent-to-agent transactions. IATI's publisher-contributed agents — each carrying deep institutional knowledge about specific geographies, sectors or funding streams — become valuable nodes in this knowledge economy. A UNHCR agent with verified refugee programme data, or a development bank agent with geocoded project data, commands a premium from outside agents seeking reliable, sourced information — turning IATI's publisher network into a distributed, economically productive knowledge market.

---

## 10. What IATI Plus Is Building

IATI Plus is an all-volunteer, open-source research initiative building the infrastructure layer that IATI needs to fulfill its potential — as a query platform, as an AI-ready data source, and as a participant in the emerging agentic web. The work described in this section is approached as an evolving research programme rather than a production deployment. Each component — the knowledge graph, the change detection pipeline, the MCP server, the agent framework — represents both a practical deliverable and a set of open research questions about how best to solve it. Documented findings, architectural decisions and implementation experiments are treated as outputs of equal value to working code.

The goal is to iterate through a series of technically demanding challenges — establishing proof-of-concept implementations and a documented foundation from which the IATI community, partner institutions and the wider open-source ecosystem can continue to build. Contributors who bring domain expertise in data engineering, graph databases, AI systems, humanitarian data, or the IATI standard itself are all working on genuinely unsolved problems. There is no established playbook for what IATI Plus is attempting to build.

### Core Infrastructure

**Versioned Knowledge Graph**: IATI Plus maintains a comprehensive archive of daily IATI data snapshots, building a longitudinal record of how the corpus changes over time. This enables temporal queries — not just "what is the current state of this activity?" but "how has it changed, and when?"

**Neo4j-Based Graph Database**: A live, graph-native representation of the IATI corpus that preserves and exposes the relational structure of the data — the connections between activities, organizations, transactions, locations and results — in a format that supports complex, nested, multi-field queries.

**Change Tracking**: Daily diffing of the IATI corpus identifies which activities have been added, modified or removed since the previous snapshot, enabling real-time awareness of changes across the publisher network.

**Full Schema Exposure**: Unlike the IATI Datastore, which exposes a limited subset of fields for querying, IATI Plus exposes the full IATI schema — all elements, all attributes, all nested structures — through graph-native query interfaces.

**XPath and XQuery Support**: For users who need to work directly with the canonical XML representation of IATI data, IATI Plus provides native support for XPath and XQuery operations.

### The Knowledge Graph as Research Sandbox

Beyond serving as production infrastructure, the IATI Plus knowledge graph is explicitly designed to function as a **data sandbox and experimental platform** — a stable, queryable foundation upon which a wide range of AI applications, analytical tools and reporting use cases can be mocked up, prototyped and stress-tested without needing to first solve the data access and normalization problems that have historically blocked this kind of work. The graph handles schema traversal, relational linking, temporal versioning and query execution; experimenters bring the application logic and the research questions.

Because the graph exposes the full IATI schema — including its extensible XML namespace architecture — it preserves the complete expressive range of what publishers have chosen to report, including fields and structures that IATI's own official tools do not surface. Publishers use IATI's namespace extension mechanism to report information that goes beyond the core schema: project-level qualitative narratives, custom results frameworks, sector-specific indicators, partner-defined impact metrics and more. The knowledge graph captures this extended data and makes it available for experimental applications that the core standard alone would not support.

This makes the IATI Plus sandbox an unusually rich environment for research. Some illustrative directions that the platform is designed to support:

- **AI application prototyping**: Building and testing conversational agents, retrieval-augmented generation systems, and natural language query interfaces against real humanitarian data at scale
- **Reporting use case development**: Mocking up new reporting tools — donor dashboards, country-level aid flow visualizations, results attribution maps, SDG progress trackers — using the full depth of the IATI corpus rather than filtered subsets
- **Schema and standard research**: Investigating what publishers are actually reporting through namespace extensions, understanding the gap between the core standard and what the sector is trying to express, and using findings to inform future standard development
- **Data quality analysis**: Examining consistency, completeness and comparability across the publisher network at a level of detail not previously possible
- **Agentic interaction design**: Experimenting with how autonomous agents should interact with humanitarian data — what query patterns work, what failure modes emerge, what grounding strategies produce reliable results
- **Cross-standard harmonization research**: Testing approaches to reconciling IATI data with FTS, CRS, World Bank and other sources at the activity and transaction level

The extensible nature of the IATI XML standard means the boundaries of what can be explored are themselves an open and expanding research frontier. As publishers push what IATI can express, the sandbox grows with them — and findings from sandbox experimentation feed directly back into the core infrastructure development, creating a reinforcing cycle between research and implementation.

**MCP Server**: An IATI MCP server that exposes the knowledge graph as a tool available to any MCP-compatible AI agent — enabling agents to discover IATI's capabilities, authenticate and execute queries through the standard agent-to-tool protocol.

**A2A Protocol Support**: Infrastructure for agent-to-agent interactions, enabling IATI's own agents to communicate with outside agents using the Agent-to-Agent protocol — supporting delegation, negotiation and collaborative task execution across agent networks.

**Agent Registry Integration**: Registration of IATI's agents and capabilities with registries like NANDA's AgentFacts index, making IATI discoverable to the population of agents operating on the agentic web.

**Publisher Agent Framework**: A framework and library that enables IATI publishers to build, register and contribute their own custom agents to the IATI agent ecosystem.

**Micropayment Infrastructure**: Integration with x402 and AP2 micropayment protocols to enable metered access to IATI data and agent services, supporting a sustainable economic model for the platform.

### Community and Collaboration

IATI Plus is an all-volunteer, open-source research initiative organized around a community of student volunteers, researchers, AI engineers, data scientists, humanitarian practitioners and technology contributors. It is managed by the **Humanitarian AI Meetup Community**, linking eighteen local meetup groups across ten countries. The project welcomes contributors at all levels — from those who want to help document architectural decisions and write prompt guidance, to those building and testing core pipeline components.

Because IATI Plus is a research programme as much as a software project, contributions that advance understanding are as valuable as contributions that advance the codebase. Writing up what you tried and why it did or didn't work, documenting a design decision, or identifying a research question the project hasn't yet addressed are all meaningful contributions.

The repository is structured to enable effective contribution with the support of AI coding assistants:

- `docs/` — Architecture, data model, workflow documentation, standards references and prompt guidance for human and AI contributors
- `src/` — Ingestion pipelines, change detection, Neo4j load processes, cloud storage and compute workflows, and testing infrastructure

Volunteers contribute by refining documentation and prompts, building and testing ingestion and diffing pipelines, provisioning cloud infrastructure, validating outputs, developing the agent framework and designing and running sandbox experiments.

**Contact:** team(at)humanitarianai.org

---

## 11. The Technical Challenges IATI Plus Is Tackling

Part of what makes IATI Plus a genuine research programme — rather than a conventional software project — is the nature of the problems it is working on. None of the core challenges described below have established, off-the-shelf solutions. Each represents an open technical question at the intersection of large-scale data engineering, graph database design, XML standards, and agentic AI systems. Documenting how these challenges are approached, what works, and what doesn't is itself a primary output of the project.

The challenges fall into three domains: loading and ingesting data into the knowledge graph; tracking changes and maintaining temporal integrity; and making the graph accessible and engageable by AI agents.

---

### Challenge Domain I: Data Ingestion and Loading

**Scale and pipeline reliability.** The IATI corpus exceeds 32GB of XML distributed across thousands of individual files hosted on the servers of 1,650+ publishers worldwide. Downloading, validating and processing the full corpus daily — reliably, within a practical time window — is a non-trivial pipeline engineering problem. Any given daily run may encounter unreachable publisher endpoints, malformed XML, character encoding errors, partially updated files, or servers that respond inconsistently. Building a pipeline that handles this gracefully, logs failures meaningfully, and recovers without corrupting the archive is a foundational challenge the project must solve before anything else is possible.

**XML parsing and canonicalization.** Before any IATI record can be loaded into the graph, it must be parsed, normalized and validated. XML Canonicalization (C14N) — which produces a stable, byte-identical representation of an XML document regardless of superficial formatting differences — is required to produce representations suitable for diffing and comparison. Applying C14N consistently and correctly across a corpus of this scale and heterogeneity, while handling the full range of XML encoding edge cases that real-world publisher files contain, is technically demanding work.

**Schema mapping to a graph model.** IATI's hundreds of elements, attributes, nested structures, codelists and namespace extensions must be mapped to a coherent Neo4j node-and-relationship model. This design decision has long-lasting consequences: too flat and the graph loses the relational structure that makes it valuable; too granular and it becomes unwieldy to query efficiently. There is no established reference implementation for mapping IATI XML to a graph database. Designing, testing and iterating on this mapping — and documenting the decisions made and why — is a core research contribution of the project.

**Namespace extension handling.** IATI's extensibility allows publishers to include data outside the core schema using XML namespace extensions. These extensions contain information that publishers have determined is important but that the standard does not yet accommodate — making them a valuable signal about emerging data needs. Deciding what to capture from extensions, how to model it in the graph, and how to surface it for querying without breaking the core schema model is an open design problem with no precedent in the IATI ecosystem.

**Codelist and reference data versioning.** IATI relies on controlled vocabularies — sector codes, country codes, transaction types, aid types, policy markers and many more — that are themselves versioned and periodically updated by the IATI Secretariat. The graph must correctly resolve these references, handle the fact that a code's meaning may have changed between versions, and maintain consistency across a corpus where different publishers may be referencing different codelist versions at the same time.

**Duplicate activity resolution.** The same aid activity is frequently reported by multiple organizations — a donor government reports the commitment while the implementing NGO reports the disbursement and results. These are the same real-world activity described from different perspectives. Identifying, linking and reconciling these duplicates at ingestion time — without incorrectly merging genuinely distinct activities — is a subtle data quality problem that significantly affects the usefulness of any analysis performed on the graph.

---

### Challenge Domain II: Change Tracking and Temporal Versioning

**Reliable daily diffing.** The core change-tracking mechanism requires comparing each day's XML snapshot against the previous day's, identifying which activities have been added, modified or removed, and computing structured change events that can be stored and queried in the graph. This sounds straightforward but is technically subtle: minor formatting changes in XML that carry no semantic difference — whitespace, attribute ordering, encoding variations — must not be treated as meaningful changes. XML canonicalization addresses this in principle, but getting it right consistently across 32GB of heterogeneous publisher data at daily cadence is an engineering challenge that requires careful testing and validation.

**Change granularity design.** When an IATI activity changes, the change may be at any level of nesting — a transaction amount, a result indicator value, a partner name, a budget revision, a document link. Deciding how granularly to track and represent these changes in the graph — and how to store them in a way that supports efficient temporal queries without creating an unmanageable volume of change nodes — involves significant design tradeoffs between completeness, query performance and storage cost. These tradeoffs need to be explored empirically, not just theorized.

**Point-in-time reconstruction.** The project's architecture calls for each IATI activity to exist in the graph as both a current node and a chain of versioned historical nodes with `valid_from` and `valid_to` timestamps, enabling queries that reconstruct the state of the aid landscape at any point in time. Maintaining this versioned chain correctly as the corpus evolves daily — ensuring no inconsistencies, orphaned nodes, broken chains or timestamp conflicts accumulate over months and years of operation — requires careful transaction design and ongoing integrity monitoring.

**Publisher irregularities and disappearing data.** Publishers do not update their IATI data on a consistent schedule. Some publish daily, some monthly, some sporadically. An activity that disappears from a publisher's feed on a given day may have been genuinely completed, accidentally omitted from an export, temporarily unavailable due to a server issue, or moved to a different file. Distinguishing these cases programmatically — and deciding how each should be represented in the temporal graph — requires heuristics, validation logic and potentially human review workflows that need to be designed and tested.

**Storage architecture and long-term cost.** A daily snapshot archive of a 32GB+ corpus accumulates storage at significant and growing cost. Designing an AWS S3 architecture that is cost-effective, supports retrieval at arbitrary historical points, remains manageable over a multi-year horizon, and is affordable for a volunteer-run project with no guaranteed funding requires careful thinking about compression strategies, partitioning schemes, retention policies and tiered storage approaches.

---

### Challenge Domain III: AI Agent Access and Engagement

**Graph schema design for agent query performance.** A Neo4j graph optimized for human browsing may perform poorly under the multi-hop, multi-field, aggregation-heavy queries that AI agents will generate at machine speed and scale. Indexes, query patterns and graph topology all need to be co-designed with the agent query workload in mind — but that workload is not yet well-defined, because the agent applications do not yet exist. This is a genuine chicken-and-egg research problem: the schema shapes what queries are possible, the queries reveal what the schema needs to support, and neither side of this relationship is fixed. Iterating toward a schema design that performs well for the full range of intended agent uses is an ongoing research task.

**Natural language to Cypher translation.** For AI agents to query the knowledge graph via natural language instructions, the system needs a reliable mechanism for translating those instructions into valid Neo4j Cypher queries against a complex schema with hundreds of node types, relationship types and properties. Large language models can generate plausible Cypher, but correctness — especially for complex multi-hop queries, aggregations and temporal filters — is not guaranteed. Designing the query generation layer, the validation and error recovery strategies, and the grounding mechanisms that ensure agent queries return accurate rather than plausible-sounding results is a core research problem.

**MCP server design.** Building an MCP server that correctly exposes the knowledge graph as a tool available to any MCP-compatible AI agent requires designing a clean, well-documented tool interface — defining what operations are exposed, what parameters they accept, what outputs they return, how errors are communicated, and how the server's capabilities are advertised to agent discovery systems. The design of this interface has significant downstream implications for what kinds of queries agents can express, how reliably they can use the results, and whether the interface remains useful as both the graph and the MCP specification evolve.

**A2A protocol integration.** Agent-to-agent communication via the A2A protocol requires IATI's own agents to advertise their capabilities in machine-readable formats, accept and execute delegated tasks from outside agents, negotiate capability boundaries, handle authentication and trust, and return structured results that downstream agents can reliably consume. The patterns and best practices for doing this correctly — especially in a humanitarian data context where result accuracy has real-world consequences — are not yet established in any reference implementation. IATI Plus would be among the first deployments to tackle this at domain-specific scale.

**Authentication, rate limiting and access control.** A publicly accessible knowledge graph serving populations of autonomous agents — some operating at high query volumes — requires robust authentication, rate limiting, and access control infrastructure. Without these, the graph is vulnerable to abuse, exhaustion of compute resources, and denial-of-service from runaway agent loops. Designing a system that is open enough to support a volunteer research community and its sandbox experiments, while secure and stable enough to serve production agent traffic, is a genuine architectural tension with no obvious off-the-shelf resolution.

**Micropayment integration.** Integrating x402 or AP2 micropayment protocols into the platform requires correctly metering usage at query or session level, authenticating payment claims in real time, handling failed or disputed payments gracefully, maintaining an audit trail of transactions, and ensuring that the payment layer does not introduce latency or failure modes that degrade the agent experience. These are capabilities that do not yet have widely adopted reference implementations, and designing them for a research platform that may not yet have production traffic requires careful scoping of what to build and validate first.

**Reliability for agent dependents.** Autonomous agents that depend on IATI Plus as a data source will fail silently, produce wrong results, or enter error loops if the graph is unavailable, stale or returning malformed responses. Building the monitoring, alerting, graceful degradation, circuit-breaking and recovery mechanisms that make the platform reliably available — as a volunteer project with no dedicated operations team and no SLA obligations — is a genuine operational challenge that grows in importance as the platform is adopted by real agent applications.

---

### Why These Challenges Matter Beyond IATI Plus

The technical challenges IATI Plus is working on are not unique to IATI. They represent a broader category of problems that any organization attempting to make a large, heterogeneous, real-world open dataset accessible to autonomous AI agents will face. The approaches, architectures, failure modes and solutions that IATI Plus documents through its research will be directly applicable to other humanitarian and development data platforms, and potentially to the wider open data ecosystem. In this sense, IATI Plus is not just building infrastructure for IATI — it is contributing to a growing body of practical knowledge about how to make the world's open data resources genuinely usable by the next generation of AI systems.

---

## 12. Reference: The Sector's Data Landscape

The following is a reference map of the major data sharing frameworks, portals and repositories used across the humanitarian and development sector — provided as context for understanding IATI's position and how IATI Plus relates to the broader ecosystem.

### Open Data Standards and Reporting Frameworks

**IATI — International Aid Transparency Initiative** | https://iatistandard.org
The dominant open data publishing standard for development and humanitarian activities. Covers the full activity lifecycle in structured XML across 1,650+ publishing organizations.

**OECD DAC Creditor Reporting System (CRS)** | https://data-explorer.oecd.org
The official statistical reporting system for Official Development Assistance (ODA). Covers 28 DAC member governments. Authoritative for aggregate ODA statistics; limited depth at activity level.

**HXL — Humanitarian Exchange Language** | https://hxlstandard.org
A lightweight tagging standard that adds machine-readable metadata to existing spreadsheets and CSV files. Improves interoperability without requiring system changes.

**SDMX — Statistical Data and Metadata eXchange** | https://sdmx.org
An ISO standard for statistical data exchange, used widely by the UN system, World Bank and IMF.

### Global Data Portals and Repositories

**HDX — Humanitarian Data Exchange** | https://data.humdata.org
OCHA's open data platform for humanitarian information. Hosts 20,000+ datasets from 1,900+ sources. A repository, not a publishing standard.

**World Bank Open Data / Data360** | https://data.worldbank.org
Free access to global development indicators, microdata and project data from the World Bank Group.

**UN Data** | https://data.un.org
Gateway to 32 UN system statistical databases covering 60+ million records.

**ReliefWeb** | https://reliefweb.int
OCHA's humanitarian information platform: news, reports, maps and situation updates on crises worldwide.

**d-portal** | https://d-portal.org
IATI's own visualization and exploration tool for browsing published activity data by country, organization and sector.

### Financial Tracking and Aid Flow Platforms

**FTS — Financial Tracking Service** | https://fts.unocha.org
OCHA's real-time database of humanitarian funding flows, mapped against response plan requirements. Publishes to IATI.

**AidData** | https://www.aiddata.org
Research lab at the College of William & Mary tracking development finance with geocoded, research-grade datasets.

**TOSSD — Development Finance Portal** | https://www.tossd.org
Tracks Total Official Support for Sustainable Development, including private finance mobilized by official actors.

**Open Contracting Data Standard (OCDS)** | https://www.open-contracting.org
Open data standard for government contracting and procurement, used in development contexts for accountability monitoring.

### Sector-Specific and Thematic Platforms

**WFP HungerMap Live** | https://hungermap.wfp.org — Real-time food security monitoring

**UNHCR Refugee Data Finder** | https://www.unhcr.org/refugee-statistics — Forced displacement statistics

**FAOSTAT** | https://www.fao.org/faostat — Food, agriculture and nutrition data across 245 countries

**ACLED** | https://acleddata.com — Disaggregated conflict and political violence event data

**EM-DAT** | https://www.emdat.be — International disaster database since 1900

**WHO Global Health Observatory** | https://www.who.int/data/gho — Health statistics for 194 countries

### National and Donor-Specific Trackers

**UK Development Tracker** | https://devtracker.fcdo.gov.uk — UK ODA project-level data, IATI-aligned

**EU Aid Explorer** | https://euaidexplorer.ec.europa.eu — EU development and humanitarian aid tracking

**USAID Development Data Library** | https://data.usaid.gov — USAID program datasets and evaluations

**Australian Aid Tracker** | https://www.dfat.gov.au/aid/aid-tracker — Australian ODA project data, IATI-aligned

### SDG and Global Monitoring

**SDG Global Indicators Database** | https://unstats.un.org/sdgs — UN Statistics Division's official SDG progress data

**Our World in Data** | https://ourworldindata.org — Long-run development, health and poverty trends, widely used by researchers and media

---

---

## 13. IATI's 2030 Strategic Plan and Its Relationship to IATI Plus

In 2025, IATI's membership unanimously endorsed the **IATI Strategic Plan 2026–2030**, adopted formally at the 2025 Members' Assembly and recognized at the Fourth International Conference on Financing for Development in Sevilla, where the Compromiso de Sevilla outcome document specifically recognized IATI's role in fostering transparency of development cooperation. The plan was informed by a year-long global consultation process, with in-person workshops in Brussels, Nairobi and Abidjan, online consultations and bilateral interviews across the IATI membership and wider community. It represents the clearest and most ambitious statement IATI has ever made about where it needs to go.

Understanding the 2030 Strategic Plan is important context for understanding IATI Plus — because the plan explicitly identifies the same infrastructure gap that IATI Plus is building to close, and because IATI Plus is positioned to serve as a practical delivery mechanism for the plan's most technically demanding commitments.

### The Plan's Central Diagnosis

The Strategic Plan opens with an honest and important admission: despite seventeen years of progress and a corpus covering trillions of dollars in development finance, *simply publishing data is not enough*. IATI's own evaluations and community feedback have identified a persistent "usability gap" — data that is published but not used, infrastructure that is technically available but practically inaccessible, and a growing mismatch between what IATI's publishers produce and what IATI's users actually need. The plan calls explicitly for IATI to "shift from a passive repository to an active driver of data use and accountability."

This is precisely the problem IATI Plus is building to solve.

### The Strategic Vision: Transparency 1.0 → 2.0 → 3.0

The plan frames IATI's evolution across three phases of transparency ambition:

**Transparency 1.0 — Data Availability and Quality:** The phase IATI has largely completed. Publishing comprehensive, standardised, open, machine-readable data. Establishing the availability of information through IATI's open data standard.

**Transparency 2.0 — Data Usability and Uptake:** The phase IATI is now entering. Making IATI data more interoperable, relevant and user-friendly so that it is routinely integrated and used by stakeholders. This involves improving relevance, advocacy and usability of tools — including AI-ready data and user-centric interfaces — to drive deeper and broader uptake.

**Transparency 3.0 — Contribution to Impact:** The aspired future phase by 2030. Demonstrating a clear, attributable line from publishing data to achieving better development outcomes on the ground. Understanding how data use improves coordination, planning, budgeting, accountability and learning in international cooperation.

IATI Plus is infrastructure for the Transparency 2.0 transition — without graph-native querying, temporal versioning and agentic protocol support, there is no path to the data usability and uptake the plan requires. It is also a prerequisite for Transparency 3.0, because impact attribution requires being able to track changes in activities, transactions and results over time — which requires the versioned historical archive IATI Plus is building.

### Two Core Outcomes

The plan commits IATI to two reinforcing outcomes by 2030:

**Outcome 1 — Enhanced Data Use:** All stakeholders systematically use development cooperation data, leading to greater transparency, mutual accountability and better decisions at local, national and global levels. By 2030, IATI data will be routinely embedded in government budgeting and planning systems, civil society monitoring, donor portfolio management and crisis coordination.

**Outcome 2 — More Accountable and Effective International Cooperation:** An open, trusted and comprehensive evidence base informs international cooperation, so that resources are better aligned with needs and results. IATI becomes a comprehensive global public data platform, trusted for quality, completeness and near-real-time updates — covering not just ODA but climate finance, South-South cooperation, philanthropy and private investment flows.

Both outcomes are directly served by IATI Plus infrastructure. Enhanced data use requires queryable, accessible, AI-ready data. A trusted comprehensive evidence base requires temporal versioning, duplication resolution, cross-standard harmonization and schema-complete indexing.

### Four Action Areas and Where IATI Plus Fits

**Action Area A — Strengthening Country Data-Use Systems**
The plan commits IATI to embedding data in country-level planning, financial management and budgeting systems, explicitly including "AI, automation and machine-assisted analytics." It calls for direct integration of IATI databases into finance ministry systems, parliament monitoring tools and civil society platforms. IATI Plus's graph-native query infrastructure and natural language agent interfaces are the technical layer that makes this integration practical — without them, embedding IATI data into country systems requires each country to build its own data engineering pipeline from scratch.

**Action Area B — Enhancing IATI Infrastructure for Data Quality and Usability**
This is the action area most directly aligned with IATI Plus's core work. The plan commits to:
- Transforming IATI's technical infrastructure toward a "unified backend and frontend architecture"
- Making IATI "AI-ready" so that qualitative data, documents and results can be leveraged with AI tools for insight generation
- Improving interoperability with OECD CRS, OCHA FTS and other standards
- Supporting AI-assisted data extraction, data quality dashboards and auto-fill tools to reduce publishing burden
- Moving toward "publish once, use everywhere" through greater interoperability
- Deploying AI technologies for data validation, translation and insight generation

The plan also explicitly acknowledges: *"Adoption of AI agentic tools for structured-data and analytics will continue to increase exponentially, and as such the basic understanding of what 'data access' and 'data use' mean will evolve significantly."* This is a direct recognition that the agentic web IATI Plus is building for is not a speculative future but a near-term reality that IATI's infrastructure must prepare for.

**Action Area C — Championing Transparency and Accountability**
The plan calls for IATI to expand and diversify its membership, engage more assertively in global policy forums, and champion transparency as a global public good. It explicitly notes that IATI data is registered as a **Verified Digital Public Good** with the Digital Public Goods Alliance. IATI Plus's open-source, community-driven model aligns directly with this framing — building infrastructure that is itself a public good, contributed to by a global community of volunteers, researchers and organizations.

**Action Area D — Promoting IATI Data in Policy Dialogues**
The plan commits to bridging the gap between data and policy, including "potentially with AI-enabled systems for analysis and decision-making" to curate data insights for global policy audiences. IATI Plus's natural language agent interfaces and publisher agent library are the practical realization of this commitment — enabling non-technical policy audiences to interact with IATI data in natural language, through agents that understand the structure and semantics of the corpus.

### Financial Sustainability and the IATI Plus Economic Model

The plan acknowledges that IATI's membership model and financing approach need renewal to ensure sustainability, and commits to diversifying the funding base through voluntary contributions, pooled trust funds and exploration of philanthropic and private sector sources. It is notable that the plan explicitly states: *"IATI's data and standard will remain open and free to all as a global public good."*

IATI Plus's micropayment architecture — which enables metered access to premium query infrastructure and publisher agent services — is consistent with this commitment: the data remains open and free, while the query infrastructure and agent services that add computational value on top of it can be sustainably funded through usage-based revenue. This model, where the raw data is a public good but the intelligence layer on top is economically productive, is precisely the kind of financing innovation the plan's sustainability agenda calls for.

### What the Plan Does Not Yet Address

The 2030 Strategic Plan is forward-looking and ambitious, but it was written before the agentic web's protocol stack had fully consolidated. The plan refers to AI tools and AI-ready infrastructure, and acknowledges that the meaning of "data access" and "data use" will evolve significantly — but it does not yet articulate a specific response to MCP, A2A, the micropayment protocols, or the NANDA vision of an Internet of AI Agents in which IATI would need to function as a discoverable, interoperable agent ecosystem node.

This is the gap IATI Plus fills between the plan's ambitions and the emerging technical reality. The plan sets the strategic direction: IATI must become a driver of data use, AI-ready, and embedded in global accountability systems. IATI Plus provides the infrastructure architecture that makes that vision achievable in the specific context of the agentic web — graph-native querying, temporal versioning, MCP/A2A protocol support, publisher agent frameworks and micropayment integration.

### Summary Alignment Table

| IATI 2030 Strategic Commitment | IATI Plus Response |
|---|---|
| Shift from passive repository to active data use driver | Graph-native knowledge graph with complex query capability |
| AI-ready infrastructure for insight generation | MCP server, A2A protocol support, natural language agent interfaces |
| Temporal data — near real-time updates and change tracking | Daily snapshot archive and change detection pipeline |
| Interoperability across IATI, CRS, FTS and other standards | Cross-standard harmonization agents |
| Reduce publishing burden — "publish once, use everywhere" | Automated publisher agents for IATI XML generation and validation |
| Embed IATI data in country planning and financial systems | Queryable API layer usable by national systems without custom pipelines |
| AI-enabled policy dialogue support | Natural language query agents and publisher-contributed specialist agents |
| Financial sustainability beyond traditional donor funding | Micropayment infrastructure (x402/AP2) for sustainable query revenue |
| IATI as a global public good | Open-source codebase, community-governed, Humanitarian AI Meetup network |
| Agentic AI tools for analytics (recognized but not yet architected) | Full agentic web participation: agent registry, publisher agent library, A2A negotiation |

The IATI 2030 Strategic Plan is the mandate. IATI Plus is part of the infrastructure that delivers it.

---

*This document was prepared by the IATI Plus project team. For more information or to get involved, contact team(at)humanitarianai.org. IATI Plus is managed by the Humanitarian AI Meetup Community, linking eighteen local groups across ten countries.*

*Last updated: May 2026*
