# Master Business Process Index
## University HR Change Management & Automation System

**Document Identifier:** `DOC-02-BPI-00`  
**Phase:** Phase 2 — Business Process Documentation (Documentation-Only)  
**Location:** `docs/02-business-process/00-BUSINESS-PROCESS-INDEX.md`  
**Status:** Approved Business Process Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Purpose

This Master Business Process Index establishes the definitive inventory, architectural framing, and navigation structure for Phase 2 (Business Process Documentation) of the University HR Change Management & Automation System. 

The primary objective of Business Process Documentation is to describe **how the institution's human resource processes operate from a business and operational perspective**:
- What events trigger each process.
- Which institutional actors and authorities participate.
- What business data, documentation, and statutory enclosures enter each workflow.
- What operational activities and evaluations occur.
- What decision gates and approval points are enforced.
- What physical and digital outputs are generated.
- What operational timelines, turnaround times (TAT), and Service Level Agreements (SLAs) apply.
- How exceptions, non-compliance conditions, and discrepancy loops are resolved.
- How processes interface and transfer responsibility across Module I, Module II, and Module III.

> [!IMPORTANT]
> **Business-Level Focus & Technology Independence:**  
> This documentation layer defines **institutional business operations**, independent of underlying software technologies, database schemas, or communication protocols. Detailed technical execution workflows, state machines, API interactions, and event schemas will be formally documented during subsequent engineering phases (specifically **Phase 6 — Workflow Documentation** under `docs/06-workflows/`). The Phase 6 workflow documentation has **NOT** been started and is **NOT** claimed to be complete.

---

## 2. Authoritative Source Hierarchy

All business processes documented herein strictly derive from the approved project baseline in the following order of legal and operational authority:

1. **Original Official Requirement PDFs** (`source-requirements/`):
   - *Module I — HR Change Management & Automation System* (`source-requirements/27-07-26 - Revised HR Change Management & Automation System-Module I.pdf`)
   - *Module II — Recruitment & Selection Automation System* (`source-requirements/Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf`)
   - *Module III — Performance Management Automation System* (`source-requirements/Requirement_Brief_Module_III_Performance_Management_Automation_System.pdf`)
2. **Project Requirements Analysis Baseline** ([`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md))
3. **Formal Requirements Documentation** ([`docs/01-requirements/`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/))
4. **Functional Requirements Documentation** ([`docs/03-functional-requirements/`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/))
5. **Technology Architecture Baseline** ([`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md))
6. **Architecture Decision Records** ([`docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md))

---

## 3. Relationship to Other Documentation Phases

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               DOCUMENTATION LIFECYCLE RELATIONSHIP                               │
├────────────────────────────────┬────────────────────────────────┬────────────────────────────────┤
│ 1. REQUIREMENTS (PHASE 1)      │ 2. BUSINESS PROCESSES (PHASE 2)│ 3. FUNCTIONAL REQS (PHASE 3)   │
│ docs/01-requirements/          │ docs/02-business-process/      │ docs/03-functional-reqs/       │
├────────────────────────────────┼────────────────────────────────┼────────────────────────────────┤
│ • What the business needs      │ • How the institution operates │ • Detailed system capabilities │
│ • Source requirement catalogue │ • Triggers, actors, activities │ • Field-level requirements     │
│ • Traceability & TBD log       │ • Approvals, SLAs, handoffs    │ • UI/Validation constraints    │
│ • Classification [A] through [E│ • Pure business logic          │ • Functional traceability      │
│ [STATUS: COMPLETE]             │ [STATUS: ACTIVE PHASE]         │ [STATUS: COMPLETE]             │
├────────────────────────────────┴────────────────────────────────┴────────────────────────────────┤
│                                                │                                                 │
│                                                ▼                                                 │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 6. TECHNICAL WORKFLOWS (PHASE 6 — FUTURE DEPENDENCY)                                             │
│ docs/06-workflows/                                                                              │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ • Technical state machine specifications, state transition tables, and rollback mechanics        │
│ • Concrete REST API triggers, Socket.IO invalidation hooks, and background worker job execution  │
│ [STATUS: PENDING — NOT STARTED]                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Phase 2 Document Suite Structure

The Phase 2 Business Process documentation suite comprises nine (9) comprehensive, cross-referenced documents maintained strictly within `docs/02-business-process/`:

| Document File | Document Title | Primary Scope & Business Coverage |
|---|---|---|
| [`00-BUSINESS-PROCESS-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/00-BUSINESS-PROCESS-INDEX.md) | **Master Business Process Index** | Master directory, architectural framing, process inventory, and lifecycle relationships. |
| [`01-BUSINESS-PROCESS-FRAMEWORK.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-FRAMEWORK.md) | **Business Process Framework** | Standardized process model, actor matrix, lifecycle stages, and documentation template. |
| [`02-MODULE-I-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-MODULE-I-BUSINESS-PROCESSES.md) | **Module I Business Processes** | Core Database, Dynamic Org Chart, Dossier, 10 Service Changes, 2-Level Approvals, Effective Dates, Audit, ERP. |
| [`03-MODULE-II-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/03-MODULE-II-BUSINESS-PROCESSES.md) | **Module II Business Processes** | Academic Manpower Planning, Non-Academic Planning, Urgent Replacement, Sourcing, Screening, SCM, 3-Round, LOI, Trackers. |
| [`04-MODULE-III-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/04-MODULE-III-BUSINESS-PROCESSES.md) | **Module III Business Processes** | Group-D 10th Lockout & Annual Review, General Staff KRA/KPI Quarterly Cadence, Faculty ECM Appraisal Route. |
| [`05-CROSS-MODULE-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/05-CROSS-MODULE-BUSINESS-PROCESSES.md) | **Cross-Module Business Processes** | Recruitment-to-Core DB, Resignation-to-Replacement, Master Data-to-Appraisal, Appraisal-to-Change Request handoffs. |
| [`06-BUSINESS-RULES-AND-DECISION-POINTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/06-BUSINESS-RULES-AND-DECISION-POINTS.md) | **Business Rules & Decision Points** | Consolidated, categorized inventory of all operational rules, validation gates, and decision trees. |
| [`07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md) | **Business SLA & Escalation Model** | Institutional deadlines, turnaround commitments, reminder schedules, and non-compliance escalations. |
| [`08-BUSINESS-PROCESS-QUALITY-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/08-BUSINESS-PROCESS-QUALITY-REVIEW.md) | **Business Process Quality Review** | Formal verification against source PDFs, anti-invention check, traceability matrix, and readiness certification. |

---

## 5. Master Inventory of Documented Business Processes

The Phase 2 documentation details **59 discrete institutional business processes** mapped directly to the authoritative requirement catalogue:

### 5.1 Module I — HR Change Management & Core DB (10 Processes)
- `BP-M1-001`: Central Employee Database Management & Master Record Maintenance (`REQ-MOD1-01`, `REQ-ENT-01`)
- `BP-M1-002`: Dynamic Organization Structure Realignment & Hierarchy Maintenance (`REQ-MOD1-02`, `REQ-MOD1-03`, `REQ-MOD1-04`)
- `BP-M1-003`: Digital Employee File / Longitudinal Dossier Maintenance (`REQ-MOD1-05`)
- `BP-M1-004`: Employee Service Change Request Initiation (10 Standardized Formats) (`REQ-MOD1-06` to `REQ-MOD1-16`)
- `BP-M1-005`: Two-Level Approval Hierarchy — Level 1: HR Review & Vetting (`REQ-MOD1-17`)
- `BP-M1-006`: Two-Level Approval Hierarchy — Level 2: Senior Management Final Approval (`REQ-MOD1-17`)
- `BP-M1-007`: Effective-Date Scheduling & Master Activation Processing (`REQ-MOD1-18`, `REQ-MOD1-19`)
- `BP-M1-008`: Service Record Audit Trail Logging & Version History Maintenance (`REQ-AUD-01`, `REQ-AUD-02`)
- `BP-M1-009`: University Enterprise Resource Planning (ERP) Master Synchronization (`REQ-EXT-01`, `REQ-EXT-02`, `REQ-EXT-03`)
- `BP-M1-010`: Real-Time HR Operational & Statutory Compliance Reporting (`REQ-REP-01`, `REQ-REP-02`, `REQ-REP-09`)

### 5.2 Module II — Recruitment & Selection Automation System (22 Processes)

#### Academic Recruitment Track (Faculty & Laboratory Technicians)
- `BP-M2-ACAD-001`: Academic Manpower Planning Advance Initiation (>= 4 Months Prior) (`REQ-MOD2-02`, `REQ-SLA-01`)
- `BP-M2-ACAD-002`: Academic Requirement Submission & Teaching Load Calculation (15 Days) (`REQ-MOD2-03`, `REQ-SLA-02`)
- `BP-M2-ACAD-003`: Academic Teaching Load Vetting & Manpower Consolidation (3 Months) (`REQ-MOD2-04`)
- `BP-M2-ACAD-004`: Academic Consolidated Approval Gate — Pro-Chancellor Turnaround (7 Days) (`REQ-MOD2-05`, `REQ-SLA-03`)
- `BP-M2-ACAD-005`: Academic Recruitment Advertisement Launch (7 Days Post-Approval) (`REQ-MOD2-06`, `REQ-SLA-04`)
- `BP-M2-ACAD-006`: Academic Multi-Channel Sourcing & CV Intake (`REQ-MOD2-11`)
- `BP-M2-ACAD-007`: Academic CV Segregation, Classification & UGC Norms Compliance (`REQ-MOD2-12`)
- `BP-M2-ACAD-008`: Academic Recruiter Calling Stage (RCS) & Pre-Interview Management Gate (`REQ-MOD2-13`, `REQ-MOD2-14`)
- `BP-M2-ACAD-009`: Statutory Selection Committee Meeting (SCM) & External Expert Participation (`REQ-MOD2-15`, `REQ-EXT-05`)
- `BP-M2-ACAD-010`: Academic Digital Scoring & Selection Matrix Compilation (`REQ-MOD2-16`)
- `BP-M2-ACAD-011`: Academic Letter of Intent (LOI) Generation & Issuance (`REQ-MOD2-19`, `REQ-DOC-04`)
- `BP-M2-ACAD-012`: Academic "Yet to Join" Tracking & Pre-Onboarding Countdown (`REQ-MOD2-20`, `REQ-REP-04`)

#### Non-Academic Recruitment Track (Administrative & Support Staff)
- `BP-M2-NACAD-001`: Non-Academic Manpower Planning Advance Initiation (>= 4 Months Prior) (`REQ-MOD2-07`)
- `BP-M2-NACAD-002`: Non-Academic Annual Requisition Restriction (Strict 1 Planned MRF/Dept/Year) (`REQ-MOD2-07`)
- `BP-M2-NACAD-003`: Non-Academic Requirement Vetting, Consolidation & Approval Gate (`REQ-MOD2-07`)
- `BP-M2-NACAD-004`: Non-Academic Recruitment Launch & Sourcing Window (`REQ-MOD2-07`, `REQ-MOD2-11`)
- `BP-M2-NACAD-005`: Non-Academic CV Screening & RCS Pre-Interview Gate (`REQ-MOD2-12`, `REQ-MOD2-13`, `REQ-MOD2-14`)
- `BP-M2-NACAD-006`: Non-Academic Three-Round Sequential Selection (Technical, HR, Management) (`REQ-MOD2-17`, `REQ-MOD2-18`)
- `BP-M2-NACAD-007`: Non-Academic Selection Decision, LOI Generation & Pre-Onboarding (`REQ-MOD2-19`, `REQ-MOD2-20`)

#### Urgent Replacement Track & Sourcing Infrastructure
- `BP-M2-URG-001`: Urgent Replacement Recruitment Initiation (Resignation Trigger & Ad-Hoc MRF) (`REQ-MOD2-08`, `REQ-MOD2-09`)
- `BP-M2-TRK-001`: Central CV Database Ingestion, Profile Management & Deduplication (`REQ-MOD2-11`)
- `BP-M2-TRK-002`: Open Positions Tracker Maintenance & Weekly Executive Briefing (`REQ-MOD2-10`, `REQ-REP-03`)

### 5.3 Module III — Performance Management Automation System (22 Processes)

#### Subsystem 1: Group-D / Band-I Support Staff Performance Process
- `BP-M3-GD-001`: Monthly Evaluation Form Dispatch & HOD Assignment (`REQ-MOD3-01`)
- `BP-M3-GD-002`: Monthly Evaluation Submission Window & Grace Period (Due 7th, Grace to 10th) (`REQ-MOD3-02`, `REQ-MOD3-03`, `REQ-SLA-05`, `REQ-SLA-06`)
- `BP-M3-GD-003`: 10th-of-Month Auto-Lockout Enforcement & Non-Compliance Flagging (`REQ-MOD3-04`, `REQ-REP-07`)
- `BP-M3-GD-004`: Executive Approval Gateway — Vice President – Administration Sign-Off (`REQ-MOD3-05`)
- `BP-M3-GD-005`: Monthly Evaluation Collation & HR Performance Report Generation (`REQ-MOD3-06`, `REQ-REP-05`)
- `BP-M3-GD-006`: Group-D Annual Evaluation Trigger & 12-Month Score Aggregation (`REQ-MOD3-07`, `REQ-MOD3-08`, `REQ-REP-06`)
- `BP-M3-GD-007`: Mandatory Probation Verification Gate for Support Staff (`REQ-MOD3-09`)
- `BP-M3-GD-008`: Support Staff Annual Compensation Review & Outcome Archiving (`REQ-MOD3-09`, `REQ-DOC-03`)

#### Subsystem 2: General Staff KRA/KPI Appraisal Cycle
- `BP-M3-KRA-001`: Onboarding Goal Setting & Joint Locking Window (30 Days from DOJ) (`REQ-MOD3-10`, `REQ-MOD3-11`, `REQ-SLA-07`, `REQ-AUD-04`)
- `BP-M3-KRA-002`: Quarterly Review Cycle Initiation & Milestone Scheduling (Q1–Q4) (`REQ-MOD3-12`, `REQ-SLA-08`)
- `BP-M3-KRA-003`: Quarterly Self-Review Submission & Supervisor Verification (15 Days / 7 Days) (`REQ-MOD3-12`, `REQ-SLA-08`)
- `BP-M3-KRA-004`: Quarterly HR Compliance Observations & Management Executive Review (`REQ-MOD3-12`)
- `BP-M3-KRA-005`: Annual KRA/KPI Appraisal Consolidation & Module I Direct Handshake (`REQ-MOD3-13`)

#### Subsystem 3: Faculty Annual Performance Appraisal (ECM Route)
- `BP-M3-FAC-001`: Monthly Faculty Appraisal Eligibility Identification (10th-of-Month Scanner) (`REQ-MOD3-14`, `REQ-REP-08`)
- `BP-M3-FAC-002`: Eligible Faculty List Generation & Registrar Routing (`REQ-MOD3-14`)
- `BP-M3-FAC-003`: Faculty Self-Appraisal Form Issuance & Submission Window (7 Working Days) (`REQ-MOD3-15`, `REQ-SLA-09`)
- `BP-M3-FAC-004`: Multi-Departmental Parallel Verification Workflow (Dean, R&D, Placement, HR) (`REQ-MOD3-16`)
- `BP-M3-FAC-005`: Circular Discrepancy Flagging & Resubmission Review Loop (`REQ-MOD3-16`)
- `BP-M3-FAC-006`: Evaluation Committee Meeting (ECM) Scheduling & Digital Score Entry (`REQ-MOD3-17`)
- `BP-M3-FAC-007`: TNU Protocol Evaluation Matrix Compilation & Synthesis (`REQ-MOD3-18`, `REQ-DOC-03`)
- `BP-M3-FAC-008`: Management Decision & Salary Cycle Implementation Tracking (`REQ-MOD3-19`)
- `BP-M3-FAC-009`: Automated Compensation Revision Letter Generation & Digital Dossier Archiving (`REQ-MOD3-19`, `REQ-DOC-05`)

### 5.4 Cross-Module Integration Processes (5 Processes)
- `BP-XMOD-001`: Recruitment-to-Central Employee Database Handshake (`REQ-INT-01`)
- `BP-XMOD-002`: Dean Resignation Acceptance to Urgent Replacement Trigger (`REQ-INT-02`)
- `BP-XMOD-003`: Central Employee Master Data & Hierarchy Feed to Performance Subsystems (`REQ-INT-03`)
- `BP-XMOD-004`: Approved Annual Performance Appraisal Handshake to Module I Change Request (`REQ-INT-04`)
- `BP-XMOD-005`: Dynamic Organizational Realignment Feed to Active Performance Review Routing (`REQ-MOD1-03`, `REQ-INT-03`)

---

## 6. Classification Scheme

Every business process, decision point, and operational rule is tagged with the project's standard classification scheme:

- **`[A] Explicit Requirement`:** Operational rule, actor role, timeline, or workflow gate directly mandated by the official source requirement briefs.
- **`[B] Logical Implication`:** Necessary operational or process relationship required to execute an explicit requirement without breaking business continuity.
- **`[C] Approved Technical Decision`:** Approved platform capability or architectural decision established in [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md). *(Note: Used strictly to denote approved technical capabilities; never used to convert technical architecture into an artificial business rule).*
- **`[D] Proposed Detail`:** Proposed operational engineering threshold or administrative convention awaiting official University confirmation.
- **`[E] TBD / Open Decision`:** Unresolved institutional policy, missing physical template schema, or external interface specification formally logged in [`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md).

---

## 7. Documentation Governance & Compliance Confirmation

1. **No Code / Schema Generation:** Zero application code, zero SQL scripts, zero database schemas, zero API DTOs, and zero UI component code were created in this phase.
2. **Strict Module Separation:**
   - Academic and Non-Academic recruitment tracks are maintained as completely distinct business processes.
   - The three Module III performance subsystems (Group-D, Staff KRA/KPI, Faculty ECM) are maintained as completely distinct business processes.
3. **Anti-Invention Adherence:** No scoring weights, monetary compensation brackets, committee quorums, resignation intake channels, or unauthorized approval tiers have been invented.
4. **Separation of Business Deadlines and Technical Scheduling:** All institutional deadlines (e.g., 7th of the month, 10th-of-month lockout) are documented as business policy rules, completely decoupled from technical cron execution parameters.
5. **Phase Status:** **Phase 2 — Business Process Documentation is COMPLETE and READY FOR REVIEW.** Phase 6 (Detailed Workflows) remains pending.

---
*End of Document — Master Business Process Index.*
