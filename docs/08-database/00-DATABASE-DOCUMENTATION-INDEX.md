# Phase 4 — Database Documentation
## 00. Database Documentation Master Index

```
====================================================================================================
STATUS:
PHASE 4 FOUNDATION — DOCUMENTATION ONLY — INITIAL ARCHITECTURE ESTABLISHMENT

IMPORTANT GOVERNANCE NOTICE:
This phase is STRICTLY DOCUMENTATION ONLY. 
No application code, database migration files, SQL DDL/DML scripts, Prisma schemas, TypeORM entities,
or physical database tables are created or modified during this phase. 
The official baseline of 104 atomic requirements (docs/01-requirements/02-REQUIREMENT-CATALOGUE.md),
59 business processes (docs/02-business-process/), 60 business rules, and the approved Technology 
Architecture Baseline (TECHNOLOGY_ARCHITECTURE_BASELINE.md) remain strictly frozen and uncompromised.
====================================================================================================
```

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/08-database/00-DATABASE-DOCUMENTATION-INDEX.md` |
| **System Phase** | Phase 4 — Database Documentation |
| **Project Name** | University HR Change Management & Automation System |
| **Document Purpose** | Master index, governance framework, roadmap, and scope specification for Phase 4 Database Documentation |
| **Date of Preparation** | September 29, 2026 |
| **Authoritative Baselines** | `docs/01-requirements/` (104 Frozen Requirements); `docs/02-business-process/` (59 Frozen Processes); `docs/03-functional-requirements/` (Approved FRDs); `docs/07-system-architecture/` & `TECHNOLOGY_ARCHITECTURE_BASELINE.md` |
| **Database Technology Baseline** | **PostgreSQL** (Primary Relational System of Record); **Redis** (Supporting In-Memory Cache, Pub/Sub & Queue Broker) |
| **Architecture Pattern** | **Modular Monolith** (NestJS + TypeScript) |

---

## 1. Purpose of Phase 4 Database Documentation

The purpose of Phase 4 (Database Documentation) is to translate the established and frozen business requirements, business processes, and functional requirement specifications into a comprehensive, rigorously specified **relational database architecture** for the University HR Change Management & Automation System.

Phase 4 defines the conceptual, logical, and structural blueprints required to ensure that:
1. **Single Source of Truth:** The database functions as the authoritative, institutional System of Record, eliminating redundant employee data entry across university departments.
2. **Relational Data Integrity:** Strict ACID transactional consistency, referential integrity, and domain constraints govern all employee service records, recruitment funnels, and performance evaluations.
3. **Temporal History & Auditability:** No historical employee service records or evaluation scorecards are destructively overwritten. Every master record change, workflow approval, and compensation revision maintains an immutable, time-stamped audit trail with effective-date scheduling.
4. **Data Isolation & Staging:** Pending, rejected, or future-dated changes are strictly separated from current, approved master employee data.
5. **Modular Monolith Encapsulation:** Domain boundaries defined in the backend architecture are respected at the database layer, establishing clear module data ownership without raw cross-domain writes.
6. **Strict Source Grounding:** Every database entity, relationship, and lifecycle state traces directly back to frozen requirements (`REQ-*`), business processes (`BP-*`), business rules (`BR-*`), or approved functional requirements (`MOD*-REQ-*`).

---

## 2. Scope of Database Documentation

The scope of Phase 4 database documentation covers the complete data persistence requirements across all modules and shared services of the University HR platform:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            PHASE 4 DATABASE DOCUMENTATION SCOPE                                  │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ MODULE I DATA DOMAINS         │ MODULE II DATA DOMAINS         │ MODULE III DATA DOMAINS         │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ • Central Employee Database   │ • Academic Manpower Planning   │ • Subsystem 1: Group-D Monthly  │
│ • Organization Hierarchy      │   (Teaching Loads, Attach. 1)  │   & Annual Appraisals           │
│ • Dynamic Org Chart Nodes     │ • Non-Academic Manpower Plans  │ • Subsystem 2: General Staff    │
│ • Digital Personal Dossiers   │ • Manpower Requisition Forms   │   KRA/KPI Lifecycle (Q1–Q4)     │
│ • 10 Service Change Formats   │   (Planned vs Urgent MRFs)     │ • Subsystem 3: Faculty Annual   │
│ • 2-Level Approval History    │ • Open Positions Tracker       │   Appraisals (ECM Route)        │
│ • Effective-Date Scheduler    │ • Omnichannel CV Repository    │ • Multi-Unit Verification Logs  │
│ • Employee Service History    │ • Recruiter Calling Sheet (RCS)│ • Digital ECM Score Sheets      │
│ • ERP Outbox Staging Records  │ • Statutory Academic SCM Panels│ • TNU Protocol Matrix Records   │
│                               │ • Non-Academic 3-Round Panels  │ • Compensation Revisions & Slabs│
│                               │ • LOI & Pre-Onboarding ("YTJ") │                                 │
├───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┤
│ SHARED & PLATFORM-WIDE DATA DOMAINS                                                             │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ • Identity, Authentication Credentials & Session Storage                                         │
│ • Role-Based Access Control (RBAC) & Contextual Row-Level Data Scoping Rules                     │
│ • Universal Workflow Engine States, Transitions & Approval Comments                              │
│ • SLA Countdown Timers, Grace Period Cutoffs & Automated Lockout Timestamps                      │
│ • Document & Attachment Metadata (Abstracted Object Storage Pointers & SHA-256 Hashes)           │
│ • Multi-Channel Notification Templates & Delivery Logs                                           │
│ • Immutable Append-Only Audit Trail & Point-in-Time Version History                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Authoritative Source Documents

Phase 4 database documentation is derived directly and exclusively from the approved and frozen project artifacts:

1. **Requirements Documentation (`docs/01-requirements/`):**
   - [`01-PROJECT-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/01-PROJECT-REQUIREMENTS-SPECIFICATION.md) — System purpose, core structures, and requirements baselines.
   - [`02-REQUIREMENT-CATALOGUE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md) — 104 frozen atomic requirements across Modules I, II, III, Shared, Integration, Security, and Reporting.
   - [`03-SCOPE-AND-BOUNDARIES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/03-SCOPE-AND-BOUNDARIES.md) — Module boundaries, in-scope data flows, and out-of-scope constraints.
   - [`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md) — Frozen register of 11 baseline open decisions (`REQ-TBD-01` to `11`).
   - [`09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md) — Informational review artifact synthesizing candidate changes and open confirmation items (Reference only; NOT an approved requirement baseline).
   - [`10-STAKEHOLDER-DECISION-SHEET.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md) — Pending stakeholder decision register (Reference only; decisions remain unconfirmed and do not alter the frozen baseline).
2. **Business Process Documentation (`docs/02-business-process/`):**
   - [`01-BUSINESS-PROCESS-FRAMEWORK.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-FRAMEWORK.md) — Master lifecycle maps, actor matrices, and cross-cutting workflow standards.
   - [`02-MODULE-1-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-MODULE-1-BUSINESS-PROCESSES.md) — 12 business processes governing employee master records, service change lifecycles, and audit logging (`BP-M1-001` to `012`).
   - [`03-MODULE-2-ACADEMIC-RECRUITMENT-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/03-MODULE-2-ACADEMIC-RECRUITMENT-PROCESSES.md) — 12 academic recruitment processes (`BP-M2-ACAD-001` to `012`).
   - [`04-MODULE-2-NON-ACADEMIC-RECRUITMENT-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/04-MODULE-2-NON-ACADEMIC-RECRUITMENT-PROCESSES.md) — 8 non-academic recruitment processes (`BP-M2-NACAD-001` to `008`).
   - [`05-MODULE-3-PERFORMANCE-MANAGEMENT-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/05-MODULE-3-PERFORMANCE-MANAGEMENT-PROCESSES.md) — Performance management processes across Subsystem 1 (Group-D), Subsystem 2 (KRA/KPI Staff), and Subsystem 3 (Faculty ECM).
   - [`06-CROSS-MODULE-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/06-CROSS-MODULE-BUSINESS-PROCESSES.md) — Cross-module handshakes (`BP-XMOD-001` to `005`).
   - [`07-BUSINESS-RULES-CATALOGUE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/07-BUSINESS-RULES-CATALOGUE.md) — 60 formal business rules (`BR-M1-*`, `BR-M2-*`, `BR-M3-*`, `BR-SYS-*`).
   - [`08-BUSINESS-PROCESS-SLA-AND-ESCALATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/08-BUSINESS-PROCESS-SLA-AND-ESCALATION.md) — Master SLA matrices, notification countdowns, and lockout rules.
3. **Functional Requirements Specifications (`docs/03-functional-requirements/`):**
   - [`01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md) — Change management functional specifications.
   - [`02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md) — Recruitment & selection functional specifications.
   - [`03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md) — Performance management functional specifications.
   - [`04-SHARED-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md) — Cross-cutting functional specifications.
4. **Architecture Baseline (`docs/07-system-architecture/` & Root):**
   - [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md) — Approved Modular Monolith architecture, technology stack, and component boundaries.
   - [`docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md) — Socket.IO real-time notification layer and cache invalidation.

---

## 4. Database Technology Baseline

The system database architecture adheres strictly to the approved technical baseline:

| Dimension | Approved Technology / Baseline Specification | Architectural Rationale | Classification |
|---|---|---|---|
| **Primary Database Engine** | **PostgreSQL** (Current Stable Release) | Serves as the authoritative **System of Record**. Provides full ACID transactional guarantees, relational foreign key constraints, temporal timestamping, check constraints, and semi-structured dynamic form support. | `[C] Approved Technical Decision` |
| **Supporting In-Memory Store** | **Redis** (Current Stable Release) | Dedicated in-memory data store supporting high-speed caching (Organization Chart hierarchy tree, active role permissions), real-time WebSocket pub/sub adapters, and job queue persistence for asynchronous background workers. **Redis is NOT a persistent system of record.** | `[C] Approved Technical Decision` |
| **Backend Framework Pattern** | **Modular Monolith** (NestJS + TypeScript) | Implemented as a single deployable application with strict internal domain boundaries. All domain modules interface with the PostgreSQL database through encapsulated repository interfaces. | `[C] Approved Technical Decision` |
| **Persistence Boundary Rule** | **Single Unified PostgreSQL Database with Logical Domain Separation** | The application operates against a unified PostgreSQL database instance, preserving atomic transactions across domain boundaries while maintaining logical domain ownership. Physical PostgreSQL schema partitioning remains a downstream design decision unless explicitly required by the approved baseline. | `[C] Approved Technical Decision` |
| **Binary Document Storage** | **Object Storage** (S3-Compatible API) | Resumes, certificates, evaluation evidence, and auto-generated PDFs are stored in durable object storage. PostgreSQL stores strictly metadata, file keys, MIME types, and SHA-256 hashes. | `[C] Approved Technical Decision` |

---

## 5. Planned Phase 4 Database Documentation Structure

Phase 4 database documentation is planned as a structured series of progressive documents. To maintain strict governance, individual detailed documents will be established sequentially without premature implementation:

```
docs/08-database/
│
├── 00-DATABASE-DOCUMENTATION-INDEX.md            ◄ [CURRENT DOCUMENT: Master Index & Governance]
├── 01-DATABASE-DESIGN-OVERVIEW.md                ◄ [FOUNDATION: High-Level Architecture & Design Principles]
├── 02-DATA-MODEL-OVERVIEW.md                     ◄ [FOUNDATION: Conceptual Data Domains & Entities]
│
├── [PLANNED FUTURE DOCUMENTS — TO BE CREATED SEQUENTIALLY]
│
├── 03-ENTITY-IDENTIFICATION.md                   ◄ (Detailed entity inventory, domain boundaries & classifications)
├── 04-ENTITY-RELATIONSHIP-SPECIFICATION.md       ◄ (Entity-relationship diagrams [ERD] & cardinality models)
├── 05-ENTITY-WISE-DETAILED-SPECIFICATION.md       ◄ (Comprehensive entity definitions, business semantics & lifecycles)
├── 06-DATABASE-SCHEMA-SPECIFICATION.md           ◄ (Logical relational tables, columns, data types & defaults)
├── 07-CONSTRAINTS-AND-RELATIONSHIPS.md           ◄ (Primary keys, foreign keys, unique constraints & check rules)
├── 08-AUDIT-AND-VERSION-HISTORY-MODEL.md         ◄ (Immutable audit ledger schema, diff tracking & actor attribution)
├── 09-EFFECTIVE-DATE-DATA-MODEL.md               ◄ (Temporal activation schema, pending states & point-in-time querying)
├── 10-INDEXING-STRATEGY.md                       ◄ (B-Tree, GIN, composite indexes & query performance optimization)
├── 11-DATA-INTEGRITY-CONSIDERATIONS.md           ◄ (ACID transactional boundaries, outbox pattern & consistency guards)
└── 12-DATABASE-QUALITY-REVIEW.md                 ◄ (Traceability audit, governance verification & baseline compliance)
```

---

## 6. Document Status & Lifecycle

- **Current Status:** `PHASE 4 INITIAL FOUNDATION — DOCUMENTATION ONLY`.
- **Approved Documents in Current Pass:**
  1. `00-DATABASE-DOCUMENTATION-INDEX.md` (Master Index & Governance)
  2. `01-DATABASE-DESIGN-OVERVIEW.md` (Database Architecture & Design Overview)
  3. `02-DATA-MODEL-OVERVIEW.md` (Conceptual Data Model Overview)
- **Lifecycle Transition:** Detailed schema specifications, ERDs, and physical constraints will be elaborated sequentially in subsequent planned documents (`03` through `12`) following completion and governance verification of the current foundation documents.

---

## 7. Dependency on Upstream Documentation Layers

Phase 4 database documentation maintains strict backward traceability to all prior completed phases:

```
[Phase 1: Requirements Baseline (104 Atomic Requirements)]
                     │
                     ▼
[Phase 1.5: Technology Architecture Baseline (PostgreSQL + NestJS Modular Monolith)]
                     │
                     ▼
[Phase 2: Business Process Baseline (59 Business Processes + 60 Business Rules)]
                     │
                     ▼
[Phase 3: Functional Requirements Specifications (FRDs for Mod I, II, III, Shared)]
                     │
                     ▼
====================================================================================
[PHASE 4: DATABASE DOCUMENTATION (Conceptual -> Logical -> Physical Blueprints)]
====================================================================================
                     │ (Future Downstream Dependencies)
                     ▼
[Phase 5: API Specifications & Data Transfer Objects (DTOs)]
                     │
                     ▼
[Phase 6: Implementation & Application Code (NestJS Services, Next.js UI)]
```

---

## 8. Governance Rules for Phase 4

The following governance rules are strictly enforced across all Phase 4 database activities:

1. **Documentation Only:** No application code, ORM entities, migration files, SQL scripts, or database instances may be generated during Phase 4.
2. **Frozen Baseline Protection:** The existing baseline of 104 atomic requirements, 59 business processes, and 60 business rules remains strictly frozen. No database document may alter or invalidate an approved baseline.
3. **No Unapproved Business Rules:** Database documentation must not invent missing business rules, arbitrary validation formulas, or unapproved workflows.
4. **Mandatory TBD Tagging:** Where the source documentation does not provide sufficient detail to define a data structure or relationship, the item must be explicitly classified as `[E] TBD / Open Decision` and cross-referenced with the official project TBD register (`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`).
5. **Separation of Concerns:** Business requirements must be kept strictly distinct from technical/database design decisions. Technical selections must be classified appropriately as `[C] Approved Technical Decision` or `[D] Proposed Detail`.
6. **Separation of Master vs. Staged Data:** The data architecture must strictly prevent pending or unapproved change requests from mutating active master employee records (`[A]` Baseline `REQ-MOD1-05`).
7. **First-Class Temporal Tracking:** Audit logging, historical versioning, and effective-date activation must be represented as first-class architectural capabilities in PostgreSQL (`[A]` Baseline `REQ-MOD1-07`, `REQ-MOD1-08`).
8. **Official Requirements as Sole Business Source of Truth:** Unconfirmed stakeholder decision items (`CONF-01` through `CONF-10`) and candidate delta items (`DLT-*`) do not constitute approved business requirements. The database documentation strictly adheres to the frozen 104-requirement baseline as the authoritative source of truth. Where stakeholder proposals diverge from the frozen baseline, the frozen requirement governs.
9. **Analytical Data-Domain Inventory Notice:** The identified conceptual entity count is an analytical data-domain inventory and does not represent the final number of physical PostgreSQL tables.

---
*End of Document — Master Index: Phase 4 Database Documentation.*
