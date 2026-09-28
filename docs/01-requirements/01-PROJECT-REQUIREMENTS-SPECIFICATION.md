# Project Requirements Specification
## University HR Change Management & Automation System

**Document Identifier:** `DOC-01-PRS-01`  
**Phase:** Phase 1 — Requirements Engineering & Specification (Documentation-Only)  
**Location:** `docs/01-requirements/01-PROJECT-REQUIREMENTS-SPECIFICATION.md`  
**Status:** Approved Requirements Specification Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Document Purpose

This document constitutes the formal, high-level **Project Requirements Specification (PRS)** for the University HR Change Management & Automation System. Its objective is to articulate the comprehensive business requirements, operational context, strategic goals, functional domain overviews, architectural boundaries, cross-cutting requirements, and governance constraints that define the project scope.

This specification serves as the primary contractual and architectural baseline for University Leadership, Academic Deans, Department Heads, Human Resources personnel, and future technical engineering teams. It bridges institutional intent with verifiable system requirements while rigorously preserving the distinction between explicit business mandates, logical deductions, approved technical decisions, proposed details, and open policy decisions.

---

## 2. Project Overview

The University is commissioning an enterprise-grade, web-based, unified **HR Change Management & Automation System** spanning three core institutional modules:
1. **Module I — HR Change Management & Core Employee Database:** The single source of truth for employee service data, organizational structures, standardized change management, two-level approvals, temporal versioning, and ERP reflection.
2. **Module II — Recruitment & Selection Automation System:** The end-to-end talent acquisition platform managing Academic and Non-Academic manpower planning, urgent replacement workflows, omnichannel sourcing, UGC-compliant screening, statutory selection committees, interview evaluations, and Letter of Intent (LOI) issuance.
3. **Module III — Performance Management Automation System:** The performance evaluation engine governing three independent appraisal tracks: Group-D / Band I monthly and annual reviews, General Staff KRA/KPI quarterly lifecycles, and Faculty Annual Appraisals via the Evaluation Committee Meeting (ECM) route.

The platform eliminates administrative friction, insulates the university against audit vulnerabilities, and automates deadline-driven academic and administrative operations across all schools and departments.

---

## 3. Business Context

The University operates across diverse academic schools, administrative directorates, research cells, and operational support units. This ecosystem encompasses three distinct categories of personnel:
- **Academic Staff:** Teaching Faculty, Deans, Associate Deans, Program Chairs, Research Fellows, and Teaching Associates whose qualifications, recruitment, workload, and performance are strictly governed by statutory bodies (e.g., University Grants Commission / UGC) and university governing statutes.
- **Administrative & Technical Staff:** Department heads, administrative officers, technical assistants, laboratory technicians, and operational staff whose hiring and appraisals follow structured quarterly performance indicators and multi-tier interviews.
- **Support Staff (Group-D / Band I):** Operational, maintenance, housekeeping, security, and facility staff evaluated on a disciplined monthly basis by departmental heads.

Managing this heterogeneous workforce across academic semesters, fiscal years, and recruitment cycles requires an automated, role-aware, and auditable software infrastructure.

---

## 4. Strategic Objectives

The system is designed to achieve six primary institutional objectives:

1. **Elimination of Duplicate Data Entry [A]:** Ensure that every approved change in service condition, completed recruitment milestone, or finalized appraisal outcome automatically propagates across connected records, organizational structures, reports, and digital employee files without manual intervention.
2. **Single Source of Truth & Full ERP Reflection [A]:** Establish a centralized, authoritative Central Employee Database that maintains complete synchronization with the University's Enterprise Resource Planning (ERP) platform.
3. **Multi-Track Governance & Procedural Integrity [A]:** Enforce distinct, role-governed workflows for Academic and Non-Academic hiring, and preserve the independence of all three performance management subsystems.
4. **Comprehensive Auditability & Temporal Versioning [A]:** Provide a uniform database change methodology that captures every transaction with immutable audit trails, actor attribution, state diffs, and temporal validity via effective dates (`effective_date`).
5. **Automated SLA Enforcement & Operational Discipline [A]:** Replace manual chasing with system-driven schedules, automated advance communications, reminder sequences, grace periods, auto-lockouts, and escalation notifications.
6. **Dynamic Operational Visibility [A]:** Provide administrative teams with real-time reporting dashboards, flexible report-generation engines, and longitudinal employee dossiers.

---

## 5. Problem Statement

Prior to this automation initiative, the university's HR operations were characterized by:
- **Fragmented Master Data:** Employee service conditions (designations, salaries, reporting lines) were maintained across disparate spreadsheets, paper service books, and decoupled departmental registries, leading to desynchronization with the central ERP.
- **Uncontrolled Data Modifications:** Service modifications (increments, transfers, additional administrative responsibilities) were executed through ad-hoc memorandums lacking centralized version control or retrospective temporal tracking.
- **Recruitment Bottlenecks:** Manpower planning for upcoming academic semesters occurred without standardized workload calculations (Teaching Load Attachment 1), leading to compressed recruitment timelines, delayed advertising, and last-minute hiring.
- **Audit Risks in Selection:** Academic selection committee meetings (SCM) and staff interviews relied on paper evaluation sheets, introducing compliance vulnerabilities under statutory accreditation standards.
- **Appraisal Delays & Conflation:** Performance appraisals suffered from high turnaround times, missed submission deadlines, lack of objective KRA goal-locking, and attempts to force disparate employee groups (Faculty vs. Support Staff) into a single inappropriate review mechanism.

---

## 6. System Vision

The University HR Change Management & Automation System will operate as a unified, cohesive platform that acts as the institutional **digital backbone** for the complete employee lifecycle:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   INSTITUTIONAL SYSTEM VISION                                    │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                               MODULE II: TALENT ACQUISITION                                      │
│  Academic & Non-Academic Manpower Requisitions ──► Sourcing ──► Screening ──► Selection ──► LOI │
└──────────────────────────────────────────┬───────────────────────────────────────────────────────┘
                                           │ Onboarding Handshake (SHR-INT-01)
                                           ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                     MODULE I: CORE REPOSITORY & CHANGE MANAGEMENT ENGINE                         │
│  Central Employee DB (ERP Synced) ◄──► Dynamic Org Chart ◄──► Digital Employee Files (Dossiers) │
│  10 Change Formats ──► 2-Level Approvals (HR ➔ Senior Mgmt) ──► Effective Date Versioning       │
└──────────────────────────────────────────┬───────────────────────────────────────────────────────┘
                     ▲                     │ Master Data Feed (SHR-INT-03)
                     │                     ▼
┌────────────────────┴─────────────────────────────────────────────────────────────────────────────┐
│                           MODULE III: PERFORMANCE MANAGEMENT ENGINE                              │
│  • Sub-System 1: Group-D Monthly Ratings (7th/10th auto-lock) & Annual Weighted Averages         │
│  • Sub-System 2: Staff KRA/KPI Onboarding (30-day lock) & Quarterly Reviews (Q1-Q4)              │
│  • Sub-System 3: Faculty Annual Appraisal via Statutory ECM Route (Monthly Eligibility 10th)     │
│  Approved Outcomes Auto-Feed into Module I Service Change Requests (SHR-INT-04)                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 7. Project Scope

### 7.1 In-Scope Capabilities
- **Module I:** Central Employee Database, Dynamic Org Chart, Digital Employee File, 10 standardized service condition change formats, 2-level approval workflow, effective date methodology, immutable audit logging, dynamic reporting engine, and ERP outbox synchronization.
- **Module II:** Academic Manpower Planning (semester cycle), Non-Academic Manpower Planning (annual cycle), Urgent Replacement (resignation) workflow, Open Positions Tracker, omnichannel CV ingestion, UGC shortlisting engine, Recruiter Calling Sheet (RCS), Statutory Selection Committee (SCM) digital scoring, 3-Round Non-Academic interviews, automated LOI generation, and "Yet to Join" pipeline tracking.
- **Module III:** Group-D monthly evaluation and annual reports, Staff 30-day KRA/KPI goal setting and quarterly reviews, Faculty annual appraisal eligibility tracking, multi-departmental verification with discrepancy handling, statutory Evaluation Committee Meetings (ECM), TNU Protocol matrix compilation, and compensation letter generation.
- **Shared Infrastructure:** Common master data primitives, universal workflow engine, SLA scheduler, notification dispatcher, central form/template catalog, document management, and RBAC security.

### 7.2 Out-of-Scope Capabilities
- Core ERP finance, student lifecycle, and general ledger modules.
- Biometric attendance hardware and physical access turnstiles.
- Complete payroll computation, tax withholding, and direct bank disbursement (managed within ERP/Payroll).
- University LMS (Learning Management System) course delivery and student grading.
- Full ATS public career portal with applicant self-service accounts (initial sourcing captures CVs via designated intake channels).

---

## 8. Major Functional Areas

The system comprises four major functional areas:
1. **Change Management & Organization Core (Module I)**
2. **Talent Sourcing & Selection (Module II)**
3. **Multi-Track Performance Management (Module III)**
4. **Cross-Cutting Shared Infrastructure (Shared Services)**

---

## 9. Module I Overview: HR Change Management & Core DB

Module I provides the system of record and transactional change architecture:
- **Central Employee Database [A]:** Master record of all personnel, maintaining relational identity and full synchronization with the university ERP.
- **Dynamic Organization Chart [A]:** Automatically renders reporting hierarchies; realigns dynamically upon approved updates to designations, reportees, reporting authorities, or departments.
- **Digital Employee File [A]:** Unified, chronologically organized dossier linking personal profiles, appointments, historical service changes, credentials, and performance evaluations.
- **Ten Standardized Change Formats [A]:**
  - *Format (a):* Change in Salary
  - *Format (b):* Change in Designation
  - *Format (c):* Change in Reportee
  - *Format (d):* Change in Reporting Authority
  - *Format (e):* Change in Level
  - *Format (f):* Change in Department / School
  - *Format (g):* Change in Location
  - *Format (h):* Additional Responsibility Added (e.g., Dean, HOD, Proctor, Warden)
  - *Format (i):* Change in Qualifications
  - *Format (j):* Any Other Employee Service Condition
- **Two-Level Approval Hierarchy [A]:** Level 1 HR vetting followed strictly by Level 2 Senior Management authorization.
- **Effective-Date Methodology [A]:** Support for advance submissions activating automatically on `effective_date`.
- **Audit Trails & Version History [A]:** Tamper-evident logging of actor, timestamps, and full state diffs without destructive overwrites.

---

## 10. Module II Overview: Recruitment & Selection Automation

Module II automates institutional talent acquisition while rigorously segregating Academic and Non-Academic tracks:
- **Academic Manpower Planning [A]:** Automated initiation $\ge$ 4 months before semester commencement; Deans submit Teaching Load (Attachment 1) within 15 days; HR vetting over 3 months; Pro-Chancellor approval turnaround within 7 days; ad launch within 7 days.
- **Non-Academic Manpower Planning [A]:** Formal MRF (Enclosure 1) initiated by HR with Department Heads, restricted to 1 planned requisition per year.
- **Urgent Replacement Workflow [A]:** Resignation acceptance by School Dean immediately triggers urgent replacement countdown, alerting Head HR and authorizing ad-hoc MRF.
- **Open Positions Tracker [A]:** Authoritative registry (Attachment 3) maintained within 30 days of approval; weekly progress reports submitted to Senior Management.
- **Omnichannel Sourcing & Central CV Database [A]:** Centralized ingestion across print media, website, social channels (LinkedIn, Facebook, Instagram), designated email inboxes, employee referrals, and Internshala.
- **UGC Norms Screening [A]:** Automated qualification matching against applicable statutory criteria (UGC/AICTE/State regulations).
- **Recruiter Calling Sheet (RCS) [A]:** Structured phone screening log reviewed by HOD-HR and approved by Management prior to scheduling interviews.
- **Selection Workflows [A]:**
  - *Academic:* Statutory Selection Committee Meeting (SCM) comprising Vice Chancellor, Dean, HOD, and External Subject Expert, utilizing digital scoring sheets.
  - *Non-Academic:* 3-Round interview structure (Technical, HR, Management) assessing Job Knowledge, Communication Skills, and Attitude.
- **Pre-Onboarding & LOI [A]:** Automated Letter of Intent (LOI) generation upon Management sign-off; "Yet to Join" pipeline tracking; pre-onboarding notifications to Deans, HODs, and Admin/IT.

---

## 11. Module III Overview: Performance Management Automation

Module III governs three independent, non-conflated performance appraisal subsystems:

### 11.1 Sub-System 1: Group-D / Band I Staff Review
- **Monthly Evaluation [A]:** Standardized digital rating form (Enclosure 1) routed to HODs.
- **Strict Timelines [A]:** Due on the 7th of every month; automated 3-day grace period up to the 10th; daily reminders.
- **Auto-Lockout [A/C]:** Explicit business cutoff on the 10th; automated background lock flags missed forms as "Not Submitted" for HR visibility.
- **VP Approval & Collation [A]:** Final sign-off by Vice President – Administration; automatic collation into Monthly Report (Enclosure 2).
- **Annual Milestone [A]:** Automatic generation at 1-year service mark from Date of Joining (DOJ); calculation of 12-month parameter-wise weighted averages; mandatory probation verification gate before compensation review.

### 11.2 Sub-System 2: General Employee KRA/KPI Lifecycle
- **Stage 1 (Goal Setting) [A]:** New joiners configure KRA/KPI Goal Sheets within 30 days of DOJ; formal locking by HR and Management.
- **Stage 2 (Quarterly Review) [A]:** Four quarterly cycles (Q1–Q4); 90-day intimation, 20-day reminder, 15-day employee self-assessment window, 7-day supervisor verification; TAT tracking.
- **Stage 3 (Annual Integration) [A]:** 4-quarter performance synthesis feeding directly into Module I service change requests.

### 11.3 Sub-System 3: Faculty Annual Appraisal via ECM Route
- **Eligibility Identification [A]:** System automatically identifies eligible faculty (confirmed probation + $\ge$ 12 months service) on the 10th of every month; list transmitted to Registrar.
- **Self-Appraisal [A]:** Faculty submit self-appraisal form (Enclosure 1) within 7 working days.
- **Multi-Departmental Verification [A]:** Parallel verification by Dean, Director R&D, Placement Cell, and HR; circular discrepancy handling loop for contested claims.
- **Evaluation Committee Meeting (ECM) [A]:** Scheduled by Registrar; statutory committee scores faculty via digital ECM Score Sheet (Enclosure 2).
- **TNU Protocol Matrix [A]:** System compiles evaluation matrix combining ECM scores, previous increments, and TNU Protocol parameters for Management decision.
- **Salary Cycle & Letter [A]:** Tracks approved adjustments into the next salary cycle; auto-generates compensation revision letter for faculty and payroll.

---

## 12. Shared/Common Capabilities

The platform includes enterprise shared services:
- **Central Master Data Primitives:** Single definition of employees, schools, departments, designations, and job bands.
- **Generic Workflow & State Machine Engine:** Universal state management supporting linear and branching approvals.
- **Timeline & SLA Countdown Engine:** Asynchronous temporal monitoring tracking statutory and operational deadlines.
- **Unified Notification Service:** Email, in-app alerts, and system notices dispatched without blocking transactions.
- **Central Digital Form Catalog:** Version-controlled storage and configuration for all standardized forms and templates.
- **Document & Binary Asset Storage:** Secure storage for CVs, certificates, and auto-generated PDFs.
- **Tamper-Evident Audit Logging:** Universal logging recording actor, timestamp, IP, and state diffs.

---

## 13. Cross-Module Integration Requirements

The three modules maintain strict transactional handshakes:

| Integration Flow | Source Module | Target Module | Triggering Business Event | Automated Action in Target Module |
|---|---|---|---|---|
| **`SHR-INT-01`** [A] | Module II | Module I | Candidate accepts LOI and completes Day-1 Onboarding. | Automatically instantiates new employee master record in Central DB and attaches position node in Dynamic Org Chart. |
| **`SHR-INT-02`** [A] | Module I | Module II | Employee resignation is accepted by School Dean. | Automatically triggers Module II urgent replacement countdown, notifies Head HR, and authorizes ad-hoc MRF. |
| **`SHR-INT-03`** [A] | Module I | Module III | Continuous employee service tracking. | Synchronizes DOJ, probation status, current supervisor, and band to drive appraisal eligibility and form routing. |
| **`SHR-INT-04`** [A] | Module III | Module I | Annual appraisal outcome approved by Management (Group-D, Staff, or Faculty). | Automatically injects a formal service condition change request into Module I without manual duplicate entry. |

---

## 14. Audit, Versioning and Traceability Requirements

- **Universal Audit Methodology [A]:** Every database mutation across Modules I, II, and III must log the actor identity, role, timestamp, action type, and before/after state diff.
- **Non-Destructive Temporal History [A]:** Historical records must never be purged or updated destructively; changes utilize temporal validity markers.
- **Template Versioning [A]:** Updates to evaluation forms, scoring criteria, or change formats must create new versioned templates with full audit logs, ensuring historical appraisals remain tied to the version active during that cycle.
- **Forward & Backward Traceability [B]:** Every operational record must trace back to its initiating requisition, appraisal cycle, or service change request.

---

## 15. SLA and Notification Requirements

The system enforces automated temporal monitoring:
- **Advance Intimations [A]:** $\ge$ 4 months before semester (Academic Planning), 90 days before quarter close (KRA Review).
- **Milestone Deadlines [A]:** 15-day Dean submission, 3-month HR vetting, 7-day Pro-Chancellor turnaround, 7th-of-month Group-D due date, 30-day KRA setup, 7-day faculty self-appraisal.
- **Grace Periods & Auto-Locks [A/C]:** 3-day grace period up to the 10th for Group-D evaluations, terminating in automated submission lockout.
- **Escalations [B]:** Overdue warnings dispatched to supervisors and HR when turnaround thresholds are breached.

---

## 16. Reporting Requirements

- **Module I [A]:** Administrative capability for HR to add, modify, or retire report formats; on-demand real-time execution across employee rosters, org hierarchies, and change audit trails.
- **Module II [A]:** Weekly Open Positions Report to Senior Management, sourcing channel effectiveness analytics, candidate funnel metrics, "Yet to Join" dashboard, and pre-onboarding briefings.
- **Module III [A]:** Group-D Monthly Report (Enclosure 2), Annual Weighted Report, "Not Submitted" non-compliance audit, 30-day KRA setup tracking, quarterly submission matrices, monthly eligible faculty lists, ECM score sheet compilations, and compiled evaluation matrices.
- **Export Standards [B]:** All reports must support structured export in Excel (XLSX) and CSV formats.

---

## 17. Document, Form, and Template Requirements

The system must digitally maintain all standardized formats referenced in official briefs:
- **Module I:** Formats (a) through (j).
- **Module II:** Manpower Requisition Form (MRF Enclosure 1), Teaching Load Format (Attachment 1), Vacancy Specification (Attachment 2), Open Positions Tracker (Attachment 3), Recruiter Calling Sheet (RCS), SCM Digital Evaluation Sheet, Non-Faculty Digital Evaluation Sheet, and auto-generated Letter of Intent (LOI).
- **Module III:** Group-D Evaluation Form (Enclosure 1), Group-D Monthly/Annual Report Template (Enclosure 2), KRA Goal Sheet, Quarterly Review Form, Faculty Self-Appraisal Form (Enclosure 1), ECM Score Sheet (Enclosure 2), Evaluation Matrix Template (Enclosure 3 / TNU Protocol), and Faculty Compensation Revision Letter.

---

## 18. External Integration Requirements

- **University ERP Synchronization [A]:** Central Employee Database must maintain full reflection and synchronization with the University ERP.
- **Outbox Pattern Execution [C]:** Outbound ERP synchronization events must utilize transactional outbox patterns to guarantee eventual consistency.
- **ERP Protocol & Transport [E]:** The specific physical transport (REST API, database staging, or SFTP batch sync) is subject to university IT confirmation (`[E] TBD`).
- **External Subject Expert Access [E]:** Secure, external access mechanism for statutory SCM members (e.g., magic link or OTP portal) subject to security confirmation (`[E] TBD`).
- **Identity Provider (IdP) [E]:** Enterprise Single Sign-On integration (Google Workspace, Microsoft Entra ID, or LDAP) subject to institutional IT confirmation (`[E] TBD`).

---

## 19. Security and Access-Control Requirements

- **Role-Based Access Control (RBAC) [A/B]:** Strict functional role separation ensuring actors access only authorized resources:
  - *Employees:* View personal profile, submit KRA self-reviews, submit faculty self-appraisal.
  - *HODs / Supervisors:* View direct reportees, conduct monthly Group-D ratings, verify KRA quarterly reviews.
  - *Deans:* View School-wide personnel, submit academic manpower planning, accept employee resignations.
  - *HR Administrators:* Cross-departmental coordination, shortlisting, RCS review, form catalog management.
  - *Senior Management (VC, Pro-Chancellor, Registrar, VP-Admin):* Institutional approvals, executive reports, final authorization.
  - *External Experts:* Scoped, time-limited evaluation access restricted to assigned candidates.
- **Data Privacy & Salary Masking [B]:** Strict isolation of compensation data; access restricted to authorized HR and Management authorities.

---

## 20. High-Level Data Requirements

- **Relational Integrity [B]:** Strict relational foreign keys linking employee identity across service changes, job applications, and appraisal scorecards.
- **Temporal Data Modeling [B]:** Master records must capture effective date intervals (`effective_date` and audit validity) to reconstruct organizational structures at any historical point in time.
- **Document Metadata Segregation [C]:** Binary documents (CVs, degree certificates, letters) stored in object storage with checksums and access controls held in relational metadata tables.
- **Soft Deletion [B]:** Business records must not be physically erased; soft deletion (`deleted_at`) preserves longitudinal audit trails.

---

## 21. High-Level Automation Requirements

- **Temporal Scheduling Engine [B/C]:** Automated background execution of calendar-driven tasks (semester planning triggers, monthly evaluation generation, reminder dispatches, midnight auto-locks, effective-date activations).
- **Asynchronous Task Queuing [C]:** High-volume notifications, report generation, and document conversions executed in background worker queues to ensure sub-second UI responsiveness.
- **Event-Driven Handshakes [B/C]:** Cross-module data flows (LOI onboarding, resignation trigger, appraisal compensation updates) orchestrated via idempotent event handlers.

---

## 22. Requirement Classification Summary

All requirements throughout the project baseline adhere to the governing classification taxonomy:
- **`[A] Explicit Requirement`:** Verified directly against official requirement briefs.
- **`[B] Logical Implication`:** Derived as operationally essential to fulfill explicit requirements.
- **`[C] Approved Technical Decision`:** Aligned with approved technical architecture baseline.
- **`[D] Proposed Detail`:** Proposed engineering parameters awaiting formal university ratification.
- **`[E] TBD / Open Decision`:** Documented open items requiring university clarification.

---

## 23. Assumptions

1. The University maintains a central directory of active schools, academic departments, and administrative units.
2. Academic calendars follow standardized semester cycles (typically Autumn and Spring) to anchor the 4-month manpower planning trigger.
3. Every active employee possesses a unique institutional identifier (Employee ID) that remains immutable across transfers and promotions.
4. Institutional email infrastructure (SMTP) is accessible for outbound system notifications.
5. Management and HR authorities possess digital credentials capable of executing authorized digital sign-offs.

---

## 24. Constraints

1. **Regulatory & Statutory Compliance [A]:** Academic recruitment and faculty evaluations must strictly adhere to University Grants Commission (UGC) and relevant statutory body regulations.
2. **Statutory Committee Quorums [A]:** Selection Committee Meetings (SCM) and Evaluation Committee Meetings (ECM) require designated statutory quorums, including external experts.
3. **Approved Technology Stack Baseline [C]:** Development is strictly bound to Next.js (TypeScript, Vanilla CSS / CSS Modules) and NestJS Modular Monolith (PostgreSQL, Redis). Tailwind CSS, Shadcn UI, and microservice architectures are excluded.
4. **No Premature Implementation:** This project phase is strictly documentation-only; no code, database migrations, or UI components may be implemented.

---

## 25. Open Questions / TBD Summary

The following eleven items require institutional confirmation (detailed in [`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md)):
1. **`REQ-TBD-01`:** Specific ERP vendor platform and integration protocol for full reflection.
2. **`REQ-TBD-02`:** Field-level Excel/Word schemas for Attachments 1-3, Enclosures 1-4, and TNU Protocol.
3. **`REQ-TBD-03`:** Appraisal track boundary definition for Lab Technicians, Teaching Associates, and Technical Assistants.
4. **`REQ-TBD-04`:** Mathematical parameter weightages for the TNU Protocol and statutory SCM/ECM committee compositions.
5. **`REQ-TBD-05`:** Specific compensation revision slabs for Group-D and Faculty appraisal increments.
6. **`REQ-TBD-06`:** Resignation intake and clearance interface in Module I prior to Dean acceptance.
7. **`REQ-TBD-07`:** Institutional Identity Provider (SSO) and authentication model for external subject experts.
8. **`REQ-TBD-08`:** Operational distinction and lifecycle handoff between Letter of Intent (LOI) and formal Appointment Letter.
9. **`REQ-TBD-09`:** Policy confirmation regarding administrative allowances for additional responsibilities.
10. **`REQ-TBD-10`:** Outbound notification gateway configurations (SMTP host and SMS/WhatsApp endpoints).
11. **`REQ-TBD-11`:** Statutory document retention schedules for candidate CVs, scorecards, and audit logs.

---

## 26. Requirement Traceability Framework

Requirements specified herein link directly to the baseline traceability IDs established in [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) and the detailed functional requirements in `docs/03-functional-requirements/`:
- **Module I Core:** `MOD1-CDB-01`, `MOD1-ORG-01`, `MOD1-CHG-01`, `MOD1-APP-01`, `MOD1-DAT-01`
- **Module II Sourcing & Selection:** `MOD2-MP-FAC-01`, `MOD2-MP-FAC-02`, `MOD2-MP-NF-01`, `MOD2-RES-01`, `MOD2-SRC-01`, `MOD2-SRC-02`, `MOD2-SEL-FAC-01`, `MOD2-SEL-NF-01`, `MOD2-ONB-01`
- **Module III Performance:** `MOD3-GD-EVAL-01`, `MOD3-GD-APP-01`, `MOD3-GD-ANN-01`, `MOD3-KRA-SET-01`, `MOD3-KRA-QTR-01`, `MOD3-KRA-INT-01`, `MOD3-FAC-ELG-01`, `MOD3-FAC-VER-01`, `MOD3-FAC-ECM-01`, `MOD3-FAC-SAL-01`

Complete atomized mapping is detailed in [`04-REQUIREMENTS-TRACEABILITY.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/04-REQUIREMENTS-TRACEABILITY.md).

---
*End of Document — Project Requirements Specification.*
