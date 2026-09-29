# Phase 4 — Database Documentation
## 01. Database Design Overview

```
====================================================================================================
STATUS:
PHASE 4 FOUNDATION — DOCUMENTATION ONLY — INITIAL ARCHITECTURE ESTABLISHMENT

IMPORTANT GOVERNANCE NOTICE:
This document is STRICTLY DOCUMENTATION ONLY. 
It establishes the conceptual database design principles, architectural patterns, and domain 
boundaries for the University HR Change Management & Automation System. 
No physical tables, database migration files, SQL DDL scripts, Prisma schemas, or TypeORM entities 
are created herein. All requirements (104 frozen baseline), business processes (59 frozen baseline), 
and business rules (60 frozen baseline) remain strictly protected.
====================================================================================================
```

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md` |
| **System Phase** | Phase 4 — Database Documentation |
| **Project Name** | University HR Change Management & Automation System |
| **Document Purpose** | High-level architectural specification of the database design, System of Record concept, domain relationships, and data integrity principles |
| **Date of Preparation** | September 29, 2026 |
| **Authoritative Baselines** | `docs/01-requirements/` (104 Requirements); `docs/02-business-process/` (59 Processes); `docs/03-functional-requirements/` (Approved FRDs); `TECHNOLOGY_ARCHITECTURE_BASELINE.md` |
| **Database Technology** | **PostgreSQL** (Primary Relational System of Record — `[C] Approved Technical Decision`) |
| **Supporting In-Memory Store** | **Redis** (Cache, Real-Time Pub/Sub, and Job Queue Broker — `[C] Approved Technical Decision`) |
| **Backend Architecture** | **Modular Monolith** (NestJS + TypeScript — `[C] Approved Technical Decision`) |

---

## 1. Executive Summary & Design Philosophy

The database architecture for the University HR Change Management & Automation System is designed to serve as the single, authoritative, enterprise-wide **System of Record** for all employee service records, recruitment operations, and performance management cycles across the institution.

In strict alignment with the frozen requirements baseline and the approved Modular Monolith architecture, the database design adheres to five fundamental architectural principles:
1. **Authoritative Single Source of Truth:** Centralized employee master records eliminate duplicate data entry across administrative units (`[A]` Baseline `REQ-MOD1-01`, `MOD1-CDB-REQ-02`).
2. **Strict Separation of Master Data and Staged Changes:** Pending, unapproved, or future-dated change requests must never directly overwrite or mutate active employee master records (`[A]` Baseline `REQ-MOD1-05`, `BP-M1-004`).
3. **Immutable Temporal History & First-Class Auditing:** No historical personnel record, performance evaluation score, or approval action is ever destructively overwritten (`[A]` Baseline `REQ-MOD1-08`, `REQ-SEC-04`).
4. **Domain Boundary Encapsulation:** Modules within the Modular Monolith maintain logical ownership over their respective domain tables without raw cross-module database writes (`[C]` Approved Technical Baseline, `TECHNOLOGY_ARCHITECTURE_BASELINE.md` Section 6 & 11).
5. **ACID Transactional Guarantees:** Relational integrity, foreign key consistency, and atomic cross-domain transactions are enforced strictly via PostgreSQL (`[C]` Approved Technical Baseline).

> **Architectural Scope Declaration:**  
> The identified conceptual entity count is an analytical data-domain inventory and does not represent the final number of physical PostgreSQL tables.

---

## 2. PostgreSQL as the Authoritative System of Record

### 2.1 The System of Record Concept
In an enterprise academic environment, institutional personnel data is subject to rigorous regulatory oversight (e.g., UGC guidelines), statutory selection committees, financial audits, and multi-tier approval chains. 

PostgreSQL is designated as the sole **System of Record** for the platform:
- **Exclusivity:** All active employee profiles, organizational hierarchies, position requisitions, evaluation scorecards, and salary revisions reside authoritatively in PostgreSQL (`[C] Approved Technical Decision`).
- **Elimination of Split-Brain States:** External institutional systems (such as the University ERP) do not maintain disparate, unsynchronized employee records. Instead, changes committed to PostgreSQL are reliably propagated outbound to the ERP via transactional staging queues (`[A]` Baseline `REQ-MOD1-04`, `REQ-INT-01`).
- **No Transient Authority:** Supporting infrastructure layers—specifically Redis—are strictly transient. Redis stores cached copies of trees and ephemeral queue jobs, but holds zero authoritative state (`[C] Approved Technical Decision`).

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             SYSTEM OF RECORD (POSTGRESQL) TOPOLOGY                               │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   [ Client Browser / UI ] ──► [ NestJS Modular Monolith ] ──► [ POSTGRESQL (System of Record) ] │
│                                             │                         │                          │
│                                             ▼                         ▼                          │
│                                    [ REDIS (Cache/Queue) ]   [ Transactional Outbox Staging ]    │
│                                    • Ephemeral Org Tree      • ERP Sync Outbox Staging           │
│                                    • Background Job Queue    • Notification Outbox Staging       │
│                                    • WebSocket Pub/Sub       • Object Storage Metadata Pointers  │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 2.2 Relational Consistency & Transactional Guarantees
PostgreSQL provides robust **ACID** (Atomicity, Consistency, Isolation, Durability) guarantees essential for high-stakes HR operations (`[C] Approved Technical Decision`):
- **Atomicity:** A multi-step transaction (such as accepting an LOI, instantiating an employee master record, allocating an organization chart node, and marking an open position as filled) either commits completely or rolls back entirely (`[B]` Logical Implication from `BP-XMOD-001`).
- **Consistency:** Referential integrity is enforced at the relational database level via foreign keys and domain constraints, preventing orphaned records (`[B]` Logical Implication).
- **Isolation:** Transaction isolation ensures concurrent operations (such as simultaneous approvals or salary reviews) do not produce dirty reads or inconsistent intermediate states (`[B/C]`).
- **Durability:** Committed personnel transactions are persistently recorded by PostgreSQL, surviving system restarts and hardware failures without data loss (`[C] Approved Technical Decision`).

### 2.3 Semi-Structured Data Handling for Configurable Dynamic Forms `[C/D]`
While core organizational entities (employees, departments, requisitions, approval logs) are strictly modeled in normalized relational structures, specific university workflows require configurable parameter sets that evolve over time:
- **Group-D Role-Specific KPIs (`[A]` `REQ-MOD3-01` / `MOD3-GD-REQ-02`):** Different service roles (e.g., peons, drivers, security personnel, sweepers) possess unique operational competency rubrics.
- **Recruiter Calling Sheets (`[A]` `REQ-MOD2-12` / `MOD2-RCS-REQ-01`):** Telephonic screening questions vary dynamically across academic disciplines and administrative functions.
- **TNU Protocol Matrices (`[A]` `REQ-MOD3-18` / `MOD3-FAC-REQ-14`):** Annual Faculty Evaluation Committee score categories require periodic adjustment by academic leadership.

To accommodate these configurable form templates without requiring structural database schema migrations, the approved technology baseline utilizes PostgreSQL's native **`JSONB`** capability (`[C] Approved Technical Decision`, `TECHNOLOGY_ARCHITECTURE_BASELINE.md` lines 90, 500). Detailed indexing strategies (such as GIN indexes) are classified as `[D] Proposed Detail` and will be specified in downstream physical documentation.

---

## 3. Modular Monolith Relationship to the Database

### 3.1 Single Unified PostgreSQL Database with Logical Domain Separation
The backend application is architected as a **Modular Monolith** in NestJS (`[C] Approved Technical Decision`). To match this software architecture:
- **Single Database Instance:** All modules connect to one unified PostgreSQL database, eliminating the operational overhead, network latency, and distributed two-phase commit protocols of microservice databases (`[C] Approved Technical Decision`).
- **Logical Domain Separation:** Entities are logically organized and owned by functional domain (e.g., core employee records, recruitment pipelines, performance management subsystems, shared platform services). The design maintains module/domain ownership boundaries, while physical PostgreSQL schema partitioning remains a downstream design decision unless explicitly required by the approved architecture baseline (`[C/D]`).

### 3.2 Domain Data Ownership & Boundary Protection
To preserve the modularity of the codebase and prevent architectural erosion:
1. **Module Ownership:** Each NestJS module possesses exclusive ownership over its designated domain entities (`[C] Approved Technical Decision`).
2. **Encapsulated Data Access:** Modules may **not** execute direct cross-domain writes into entities owned by other modules (`[C] Approved Technical Decision`).
3. **Public In-Process Contracts:** When one domain requires data or actions from another (e.g., Module III creating a change request in Module I upon appraisal completion), it invokes the domain's public service contract or emits an in-process domain event (`[B]` Logical Implication from `BP-XMOD-004`).

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                        MODULAR MONOLITH DATABASE ACCESS PATTERN                                  │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   [ EmployeeCoreModule ]       [ RecruitmentModule ]       [ PerformanceManagementModule ]       │
│           │                             │                                 │                      │
│           ▼                             ▼                                 ▼                      │
│   (Core Domain Entities)       (Recruitment Entities)           (Performance Entities)           │
│   • Employee Master Records    • Manpower Requisitions          • Group-D Evaluations            │
│   • Organization Nodes         • Candidate Applications         • Staff KRA/KPI Reviews          │
│   • Service Change Requests    • Interview Scorecards           • Faculty ECM Evaluation Matrices│
│           │                             │                                 │                      │
│           └─────────────────────────────┼─────────────────────────────────┘                      │
│                                         ▼                                                        │
│                    [ UNIFIED POSTGRESQL RELATIONAL ENGINE ]                                      │
│                    • Shared ACID Transaction Boundary                                            │
│                    • Universal Foreign Key Referential Integrity                                 │
│                    • Shared Immutable Audit Trail Ledger                                         │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Major Functional Data Domains

The data model is partitioned into four major functional data domains derived directly from the project requirements:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 MAJOR FUNCTIONAL DATA DOMAINS                                    │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 1. MODULE I: CHANGE MGMT      │ 2. MODULE II: RECRUITMENT      │ 3. MODULE III: PERFORMANCE      │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ • Employee Master Data        │ • Academic Manpower Requisition│ • Subsystem 1: Group-D          │
│ • Org Hierarchy & Nodes       │ • Non-Academic Manpower MRFs   │   - Role KPI Templates          │
│ • Digital Personal Dossiers   │ • Urgent Replacement Tracking  │   - Monthly Evaluation Forms    │
│ • 10 Service Change Formats   │ • Open Positions Tracker       │   - Annual Collation Slabs      │
│ • 2-Level Approval History    │ • Omnichannel Candidate CVs    │ • Subsystem 2: Staff KRA/KPI    │
│ • Effective-Date Activations  │ • Recruiter Calling Records    │   - 30-Day Goal Setting         │
│ • Historical Version Ledger   │ • Academic SCM Panel Sessions  │   - Quarterly Q1-Q4 Reviews     │
│ • ERP Outbox Staging Records  │ • Non-Academic 3-Round Panels  │   - Annual Appraisal Handshake  │
│                               │ • LOI & "Yet to Join" Tracking │ • Subsystem 3: Faculty ECM      │
│                               │                                │   - Monthly Eligibility Scanner │
│                               │                                │   - 7-Day Self-Appraisal Forms  │
│                               │                                │   - 4-Unit Verification Logs    │
│                               │                                │   - Digital ECM Score Sheets    │
│                               │                                │   - TNU Protocol Matrices       │
├───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┤
│ 4. CORE SHARED PLATFORM DATA DOMAINS                                                             │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ • User Accounts, Credentials & Sessions (`SHR-AUT-REQ-01`)                                       │
│ • Role-Based Access Control (RBAC) & Contextual Data Scoping Rules (`SHR-RBC-REQ-01`)            │
│ • Universal Workflow Engine FSM Instances, States & Transitions (`SHR-WFL-REQ-01`)               │
│ • SLA Countdown Timers, Grace Periods & Auto-Lockout Timestamps (`SHR-SLA-REQ-01`)              │
│ • Document & Attachment Metadata (Object Storage Abstracted Pointers) (`SHR-DOC-REQ-01`)         │
│ • Notification Delivery Queue, Templates & Dispatch History (`SHR-NTF-REQ-01`)                  │
│ • Immutable Append-Only Audit Trail & Point-in-Time History (`MOD1-AUD-REQ-01`, `SHR-WFL-REQ-02`)│
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 5. Cross-Domain Data Relationships & Topology

### 5.1 Employee Master Data vs. Service Change Management
The relationship between active employee records and change requests is the core architectural foundation of Module I:
- **Strict Staging Separation:** When an authorized user raises a Service Change Request (across any of the 10 supported change categories: Salary, Designation, Reportee, Supervisor, Level, School, Location, Additional Responsibility, Qualification, or Other Service Condition), the proposed values are stored in a dedicated service change request staging entity (`[A]` Baseline `REQ-MOD1-05`).
- **No Direct Master Mutation:** The active employee master record remains completely unchanged throughout the 2-level approval workflow (`HR Level` → `Senior Management Level`) (`[A]` Baseline `REQ-MOD1-06`).
- **Effective-Date Gating:** Once approved by Senior Management:
  - If `effective_date <= CURRENT_DATE`: The change is activated immediately within an atomic database transaction (`[A]` Baseline `REQ-MOD1-07`).
  - If `effective_date > CURRENT_DATE`: The request transitions to an `APPROVED_PENDING_ACTIVATION` state. Active master records remain unaltered until the scheduled effective date arrives (`[A]` Baseline `REQ-MOD1-07`, `BP-M1-007`).
- **Historical Ledgering:** Upon activation, the prior state is recorded into the historical service ledger, ensuring an unbroken, point-in-time reconstruction of the employee's entire university tenure (`[A]` Baseline `REQ-MOD1-08`).

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                   SERVICE CHANGE MANAGEMENT DATA LIFECYCLE TOPOLOGY                              │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   [ Active Employee Master Record ]                                                              │
│   (Current Single Source of Truth)                                                               │
│               │                                                                                  │
│               │ (Read Current Attributes)                                                        │
│               ▼                                                                                  │
│   [ Service Change Request ] ──► [ Level 1: HR Review ] ──► [ Level 2: Management Approval ]     │
│   (Isolated Staged Entity)                                               │                       │
│                                                                          ▼                       │
│                                                         Is Effective Date in Future?             │
│                                                         ├── YES ──► [ Staged Activation Queue ] │
│                                                         │           (Waits for Scheduled Worker) │
│                                                         │                     │                  │
│                                                         └── NO ◄──────────────┘                  │
│                                                             │                                    │
│                                                             ▼                                    │
│                                                  [ ATOMIC COMMIT PASS ]                          │
│                                                  1. Append Record to Service History Ledger      │
│                                                  2. Update Active Employee Master Record         │
│                                                  3. Trigger Real-Time Org Chart Invalidation     │
│                                                  4. Stage Record in ERP Outbox                   │
│                                                  5. Append State Diff to Audit Trail             │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 5.2 Recruitment Data vs. Employee Master Data
Module II data relates to Module I through strict, event-driven lifecycle boundaries:
1. **Candidate to Employee Transition (`[A]` `BP-XMOD-001`):**
   - Candidate applications, recruiter call records, interview scores, and LOI records remain within the recruitment domain.
   - Upon candidate LOI acceptance and completion of pre-onboarding verification milestones, an internal domain event (e.g., candidate onboarding event `[D] Proposed Detail`) triggers an atomic transaction that:
     - Instantiates a new master record in the employee master entity.
     - Allocates an organizational node in the organization hierarchy.
     - Updates the corresponding open positions tracker entry from `OFFERED` to `FILLED`.
     - Archives the candidate's verified application dossier into their newly created Digital Employee File (`[A]` Baseline `MOD1-FIL-REQ-01`).
2. **Employee Resignation to Urgent Replacement (`[A]` `BP-XMOD-002`):**
   - When a faculty or staff member's resignation is accepted by the School Dean in Module I, the system triggers the Urgent Replacement Workflow in Module II (e.g., employee resignation event `[D] Proposed Detail`).
   - This trigger initiates replacement monitoring, starts the replacement countdown clock, and pre-populates an ad-hoc MRF (`[A]` Baseline `REQ-MOD2-03`).

### 5.3 Performance Management Data vs. Employee Master Data
Module III exhibits a dual relationship with Module I:
1. **Inbound Master Data Consumption (`[A]` `BP-XMOD-003`):**
   - The three performance subsystems query Module I master employee records to drive operational eligibility:
     - *Group-D Monthly Forms:* Pulls active Group-D staff and their current departmental reporting lines on the 1st of every month (`[A]` Baseline `MOD3-GD-REQ-04`).
     - *General Staff KRA/KPI:* Consumes Date of Joining (DOJ) to trigger the 30-day goal-setting countdown and subsequent 90-day quarterly review triggers (`[A]` Baseline `MOD3-KRA-REQ-01`).
     - *Faculty ECM:* Scans monthly for faculty matching `probation_completed = TRUE` and `(current_date - last_appraisal_date) >= 12 months` (`[A]` Baseline `MOD3-FAC-REQ-01`).
2. **Outbound Appraisal Handshake into Change Management (`[A]` `BP-XMOD-004`):**
   - When an appraisal cycle is finalized by Senior Management:
     - The approved increment percentage, new salary, designation change, or promotion level is compiled into a formal payload.
     - The system executes an in-process transactional call into `ChangeManagementModule`, instantiating a formal Module I Change Request automatically without manual data re-entry (`[A]` Baseline `REQ-INT-04`, `MOD3-KRA-REQ-18`).

---

## 6. Audit Trail & Temporal Version History Architecture

### 6.1 First-Class Immutable Audit Requirement
In compliance with `REQ-MOD1-08`, `REQ-SEC-04`, and `MOD1-AUD-REQ-01` through `06`, the database architecture incorporates an append-only, tamper-evident audit ledger:
- **Non-Destructive Persistence:** Master data records are never modified without recording the modification in the audit ledger (`[A]` Baseline `REQ-MOD1-08`).
- **Actor Attribution:** Every audit record captures the acting user ID, originating IP address, action type (e.g., creation, update, approval, rejection, activation `[D] Proposed Detail`), and authoritative server timestamp (`[C] Approved Technical Decision`).
- **Immutability Principle `[B/C]`:** Audit logs are append-only. The system architecture enforces that audit records cannot be modified or deleted by standard application operations.

### 6.2 Before/After State Diffing `[C]`
For every change committed to employee master data, service conditions, evaluation scorecards, or workflow states, the audit engine records:
1. **Prior State Representation:** Structured representation of the entity state prior to the transaction (`[C] Approved Technical Decision`).
2. **Updated State Representation:** Structured representation of the entity state immediately following the transaction (`[C] Approved Technical Decision`).
3. **Modified Attributes:** Explicit list of modified attributes, allowing instant visual rendering of historical changes in the administrative UI (`[D] Proposed Detail`).

### 6.3 Historical Service Ledger
Complementing the technical audit trail, a dedicated business-level entity—**`employee_service_history`**—maintains a continuous, sequential timeline of an employee's service terms (designation, salary band, school, reporting supervisor, and rank) throughout their institutional tenure (`[A]` Baseline `MOD1-AUD-REQ-04`).

---

## 7. Effective-Date Temporal Processing Architecture

### 7.1 Temporal States of Personnel Changes
Service condition changes do not always take effect on the day of managerial approval. Academic institutions frequently approve changes in advance (e.g., annual increments effective July 1st, semester promotions effective with the new academic session).

The database architecture formally supports three temporal states (`[A]` Baseline `REQ-MOD1-07`, `BP-M1-007`):
1. **Immediate Execution:** If `effective_date <= CURRENT_DATE` upon final Level 2 approval, the change activates immediately.
2. **Approved Pending Activation:** If `effective_date > CURRENT_DATE`, the change request is held in an approved, pending-activation state.
3. **Active State:** The change has reached its effective date and has been merged into the master record.

### 7.2 Staged Activation Engine
To handle future-dated changes without blocking real-time operations:
- Future changes reside in the staging entity with indexed effective-date attributes (`[C] Approved Technical Decision`).
- **Periodic Scheduled Activation Worker `[C/D]`:** A scheduled background worker executes periodically (e.g., daily at scheduled day transition `[D] Proposed Detail`), scanning for approved records whose effective date has arrived (`SlaTimelineModule`).
- When triggered, each pending change is applied to the active employee master entity within an atomic database transaction.

### 7.3 Point-in-Time Historical Queries
The presence of effective-date attributes alongside creation timestamps and historical service ledgers allows the reporting engine to execute **point-in-time reconstruction queries** (e.g., *"What was an employee's official designation and reporting line on a specific past date?"*), fulfilling statutory accreditation and institutional audit requirements (`[A]` Baseline `REQ-MOD1-08`).

---

## 8. Reporting Requirements Impacting Data Design

The database design directly accommodates the rigorous reporting specifications established across Modules I, II, and III (`[A]` Baseline `REQ-REP-01` to `08`, `MOD1-REP-REQ-01` to `05`, `MOD2-REP-REQ-01` to `05`, `MOD3-REP-REQ-01` to `06`):

1. **Strategic Relational Indexing `[C/D]`:** High-frequency reporting dimensions (such as departmental identifiers, school identifiers, status flags, employment types, effective dates, and creation timestamps) are indexed to ensure dynamic filtering executes efficiently.
2. **Database Read Views `[C]`:** Relational database views encapsulate complex joins (such as joining candidate applications with screening records and interview panel scores), providing clean interfaces for reporting queries.
3. **Non-Blocking Query Architecture `[C/D]`:** Large analytical queries and streaming tabular exports (Excel/CSV) operate with non-blocking read-only transaction parameters (`[D] Proposed Detail`), preventing locking contention against operational transactions.

---

## 9. Data Integrity Principles & Transactional Consistency

### 9.1 Relational Integrity Rules
The following relational integrity principles govern all database specifications:
- **Foreign Key Enforcement:** Child relationships (e.g., department assignment, supervisor link, candidate application, evaluation score) enforce relational foreign keys (`[B]` Logical Implication).
- **Unique Constraints:** Natural business uniqueness is enforced at the database level (e.g., unique institutional email, unique Employee ID, unique candidate application per job requisition) (`[B]` Logical Implication).
- **Check Constraints:** Domain boundaries and valid ranges are validated via database check constraints (e.g., score ranges within valid bounds, effective dates non-null) (`[B/C]`).

### 9.2 Transactional Outbox Pattern for Asynchronous Integrations
The application integrates with external systems that lack distributed transaction support:
- Institutional ERP (`[A]` Baseline `REQ-MOD1-04`, `REQ-INT-01`)
- Multi-Channel Notification Gateways (`[A]` Baseline `SHR-NTF-REQ-01`)
- External Object Storage (`[C]` Approved Technical Decision `SHR-DOC-REQ-01`)

To guarantee data consistency without distributed two-phase commit overhead, the database architecture employs the **Transactional Outbox Pattern** (`[C] Approved Technical Decision`):
1. When a personnel change or notification trigger occurs, the business entity update AND an outbox message record are written into PostgreSQL within the **same local ACID transaction**.
2. If the transaction rolls back, no outbox event is created.
3. An asynchronous background worker continuously monitors the outbox staging entity, dispatches the payload to the external system (with retry logic and exponential backoff), and marks the outbox record as delivered upon successful acknowledgment.

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             TRANSACTIONAL OUTBOX PATTERN TOPOLOGY                                │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   [ Service Action: e.g., Finalize Salary Revision ]                                             │
│                           │                                                                      │
│                           ▼ (Single Local ACID Transaction Boundary)                             │
│   ┌──────────────────────────────────────────────────────────────────────────────────────────┐   │
│   │ 1. Update Active Employee Master Record with new salary attributes                       │   │
│   │ 2. Append historical slice to Employee Service History Ledger                            │   │
│   │ 3. Stage outbound synchronization payload in ERP Outbox Staging Entity                   │   │
│   │ 4. Stage message payload in Notification Outbox Staging Entity                           │   │
│   │ 5. Append complete state diff to Immutable Audit Trail Ledger                            │   │
│   └──────────────────────────────────────────────────────────────────────────────────────────┘   │
│                           │                                                                      │
│                           ▼ (Transaction Successfully Committed)                                 │
│   [ Background Worker / Poller ] ──► Reads pending records from ERP Outbox Staging Entity        │
│                 │                                                                                │
│                 ├──► Delivers to University ERP via configured interface                         │
│                 └──► On Success: Updates outbox staging record status to 'PROCESSED'             │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 10. High-Level Data Lifecycle Considerations

### 10.1 Universal Entity Lifecycle Stages
All major transaction entities across Modules I, II, and III transition through standardized, auditable lifecycle states (`[B]` Logical Implication):

```
[ DRAFT / INITIALIZED ]
         │
         ▼
[ SUBMITTED / PENDING REVIEW ] ◄──┐ (Clarification Loop supported)
         │                         │
         ▼                         │
[ VETTED / ENDORSED ] ─────────────┘
         │
         ▼
[ APPROVED / FINALIZED ] ───────► [ REJECTED / DISAPPROVED ]
         │                               │
         ▼                               ▼
[ STAGED / PENDING ACTIVATION ]     [ TERMINAL ARCHIVE ]
         │
         ▼
[ ACTIVE / OPERATIONAL ]
         │
         ▼
[ SUPERSEDED / HISTORICAL ARCHIVE ]
```

### 10.2 Data Retention & Historical Preservation Principle `[B/C]`
In strict compliance with statutory university governance, accreditation auditability, and the immutable audit baseline:
- **Historical Preservation Principle `[B]`:** Personnel service records, approved service condition changes, completed interview evaluation scorecards, and approved annual appraisal reports are preserved historically without destructive loss of required history (`[B]` Logical Implication from `REQ-MOD1-08`, `REQ-SEC-04`). Final statutory document retention and eventual archival/deletion schedules remain governed by official institutional policy and `REQ-TBD-11` where applicable (`[B/E]`).
- **Lifecycle State Management `[C]`:** Operational deactivation (such as employee resignations or withdrawn requisitions) is represented conceptually through explicit lifecycle states and status indicators, rather than destructive record removal (`[C] Approved Technical Decision`).

---

## 11. Explicit Scope Delimitation

To preserve the governance constraints of Phase 4:
- **No Physical Tables Created:** This document defines the conceptual database architecture and operational principles. Detailed column-by-column relational schema definitions, data types, indexes, and constraints will be formally specified in subsequent planned documents (`03-ENTITY-IDENTIFICATION.md` through `07-CONSTRAINTS-AND-RELATIONSHIPS.md`).
- **No Database Migrations or Code:** No SQL DDL/DML, Prisma schema syntax, TypeORM annotations, or backend entity code has been created or executed during this step.

---
*End of Document — Database Design Overview.*
