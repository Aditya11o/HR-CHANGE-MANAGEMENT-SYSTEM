# Phase 4 — Database Documentation
## 02. Conceptual Data Model Overview

```
====================================================================================================
STATUS:
PHASE 4 FOUNDATION — DOCUMENTATION ONLY — INITIAL ARCHITECTURE ESTABLISHMENT

IMPORTANT GOVERNANCE NOTICE:
This document is STRICTLY DOCUMENTATION ONLY. 
It identifies the conceptual data domains, core business entities, relationships, and lifecycle states 
explicitly supported by the existing requirements (104 frozen baseline), business processes (59 frozen baseline), 
and approved Functional Requirements Specifications (FRDs). 
No physical database tables, column-level DDL scripts, foreign key constraint declarations, Prisma schemas, 
or TypeORM entities are created herein. All items lacking complete source definition are strictly 
classified as [E] TBD / Open Decision.
====================================================================================================
```

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/08-database/02-DATA-MODEL-OVERVIEW.md` |
| **System Phase** | Phase 4 — Database Documentation |
| **Project Name** | University HR Change Management & Automation System |
| **Document Purpose** | Conceptual data model cataloguing all explicitly supported business entities, domains, relationships, lifecycles, and open TBD decisions |
| **Date of Preparation** | September 29, 2026 |
| **Authoritative Baselines** | `docs/01-requirements/` (104 Requirements); `docs/02-business-process/` (59 Processes); `docs/03-functional-requirements/` (Approved FRDs); `TECHNOLOGY_ARCHITECTURE_BASELINE.md` |
| **Database Technology** | **PostgreSQL** (Primary Relational System of Record — `[C] Approved Technical Decision`) |

---

## 1. Introduction to Conceptual Data Modeling

The conceptual data model establishes the formal taxonomy of **business data domains** and **conceptual entities** that underpin the University HR Change Management & Automation System. 

In strict compliance with project governance:
- Every conceptual entity documented herein maps directly to an approved requirement ID (`REQ-*`), business process (`BP-*`), business rule (`BR-*`), or functional requirement (`MOD*-REQ-*`).
- No technical column names, arbitrary IDs, or invented database tables are introduced.
- No relationships are assumed merely because they are standard in commercial HR software. Only relationships explicitly defined in the university workflows and requirement briefs are recognized.
- Where university policy has not yet defined the full data schema or formula, the entity or attribute is explicitly tagged as **`[E] TBD / Open Decision`**.
- Unconfirmed stakeholder decision items (`CONF-01` to `CONF-10`) do not alter the baseline; the frozen requirements remain the authoritative baseline.

> **Architectural Scope Declaration:**  
> The identified conceptual entity count is an analytical data-domain inventory and does not represent the final number of physical PostgreSQL tables.

---

## 2. Classification Taxonomy

Each conceptual entity and data domain is categorized according to the established project classification standard:

| Classification Tag | Definition | Governance Constraint |
|---|---|---|
| **`[A] Explicit Requirement`** | The entity, lifecycle state, or relationship is directly stated in official requirement briefs or baseline documents. | Must be faithfully modeled without modification. |
| **`[B] Logical Implication`** | The entity or relationship is a mathematically or architecturally necessary deduction from an explicit requirement. | Derived strictly from business logic; no extraneous features. |
| **`[C] Approved Technical Decision`**| The persistence structure is an approved component of the Technology Architecture Baseline. | PostgreSQL, Redis caching, Object Storage metadata, Outbox pattern. |
| **`[D] Proposed Detail`** | A provisional implementation specification requiring formal operational confirmation. | E.g., proposed file size limits or queue concurrency parameters. |
| **`[E] TBD / Open Decision`** | The data structure or policy formula is incomplete in source materials and requires leadership decision. | Preserved without making assumptions or inventing missing rules. |

---

## 3. Module I Conceptual Data Domains & Entities

Module I governs the Central Employee Database, Organization Hierarchy, Digital Personal Dossiers, and Service Condition Change Management:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            MODULE I: CONCEPTUAL DATA TOPOLOGY                                    │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   ┌──────────────────────────┐      1:1      ┌──────────────────────────┐                        │
│   │   Organization Node      │◄─────────────►│     Employee Master      │                        │
│   │  (Hierarchy & Reporting) │               │ (Single Source of Truth) │                        │
│   └──────────────────────────┘               └─────────────┬────────────┘                        │
│                                                            │                                     │
│                 ┌──────────────────────────────────────────┼─────────────────────────┐           │
│                 │ 1:1                                      │ 1:M                     │ 1:M       │
│                 ▼                                          ▼                         ▼           │
│   ┌──────────────────────────┐               ┌──────────────────────────┐ ┌────────────────────┐ │
│   │   Digital Personal File  │               │   Service Change Request │ │  Service History   │ │
│   │  (Archived Dossier Items)│               │ (Staged 10 Change Types) │ │ (Historical Ledger)│ │
│   └──────────────────────────┘               └─────────────┬────────────┘ └────────────────────┘ │
│                                                            │ 1:M                                 │
│                                                            ▼                                     │
│                                              ┌──────────────────────────┐                        │
│                                              │  Change Approval Action  │                        │
│                                              │   (2-Level Sign-Off Log) │                        │
│                                              └──────────────────────────┘                        │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 3.1 Entity: Employee Master Record
- **Domain:** Module I — Central Employee Database
- **Purpose:** Serves as the authoritative single source of truth for all active personnel across the University (`[A]` Baseline `REQ-MOD1-01`, `MOD1-CDB-REQ-01`).
- **Source References:** `REQ-MOD1-01` to `05`, `BP-M1-001`, `MOD1-CDB-REQ-01` to `05`.
- **Key Business Meaning:** Maintains core employment attributes: unique Employee ID, legal name, official designation, school/department assignment, salary/pay structure, level/band, supervisory reporting line, Date of Joining (DOJ), probation clearance status, and operational status.
- **Major Relationships:**
  - *Belongs to* School / Department (`[A]` `REQ-MOD1-01`).
  - *Reports to* Supervisory Employee (self-referencing hierarchical relation) (`[A]` `REQ-MOD1-02`).
  - *Has one* Organization Hierarchy Node (`[A]` `MOD1-ORG-REQ-01`).
  - *Has one* Digital Personal File (`[A]` `MOD1-FIL-REQ-01`).
  - *Has many* Service Condition Change Requests (`[A]` `REQ-MOD1-05`).
  - *Has many* Historical Service Ledger entries (`[A]` `REQ-MOD1-08`).
- **Lifecycle Considerations:** Transitions through operational statuses: Active, On Probation, Confirmed, Resigned, Retired (`[B]` `MOD1-CDB-REQ-05`). Operational deactivation is represented through lifecycle state transitions without destructive loss of required history, ensuring required historical service records are preserved (`[A]` `REQ-MOD1-08`), while final data retention and archival/deletion policies remain governed by the official requirements and statutory retention schedules under `REQ-TBD-11` where applicable (`[B/E]`).
- **Audit & Version Considerations:** Every attribute modification is captured in the immutable audit trail with actor attribution and state diffs (`[A]` `MOD1-AUD-REQ-01`).
- **Effective-Date Considerations:** The master record reflects currently active service conditions. Scheduled future-dated changes do not mutate this entity until the effective date arrives (`[A]` `REQ-MOD1-07`).
- **Classification Status:** `[A] Explicit Requirement`.

### 3.2 Entity: Organization Hierarchy Node & Reporting Line
- **Domain:** Module I — Dynamic Organization Chart
- **Purpose:** Models the university's hierarchical organizational structure, connecting schools, departments, and supervisory reporting lines (`[A]` Baseline `REQ-MOD1-02`, `MOD1-ORG-REQ-01`).
- **Source References:** `REQ-MOD1-02`, `BP-M1-002`, `MOD1-ORG-REQ-01` to `04`, `SHR-ORG-REQ-01` to `03`.
- **Key Business Meaning:** Encapsulates parent-child reporting links. Provides the topological structure consumed by workflow engines to route approval tasks to HODs, Deans, and Reporting Authorities (`[B]` `SHR-ORG-REQ-03`).
- **Major Relationships:**
  - *Linked 1-to-1 with* Employee Master Record (`[A]` `MOD1-ORG-REQ-01`).
  - *Parent-child relationship with* Supervisory Node (`[A]` `REQ-MOD1-02`).
  - *Belongs to* Department / School administrative unit (`[A]` `REQ-MOD1-01`).
- **Lifecycle Considerations:** Instantiated on candidate onboarding; realigned in real time upon approved change in reporting authority, designation, or department transfer (`[A]` `MOD1-ORG-REQ-02`).
- **Audit & Version Considerations:** All reporting line adjustments are logged with effective dates and approving authority (`[A]` `MOD1-AUD-REQ-01`).
- **Effective-Date Considerations:** Hierarchy updates take effect on the effective date of the authorizing change request (`[A]` `REQ-MOD1-07`).
- **Classification Status:** `[A] Explicit Requirement`.

### 3.3 Entity: Digital Employee File & Dossier Item
- **Domain:** Module I — Digital Personal Dossier
- **Purpose:** Consolidated digital personal folder archiving all historical personnel documents and verified records (`[A]` Baseline `REQ-MOD1-03`, `MOD1-FIL-REQ-01`).
- **Source References:** `REQ-MOD1-03`, `BP-M1-003`, `MOD1-FIL-REQ-01` to `04`, `SHR-FIL-REQ-01` to `03`.
- **Key Business Meaning:** Permanent repository indexing: verified joining credentials, degree certificates, signed LOI, service change notices, increment letters, and annual appraisal scorecards.
- **Major Relationships:**
  - *Belongs to* Employee Master Record (`[A]` `REQ-MOD1-03`).
  - *References* Document Metadata (abstracted Object Storage pointers) (`[C]` `SHR-DOC-REQ-01`).
- **Lifecycle Considerations:** Created on Day-1 onboarding; append-only ingestion across employee lifecycle; permanent institutional retention (`[A]` `SHR-FIL-REQ-02`).
- **Audit & Version Considerations:** Documents are read-only and tamper-evident once indexed (`[B]` `SHR-FIL-REQ-03`).
- **Effective-Date Considerations:** N/A (archival is event-triggered).
- **Classification Status:** `[A] Explicit Requirement`.

### 3.4 Entity: Service Condition Change Request (Polymorphic)
- **Domain:** Module I — Change Management Engine
- **Purpose:** Isolated staging entity capturing proposed service modifications across 10 standardized categories (`[A]` Baseline `REQ-MOD1-05`, `MOD1-CHG-REQ-01`).
- **Source References:** `REQ-MOD1-05`, `REQ-MOD1-07`, `BP-M1-004` to `007`, `MOD1-CHG-REQ-01` to `12`.
- **Key Business Meaning:** Staged container supporting 10 distinct service change formats: (1) Salary Change, (2) Designation Change, (3) Reportee Change, (4) Reporting Authority Change, (5) Level Change, (6) Department/School Change, (7) Location Change, (8) Additional Responsibility, (9) Qualification Change, (10) Other Service Condition. Strictly isolates pending requests from active master records.
- **Major Relationships:**
  - *Belongs to* Employee Master Record (`[A]` `REQ-MOD1-05`).
  - *Initiated by* HR Operations (`[A]` Baseline `REQ-MOD1-05`; note: extending initiation to administrative/departmental officers is a pending governance item under reference `CONF-01`).
  - *Has many* Change Approval Actions (2-level hierarchy) (`[A]` `REQ-MOD1-06`).
- **Lifecycle Considerations:** Standard state transitions: Draft → Submitted → Pending HR Review → Pending Management Approval → Approved (or Rejected / Returned for Clarification). If approved with future effective date: Approved Pending Activation → Activated (`[B]` Logical Implication from `BP-M1-004` to `007`).
- **Audit & Version Considerations:** Every state transition and proposed field value is logged in the audit trail (`[A]` `MOD1-AUD-REQ-01`).
- **Effective-Date Considerations:** Core business attribute. Governs whether activation occurs immediately upon Level 2 approval or stages for scheduled activation (`[A]` `REQ-MOD1-07`).
- **Classification Status:** `[A] Explicit Requirement`.

### 3.5 Entity: Service Change Approval Action
- **Domain:** Module I — Approval Hierarchy
- **Purpose:** Records individual review, endorsement, clarification, or rejection actions within the 2-level approval hierarchy (`[A]` Baseline `REQ-MOD1-06`, `MOD1-APP-REQ-01`).
- **Source References:** `REQ-MOD1-06`, `BP-M1-005`/`006`, `MOD1-APP-REQ-01` to `06`.
- **Key Business Meaning:** Formal governance record capturing: approval level (`Level 1: HR Team`, `Level 2: Senior Management`), acting user ID, action timestamp, decision code, and mandatory written comments.
- **Major Relationships:**
  - *Belongs to* Service Condition Change Request (`[A]` `REQ-MOD1-06`).
  - *References* Approver User Account (`[B]` `SHR-AUT-REQ-01`).
- **Lifecycle Considerations:** Append-only transaction log. Once submitted, an approval action cannot be edited or deleted (`[A]` `MOD1-APP-REQ-04`).
- **Audit & Version Considerations:** Fully auditable and tamper-evident (`[A]` `REQ-SEC-04`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

### 3.6 Entity: Employee Service History / Historical Version Ledger
- **Domain:** Module I — Historical Ledgering
- **Purpose:** Maintains a chronological, continuous ledger of activated service conditions throughout an employee's institutional career (`[A]` Baseline `REQ-MOD1-08`, `MOD1-AUD-REQ-04`).
- **Source References:** `REQ-MOD1-08`, `BP-M1-007`, `MOD1-AUD-REQ-04`.
- **Key Business Meaning:** Stores historical service slices bounded by effective temporal boundaries, capturing the designation, salary, department, reporting authority, and rank active during that specific interval.
- **Major Relationships:**
  - *Belongs to* Employee Master Record (`[A]` `REQ-MOD1-08`).
  - *Originates from* Activated Service Condition Change Request (`[A]` `REQ-MOD1-07`).
- **Lifecycle Considerations:** Append-only ledger. New record created upon activation of each service change; prior active record is closed out (`[B]` `MOD1-AUD-REQ-04`).
- **Audit & Version Considerations:** Immutable historical record (`[A]` `REQ-MOD1-08`).
- **Effective-Date Considerations:** Governed strictly by effective dates to support point-in-time historical queries (`[A]` `REQ-MOD1-08`).
- **Classification Status:** `[A] Explicit Requirement`.

---

## 4. Module II Conceptual Data Domains & Entities

Module II governs Academic and Non-Academic Manpower Planning, Requisitions (MRF), Sourcing, CV Processing, Selection Committees, Multi-Round Interviews, and Pre-Onboarding:

### 4.1 Entity: Academic Manpower Plan & Workload Requisition
- **Domain:** Module II — Academic Manpower Planning
- **Purpose:** Encapsulates semester faculty requisition proposals based on teaching load assessments (`[A]` Baseline `REQ-MOD2-02`, `MOD2-MP-FAC-REQ-01`).
- **Source References:** `REQ-MOD2-02` to `06`, `BP-M2-ACAD-001` to `006`, `MOD2-MP-FAC-REQ-01` to `08`.
- **Key Business Meaning:** Represents the 4-month semester planning cycle for teaching faculty. Holds Dean's requirement submissions, teaching load distribution (**Attachment 1**), HR vetting findings, and Pro-Chancellor approval.
- **Major Relationships:**
  - *Belongs to* School / Academic Department (`[A]` `REQ-MOD2-02`).
  - *Submitted by* Dean of School (within 15-day SLA) (`[A]` `MOD2-MP-FAC-REQ-02`).
  - *Vetted by* HR Department (`[A]` Baseline `REQ-MOD2-05`, `BP-M2-ACAD-003`; note: formal academic vetting role for Associate Dean is a pending governance item under reference `CONF-02` / `CONF-03` / `CFL-01`).
  - *Approved by* Hon'ble Pro-Chancellor (7-day turnaround SLA) (`[A]` `MOD2-MP-FAC-REQ-05`).
  - *Generates* Manpower Requisition Forms (MRF) upon approval (`[A]` `MOD2-MP-FAC-REQ-06`).
- **Lifecycle Considerations:** Triggered (T-4m) → Dean Submitting (15d) → HR Vetting (T-3m) → Pro-Chancellor Approval (7d) → Approved (`[A]` Baseline `BP-M2-ACAD-001` to `005`).
- **Audit & Version Considerations:** Vetting remarks, clarification loops, and approvals logged (`[A]` `REQ-MOD2-05`).
- **Effective-Date Considerations:** Auto-calculates target completion deadline at least 1 month prior to semester start (`[A]` `MOD2-MP-FAC-REQ-08`).
- **Classification Status:** `[A] Explicit Requirement`.

### 4.2 Entity: Non-Academic Manpower Plan
- **Domain:** Module II — Non-Academic Manpower Planning
- **Purpose:** Governs annual non-faculty staffing requisitions (`[A]` Baseline `REQ-MOD2-07`, `MOD2-MP-NF-REQ-01`).
- **Source References:** `REQ-MOD2-07` to `10`, `BP-M2-NACAD-001` to `005`, `MOD2-MP-NF-REQ-01` to `07`.
- **Key Business Meaning:** Annual staffing plan for administrative, technical, and operational staff (including Lab Technicians under baseline `REQ-MOD2-01`; note: grouping Lab Technicians under Academic SCM is a pending governance item under reference `CONF-04` / `CFL-02`). Enforces the strict institutional rule of **maximum 1 planned requisition per department per year** (`[A]` `MOD2-MP-NF-REQ-04`).
- **Major Relationships:**
  - *Belongs to* Department (`[A]` `REQ-MOD2-07`).
  - *Submitted by* Head of Department (within 15-day SLA) (`[A]` `MOD2-MP-NF-REQ-02`).
  - *Vetted by* Head of HR (15-day consolidation SLA) (`[A]` `MOD2-MP-NF-REQ-03`).
  - *Approved by* Hon'ble Pro-Chancellor (7-day turnaround SLA) (`[A]` `MOD2-MP-NF-REQ-04`).
  - *Generates* Manpower Requisition Forms upon approval (`[A]` `MOD2-MP-NF-REQ-05`).
- **Lifecycle Considerations:** Annual Trigger (4m) → HOD Submission → HR Vetting → Pro-Chancellor Approval → MRF Generation (`[A]` `BP-M2-NACAD-001` to `005`).
- **Audit & Version Considerations:** Quota enforcement check and approvals logged (`[A]` `REQ-MOD2-09`).
- **Effective-Date Considerations:** Target completion at least 1 month prior to operational deployment (`[A]` `MOD2-MP-NF-REQ-07`).
- **Classification Status:** `[A] Explicit Requirement`.

### 4.3 Entity: Manpower Requisition Form (MRF)
- **Domain:** Module II — Position Requisition Lifecycle
- **Purpose:** Formal operational requisition authorizing job publication and sourcing (`[A]` Baseline `REQ-MOD2-03`, `REQ-MOD2-06`, `MOD2-MRF-REQ-01`).
- **Source References:** `REQ-MOD2-03`, `REQ-MOD2-06`, `BP-M2-ACAD-006`, `BP-M2-NACAD-005`, `MOD2-MRF-REQ-01` to `07`.
- **Key Business Meaning:** Distinct authorization record categorized as either **Planned MRF** (originating from approved annual/semester plans) or **Urgent Replacement MRF** (originating from an accepted resignation). Authorizes public advertisement within 7 days.
- **Major Relationships:**
  - *Linked to* Academic or Non-Academic Manpower Plan (for planned MRFs) (`[A]` `REQ-MOD2-06`).
  - *Linked to* Urgent Replacement Tracker (for replacement MRFs) (`[A]` `REQ-MOD2-03`).
  - *Generates* Open Positions Tracker entry (`[A]` `MOD2-POS-REQ-01`).
- **Lifecycle Considerations:** Raised → Received by HR → Published (within 7-day SLA) → Active Sourcing → Fulfilled / Closed (`[A]` Baseline `BP-M2-ACAD-006`).
- **Audit & Version Considerations:** Requisition metadata and timeline SLAs tracked in audit trail (`[A]` `MOD2-MRF-REQ-07`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

### 4.4 Entity: Open Positions Tracker Entry
- **Domain:** Module II — Headcount Tracking
- **Purpose:** Authoritative operational ledger tracking all active vacancies across the institution (`[A]` Baseline `REQ-MOD2-11`, `MOD2-POS-REQ-01`).
- **Source References:** `REQ-MOD2-11`, `BP-M2-ACAD-006`, `MOD2-POS-REQ-01` to `05`.
- **Key Business Meaning:** University **Attachment 3** requisition tracker. Auto-instantiated within 30 days of MRF approval, providing real-time visibility into hiring progress across all academic and administrative units.
- **Major Relationships:**
  - *Linked 1-to-1 with* MRF (`[A]` `REQ-MOD2-11`).
  - *Associated with* Candidate Applications and Selection Panels (`[B]` `MOD2-POS-REQ-03`).
- **Lifecycle Considerations:** Transitions through: Open → Sourcing → Interviewing → Offered → Filled (upon candidate LOI acceptance) or Cancelled (`[B]` `MOD2-POS-REQ-02`).
- **Audit & Version Considerations:** Headcount allocation and state changes logged (`[A]` `MOD2-POS-REQ-05`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

### 4.5 Entity: Candidate Profile & Application Record
- **Domain:** Module II — Central CV Database & Omnichannel Sourcing
- **Purpose:** Centralized applicant repository capturing multi-channel candidate data (`[A]` Baseline `REQ-MOD2-12`, `REQ-MOD2-19`, `MOD2-SRC-REQ-01`).
- **Source References:** `REQ-MOD2-12`, `REQ-MOD2-19`, `BP-M2-TRK-001`, `MOD2-SRC-REQ-01` to `06`, `MOD2-SCR-REQ-01` to `05`.
- **Key Business Meaning:** Ingests candidate profiles from website applications, direct email, referrals, and external job portals. Deduplicates by email/phone. Stores parsed qualification attributes, UGC compliance eligibility flags, and screening outcomes.
- **Major Relationships:**
  - *Applies to* Open Position / MRF (`[A]` `REQ-MOD2-12`).
  - *References* Candidate Resume in Object Storage (`[C]` `SHR-DOC-REQ-01`).
  - *Has one* Recruiter Calling Record (RCS) (`[A]` `MOD2-RCS-REQ-01`).
  - *Has many* Interview Round / SCM Score Records (`[A]` `REQ-MOD2-14`, `15`).
  - *Has zero-or-one* Letter of Intent (LOI) Record (`[A]` `REQ-MOD2-16`).
- **Lifecycle Considerations:** Ingested → Screened (Eligible/Ineligible) → RCS in Progress → Shortlisted → Interview Scheduled → Recommended / Rejected → LOI Issued → Onboarded (`[B]` `BP-M2-TRK-001`).
- **Audit & Version Considerations:** Screening scores, UGC compliance flags, and shortlisting actions tracked in audit log (`[A]` `MOD2-SCR-REQ-05`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

### 4.6 Entity: Recruiter Calling Record (RCS)
- **Domain:** Module II — Preliminary Screening Feedback
- **Purpose:** Captures telephonic screening feedback and candidate qualification verification (`[A]` Baseline `REQ-MOD2-12`, `MOD2-RCS-REQ-01`).
- **Source References:** `REQ-MOD2-12`, `BP-M2-ACAD-007`, `MOD2-RCS-REQ-01` to `06`.
- **Key Business Meaning:** Standardized Recruiter Calling Sheet form capturing current salary, expected salary, notice period, location willingness, communication skills, and recruiter recommendations. Routes candidate dossiers to HOD and HR review for interview shortlisting.
- **Major Relationships:**
  - *Belongs to* Candidate Application Record (`[A]` `REQ-MOD2-12`).
  - *Recorded by* Recruiter User (`[A]` `MOD2-RCS-REQ-02`).
- **Lifecycle Considerations:** Transitions through candidate calling, recruiter feedback capture, and departmental shortlisting for interview scheduling (`[A]` Baseline `BP-M2-ACAD-008`; note: introducing an executive pre-interview management approval gate is a pending governance item under reference `CONF-05` / `CFL-03`).
- **Audit & Version Considerations:** Logged with recruiter identity and submission timestamp (`[A]` `MOD2-RCS-REQ-06`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

### 4.7 Entity: Academic Selection Committee (SCM) Session & Score Record
- **Domain:** Module II — Academic Selection Portal
- **Purpose:** Manages statutory Selection Committee Meetings (SCM) for faculty recruitment (`[A]` Baseline `REQ-MOD2-14`, `MOD2-SCM-REQ-01`).
- **Source References:** `REQ-MOD2-14`, `BP-M2-ACAD-009`/`010`, `MOD2-SCM-REQ-01` to `06`.
- **Key Business Meaning:** Represents the statutory academic evaluation panel. Manages secure digital invitations and time-limited tokens for External Subject Experts. Captures individual evaluator marks across subject knowledge, pedagogy, research, and communication. Auto-compiles the composite Evaluation Matrix for Management final cost approval.
- **Major Relationships:**
  - *Linked to* Candidate Application and Open Position (`[A]` `REQ-MOD2-14`).
  - *Evaluated by* Committee Members (Internal Leadership & External Subject Experts) (`[A]` `MOD2-SCM-REQ-03`).
- **Lifecycle Considerations:** Panel scheduling, mark entry during interview, automatic compilation of the evaluation matrix, and submission to Senior Management for final cost approval (`[A]` Baseline `REQ-MOD2-14`; note: an intermediate HR recommendation review checkpoint is a pending governance item under reference `CONF-06`).
- **Audit & Version Considerations:** Individual scorecards submitted by panelists are permanently locked and immutable (`[A]` `MOD2-SCM-REQ-04`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

### 4.8 Entity: Non-Academic Interview Round & Evaluation Score Record
- **Domain:** Module II — Non-Academic Interview Engine
- **Purpose:** Enforces 3-round sequential evaluations for non-faculty staff (`[A]` Baseline `REQ-MOD2-15`, `MOD2-INT-REQ-01`).
- **Source References:** `REQ-MOD2-15`, `BP-M2-NACAD-006`/`007`, `MOD2-INT-REQ-01` to `06`.
- **Key Business Meaning:** Enforces strict sequential progression: Round 1 (Technical Interview — HOD/Technical Panel) → Round 2 (HR Interview — Head HR) → Round 3 (Management Interview — Senior Leadership). Captures scores for Job Knowledge, Communication, and Attitude.
- **Major Relationships:**
  - *Belongs to* Candidate Application Record (`[A]` `REQ-MOD2-15`).
  - *Evaluated by* Designated Round Panelists (`[A]` `MOD2-INT-REQ-02`).
- **Lifecycle Considerations:** Round 1 (Passed/Failed) → Round 2 (Passed/Failed) → Round 3 (Passed/Failed) → Management Cost Sign-Off (`[A]` Baseline `BP-M2-NACAD-006`).
- **Audit & Version Considerations:** Evaluator identity, score breakdown, and recommendation logged per round (`[A]` `MOD2-INT-REQ-06`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

### 4.9 Entity: Letter of Intent (LOI) & Pre-Onboarding ("Yet to Join") Record
- **Domain:** Module II — Offer Management & Pre-Onboarding
- **Purpose:** Governs formal offer generation, candidate acceptance, and pre-onboarding tracking (`[A]` Baseline `REQ-MOD2-16` to `18`, `MOD2-YTJ-REQ-01`).
- **Source References:** `REQ-MOD2-16` to `18`, `BP-M2-ACAD-011`/`012`, `BP-M2-NACAD-008`, `MOD2-YTJ-REQ-01` to `07`.
- **Key Business Meaning:** Auto-generates Letter of Intent PDF upon Management cost approval. Upon candidate acceptance, flags candidate as "Yet to Join" and triggers pre-onboarding notifications to Deans, HODs, Admin, and IT teams. On Day 1, executes atomic instantiation of Employee Master Record in Module I.
- **Major Relationships:**
  - *Belongs to* Candidate Application Record (`[A]` `REQ-MOD2-16`).
  - *Instantiates* Employee Master Record upon successful onboarding (`[A]` Baseline `BP-XMOD-001`).
- **Lifecycle Considerations:** Offer Generation → Candidate Acceptance (or Decline) → Pre-Onboarding Milestone Tracking → Onboarded (`[A]` Baseline `BP-M2-ACAD-011`/`012`).
- **Audit & Version Considerations:** Candidate acceptance timestamp, document hash, and terms logged (`[A]` `MOD2-YTJ-REQ-06`).
- **Effective-Date Considerations:** Stores scheduled Date of Joining (DOJ).
- **Classification Status:** `[A] Explicit Requirement`.

### 4.10 Entity: Urgent Replacement Tracker
- **Domain:** Module II — Resignation-Triggered Sourcing
- **Purpose:** Monitors urgent faculty or staff replacement workflows (`[A]` Baseline `REQ-MOD2-03`, `MOD2-URG-REQ-01`).
- **Source References:** `REQ-MOD2-03`, `BP-M2-URG-001`, `MOD2-URG-REQ-01` to `06`.
- **Key Business Meaning:** Triggered by accepted resignation in Module I. Starts replacement countdown clock, routes fast-track ad-hoc MRF to HR and Pro-Chancellor, and monitors hiring progress against resignation notice period.
- **Major Relationships:**
  - *Linked to* Resigning Employee ID (`[A]` `BP-XMOD-002`).
  - *Generates* Urgent Replacement MRF (`[A]` `REQ-MOD2-03`).
- **Lifecycle Considerations:** Triggered → Replacement Clock Running → MRF Approved → Candidate Selected → Closed on Day-1 Joining (`[A]` Baseline `BP-M2-URG-001`).
- **Audit & Version Considerations:** Countdown SLA warnings and escalations logged (`[A]` `MOD2-URG-REQ-05`).
- **Effective-Date Considerations:** Aligned with employee notice period.
- **Classification Status:** `[A] Explicit Requirement`.

---

## 5. Module III Conceptual Data Domains & Entities

Module III preserves **three completely independent performance management subsystems**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                           MODULE III: INDEPENDENT SUBSYSTEM TOPOLOGY                             │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ SUBSYSTEM 1: GROUP-D          │ SUBSYSTEM 2: STAFF KRA/KPI     │ SUBSYSTEM 3: FACULTY ECM        │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ • Group-D Form Template       │ • 30-Day Goal Setting Record   │ • Monthly Eligibility Batch     │
│   (Configurable Role KPIs)    │ • Quarterly Reviews (Q1–Q4)    │ • 7-Day Self-Appraisal Dossier  │
│ • Monthly Evaluation Instance │ • Turnaround Time (TAT) Metrics│ • 4-Unit Verification Logs      │
│   (7th/10th Lockout Worker)   │ • Annual Appraisal Outcome     │ • Digital ECM Score Sheets      │
│ • VP-Administration Approval  │   (Direct Handshake to Mod I)  │ • TNU Protocol Matrix Record    │
│ • Annual Collation Report     │                                │ • Management Compensation Dec.  │
│   (12m Weighted Calc + Slabs) │                                │ • Auto-Generated Letters        │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

### 5.1 Subsystem 1: Group-D / Band I Monthly & Annual Appraisal
#### 5.1.1 Entity: Group-D Evaluation Form Template (JSONB Configurable)
- **Domain:** Module III — Subsystem 1 Repository
- **Purpose:** Master repository of role-specific KPI templates for Group-D service roles (`[A]` Baseline `REQ-MOD3-01`, `MOD3-GD-REQ-01`).
- **Source References:** `REQ-MOD3-01` to `03`, `BP-M3-GD-001`, `MOD3-GD-REQ-01` to `03`.
- **Key Business Meaning:** University **Enclosure 1** standardized templates. Configurable by HR to capture role-specific competencies (work quality, attendance, discipline) per designation (`[C]` semi-structured template).
- **Major Relationships:** Owned by HR Team; Instantiates monthly evaluation forms (`[A]` `REQ-MOD3-01`).
- **Lifecycle Considerations:** Draft → Active Version → Superseded (`[B]` `MOD3-GD-REQ-03`).
- **Audit & Version Considerations:** Every schema version update is logged with an immutable audit trail (`[A]` `MOD3-GD-REQ-03`).
- **Effective-Date Considerations:** Version validity dates tracked.
- **Classification Status:** `[A] Explicit Requirement`.

#### 5.1.2 Entity: Group-D Monthly Evaluation Instance
- **Domain:** Module III — Subsystem 1 Monthly Engine
- **Purpose:** Monthly evaluation form completed for each Group-D employee (`[A]` Baseline `REQ-MOD3-01`, `MOD3-GD-REQ-04`).
- **Source References:** `REQ-MOD3-01` to `05`, `BP-M3-GD-002` to `005`, `MOD3-GD-REQ-04` to `13`.
- **Key Business Meaning:** Dispatched on the 1st of every month. Strict submission due date on the 7th; 3-day grace period to the 10th. Auto-locked at 23:59 on the 10th by background worker if unsubmitted (`status = 'NOT_SUBMITTED'`). Requires formal digital sign-off from VP-Administration.
- **Major Relationships:**
  - *Belongs to* Group-D Employee (`[A]` `REQ-MOD3-01`).
  - *Evaluated by* Immediate Supervisor / Reporting Authority with HOD endorsement (`[A]` Baseline `REQ-MOD3-01`, `BP-M3-GD-002`; note: assigning direct online completion exclusively to HODs is a pending governance item under reference `CONF-07` / `CFL-04`).
  - *Approved by* Vice President – Administration (`[A]` `REQ-MOD3-04`).
- **Lifecycle Considerations:** Dispatched (1st) → Pending Supervisor/HOD → Submitted (by 7th/10th) → Pending VP-Administration Approval → Approved (or Auto-Locked Not Submitted) (`[A]` Baseline `BP-M3-GD-002` to `004`).
- **Audit & Version Considerations:** Evaluator scoring, submission timestamps, and VP-Admin approvals logged (`[A]` `MOD3-GD-REQ-13`).
- **Effective-Date Considerations:** Pertains to specific evaluation calendar month.
- **Classification Status:** `[A] Explicit Requirement`.

#### 5.1.3 Entity: Group-D Annual Collation Report
- **Domain:** Module III — Subsystem 1 Annual Review
- **Purpose:** 12-month performance aggregation and compensation revision review (`[A]` Baseline `REQ-MOD3-06`, `MOD3-GD-REQ-14`).
- **Source References:** `REQ-MOD3-06` to `08`, `BP-M3-GD-006` to `008`, `MOD3-GD-REQ-14` to `21`.
- **Key Business Meaning:** Auto-triggered on the 1-year anniversary of Date of Joining (DOJ). Aggregates 12 monthly evaluation reports, computes parameter-weighted average scores (`REQ-TBD-09`), verifies mandatory probation clearance (`REQ-TBD-05`), and records Management compensation slab decisions.
- **Major Relationships:**
  - *Belongs to* Group-D Employee (`[A]` `REQ-MOD3-06`).
  - *Aggregates 12* Monthly Evaluation Instances (`[A]` `REQ-MOD3-06`).
  - *Stores* Senior Management compensation revision decision (`[A]` `REQ-MOD3-08`).
- **Lifecycle Considerations:** Triggered at 12m DOJ → Probation Verified → Management Review → Finalized & Archived to Digital File (`[A]` Baseline `BP-M3-GD-006` to `008`).
- **Audit & Version Considerations:** Calculation inputs and Management slab choices logged (`[A]` `MOD3-GD-REQ-21`).
- **Effective-Date Considerations:** Governs effective date of compensation adjustment.
- **Classification Status:** `[A] Explicit Requirement`.

---

### 5.2 Subsystem 2: General Staff KRA/KPI Lifecycle
#### 5.2.1 Entity: General Staff KRA/KPI Goal Setting Record
- **Domain:** Module III — Subsystem 2 Onboarding
- **Purpose:** Captures and locks performance goals for new staff joiners within 30 days of DOJ (`[A]` Baseline `REQ-MOD3-09`, `MOD3-KRA-REQ-01`).
- **Source References:** `REQ-MOD3-09`, `BP-M3-KRA-001`, `MOD3-KRA-REQ-01` to `04`.
- **Key Business Meaning:** Collaborative goal setting between employee and Reporting Authority within strict 30-day countdown from DOJ. Verified by HR and formally locked by Senior Management.
- **Major Relationships:**
  - *Belongs to* Staff Employee (`[A]` `REQ-MOD3-09`).
  - *Verified by* Supervisor, HR, and Management (`[A]` `MOD3-KRA-REQ-02`).
- **Lifecycle Considerations:** Initiated (on DOJ) → Drafted → Supervisor Verified → HR Verified → Management Locked (within 30 days) (`[A]` Baseline `BP-M3-KRA-001`).
- **Audit & Version Considerations:** Goal definitions and lock timestamps logged (`[A]` `MOD3-KRA-REQ-04`).
- **Effective-Date Considerations:** Applies to annual performance cycle.
- **Classification Status:** `[A] Explicit Requirement`.

#### 5.2.2 Entity: General Staff Quarterly Review Record (Q1–Q4)
- **Domain:** Module III — Subsystem 2 Quarterly Cycle
- **Purpose:** Quarterly review against approved KRAs/KPIs across Q1, Q2, Q3, and Q4 (`[A]` Baseline `REQ-MOD3-10`, `MOD3-KRA-REQ-05`).
- **Source References:** `REQ-MOD3-10` to `12`, `BP-M3-KRA-002` to `004`, `MOD3-KRA-REQ-05` to `14`.
- **Key Business Meaning:** 90-day review cadence; automated submission reminders (`[A]` Baseline `REQ-MOD3-10`; note: exact temporal formula is under clarification under reference `CONF-08`); 15-day employee self-assessment with uploaded evidence; 7-day supervisor verification; HR observation; Management comments.
- **Major Relationships:**
  - *Belongs to* Staff Employee (`[A]` `REQ-MOD3-10`).
  - *Linked to* Goal Setting Record (`[B]` `MOD3-KRA-REQ-05`).
  - *Evaluated by* Supervisor, HR, and Management (`[A]` `MOD3-KRA-REQ-07`).
- **Lifecycle Considerations:** Triggered at 90 days → Employee Submitting (15d) → Supervisor Verification (7d) → HR Review → Management Comments → Completed. Repeats across Q1, Q2, Q3, Q4 (`[A]` Baseline `BP-M3-KRA-002` to `004`).
- **Audit & Version Considerations:** All comments, scores, and evidentiary file links logged (`[A]` `MOD3-KRA-REQ-14`).
- **Effective-Date Considerations:** Pertains to specific quarter (Q1–Q4).
- **Classification Status:** `[A] Explicit Requirement`.

#### 5.2.3 Entity: General Staff Annual Appraisal Outcome
- **Domain:** Module III — Subsystem 2 Handshake
- **Purpose:** Final annual appraisal decision and automatic Module I handshake (`[A]` Baseline `REQ-MOD3-13`, `MOD3-KRA-REQ-15`).
- **Source References:** `REQ-MOD3-13`, `BP-M3-KRA-005`, `MOD3-KRA-REQ-15` to `18`.
- **Key Business Meaning:** Triggered upon completion of Q4. Senior Management reviews the full annual performance portfolio and approves increment, designation change, or promotion. System automatically initializes a Module I Change Request without manual re-entry (`[A]` Baseline `BP-XMOD-004`).
- **Major Relationships:**
  - *Belongs to* Staff Employee (`[A]` `REQ-MOD3-13`).
  - *Synthesizes* Q1–Q4 Quarterly Review Records (`[A]` `MOD3-KRA-REQ-15`).
  - *Directly instantiates* Service Condition Change Request in Module I (`[A]` `REQ-INT-04`).
- **Lifecycle Considerations:** Triggered post-Q4 → Management Review → Approved → Module I Handshake Executed (`[A]` Baseline `BP-M3-KRA-005`).
- **Audit & Version Considerations:** Management decisions and cross-module handshake logged (`[A]` `MOD3-KRA-REQ-18`).
- **Effective-Date Considerations:** Sets effective date for salary/designation modification.
- **Classification Status:** `[A] Explicit Requirement`.

---

### 5.3 Subsystem 3: Faculty Annual Performance Appraisal (ECM Route)
#### 5.3.1 Entity: Faculty Annual Appraisal Eligibility Batch
- **Domain:** Module III — Subsystem 3 Eligibility Scanner
- **Purpose:** Monthly batch scanner identifying eligible faculty for annual ECM review (`[A]` Baseline `REQ-MOD3-14`, `MOD3-FAC-REQ-01`).
- **Source References:** `REQ-MOD3-14` to `15`, `BP-M3-FAC-001` to `002`, `MOD3-FAC-REQ-01` to `05`.
- **Key Business Meaning:** Runs on the 10th of every month. Queries PostgreSQL for faculty matching: `probation_completed = TRUE` and `(current_date - last_appraisal_date) >= 12 months`. Routes eligible roster to Office of the Registrar.
- **Major Relationships:** Aggregates eligible Faculty Employees; Confirmed by Registrar (`[A]` `REQ-MOD3-15`).
- **Lifecycle Considerations:** Scanned (10th) → HR Review → Registrar Roster Confirmation → Auto-Issue of Self-Appraisal Forms (`[A]` Baseline `BP-M3-FAC-001`/`002`).
- **Audit & Version Considerations:** Scanner criteria, execution logs, and Registrar confirmations tracked (`[A]` `MOD3-FAC-REQ-05`).
- **Effective-Date Considerations:** Monthly execution cadence.
- **Classification Status:** `[A] Explicit Requirement`.

#### 5.3.2 Entity: Faculty Self-Appraisal Dossier & Multi-Unit Verification Record
- **Domain:** Module III — Subsystem 3 Verification Workflow
- **Purpose:** Captures self-appraisal submissions, evidence, and parallel multi-departmental verifications (`[A]` Baseline `REQ-MOD3-16`, `MOD3-FAC-REQ-06`).
- **Source References:** `REQ-MOD3-16` to `17`, `BP-M3-FAC-003` to `005`, `MOD3-FAC-REQ-06` to `13`.
- **Key Business Meaning:** 7 working days submission deadline with daily reminders. Routes in parallel to exactly 4 verification units: School Dean (academic), R&D Cell (research), Placement Cell (industry linkage), HR Department (compliance) (`[A]` Baseline `REQ-MOD3-17`, `BP-M3-FAC-004`; note: configurable dynamic routing for additional stakeholders is a pending governance item under reference `CONF-09`). Handles discrepancy flagging and resubmission tracking.
- **Major Relationships:**
  - *Belongs to* Faculty Employee (`[A]` `REQ-MOD3-16`).
  - *Verified by* School Dean, R&D Cell, Placement Cell, HR Department (`[A]` `REQ-MOD3-17`).
- **Lifecycle Considerations:** Issued → In Progress (7d) → Submitted → Multi-Unit Verification → Verified (Ready for ECM) / Discrepancy Returned (`[A]` Baseline `BP-M3-FAC-003` to `005`).
- **Audit & Version Considerations:** All verification findings, discrepancy notes, and resubmissions tracked (`[A]` `MOD3-FAC-REQ-13`).
- **Effective-Date Considerations:** N/A.
- **Classification Status:** `[A] Explicit Requirement`.

#### 5.3.3 Entity: Faculty ECM Session & TNU Protocol Evaluation Matrix Record
- **Domain:** Module III — Subsystem 3 Evaluation Matrix & Decision
- **Purpose:** Committee meeting evaluations, TNU Protocol Matrix synthesis, and compensation decisions (`[A]` Baseline `REQ-MOD3-18`, `MOD3-FAC-REQ-14`).
- **Source References:** `REQ-MOD3-18` to `20`, `BP-M3-FAC-006` to `008`, `MOD3-FAC-REQ-14` to `22`.
- **Key Business Meaning:** Scheduled by Registrar. Evaluation Committee Meeting (ECM) members enter digital score sheets during session. System synthesizes scores, past increment history, and TNU Protocol parameters into the composite Evaluation Matrix. Senior Management records final compensation decision (annual increment, accelerated increment, promotion) (`[A]` Baseline `REQ-MOD3-19`, `BP-M3-FAC-008`; note: expanding formal outcomes to include PIP, Reprimand, and Probation Extension is a pending governance item under reference `CONF-10`). System auto-generates outcome letters and triggers Module I handshake.
- **Major Relationships:**
  - *References* Faculty Dossier (`[A]` `REQ-MOD3-18`).
  - *Evaluated by* ECM Committee Members (`[A]` `MOD3-FAC-REQ-15`).
  - *Decided by* Senior Management (`[A]` `REQ-MOD3-19`).
  - *Creates* Service Condition Change Request in Module I (`[A]` `BP-XMOD-004`).
- **Lifecycle Considerations:** Scheduled by Registrar → Meeting in Session (Digital Scoring) → Matrix Compiled → Management Decision → Letters Generated & Handshake Executed (`[A]` Baseline `BP-M3-FAC-006` to `008`).
- **Audit & Version Considerations:** Individual evaluator marks and Management decisions are immutable once committed (`[A]` `MOD3-FAC-REQ-22`).
- **Effective-Date Considerations:** Governs salary revision effective date (next applicable salary cycle).
- **Classification Status:** `[A] Explicit Requirement`.

---

## 6. Shared Platform Conceptual Data Domains & Entities

Shared platform entities provide cross-cutting capabilities across all modules:

### 6.1 Entity: User Account & Authentication Credential Profile
- **Domain:** Shared Services — Identity & Access Management (IAM)
- **Purpose:** Manages authentication credentials, sessions, and security policies (`[B]` `REQ-SEC-01`, `SHR-AUT-REQ-01`).
- **Source References:** `REQ-SEC-01`, `REQ-SEC-02`, `SHR-AUT-REQ-01` to `04`.
- **Key Business Meaning:** Manages user identity, secure password hashing, login lockout counters, session validity, and single-use magic tokens for external statutory SCM experts (`[A]` `SHR-AUT-REQ-03`).
- **Classification Status:** `[B] Derived Requirement`.

### 6.2 Entity: Role & Permission Assignment
- **Domain:** Shared Services — Role-Based Access Control (RBAC)
- **Purpose:** Enforces fine-grained permissions and contextual row-level data scoping (`[B]` `REQ-SEC-03`, `SHR-RBC-REQ-01`).
- **Source References:** `REQ-SEC-03`, `SHR-RBC-REQ-01` to `02`.
- **Key Business Meaning:** Maps roles (Pro-Chancellor, Management, Deans, HODs, HR, Committee Members, Staff) to permissions. Enforces row-level scoping (e.g., HOD restricted to department, Dean to school).
- **Classification Status:** `[B] Derived Requirement`.

### 6.3 Entity: Workflow State Instance & Transition Log
- **Domain:** Shared Services — Universal Workflow Engine
- **Purpose:** Finite State Machine (FSM) instance tracking across all approval workflows (`[B]` `REQ-MOD1-06`, `SHR-WFL-REQ-01`).
- **Source References:** `REQ-MOD1-06`, `REQ-MOD2-14`, `REQ-MOD3-04`, `SHR-WFL-REQ-01` to `03`.
- **Key Business Meaning:** Standardized engine tracking current state, prior state, acting user, transition guards, and mandatory comments across change requests, requisitions, and appraisals.
- **Classification Status:** `[B] Derived Requirement`.

### 6.4 Entity: SLA & Deadline Timer Record
- **Domain:** Shared Services — SLA & Timeline Management
- **Purpose:** Tracks deadlines, countdown timers, grace periods, and automated lockouts (`[B]` `REQ-MOD3-02`, `SHR-SLA-REQ-01`).
- **Source References:** `REQ-MOD3-02`, `REQ-MOD2-02`, `SHR-SLA-REQ-01` to `03`.
- **Key Business Meaning:** Powers automated background monitoring for 4-month planning triggers, 15-day submission windows, 7-day turnaround SLAs, and 7th/10th auto-locks.
- **Classification Status:** `[B] Derived Requirement`.

### 6.5 Entity: Document Metadata & Binary Reference
- **Domain:** Shared Services — Document Management
- **Purpose:** Abstracted pointer to binary files stored in Object Storage (`[C]` `REQ-MOD1-03`, `SHR-DOC-REQ-01`).
- **Source References:** `REQ-MOD1-03`, `REQ-MOD2-12`, `REQ-MOD3-16`, `SHR-DOC-REQ-01` to `03`.
- **Key Business Meaning:** Stores object keys, MIME types, file sizes, and SHA-256 hashes for CVs, certificates, evidence files, and generated PDF letters.
- **Classification Status:** `[C] Approved Technical Decision`.

### 6.6 Entity: Notification Queue & Dispatch Record
- **Domain:** Shared Services — Multi-Channel Notifications
- **Purpose:** Asynchronous delivery tracking for emails and in-app alerts (`[B]` `REQ-MOD3-02`, `SHR-NTF-REQ-01`).
- **Source References:** `REQ-MOD3-02`, `REQ-MOD2-18`, `SHR-NTF-REQ-01` to `03`.
- **Key Business Meaning:** Captures message templates, recipient addresses, delivery status (`PENDING`, `SENT`, `FAILED`), retry attempts, and dispatch timestamps.
- **Classification Status:** `[B] Derived Requirement`.

### 6.7 Entity: Immutable Audit Trail Entry
- **Domain:** Shared Services — Security & Governance Auditing
- **Purpose:** Append-only audit trail capturing full before/after state diffs (`[A]` Baseline `REQ-MOD1-08`, `REQ-SEC-04`).
- **Source References:** `REQ-MOD1-08`, `REQ-SEC-04`, `MOD1-AUD-REQ-01` to `06`.
- **Key Business Meaning:** Tamper-evident ledger recording actor ID, timestamp, IP, entity name, entity ID, pre-state data, and post-state data.
- **Classification Status:** `[A] Explicit Requirement`.

### 6.8 Entity: ERP Transactional Outbox Staging Record
- **Domain:** Shared Services — ERP Integration
- **Purpose:** Transactional outbox staging table for reliable external ERP synchronization (`[C]` `REQ-MOD1-04`, `REQ-INT-01`).
- **Source References:** `REQ-MOD1-04`, `REQ-INT-01`, `MOD1-CDB-REQ-03`, `TECHNOLOGY_ARCHITECTURE_BASELINE.md` Section 7 & 12.
- **Key Business Meaning:** Atomic staging of approved master data deltas to guarantee zero message loss during external network or ERP downtime.
- **Classification Status:** `[C] Approved Technical Decision`.

---

## 7. Consolidated Data Model TBD Register

The official requirements baseline establishes **exactly eleven (11) controlled TBD items** (`REQ-TBD-01` through `REQ-TBD-11`), documented in [`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md). 

The following register identifies their direct architectural impact on database modeling:

| TBD ID | Topic / Scope | Affected Conceptual Entity | Open Data Decision / Policy Item | Decision Owner |
|---|---|---|---|---|
| **`REQ-TBD-01`** | ERP Synchronization Protocol | `ERP Transactional Outbox Staging Record` | Technical integration transport: Database staging table vs. REST API webhooks vs. SFTP batch flat-files. | University IT / ERP Lead |
| **`REQ-TBD-02`** | Standardized Attachment Schemas | `Academic Manpower Plan`, `Group-D Template`, `Faculty Dossier` | Field-level parameter templates for Attachment 1 (Teaching Load), Enclosure 1 (Group-D KPIs), and Enclosure 1 (Faculty Self-Appraisal). | Head HR / Deans Committee |
| **`REQ-TBD-03`** | Staff Appraisal Track Boundaries | `Group-D Monthly Evaluation`, `Staff Quarterly Review` | Allocation of mid-level technical staff (Lab Technicians, Technical Assistants, Teaching Associates) between appraisal tracks. | Registrar / Head HR |
| **`REQ-TBD-04`** | TNU Protocol Parameter Weights | `Faculty ECM Session & TNU Protocol Matrix` | Mathematical scoring weights and percentage allocations across teaching, research, placement, and institutional service. | Academic Council / Registrar |
| **`REQ-TBD-05`** | Pre-Defined Compensation Slabs | `Group-D Annual Collation Report`, `Faculty ECM Record` | Quantitative monetary brackets and percentage revision slabs for annual compensation decisions. | Senior Management / Finance |
| **`REQ-TBD-06`** | Resignation Intake Interface | `Urgent Replacement Tracker`, `Employee Master Record` | Upstream resignation intake mechanism in Module I: Employee self-service submission vs. Dean/HR administrative entry. | Head HR / Deans |
| **`REQ-TBD-07`** | Enterprise SSO & Expert Access | `User Account & Credential Profile` | University Identity Provider (Google Workspace, Microsoft Entra, LDAP) and secure token delivery format for external SCM experts. | University IT / Security |
| **`REQ-TBD-08`** | LOI vs. Appointment Letter | `Letter of Intent (LOI) Record` | Contractual boundary: Whether LOI is the sole pre-joining instrument or if a distinct formal Appointment Letter is generated post-joining. | HR Department / Legal |
| **`REQ-TBD-09`** | Administrative Allowances | `Employee Master Record`, `Service History Ledger` | Financial allowance and honorarium rules for secondary administrative roles (Dean, HOD, Proctor, Warden). | HR Leadership / Finance |
| **`REQ-TBD-10`** | Outbound Communication Gateways | `Notification Queue & Dispatch Record` | Host configurations, SMTP relays, and SMS/WhatsApp gateway credentials for automated reminders. | University Systems Admin |
| **`REQ-TBD-11`** | Document Retention Schedules | `Immutable Audit Trail Entry`, `Document Metadata` | Statutory retention schedules (in years) for candidate CVs, SCM scorecards, and historical service change logs. | Registrar / Legal Counsel |

> **Informational Governance Note on Provisional Review Items:**  
> The post-release stakeholder delta review (`docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md`) identified 9 additional candidate TBDs (`REQ-TBD-12` through `REQ-TBD-20`, covering multi-change concurrency, withdrawal rules, rejection reason taxonomies, pre-onboarding milestones, PIP tracking, reprimands, probation extensions, and auto-lockout reasons). In accordance with project governance, these remain provisional candidate items subject to formal leadership sign-off on the Decision Sheet (`10-STAKEHOLDER-DECISION-SHEET.md`), and do not alter the frozen 11-TBD baseline.

---

## 8. Conceptual Data Model Summary & Traceability

The conceptual data model establishes **33 primary conceptual entities** partitioned across 4 functional domains, with complete backward traceability:

| Domain | Total Entities | Explicit Requirements `[A]` | Derived Requirements `[B]` | Approved Technical `[C]` |
|---|---|---|---|---|
| **Module I: Change Management** | 6 Entities | 6 | 0 | 0 |
| **Module II: Recruitment & Selection** | 10 Entities | 10 | 0 | 0 |
| **Module III: Performance Management** | 9 Entities | 9 | 0 | 0 |
| **Shared Platform Infrastructure** | 8 Entities | 1 | 5 | 2 |
| **Total Conceptual Entities** | **33 Entities** | **26 `[A]`** | **5 `[B]`** | **2 `[C]`** |

> **Analytical Inventory Statement:**  
> The identified conceptual entity count (33 primary conceptual entities) is an analytical data-domain inventory and does not represent the final number of physical PostgreSQL tables. Physical tables, junction tables, and audit ledgers will be derived during the logical schema specification phase.

---
*End of Document — Conceptual Data Model Overview.*
