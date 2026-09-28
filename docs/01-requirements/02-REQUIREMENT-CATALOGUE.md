# Comprehensive Requirement Catalogue
## University HR Change Management & Automation System

**Document Identifier:** `DOC-01-CAT-02`  
**Phase:** Phase 1 — Requirements Engineering & Specification (Documentation-Only)  
**Location:** `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`  
**Status:** Approved Requirement Catalogue Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Document Overview

This catalogue presents the structured, itemized inventory of all business, functional, and architectural requirements governing the University HR Change Management & Automation System. 

### Classification Governance
Every requirement in this catalogue is tagged with its official classification marker:
- **`[A] Explicit Requirement`:** Directly stated in the official source briefs.
- **`[B] Logical Implication`:** Operationally or mathematically necessary to execute an explicit requirement.
- **`[C] Approved Technical Decision`:** Approved as part of the technical architecture baseline.
- **`[D] Proposed Detail`:** Proposed operational engineering threshold awaiting official university policy confirmation.
- **`[E] TBD / Open Decision`:** Unresolved policy, schema, or integration detail requiring formal institutional decision.

> [!IMPORTANT]
> **Priority Policy:** In strict compliance with enterprise documentation standards, priority columns are populated **ONLY** where the authoritative source documents explicitly establish a priority. Subjective priorities (such as generic High/Medium/Low) are not invented.

---

## Section A: Enterprise / Common Requirements

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-ENT-01` | `SHR-CDB-REQ-01` | The system shall provide a single, centralized database representing the authoritative single source of truth for all employee service records. | Enterprise / Shared | `[A]` | Module I, Background & Structure (1) | None | Core master data primitive. |
| `REQ-ENT-02` | `SHR-CDB-REQ-02` | The system shall eliminate duplicate data entry by ensuring any approved change or milestone automatically updates all connected records. | Enterprise / Shared | `[A]` | Module I, Background & Objective | `REQ-ENT-01` | Cross-module propagation rule. |
| `REQ-ENT-03` | `SHR-AUT-REQ-01` | The system shall enforce role-based authentication and granular authorization across all administrative, academic, and executive users. | Enterprise / Security | `[B]` | Universal Baseline | None | RBAC boundary enforcement. Identity Provider protocol is `[E] TBD`. |
| `REQ-ENT-04` | `SHR-CMN-REQ-01` | All system timestamps shall be stored in UTC with display rendering in Local University Time (IST). Date formatting shall adhere to standard academic conventions. | Enterprise / Shared | `[B]` | Universal Baseline | None | Prevents timezone drift across semester triggers. |
| `REQ-ENT-05` | `SHR-CMN-REQ-02` | Master records, transaction histories, and evaluations shall never be physically deleted; records shall utilize soft deletion with complete audit trails. | Enterprise / Shared | `[B]` | Universal Baseline | None | Preserves historical audit integrity. |
| `REQ-ENT-06` | `SHR-CMN-REQ-03` | All workflow state transition operations shall be idempotent, preventing duplicate approvals or double-execution of financial compensation changes. | Enterprise / Shared | `[B]` | Universal Baseline | None | Guard against duplicate network requests. |

---

## Section B: Module I — HR Change Management & Core DB

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-MOD1-01` | `MOD1-CDB-01` / `MOD1-CDB-REQ-01` | The system shall maintain an authoritative Central Database of all Employees containing complete service, personal, academic, and structural profiles. | Module I | `[A]` | Module I Brief, Structure (1) | `REQ-ENT-01` | Master relational record. |
| `REQ-MOD1-02` | `MOD1-ORG-01` / `MOD1-ORG-REQ-01` | The system shall maintain a dynamic Organization Chart directly connected to the Central Employee Database. | Module I | `[A]` | Module I Brief, Structure (2) | `REQ-MOD1-01` | Real-time hierarchical visual structure. |
| `REQ-MOD1-03` | `MOD1-ORG-02` / `MOD1-ORG-REQ-02` | The Organization Chart shall automatically realign its visual and structural hierarchy whenever changes in designations, reportees, reporting authorities, or departments are approved. | Module I | `[A]` | Module I Brief, Structure (2) | `REQ-MOD1-02` | Automated hierarchy recalculation. |
| `REQ-MOD1-04` | `MOD1-ORG-REQ-04` | The organizational hierarchy shall render with high performance and sub-second responsiveness, ensuring immediate, real-time reflection across visual tree structures upon any approved change. | Module I | `[B]` | Derived from Structure (2) | `REQ-MOD1-03` | Caching architecture governed by approved technical baseline. |
| `REQ-MOD1-05` | `MOD1-FIL-01` / `MOD1-FIL-REQ-01` | The system shall provide a connected Digital Employee File that serves as an immutable, longitudinal dossier for each employee. | Module I | `[A]` | Module I Brief, Objective | `REQ-MOD1-01` | Aggregates all service records, files, and appraisal outcomes. |
| `REQ-MOD1-06` | `MOD1-CHG-01` / `MOD1-CHG-REQ-01` | The system shall provide a standardized digital change format for Change in Salary (increments, revisions, allowances) [Format (a)]. | Module I | `[A]` | Module I Brief, Structure 3(a) | `REQ-MOD1-01` | Captures component-level financial adjustments. |
| `REQ-MOD1-07` | `MOD1-CHG-01` / `MOD1-CHG-REQ-03` | The system shall provide a standardized digital change format for Change in Designation [Format (b)]. | Module I | `[A]` | Module I Brief, Structure 3(b) | `REQ-MOD1-01` | Prompts Org Chart realignment. |
| `REQ-MOD1-08` | `MOD1-CHG-01` / `MOD1-CHG-REQ-05` | The system shall provide a standardized digital change format for Change in Reportee [Format (c)]. | Module I | `[A]` | Module I Brief, Structure 3(c) | `REQ-MOD1-02` | Reassigns subordinate nodes. |
| `REQ-MOD1-09` | `MOD1-CHG-01` / `MOD1-CHG-REQ-07` | The system shall provide a standardized digital change format for Change in Reporting Authority [Format (d)]. | Module I | `[A]` | Module I Brief, Structure 3(d) | `REQ-MOD1-02` | Updates parent supervisor edge in Org Chart. |
| `REQ-MOD1-10` | `MOD1-CHG-01` / `MOD1-CHG-REQ-09` | The system shall provide a standardized digital change format for Change in Level (grade/band progression) [Format (e)]. | Module I | `[A]` | Module I Brief, Structure 3(e) | `REQ-MOD1-01` | Updates compensation band. |
| `REQ-MOD1-11` | `MOD1-CHG-01` / `MOD1-CHG-REQ-11` | The system shall provide a standardized digital change format for Change in Department / School [Format (f)]. | Module I | `[A]` | Module I Brief, Structure 3(f) | `REQ-MOD1-02` | Moves employee node between organizational subtrees. |
| `REQ-MOD1-12` | `MOD1-CHG-01` / `MOD1-CHG-REQ-13` | The system shall provide a standardized digital change format for Change in Location (campus/office) [Format (g)]. | Module I | `[A]` | Module I Brief, Structure 3(g) | `REQ-MOD1-01` | Captures physical workstation change. |
| `REQ-MOD1-13` | `MOD1-CHG-01` / `MOD1-CHG-REQ-14` | The system shall provide a standardized digital change format for Additional Responsibility Added (e.g., Dean, HOD, Proctor, Warden) [Format (h)]. | Module I | `[A]` | Module I Brief, Structure 3(h) | `REQ-MOD1-01` | Appends secondary role without removing primary post. |
| `REQ-MOD1-14` | `MOD1-CHG-REQ-15` | The system shall track effective start dates and expected tenures associated with additional responsibilities (administrative allowances are subject to HR policy confirmation, classified under REQ-TBD-09). | Module I | `[B]` | Module I Brief, Structure 3(h) | `REQ-MOD1-13` | Allowance formula is `[E] TBD` (REQ-TBD-09). |
| `REQ-MOD1-15` | `MOD1-CHG-01` / `MOD1-CHG-REQ-16` | The system shall provide a standardized digital change format for Change in Qualifications (degrees, certifications, licenses) [Format (i)]. | Module I | `[A]` | Module I Brief, Structure 3(i) | `REQ-MOD1-01` | Supports digital document upload and verification proof. |
| `REQ-MOD1-16` | `MOD1-CHG-01` / `MOD1-CHG-REQ-18` | The system shall provide an extensible change format for Any Other Employee Service Condition [Format (j)]. | Module I | `[A]` | Module I Brief, Structure 3(j) | `REQ-MOD1-01` | HR-configurable change mechanism. |
| `REQ-MOD1-17` | `MOD1-APP-01` / `MOD1-APP-REQ-01` | All employee data changes shall follow a mandatory two-level approval hierarchy: Level 1 (HR Level) followed by Level 2 (Senior Management Level). | Module I | `[A]` | Module I Brief, Approval Hierarchy (a, b) | `REQ-MOD1-06` to `16` | Strict sequential gating. |
| `REQ-MOD1-18` | `MOD1-DAT-01` / `MOD1-EFF-REQ-01` | The database change methodology shall natively support an `effective_date` parameter for all change formats, allowing future-dated change scheduling. | Module I | `[A]` | Module I Brief, Methodology | `REQ-MOD1-17` | Temporal scheduling core. |
| `REQ-MOD1-19` | `MOD1-EFF-REQ-03` | Automated Scheduled Activation Processing: The technical activation timing for approved changes on `effective_date` shall be executed via automated background/scheduled processing, committing updates, realigning the Org Chart, and emitting ERP sync events. | Module I | `[C]` | Tech Architecture Baseline, Section 7 | `REQ-MOD1-18` | Approved technical execution timing. |

---

## Section C: Module II — Recruitment & Selection Automation

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-MOD2-01` | `MOD2-REC-REQ-01` | The system shall strictly segregate the approval chains and evaluation workflows of Academic (Faculty/Lab Tech) and Non-Academic (Staff) recruitment. | Module II | `[A]` | Module II Brief, Section 1 | None | Independent multi-track recruitment architecture. |
| `REQ-MOD2-02` | `MOD2-MP-FAC-01` | For Academic positions, the system shall automatically initiate manpower planning communication at least four (4) months prior to semester commencement. | Module II | `[A]` | Module II Brief, Section 1(a) | `REQ-MOD2-01` | Advance calendar trigger (Associate Dean to Deans). |
| `REQ-MOD2-03` | `MOD2-MP-FAC-02` | School Deans shall submit academic manpower requirements along with teaching load calculations using Attachment 1 within fifteen (15) days of receipt. | Module II | `[A]` | Module II Brief, Section 1(b) | `REQ-MOD2-02` | Enclosure 2 (Teaching Load format). |
| `REQ-MOD2-04` | `MOD2-REC-REQ-04` | HR shall vet submitted teaching loads over a three (3) month window and consolidate requirements into Enclosure 1 (MRF) and Enclosure 3 (Attachment 2). | Module II | `[A]` | Module II Brief, Section 1(c, d) | `REQ-MOD2-03` | Consolidated institutional requirement. |
| `REQ-MOD2-05` | `MOD2-REC-REQ-05` | Consolidated academic manpower requirements shall be submitted to the Pro-Chancellor for approval, with a mandatory 7-day turnaround time (TAT). | Module II | `[A]` | Module II Brief, Section 1(e) | `REQ-MOD2-04` | Pro-Chancellor approval gate. |
| `REQ-MOD2-06` | `MOD2-REC-REQ-06` | HR shall launch public recruitment advertisements within seven (7) days of receiving Pro-Chancellor approval. | Module II | `[A]` | Module II Brief, Section 1(f) | `REQ-MOD2-05` | Ad launch SLA timer. |
| `REQ-MOD2-07` | `MOD2-MP-NF-01` | For Non-Academic positions, HR shall initiate manpower planning with Department Heads, restricted to one (1) planned requisition per year. | Module II | `[A]` | Module II Brief, Section 1(g) | `REQ-MOD2-01` | Planned requisition frequency quota. |
| `REQ-MOD2-08` | `MOD2-RES-01` / `MOD2-REC-REQ-08` | When an employee resignation is accepted by the School Dean, the system shall immediately start the urgent replacement countdown clock and notify Head HR. | Module II | `[A]` | Module II Brief, Section 1(i) | `REQ-MOD1-01` | Urgent replacement workflow trigger. |
| `REQ-MOD2-09` | `MOD2-REC-REQ-09` | Upon resignation notification, the Dean/HOD shall submit an ad-hoc MRF (Enclosure 1) specifying replacement urgency and reason for hire. | Module II | `[A]` | Module II Brief, Section 1(i) | `REQ-MOD2-08` | Ad-hoc MRF bypasses annual quota. |
| `REQ-MOD2-10` | `MOD2-REC-REQ-11` | The system shall maintain an Open Positions Tracker in the format of Attachment 3 (Enclosure 4) within thirty (30) days of approval. | Module II | `[A]` | Module II Brief, Section 2 & 3 | `REQ-MOD2-05`, `09` | Authoritative requisition registry. |
| `REQ-MOD2-11` | `MOD2-SRC-01` / `MOD2-REC-REQ-13` | The system shall capture applications into a Central CV Database across multiple sourcing channels: print media, website, social channels, emails, and Internshala. | Module II | `[A]` | Module II Brief, Section 4 | None | Omnichannel ingestion engine. |
| `REQ-MOD2-12` | `MOD2-SRC-02` / `MOD2-REC-REQ-14` | The system shall automatically segregate, classify, and shortlist CVs against qualifications, experience, and applicable statutory UGC norms. | Module II | `[A]` | Module II Brief, Section 5 | `REQ-MOD2-11` | Statutory criteria matching engine. |
| `REQ-MOD2-13` | `MOD2-REC-REQ-15` | The system shall maintain a digital Recruiter Calling Sheet (RCS) capturing initial phone screening remarks, communication rating, and qualification checks. | Module II | `[A]` | Module II Brief, Section 6 | `REQ-MOD2-12` | Recruiter screening ledger. |
| `REQ-MOD2-14` | `MOD2-REC-REQ-16` | RCS evaluation comments shall be reviewed by HOD-HR and submitted to Management for pre-approval prior to scheduling interviews. | Module II | `[A]` | Module II Brief, Section 7 | `REQ-MOD2-13` | Management interview gateway. |
| `REQ-MOD2-15` | `MOD2-SEL-FAC-01` | For Academic candidates, selection shall be conducted by a statutory Selection Committee Meeting (SCM) including Vice Chancellor, Dean, HOD, and External Expert. | Module II | `[A]` | Module II Brief, Selection A(a-d) | `REQ-MOD2-14` | Statutory academic selection workflow. |
| `REQ-MOD2-16` | `MOD2-REC-REQ-18` | SCM panel members shall record evaluation scores digitally across defined criteria; the system shall compile the final selection matrix for Management approval. | Module II | `[A]` | Module II Brief, Selection A(c, d) | `REQ-MOD2-15` | Digital scoring compilation. |
| `REQ-MOD2-17` | `MOD2-SEL-NF-01` | For Non-Academic candidates, selection shall follow a 3-Round interview process: Round 1 (Technical), Round 2 (HR), and Round 3 (Management). | Module II | `[A]` | Module II Brief, Selection B(a) | `REQ-MOD2-14` | 3-tier sequential interview evaluation. |
| `REQ-MOD2-18` | `MOD2-REC-REQ-20` | Non-Academic candidates shall be evaluated on Job Knowledge, Communication Skills, and Attitude, with weighted scoring per round. | Module II | `[A]` | Module II Brief, Selection B(a) | `REQ-MOD2-17` | Digital staff evaluation scorecard. |
| `REQ-MOD2-19` | `MOD2-ONB-01` / `MOD2-REC-REQ-21` | Upon Management approval, the system shall automatically generate a Letter of Intent (LOI) populated with candidate and compensation details. | Module II | `[A]` | Module II Brief, Selection A(e), B(b) | `REQ-MOD2-16`, `18` | Pre-offer document generation. |
| `REQ-MOD2-20` | `MOD2-REC-REQ-22` | Candidates accepting the LOI shall be tagged as "Yet to Join", initiating notice period monitoring and pre-onboarding notifications to Deans, HODs, and IT. | Module II | `[A]` | Module II Brief, Selection A(e), B(b) | `REQ-MOD2-19` | Onboarding countdown pipeline. |

---

## Section D: Module III — Performance Management Automation

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-MOD3-01` | `MOD3-GD-EVAL-01` | For Group-D staff, the system shall route a monthly digital Evaluation Form (Enclosure 1) to the HOD for each reporting member. | Module III (Group-D) | `[A]` | Group-D Brief, Section 1 & 2(a) | `REQ-MOD1-01` | Role-specific KPIs & competencies. |
| `REQ-MOD3-02` | `MOD3-GD-REQ-05` | Group-D monthly evaluation forms shall have a strict submission due date of the 7th of every month. | Module III (Group-D) | `[A]` | Group-D Brief, Section 2(c) | `REQ-MOD3-01` | Monthly operational deadline. |
| `REQ-MOD3-03` | `MOD3-GD-REQ-06` | The system shall provide an automated 3-day grace period up to the 10th of the month, sending daily reminders on the 8th, 9th, and 10th. | Module III (Group-D) | `[A]` | Group-D Brief, Section 2(c, d) | `REQ-MOD3-02` | Automated grace period & reminders. |
| `REQ-MOD3-04` | `MOD3-GD-REQ-08` | Auto-Lockout & "Not Submitted" Non-Compliance Flag: If the monthly evaluation is not submitted within the grace period (by the 10th of the month), the system shall automatically lock submission and flag the evaluation as "Not Submitted" for HR (technical execution timing at 23:59 governed by approved technical baseline [C]). | Module III (Group-D) | `[A]` | Group-D Brief, Section 2(e) | `REQ-MOD3-03` | Explicit business auto-lockout on 10th of month. |
| `REQ-MOD3-05` | `MOD3-GD-APP-01` | Group-D evaluations shall require mandatory digital sign-off and approval from the Vice President – Administration before becoming final. | Module III (Group-D) | `[A]` | Group-D Brief, Section 2(b) | `REQ-MOD3-01` | VP-Admin executive approval gate. |
| `REQ-MOD3-06` | `MOD3-GD-REQ-10` | The system shall automatically collate submitted monthly evaluations into a Monthly Performance Report (Enclosure 2 Template) for HR. | Module III (Group-D) | `[A]` | Group-D Brief, Section 3 | `REQ-MOD3-05` | Automated monthly collation. |
| `REQ-MOD3-07` | `MOD3-GD-ANN-01` | The system shall trigger an Annual Report for Group-D staff at one (1) year of employment (and subsequent years) based on Date of Joining (DOJ). | Module III (Group-D) | `[A]` | Group-D Brief, Section 4(a) | `REQ-MOD1-01` | Annual anniversary milestone. |
| `REQ-MOD3-08` | `MOD3-GD-REQ-12` | The Annual Report shall compute parameter-wise weighted average scores across the twelve (12) monthly evaluations. | Module III (Group-D) | `[A]` | Group-D Brief, Section 4(b) | `REQ-MOD3-07` | Annual score aggregation. |
| `REQ-MOD3-09` | `MOD3-GD-REQ-14` | The system shall enforce a mandatory probation verification gate; unconfirmed staff cannot proceed to compensation review. | Module III (Group-D) | `[A]` | Group-D Brief, Section 5(b) | `REQ-MOD3-08` | Statutory probation gate. |
| `REQ-MOD3-10` | `MOD3-KRA-SET-01` | For General Staff, new joiners shall set KRA/KPI Goal Sheets within thirty (30) days of Date of Joining (DOJ). | Module III (KRA/KPI) | `[A]` | KRA/KPI Brief, Stage 1 | `REQ-MOD1-01` | Onboarding goal-setting SLA. |
| `REQ-MOD3-11` | `MOD3-KRA-REQ-02` | KRA/KPI goal sheets shall require joint review and locking by HR and Management, freezing goals for the evaluation cycle. | Module III (KRA/KPI) | `[A]` | KRA/KPI Brief, Stage 1 | `REQ-MOD3-10` | Formal goal lock mechanism. |
| `REQ-MOD3-12` | `MOD3-KRA-QTR-01` | The system shall execute four quarterly review cycles (Q1–Q4) with 90-day intimation, 20-day reminder, 15-day submission window, and 7-day supervisor verification. | Module III (KRA/KPI) | `[A]` | KRA/KPI Brief, Stage 2 | `REQ-MOD3-11` | Structured quarterly SLA engine. |
| `REQ-MOD3-13` | `MOD3-KRA-INT-01` | The annual KRA/KPI performance outcome shall feed directly into Module I as a formal service change request (promotion, salary increment, or band change). | Module III (KRA/KPI) | `[A]` | KRA/KPI Brief, Stage 3 | `REQ-MOD3-12` | Handshake to Module I. |
| `REQ-MOD3-14` | `MOD3-FAC-ELG-01` | The system shall automatically identify eligible faculty (probation completed + $\ge$ 12 months service) on the 10th of every month and transmit the list to Registrar. | Module III (Faculty) | `[A]` | Faculty ECM Brief, Section 1 | `REQ-MOD1-01` | Monthly automated eligibility query. |
| `REQ-MOD3-15` | `MOD3-FAC-REQ-03` | Eligible faculty shall submit a digital Self-Appraisal Form (Enclosure 1) within seven (7) working days of receiving notification. | Module III (Faculty) | `[A]` | Faculty ECM Brief, Section 2 | `REQ-MOD3-14` | Self-appraisal submission SLA. |
| `REQ-MOD3-16` | `MOD3-FAC-VER-01` | Submitted self-appraisals shall route for parallel verification across Dean, Director R&D, Placement Cell, and HR, with a circular discrepancy return loop. | Module III (Faculty) | `[A]` | Faculty ECM Brief, Section 3 | `REQ-MOD3-15` | Multi-departmental verification & dispute loop. |
| `REQ-MOD3-17` | `MOD3-FAC-ECM-01` | The Registrar shall schedule a monthly Evaluation Committee Meeting (ECM) where statutory committee members enter scores via digital ECM Score Sheets (Enclosure 2). | Module III (Faculty) | `[A]` | Faculty ECM Brief, Section 4 | `REQ-MOD3-16` | Statutory ECM evaluation. |
| `REQ-MOD3-18` | `MOD3-FAC-REQ-07` | The system shall compile an Evaluation Matrix combining ECM scores, previous increment history, and TNU Protocol parameters for Management decision. | Module III (Faculty) | `[A]` | Faculty ECM Brief, Section 5 | `REQ-MOD3-17` | Synthesis for executive approval. |
| `REQ-MOD3-19` | `MOD3-FAC-SAL-01` | Approved faculty increments shall be tracked into the next salary cycle, and the system shall auto-generate the official compensation revision letter. | Module III (Faculty) | `[A]` | Faculty ECM Brief, Section 6 | `REQ-MOD3-18` | Salary cycle tracking & letter dispatch. |

---

## Section E: Cross-Module Integration Requirements

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-INT-01` | `SHR-INT-REQ-01` | When a candidate accepts an LOI and completes Day-1 onboarding, Module II shall automatically instantiate the master employee record in Module I Central DB. | Cross-Module | `[A]` | Mod II Selection & Mod I Background | `REQ-MOD2-19` | Onboarding handshake. |
| `REQ-INT-02` | `SHR-INT-REQ-02` | When an employee resignation is accepted by the School Dean in Module I, the system shall notify Head HR and start the Module II urgent replacement countdown. | Cross-Module | `[A]` | Mod II Section 1(i) & Mod I CDB | `REQ-MOD1-01` | Resignation replacement trigger. |
| `REQ-INT-03` | `SHR-INT-REQ-03` | Module III shall continuously consume employee Date of Joining, probation status, current department, and supervisor hierarchy from Module I. | Cross-Module | `[A]` | Universal Master Baseline | `REQ-MOD1-01` | Appraisal eligibility & routing feed. |
| `REQ-INT-04` | `SHR-INT-REQ-04` | Approved annual appraisal outcomes from Module III (Group-D, Staff KRA, Faculty ECM) shall automatically inject service change requests into Module I. | Cross-Module | `[A]` | Mod III Briefs & Mod I Structure 3 | `REQ-MOD3-08`, `13`, `18` | Eliminates manual re-keying of promotions/increments. |

---

## Section F: Reporting Requirements

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-REP-01` | `MOD1-REP-REQ-01` | The system shall provide an extensible reporting engine enabling HR administrators to add, modify, or retire report formats without code modifications. | Module I / Shared | `[A]` | Module I Brief, Reports | `REQ-MOD1-01` | Dynamic report builder. |
| `REQ-REP-02` | `MOD1-REP-REQ-03` | All operational and master reports shall support real-time execution against current database state. | Module I / Shared | `[A]` | Module I Brief, Reports | `REQ-MOD1-01` | Real-time query execution. |
| `REQ-REP-03` | `MOD2-REP-REQ-01` | The system shall auto-generate a Weekly Open Positions Report submitted to Senior Management detailing active vacancies and recruitment progress. | Module II | `[A]` | Module II Brief, Section 3 | `REQ-MOD2-10` | Weekly executive recruitment briefing. |
| `REQ-REP-04` | `MOD2-REP-REQ-04` | The system shall maintain a dedicated "Yet to Join" Tracker dashboard monitoring candidates who accepted LOIs through notice periods to Day-1 joining. | Module II | `[A]` | Module II Brief, Selection A(e), B(b) | `REQ-MOD2-19` | Onboarding pipeline tracking. |
| `REQ-REP-05` | `MOD3-REP-REQ-01` | The system shall auto-collate Group-D Monthly Performance Reports using the Enclosure 2 template for HR without manual compilation. | Module III | `[A]` | Group-D Brief, Section 3 | `REQ-MOD3-06` | Monthly support staff reporting. |
| `REQ-REP-06` | `MOD3-REP-REQ-02` | The system shall generate an Annual Performance Report for Group-D staff computing 12-month weighted average scores per parameter. | Module III | `[A]` | Group-D Brief, Section 4 | `REQ-MOD3-08` | Annual compensation review basis. |
| `REQ-REP-07` | `MOD3-REP-REQ-03` | The system shall generate real-time non-compliance audit reports identifying HODs who failed to submit Group-D evaluations prior to the 10th-of-month auto-lock. | Module III | `[A]` | Group-D Brief, Section 2(e) | `REQ-MOD3-04` | Compliance audit reporting. |
| `REQ-REP-08` | `MOD3-REP-REQ-07` | The system shall auto-generate a Monthly Eligible Faculty List on the 10th of every month listing faculty completing probation and $\ge$ 12 months service. | Module III | `[A]` | Faculty ECM Brief, Section 1 | `REQ-MOD3-14` | Monthly statutory appraisal trigger. |
| `REQ-REP-09` | `SHR-REP-REQ-03` | All system reports shall support structured data export in Excel (XLSX) and CSV formats. | Shared / Reporting | `[B]` | Universal Baseline | `REQ-REP-01` | Standard data export utility. |

---

## Section G: Audit and Versioning Requirements

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-AUD-01` | `MOD1-DAT-01` / `MOD1-AUD-REQ-01` | The system shall enforce an immutable audit trail capturing every master modification, approval, rejection, and state transition with timestamps and actor IDs. | Module I / Shared | `[A]` | Module I Brief, Methodology | None | Write-once append-only audit ledger. |
| `REQ-AUD-02` | `MOD1-VER-REQ-01` | The system shall maintain complete version history across all employee service condition changes without destructive overwrites. | Module I / Shared | `[A]` | Module I Brief, Methodology | `REQ-AUD-01` | Non-destructive temporal versioning. |
| `REQ-AUD-03` | `MOD3-GD-REQ-03` | The system shall allow the HR Team to update evaluation forms, versioning each iteration with an immutable audit trail. | Module III | `[A]` | Group-D Brief, Section 1(b) | None | Template version control. |
| `REQ-AUD-04` | `MOD3-KRA-REQ-02` | KRA/KPI goal sheets shall be frozen and version-locked upon HR and Management verification; revisions require tracked change requests. | Module III | `[A]` | KRA/KPI Brief, Stage 1 | None | Goal locking integrity. |

---

## Section H: Notification and SLA Requirements

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-SLA-01` | `MOD2-MP-FAC-01` | Automated advance notification dispatched $\ge$ 4 months prior to semester to initiate Academic Manpower Planning. | Module II | `[A]` | Module II Brief, Section 1(a) | None | Semester calendar trigger. |
| `REQ-SLA-02` | `MOD2-REC-REQ-03` | 15-day SLA timer enforced for School Deans to submit academic requirements and teaching loads. | Module II | `[A]` | Module II Brief, Section 1(b) | `REQ-SLA-01` | Dean submission countdown. |
| `REQ-SLA-03` | `MOD2-REC-REQ-05` | 7-day turnaround SLA enforced for Pro-Chancellor review and approval of consolidated academic manpower. | Module II | `[A]` | Module II Brief, Section 1(e) | `REQ-SLA-02` | Executive approval turnaround. |
| `REQ-SLA-04` | `MOD2-REC-REQ-06` | 7-day SLA enforced for HR to launch recruitment advertisements following Pro-Chancellor approval. | Module II | `[A]` | Module II Brief, Section 1(f) | `REQ-SLA-03` | Advertisement launch countdown. |
| `REQ-SLA-05` | `MOD3-GD-REQ-05` | Monthly submission due date enforced on the 7th of every month for Group-D evaluations. | Module III | `[A]` | Group-D Brief, Section 2(c) | None | Monthly evaluation deadline. |
| `REQ-SLA-06` | `MOD3-GD-REQ-06` | Automated 3-day grace period up to the 10th of the month with daily reminder notifications (8th, 9th, 10th). | Module III | `[A]` | Group-D Brief, Section 2(c, d) | `REQ-SLA-05` | Grace period reminders. |
| `REQ-SLA-07` | `MOD3-KRA-REQ-01` | 30-day onboarding SLA countdown from Date of Joining for new joiners to configure KRA/KPI goal sheets. | Module III | `[A]` | KRA/KPI Brief, Stage 1 | `REQ-ENT-01` | Onboarding goal-setting SLA. |
| `REQ-SLA-08` | `MOD3-KRA-REQ-03` | Structured quarterly SLA: 90-day advance intimation, 20-day reminder, 15-day employee self-review, and 7-day supervisor verification. | Module III | `[A]` | KRA/KPI Brief, Stage 2 | `REQ-SLA-07` | Quarterly review cadence. |
| `REQ-SLA-09` | `MOD3-FAC-REQ-03` | 7 working days submission SLA for eligible faculty to submit their annual self-appraisal form upon receiving notification. | Module III | `[A]` | Faculty ECM Brief, Section 2 | `REQ-REP-08` | Faculty self-appraisal turnaround. |
| `REQ-SLA-10` | `SHR-NTF-REQ-03` | Notification dispatch shall be offloaded to asynchronous background queues to prevent blocking web transactions. | Shared / Technical | `[C]` | Approved Tech Baseline | None | Decoupled background notification execution. |

---

## Section I: Document, Form, and Template Requirements

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-DOC-01` | `SHR-CFG-REQ-01` | The system shall provide a centralized, version-controlled repository maintaining standardized digital forms for Formats (a) through (j). | Module I | `[A]` | Module I Brief, Structure 3 | None | 10 service change formats. |
| `REQ-DOC-02` | `SHR-CFG-REQ-01` | The system shall maintain standardized digital templates for Enclosure 1 (MRF), Attachment 1 (Teaching Load), Attachment 2 (Vacancy Spec), Attachment 3 (Tracker), and RCS. | Module II | `[A]` | Module II Enclosures | None | Field schemas are `[E] TBD`. |
| `REQ-DOC-03` | `SHR-CFG-REQ-01` | The system shall maintain standardized digital templates for Group-D Form (Enclosure 1), Report (Enclosure 2), KRA Goal Sheet, Faculty Form (Enclosure 1), ECM Sheet (Enclosure 2), and TNU Matrix (Enclosure 3). | Module III | `[A]` | Module III Enclosures | None | Scoring weights are `[E] TBD`. |
| `REQ-DOC-04` | `MOD2-REC-REQ-21` | The system shall auto-generate official Letter of Intent (LOI) documents upon Management approval of candidate selection. | Module II | `[A]` | Module II Brief, Selection A(e), B(b) | `REQ-MOD2-16`, `18` | Auto-generated PDF letter. |
| `REQ-DOC-05` | `MOD3-FAC-REQ-09` | The system shall auto-generate official compensation revision letters for faculty upon Management approval of ECM appraisal outcomes. | Module III | `[A]` | Faculty ECM Brief, Section 6(b) | `REQ-MOD3-18` | Auto-generated PDF letter. |
| `REQ-DOC-06` | `SHR-DOC-REQ-01` | Binary files (CVs, certificates, letters) shall be stored in Object Storage with access controls and checksums stored in relational database metadata. | Shared / Technical | `[C]` | Approved Tech Baseline | None | Binary/metadata separation. |
| `REQ-DOC-07` | `SHR-DOC-REQ-02(a)` | File Upload Security & Validation: All file uploads shall undergo strict MIME-type validation and SHA-256 integrity hashing to ensure document security and file integrity. | Shared / Security | `[B]` | Universal Baseline | None | Security validation primitive. |
| `REQ-DOC-08` | `SHR-DOC-REQ-02(b)` | Operational File Size Enforcement: Document uploads shall enforce an operational file size limit (proposed threshold of maximum 10MB per document), subject to University IT confirmation. | Shared / Storage | `[D]` | FRD Quality Review & Architecture Baseline | `REQ-DOC-07` | Proposed engineering threshold; not official university policy. |

---

## Section J: Integration Requirements

| Requirement ID | Traceability ID | Requirement Statement | Module / Domain | Class | Source Reference | Dependencies | Notes / TBD |
|---|---|---|---|---|---|---|---|
| `REQ-EXT-01` | `MOD1-CDB-03` / `SHR-ERP-REQ-01` | The Central Employee Database shall be fully reflected and synchronized with the University Enterprise Resource Planning (ERP) platform. | Module I / ERP | `[A]` | Module I Brief, Structure (1) | `REQ-MOD1-01` | Full ERP reflection mandate. |
| `REQ-EXT-02` | `SHR-ERP-REQ-02` | Outbound ERP synchronization payloads shall be written to an immutable outbox within the local transaction to ensure eventual consistency. | Architecture / ERP | `[C]` | Approved Tech Baseline | `REQ-EXT-01` | Transactional outbox pattern. |
| `REQ-EXT-03` | `SHR-ERP-REQ-03` | The specific physical protocol and payload structure for ERP synchronization is classified as `[E] TBD` pending University IT confirmation. | Architecture / ERP | `[E]` | Module I Brief & Tech Baseline | `REQ-EXT-01` | REST, DB staging, or SFTP (`[E] TBD` / REQ-TBD-01). |
| `REQ-EXT-04` | `SHR-TBD-01` | Institutional Single Sign-On (SSO) integration mechanism (Google Workspace, Microsoft Entra ID, or LDAP) is classified as `[E] TBD`. | Security / SSO | `[E]` | Universal Baseline | None | Enterprise IdP configuration (`[E] TBD` / REQ-TBD-07a). |
| `REQ-EXT-05` | `REQ-TBD-07` | External Subject Expert secure access mechanism (time-limited magic links or OTP-verified portal) is classified as `[E] TBD`. | Security / External | `[E]` | Module II Selection A(a) | None | External authentication model (`[E] TBD` / REQ-TBD-07b). |

---

## Section K: Classification Reconciliation & TBD Register Cross-Reference

### 1. Mathematical Classification Summary
Every atomic requirement in this catalogue has been assigned a single, unambiguous classification code. The counts mathematically reconcile across all sections:

| Classification Marker | Classification Name | Atomic Count | Percentage | Mathematical Verification Formula |
|:---:|---|:---:|:---:|---|
| **`[A]`** | **Explicit Requirement** | **88** | 84.62% | Directly stated in official PDFs |
| **`[B]`** | **Logical Implication** | **8** | 7.69% | Operationally and logically necessary primitives |
| **`[C]`** | **Approved Technical Decision** | **4** | 3.85% | Approved technical architecture decisions |
| **`[D]`** | **Proposed Detail** | **1** | 0.96% | Proposed engineering threshold (10MB upload limit) |
| **`[E]`** | **TBD / Open Decision** | **3** | 2.88% | Standalone atomic integration requirements pending IT confirmation |
| **TOTAL** | | **104** | **100.00%** | **88 + 8 + 4 + 1 + 3 = 104** |

### 2. Reconciliation with the TBD Register (`REQ-TBD-01` through `REQ-TBD-11`)
The project maintains a dedicated Controlled TBD Register in [`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md) containing eleven (11) items. Their exact relationship to this atomic requirement catalogue is structured as follows:

| TBD Register ID | Open Decision Title / Domain | Nature of Item | How Represented in Catalogue |
|---|---|---|---|
| **`REQ-TBD-01`** | ERP Synchronization Architecture & Protocol | Standalone System Integration Requirement | Catalogued as **`REQ-EXT-03`** (`[E]`) in Section J. |
| **`REQ-TBD-02`** | Standardized Attachment & Enclosure Schemas | Schema & Form Template Field Gap | Qualifies **`REQ-DOC-02`** & **`REQ-DOC-03`** (digital form maintenance is `[A]`; field schemas are `[E] TBD`). |
| **`REQ-TBD-03`** | Staff Appraisal Track Boundary Definitions | Operational Track Allocation Policy Gap | Qualifies **`REQ-MOD3-10`** & **`REQ-MOD3-14`** (track rules for Lab Techs / Teaching Associates). |
| **`REQ-TBD-04`** | TNU Protocol Parameter Weights & Quorums | Mathematical Weightage & Governance Gap | Qualifies **`REQ-MOD2-15`** & **`REQ-MOD3-18`** (matrix compilation is `[A]`; scoring weights are `[E] TBD`). |
| **`REQ-TBD-05`** | Pre-Defined Compensation Revision Slabs | Financial Compensation Policy Gap | Qualifies **`REQ-MOD3-09`** & **`REQ-MOD3-19`** (increment reviews are `[A]`; monetary slabs are `[E] TBD`). |
| **`REQ-TBD-06`** | Resignation Upstream Intake & Clearance | Workflow Initiation Interface Gap | Qualifies **`REQ-MOD2-08`** & **`REQ-INT-02`** (resignation replacement trigger is `[A]`; upstream intake is `[E] TBD`). |
| **`REQ-TBD-07(a)`** | Enterprise Single Sign-On (IdP) | Standalone System Security Requirement | Catalogued as **`REQ-EXT-04`** (`[E]`) in Section J. |
| **`REQ-TBD-07(b)`** | External Subject Expert Access Protocol | Standalone System Security Requirement | Catalogued as **`REQ-EXT-05`** (`[E]`) in Section J. |
| **`REQ-TBD-08`** | LOI vs. Formal Appointment Letter Lifecycle | Contractual & Legal Lifecycle Gap | Qualifies **`REQ-MOD2-19`** & **`REQ-DOC-04`** (LOI issuance is `[A]`; post-joining contract is `[E] TBD`). |
| **`REQ-TBD-09`** | Administrative Allowance for Secondary Roles | HR Financial Policy Gap | Qualifies **`REQ-MOD1-13`** & **`REQ-MOD1-14`** (Format 3(h) is `[A]`; allowance rule is `[E] TBD`). |
| **`REQ-TBD-10`** | Outbound Communication Gateways & Relays | Infrastructure Host Configuration Gap | Qualifies **`REQ-SLA-10`** (queue dispatch is `[C]`; SMTP relay and SMS gateway credentials are `[E] TBD`). |
| **`REQ-TBD-11`** | Document Retention & Archival Lifecycle | Legal & Compliance Retention Schedule Gap | Qualifies **`REQ-AUD-01`** & **`REQ-DOC-06`** (audit log is `[A]`; retention schedule is `[E] TBD`). |

---
*End of Document — Comprehensive Requirement Catalogue.*
