# Phase 4 — Database Documentation
## 03. Conceptual Entity Identification & Domain Inventory

```
====================================================================================================
STATUS:
PHASE 4 — STEP 2: CONCEPTUAL ENTITY IDENTIFICATION & DOMAIN INVENTORY
DOCUMENTATION ONLY — NO PHYSICAL DATABASE ARTIFACTS

IMPORTANT GOVERNANCE NOTICE:
This document is STRICTLY DOCUMENTATION ONLY. 
It establishes the conceptual entity inventory, functional domain ownership, business purposes, 
classifications, and requirement traceability for the University HR Change Management & Automation System.
No physical database tables, column definitions, data types, primary/foreign keys, indexes, 
SQL DDL/DML scripts, database migration files, Prisma schemas, or TypeORM entities are created herein.
All 104 atomic requirements, 59 business processes, 60 business rules, and the Technology Architecture
Baseline remain strictly frozen and authoritative.
====================================================================================================
```

---

## 1. Document Control

| Metadata Field | Specification Detail |
|---|---|
| **Document Title** | Conceptual Entity Identification & Domain Inventory |
| **Document Reference** | `docs/08-database/03-ENTITY-IDENTIFICATION.md` |
| **System Phase** | Phase 4 — Database Documentation (Step 2) |
| **Project Name** | University HR Change Management & Automation System |
| **Document Version** | `1.0.0` (Conceptual Baseline) |
| **Document Status** | `COMPLETED — CONCEPTUAL ENTITY IDENTIFICATION` |
| **Baseline Date** | September 29, 2026 |
| **Authoritative Source of Truth** | Official Project Requirements (`docs/01-requirements/`), Business Process Baseline (`docs/02-business-process/`), Functional Requirements Specifications (`docs/03-functional-requirements/`), System Architecture Baseline (`docs/07-system-architecture/` & `TECHNOLOGY_ARCHITECTURE_BASELINE.md`), and Foundation Documents ([`00-DATABASE-DOCUMENTATION-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/00-DATABASE-DOCUMENTATION-INDEX.md), [`01-DATABASE-DESIGN-OVERVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md), [`02-DATA-MODEL-OVERVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/02-DATA-MODEL-OVERVIEW.md)) |
| **Scope of Document** | Formal identification, domain ownership mapping, business justification, conceptual classification, and backward traceability of all 33 primary conceptual entities across Module I, Module II, Module III, and Shared Platform Services |

---

## 2. Purpose of Conceptual Entity Identification

The purpose of this document is to establish the authoritative, comprehensive inventory of **conceptual data entities** required by the approved requirements, business processes, and functional specifications of the University HR Change Management & Automation System.

Entity identification bridges the gap between functional specifications and relational database modeling by:
1. **Cataloguing What Exists:** Identifying every distinct business object, document, transaction record, evaluation scorecard, and audit ledger that requires state persistence.
2. **Establishing Domain Ownership:** Assigning clear, unambiguous ownership of each conceptual entity to its originating functional module within the Modular Monolith application architecture.
3. **Providing Source Grounding:** Justifying the existence of every entity through backward traceability to frozen requirement IDs (`REQ-*`), business processes (`BP-*`), business rules (`BR-*`), and functional requirements (`MOD*-REQ-*`).
4. **Classifying Data Roles:** Categorizing entities across standard architectural data roles (Master, Transactional, Workflow, Evaluation, Configuration, Audit, Document Metadata, Communication, Derived, and Integration Data).
5. **Preventing Premature Implementation:** Establishing conceptual entity boundaries without premature decisions regarding physical table counts, normalization levels, column types, primary/foreign keys, or storage engines.

---

## 3. Entity Identification Principles

The conceptual entity inventory is governed by the following core principles:

1. **Source-Grounded Identification:**  
   An entity is recognized if and only if it is explicitly mandated by the official requirements baseline or is mathematically and architecturally necessary to satisfy a frozen business process or rule. No entities are invented based on generic commercial HR software assumptions.
2. **Conceptual vs. Physical Entity Distinction:**  
   Conceptual entities represent real-world business domains and information models. They do not dictate a 1-to-1 correspondence with physical PostgreSQL tables. Normalization, denormalization, junction tables, and partitioning are physical design concerns addressed in subsequent documentation phases.
   > **Analytical Scope Declaration:**  
   > The identified conceptual entity count is an analytical data-domain inventory and does not represent the final number of physical PostgreSQL tables.
3. **Domain Ownership Boundaries:**  
   Each conceptual entity has a defined logical domain owner or shared-platform ownership boundary. Cross-domain interaction does not imply physical database ownership or physical schema separation. In alignment with the approved Modular Monolith architecture, logical domain boundaries govern conceptual data stewardship, and cross-domain collaboration occurs through defined application interfaces and domain events without raw cross-domain writes.
4. **Master vs. Transactional vs. Supporting Entities:**  
   A strict architectural distinction is maintained between:
   - *Master Data:* Long-lived, authoritative core records representing university entities (e.g., active employees, organizational nodes).
   - *Transactional Data:* Point-in-time requests, applications, and decisions that progress through lifecycles (e.g., change requests, job requisitions, candidate applications).
   - *Supporting / Operational Data:* Evaluation scorecards, workflow transition logs, timers, document metadata, audit logs, and integration staging buffers.
5. **Requirement & Process Traceability:**  
   Every conceptual entity possesses bidirectional traceability to the upstream documentation baseline. If an entity cannot be traced to an approved requirement or process, it cannot exist in this inventory.
6. **No Premature Physical Schema Decisions:**  
   This document does not specify PostgreSQL schema names, column types, keys, constraints, indexes, or storage parameters. It defines business entities and conceptual boundaries only.
7. **TBD Preservation:**  
   Where specific entity attributes, calculation algorithms, or policy boundaries remain unresolved in the upstream baseline, they are tagged as `[E] TBD / Open Decision` and mapped to the official project TBD register ([`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md)). No TBD is silently resolved or assumed.

---

## 4. Entity Classification Taxonomy

To provide architectural clarity, all 33 conceptual entities are classified using a controlled taxonomy grounded in the source documentation:

| Classification | Definition | Architectural Characteristics | Typical Lifespan |
|---|---|---|---|
| **Master Data** | Core institutional business entities that provide context across all university operations. | High read frequency; low update frequency; strict referential anchoring; central single source of truth. | Active throughout institutional tenure; retention duration is governed by official institutional policy and the applicable unresolved retention requirements under REQ-TBD-11. |
| **Transactional Data** | Discrete operational requests, requisitions, or applications that move through business lifecycles. | Finite state progression; state-driven mutability; strict validation gates; event generation upon completion. | Active during lifecycle; archival and retention governed by institutional policy and REQ-TBD-11. |
| **Workflow / Process Data** | State machine tracking records, approval logs, and transition signatures. | Append-only; actor-attributed; chronological sequencing; state transition validation. | Retained for institutional governance; retention duration governed by REQ-TBD-11. |
| **Reference / Configuration Data** | Reusable templates, rubrics, organizational schemas, and access control rules. | Configurable by authorized administrative actors; versioned; semi-structured or parametric. | Active per academic/operational version; prior versions retained per institutional governance. |
| **Evaluation / Assessment Data** | Quantitative scorecards, qualitative feedback, review dossiers, and committee outcome matrices. | Strict evaluation window; locked/tamper-evident once submitted; multi-party scoring inputs. | Retained in employee/applicant dossier; retention duration is governed by official institutional policy and the applicable unresolved retention requirements under REQ-TBD-11. |
| **Audit / History Data** | Append-only chronological ledgers of historical personnel states, transaction diffs, and security events. | Non-destructive; immutable; tamper-evident; point-in-time reconstructible; actor-attributed. | Retention duration is governed by official institutional policy and the applicable unresolved retention requirements under REQ-TBD-11. |
| **Document / Attachment Metadata** | Pointers, hashes, MIME types, and descriptive metadata for binary objects stored externally. | Abstracted metadata referencing external storage; tamper-evident once verified; cryptographic verification. | Tied to referencing entity lifecycle; retention duration governed by REQ-TBD-11. |
| **Notification / Communication Data** | Outbound messages, template references, dispatch queues, and transmission logs. | Transient staging progressing to historical dispatch logging; asynchronous delivery tracking. | Operational retention duration is governed by institutional communication policy and REQ-TBD-10/REQ-TBD-11. |
| **Reporting / Derived Data** | Aggregated operational ledgers, composite tracking views, and headcount monitoring entities. | Real-time operational synthesis across transactional entities; dynamic status reflection. | Synchronized with active transactions. |
| **Integration / Supporting Data** | Staging queues and outbox buffers guaranteeing reliable external synchronization. | Local transactional boundaries; transactional outbox pattern; asynchronous poller consumption. | Transient operational state; processed status retained for reconciliation per REQ-TBD-01. |

---

## 5. Module I — Change Management Entities

Module I governs the Central Employee Database, Dynamic Organization Hierarchy, Digital Personal Dossiers, and Service Condition Change Management. It encapsulates **six (6) conceptual entities**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             MODULE I: CONCEPTUAL ENTITY INVENTORY                                │
├──────────────┬────────────────────────────────────────────┬──────────────────────────────────────┤
│ ENTITY ID    │ CONCEPTUAL ENTITY NAME                     │ CONCEPTUAL CLASSIFICATION            │
├──────────────┼────────────────────────────────────────────┼──────────────────────────────────────┤
│ ENT-MOD1-01  │ Employee Master Record                     │ Master Data                          │
│ ENT-MOD1-02  │ Organization Hierarchy Node                │ Master Data                          │
│ ENT-MOD1-03  │ Digital Employee File & Dossier Item       │ Document / Attachment Metadata       │
│ ENT-MOD1-04  │ Service Condition Change Request           │ Transactional Data                   │
│ ENT-MOD1-05  │ Service Change Approval Action             │ Workflow / Process Data              │
│ ENT-MOD1-06  │ Employee Service History Ledger            │ Audit / History Data                 │
└──────────────┴────────────────────────────────────────────┴──────────────────────────────────────┘
```

### 5.1 ENT-MOD1-01: Employee Master Record
- **Conceptual Classification:** Master Data
- **Domain Owner:** Module I (`EmployeeCoreModule`)
- **Purpose:** Serves as the authoritative, institutional Single Source of Truth for all active faculty, administrative staff, and technical personnel across the university.
- **Business Description:** Stores core profile, identification, organizational placement, official designation, rank/band, supervisory reporting line, Date of Joining (DOJ), probation clearance status, and current operational status. Reflects exclusively currently active service conditions; pending or scheduled changes never directly mutate this record.
- **Requirement Traceability:** `REQ-MOD1-01`, `REQ-MOD1-02`, `REQ-MOD1-04`, `REQ-MOD1-05`, `REQ-MOD1-07`, `REQ-MOD1-08`.
- **Business Process Traceability:** `BP-M1-001`, `BP-M1-004`, `BP-M1-007`, `BP-M1-011`, `BP-XMOD-001`, `BP-XMOD-003`.
- **Functional Requirement Traceability:** `MOD1-CDB-REQ-01` to `05`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Operational deactivation (resignation, retirement) is represented through lifecycle states without destructive loss of required history (`REQ-MOD1-08`). Final document retention and archival/deletion schedules remain governed by official institutional policy and statutory retention rules under `REQ-TBD-11` where applicable (`[B/E]`).

### 5.2 ENT-MOD1-02: Organization Hierarchy Node
- **Conceptual Classification:** Master Data
- **Domain Owner:** Module I (`OrgHierarchyModule`)
- **Purpose:** Models the university's institutional organizational structure, departmental trees, and reporting lines.
- **Business Description:** Represents positions, schools, departments, and supervisory reporting relationships. Powers dynamic organizational chart rendering and provides the topological reporting structure consumed by workflow engines for routing approvals to HODs, Deans, and Executive Leadership.
- **Requirement Traceability:** `REQ-MOD1-02`, `REQ-MOD1-06`, `REQ-SHR-04`.
- **Business Process Traceability:** `BP-M1-002`, `BP-M1-010`.
- **Functional Requirement Traceability:** `MOD1-ORG-REQ-01` to `04`, `SHR-ORG-REQ-01` to `03`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Maintained 1-to-1 with active employee assignments. Realigned in real-time upon approved service condition change requests affecting supervisor, designation, or department transfer.

### 5.3 ENT-MOD1-03: Digital Employee File & Dossier Item
- **Conceptual Classification:** Document / Attachment Metadata
- **Domain Owner:** Module I (`EmployeeFileModule`)
- **Purpose:** Provides a centralized institutional digital dossier archiving historical personnel documents, verified credentials, and institutional notices.
- **Business Description:** Consolidated personal folder tracking verified joining credentials, signed Letters of Intent, degree certificates, promotion orders, increment notices, disciplinary records, and annual evaluation scorecards.
- **Requirement Traceability:** `REQ-MOD1-03`.
- **Business Process Traceability:** `BP-M1-003`, `BP-XMOD-001`, `BP-XMOD-004`.
- **Functional Requirement Traceability:** `MOD1-FIL-REQ-01` to `04`, `SHR-FIL-REQ-01` to `03`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Ingestion occurs across employee tenure. Physical documents reside in external durable document storage; this entity manages the institutional dossier index and metadata.

### 5.4 ENT-MOD1-04: Service Condition Change Request (Polymorphic)
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module I (`ChangeManagementModule`)
- **Purpose:** Encapsulates proposed service modifications across 10 standardized categories in an isolated staging container.
- **Business Description:** Container holding proposed changes across ten official categories: (1) Salary Change, (2) Designation Change, (3) Reportee Change, (4) Reporting Authority Change, (5) Level Change, (6) Department/School Change, (7) Location Change, (8) Additional Responsibility, (9) Qualification Change, (10) Other Service Condition. Completely isolates pending changes from master records during review.
- **Requirement Traceability:** `REQ-MOD1-05`, `REQ-MOD1-06`, `REQ-MOD1-07`.
- **Business Process Traceability:** `BP-M1-004`, `BP-M1-005`, `BP-M1-006`, `BP-M1-007`.
- **Functional Requirement Traceability:** `MOD1-CHG-REQ-01` to `12`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Initiated by HR Operations under official baseline `REQ-MOD1-05`. (Note: Extending initiation to administrative/departmental officers is a pending governance item under reference `CONF-01`). Supports effective-date scheduling: applies immediately if effective date has arrived, or stages in an approved pending-activation state until scheduled activation.

### 5.5 ENT-MOD1-05: Service Change Approval Action
- **Conceptual Classification:** Workflow / Process Data
- **Domain Owner:** Module I (`ChangeApprovalModule`)
- **Purpose:** Records individual review, endorsement, clarification, or rejection actions within the 2-level approval hierarchy.
- **Business Description:** Captures formal sign-offs across `Level 1: HR Review` and `Level 2: Senior Management Approval`. Stores acting authority ID, action timestamp, decision outcome (such as approved, rejected, or clarification requested), and mandatory written justification comments.
- **Requirement Traceability:** `REQ-MOD1-06`.
- **Business Process Traceability:** `BP-M1-005`, `BP-M1-006`.
- **Functional Requirement Traceability:** `MOD1-APP-REQ-01` to `06`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Append-only workflow log. Once submitted, an approval action cannot be edited, overwritten, or deleted.

### 5.6 ENT-MOD1-06: Employee Service History Ledger
- **Conceptual Classification:** Audit / History Data
- **Domain Owner:** Module I (`EmployeeCoreModule`)
- **Purpose:** Maintains a sequential historical timeline of all activated service conditions across an employee's institutional tenure.
- **Business Description:** Records bounded historical service slices capturing the designation, salary, pay band, school, department, reporting supervisor, and rank that were active during specific historical intervals.
- **Requirement Traceability:** `REQ-MOD1-08`.
- **Business Process Traceability:** `BP-M1-007`, `BP-M1-008`.
- **Functional Requirement Traceability:** `MOD1-AUD-REQ-04`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Append-only ledger updated automatically upon activation of an approved change request. Powers point-in-time reconstruction queries for accreditation, statutory audits, and service book verification.

---

## 6. Module II — Recruitment & Selection Entities

Module II governs Academic and Non-Academic Manpower Planning, Requisitions (MRF), Sourcing, CV Processing, Selection Committees, Multi-Round Interviews, and Pre-Onboarding. It encapsulates **ten (10) conceptual entities**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            MODULE II: CONCEPTUAL ENTITY INVENTORY                                │
├──────────────┬────────────────────────────────────────────┬──────────────────────────────────────┤
│ ENTITY ID    │ CONCEPTUAL ENTITY NAME                     │ CONCEPTUAL CLASSIFICATION            │
├──────────────┼────────────────────────────────────────────┼──────────────────────────────────────┤
│ ENT-MOD2-01  │ Academic Manpower Plan & Workload Req.     │ Transactional Data                   │
│ ENT-MOD2-02  │ Non-Academic Manpower Plan                 │ Transactional Data                   │
│ ENT-MOD2-03  │ Manpower Requisition Form (MRF)            │ Transactional Data                   │
│ ENT-MOD2-04  │ Open Positions Tracker Entry               │ Reporting / Derived Data             │
│ ENT-MOD2-05  │ Candidate Profile & Application Record     │ Transactional Data                   │
│ ENT-MOD2-06  │ Recruiter Calling Record (RCS)             │ Evaluation / Assessment Data         │
│ ENT-MOD2-07  │ Academic SCM Session & Score Record        │ Evaluation / Assessment Data         │
│ ENT-MOD2-08  │ Non-Academic Interview Round & Score Rec.  │ Evaluation / Assessment Data         │
│ ENT-MOD2-09  │ Letter of Intent (LOI) & Pre-Onboarding    │ Transactional Data                   │
│ ENT-MOD2-10  │ Urgent Replacement Tracker                 │ Transactional Data                   │
└──────────────┴────────────────────────────────────────────┴──────────────────────────────────────┘
```

### 6.1 ENT-MOD2-01: Academic Manpower Plan & Workload Requisition
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module II (`AcademicRecruitmentModule`)
- **Purpose:** Encapsulates semester faculty requisition proposals based on curriculum teaching load assessments.
- **Business Description:** Represents the 4-month semester planning cycle for teaching faculty. Holds Dean's requirement submissions, teaching load distribution (**Attachment 1**), HR vetting findings, and Pro-Chancellor approval.
- **Requirement Traceability:** `REQ-MOD2-02`, `REQ-MOD2-04`, `REQ-MOD2-05`, `REQ-MOD2-06`.
- **Business Process Traceability:** `BP-M2-ACAD-001` to `006`.
- **Functional Requirement Traceability:** `MOD2-MP-FAC-REQ-01` to `08`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Submitted by Dean of School; vetted by HR Department; approved by Hon'ble Pro-Chancellor (7-day SLA). (Note: Introducing an Associate Dean formal vetting step is a pending governance item under reference `CONF-02` / `CONF-03` / `CFL-01`).

### 6.2 ENT-MOD2-02: Non-Academic Manpower Plan
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module II (`NonAcademicRecruitmentModule`)
- **Purpose:** Governs annual staffing requisitions for administrative, technical, and operational cadres.
- **Business Description:** Annual departmental staffing requisition. Holds HOD submissions, justification narratives, HR consolidation findings, and Pro-Chancellor approval. Enforces the strict rule of **maximum 1 planned requisition per department per year**.
- **Requirement Traceability:** `REQ-MOD2-07`, `REQ-MOD2-08`, `REQ-MOD2-09`, `REQ-MOD2-10`.
- **Business Process Traceability:** `BP-M2-NACAD-001` to `005`.
- **Functional Requirement Traceability:** `MOD2-MP-NF-REQ-01` to `07`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Covers technical and operational staff, including Lab Technicians under baseline `REQ-MOD2-01`. (Note: Grouping Lab Technicians under Academic SCM is a pending governance item under reference `CONF-04` / `CFL-02`).

### 6.3 ENT-MOD2-03: Manpower Requisition Form (MRF)
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module II (`RecruitmentCoreModule`)
- **Purpose:** Formal operational requisition authorizing job advertisement, sourcing, and candidate selection.
- **Business Description:** Authorizes recruitment operations. Categorized as either **Planned MRF** (originating from approved semester/annual plans) or **Urgent Replacement MRF** (originating from an accepted resignation). Authorizes public job publication within 7 days.
- **Requirement Traceability:** `REQ-MOD2-03`, `REQ-MOD2-06`, `REQ-MOD2-10`.
- **Business Process Traceability:** `BP-M2-ACAD-006`, `BP-M2-NACAD-005`.
- **Functional Requirement Traceability:** `MOD2-MRF-REQ-01` to `07`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Automatically links to downstream candidate sourcing pipelines and generates an Open Positions Tracker entry.

### 6.4 ENT-MOD2-04: Open Positions Tracker Entry
- **Conceptual Classification:** Reporting / Derived Data
- **Domain Owner:** Module II (`RecruitmentTrackingModule`)
- **Purpose:** Authoritative operational ledger tracking all active vacancies, headcount progress, and sourcing funnels.
- **Business Description:** University **Attachment 3** position tracker. Instantiated automatically within 30 days of MRF approval. Provides real-time visibility into hiring progress across all academic and administrative units.
- **Requirement Traceability:** `REQ-MOD2-11`.
- **Business Process Traceability:** `BP-M2-ACAD-006`, `BP-M2-TRK-001`.
- **Functional Requirement Traceability:** `MOD2-POS-REQ-01` to `05`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Transitions through: Open → Sourcing → Interviewing → Offered → Filled (upon candidate LOI acceptance) or Cancelled.

### 6.5 ENT-MOD2-05: Candidate Profile & Application Record
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module II (`CandidateSourcingModule`)
- **Purpose:** Centralized applicant repository capturing multi-channel candidate applications and screening outcomes.
- **Business Description:** Stores applicant profiles ingested from university portal, email, referrals, and external job portals. Manages candidate deduplication, parsed qualification attributes, UGC compliance eligibility flags, and overall screening status.
- **Requirement Traceability:** `REQ-MOD2-12`, `REQ-MOD2-13`, `REQ-MOD2-19`.
- **Business Process Traceability:** `BP-M2-TRK-001`, `BP-M2-ACAD-007`.
- **Functional Requirement Traceability:** `MOD2-SRC-REQ-01` to `06`, `MOD2-SCR-REQ-01` to `05`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Conceptually linked to candidate resumes in external document storage via document metadata.

### 6.6 ENT-MOD2-06: Recruiter Calling Record (RCS)
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module II (`CandidateScreeningModule`)
- **Purpose:** Captures telephonic screening feedback and preliminary candidate verification.
- **Business Description:** Standardized Recruiter Calling Sheet form capturing current CTC, expected CTC, notice period, location willingness, communication evaluation, and recruiter recommendations. Routes candidate dossiers to HOD and HR review for interview shortlisting.
- **Requirement Traceability:** `REQ-MOD2-12`.
- **Business Process Traceability:** `BP-M2-ACAD-007`, `BP-M2-ACAD-008`.
- **Functional Requirement Traceability:** `MOD2-RCS-REQ-01` to `06`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Informs departmental shortlisting. (Note: Introducing an executive pre-interview management approval gate is a pending governance item under reference `CONF-05` / `CFL-03`).

### 6.7 ENT-MOD2-07: Academic Selection Committee (SCM) Session & Score Record
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module II (`AcademicSelectionModule`)
- **Purpose:** Manages statutory Selection Committee Meetings (SCM) for faculty recruitment and aggregates panel evaluation scores.
- **Business Description:** Represents the statutory academic evaluation panel. Manages secure digital access tokens for External Subject Experts. Captures individual evaluator marks across subject knowledge, pedagogy, research, and communication. Auto-compiles the composite Evaluation Matrix for Management final cost approval.
- **Requirement Traceability:** `REQ-MOD2-14`.
- **Business Process Traceability:** `BP-M2-ACAD-009`, `BP-M2-ACAD-010`.
- **Functional Requirement Traceability:** `MOD2-SCM-REQ-01` to `06`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Evaluation matrix is submitted directly to Senior Management for final cost approval under official baseline `REQ-MOD2-14`. (Note: Introducing an intermediate post-SCM HR recommendation checkpoint is a pending governance item under reference `CONF-06`). Individual scorecards submitted by panelists are locked and tamper-evident once submitted.

### 6.8 ENT-MOD2-08: Non-Academic Interview Round & Evaluation Score Record
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module II (`NonAcademicSelectionModule`)
- **Purpose:** Enforces 3-round sequential evaluations and score capture for non-faculty candidates.
- **Business Description:** Enforces strict sequential progression: Round 1 (Technical Interview — HOD/Technical Panel) → Round 2 (HR Interview — Head HR) → Round 3 (Management Interview — Senior Leadership). Captures scores for Job Knowledge, Communication, and Attitude.
- **Requirement Traceability:** `REQ-MOD2-15`.
- **Business Process Traceability:** `BP-M2-NACAD-006`, `BP-M2-NACAD-007`.
- **Functional Requirement Traceability:** `MOD2-INT-REQ-01` to `06`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Candidate must pass a round before advancing to the subsequent round.

### 6.9 ENT-MOD2-09: Letter of Intent (LOI) & Pre-Onboarding ("Yet to Join") Record
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module II (`OfferOnboardingModule`)
- **Purpose:** Governs formal offer generation, candidate acceptance, and pre-onboarding tracking.
- **Business Description:** Auto-generates Letter of Intent PDF upon Management cost approval. Upon candidate acceptance, flags candidate as "Yet to Join" and triggers pre-onboarding notifications to Deans, HODs, Admin, and IT teams. On Day 1, triggers atomic instantiation of Employee Master Record in Module I.
- **Requirement Traceability:** `REQ-MOD2-16`, `REQ-MOD2-17`, `REQ-MOD2-18`.
- **Business Process Traceability:** `BP-M2-ACAD-011`, `BP-M2-ACAD-012`, `BP-M2-NACAD-008`, `BP-XMOD-001`.
- **Functional Requirement Traceability:** `MOD2-YTJ-REQ-01` to `07`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Contractual boundary regarding whether LOI is the sole pre-joining instrument or if a distinct formal Appointment Letter is issued is an open policy item under `REQ-TBD-08`.

### 6.10 ENT-MOD2-10: Urgent Replacement Tracker
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module II (`UrgentRecruitmentModule`)
- **Purpose:** Monitors urgent faculty or staff replacement workflows triggered by accepted employee resignations.
- **Business Description:** Triggered by accepted resignation in Module I. Starts replacement countdown clock, routes fast-track ad-hoc MRF to HR and Pro-Chancellor, and monitors hiring progress against resignation notice period.
- **Requirement Traceability:** `REQ-MOD2-03`.
- **Business Process Traceability:** `BP-M2-URG-001`, `BP-XMOD-002`.
- **Functional Requirement Traceability:** `MOD2-URG-REQ-01` to `06`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Directly bridges Module I resignation events (`BP-XMOD-002`) into Module II recruitment workflows.

---

## 7. Module III — Performance Management Entities

Module III preserves **three completely independent performance management subsystems**. It encapsulates **nine (9) conceptual entities**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            MODULE III: CONCEPTUAL ENTITY INVENTORY                               │
├──────────────┬────────────────────────────────────────────┬──────────────────────────────────────┤
│ ENTITY ID    │ CONCEPTUAL ENTITY NAME                     │ CONCEPTUAL CLASSIFICATION            │
├──────────────┼────────────────────────────────────────────┼──────────────────────────────────────┤
│ ENT-MOD3-01  │ Group-D Evaluation Form Template           │ Reference / Configuration Data       │
│ ENT-MOD3-02  │ Group-D Monthly Evaluation Instance        │ Evaluation / Assessment Data         │
│ ENT-MOD3-03  │ Group-D Annual Collation Report            │ Evaluation / Assessment Data         │
│ ENT-MOD3-04  │ General Staff KRA/KPI Goal Setting Record  │ Evaluation / Assessment Data         │
│ ENT-MOD3-05  │ General Staff Quarterly Review Record      │ Evaluation / Assessment Data         │
│ ENT-MOD3-06  │ General Staff Annual Appraisal Outcome     │ Evaluation / Assessment Data         │
│ ENT-MOD3-07  │ Faculty Appraisal Eligibility Batch        │ Transactional Data                   │
│ ENT-MOD3-08  │ Faculty Self-Appraisal Dossier & Verif.    │ Evaluation / Assessment Data         │
│ ENT-MOD3-09  │ Faculty ECM Session & TNU Protocol Matrix  │ Evaluation / Assessment Data         │
└──────────────┴────────────────────────────────────────────┴──────────────────────────────────────┘
```

### 7.1 Subsystem 1: Group-D / Band I Monthly & Annual Appraisal

#### 7.1.1 ENT-MOD3-01: Group-D Evaluation Form Template
- **Conceptual Classification:** Reference / Configuration Data
- **Domain Owner:** Module III (`GroupDPerformanceModule`)
- **Purpose:** Master repository of role-specific KPI templates for Group-D service roles.
- **Business Description:** University **Enclosure 1** standardized templates. Configurable by HR to capture role-specific competencies (work quality, attendance, discipline) per designation (peons, drivers, security personnel, sweepers).
- **Requirement Traceability:** `REQ-MOD3-01`, `REQ-MOD3-03`.
- **Business Process Traceability:** `BP-M3-GD-001`.
- **Functional Requirement Traceability:** `MOD3-GD-REQ-01` to `03`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Utilizes semi-structured template configuration (`[C] Approved Technical Decision`). Instantiates monthly evaluation forms across active Group-D personnel.

#### 7.1.2 ENT-MOD3-02: Group-D Monthly Evaluation Instance
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module III (`GroupDPerformanceModule`)
- **Purpose:** Monthly evaluation form completed for each Group-D employee.
- **Business Description:** Dispatched on the 1st of every month. Strict submission due date on the 7th; 3-day grace period to the 10th. Auto-locked at 23:59 on the 10th by automated timeline worker if unsubmitted, transitioning to an unsubmitted evaluation state. Requires formal digital sign-off from VP-Administration.
- **Requirement Traceability:** `REQ-MOD3-01`, `REQ-MOD3-02`, `REQ-MOD3-04`, `REQ-MOD3-05`.
- **Business Process Traceability:** `BP-M3-GD-002`, `BP-M3-GD-003`, `BP-M3-GD-004`, `BP-M3-GD-005`.
- **Functional Requirement Traceability:** `MOD3-GD-REQ-04` to `13`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Evaluated by immediate supervisor with HOD endorsement under baseline `REQ-MOD3-01` / `BP-M3-GD-002`. (Note: Direct exclusive online completion by HODs is a pending governance item under reference `CONF-07` / `CFL-04`).

#### 7.1.3 ENT-MOD3-03: Group-D Annual Collation Report
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module III (`GroupDPerformanceModule`)
- **Purpose:** 12-month performance aggregation and compensation revision review for Group-D personnel.
- **Business Description:** Auto-triggered on the 1-year anniversary of Date of Joining (DOJ). Aggregates 12 monthly evaluation reports, computes parameter-weighted average scores, verifies mandatory probation clearance, and records Management compensation slab decisions.
- **Requirement Traceability:** `REQ-MOD3-06`, `REQ-MOD3-07`, `REQ-MOD3-08`.
- **Business Process Traceability:** `BP-M3-GD-006`, `BP-M3-GD-007`, `BP-M3-GD-008`.
- **Functional Requirement Traceability:** `MOD3-GD-REQ-14` to `21`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Aggregates 12 monthly evaluation instances. Specific compensation brackets remain an open policy decision under `REQ-TBD-05`.

---

### 7.2 Subsystem 2: General Staff KRA/KPI Lifecycle

#### 7.2.1 ENT-MOD3-04: General Staff KRA/KPI Goal Setting Record
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module III (`StaffPerformanceModule`)
- **Purpose:** Captures and locks performance goals for new staff joiners within 30 days of Date of Joining (DOJ).
- **Business Description:** Collaborative goal setting between employee and Reporting Authority within strict 30-day countdown from DOJ. Verified by HR and formally locked by Senior Management.
- **Requirement Traceability:** `REQ-MOD3-09`.
- **Business Process Traceability:** `BP-M3-KRA-001`.
- **Functional Requirement Traceability:** `MOD3-KRA-REQ-01` to `04`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Anchors the subsequent quarterly review cycles across Q1–Q4.

#### 7.2.2 ENT-MOD3-05: General Staff Quarterly Review Record (Q1–Q4)
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module III (`StaffPerformanceModule`)
- **Purpose:** Quarterly review against approved KRAs/KPIs across Q1, Q2, Q3, and Q4.
- **Business Description:** 90-day review cadence; automated submission reminders; 15-day employee self-assessment with uploaded evidence; 7-day supervisor verification; HR observation; Management comments.
- **Requirement Traceability:** `REQ-MOD3-10`, `REQ-MOD3-11`, `REQ-MOD3-12`.
- **Business Process Traceability:** `BP-M3-KRA-002`, `BP-M3-KRA-003`, `BP-M3-KRA-004`.
- **Functional Requirement Traceability:** `MOD3-KRA-REQ-05` to `14`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Governed by 90-day cadence. (Note: Exact temporal formula clarification is under pending reference `CONF-08`).

#### 7.2.3 ENT-MOD3-06: General Staff Annual Appraisal Outcome
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module III (`StaffPerformanceModule`)
- **Purpose:** Final annual appraisal decision and automatic Module I handshake.
- **Business Description:** Triggered upon completion of Q4. Senior Management reviews the full annual performance portfolio and approves increment, designation change, or promotion. System automatically initializes a Module I Change Request without manual re-entry (`BP-XMOD-004`).
- **Requirement Traceability:** `REQ-MOD3-13`, `REQ-INT-04`.
- **Business Process Traceability:** `BP-M3-KRA-005`, `BP-XMOD-004`.
- **Functional Requirement Traceability:** `MOD3-KRA-REQ-15` to `18`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Directly instantiates a Service Condition Change Request in Module I upon final sign-off.

---

### 7.3 Subsystem 3: Faculty Annual Performance Appraisal (ECM Route)

#### 7.3.1 ENT-MOD3-07: Faculty Annual Appraisal Eligibility Batch
- **Conceptual Classification:** Transactional Data
- **Domain Owner:** Module III (`FacultyAppraisalModule`)
- **Purpose:** Monthly batch scanner identifying eligible faculty for annual Evaluation Committee Meeting (ECM) review.
- **Business Description:** Runs on the 10th of every month. Scans database for faculty matching: `probation_completed = TRUE` and `(current_date - last_appraisal_date) >= 12 months`. Routes eligible roster to Office of the Registrar.
- **Requirement Traceability:** `REQ-MOD3-14`, `REQ-MOD3-15`.
- **Business Process Traceability:** `BP-M3-FAC-001`, `BP-M3-FAC-002`.
- **Functional Requirement Traceability:** `MOD3-FAC-REQ-01` to `05`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Confirmed by Registrar before self-appraisal forms are auto-dispatched.

#### 7.3.2 ENT-MOD3-08: Faculty Self-Appraisal Dossier & Multi-Unit Verification Record
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module III (`FacultyAppraisalModule`)
- **Purpose:** Captures self-appraisal submissions, evidence, and parallel multi-departmental verifications.
- **Business Description:** 7 working days submission deadline with daily reminders. Routes in parallel to exactly 4 verification units: School Dean (academic), R&D Cell (research), Placement Cell (industry linkage), HR Department (compliance). Handles discrepancy flagging and resubmission tracking.
- **Requirement Traceability:** `REQ-MOD3-16`, `REQ-MOD3-17`.
- **Business Process Traceability:** `BP-M3-FAC-003`, `BP-M3-FAC-004`, `BP-M3-FAC-005`.
- **Functional Requirement Traceability:** `MOD3-FAC-REQ-06` to `13`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Operates strictly across the 4 approved verification units under baseline `REQ-MOD3-17`. (Note: Configurable dynamic routing for additional stakeholders is a pending governance item under reference `CONF-09`).

#### 7.3.3 ENT-MOD3-09: Faculty ECM Session & TNU Protocol Evaluation Matrix Record
- **Conceptual Classification:** Evaluation / Assessment Data
- **Domain Owner:** Module III (`FacultyAppraisalModule`)
- **Purpose:** Committee meeting evaluations, TNU Protocol Matrix synthesis, and compensation decisions.
- **Business Description:** Scheduled by Registrar. Evaluation Committee Meeting (ECM) members enter digital score sheets during session. System synthesizes scores, past increment history, and TNU Protocol parameters into the composite Evaluation Matrix. Senior Management records final compensation decision (annual increment, accelerated increment, promotion). System auto-generates outcome letters and triggers Module I handshake.
- **Requirement Traceability:** `REQ-MOD3-18`, `REQ-MOD3-19`, `REQ-MOD3-20`, `REQ-INT-04`.
- **Business Process Traceability:** `BP-M3-FAC-006`, `BP-M3-FAC-007`, `BP-M3-FAC-008`, `BP-XMOD-004`.
- **Functional Requirement Traceability:** `MOD3-FAC-REQ-14` to `22`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Governed by the 3 baseline outcomes: annual increment, accelerated increment, promotion (`REQ-MOD3-19`). (Note: Expanding formal outcomes to include PIP, Reprimand, and Probation Extension is a pending governance item under reference `CONF-10`). Mathematical weights across categories remain an open decision under `REQ-TBD-04`.

---

## 8. Shared Platform Entities

Shared platform entities provide cross-cutting capabilities across all modules. It encapsulates **eight (8) conceptual entities**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            SHARED PLATFORM CONCEPTUAL ENTITY INVENTORY                           │
├──────────────┬────────────────────────────────────────────┬──────────────────────────────────────┤
│ ENTITY ID    │ CONCEPTUAL ENTITY NAME                     │ CONCEPTUAL CLASSIFICATION            │
├──────────────┼────────────────────────────────────────────┼──────────────────────────────────────┤
│ ENT-SHR-01   │ User Account & Credential Profile          │ Integration / Supporting Data        │
│ ENT-SHR-02   │ Role & Permission Assignment               │ Reference / Configuration Data       │
│ ENT-SHR-03   │ Workflow State Instance & Transition Log   │ Workflow / Process Data              │
│ ENT-SHR-04   │ SLA & Deadline Timer Record                │ Workflow / Process Data              │
│ ENT-SHR-05   │ Document Metadata & Binary Reference       │ Document / Attachment Metadata       │
│ ENT-SHR-06   │ Notification Queue & Dispatch Record       │ Notification / Communication Data    │
│ ENT-SHR-07   │ Immutable Audit Trail Entry                │ Audit / History Data                 │
│ ENT-SHR-08   │ ERP Transactional Outbox Staging Record    │ Integration / Supporting Data        │
└──────────────┴────────────────────────────────────────────┴──────────────────────────────────────┘
```

### 8.1 ENT-SHR-01: User Account & Authentication Credential Profile
- **Conceptual Classification:** Integration / Supporting Data
- **Owning/Shared Domain:** Shared Platform (`AuthIdentityModule`)
- **Purpose:** Manages authentication credentials, user identity profiles, sessions, and security policies.
- **Business Description:** Stores user identity credentials, security state, session validity, and time-limited access tokens for external statutory SCM committee experts.
- **Requirement Traceability:** `REQ-SEC-01`, `REQ-SEC-02`, `REQ-MOD2-14`.
- **Functional Traceability:** `SHR-AUT-REQ-01` to `04`.
- **Source Classification:** `[B] Logical Implication`.
- **Notes / Boundary:** Conceptually links to Employee Master Record (for university staff) or external guest profile (for external SCM experts). Enterprise SSO integration remains an open decision under `REQ-TBD-07`.

### 8.2 ENT-SHR-02: Role & Permission Assignment
- **Conceptual Classification:** Reference / Configuration Data
- **Owning/Shared Domain:** Shared Platform (`SecurityModule`)
- **Purpose:** Enforces Role-Based Access Control (RBAC) and contextual row-level data scoping rules.
- **Business Description:** Maps system roles (Pro-Chancellor, Senior Management, Deans, HODs, HR Operations, Committee Members, Staff) to permission sets. Enforces institutional row-level scoping (e.g., HOD restricted to department data, Dean to school data).
- **Requirement Traceability:** `REQ-SEC-03`.
- **Functional Traceability:** `SHR-RBC-REQ-01` to `02`.
- **Source Classification:** `[B] Logical Implication`.
- **Notes / Boundary:** Consumed by all functional modules to enforce authorization boundaries.

### 8.3 ENT-SHR-03: Workflow State Instance & Transition Log
- **Conceptual Classification:** Workflow / Process Data
- **Owning/Shared Domain:** Shared Platform (`WorkflowEngineModule`)
- **Purpose:** Manages Finite State Machine (FSM) instances across all university approval workflows.
- **Business Description:** Tracks current state, prior state, acting user, transition guard criteria, and mandatory approval comments across change requests, requisitions, and appraisals.
- **Requirement Traceability:** `REQ-MOD1-06`, `REQ-MOD2-14`, `REQ-MOD3-04`, `REQ-SHR-01`.
- **Functional Traceability:** `SHR-WFL-REQ-01` to `03`.
- **Source Classification:** `[B] Logical Implication`.
- **Notes / Boundary:** Encapsulates universal workflow logic, isolating business entities from repetitive state-tracking implementations.

### 8.4 ENT-SHR-04: SLA & Deadline Timer Record
- **Conceptual Classification:** Workflow / Process Data
- **Owning/Shared Domain:** Shared Platform (`SlaTimelineModule`)
- **Purpose:** Tracks operational deadlines, countdown timers, grace periods, and automated lockout timestamps.
- **Business Description:** Manages timers for 4-month planning triggers, 15-day submission windows, 7-day turnaround SLAs, and 7th/10th auto-locks. Powers periodic background workers that identify SLA breaches and trigger escalations.
- **Requirement Traceability:** `REQ-MOD2-02`, `REQ-MOD3-02`, `REQ-SHR-03`.
- **Functional Traceability:** `SHR-SLA-REQ-01` to `03`.
- **Source Classification:** `[B] Logical Implication`.
- **Notes / Boundary:** Operates asynchronously across all three business modules.

### 8.5 ENT-SHR-05: Document Metadata & Binary Reference
- **Conceptual Classification:** Document / Attachment Metadata
- **Owning/Shared Domain:** Shared Platform (`DocumentManagementModule`)
- **Purpose:** Maintains metadata pointers and cryptographic hashes for binary files stored in external durable document storage.
- **Business Description:** Maintains external document storage locator references, document types, file sizes, and cryptographic verification hashes for candidate resumes, degree certificates, evaluation evidence, and system-generated letters, ensuring the relational database stores metadata rather than raw binary files.
- **Requirement Traceability:** `REQ-MOD1-03`, `REQ-MOD2-12`, `REQ-MOD3-16`, `REQ-SHR-02`.
- **Functional Traceability:** `SHR-DOC-REQ-01` to `03`.
- **Source Classification:** `[C] Approved Technical Decision`.
- **Notes / Boundary:** Abstracted reference to external durable document storage as established in the approved technology baseline.

### 8.6 ENT-SHR-06: Notification Queue & Dispatch Record
- **Conceptual Classification:** Notification / Communication Data
- **Owning/Shared Domain:** Shared Platform (`NotificationEngineModule`)
- **Purpose:** Asynchronous delivery tracking for multi-channel emails, SMS alerts, and in-app notifications.
- **Business Description:** Captures notification templates, recipient addresses, delivery status (such as pending, dispatched, or failed), retry attempts, error logs, and dispatch timestamps.
- **Requirement Traceability:** `REQ-MOD2-18`, `REQ-MOD3-02`, `REQ-SHR-05`.
- **Functional Traceability:** `SHR-NTF-REQ-01` to `03`.
- **Source Classification:** `[B] Logical Implication`.
- **Notes / Boundary:** Outbound communication gateway host configurations remain an open technical decision under `REQ-TBD-10`.

### 8.7 ENT-SHR-07: Immutable Audit Trail Entry
- **Conceptual Classification:** Audit / History Data
- **Owning/Shared Domain:** Shared Platform (`AuditSecurityModule`)
- **Purpose:** Append-only audit trail capturing full before/after state diffs for all data mutations across the system.
- **Business Description:** Tamper-evident ledger recording acting user ID, originating IP address, timestamp, affected entity name, entity ID, pre-state data snapshot, and post-state data snapshot.
- **Requirement Traceability:** `REQ-MOD1-08`, `REQ-SEC-04`.
- **Functional Traceability:** `MOD1-AUD-REQ-01` to `06`, `SHR-AUD-REQ-01`.
- **Source Classification:** `[A] Explicit Requirement`.
- **Notes / Boundary:** Append-only audit record. Document and audit log retention schedules remain an open policy decision under `REQ-TBD-11`.

### 8.8 ENT-SHR-08: ERP Transactional Outbox Staging Record
- **Conceptual Classification:** Integration / Supporting Data
- **Owning/Shared Domain:** Shared Platform (`ErpIntegrationModule`)
- **Purpose:** Staging record implementing the Transactional Outbox Pattern for guaranteed, reliable ERP synchronization.
- **Business Description:** Stores outbound synchronization payloads written within the same transactional boundary as approved master data changes, ensuring reliable external propagation.
- **Requirement Traceability:** `REQ-MOD1-04`, `REQ-INT-01`.
- **Functional Traceability:** `MOD1-CDB-REQ-03`, `SHR-INT-REQ-01`.
- **Source Classification:** `[C] Approved Technical Decision`.
- **Notes / Boundary:** Integration transport mechanism (staging table vs. REST API vs. SFTP batch) remains an open decision under `REQ-TBD-01`.

---

## 9. Cross-Module Entity Relationships — CONCEPTUAL ONLY

The following section outlines the conceptual associations between entities across different functional domains. In compliance with Phase 4 governance, **no physical foreign keys, cascade rules, or physical table constraints are defined here**.

### 9.1 Module I ↔ Module II (Recruitment to Employee Master)
- **Candidate Onboarding Association:**
  - `ENT-MOD2-09: Letter of Intent & Pre-Onboarding Record` *conceptually triggers the instantiation of* `ENT-MOD1-01: Employee Master Record` and `ENT-MOD1-02: Organization Hierarchy Node` upon Day-1 onboarding verification (`BP-XMOD-001`).
  - `ENT-MOD2-05: Candidate Profile & Application Record` *transfers verified credentials into* `ENT-MOD1-03: Digital Employee File & Dossier Item` upon successful onboarding.
  - Instantiation of `ENT-MOD1-01` *conceptually marks as filled* the corresponding `ENT-MOD2-04: Open Positions Tracker Entry`.
- **Resignation to Urgent Replacement Association:**
  - `ENT-MOD1-01: Employee Master Record` (transitioning to resigned state) *conceptually initiates* `ENT-MOD2-10: Urgent Replacement Tracker` (`BP-XMOD-002`).
  - `ENT-MOD2-10: Urgent Replacement Tracker` *conceptually pre-populates and spawns* `ENT-MOD2-03: Manpower Requisition Form (MRF)`.

### 9.2 Module I ↔ Module III (Performance to Change Management)
- **Appraisal Eligibility Association (Inbound to Module III):**
  - `ENT-MOD1-01: Employee Master Record` *conceptually provides active personnel rosters and reporting lines to* `ENT-MOD3-02: Group-D Monthly Evaluation Instance` on the 1st of every month (`BP-XMOD-003`).
  - `ENT-MOD1-01: Employee Master Record` *conceptually provides Date of Joining (DOJ) to initiate* `ENT-MOD3-04: General Staff Goal Setting Record` (within 30 days) and `ENT-MOD3-05: Quarterly Review Record` (every 90 days).
  - `ENT-MOD1-01: Employee Master Record` *conceptually provides probation clearance and last appraisal date to* `ENT-MOD3-07: Faculty Eligibility Batch` on the 10th of every month.
- **Appraisal Outcome Handshake (Outbound from Module III):**
  - `ENT-MOD3-03: Group-D Annual Collation Report` *conceptually generates* `ENT-MOD1-04: Service Condition Change Request` upon Management salary slab approval.
  - `ENT-MOD3-06: General Staff Annual Appraisal Outcome` *conceptually generates* `ENT-MOD1-04: Service Condition Change Request` for approved increments, title changes, or promotions (`BP-XMOD-004`).
  - `ENT-MOD3-09: Faculty ECM Session & TNU Protocol Matrix` *conceptually generates* `ENT-MOD1-04: Service Condition Change Request` for approved annual or accelerated increments.

### 9.3 Module I Internal Relationships
- `ENT-MOD1-01: Employee Master Record` *conceptually anchors* `ENT-MOD1-02: Organization Hierarchy Node`, representing the employee's active institutional reporting placement.
- `ENT-MOD1-01: Employee Master Record` *conceptually possesses* `ENT-MOD1-03: Digital Employee File & Dossier Item`.
- `ENT-MOD1-01: Employee Master Record` *conceptually undergoes proposed modifications via* `ENT-MOD1-04: Service Condition Change Request`.
- `ENT-MOD1-04: Service Condition Change Request` *conceptually accumulates* `ENT-MOD1-05: Service Change Approval Action` entries.
- `ENT-MOD1-04: Service Condition Change Request` (upon activation) *conceptually appends historical records to* `ENT-MOD1-06: Employee Service History Ledger` and *updates* `ENT-MOD1-01: Employee Master Record`.

### 9.4 Shared Platform Cross-Cutting Associations
- `ENT-SHR-07: Immutable Audit Trail Entry` *conceptually monitors and records before/after state diffs for all mutations across* all Module I, II, and III entities (`REQ-MOD1-08`, `REQ-SEC-04`).
- `ENT-SHR-03: Workflow State Instance & Transition Log` *conceptually tracks lifecycle state transitions for* `ENT-MOD1-04`, `ENT-MOD2-01`, `ENT-MOD2-02`, `ENT-MOD2-03`, `ENT-MOD3-02`, `ENT-MOD3-05`, `ENT-MOD3-08`, and `ENT-MOD3-09`.
- `ENT-SHR-04: SLA & Deadline Timer Record` *conceptually monitors time-bound submission windows, turnaround times, and lockouts for* all requisition, evaluation, and approval entities.
- `ENT-SHR-05: Document Metadata & Binary Reference` *conceptually provides cryptographic pointer management for binary attachments associated with* `ENT-MOD1-03`, `ENT-MOD2-01`, `ENT-MOD2-05`, `ENT-MOD2-09`, `ENT-MOD3-05`, `ENT-MOD3-08`, and `ENT-MOD3-09`.
- `ENT-SHR-08: ERP Transactional Outbox Staging Record` *conceptually stages outbound updates whenever* `ENT-MOD1-01: Employee Master Record` is updated or activated.

---

## 10. Entity Traceability Matrix

The following matrix provides comprehensive backward traceability for every conceptual entity to the frozen project baseline:

| Entity ID | Entity Name | Domain Owner | Conceptual Classification | Requirement IDs | Business Process IDs | Functional IDs | Source Class |
|---|---|---|---|---|---|---|---|
| **`ENT-MOD1-01`** | Employee Master Record | Module I | Master Data | `REQ-MOD1-01`, `02`, `04`, `05`, `07`, `08` | `BP-M1-001`, `004`, `007`, `011`, `BP-XMOD-001`, `003` | `MOD1-CDB-REQ-01` to `05` | `[A]` |
| **`ENT-MOD1-02`** | Organization Hierarchy Node | Module I | Master Data | `REQ-MOD1-02`, `06`, `REQ-SHR-04` | `BP-M1-002`, `010` | `MOD1-ORG-REQ-01` to `04` | `[A]` |
| **`ENT-MOD1-03`** | Digital Employee File & Dossier Item | Module I | Document / Attachment Metadata | `REQ-MOD1-03` | `BP-M1-003`, `BP-XMOD-001`, `004` | `MOD1-FIL-REQ-01` to `04` | `[A]` |
| **`ENT-MOD1-04`** | Service Condition Change Request | Module I | Transactional Data | `REQ-MOD1-05`, `06`, `07` | `BP-M1-004`, `005`, `006`, `007` | `MOD1-CHG-REQ-01` to `12` | `[A]` |
| **`ENT-MOD1-05`** | Service Change Approval Action | Module I | Workflow / Process Data | `REQ-MOD1-06` | `BP-M1-005`, `006` | `MOD1-APP-REQ-01` to `06` | `[A]` |
| **`ENT-MOD1-06`** | Employee Service History Ledger | Module I | Audit / History Data | `REQ-MOD1-08` | `BP-M1-007`, `008` | `MOD1-AUD-REQ-04` | `[A]` |
| **`ENT-MOD2-01`** | Academic Manpower Plan & Workload Req. | Module II | Transactional Data | `REQ-MOD2-02`, `04`, `05`, `06` | `BP-M2-ACAD-001` to `006` | `MOD2-MP-FAC-REQ-01` to `08` | `[A]` |
| **`ENT-MOD2-02`** | Non-Academic Manpower Plan | Module II | Transactional Data | `REQ-MOD2-07`, `08`, `09`, `10` | `BP-M2-NACAD-001` to `005` | `MOD2-MP-NF-REQ-01` to `07` | `[A]` |
| **`ENT-MOD2-03`** | Manpower Requisition Form (MRF) | Module II | Transactional Data | `REQ-MOD2-03`, `06`, `10` | `BP-M2-ACAD-006`, `BP-M2-NACAD-005` | `MOD2-MRF-REQ-01` to `07` | `[A]` |
| **`ENT-MOD2-04`** | Open Positions Tracker Entry | Module II | Reporting / Derived Data | `REQ-MOD2-11` | `BP-M2-ACAD-006`, `BP-M2-TRK-001` | `MOD2-POS-REQ-01` to `05` | `[A]` |
| **`ENT-MOD2-05`** | Candidate Profile & Application Record | Module II | Transactional Data | `REQ-MOD2-12`, `13`, `19` | `BP-M2-TRK-001`, `BP-M2-ACAD-007` | `MOD2-SRC-REQ-01` to `06` | `[A]` |
| **`ENT-MOD2-06`** | Recruiter Calling Record (RCS) | Module II | Evaluation / Assessment Data | `REQ-MOD2-12` | `BP-M2-ACAD-007`, `008` | `MOD2-RCS-REQ-01` to `06` | `[A]` |
| **`ENT-MOD2-07`** | Academic SCM Session & Score Record | Module II | Evaluation / Assessment Data | `REQ-MOD2-14` | `BP-M2-ACAD-009`, `010` | `MOD2-SCM-REQ-01` to `06` | `[A]` |
| **`ENT-MOD2-08`** | Non-Academic Interview Round & Score Rec. | Module II | Evaluation / Assessment Data | `REQ-MOD2-15` | `BP-M2-NACAD-006`, `007` | `MOD2-INT-REQ-01` to `06` | `[A]` |
| **`ENT-MOD2-09`** | Letter of Intent (LOI) & Pre-Onboarding | Module II | Transactional Data | `REQ-MOD2-16`, `17`, `18` | `BP-M2-ACAD-011`, `012`, `BP-XMOD-001` | `MOD2-YTJ-REQ-01` to `07` | `[A]` |
| **`ENT-MOD2-10`** | Urgent Replacement Tracker | Module II | Transactional Data | `REQ-MOD2-03` | `BP-M2-URG-001`, `BP-XMOD-002` | `MOD2-URG-REQ-01` to `06` | `[A]` |
| **`ENT-MOD3-01`** | Group-D Evaluation Form Template | Module III | Reference / Configuration Data | `REQ-MOD3-01`, `03` | `BP-M3-GD-001` | `MOD3-GD-REQ-01` to `03` | `[A]` |
| **`ENT-MOD3-02`** | Group-D Monthly Evaluation Instance | Module III | Evaluation / Assessment Data | `REQ-MOD3-01`, `02`, `04`, `05` | `BP-M3-GD-002` to `005` | `MOD3-GD-REQ-04` to `13` | `[A]` |
| **`ENT-MOD3-03`** | Group-D Annual Collation Report | Module III | Evaluation / Assessment Data | `REQ-MOD3-06`, `07`, `08` | `BP-M3-GD-006` to `008` | `MOD3-GD-REQ-14` to `21` | `[A]` |
| **`ENT-MOD3-04`** | General Staff Goal Setting Record | Module III | Evaluation / Assessment Data | `REQ-MOD3-09` | `BP-M3-KRA-001` | `MOD3-KRA-REQ-01` to `04` | `[A]` |
| **`ENT-MOD3-05`** | General Staff Quarterly Review Record | Module III | Evaluation / Assessment Data | `REQ-MOD3-10`, `11`, `12` | `BP-M3-KRA-002` to `004` | `MOD3-KRA-REQ-05` to `14` | `[A]` |
| **`ENT-MOD3-06`** | General Staff Annual Appraisal Outcome | Module III | Evaluation / Assessment Data | `REQ-MOD3-13`, `REQ-INT-04` | `BP-M3-KRA-005`, `BP-XMOD-004` | `MOD3-KRA-REQ-15` to `18` | `[A]` |
| **`ENT-MOD3-07`** | Faculty Appraisal Eligibility Batch | Module III | Transactional Data | `REQ-MOD3-14`, `15` | `BP-M3-FAC-001`, `002` | `MOD3-FAC-REQ-01` to `05` | `[A]` |
| **`ENT-MOD3-08`** | Faculty Self-Appraisal Dossier & Verif. | Module III | Evaluation / Assessment Data | `REQ-MOD3-16`, `17` | `BP-M3-FAC-003` to `005` | `MOD3-FAC-REQ-06` to `13` | `[A]` |
| **`ENT-MOD3-09`** | Faculty ECM Session & TNU Protocol Matrix | Module III | Evaluation / Assessment Data | `REQ-MOD3-18`, `19`, `20`, `REQ-INT-04` | `BP-M3-FAC-006` to `008`, `BP-XMOD-004` | `MOD3-FAC-REQ-14` to `22` | `[A]` |
| **`ENT-SHR-01`** | User Account & Credential Profile | Shared | Integration / Supporting Data | `REQ-SEC-01`, `02`, `REQ-MOD2-14` | Process-wide Authentication | `SHR-AUT-REQ-01` to `04` | `[B]` |
| **`ENT-SHR-02`** | Role & Permission Assignment | Shared | Reference / Configuration Data | `REQ-SEC-03` | Platform RBAC Enforcement | `SHR-RBC-REQ-01` to `02` | `[B]` |
| **`ENT-SHR-03`** | Workflow State Instance & Transition Log | Shared | Workflow / Process Data | `REQ-MOD1-06`, `REQ-MOD2-14`, `REQ-MOD3-04` | Universal FSM Engines | `SHR-WFL-REQ-01` to `03` | `[B]` |
| **`ENT-SHR-04`** | SLA & Deadline Timer Record | Shared | Workflow / Process Data | `REQ-MOD2-02`, `REQ-MOD3-02`, `REQ-SHR-03` | SLA & Escalation Handlers | `SHR-SLA-REQ-01` to `03` | `[B]` |
| **`ENT-SHR-05`** | Document Metadata & Binary Reference | Shared | Document / Attachment Metadata | `REQ-MOD1-03`, `REQ-MOD2-12`, `REQ-MOD3-16` | Universal Storage Handlers | `SHR-DOC-REQ-01` to `03` | `[C]` |
| **`ENT-SHR-06`** | Notification Queue & Dispatch Record | Shared | Notification / Communication Data | `REQ-MOD2-18`, `REQ-MOD3-02`, `REQ-SHR-05` | Multi-Channel Dispatchers | `SHR-NTF-REQ-01` to `03` | `[B]` |
| **`ENT-SHR-07`** | Immutable Audit Trail Entry | Shared | Audit / History Data | `REQ-MOD1-08`, `REQ-SEC-04` | Platform-Wide Audit Ingestion | `MOD1-AUD-REQ-01` to `06` | `[A]` |
| **`ENT-SHR-08`** | ERP Transactional Outbox Staging Record | Shared | Integration / Supporting Data | `REQ-MOD1-04`, `REQ-INT-01` | `BP-M1-004`, `007` | `MOD1-CDB-REQ-03`, `SHR-INT-REQ-01` | `[C]` |

---

## 11. Entity Count Reconciliation

The conceptual entity inventory establishes **exactly thirty-three (33) primary conceptual entities** partitioned across the four architectural domains:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 ENTITY COUNT RECONCILIATION                                      │
├───────────────────────────────────────┬─────────────────┬────────────────────────────────────────┤
│ ARCHITECTURAL DOMAIN                  │ ENTITY COUNT    │ ENTITY IDENTIFIERS                     │
├───────────────────────────────────────┼─────────────────┼────────────────────────────────────────┤
│ Module I: Change Management           │ 6 Entities      │ ENT-MOD1-01 through ENT-MOD1-06        │
│ Module II: Recruitment & Selection    │ 10 Entities     │ ENT-MOD2-01 through ENT-MOD2-10        │
│ Module III: Performance Management    │ 9 Entities      │ ENT-MOD3-01 through ENT-MOD3-09        │
│ Shared Platform Infrastructure        │ 8 Entities      │ ENT-SHR-01 through ENT-SHR-08          │
├───────────────────────────────────────┼─────────────────┼────────────────────────────────────────┤
│ TOTAL PRIMARY CONCEPTUAL ENTITIES     │ 33 Entities     │ Verified Complete Inventory            │
└───────────────────────────────────────┴─────────────────┴────────────────────────────────────────┘
```

> **Explicit Analytical Inventory Statement:**  
> The 33 entities represent a conceptual analytical inventory and do not represent the final number of physical PostgreSQL tables. Physical tables, junction tables, audit partitions, and normalized relational structures will be specified during downstream logical and physical schema design phases.

---

## 12. TBD and Boundary Register

The conceptual entity inventory preserves the **eleven (11) official baseline TBD items** from [`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md). None of these items are resolved in this step:

| TBD ID | Affected Conceptual Entity | Architectural Aspect Affected | Impact Description |
|---|---|---|---|
| **`REQ-TBD-01`** | `ENT-SHR-08: ERP Transactional Outbox Staging Record` | Integration Transport & Staging Attributes | Governs whether outbound sync occurs via direct database staging tables, REST webhooks, or scheduled SFTP batch exports. |
| **`REQ-TBD-02`** | `ENT-MOD2-01: Academic Manpower Plan`, `ENT-MOD3-01: Group-D Form Template`, `ENT-MOD3-08: Faculty Self-Appraisal Dossier` | Entity Attributes & Form Schemas | Governs exact field-level parameters for Attachment 1 (Teaching Load), Enclosure 1 (Group-D KPIs), and Enclosure 1 (Faculty Dossier). |
| **`REQ-TBD-03`** | `ENT-MOD3-02: Group-D Monthly Evaluation`, `ENT-MOD3-05: Staff Quarterly Review` | Entity Scope & Workflow Ownership | Governs whether technical cadre staff (Lab Technicians, Technical Assistants) are evaluated under Subsystem 1 or Subsystem 2. |
| **`REQ-TBD-04`** | `ENT-MOD3-09: Faculty ECM Session & TNU Protocol Matrix` | Calculation Formula & Scoring Attributes | Governs mathematical weighting formulas and percentage distribution across teaching, research, placement, and service. |
| **`REQ-TBD-05`** | `ENT-MOD3-03: Group-D Annual Collation Report`, `ENT-MOD3-09: Faculty ECM Session Matrix` | Entity Attributes & Decision Slabs | Governs monetary thresholds and percentage increment brackets for annual compensation decisions. |
| **`REQ-TBD-06`** | `ENT-MOD2-10: Urgent Replacement Tracker`, `ENT-MOD1-01: Employee Master Record` | Workflow Initiation & Intake Boundaries | Governs whether resignation intake originates via employee self-service portal or Dean/HR administrative data entry. |
| **`REQ-TBD-07`** | `ENT-SHR-01: User Account & Credential Profile` | Entity Attributes & Authentication Scope | Governs University Identity Provider protocol (Google Workspace, Microsoft Entra, LDAP) and token delivery format for external experts. |
| **`REQ-TBD-08`** | `ENT-MOD2-09: Letter of Intent & Pre-Onboarding Record` | Entity Lifecycle & Contractual Scope | Governs whether LOI is the sole pre-joining instrument or if a distinct formal Appointment Letter is generated post-joining. |
| **`REQ-TBD-09`** | `ENT-MOD1-01: Employee Master Record`, `ENT-MOD1-06: Employee Service History Ledger` | Entity Attributes & Allowance Rules | Governs honorarium and financial allowance tracking rules for secondary administrative roles (Dean, HOD, Proctor, Warden). |
| **`REQ-TBD-10`** | `ENT-SHR-06: Notification Queue & Dispatch Record` | Entity Configuration & Delivery Attributes | Governs SMTP host, SMS gateway, and WhatsApp API credentials for automated notification dispatch. |
| **`REQ-TBD-11`** | `ENT-SHR-07: Immutable Audit Trail Entry`, `ENT-SHR-05: Document Metadata` | Data Retention, Archival & Purging Lifecycle | Governs statutory data retention schedules (in years) for candidate applications, interview scorecards, and audit logs. |

---

## 13. Out-of-Scope Decisions

To maintain strict compliance with Phase 4 governance, the following database design activities are explicitly **out of scope** for this document:

1. **No Physical Database Tables:** No PostgreSQL tables are defined, created, or instantiated.
2. **No PostgreSQL Schema Partitioning:** No physical database schemas (`public`, `mod1`, `mod2`, etc.) are assigned or mandated.
3. **No Columns or Data Types:** Specific table columns, data types (`VARCHAR`, `INT`, `TIMESTAMPTZ`, etc.), and nullability constraints are not defined.
4. **No Primary or Foreign Keys:** Primary key mechanisms (`UUIDv7`, `BIGINT`, composite) and relational foreign key constraints are not specified.
5. **No Indexes:** B-Tree, GIN, composite, or partial indexes are not specified.
6. **No Table Constraints:** Database check constraints, unique constraints, and foreign key cascades are not declared.
7. **No Normalization Level Finalization:** 3NF, BCNF, or denormalization strategies are deferred to logical schema design.
8. **No ORM Entities or Mappings:** No Prisma schema models, TypeORM entity classes, or annotations are generated.
9. **No Migration Scripts:** No SQL DDL/DML migrations or database migration files are created.

---

## 14. Quality & Governance Review

| Audit Checkpoint | Verification Finding | Compliance Status |
|---|---|---|
| **Entity Count Reconciliation** | Exactly 33 conceptual entities documented across 4 domains (6 Mod I, 10 Mod II, 9 Mod III, 8 Shared). | Verified Compliant |
| **Requirements Baseline Integrity** | All 104 atomic requirements in `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md` remain untouched and frozen. | Verified Compliant |
| **Business Process Integrity** | All 59 business processes across `docs/02-business-process/` remain untouched and frozen. | Verified Compliant |
| **Business Rules Integrity** | All 60 business rules in `docs/02-business-process/07-BUSINESS-RULES-CATALOGUE.md` remain untouched and frozen. | Verified Compliant |
| **TBD Baseline Integrity** | Exactly 11 official baseline TBDs documented; zero TBDs resolved or invented. | Verified Compliant |
| **Stakeholder Delta Isolation** | Unconfirmed delta items (`CONF-01` to `CONF-10`, `DLT-*`) are strictly isolated and not promoted to approved requirements. | Verified Compliant |
| **Physical Design Isolation** | Zero physical tables, columns, keys, indexes, DDL/DML, migrations, or ORM entities created. | Verified Compliant |
| **Traceability Completeness** | Every entity possesses direct, verified backward traceability to official requirements, processes, and FRDs. | Verified Compliant |

---

## 15. Document Status & Progression

```
====================================================================================================
DOCUMENT STATUS:
COMPLETED — CONCEPTUAL ENTITY IDENTIFICATION

NEXT PLANNED DOCUMENT:
docs/08-database/04-ENTITY-RELATIONSHIP-SPECIFICATION.md
Description:
Conceptual entity-relationship specification, conceptual cardinality, and cross-domain interaction topology.
====================================================================================================
```

---
*End of Document — Conceptual Entity Identification & Domain Inventory.*
