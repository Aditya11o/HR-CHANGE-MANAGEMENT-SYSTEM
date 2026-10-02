# Database Schema Specification
## University HR Change Management & Automation System

**Document Identifier:** `DOC-08-DB-06`  
**Phase:** Phase 4 — Database Documentation (Step 5: Database Schema Specification)  
**Location:** `docs/08-database/06-DATABASE-SCHEMA-SPECIFICATION.md`  
**Status:** Approved Database Schema Specification Baseline  
**Date:** October 2, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Document Control and Status

### 1.1 Document Revision History

| Version | Release Date | Primary Author / Contributor | Description of Changes / Baseline State |
|---|---|---|---|
| `1.0.0` | October 2, 2026 | Database Architecture & Engineering Working Group | Initial official release of the Database Schema Specification translating the 33 approved conceptual entities, 41 conceptual relationships, and 344 logical attributes into a structured, source-grounded schema specification for the University HR Change Management & Automation System. Establishes logical domain groupings, entity schema profiles, key and identity strategies, referential integrity guidelines, data validation expectations, temporal lifecycle boundaries, and ERP integration patterns under PostgreSQL and Modular Monolith architecture. |

### 1.2 Document Lifecycle & Governance State

```
====================================================================================================
LIFECYCLE STATUS:
APPROVED DATABASE SCHEMA SPECIFICATION BASELINE — DOCUMENTATION ONLY

GOVERNANCE DIRECTIVE:
1. STRICT DOCUMENTATION ONLY: Contains zero physical DDL, SQL scripts, live database connections,
   primary keys, foreign keys, physical indexes, storage engine parameters, Prisma/TypeORM ORM code,
   or application code.
2. SOURCE-GROUNDED GROUND TRUTH: Grounded strictly in the frozen official requirements baseline
   (104 atomic requirements, 59 business processes, 60 business rules, 11 baseline TBDs).
3. MODULAR MONOLITH PRESERVATION: Adheres to a single unified PostgreSQL database with logical domain
   separation matching the backend Modular Monolith architecture. Physical PostgreSQL schema
   partitioning is treated as a proposed organizational structure, not an approved microservice boundary.
4. 5-TIER CLASSIFICATION ENFORCEMENT: Every schema statement, domain grouping, and identity strategy is
   explicitly tagged ([A] Explicit Requirement, [B] Logical Implication, [C] Approved Technical Decision,
   [D] Proposed Detail, [E] TBD / Open Decision).
5. UNRESOLVED DECISION ISOLATION: Open policy items, missing enclosure templates, and uncodified
   statutory retention rules are isolated under [E] and mapped to the official project TBD register.
====================================================================================================
```

---

## 2. Purpose and Scope

### 2.1 Purpose

The primary objective of this document is to translate the approved conceptual entities from [`03-ENTITY-IDENTIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/03-ENTITY-IDENTIFICATION.md), conceptual relationships from [`04-ENTITY-RELATIONSHIP-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/04-ENTITY-RELATIONSHIP-SPECIFICATION.md), and logical attributes from [`05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md) into a formal, structured **Database Schema Specification**.

This specification defines the logical database schema organization, domain ownership boundaries, entity schema profiles, identity and key strategies, referential integrity expectations, and cross-module integration mechanics necessary to guide subsequent physical schema design (`07-CONSTRAINTS-AND-RELATIONSHIPS.md`, `08-AUDIT-AND-VERSION-HISTORY-MODEL.md`, `09-EFFECTIVE-DATE-DATA-MODEL.md`, `10-INDEXING-STRATEGY.md`) without prematurely implementing physical database artifacts.

### 2.2 Functional Scope

This specification provides schema-level definitions for all **thirty-three (33) approved primary conceptual entities**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             APPROVED CONCEPTUAL ENTITY COVERAGE                                  │
├───────────────────────────────┬───────────────────────────────┬──────────────────────────────────┤
│ FUNCTIONAL DOMAIN             │ CONCEPTUAL ENTITY RANGE       │ TOTAL PRIMARY ENTITIES           │
├───────────────────────────────┼───────────────────────────────┼──────────────────────────────────┤
│ Module I: Change Management   │ ENT-MOD1-01 to ENT-MOD1-06    │ 6 Conceptual Entities            │
│ Module II: Recruitment        │ ENT-MOD2-01 to ENT-MOD2-10    │ 10 Conceptual Entities           │
│ Module III: Performance Mgmt  │ ENT-MOD3-01 to ENT-MOD3-09    │ 9 Conceptual Entities            │
│ Shared Enterprise Platform    │ ENT-SHR-01  to ENT-SHR-08     │ 8 Conceptual Entities            │
├───────────────────────────────┴───────────────────────────────┼──────────────────────────────────┤
│ TOTAL PRIMARY CONCEPTUAL ENTITIES FULLY ACCOUNTED FOR:        │ 33 Conceptual Entities           │
└───────────────────────────────────────────────────────────────┴──────────────────────────────────┘
```

Furthermore, this specification accounts for and preserves all **forty-one (41) approved conceptual relationships** (`REL-M1-001` to `007`, `REL-M2-001` to `009`, `REL-M3-001` to `006`, `REL-SHR-001` to `008`, `REL-XMOD-001` to `011`) established in Step 3.

### 2.3 Strict Implementation Exclusions

In strict accordance with Phase 4 governance, this document is documentation-only. The following implementation elements are strictly excluded:

- **No SQL, DDL, or DML Statements:** No `CREATE TABLE`, `ALTER TABLE`, `CREATE SCHEMA`, or SQL syntax.
- **No Physical Database Tables or Live Schemas:** No live database tables, tablespaces, or physical partitions created on a database instance.
- **No Physical Primary or Foreign Keys:** No SQL `PRIMARY KEY`, `FOREIGN KEY`, or surrogate sequence definitions.
- **No Physical Database Constraints or Indexes:** No B-Tree, GIN, unique constraint indexes, or SQL check constraints.
- **No Engine-Specific Physical Data Types:** No database-specific physical type definitions (e.g., `VARCHAR(255)`, `BIGINT`, `SERIAL`, `TIMESTAMPTZ`, `CITEXT`); attributes reference conceptual logical types.
- **No Object-Relational Mapping (ORM) Code:** No Prisma schemas, TypeORM entities, or ActiveRecord classes.
- **No Migrations or Seed Data:** No database migration files, seed scripts, stored procedures, or triggers.
- **No Application Code or API Endpoints:** No TypeScript classes, REST controllers, DTOs, or service implementations.
- **No Live Database Connections:** No connection strings, live pool configurations, or environment mutation.

---

## 3. Source Documents and Governance

### 3.1 Authoritative Baseline Hierarchy

This specification derives its authority strictly from the frozen project documentation:

1. **Requirements Baseline:**
   - [`docs/01-requirements/01-PROJECT-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/01-PROJECT-REQUIREMENTS-SPECIFICATION.md)
   - [`docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md) (104 Atomic Requirements)
   - [`docs/01-requirements/04-REQUIREMENTS-TRACEABILITY.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/04-REQUIREMENTS-TRACEABILITY.md)
   - [`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md) (11 Baseline TBDs: `REQ-TBD-01` to `REQ-TBD-11`)
2. **Business Process & Business Rule Baseline:**
   - [`docs/02-business-process/00-BUSINESS-PROCESS-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/00-BUSINESS-PROCESS-INDEX.md) (59 Business Processes: `BP-*`)
   - [`docs/02-business-process/01-BUSINESS-RULES-CATALOGUE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-RULES-CATALOGUE.md) (60 Business Rules: `BR-*`)
   - Module-Specific Process Specifications: `03-MODULE-1-*`, `04-MODULE-2-*`, `05-MODULE-3-*`, `06-CROSS-MODULE-*`.
3. **Functional Requirements Specifications (FRDs):**
   - [`docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md)
   - [`docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md)
   - [`docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md)
   - [`docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md)
4. **Architectural Baseline:**
   - [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)
   - [`docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md)
   - [`docs/08-database/00-DATABASE-DOCUMENTATION-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/00-DATABASE-DOCUMENTATION-INDEX.md)
   - [`docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md)
   - [`docs/08-database/02-DATA-MODEL-OVERVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/02-DATA-MODEL-OVERVIEW.md)
   - [`docs/08-database/03-ENTITY-IDENTIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/03-ENTITY-IDENTIFICATION.md)
   - [`docs/08-database/04-ENTITY-RELATIONSHIP-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/04-ENTITY-RELATIONSHIP-SPECIFICATION.md)
   - [`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md)

### 3.2 Stakeholder Delta Isolation

The frozen official requirements supplied by the mentor are the sole business source of truth. Stakeholder feedback artifacts (`CONF-01` through `CONF-10` and `DLT-*` items from `09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md` and `10-STAKEHOLDER-DECISION-SHEET.md`) are reference-only and have **not** been promoted into this schema specification.

---

## 4. Schema Specification Principles

The schema specification adheres to five fundamental database engineering principles:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 SCHEMA SPECIFICATION PRINCIPLES                                  │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. CONCEPTUAL-TO-LOGICAL CONTINUITY: Every schema entity maps directly to an approved conceptual  │
│    entity from Step 2, preserves its relationships from Step 3, and references its attributes     │
│    from Step 4. No entities are split, merged, or renamed.                                       │
│ 2. MODULAR MONOLITH ALIGNMENT: Database domains map directly to backend NestJS module boundaries  │
│    without assuming microservice database fragmentation. All domains share a single ACID engine. │
│ 3. LOGICAL OVER PHYSICAL DOMAINS: Domain groupings represent logical boundaries; physical        │
│    PostgreSQL schema partitioning is evaluated as an architectural option, not a mandated split. │
│ 4. STRICT BINARY SEPARATION: Object storage handles binary artifacts (resumes, scorecards, PDFs);│
│    the database schema manages strictly metadata, URI keys, MIME types, and cryptographic hashes.│
│ 5. RIGOROUS UNCERTAINTY GOVERNANCE: Where schema-level decisions (key formats, enclosure fields, │
│    ERP payloads) lack source grounding, they are tagged [E] and tied to the official TBD log.    │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 5. PostgreSQL Architecture Alignment

### 5.1 Authoritative System of Record

The approved technical baseline ([`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)) establishes **PostgreSQL (Current Stable Release)** as the authoritative **System of Record** (`[C] Approved Technical Decision`):

- **ACID Transaction Guarantees:** PostgreSQL provides full atomic transaction boundaries across all functional modules. Cross-module workflows (such as candidate onboarding into employee master, or appraisal outcome handshake into change request) execute within transactional contexts.
- **Relational Integrity:** Foreign key referential integrity protects relationships between master records, change requests, evaluation scorecards, and audit logs.
- **Semi-Structured Support:** PostgreSQL's native JSON support (`JSONB`) accommodates semi-structured payloads (dynamic change diffs, configurable KPI template schemas, SCM evaluation mark arrays, and audit state snapshots) while preserving relational integrity on core master fields (`[C]`).
- **Temporal and Scheduling Operations:** Native timestamp and date indexing support effective-date scheduling (`effective_date` activation) and SLA countdown timers.

### 5.2 Supporting In-Memory Store (Redis) Boundary

As established in [`01-DATABASE-DESIGN-OVERVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md) Section 2.2, **Redis** operates exclusively as an ephemeral supporting store (`[C] Approved Technical Decision`):
- **Role:** High-speed caching (Organization Chart hierarchy DAG tree, active role permissions), WebSocket pub/sub adapters (`ADR-001`), and BullMQ background worker queue persistence.
- **Persistence Boundary Rule:** **Redis is NOT a persistent system of record.** Every persistent business state, workflow transition, evaluation score, and audit record resides strictly within PostgreSQL.

### 5.3 Physical Schema Partitioning vs. Logical Separation

The backend application is architected as a **Modular Monolith** in NestJS (`[C] Approved Technical Decision`):
- **Single Unified Database Instance:** All modules connect to one unified PostgreSQL database instance, eliminating network overhead, distributed two-phase commit protocols, and cross-database transaction failures (`[C]`).
- **Logical Domain Separation:** Entities are logically grouped and owned by domain modules.
- **Physical Schema Options (`[D] Proposed Detail`):**
  - *Option 1 (Default Monolithic Schema):* All tables reside in the standard `public` schema with consistent domain-prefixed table names (e.g., `emp_*`, `rec_*`, `perf_*`, `shr_*`). This maximizes simplicity and query performance across modules.
  - *Option 2 (PostgreSQL Namespace Schemas):* Tables are segregated into dedicated PostgreSQL schemas (`mod_change`, `mod_recruitment`, `mod_performance`, `platform_shared`, `platform_integration`).
  - *Architectural Rationale:* The choice between single-schema prefixed tables and multi-schema namespaces is an implementation-level physical detail (`[D] Proposed Detail`). Both options preserve the required Modular Monolith architecture and single database instance.

---

## 6. Logical Domain Organization

The 33 conceptual entities are logically organized into **five (5) functional schema domains**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            LOGICAL SCHEMA DOMAIN ARCHITECTURE                                    │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ FUNCTIONAL DOMAIN             │ PRIMARY BUSINESS RESPONSIBILITY│ ASSOCIATED CONCEPTUAL ENTITIES  │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 1. Core Employee & Change     │ Authoritative Single Source of │ ENT-MOD1-01 (Employee Master)   │
│    Management Domain          │ Truth for personnel, org tree, │ ENT-MOD1-02 (Org Hierarchy Node)│
│    (Domain Owner: Module I)   │ dossiers, service changes, and │ ENT-MOD1-03 (Digital Dossier)   │
│                               │ historical service ledger.     │ ENT-MOD1-04 (Change Request)    │
│                               │                                │ ENT-MOD1-05 (Approval Action)   │
│                               │                                │ ENT-MOD1-06 (Service History)   │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 2. Recruitment & Selection    │ Manpower planning, MRFs, open  │ ENT-MOD2-01 (Academic Plan)     │
│    Domain                     │ positions tracking, candidate  │ ENT-MOD2-02 (Non-Academic Plan) │
│    (Domain Owner: Module II)  │ sourcing, CV database, RCS,    │ ENT-MOD2-03 (MRF Requisition)   │
│                               │ SCM committees, interviews,    │ ENT-MOD2-04 (Position Tracker)  │
│                               │ LOI offers, and replacements.  │ ENT-MOD2-05 (Candidate Profile) │
│                               │                                │ ENT-MOD2-06 (Recruiter Calling) │
│                               │                                │ ENT-MOD2-07 (SCM Session Record)│
│                               │                                │ ENT-MOD2-08 (Non-Acad Interview)│
│                               │                                │ ENT-MOD2-09 (Letter of Intent)  │
│                               │                                │ ENT-MOD2-10 (Replacement Track) │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 3. Performance Management     │ Three independent appraisal    │ ENT-MOD3-01 (Group-D Template)  │
│    Domain                     │ subsystems: Group-D monthly,   │ ENT-MOD3-02 (Group-D Monthly)   │
│    (Domain Owner: Module III) │ Staff KRA/KPI quarterly, and   │ ENT-MOD3-03 (Group-D Annual)    │
│                               │ Faculty annual ECM route.      │ ENT-MOD3-04 (KRA Goal Setting)  │
│                               │                                │ ENT-MOD3-05 (Staff Quarterly)   │
│                               │                                │ ENT-MOD3-06 (Staff Annual)      │
│                               │                                │ ENT-MOD3-07 (Faculty Batch)     │
│                               │                                │ ENT-MOD3-08 (Faculty Dossier)   │
│                               │                                │ ENT-MOD3-09 (Faculty ECM Record)│
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 4. Shared Platform Services   │ Cross-cutting IAM, roles/RBAC, │ ENT-SHR-01 (User Account)       │
│    Domain                     │ workflow FSM tracking, SLA     │ ENT-SHR-02 (Role Assignment)    │
│    (Domain Owner: Platform)   │ countdown timers, document     │ ENT-SHR-03 (Workflow Instance)  │
│                               │ metadata, notifications, and   │ ENT-SHR-04 (SLA Timer Record)   │
│                               │ immutable audit logging.       │ ENT-SHR-05 (Document Metadata)  │
│                               │                                │ ENT-SHR-06 (Notification Queue) │
│                               │                                │ ENT-SHR-07 (Audit Trail Entry)  │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 5. Integration & ERP Domain   │ Transactional outbox staging   │ ENT-SHR-08 (ERP Outbox Staging) │
│    (Domain Owner: Integration)│ guaranteeing reliable master   │                                 │
│                               │ data reflection in campus ERP. │                                 │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

---

## 7. Entity Schema Specification — Module I

### 7.1 ENT-MOD1-01: Employee Master Record
- **Domain Owner:** Module I (`EmployeeCoreModule`)
- **Business Purpose:** Central institutional repository of active personnel records (`REQ-MOD1-01`). Reflects currently active service conditions only; pending changes never mutate this entity directly.
- **Proposed Schema Grouping / Illustrative Table:** `core_change.employee_master` / `emp_master_record` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-EMP-01` to `ATTR-EMP-14` (from Step 4).
- **Associated Conceptual Relationships:** `REL-M1-001`, `REL-M1-002`, `REL-M1-003`, `REL-M1-004`, `REL-M1-006`, `REL-M1-007`, `REL-XMOD-001`, `REL-XMOD-002`, `REL-XMOD-003`, `REL-XMOD-005`, `REL-XMOD-006`, `REL-XMOD-007`, `REL-XMOD-008`, `REL-XMOD-009`, `REL-XMOD-010`, `REL-SHR-001`, `REL-SHR-008`.
- **Data Lifecycle & Temporal Boundaries:** Instantiated upon Day-1 candidate joining (`BP-XMOD-001`). Mutated only when an approved change request reaches its scheduled effective date (`BP-M1-007`). Deactivated (resigned/retired) via lifecycle state without destructive data deletion (`REQ-MOD1-08`).
- **Source Traceability:** `REQ-MOD1-01`, `REQ-MOD1-04`, `REQ-MOD1-07`, `REQ-MOD1-08`; `BP-M1-001`, `BP-M1-007`; `BR-01`, `BR-06`, `BR-10`; `MOD1-CDB-REQ-01` to `05`.
- **Governing Unresolved Decisions:** Employee ID generation authority and ERP physical key synchronization (`REQ-TBD-01`). Statutory retention duration under `REQ-TBD-11`.

### 7.2 ENT-MOD1-02: Organization Hierarchy Node
- **Domain Owner:** Module I (`OrgHierarchyModule`)
- **Business Purpose:** Models university organizational positions, schools, departments, and supervisory reporting lines (`REQ-MOD1-02`). Powers dynamic organization chart rendering and approval routing.
- **Proposed Schema Grouping / Illustrative Table:** `core_change.org_hierarchy_nodes` / `emp_org_nodes` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-ORG-01` to `ATTR-ORG-08`.
- **Associated Conceptual Relationships:** `REL-M1-001` (Supervisory self-referential tree), `REL-M1-002` (Employee active assignment).
- **Data Lifecycle & Temporal Boundaries:** Nodes persist across organizational lifecycles. Realignment occurs automatically upon approved change activation affecting supervisory reporting, designation, or department transfer (`BP-M1-010`).
- **Source Traceability:** `REQ-MOD1-02`, `REQ-MOD1-06`; `BP-M1-002`, `BP-M1-010`; `BR-02`, `BR-06`; `MOD1-ORG-REQ-01` to `04`.
- **Governing Unresolved Decisions:** Dual reporting line topology support (`MOD1-TBD-03` / open decision).

### 7.3 ENT-MOD1-03: Digital Personal File & Dossier Item
- **Domain Owner:** Module I (`EmployeeFileModule`)
- **Business Purpose:** Centralized digital dossier indexing and archiving verified credentials, appointment letters, promotion orders, and evaluation reports (`REQ-MOD1-03`).
- **Proposed Schema Grouping / Illustrative Table:** `core_change.employee_dossier_items` / `emp_dossier_items` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-DOS-01` to `ATTR-DOS-08`.
- **Associated Conceptual Relationships:** `REL-M1-003` (Employee dossier link), `REL-XMOD-003` (Document binary metadata pointer in `ENT-SHR-05`).
- **Data Lifecycle & Temporal Boundaries:** Append-only ingestion across employee tenure. Items are permanently read-only once verified.
- **Source Traceability:** `REQ-MOD1-03`; `BP-M1-003`, `BP-XMOD-001`, `BP-XMOD-004`; `BR-03`; `MOD1-FIL-REQ-01` to `04`.
- **Governing Unresolved Decisions:** Document archival retention and disposal rules under `REQ-TBD-11`.

### 7.4 ENT-MOD1-04: Service Condition Change Request
- **Domain Owner:** Module I (`ChangeManagementModule`)
- **Business Purpose:** Isolated staging container encapsulating proposed service modifications across 10 standardized categories (`REQ-MOD1-05`). Completely isolates proposed data from master records.
- **Proposed Schema Grouping / Illustrative Table:** `core_change.service_change_requests` / `emp_change_requests` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-CHG-01` to `ATTR-CHG-12`.
- **Associated Conceptual Relationships:** `REL-M1-004` (Target employee reference), `REL-M1-005` (Approval action history), `REL-M1-006` (Service history activation slice), `REL-XMOD-004` (Module III appraisal outcome trigger).
- **Data Lifecycle & Temporal Boundaries:** Transitions through strict FSM (`INITIATED` $\rightarrow$ `PENDING_HR` $\rightarrow$ `PENDING_SENIOR_MGMT` $\rightarrow$ `APPROVED_PENDING_ACTIVATION` $\rightarrow$ `COMMITTED_ACTIVE` / `REJECTED`). Future-dated requests stage in pending activation until the scheduled date arrives.
- **Source Traceability:** `REQ-MOD1-05`, `REQ-MOD1-06`, `REQ-MOD1-07`; `BP-M1-004` to `BP-M1-007`; `BR-04`, `BR-05`, `BR-07`, `BR-14`; `MOD1-CHG-REQ-01` to `19`.
- **Governing Unresolved Decisions:** Format field-level schemas under `REQ-TBD-02`. Administrative allowances for secondary roles under `REQ-TBD-09`.

### 7.5 ENT-MOD1-05: Service Change Approval Action
- **Domain Owner:** Module I (`ChangeApprovalModule`)
- **Business Purpose:** Captures individual review, endorsement, clarification, or rejection sign-offs across the two-level approval hierarchy (`REQ-MOD1-06`).
- **Proposed Schema Grouping / Illustrative Table:** `core_change.change_approval_actions` / `emp_change_approvals` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-APP-01` to `ATTR-APP-07`.
- **Associated Conceptual Relationships:** `REL-M1-005` (Change request approval log).
- **Data Lifecycle & Temporal Boundaries:** Strictly append-only. Once recorded, an approval sign-off or rejection cannot be modified, overwritten, or deleted (`MOD1-APP-REQ-01`).
- **Source Traceability:** `REQ-MOD1-06`; `BP-M1-005`, `BP-M1-006`; `BR-04`, `BR-07`, `BR-18`; `MOD1-APP-REQ-01` to `06`.
- **Governing Unresolved Decisions:** None. Approval hierarchy explicitly governed by baseline.

### 7.6 ENT-MOD1-06: Employee Service History Ledger
- **Domain Owner:** Module I (`EmployeeCoreModule`)
- **Business Purpose:** Maintains an immutable chronological ledger of bounded temporal intervals (`valid_from` to `valid_to`) capturing designations, salaries, bands, and reporting lines active during each period (`REQ-MOD1-08`).
- **Proposed Schema Grouping / Illustrative Table:** `core_change.employee_service_history` / `emp_service_history_slices` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-HST-01` to `ATTR-HST-12`.
- **Associated Conceptual Relationships:** `REL-M1-006` (Activating change request link), `REL-M1-007` (Target employee timeline).
- **Data Lifecycle & Temporal Boundaries:** Append-only ledger updated automatically upon effective-date activation of an approved change request. Slices are immutable once created.
- **Source Traceability:** `REQ-MOD1-08`; `BP-M1-007`, `BP-M1-008`; `BR-08`, `BR-10`; `MOD1-VER-REQ-01`, `MOD1-VER-REQ-02`.
- **Governing Unresolved Decisions:** Historical ledger retention duration under `REQ-TBD-11`.

---

## 8. Entity Schema Specification — Module II

### 8.1 ENT-MOD2-01: Academic Manpower Plan & Workload Requisition
- **Domain Owner:** Module II (`AcademicRecruitmentModule`)
- **Business Purpose:** Encapsulates the 4-month semester faculty requisition proposal based on curriculum teaching load assessments (`REQ-MOD2-02`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.academic_manpower_plans` / `rec_acad_plans` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-AMP-01` to `ATTR-AMP-11`.
- **Associated Conceptual Relationships:** `REL-M2-001` (Plan authorization of MRFs).
- **Data Lifecycle & Temporal Boundaries:** Cycle begins at T-4 months; Dean submits within 15 days; Associate Dean vets by T-3 months; Pro-Chancellor turnaround in 7 days; closes upon MRF authorization.
- **Source Traceability:** `REQ-MOD2-02`, `REQ-MOD2-04`, `REQ-MOD2-05`; `BP-M2-ACAD-001` to `006`; `BR-21`, `BR-22`, `BR-23`; `MOD2-MP-FAC-REQ-01` to `08`.
- **Governing Unresolved Decisions:** Teaching load attachment schema under `REQ-TBD-02`.

### 8.2 ENT-MOD2-02: Non-Academic Manpower Plan
- **Domain Owner:** Module II (`NonAcademicRecruitmentModule`)
- **Business Purpose:** Governs annual staffing requisitions for administrative and operational units (`REQ-MOD2-07`), enforcing the rule of maximum 1 planned requisition per department per year (`BR-24`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.non_academic_manpower_plans` / `rec_non_acad_plans` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-NMP-01` to `ATTR-NMP-12`.
- **Associated Conceptual Relationships:** `REL-M2-002` (Non-academic plan authorization of MRFs).
- **Data Lifecycle & Temporal Boundaries:** Cycle begins at T-4 months; HOD submits within 15 days; Head HR vets by T-3 months; Pro-Chancellor approves; closes upon MRF generation.
- **Source Traceability:** `REQ-MOD2-07`, `REQ-MOD2-08`, `REQ-MOD2-09`, `REQ-MOD2-10`; `BP-M2-NACAD-001` to `005`; `BR-24`, `BR-25`, `BR-26`; `MOD2-MP-NF-REQ-01` to `08`.
- **Governing Unresolved Decisions:** Track allocation for technical staff under `REQ-TBD-03`.

### 8.3 ENT-MOD2-03: Manpower Requisition Form (MRF)
- **Domain Owner:** Module II (`RecruitmentCoreModule`)
- **Business Purpose:** Authoritative requisition authorizing job advertisement, candidate sourcing, and selection operations (`REQ-MOD2-03`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.manpower_requisitions` / `rec_mrf_requisitions` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-MRF-01` to `ATTR-MRF-13`.
- **Associated Conceptual Relationships:** `REL-M2-001`, `REL-M2-002`, `REL-M2-003` (Instantiates Open Positions Tracker), `REL-M2-004` (Governs candidate applications), `REL-M2-010` (Urgent replacement linkage).
- **Data Lifecycle & Temporal Boundaries:** Transitions from `DRAFT` to `AUTHORIZED`; triggers public ads within 7 days; remains active until all authorized vacancies are filled or cancelled.
- **Source Traceability:** `REQ-MOD2-03`, `REQ-MOD2-06`, `REQ-MOD2-10`; `BP-M2-ACAD-006`, `BP-M2-NACAD-005`; `BR-23`, `BR-27`; `MOD2-MRF-REQ-01` to `07`.
- **Governing Unresolved Decisions:** Enclosure 1 standardized form schema under `REQ-TBD-02`.

### 8.4 ENT-MOD2-04: Open Positions Tracker Entry
- **Domain Owner:** Module II (`RecruitmentTrackingModule`)
- **Business Purpose:** University **Attachment 3** position tracker maintaining real-time visibility into hiring progress across all academic and administrative units (`REQ-MOD2-11`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.open_positions_tracker` / `rec_position_tracker` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-OPT-01` to `ATTR-OPT-10`.
- **Associated Conceptual Relationships:** `REL-M2-003` (Parent MRF link).
- **Data Lifecycle & Temporal Boundaries:** Instantiated within 30 days of MRF approval; updated continuously during sourcing/interviews; closes upon candidate Day-1 onboarding.
- **Source Traceability:** `REQ-MOD2-11`; `BP-M2-ACAD-006`, `BP-M2-TRK-001`; `BR-27`, `BR-28`; `MOD2-POS-REQ-01` to `05`.
- **Governing Unresolved Decisions:** Attachment 3 field layout under `REQ-TBD-02`.

### 8.5 ENT-MOD2-05: Candidate Profile & Application Record
- **Domain Owner:** Module II (`CandidateSourcingModule`)
- **Business Purpose:** Centralized applicant repository capturing multi-channel candidate applications, deduplication, parsed qualifications, and screening outcomes (`REQ-MOD2-12`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.candidate_applications` / `rec_candidate_profiles` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-CAN-01` to `ATTR-CAN-13`.
- **Associated Conceptual Relationships:** `REL-M2-004` (MRF link), `REL-M2-005` (RCS screening sheet), `REL-M2-006` (Academic SCM session), `REL-M2-007` (Non-academic interview rounds), `REL-M2-008` (Letter of Intent offer), `REL-XMOD-011` (External resume document metadata).
- **Data Lifecycle & Temporal Boundaries:** Ingested from multi-channel portals; undergoes criteria/UGC screening; advances through RCS/interviews; retained or archived.
- **Source Traceability:** `REQ-MOD2-12`, `REQ-MOD2-13`, `REQ-MOD2-19`; `BP-M2-TRK-001`, `BP-M2-ACAD-007`; `BR-29`, `BR-30`, `BR-31`; `MOD2-SRC-REQ-01` to `06`, `MOD2-SCR-REQ-01` to `05`.
- **Governing Unresolved Decisions:** Candidate CV statutory retention duration under `REQ-TBD-11`.

### 8.6 ENT-MOD2-06: Recruiter Calling Record (RCS)
- **Domain Owner:** Module II (`CandidateScreeningModule`)
- **Business Purpose:** Captures telephonic screening feedback, compensation expectations, notice periods, and recruiter recommendations (`REQ-MOD2-12`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.recruiter_calling_sheets` / `rec_calling_records` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-RCS-01` to `ATTR-RCS-12`.
- **Associated Conceptual Relationships:** `REL-M2-005` (Candidate application link).
- **Data Lifecycle & Temporal Boundaries:** Captured post-shortlisting; reviewed by Head HR; gates pre-interview Senior Management clearance.
- **Source Traceability:** `REQ-MOD2-12`; `BP-M2-ACAD-007`, `BP-M2-ACAD-008`; `BR-31`, `BR-32`; `MOD2-RCS-REQ-01` to `06`.
- **Governing Unresolved Decisions:** RCS form template schema under `REQ-TBD-02`.

### 8.7 ENT-MOD2-07: Academic Selection Committee (SCM) Session & Score Record
- **Domain Owner:** Module II (`AcademicSelectionModule`)
- **Business Purpose:** Manages statutory Selection Committee Meetings (SCM) for faculty recruitment, captures evaluator marks, and auto-compiles the composite Evaluation Matrix (`REQ-MOD2-14`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.academic_scm_sessions` / `rec_scm_sessions` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-SCM-01` to `ATTR-SCM-11`.
- **Associated Conceptual Relationships:** `REL-M2-006` (Candidate evaluation link), `REL-SHR-001` (External expert access token).
- **Data Lifecycle & Temporal Boundaries:** Scheduled upon shortlist approval; marks entered during session; scorecards locked upon submission; routes to Management for cost approval.
- **Source Traceability:** `REQ-MOD2-14`; `BP-M2-ACAD-009`, `BP-M2-ACAD-010`; `BR-33`, `BR-34`, `BR-35`; `MOD2-SCM-REQ-01` to `06`, `MOD2-EXP-REQ-01` to `02`.
- **Governing Unresolved Decisions:** Scoring weightages under `REQ-TBD-04`. Enclosure 2/3 schemas under `REQ-TBD-02`. External expert authentication under `REQ-TBD-07`.

### 8.8 ENT-MOD2-08: Non-Academic Interview Round & Score Record
- **Domain Owner:** Module II (`NonAcademicSelectionModule`)
- **Business Purpose:** Enforces 3-round sequential evaluations (Technical $\rightarrow$ HR $\rightarrow$ Management) and captures scores for Job Knowledge, Communication, and Attitude (`REQ-MOD2-15`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.non_academic_interview_rounds` / `rec_interview_rounds` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-NIR-01` to `ATTR-NIR-11`.
- **Associated Conceptual Relationships:** `REL-M2-007` (Candidate interview round link).
- **Data Lifecycle & Temporal Boundaries:** Executed sequentially; round clearance required to unlock subsequent round; finalized upon Round 3 completion.
- **Source Traceability:** `REQ-MOD2-15`; `BP-M2-NACAD-006`, `BP-M2-NACAD-007`; `BR-36`, `BR-37`; `MOD2-SEL-NF-REQ-01` to `03`.
- **Governing Unresolved Decisions:** Score normalization standards under `REQ-TBD-02`.

### 8.9 ENT-MOD2-09: Letter of Intent (LOI) & Pre-Onboarding ("Yet to Join") Record
- **Domain Owner:** Module II (`OfferOnboardingModule`)
- **Business Purpose:** Governs formal offer generation, candidate acceptance, pre-onboarding notifications, and Day-1 master record instantiation (`REQ-MOD2-16` to `18`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.letter_of_intent_records` / `rec_loi_offers` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-LOI-01` to `ATTR-LOI-12`.
- **Associated Conceptual Relationships:** `REL-M2-008` (Candidate application link), `REL-XMOD-001` (Day-1 employee master creation in `ENT-MOD1-01`).
- **Data Lifecycle & Temporal Boundaries:** Generated on Management cost approval; candidate accepts $\rightarrow$ tagged "Yet to Join"; triggers pre-onboarding notifications; closes on Day 1 upon employee creation.
- **Source Traceability:** `REQ-MOD2-16`, `REQ-MOD2-17`, `REQ-MOD2-18`; `BP-M2-ACAD-011`, `BP-M2-ACAD-012`, `BP-XMOD-001`; `BR-38`, `BR-39`, `BR-40`; `MOD2-YTJ-REQ-01` to `07`.
- **Governing Unresolved Decisions:** Legal handoff boundary between LOI and formal Appointment Letter under `REQ-TBD-08`.

### 8.10 ENT-MOD2-10: Urgent Replacement Tracker
- **Domain Owner:** Module II (`UrgentRecruitmentModule`)
- **Business Purpose:** Monitors urgent faculty or staff replacement workflows triggered by accepted employee resignations, tracking hiring progress against notice periods (`REQ-MOD2-03`).
- **Proposed Schema Grouping / Illustrative Table:** `recruitment.urgent_replacement_trackers` / `rec_replacement_trackers` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-URG-01` to `ATTR-URG-10`.
- **Associated Conceptual Relationships:** `REL-M2-009` (Ad-hoc MRF link), `REL-M2-010` (Resigning employee master reference in `ENT-MOD1-01`).
- **Data Lifecycle & Temporal Boundaries:** Triggered by resignation acceptance; starts replacement clock; monitors ad-hoc MRF vetting; closes upon replacement onboarding.
- **Source Traceability:** `REQ-MOD2-03`; `BP-M2-URG-001`, `BP-XMOD-002`; `BR-24`, `BR-41`; `MOD2-RES-REQ-01` to `06`.
- **Governing Unresolved Decisions:** Upstream resignation intake interface under `REQ-TBD-06`.

---

## 9. Entity Schema Specification — Module III

### 9.1 Subsystem 1: Group-D / Band I Monthly & Annual Appraisal

#### 9.1.1 ENT-MOD3-01: Group-D Evaluation Form Template
- **Domain Owner:** Module III (`GroupDPerformanceModule`)
- **Business Purpose:** Master repository of role-specific KPI templates for Group-D service roles (Enclosure 1 standardized templates) (`REQ-MOD3-01`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.group_d_templates` / `perf_gd_templates` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-GDT-01` to `ATTR-GDT-07`.
- **Associated Conceptual Relationships:** `REL-M3-001` (Template instantiation of monthly evaluations).
- **Data Lifecycle & Temporal Boundaries:** Configured by HR; versioned with audit logging; active templates generate monthly instances.
- **Source Traceability:** `REQ-MOD3-01`, `REQ-MOD3-03`; `BP-M3-GD-001`; `BR-42`, `BR-43`; `MOD3-GD-REQ-01` to `03`.
- **Governing Unresolved Decisions:** Enclosure 1 field schema under `REQ-TBD-02`.

#### 9.1.2 ENT-MOD3-02: Group-D Monthly Evaluation Instance
- **Domain Owner:** Module III (`GroupDPerformanceModule`)
- **Business Purpose:** Monthly evaluation form completed by HODs for each Group-D employee (`REQ-MOD3-01`), subject to strict 7th due date, 10th grace cutoff auto-lock, and VP-Administration sign-off.
- **Proposed Schema Grouping / Illustrative Table:** `performance.group_d_monthly_evaluations` / `perf_gd_monthly_evals` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-GDM-01` to `ATTR-GDM-12`.
- **Associated Conceptual Relationships:** `REL-M3-001` (Template link), `REL-M3-002` (Collation into Annual Report), `REL-XMOD-005` (Target employee master link).
- **Data Lifecycle & Temporal Boundaries:** Dispatched 1st of month; due 7th; grace period to 10th; auto-locked at 23:59 on 10th if unsubmitted; VP-Admin approves.
- **Source Traceability:** `REQ-MOD3-01`, `REQ-MOD3-02`, `REQ-MOD3-04`, `REQ-MOD3-05`; `BP-M3-GD-002` to `005`; `BR-44` to `BR-47`; `MOD3-GD-REQ-04` to `13`.
- **Governing Unresolved Decisions:** Enclosure 2 monthly report layout under `REQ-TBD-02`.

#### 9.1.3 ENT-MOD3-03: Group-D Annual Collation Report
- **Domain Owner:** Module III (`GroupDPerformanceModule`)
- **Business Purpose:** 12-month performance aggregation, weighted scoring, mandatory probation gate verification, and Management compensation slab review (`REQ-MOD3-06` to `08`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.group_d_annual_reports` / `perf_gd_annual_reports` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-GDA-01` to `ATTR-GDA-11`.
- **Associated Conceptual Relationships:** `REL-M3-002` (Monthly evaluations set), `REL-XMOD-006` (Target employee link), `REL-XMOD-004` (Module I change handshake).
- **Data Lifecycle & Temporal Boundaries:** Auto-triggered on 1-year DOJ anniversary; aggregates 12 reports; verifies probation; records Management slab decision; triggers Module I salary change.
- **Source Traceability:** `REQ-MOD3-06`, `REQ-MOD3-07`, `REQ-MOD3-08`; `BP-M3-GD-006` to `008`; `BR-48`, `BR-49`, `BR-50`; `MOD3-GD-REQ-14` to `21`.
- **Governing Unresolved Decisions:** Pre-defined compensation slabs under `REQ-TBD-05`.

---

### 9.2 Subsystem 2: General Staff KRA/KPI Lifecycle

#### 9.2.1 ENT-MOD3-04: General Staff KRA/KPI Goal Setting Record
- **Domain Owner:** Module III (`StaffPerformanceModule`)
- **Business Purpose:** Captures and locks performance goals for new staff joiners within strict 30 days of Date of Joining (DOJ) (`REQ-MOD3-09`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.staff_kra_goals` / `perf_staff_goals` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-KRG-01` to `ATTR-KRG-10`.
- **Associated Conceptual Relationships:** `REL-M3-003` (Anchors quarterly reviews Q1–Q4), `REL-XMOD-007` (Target employee master link).
- **Data Lifecycle & Temporal Boundaries:** Initialized on Day 1; 30-day completion SLA; verified by HR; locked by Management; immutable during quarterly reviews.
- **Source Traceability:** `REQ-MOD3-09`; `BP-M3-KRA-001`; `BR-51`, `BR-52`; `MOD3-KRA-REQ-01` to `04`.
- **Governing Unresolved Decisions:** Staff appraisal track boundary definitions under `REQ-TBD-03`. Goal sheet template schema under `REQ-TBD-02`.

#### 9.2.2 ENT-MOD3-05: General Staff Quarterly Review Record (Q1–Q4)
- **Domain Owner:** Module III (`StaffPerformanceModule`)
- **Business Purpose:** Quarterly review against locked KRAs/KPIs across Q1, Q2, Q3, and Q4 with 90-day triggers and 15-day submission windows (`REQ-MOD3-10` to `12`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.staff_quarterly_reviews` / `perf_staff_quarterly_evals` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-KRQ-01` to `ATTR-KRQ-12`.
- **Associated Conceptual Relationships:** `REL-M3-003` (Goal record link), `REL-M3-004` (Collation into Annual Outcome), `REL-XMOD-008` (Target employee link).
- **Data Lifecycle & Temporal Boundaries:** Initiated at 90 days from DOJ; 15-day employee self-review; 7-day supervisor verification; HR review; Management comments; advances sequentially Q1 $\rightarrow$ Q4.
- **Source Traceability:** `REQ-MOD3-10`, `REQ-MOD3-11`, `REQ-MOD3-12`; `BP-M3-KRA-002` to `004`; `BR-53`, `BR-54`; `MOD3-KRA-REQ-05` to `14`.
- **Governing Unresolved Decisions:** Scoring formulas and templates under `REQ-TBD-02`.

#### 9.2.3 ENT-MOD3-06: General Staff Annual Appraisal Outcome
- **Domain Owner:** Module III (`StaffPerformanceModule`)
- **Business Purpose:** Consolidated annual appraisal review and automatic Module I handshake for increments, promotions, or band realignments (`REQ-MOD3-13`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.staff_annual_outcomes` / `perf_staff_annual_outcomes` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-KRA-01` to `ATTR-KRA-10`.
- **Associated Conceptual Relationships:** `REL-M3-004` (Quarterly reviews set), `REL-XMOD-009` (Target employee link), `REL-XMOD-004` (Handshake to `ENT-MOD1-04`).
- **Data Lifecycle & Temporal Boundaries:** Triggered post-Q4; Management records decision; automatically initializes Change Request in Module I without duplicate data entry.
- **Source Traceability:** `REQ-MOD3-13`, `REQ-INT-04`; `BP-M3-KRA-005`, `BP-XMOD-004`; `BR-54`; `MOD3-KRA-REQ-15` to `18`.
- **Governing Unresolved Decisions:** Pre-defined compensation revision scales under `REQ-TBD-05`.

---

### 9.3 Subsystem 3: Faculty Annual Performance Appraisal (ECM Route)

#### 9.3.1 ENT-MOD3-07: Faculty Annual Appraisal Eligibility Batch
- **Domain Owner:** Module III (`FacultyAppraisalModule`)
- **Business Purpose:** Monthly batch scanner identifying faculty completing probation and $\ge 12$ months service, routing eligible list to Registrar by the 10th of every month (`REQ-MOD3-14` to `15`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.faculty_eligibility_batches` / `perf_fac_eligibility_batches` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-FEB-01` to `ATTR-FEB-08`.
- **Associated Conceptual Relationships:** `REL-M3-005` (Spawns self-appraisal dossiers).
- **Data Lifecycle & Temporal Boundaries:** Runs on 10th of every month; identifies eligible faculty; transmits to Registrar; triggers self-appraisal form auto-dispatch.
- **Source Traceability:** `REQ-MOD3-14`, `REQ-MOD3-15`; `BP-M3-FAC-001`, `BP-M3-FAC-002`; `BR-55`, `BR-56`; `MOD3-FAC-REQ-01` to `05`.
- **Governing Unresolved Decisions:** Staff track boundary definitions under `REQ-TBD-03`.

#### 9.3.2 ENT-MOD3-08: Faculty Self-Appraisal Dossier & Multi-Unit Verification Record
- **Domain Owner:** Module III (`FacultyAppraisalModule`)
- **Business Purpose:** Captures faculty self-appraisal submissions and parallel verification across exactly 4 units: School Dean, R&D Cell, Placement Cell, and HR Department (`REQ-MOD3-16` to `17`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.faculty_self_appraisals` / `perf_fac_dossiers` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-FSD-01` to `ATTR-FSD-13`.
- **Associated Conceptual Relationships:** `REL-M3-005` (Parent batch link), `REL-M3-006` (Scheduling into ECM session), `REL-XMOD-010` (Target faculty employee link).
- **Data Lifecycle & Temporal Boundaries:** Auto-issued upon batch approval; 7 working days submission SLA; routes to 4 units; handles discrepancy correction loop; cleared dossiers scheduled for ECM.
- **Source Traceability:** `REQ-MOD3-16`, `REQ-MOD3-17`; `BP-M3-FAC-003` to `005`; `BR-57`, `BR-58`; `MOD3-FAC-REQ-06` to `13`.
- **Governing Unresolved Decisions:** Enclosure 1 self-appraisal form schema under `REQ-TBD-02`.

#### 9.3.3 ENT-MOD3-09: Faculty ECM Session & TNU Protocol Matrix Record
- **Domain Owner:** Module III (`FacultyAppraisalModule`)
- **Business Purpose:** Manages monthly Evaluation Committee Meetings, captures digital score sheets, compiles TNU Protocol Matrix, and records Management compensation decisions (`REQ-MOD3-18` to `20`).
- **Proposed Schema Grouping / Illustrative Table:** `performance.faculty_ecm_sessions` / `perf_fac_ecm_records` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-ECM-01` to `ATTR-ECM-13`.
- **Associated Conceptual Relationships:** `REL-M3-006` (Verified dossier link), `REL-XMOD-004` (Module I change handshake).
- **Data Lifecycle & Temporal Boundaries:** Scheduled monthly by Registrar; digital scores entered during meeting; matrix compiled; Management decides; auto-generates outcome letters; triggers Module I change.
- **Source Traceability:** `REQ-MOD3-18`, `REQ-MOD3-19`, `REQ-MOD3-20`, `REQ-INT-04`; `BP-M3-FAC-006` to `008`, `BP-XMOD-004`; `BR-59`, `BR-60`; `MOD3-FAC-REQ-14` to `22`.
- **Governing Unresolved Decisions:** TNU Protocol mathematical weightages and quorums under `REQ-TBD-04`. Compensation revision slabs under `REQ-TBD-05`. Enclosures 2 and 3 under `REQ-TBD-02`.

---

## 10. Shared Platform Schema Specification

### 10.1 ENT-SHR-01: User Account & Authentication Credential Profile
- **Domain Owner:** Shared Platform (`AuthIdentityModule`)
- **Business Purpose:** Manages user identity credentials, sessions, and secure time-limited tokens for external statutory SCM experts (`REQ-SEC-01`, `REQ-SEC-02`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_shared.user_accounts` / `shr_user_accounts` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-USR-01` to `ATTR-USR-08`.
- **Associated Conceptual Relationships:** `REL-SHR-001` (External expert access), `REL-SHR-002` (Role assignments).
- **Data Lifecycle & Temporal Boundaries:** Initialized upon staff onboarding or external expert invitation; suspended/deactivated upon resignation or role expiry.
- **Source Traceability:** `REQ-SEC-01`, `REQ-SEC-02`, `REQ-MOD2-14`; `SHR-AUT-REQ-01` to `04`.
- **Governing Unresolved Decisions:** Institutional SSO identity provider protocol under `REQ-TBD-07`.

### 10.2 ENT-SHR-02: Role & Permission Assignment
- **Domain Owner:** Shared Platform (`SecurityModule`)
- **Business Purpose:** Enforces Role-Based Access Control (RBAC) and contextual row-level scoping rules (HOD=Dept, Dean=School, Senior Mgmt=University) (`REQ-SEC-03`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_shared.role_permission_assignments` / `shr_role_assignments` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-ROL-01` to `ATTR-ROL-07`.
- **Associated Conceptual Relationships:** `REL-SHR-002` (User account link).
- **Data Lifecycle & Temporal Boundaries:** Assigned upon user creation or institutional reassignment; evaluated on every business command.
- **Source Traceability:** `REQ-SEC-03`; `SHR-RBC-REQ-01` to `02`.
- **Governing Unresolved Decisions:** None. Role taxonomy fully established in baseline.

### 10.3 ENT-SHR-03: Workflow State Instance & Transition Log
- **Domain Owner:** Shared Platform (`WorkflowEngineModule`)
- **Business Purpose:** Universal Finite State Machine (FSM) instance tracking current state, prior state, acting user, transition guards, and mandatory comments across all modules (`REQ-SHR-01`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_shared.workflow_state_instances` / `shr_workflow_instances` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-WFL-01` to `ATTR-WFL-10`.
- **Associated Conceptual Relationships:** `REL-SHR-003` (Generic polymorphic association to domain entities).
- **Data Lifecycle & Temporal Boundaries:** Active during multi-step review cycles; transition logs are strictly append-only.
- **Source Traceability:** `REQ-MOD1-06`, `REQ-MOD2-14`, `REQ-MOD3-04`, `REQ-SHR-01`; `SHR-WFL-REQ-01` to `03`.
- **Governing Unresolved Decisions:** None. FSM execution model approved.

### 10.4 ENT-SHR-04: SLA & Deadline Timer Record
- **Domain Owner:** Shared Platform (`SlaTimelineModule`)
- **Business Purpose:** Manages operational deadlines, countdown timers, grace periods, and automated lockout timestamps across all modules (`REQ-SHR-03`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_shared.sla_deadline_timers` / `shr_sla_timers` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-SLA-01` to `ATTR-SLA-09`.
- **Associated Conceptual Relationships:** `REL-SHR-004` (Monitored domain entity association).
- **Data Lifecycle & Temporal Boundaries:** Initialized upon workflow event; evaluated by background workers; executes automated locks (e.g., Group-D 10th at 23:59); resolves on task completion.
- **Source Traceability:** `REQ-MOD2-02`, `REQ-MOD3-02`, `REQ-SHR-03`; `SHR-SLA-REQ-01` to `03`.
- **Governing Unresolved Decisions:** None. Explicit deadlines codified in baseline rules.

### 10.5 ENT-SHR-05: Document Metadata & Binary Reference
- **Domain Owner:** Shared Platform (`DocumentManagementModule`)
- **Business Purpose:** Maintains external document storage locator references, document types, file sizes, and cryptographic verification hashes for binary files stored externally (`REQ-SHR-02`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_shared.document_metadata` / `shr_document_records` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-DOC-01` to `ATTR-DOC-10`.
- **Associated Conceptual Relationships:** `REL-SHR-005` (Pointers from dossiers, applications, evidence, letters).
- **Data Lifecycle & Temporal Boundaries:** Created upon upload; immutable once cryptographically signed; purged only per statutory retention rules.
- **Source Traceability:** `REQ-MOD1-03`, `REQ-MOD2-12`, `REQ-MOD3-16`, `REQ-SHR-02`; `SHR-DOC-REQ-01` to `03`.
- **Governing Unresolved Decisions:** Statutory retention schedules under `REQ-TBD-11`.

### 10.6 ENT-SHR-06: Notification Queue & Dispatch Record
- **Domain Owner:** Shared Platform (`NotificationEngineModule`)
- **Business Purpose:** Asynchronous delivery tracking for multi-channel emails, SMS alerts, and in-app notifications (`REQ-SHR-05`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_shared.notification_queue` / `shr_notification_queue` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-NTF-01` to `ATTR-NTF-09`.
- **Associated Conceptual Relationships:** `REL-SHR-006` (Recipient user link).
- **Data Lifecycle & Temporal Boundaries:** Staged in queue; dispatched by asynchronous worker; retried on failure; archived after delivery.
- **Source Traceability:** `REQ-MOD2-18`, `REQ-MOD3-02`, `REQ-SHR-05`; `SHR-NTF-REQ-01` to `03`.
- **Governing Unresolved Decisions:** Outbound SMTP relay and SMS gateway credentials under `REQ-TBD-10`.

### 10.7 ENT-SHR-07: Immutable Audit Trail Entry
- **Domain Owner:** Shared Platform (`AuditSecurityModule`)
- **Business Purpose:** Append-only audit trail capturing full before/after state diffs for all data mutations across the system (`REQ-SEC-04`, `REQ-MOD1-08`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_shared.audit_trail_entries` / `shr_audit_log` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-AUD-01` to `ATTR-AUD-10`.
- **Associated Conceptual Relationships:** `REL-SHR-007` (Actor user and target entity links).
- **Data Lifecycle & Temporal Boundaries:** Strictly append-only. Zero modification or deletion permitted; retained per statutory audit rules.
- **Source Traceability:** `REQ-MOD1-08`, `REQ-SEC-04`; `MOD1-AUD-REQ-01` to `06`, `SHR-AUD-REQ-01`.
- **Governing Unresolved Decisions:** Audit log retention duration under `REQ-TBD-11`.

### 10.8 ENT-SHR-08: ERP Transactional Outbox Staging Record
- **Domain Owner:** Shared Platform (`ErpIntegrationModule`)
- **Business Purpose:** Staging record implementing the Transactional Outbox Pattern for guaranteed, reliable ERP synchronization (`REQ-INT-01`, `MOD1-ERP-REQ-03`).
- **Proposed Schema Grouping / Illustrative Table:** `platform_integration.erp_outbox_staging` / `erp_outbox_events` (`[D] Proposed Representation`).
- **Logical Attribute References:** `ATTR-ERP-01` to `ATTR-ERP-09`.
- **Associated Conceptual Relationships:** `REL-SHR-008` (Target employee master record link).
- **Data Lifecycle & Temporal Boundaries:** Written within the same database transaction as approved master record changes; polled asynchronously; dispatched to ERP; marked acknowledged.
- **Source Traceability:** `REQ-MOD1-04`, `REQ-INT-01`; `MOD1-CDB-REQ-03`, `MOD1-ERP-REQ-03`, `SHR-INT-REQ-01`.
- **Governing Unresolved Decisions:** ERP transport architecture, physical protocol, and payload schema under `REQ-TBD-01`.

---

## 11. Key and Identity Strategy

### 11.1 Conceptual Identity Principles

In accordance with Phase 4 governance, identity is evaluated at a conceptual and logical business level:
- **No Physical Keys Assigned:** No SQL primary keys, auto-increment sequences, or foreign key syntax are created in this document.
- **Distinction Between Business Identity and Internal System Identity:**
  - *Business Identity:* Real-world institutional codes used by university stakeholders (e.g., Employee Roll Code, MRF Tracking Number, LOI Reference Number).
  - *Internal Logical Identity:* Logical identifiers utilized by the application layer to correlate entity lifecycles across relational associations and audit ledgers.

### 11.2 Entity Business Identity Catalogue

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            CONCEPTUAL BUSINESS IDENTITY OVERVIEW                                 │
├───────────────────┬───────────────────────────┬──────────────────────────────────────────────────┤
│ CONCEPTUAL ENTITY │ BUSINESS IDENTITY CONCEPT │ NATURE AND LOGICAL SCOPE                         │
├───────────────────┼───────────────────────────┼──────────────────────────────────────────────────┤
│ ENT-MOD1-01       │ Institutional Employee ID │ Authoritative university personnel code. Format  │
│                   │                           │ authority governed by REQ-TBD-01.                │
│ ENT-MOD1-02       │ Position Node Code        │ Hierarchical position code within university DAG.│
│ ENT-MOD1-03       │ Dossier Document Index    │ Permanent personal file document reference.      │
│ ENT-MOD1-04       │ Change Request Tracking ID│ Formal tracking code for service change requests.│
│ ENT-MOD1-05       │ Approval Event ID         │ Immutable sign-off action record code.           │
│ ENT-MOD1-06       │ Historical Slice Index    │ Chronological service interval slice code.       │
│ ENT-MOD2-01       │ Academic Plan ID          │ Semester workload requisition cycle code.        │
│ ENT-MOD2-02       │ Non-Academic Plan ID      │ Annual non-faculty departmental requisition code.│
│ ENT-MOD2-03       │ MRF Tracking Number       │ Requisition number (e.g., MRF-2026-ENG-001).     │
│ ENT-MOD2-04       │ Position Tracker Code     │ Attachment 3 vacancy monitoring entry code.      │
│ ENT-MOD2-05       │ Candidate Application ID  │ Multi-channel applicant tracking code.           │
│ ENT-MOD2-06       │ RCS Sheet Number          │ Recruiter calling feedback sheet reference.      │
│ ENT-MOD2-07       │ SCM Session Number        │ Statutory Selection Committee Meeting session ID.│
│ ENT-MOD2-08       │ Interview Round ID        │ Sequential interview round record identifier.    │
│ ENT-MOD2-09       │ LOI Reference Number      │ Formal offer document code (e.g., LOI-2026-089). │
│ ENT-MOD2-10       │ Replacement Tracker ID    │ Resignation replacement countdown tracking ID.   │
│ ENT-MOD3-01       │ Group-D Template Code     │ Role-specific KPI template version identifier.   │
│ ENT-MOD3-02       │ Monthly Evaluation ID     │ Group-D monthly evaluation form tracking code.   │
│ ENT-MOD3-03       │ Annual Collation Report ID│ 12-month Group-D annual report reference.        │
│ ENT-MOD3-04       │ Staff Goal Record ID      │ Onboarding 30-day KRA/KPI goal sheet identifier. │
│ ENT-MOD3-05       │ Quarterly Review ID       │ Staff quarterly review stage record code (Q1-Q4).│
│ ENT-MOD3-06       │ Annual Appraisal Outcome  │ Consolidated staff annual appraisal outcome ID.  │
│ ENT-MOD3-07       │ Eligibility Batch Code    │ Monthly 10th faculty eligibility scan batch ID.  │
│ ENT-MOD3-08       │ Faculty Dossier ID        │ Faculty self-appraisal dossier tracking number.  │
│ ENT-MOD3-09       │ ECM Session Record ID     │ Evaluation Committee Meeting outcome record ID.  │
│ ENT-SHR-01        │ Login Principal Name      │ Institutional username / email / SSO subject ID. │
│ ENT-SHR-02        │ Role Grant Identifier     │ Role-permission mapping assignment code.         │
│ ENT-SHR-03        │ Workflow Transition ID    │ FSM state transition audit record identifier.    │
│ ENT-SHR-04        │ SLA Timer Code            │ Centralized countdown deadline timer identifier. │
│ ENT-SHR-05        │ Document Storage Key      │ Immutable external object storage key / URI.     │
│ ENT-SHR-06        │ Notification Message ID   │ Asynchronous notification queue entry code.      │
│ ENT-SHR-07        │ Audit Transaction UUID    │ Tamper-evident transaction identifier.           │
│ ENT-SHR-08        │ ERP Outbox Event ID       │ Transactional staging queue event identifier.    │
└───────────────────┴───────────────────────────┴──────────────────────────────────────────────────┘
```

### 11.3 Cross-Module Identity Correlation & Matching

1. **Employee Identity Correlation (`employee_id`):** Serves as the primary correlation token linking `ENT-MOD1-01` across all functional modules:
   - Module I: Anchors Organization Nodes (`ENT-MOD1-02`), Dossier Items (`ENT-MOD1-03`), Change Requests (`ENT-MOD1-04`), and Service Slices (`ENT-MOD1-06`).
   - Module II: Links resigning employees in Replacement Trackers (`ENT-MOD2-10`).
   - Module III: Governs Group-D evaluations (`ENT-MOD3-02`/`03`), Staff goals/reviews (`ENT-MOD3-04`/`05`/`06`), and Faculty ECM dossiers (`ENT-MOD3-07`/`08`).
   - Shared Platform: Maps user accounts (`ENT-SHR-01`) and ERP outbox payloads (`ENT-SHR-08`).
2. **Requisition Correlation (`mrf_id`):** Links approved planning (`ENT-MOD2-01`/`02`), position tracking (`ENT-MOD2-04`), candidate sourcing (`ENT-MOD2-05`), and urgent replacements (`ENT-MOD2-10`).
3. **Application Correlation (`application_id`):** Links candidate profiles (`ENT-MOD2-05`) through screening (`ENT-MOD2-06`), evaluation (`ENT-MOD2-07`/`08`), and offers (`ENT-MOD2-09`).
4. **Unresolved Identity Authority (`REQ-TBD-01`):** Whether the primary `employee_id` is minted by the University ERP upon initial record handshake or generated authoritatively by the HRMS Central Database remains an open technical decision.

---

## 12. Relationship and Referential Integrity Considerations

### 12.1 Approved Conceptual Relationship Inventory

All **forty-one (41) conceptual relationships** from [`04-ENTITY-RELATIONSHIP-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/04-ENTITY-RELATIONSHIP-SPECIFICATION.md) are preserved without modification:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            APPROVED CONCEPTUAL RELATIONSHIP INVENTORY                            │
├──────────────┬────────────────────────────┬────────────────────────────┬─────────────┬───────────┤
│ REL ID       │ SOURCE ENTITY              │ TARGET ENTITY              │ CARDINALITY │ DOMAIN    │
├──────────────┼────────────────────────────┼────────────────────────────┼─────────────┼───────────┤
│ REL-M1-001   │ ENT-MOD1-02 (Org Node)     │ ENT-MOD1-02 (Org Node)     │ 1 : 0..N    │ Module I  │
│ REL-M1-002   │ ENT-MOD1-02 (Org Node)     │ ENT-MOD1-01 (Employee)     │ 1 : 0..1    │ Module I  │
│ REL-M1-003   │ ENT-MOD1-01 (Employee)     │ ENT-MOD1-03 (Dossier Item) │ 1 : 0..N    │ Module I  │
│ REL-M1-004   │ ENT-MOD1-01 (Employee)     │ ENT-MOD1-04 (Change Req)   │ 1 : 0..N    │ Module I  │
│ REL-M1-005   │ ENT-MOD1-04 (Change Req)   │ ENT-MOD1-05 (Approval Act) │ 1 : 1..N    │ Module I  │
│ REL-M1-006   │ ENT-MOD1-04 (Change Req)   │ ENT-MOD1-06 (Service Slice)│ 1 : 0..1    │ Module I  │
│ REL-M1-007   │ ENT-MOD1-01 (Employee)     │ ENT-MOD1-06 (Service Slice)│ 1 : 1..N    │ Module I  │
├──────────────┼────────────────────────────┼────────────────────────────┼─────────────┼───────────┤
│ REL-M2-001   │ ENT-MOD2-01 (Acad Plan)    │ ENT-MOD2-03 (MRF)          │ 1 : 1..N    │ Module II │
│ REL-M2-002   │ ENT-MOD2-02 (NonAcad Plan) │ ENT-MOD2-03 (MRF)          │ 1 : 1..N    │ Module II │
│ REL-M2-003   │ ENT-MOD2-03 (MRF)          │ ENT-MOD2-04 (Pos Tracker)  │ 1 : 1       │ Module II │
│ REL-M2-004   │ ENT-MOD2-03 (MRF)          │ ENT-MOD2-05 (Candidate)    │ 1 : 0..N    │ Module II │
│ REL-M2-005   │ ENT-MOD2-05 (Candidate)    │ ENT-MOD2-06 (RCS Record)   │ 1 : 0..1    │ Module II │
│ REL-M2-006   │ ENT-MOD2-05 (Candidate)    │ ENT-MOD2-07 (SCM Session)  │ 1 : 0..1    │ Module II │
│ REL-M2-007   │ ENT-MOD2-05 (Candidate)    │ ENT-MOD2-08 (Interview Rnd)│ 1 : 0..3    │ Module II │
│ REL-M2-008   │ ENT-MOD2-05 (Candidate)    │ ENT-MOD2-09 (LOI Record)   │ 1 : 0..1    │ Module II │
│ REL-M2-009   │ ENT-MOD2-10 (Urgent Repl)  │ ENT-MOD2-03 (MRF)          │ 1 : 1       │ Module II │
├──────────────┼────────────────────────────┼────────────────────────────┼─────────────┼───────────┤
│ REL-M3-001   │ ENT-MOD3-01 (GD Template)  │ ENT-MOD3-02 (GD Monthly)   │ 1 : 0..N    │ Module III│
│ REL-M3-002   │ ENT-MOD3-03 (GD Annual)    │ ENT-MOD3-02 (GD Monthly)   │ 1 : 12      │ Module III│
│ REL-M3-003   │ ENT-MOD3-04 (Staff Goal)   │ ENT-MOD3-05 (Staff Qtr)    │ 1 : 4       │ Module III│
│ REL-M3-004   │ ENT-MOD3-06 (Staff Annual) │ ENT-MOD3-05 (Staff Qtr)    │ 1 : 4       │ Module III│
│ REL-M3-005   │ ENT-MOD3-07 (Fac Batch)    │ ENT-MOD3-08 (Fac Dossier)  │ 1 : 1..N    │ Module III│
│ REL-M3-006   │ ENT-MOD3-08 (Fac Dossier)  │ ENT-MOD3-09 (Fac ECM)      │ 1 : 0..1    │ Module III│
├──────────────┼────────────────────────────┼────────────────────────────┼─────────────┼───────────┤
│ REL-SHR-001  │ ENT-SHR-01 (User Account)  │ ENT-MOD2-07 (SCM Session)  │ 1 : 0..N    │ Shared    │
│ REL-SHR-002  │ ENT-SHR-01 (User Account)  │ ENT-SHR-02 (Role Assign)   │ 1 : 1..N    │ Shared    │
│ REL-SHR-003  │ ENT-SHR-03 (Workflow FSM)  │ Domain Entities (Universal)│ 1 : 0..N    │ Shared    │
│ REL-SHR-004  │ ENT-SHR-04 (SLA Timer)     │ Monitored Domain Entities  │ 1 : 0..N    │ Shared    │
│ REL-SHR-005  │ ENT-SHR-05 (Doc Metadata)  │ Referencing Domain Entities│ 1 : 0..N    │ Shared    │
│ REL-SHR-006  │ ENT-SHR-06 (Notification)  │ ENT-SHR-01 (User Account)  │ 0..N : 1    │ Shared    │
│ REL-SHR-007  │ ENT-SHR-07 (Audit Trail)   │ Target Entities / Users    │ 0..N : 1    │ Shared    │
│ REL-SHR-008  │ ENT-SHR-08 (ERP Outbox)    │ ENT-MOD1-01 (Employee)     │ 0..N : 1    │ Shared    │
├──────────────┼────────────────────────────┼────────────────────────────┼─────────────┼───────────┤
│ REL-XMOD-001 │ ENT-MOD2-09 (LOI Record)   │ ENT-MOD1-01 (Employee)     │ 1 : 1       │ Cross-Mod │
│ REL-XMOD-002 │ ENT-MOD1-01 (Employee)     │ ENT-MOD2-10 (Urgent Repl)  │ 1 : 0..N    │ Cross-Mod │
│ REL-XMOD-003 │ ENT-MOD1-03 (Dossier Item) │ ENT-SHR-05 (Doc Metadata)  │ 1 : 1       │ Cross-Mod │
│ REL-XMOD-004 │ Mod III Outcomes (03/06/09)│ ENT-MOD1-04 (Change Req)   │ 1 : 1       │ Cross-Mod │
│ REL-XMOD-005 │ ENT-MOD1-01 (Employee)     │ ENT-MOD3-02 (GD Monthly)   │ 1 : 0..N    │ Cross-Mod │
│ REL-XMOD-006 │ ENT-MOD1-01 (Employee)     │ ENT-MOD3-03 (GD Annual)    │ 1 : 0..N    │ Cross-Mod │
│ REL-XMOD-007 │ ENT-MOD1-01 (Employee)     │ ENT-MOD3-04 (Staff Goal)   │ 1 : 1       │ Cross-Mod │
│ REL-XMOD-008 │ ENT-MOD1-01 (Employee)     │ ENT-MOD3-05 (Staff Qtr)    │ 1 : 0..N    │ Cross-Mod │
│ REL-XMOD-009 │ ENT-MOD1-01 (Employee)     │ ENT-MOD3-06 (Staff Annual) │ 1 : 0..N    │ Cross-Mod │
│ REL-XMOD-010 │ ENT-MOD1-01 (Employee)     │ ENT-MOD3-08 (Fac Dossier)  │ 1 : 0..N    │ Cross-Mod │
│ REL-XMOD-011 │ ENT-MOD2-05 (Candidate)    │ ENT-SHR-05 (Doc Metadata)  │ 1 : 1       │ Cross-Mod │
└──────────────┴────────────────────────────┴────────────────────────────┴─────────────┴───────────┘
```

### 12.2 Referential Integrity as a Future Design Consideration

In downstream physical design (`07-CONSTRAINTS-AND-RELATIONSHIPS.md`), referential integrity will be addressed under the following architectural guidelines:
1. **Intra-Domain Foreign Keys:** Direct relational foreign keys (`REFERENCES`) are appropriate between entities within the same domain (e.g., `ENT-MOD1-04` $\rightarrow$ `ENT-MOD1-05`, `ENT-MOD2-05` $\rightarrow$ `ENT-MOD2-06`).
2. **Cross-Domain Integrity via Monolith Contexts:** Cross-domain references (e.g., `ENT-MOD3-02` pointing to `ENT-MOD1-01`) share the same PostgreSQL database instance, permitting database-level foreign key enforcement while maintaining logical application-layer domain boundaries.
3. **No Cascading Deletions:** Business records (employees, change requests, applications, scorecards, appraisals) are permanent and subject to audit trails; physical `ON DELETE CASCADE` is prohibited across all core entities (`[B]`).
4. **Documented Relationship Uncertainties:**
   - `REL-SHR-001` (External Expert Access): Time-limited token lifecycle governed by `REQ-TBD-07`.
   - `REL-M2-009` (LOI vs. Appointment Letter): Formal boundary remains unspecified in baseline; qualifies `REQ-TBD-08`.
   - `REL-SHR-008` (ERP Outbox Reflection): Staging mechanics and transport protocol governed by `REQ-TBD-01`.
   - `REL-M3-001` / `REL-M3-003` (Staff Track Boundaries): Technical staff cadre allocation governed by `REQ-TBD-03`.

---

## 13. Data Integrity and Validation Considerations

### 13.1 Conceptual Integrity Framework

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            DATA INTEGRITY & VALIDATION FRAMEWORK                                 │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ INTEGRITY DIMENSION           │ SOURCE BUSINESS REQUIREMENT    │ OPERATIONAL VALIDATION RULE     │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Employee Master Integrity     │ REQ-MOD1-01, REQ-MOD1-04       │ Reflects strictly active service│
│                               │ MOD1-CDB-REQ-01 to 05          │ conditions. No pending values.  │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Change Staging Isolation      │ REQ-MOD1-05, REQ-MOD1-07       │ Proposed values staged in FSM   │
│                               │ MOD1-CHG-REQ-01 to 19          │ container. Committed only on    │
│                               │ BR-04, BR-05, BR-07            │ effective date activation.      │
├───────────────────────────────┼───────────────────────────────┼─────────────────────────────────┤
│ Two-Level Approval Gating     │ REQ-MOD1-06, BR-04, BR-07      │ Level 2 blocked until Level 1 is│
│                               │ MOD1-APP-REQ-01 to 03          │ committed. Segregation of duty. │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Single Annual Plan Quota      │ REQ-MOD2-07, BR-24             │ Department strictly restricted  │
│                               │ MOD2-MP-NF-REQ-03              │ to max 1 planned MRF per year.  │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ UGC Norm Statutory Check      │ REQ-MOD2-13, BR-30             │ Academic faculty CVs flagged for│
│                               │ MOD2-UGC-REQ-01 to 02          │ NET/SET/PhD compliance.         │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Non-Academic Round Gating     │ REQ-MOD2-15, BR-36, BR-37      │ Sequential clearance enforced:  │
│                               │ MOD2-SEL-NF-REQ-01 to 02       │ Round 1 ──► Round 2 ──► Round 3.│
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Group-D Monthly Auto-Lock     │ REQ-MOD3-04, REQ-MOD3-05       │ Forms unsubmitted by 10th at    │
│                               │ BR-45, BR-46, MOD3-GD-REQ-08   │ 23:59 auto-locked as delinquent.│
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Probation Compensation Gate   │ REQ-MOD3-06, REQ-MOD3-14       │ Probation completed = TRUE must │
│                               │ BR-49, BR-55, MOD3-GD-REQ-14   │ hold before compensation review.│
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ KRA 30-Day Goal Lock          │ REQ-MOD3-09, BR-51, BR-52      │ Goals locked within DOJ + 30    │
│                               │ MOD3-KRA-REQ-02 to 03          │ days; immutable during reviews. │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Faculty 4-Unit Verification   │ REQ-MOD3-17, BR-58             │ Parallel clearance required from│
│                               │ MOD3-FAC-REQ-07 to 11          │ Dean, R&D, Placement, and HR.   │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ Cryptographic Binary Checksum │ REQ-SHR-02, SHR-DOC-REQ-02     │ SHA-256 integrity hash verified │
│                               │ TECHNOLOGY_ARCHITECTURE_BASE   │ against tamper on binary files. │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

### 13.2 Conceptual vs. Physical Enforcement Boundary

- **Conceptual Validation (Current Baseline):** Business rules define semantic validity (e.g., probation must be complete, 2 levels of approval must occur, maximum 1 planned MRF per department per year).
- **Physical Enforcement (Future Step 6):** Translation into database-level `CHECK` constraints, composite uniqueness, foreign key triggers, or application-level service guards will be formalized in [`07-CONSTRAINTS-AND-RELATIONSHIPS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/07-CONSTRAINTS-AND-RELATIONSHIPS.md). No physical constraint syntax is assumed here.

---

## 14. Audit, History, and Lifecycle Considerations

### 14.1 Conceptual State Lifecycle Spectrum

The schema specification distinguishes between five distinct states of business information:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             INFORMATION LIFECYCLE SPECTRUM                                       │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ LIFECYCLE CATEGORY            │ BUSINESS MEANING               │ APPLICABLE ENTITIES             │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 1. Proposed / Staged Data     │ Modifications drafted or under │ ENT-MOD1-04 (Change Request)    │
│                               │ review; isolated from master.  │ ENT-MOD2-01/02 (Plans)          │
│                               │                                │ ENT-MOD2-03 (MRF Drafts)        │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 2. Approved / Pending Schedule│ Review finalized; awaiting the │ ENT-MOD1-04 (Approved Pending   │
│                               │ scheduled effective date.      │ Activation)                     │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 3. Currently Active Master    │ Authoritative state governing  │ ENT-MOD1-01 (Employee Master)   │
│                               │ current university operations. │ ENT-MOD1-02 (Org Hierarchy DAG) │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 4. Completed Evaluation Event │ Finalized scorecards, reviews, │ ENT-MOD2-07 (SCM Session)       │
│                               │ and statutory panel records.   │ ENT-MOD2-08 (Interview Rounds)  │
│                               │                                │ ENT-MOD3-02/05/08 (Evaluations) │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 5. Immutable Historical Slice │ Point-in-time snapshot of past │ ENT-MOD1-06 (Service History)   │
│                               │ service conditions / audits.   │ ENT-SHR-07 (Audit Trail Entry)  │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

### 14.2 Auditability and Version History Guarantees

1. **Immutable Audit Trail (`ENT-SHR-07`):** Every insert, update, review sign-off, approval, rejection, and scheduled activation generates an append-only audit record capturing the acting user ID, timestamp, client IP, action verb, and exact before/after JSON snapshots (`MOD1-AUD-REQ-02`).
2. **Temporal Service Book Reconstruction (`ENT-MOD1-06`):** Employee promotions, salary revisions, and transfers create contiguous temporal intervals (`valid_from` to `valid_to`), enabling retroactive statutory reporting and accreditation audits at any past date (`MOD1-VER-REQ-02`).
3. **Statutory Retention Uncertainty (`REQ-TBD-11`):** Regulatory retention durations (years to retain rejected candidate CVs, SCM marks, historical change logs) remain uncodified in official university bylaws.

---

## 15. Cross-Module and ERP Integration Considerations

### 15.1 Integration Topology & Protocol Boundaries

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            CROSS-MODULE & ERP INTEGRATION TOPOLOGY                               │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘

   [ External University ERP System ]
                  ▲
                  │ Asynchronous Dispatch via Webhooks / Batch File (REQ-TBD-01)
                  │ Polled from Outbox (Guaranteed Delivery)
   ┌──────────────┴────────────────────────────────────────────────┐
   │ platform_integration (Domain 5)                               │
   │ ENT-SHR-08: ERP Transactional Outbox Staging Record           │
   └──────────────▲────────────────────────────────────────────────┘
                  │
                  │ Atomic In-Transaction Write (MOD1-ERP-REQ-03)
   ┌──────────────┴────────────────────────────────────────────────┐
   │ core_change (Domain 1: System of Record)                      │
   │ ENT-MOD1-01: Central Employee Master Database                 │
   └──────────────▲───────────────────────────────▲────────────────┘
                  │                               │
       Day-1 Master Handshake          Appraisal Outcome Handshake
       (BP-XMOD-001)                   (BP-XMOD-004)
                  │                               │
   ┌──────────────┴──────────────┐ ┌──────────────┴────────────────┐
   │ recruitment (Domain 2)      │ │ performance (Domain 3)        │
   │ ENT-MOD2-09: Letter of      │ │ ENT-MOD3-06: Staff Outcome    │
   │ Intent ("Yet to Join")      │ │ ENT-MOD3-09: Faculty ECM      │
   └─────────────────────────────┘ └───────────────────────────────┘
```

### 15.2 Communication Protocol Baseline
- **Synchronous Commands & Queries:** Standard REST API interfaces within NestJS controllers handle all client-to-server operations.
- **Client-Side Real-Time Pushes:** **Socket.IO** is the approved technology for server-to-browser real-time events (`ADR-001`), such as live org chart updates, task reminders, and workflow notifications.
- **Critical Protocol Boundary Directive:** **Socket.IO is NOT an ERP synchronization protocol.** Real-time WebSocket adapters serve end-user web clients, while ERP synchronization is mediated strictly through the Transactional Outbox Pattern (`ENT-SHR-08`).
- **No Unapproved Middleware:** No message brokers (RabbitMQ, Kafka, ActiveMQ) or cloud-specific integration buses are approved in the architecture baseline.

---

## 16. Security and Data Classification Considerations

### 16.1 Conceptual Security Architecture Alignment

The database schema aligns with the enterprise security requirements established in [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md):
- **Authentication & Tokens (`SHR-AUT-REQ-02`):** JWT session tokens for internal personnel; time-limited signed guest access tokens for external statutory SCM experts (`ENT-SHR-01`).
- **Row-Level Access Scoping (`SHR-RBC-REQ-02`):**
  - *HOD Scope:* Filtered to departmental personnel and requisitions.
  - *Dean Scope:* Filtered to school-wide faculty, requisitions, and appraisals.
  - *Senior Management & Pro-Chancellor Scope:* Unrestricted university-wide visibility.
  - *Employee Self-Service Scope:* Personal service file and self-appraisals only.

### 16.2 Field-Level Cryptographic Recommendations

Downstream physical schema designs must implement encryption at rest for attributes classified as `Highly Sensitive (PII / Financial)`:
- `ATTR-EMP-06` (Current Base Salary Structure)
- `ATTR-CHG-06` (Proposed Compensation Revision Payload)
- `ATTR-HST-09` (Historical Salary Interval Snapshot)
- `ATTR-RCS-06` / `ATTR-RCS-07` (Candidate Current & Expected CTC)
- `ATTR-LOI-04` (Approved Offer Compensation Package)
- `ATTR-ECM-06` (Faculty Historical Increment Snapshot)
- `ATTR-USR-04` (Authentication Credential Secret Hash)

---

## 17. Unresolved Schema Decisions

In strict compliance with project governance, unresolved schema design decisions are catalogued below under classification **`[E] TBD / Open Decision`** and cross-referenced with the eleven (11) official baseline TBD items:

| Schema Decision ID | Governing Baseline TBD | Affected Schema Domain & Entity | Nature of Schema Uncertainty / Missing Decision | Required Institutional Action |
|---|---|---|---|---|
| `SCH-DEC-01` | **`REQ-TBD-01`** | Integration: `ENT-SHR-08`, Core: `ENT-MOD1-01` | ERP Synchronization Architecture: Protocol (REST API vs. database staging vs. SFTP batch); authority for minting primary employee IDs; physical staging payload schema. | University IT / ERP Technical Directorate confirmation. |
| `SCH-DEC-02` | **`REQ-TBD-02`** | Recruitment: `ENT-MOD2-01`/`03`/`06`, Performance: `ENT-MOD3-01`/`08` | Physical Enclosure Schemas: Field-level definitions and validation constraints for Attachments 1–3, MRF Enclosure 1, RCS, Group-D Enclosures 1–2, and Faculty ECM Enclosures 1–3. | HR Leadership & Academic Deans Committee approval. |
| `SCH-DEC-03` | **`REQ-TBD-03`** | Recruitment: `ENT-MOD2-02`, Performance: `ENT-MOD3-04`/`07` | Technical Cadre Appraisal Track Allocation: Schema routing allocating Lab Technicians and Teaching Associates between Group-D, Staff KRA, or Faculty ECM tracks. | Registrar & HR Leadership formal policy ruling. |
| `SCH-DEC-04` | **`REQ-TBD-04`** | Recruitment: `ENT-MOD2-07`, Performance: `ENT-MOD3-09` | TNU Protocol Weights & Quorums: Exact percentage formulas across teaching, research, and placement, plus statutory committee quorums for evaluation matrices. | Academic Council & Vice Chancellor approval. |
| `SCH-DEC-05` | **`REQ-TBD-05`** | Performance: `ENT-MOD3-03`/`06`/`09` | Pre-Defined Compensation Slabs: Quantitative monetary brackets, percentage increment tables, and step-grade scales applied against performance scores. | Senior Management & Finance Committee approval. |
| `SCH-DEC-06` | **`REQ-TBD-06`** | Core: `ENT-MOD1-01`, Recruitment: `ENT-MOD2-10` | Resignation Upstream Intake Interface: Self-service vs. administrative entry in Module I; clearance workflow prior to replacement clock initialization. | Head of HR operational process directive. |
| `SCH-DEC-07` | **`REQ-TBD-07`** | Platform: `ENT-SHR-01`, Recruitment: `ENT-MOD2-07` | Enterprise SSO Protocol & External Expert Access: Identity Provider selection (Google, Microsoft, LDAP); external expert token portal vs. OTP mechanism. | University IT Infrastructure & Cybersecurity Directorate confirmation. |
| `SCH-DEC-08` | **`REQ-TBD-08`** | Recruitment: `ENT-MOD2-09` | LOI vs. Formal Appointment Letter Boundary: Contractual handoff determining whether LOI is sole pre-joining instrument or Appointment Letter is issued post-verification. | HR Department & University Legal Counsel legal determination. |
| `SCH-DEC-09` | **`REQ-TBD-09`** | Core: `ENT-MOD1-04` | Administrative Allowance for Secondary Roles: Service rules governing mandatory administrative allowances or honorariums for Deans, HODs, Proctors in Change Format 3(h). | HR Leadership & Finance Directorate policy ruling. |
| `SCH-DEC-10` | **`REQ-TBD-10`** | Platform: `ENT-SHR-06` | Outbound Communication Gateways & Relays: SMTP host configurations, sender aliases, and SMS/WhatsApp gateway credentials for automated reminders. | University Systems Administrator & IT Infrastructure confirmation. |
| `SCH-DEC-11` | **`REQ-TBD-11`** | Core: `ENT-MOD1-03`, Platform: `ENT-SHR-05`/`07` | Statutory Document Retention & Archival Schedules: Minimum statutory years to retain rejected candidate CVs, SCM marks, historical change logs, and personnel files. | University Registrar & Legal Compliance Directorate codification. |

---

## 18. Requirement-to-Schema Traceability

The following matrix verifies that all functional requirement clusters across the approved requirements catalogue (`02-REQUIREMENT-CATALOGUE.md`) map into designated schema domains and entities:

| Requirement Cluster | Requirement Baseline IDs | Primary Schema Domain | Designated Conceptual Entities | Traceability Status |
|---|---|---|---|:---:|
| **Single Source of Truth Master DB** | `REQ-MOD1-01`, `REQ-MOD1-04`, `MOD1-CDB-REQ-01` to `05` | Core Employee & Change | `ENT-MOD1-01` | **Ground Truth Verified** |
| **Connected Dynamic Org Chart** | `REQ-MOD1-02`, `MOD1-ORG-REQ-01` to `04` | Core Employee & Change | `ENT-MOD1-02` | **Ground Truth Verified** |
| **Digital Personal Dossier** | `REQ-MOD1-03`, `MOD1-FIL-REQ-01` to `04` | Core Employee & Change | `ENT-MOD1-03`, `ENT-SHR-05` | **Ground Truth Verified** |
| **Service Change Requests (10 Formats)**| `REQ-MOD1-05`, `MOD1-CHG-REQ-01` to `19` | Core Employee & Change | `ENT-MOD1-04` | **Ground Truth Verified** |
| **Two-Level Approval Hierarchy** | `REQ-MOD1-06`, `MOD1-APP-REQ-01` to `06` | Core Employee & Change | `ENT-MOD1-05`, `ENT-SHR-03` | **Ground Truth Verified** |
| **Effective-Date Scheduling** | `REQ-MOD1-07`, `MOD1-EFF-REQ-01` to `03` | Core Employee & Change | `ENT-MOD1-04`, `ENT-MOD1-06` | **Ground Truth Verified** |
| **Service History Ledger & Versioning** | `REQ-MOD1-08`, `MOD1-VER-REQ-01` to `02` | Core Employee & Change | `ENT-MOD1-06` | **Ground Truth Verified** |
| **Academic Manpower Planning (T-4M)** | `REQ-MOD2-02`, `MOD2-MP-FAC-REQ-01` to `08` | Recruitment & Selection | `ENT-MOD2-01` | **Ground Truth Verified** |
| **Non-Academic Planning (Single Quota)**| `REQ-MOD2-07`, `MOD2-MP-NF-REQ-01` to `08` | Recruitment & Selection | `ENT-MOD2-02` | **Ground Truth Verified** |
| **MRF Requisitions & Lifecycle** | `REQ-MOD2-03`, `REQ-MOD2-06`, `MOD2-MRF-REQ-01` to `07` | Recruitment & Selection | `ENT-MOD2-03` | **Ground Truth Verified** |
| **Open Positions Tracker (Attachment 3)**| `REQ-MOD2-11`, `MOD2-POS-REQ-01` to `05` | Recruitment & Selection | `ENT-MOD2-04` | **Ground Truth Verified** |
| **Omnichannel Sourcing & Central CVs** | `REQ-MOD2-12`, `MOD2-SRC-REQ-01` to `06` | Recruitment & Selection | `ENT-MOD2-05` | **Ground Truth Verified** |
| **UGC Norm Screening Flags** | `REQ-MOD2-13`, `MOD2-UGC-REQ-01` to `02` | Recruitment & Selection | `ENT-MOD2-05` | **Ground Truth Verified** |
| **Recruiter Calling Sheet (RCS)** | `REQ-MOD2-12`, `MOD2-RCS-REQ-01` to `06` | Recruitment & Selection | `ENT-MOD2-06` | **Ground Truth Verified** |
| **Academic SCM Selection Meetings** | `REQ-MOD2-14`, `MOD2-SCM-REQ-01` to `06` | Recruitment & Selection | `ENT-MOD2-07` | **Ground Truth Verified** |
| **Non-Academic 3-Round Interviews** | `REQ-MOD2-15`, `MOD2-SEL-NF-REQ-01` to `03` | Recruitment & Selection | `ENT-MOD2-08` | **Ground Truth Verified** |
| **LOI Generation & "Yet to Join" Flag** | `REQ-MOD2-16` to `18`, `MOD2-YTJ-REQ-01` to `07` | Recruitment & Selection | `ENT-MOD2-09` | **Ground Truth Verified** |
| **Urgent Replacement Resignation Clock**| `REQ-MOD2-03`, `MOD2-RES-REQ-01` to `06` | Recruitment & Selection | `ENT-MOD2-10` | **Ground Truth Verified** |
| **Group-D Evaluation Forms & Versioning**| `REQ-MOD3-01`, `REQ-MOD3-03`, `MOD3-GD-REQ-01` to `03`| Performance Management | `ENT-MOD3-01` | **Ground Truth Verified** |
| **Group-D Monthly Due Date & Auto-Lock** | `REQ-MOD3-02`, `REQ-MOD3-04`, `MOD3-GD-REQ-04` to `13`| Performance Management | `ENT-MOD3-02` | **Ground Truth Verified** |
| **Group-D Annual Collation & Probation**| `REQ-MOD3-06` to `08`, `MOD3-GD-REQ-14` to `21`| Performance Management | `ENT-MOD3-03` | **Ground Truth Verified** |
| **General Staff KRA 30-Day Goal Setting**| `REQ-MOD3-09`, `MOD3-KRA-REQ-01` to `04` | Performance Management | `ENT-MOD3-04` | **Ground Truth Verified** |
| **General Staff Quarterly Reviews (Q1-4)**| `REQ-MOD3-10` to `12`, `MOD3-KRA-REQ-05` to `14`| Performance Management | `ENT-MOD3-05` | **Ground Truth Verified** |
| **Staff Annual Appraisal Handshake** | `REQ-MOD3-13`, `REQ-INT-04`, `MOD3-KRA-REQ-15` to `18`| Performance Management | `ENT-MOD3-06`, `ENT-MOD1-04` | **Ground Truth Verified** |
| **Faculty ECM Monthly Eligibility Scan**| `REQ-MOD3-14` to `15`, `MOD3-FAC-REQ-01` to `05`| Performance Management | `ENT-MOD3-07` | **Ground Truth Verified** |
| **Faculty Self-Appraisal & 4-Unit Check**| `REQ-MOD3-16` to `17`, `MOD3-FAC-REQ-06` to `13`| Performance Management | `ENT-MOD3-08` | **Ground Truth Verified** |
| **Faculty ECM Meeting & TNU Matrix** | `REQ-MOD3-18` to `20`, `MOD3-FAC-REQ-14` to `22`| Performance Management | `ENT-MOD3-09` | **Ground Truth Verified** |
| **Unified Identity & External Tokens** | `REQ-SEC-01` to `02`, `SHR-AUT-REQ-01` to `04` | Shared Platform | `ENT-SHR-01` | **Ground Truth Verified** |
| **Role-Based Access Control & Scoping** | `REQ-SEC-03`, `SHR-RBC-REQ-01` to `02` | Shared Platform | `ENT-SHR-02` | **Ground Truth Verified** |
| **Universal Workflow FSM & Audit Logs**| `REQ-SHR-01`, `SHR-WFL-REQ-01` to `03` | Shared Platform | `ENT-SHR-03` | **Ground Truth Verified** |
| **Unified SLA Timers & Auto-Locks** | `REQ-SHR-03`, `SHR-SLA-REQ-01` to `03` | Shared Platform | `ENT-SHR-04` | **Ground Truth Verified** |
| **Binary Object Storage Metadata** | `REQ-SHR-02`, `SHR-DOC-REQ-01` to `03` | Shared Platform | `ENT-SHR-05` | **Ground Truth Verified** |
| **Asynchronous Multi-Channel Reminders**| `REQ-SHR-05`, `SHR-NTF-REQ-01` to `03` | Shared Platform | `ENT-SHR-06` | **Ground Truth Verified** |
| **Immutable Append-Only Audit Trail** | `REQ-SEC-04`, `REQ-MOD1-08`, `SHR-AUD-REQ-01` | Shared Platform | `ENT-SHR-07` | **Ground Truth Verified** |
| **ERP Transactional Outbox Staging** | `REQ-INT-01`, `MOD1-ERP-REQ-03`, `SHR-INT-REQ-01` | Integration & ERP | `ENT-SHR-08` | **Ground Truth Verified** |

---

## 19. Quality Review and Validation

### 19.1 Quality Review Checklist

The schema specification has been audited against the rigorous quality criteria established for Phase 4:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            QUALITY AUDIT & GOVERNANCE COMPLIANCE                                 │
├──────────────────────────────────────────────────────────────────┬───────────┬───────────────────┤
│ AUDIT DIMENSION                                                  │ RESULT    │ VERIFICATION NOTE │
├──────────────────────────────────────────────────────────────────┼───────────┼───────────────────┤
│ 1. All 33 primary conceptual entities fully represented?         │ PASSED    │ 6+10+9+8 = 33     │
│ 2. All 41 conceptual relationships accounted for and unchanged?  │ PASSED    │ 100% aligned      │
│ 3. Logical attributes align with Step 4 catalogue references?    │ PASSED    │ 344 attributes ref│
│ 4. Every schema statement grounded or explicitly tagged [B/C/D]? │ PASSED    │ Zero fabrications │
│ 5. 5-tier classification framework strictly applied?             │ PASSED    │ [A]-[E] explicit  │
│ 6. Official baseline TBD references verified (REQ-TBD-01 to 11)?  │ PASSED    │ SCH-DEC-01 to 11  │
│ 7. Stakeholder delta items (CONF-*) isolated from approved base? │ PASSED    │ Reference-only    │
│ 8. Zero physical database DDL, tables, PKs, FKs, or SQL created? │ PASSED    │ Logical-only      │
│ 9. Modular Monolith & PostgreSQL architecture baseline preserved?│ PASSED    │ Single unified DB │
│ 10. Upstream requirements, rules, processes, and FRDs untouched? │ PASSED    │ Baselines frozen  │
└──────────────────────────────────────────────────────────────────┴───────────┴───────────────────┘
```

### 19.2 Governance Integrity Confirmation

1. **No Microservice Database Splitting:** The specification strictly preserves a single unified PostgreSQL database instance for the Modular Monolith application. Logical domain separation is preserved without physical database isolation.
2. **No Physical Database Artifacts Created:** The document contains zero physical DDL scripts, zero live SQL statements, zero physical primary or foreign key definitions, zero physical indexes, and zero ORM code.
3. **No Baseline Inflation:** The 104 atomic requirements, 59 business processes, 60 business rules, 11 baseline TBDs, 33 conceptual entities, and 41 conceptual relationships remain 100% frozen.

---

## 20. Limitations and Next Steps

### 20.1 Architectural Limitations of Current Artifact

1. **Schema Specification Only:** This document defines the logical organization, domain boundaries, entity profiles, and integrity expectations. It intentionally does not provide physical PostgreSQL `CREATE TABLE` scripts, physical column widths, or database storage parameters.
2. **Referential Constraints Deferred to Step 6:** Physical primary key selections, foreign key constraint declarations (`ON DELETE`, `ON UPDATE`), composite uniqueness definitions, and check constraint rules are formally specified in the upcoming Step 6 artifact: [`07-CONSTRAINTS-AND-RELATIONSHIPS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/07-CONSTRAINTS-AND-RELATIONSHIPS.md).
3. **Indexing Strategy Deferred to Step 9:** Concrete B-Tree, GIN, partial, and composite index declarations are formally evaluated in [`10-INDEXING-STRATEGY.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/10-INDEXING-STRATEGY.md).
4. **Physical Outbox and Audit Partitioning Deferred:** Table partitioning strategies for `ENT-SHR-07` (Audit Trail) and `ENT-SHR-08` (ERP Outbox) will be addressed in Steps 7 and 10.

### 20.2 Downstream Database Documentation Roadmap

```
docs/08-database/
├── 00-DATABASE-DOCUMENTATION-INDEX.md          ◄ [Master Index & Governance]
├── 01-DATABASE-DESIGN-OVERVIEW.md              ◄ [High-Level Architecture]
├── 02-DATA-MODEL-OVERVIEW.md                   ◄ [Conceptual Data Domains]
├── 03-ENTITY-IDENTIFICATION.md                 ◄ [33 Approved Conceptual Entities]
├── 04-ENTITY-RELATIONSHIP-SPECIFICATION.md     ◄ [41 Conceptual Relationships & ERDs]
├── 05-ENTITY-WISE-DETAILED-SPECIFICATION.md     ◄ [344 Logical Attributes Catalogue]
├── 06-DATABASE-SCHEMA-SPECIFICATION.md         ◄ [CURRENT ARTIFACT: Schema Specification]
│
▼ [DOWNSTREAM SEQUENTIAL STEPS]
├── 07-CONSTRAINTS-AND-RELATIONSHIPS.md         ◄ (Step 6: Primary keys, foreign keys, unique & check rules)
├── 08-AUDIT-AND-VERSION-HISTORY-MODEL.md       ◄ (Step 7: Immutable audit ledger schema & temporal diff tracking)
├── 09-EFFECTIVE-DATE-DATA-MODEL.md             ◄ (Step 8: Temporal activation schema & scheduled processing)
├── 10-INDEXING-STRATEGY.md                     ◄ (Step 9: B-Tree, GIN, composite indexes & query performance)
├── 11-DATA-INTEGRITY-CONSIDERATIONS.md         ◄ (Step 10: ACID transactional boundaries & consistency guards)
└── 12-DATABASE-QUALITY-REVIEW.md               ◄ (Step 11: Traceability audit & baseline compliance review)
```

---
*End of Document — Database Schema Specification.*
