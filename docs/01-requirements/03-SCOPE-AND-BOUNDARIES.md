# Scope and System Boundaries
## University HR Change Management & Automation System

**Document Identifier:** `DOC-01-SCB-03`  
**Phase:** Phase 1 — Requirements Engineering & Specification (Documentation-Only)  
**Location:** `docs/01-requirements/03-SCOPE-AND-BOUNDARIES.md`  
**Status:** Approved Scope & Boundaries Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Document Purpose

This document formally demarcates the operational, functional, architectural, and data boundaries of the University HR Change Management & Automation System. It establishes explicit inclusion and exclusion criteria, delimits boundaries between functional modules, defines data ownership, details integration touchpoints, and delineates the documentation-only boundaries governing the current project phase.

Clear scope definition prevents architectural creep, protects module encapsulation, and ensures all stakeholders maintain a shared understanding of system responsibilities versus external platform responsibilities.

---

## 2. In-Scope Capabilities

The system scope comprises four core capability domains:

### 2.1 Module I: HR Change Management & Core Employee Database
- **Central Employee Database [A]:** Single source of truth for employee master profiles, employment history, reporting structures, and service conditions.
- **Dynamic Organization Chart [A]:** Real-time, vector-rendered organizational hierarchy reflecting immediate structural updates upon approved changes.
- **Digital Employee File [A]:** Longitudinal electronic dossier aggregating historical appointments, qualification certificates, performance ratings, and service modifications.
- **Ten Standardized Service Change Formats [A]:** Standardized digital workflows for Formats (a) through (j).
- **Two-Level Sequential Approval Workflow [A]:** Level 1 HR vetting followed strictly by Level 2 Senior Management approval.
- **Effective-Date Database Methodology [A]:** Scheduled activation of approved modifications based on `effective_date`.
- **Immutable Audit Logging & Version History [A]:** Non-destructive temporal tracking capturing actor attribution, timestamps, and full state diffs.
- **Dynamic Reporting Engine [A]:** On-demand operational reporting with administrative capabilities to add, modify, or retire report templates.
- **ERP Reflection Boundary [A/C]:** Transactional synchronization ensuring the Central Employee Database is fully reflected in the university ERP.

### 2.2 Module II: Recruitment & Selection Automation
- **Multi-Track Manpower Planning [A]:**
  - *Academic:* Semester-based cycle triggered $\ge$ 4 months in advance, Dean teaching load submission (Attachment 1) within 15 days, 3-month HR vetting, 7-day Pro-Chancellor approval, and 7-day advertisement launch.
  - *Non-Academic:* Annual cycle managed by HR and Department Heads, strictly restricted to one (1) planned requisition per year.
- **Urgent Replacement Workflow [A]:** Resignation acceptance by School Dean initiates replacement countdown, alerts Head HR, and authorizes ad-hoc MRF.
- **Open Positions Tracker [A]:** Centralized ledger (Attachment 3) maintained within 30 days of approval with weekly executive progress reports.
- **Omnichannel Sourcing & Central CV Database [A]:** Application ingestion from print media, university website, social channels (LinkedIn, Facebook, Instagram), designated email inboxes, employee referrals, and Internshala.
- **Statutory Screening [A]:** Automated candidate classification and shortlisting against UGC and statutory criteria.
- **Recruiter Calling Sheet (RCS) [A]:** Phone screening evaluation ledger reviewed by HOD-HR and pre-approved by Management before interviews.
- **Differentiated Selection Workflows [A]:**
  - *Academic:* Statutory Selection Committee Meetings (SCM) comprising Vice Chancellor, Dean, HOD, and External Subject Expert, with digital scoring.
  - *Non-Academic:* Three-round sequential interview evaluation (Technical, HR, Management) assessing Job Knowledge, Communication Skills, and Attitude.
- **Pre-Onboarding & LOI Issuance [A]:** Automated Letter of Intent (LOI) generation, "Yet to Join" pipeline monitoring, and automated notifications to Deans, HODs, and IT.

### 2.3 Module III: Performance Management Automation
- **Three Strictly Segregated Appraisal Tracks [A]:**
  - *Sub-System 1 (Group-D / Band I Staff):* Monthly evaluation by HOD (Enclosure 1), strict due date on 7th, 3-day grace period up to 10th with daily reminders, automated submission lockout, mandatory VP-Administration approval, monthly collation (Enclosure 2), annual milestone report at 1 year from DOJ with parameter-wise weighted averages, and mandatory probation verification gate.
  - *Sub-System 2 (General Staff KRA/KPI):* 30-day onboarding goal-setting from DOJ locked by HR and Management; quarterly reviews (Q1–Q4) with 90-day intimation, 20-day reminder, 15-day submission, and 7-day supervisor verification; annual outcome handshake into Module I.
  - *Sub-System 3 (Faculty Annual Appraisal via ECM):* Monthly automated eligibility check on the 10th (probation completed + $\ge$ 12 months service), 7-day self-appraisal submission (Enclosure 1), multi-department verification (Dean, R&D, Placement, HR) with circular discrepancy loop, monthly statutory Evaluation Committee Meeting (ECM), digital score sheet (Enclosure 2), TNU Protocol matrix compilation (Enclosure 3), Management approval, salary cycle tracking, and auto-generated compensation letters.

### 2.4 Cross-Cutting Shared Capabilities
- Common master data primitives, universal workflow engine, timeline and SLA scheduler, asynchronous notification engine, central digital form/template catalog, document and binary asset management, and Role-Based Access Control (RBAC).

---

## 3. Out-of-Scope Capabilities

To ensure clear focus and prevent operational overreach, the following systems, functions, and processes are explicitly designated as **OUT OF SCOPE**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   EXPLICITLY OUT OF SCOPE                                        │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. Core ERP Financial Ledgers & General Accounting                                               │
│ 2. End-to-End Payroll Disbursement, Bank NACH/NEFT Batch Processing, and Tax Filing              │
│ 3. Physical Biometric Attendance Hardware & Turnstile Access Controllers                         │
│ 4. Student Information Systems (SIS), Admissions, Fee Collection, and Course Grading            │
│ 5. Learning Management System (LMS) Delivery (Moodle, Blackboard, Canvas)                        │
│ 6. Public Self-Service Applicant Portal (Candidates do not create self-managed accounts)          │
│ 7. Travel, Expense, and Medical Claim Management Systems                                         │
│ 8. Campus Facility Booking & Vehicle Fleet Management Systems                                    │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

1. **ERP Financial Accounting & General Ledger:** The system manages service condition records (salary scales, allowances, bands), but does not replace the university's financial accounting, balance sheets, or general ledgers.
2. **Complete Payroll Computation & Banking Disbursement:** The system tracks salary adjustments and exports them to the next salary cycle, but actual payroll calculation (gross-to-net deductions, provident fund contributions, tax TDS withholding, payslip rendering, and direct bank transfers) remains inside the external Payroll/ERP system.
3. **Hardware-Level Time & Attendance:** Physical biometric time clocks, RFID access turnstiles, and daily swipe-card logs are managed by campus security infrastructure.
4. **Student Lifecycle Management:** Admissions, academic curriculum registries, student fee collections, and examination grading remain within dedicated academic software.
5. **Public Applicant Self-Service Portal:** The sourcing engine captures incoming applications from designated channels (emails, web forms, social media, Internshala) into the Central CV Database; candidates do not maintain long-term self-service portal accounts.

---

## 4. Module Boundaries & Encapsulation

Each module functions as an encapsulated domain within a cohesive **Modular Monolith** architecture:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               MODULAR ENCAPSULATION BOUNDARIES                                   │
├─────────────────────────────────┬────────────────────────────────┬───────────────────────────────┤
│ MODULE I DOMAIN BOUNDARY        │ MODULE II DOMAIN BOUNDARY      │ MODULE III DOMAIN BOUNDARY    │
│ • Owns: Employee Master Records │ • Owns: Manpower Requisitions  │ • Owns: Monthly GD Forms      │
│ • Owns: Org Chart Hierarchy     │ • Owns: Teaching Load Vetting  │ • Owns: GD Annual Reports     │
│ • Owns: Digital Employee Dossier│ • Owns: CV Database & Sourcing │ • Owns: KRA/KPI Goal Sheets   │
│ • Owns: 10 Service Change Logs  │ • Owns: Screening & RCS Sheets │ • Owns: Quarterly Reviews     │
│ • Owns: Effective Date Engine   │ • Owns: SCM / Interview Sheets │ • Owns: Faculty Self-Appraisal│
│ • Owns: ERP Outbox Table        │ • Owns: LOI & "Yet to Join"    │ • Owns: ECM Scorecards & Matrix│
├─────────────────────────────────┴────────────────────────────────┴───────────────────────────────┤
│ SHARED FOUNDATION BOUNDARY: Auth (RBAC), Notification Queue, Form Catalog, Audit Ledger, Storage │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Module Boundary Invariants
1. **Module II never writes directly to Module I database tables:** When a candidate completes onboarding, Module II emits an event (`ONBOARDING_COMPLETED`), and Module I consumes this event to create the master employee record.
2. **Module III never updates Module I salary fields directly:** When an appraisal outcome is approved by Management, Module III raises a formal `ServiceChangeRequest` inside Module I, preserving the mandatory two-level approval and audit trail.
3. **Module I never mutates recruitment requisitions:** Module I accepts resignations and signals Module II via an event, but never manipulates Module II trackers or selection scorecards.

---

## 5. Cross-Module Boundaries & Transactional Handshakes

The boundaries between modules are bridged strictly via four formal transactional handshakes:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               CROSS-MODULE TRANSACTIONAL HANDSHAKES                              │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│ [1] ONBOARDING HANDSHAKE (MOD II ──► MOD I)                                                      │
│     Trigger: Candidate accepts LOI and completes Day-1 Onboarding.                               │
│     Boundary Crossing: Module II emits payload (personal info, qualifications, band, DOJ).       │
│     Action: Module I instantiates Employee Master Record & connects node in Dynamic Org Chart.   │
│                                                                                                  │
│ [2] RESIGNATION TRIGGER HANDSHAKE (MOD I ──► MOD II)                                             │
│     Trigger: School Dean accepts employee resignation in Module I.                               │
│     Boundary Crossing: Module I emits resignation event (employee ID, post, exit date).          │
│     Action: Module II starts replacement clock, notifies Head HR, and authorizes ad-hoc MRF.     │
│                                                                                                  │
│ [3] APPRAISAL MASTER SYNC HANDSHAKE (MOD I ──► MOD III)                                          │
│     Trigger: Continuous master data synchronization.                                             │
│     Boundary Crossing: Module I exposes employee DOJ, probation status, supervisor, and band.    │
│     Action: Module III evaluates eligibility (GD 1-yr, Faculty 12-mo) and routes review forms.   │
│                                                                                                  │
│ [4] APPRAISAL OUTCOME HANDSHAKE (MOD III ──► MOD I)                                              │
│     Trigger: Management approves annual appraisal outcome (GD, Staff KRA, or Faculty ECM).       │
│     Boundary Crossing: Module III injects approved revision (salary increment, promotion, band). │
│     Action: Module I creates a formal Service Change Request, bypassing duplicate manual entry.  │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 6. External-System Boundaries

The system interfaces with several external institutional systems. Where exact platforms or protocols are undefined in source briefs, they are governed as open items:

| External System | Functional Boundary & Interaction | Boundary Nature | Platform / Protocol Status |
|---|---|---|---|
| **University ERP** | Master employee records, structural units, designations, and approved service condition changes are reflected into the ERP. | Outbound synchronization via Transactional Outbox. | **`[E] TBD`** (Specific ERP platform, e.g. SAP/Oracle/Banner, and protocol are unconfirmed). |
| **Enterprise Identity Provider (IdP)** | Authentication of university faculty, staff, and leadership for Single Sign-On (SSO). | Inbound SAML / OAuth / OIDC authentication tokens. | **`[E] TBD`** (Google Workspace, Microsoft Entra ID, or LDAP unconfirmed). |
| **External Subject Experts** | Statutory Selection Committee (SCM) members evaluating candidates remotely. | Secure, time-limited evaluation session. | **`[E] TBD`** (Magic link or OTP portal authentication unconfirmed). |
| **Outbound Email Relay** | Dispatches automated notifications, SLA warnings, advance intimations, and PDF letters. | Asynchronous SMTP relay connection. | **`[E] TBD`** (Host configuration and credentials unconfirmed). |
| **Object Storage Provider** | Storage of binary artifacts (CVs, degree certificates, research proof, PDF letters). | S3-compatible object storage API. | **`[E] TBD`** (On-premises MinIO vs. Managed Cloud S3 unconfirmed). |
| **External Sourcing Channels** | Incoming CV ingestion from print ads, website, social media, and Internshala. | Batch ingestion / email capture / webhook feeds. | **`[E] TBD`** (Detailed ingestion formats unconfirmed). |

> [!CAUTION]
> **Anti-Invention Constraint:**  
> The system boundary shall not invent proprietary interfaces for external systems. All external touchpoints must interact through standardized abstraction adapters until institutional specifications are finalized.

---

## 7. Data Ownership Boundaries

Data entities are strictly owned by specific domains to guarantee single-source-of-truth integrity:

| Data Entity Domain | Authoritative Owner | Read Permissions | Mutation Rights |
|---|---|---|---|
| **Employee Master Data** | Module I | All Modules, All Users (Scoped) | Module I Only (via approved 2-level changes) |
| **Org Chart Hierarchy Nodes** | Module I | All Modules, All Users | Module I Only (via approved structural changes) |
| **Digital Employee Files (Dossiers)** | Module I | HR, Dean/HOD (Scoped), Employee (Self) | Module I Only (Append-only) |
| **Service Change Requests (Formats a–j)** | Module I | Initiator, HR, Senior Management | Module I State Machine Only |
| **Manpower Requisitions & MRFs** | Module II | Deans, HODs, HR, Pro-Chancellor | Module II State Machine Only |
| **Central CV Repository** | Module II | HR Recruiters, HOD-HR | Module II Ingestion Engine Only |
| **Recruitment Evaluation Scorecards** | Module II | SCM Members, Interview Panels, HR | Module II Selection Workflow Only |
| **Group-D Evaluation Forms & Reports** | Module III | HODs, HR, VP-Administration | Module III Group-D State Machine Only |
| **KRA/KPI Goal Sheets & Reviews** | Module III | Employee, Supervisor, HR, Management | Module III KRA State Machine Only |
| **Faculty Self-Appraisals & ECM Sheets** | Module III | Faculty, Verifiers, ECM Panel, Mgmt | Module III ECM State Machine Only |
| **Audit Logs & Version Ledgers** | Shared Platform | System Auditor, Compliance Officers | Append-Only (Immutable System Engine) |

---

## 8. Integration Boundaries & Guarantees

All inter-module integrations must adhere to the following architectural guarantees:
1. **Eventual Consistency via Outbox:** Cross-module state updates and outbound ERP synchronizations must commit an event payload into an outbox table within the local transaction, guaranteeing message delivery even across temporary network partitions.
2. **Idempotence:** Every integration handler must accept an idempotent idempotency key (`idempotency_key`) to prevent duplicate processing of financial increments, master record creations, or requisition triggers.
3. **Decoupled Failure Domains:** A failure in outbound ERP synchronization or external email relay must never roll back an approved local HR service change or appraisal sign-off.

---

## 9. Current-Phase Documentation Boundaries

This document operates strictly within **Phase 1 (Requirements Documentation)** of the overall project lifecycle:

- **Strictly In-Scope for Current Phase:**
  - Complete requirements elicitation, analysis, and formalization.
  - Identification and documentation of all explicit rules, logical implications, approved technical decisions, proposed details, and open questions.
  - Creation of the seven formal Requirements Documentation files in `docs/01-requirements/`.
- **Strictly Out-of-Scope for Current Phase:**
  - Creation of application code, scripts, or executable files.
  - Creation of database schemas, SQL DDL, tables, or database migrations.
  - Creation of REST API controllers, route handlers, or serialization logic.
  - Creation of Next.js components, JSX wireframes, or CSS stylesheets.
  - Creation or execution of automated test scripts.
  - Modification of files outside `docs/01-requirements/`.

---
*End of Document — Scope and System Boundaries.*
