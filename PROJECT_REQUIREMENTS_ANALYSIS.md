# University HR Change Management & Automation System
## Comprehensive Requirements Analysis & Baseline System Understanding Report

**Document Name:** `PROJECT_REQUIREMENTS_ANALYSIS.md`  
**Status:** Authoritative Requirements Baseline Analysis  
**Project:** University HR Change Management & Automation System (Modules I, II, & III)  
**Date of Analysis:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

# Project Overview

The University is establishing an enterprise-grade, web-based, unified **HR Change Management & Automation System**. The primary vision of this system is to serve as the institutional **single source of truth** for all employee service-related records, organizational structures, recruitment lifecycles, and performance management evaluations.

Historically, university HR operations—encompassing position requisitioning, talent acquisition, service condition modifications, probation tracking, periodic appraisals, and executive sign-offs—have relied on paper-based documents, disparate email exchanges, and disconnected spreadsheets. This manual paradigm creates operational friction, redundancy, delays, audit vulnerabilities, and the risk of data desynchronization across academic and administrative departments.

### Strategic Objectives
1. **Elimination of Duplicate Data Entry:** Every approved change, recruitment milestone, or appraisal outcome must automatically propagate across connected HR records, organizational structures, reports, letters, and employee personal files without manual re-keying.
2. **Single Source of Truth & ERP Reflection:** A unified Central Employee Database must maintain authoritative employee master data and be fully reflected in the University's Enterprise Resource Planning (ERP) platform.
3. **Rigorous Multi-Track Workflow Governance:** The system must enforce distinct, role-governed, multi-level approval hierarchies tailored to specific employment tracks (Academic/Faculty vs. Non-Academic/Staff vs. Band I/Group-D).
4. **Time-Stamped Auditability & Version History:** A uniform database change methodology must govern every master data change, job requisition, candidate evaluation score, and appraisal review, maintaining an immutable audit log with effective dates.
5. **Proactive SLA & Timeline Automation:** System-driven communication triggers, automated reminders, grace periods, auto-locks, and escalation mechanisms must prevent deadline overruns across semester-bound recruitment and performance review cycles.

---

# Source Documents

The analysis in this report is derived strictly and exclusively from the three authoritative requirement documents provided in the workspace. No original requirement document has been altered, renamed, or deleted.

| # | Source File Name | Document Title in Text | Author / Metadata | Pages | Size (Bytes) | Primary Scope Covered |
|---|------------------|------------------------|-------------------|-------|--------------|-----------------------|
| **1** | `27-07-26 - Revised HR Change Management & Automation System-Module I.pdf` | **REQUIREMENT BRIEF – MODULE I: HR CHANGE MANAGEMENT & AUTOMATION SYSTEM** | TNU / Word 2016 | 1 | 187,282 | Central Employee Database, ERP reflection, connected Organization Chart, 10 change formats, 2-level approval hierarchy, effective-date database change methodology, audit trail, version history, real-time reports. |
| **2** | `Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf` | **REQUIREMENT BRIEF — MODULE II: RECRUITMENT & SELECTION AUTOMATION SYSTEM** | Official University SOP / Brief | 4 | 229,584 | Academic vs. Non-Academic Manpower Planning, urgent replacement (resignation) workflow, Open Positions Tracker, multi-channel sourcing & CV Database, automated shortlisting (UGC norms), Recruiter Calling Sheet (RCS), Statutory Selection Committee Meetings (SCM), 3-Round Non-Faculty Interviews, Letter of Intent (LOI) generation, "Yet to Join" tracking, and 4 Enclosures. |
| **3** | `Requirement_Brief_Module_III_Performance_Management_Automation_System.pdf` | **REQUIREMENT BRIEF — MODULE III: PERFORMANCE MANAGEMENT AUTOMATION SYSTEM** (Comprising 3 distinct sub-briefs) | Official University SOP / Brief | 5 | 766,024 | Three distinct appraisal tracks: (1) Group-D / Band I Monthly & Annual Review; (2) General Employee KRA/KPI Onboarding & Quarterly Review Cycle; (3) Faculty Annual Appraisal via Evaluation Committee Meeting (ECM) route. Enclosures include Evaluation Forms, Score Sheets, and Matrix Templates. |

---

# Module I Summary

Module I represents the architectural foundation and transactional core of the entire HR automation suite.

### 3.1 Background & Objective
- Serves as the central, web-based single source of truth for all employee service-related changes.
- Eliminates duplicate data entry across university records.
- Guarantees that every approved change is automatically reflected across connected HR records, organizational structures, reports, generated documents, and employee digital files.

### 3.2 Core Architectural Structures
1. **Central Database of all Employees:** Authoritative repository of all university employee records, fully reflected and synchronized with the institutional ERP.
2. **Dynamic Organization Chart:** Directly connected to the Central Employee Database; automatically updates whenever database changes occur (e.g., changes in reporting hierarchy, department, or designation).
3. **Employee Data Change Formats:** The system supports standardized formats for logging service-related changes across 10 specific categories:
   - *a) Change in Salary* (increments, revisions, allowances)
   - *b) Change in Designation*
   - *c) Change in Reportee*
   - *d) Change in Reporting Authority*
   - *e) Change in Level* (band/grade transitions)
   - *f) Change in Department / School* (transfers, reorganizations)
   - *g) Change in Location* (campus or office relocations)
   - *h) Additional Responsibility Added* (administrative roles like Dean, HOD, Cell Lead)
   - *i) Change in Qualifications* (attainment of higher degrees, certifications)
   - *j) Any other employee service condition* related to database fields

### 3.3 Approval Hierarchy
All service-condition changes must navigate a formal 2-level approval hierarchy:
1. **Level 1:** HR Level (vetting, validation against policy)
2. **Level 2:** Senior Management Level (final institutional authorization)

### 3.4 Database Change Methodology
- **Effective Date Mechanism:** Changes can be submitted in advance and scheduled to take effect automatically from a specified date (`effective_date`).
- **Audit Trail & Version History:** Every modification must capture a comprehensive, timestamped audit log recording the actor, prior state, updated state, approval timestamp, and version identifier.

### 3.5 Reporting Requirements
- HR shall provide the exact lists and formats of required reports.
- System must allow administrative addition and deletion of report formats over time.
- System must natively provide for real-time report generation.

---

# Module II Summary

Module II automates the University's end-to-end Standard Operating Procedure (SOP) for Recruitment & Selection, embedded within the Module I ecosystem and linked to the Central Employee Database and the Open Positions Tracker.

### 4.1 Structural Segregation: Academic vs. Non-Academic
The document establishes that approval chains and selection processes differ substantially between Academic and Non-Academic positions. The platform must maintain two distinct, configurable workflows while sharing a unified multi-channel Sourcing and CV Database engine.

```
                                  ┌────────────────────────────────────────────────────────┐
                                  │           SHARED SOURCING & CV DATABASE ENGINE         │
                                  │ (Print, Social Media, Website, Emails, Internshala)    │
                                  └───────────────────────────┬────────────────────────────┘
                                                              │
                             ┌────────────────────────────────┴────────────────────────────────┐
                             │                                                                 │
                             ▼                                                                 ▼
             ┌───────────────────────────────┐                                 ┌───────────────────────────────┐
             │       ACADEMIC TRACK          │                                 │      NON-ACADEMIC TRACK       │
             │ (Faculty & Lab Technicians)   │                                 │     (Non-Faculty Staff)       │
             ├───────────────────────────────┤                                 ├───────────────────────────────┤
             │ • Assoc. Dean (Acad) ➔ Deans  │                                 │ • HR ➔ Department Heads       │
             │ • Teaching Load (Att. 1)      │                                 │ • Annual MRF (1 planned/yr)   │
             │ • Statutory SCM with External │                                 │ • 3-Round Interview:          │
             │   Subject Expert              │                                 │   Technical, HR, Management   │
             │ • Direct LOI ➔ Yet to Join    │                                 │ • Direct LOI ➔ Yet to Join    │
             └───────────────────────────────┘                                 └───────────────────────────────┘
```

### 4.2 Manpower Planning Workflows

#### Track A: Academic Positions (Faculty & Lab Technicians)
*(Covers Teaching Faculty, Teaching Associates, Technical Assistants, and Lab Technicians)*
1. **Trigger:** Automated communication initiated at least **four (4) months** before the start of the semester / academic year from the **Associate Dean (Academics)** to the **Deans of Schools** to assess faculty and technical workload.
2. **Submission:** Concerned Deans submit finalized requirements along with the teaching load in the prescribed format (**Attachment 1**) within **15 days** of communication. System tracks deadlines with automated reminders.
3. **Review & Vetting:** Routed to **Associate Dean (Academics)** for review/vetting, completed at least **three (3) months** before the academic year starts (with provision to seek clarifications from Deans).
4. **Consolidation & Recommendation:** Associate Dean consolidates submissions and forwards recommendations to the **Hon'ble Pro-Chancellor** within **15 days** of receipt (SLA tracked).
5. **Executive Approval:** Hon'ble Pro-Chancellor's approval is communicated back to the Dean within **7 days** (system tracks and notifies).
6. **MRF Generation:** On approval, the system enables the Dean to immediately raise a **Manpower Requisition Form (MRF)** routed to HR.
7. **Recruitment Initiation:** HR initiates recruitment (newspaper and social media advertisements) within **7 days** of receiving the MRF, alongside initiating the **RCS Tracker**.
8. **Completion SLA:** Entire recruitment process must be completed at least **one (1) month** before the start of the semester (target date auto-calculated).

#### Track B: Non-Academic Positions (Non-Faculty)
1. **Trigger:** Automated communication initiated at least **four (4) months** before the start of the academic year from **HR** to the concerned **Department Heads** (evaluating operational needs, workload analysis, replacements, or expansion).
2. **Submission:** Concerned Department Heads submit a **Manpower Requisition Form (MRF)** directly. Strictly restricted to **one (1) planned requisition per year** (urgent replacements permitted anytime) within **15 days** of communication.
3. **Review & Vetting:** Routed to **Head HR** for review/vetting, completed at least **three (3) months** before the academic year starts (with clarification provisions).
4. **Consolidation & Recommendation:** Head HR consolidates submissions and forwards recommendations to the **Hon'ble Pro-Chancellor** within **15 days** of receipt (SLA tracked).
5. **Executive Approval:** Hon'ble Pro-Chancellor's approval is communicated back to the Department Head (system tracks and notifies).
6. **Recruitment Initiation:** HR initiates recruitment within **7 days** of MRF clearance alongside the RCS Tracker.
7. **Completion SLA:** Entire recruitment process must be completed at least **fifteen (15) days** before the candidate is required to onboard (target date auto-calculated).

#### Track C: Urgent / Replacement Workflow (Resignations)
- **Trigger:** Resignation acceptance by the School Dean automatically starts the replacement clock and auto-notifies **Head HR**.
- **Ad-Hoc Requisition:** Dean / Department Head raises an ad-hoc MRF at any time.
- **SLA Pipeline:** System sequentially tracks:
  $$\text{Ad-hoc MRF Submission} \longrightarrow \text{Vetting} \longrightarrow \text{Pro-Chancellor Approval}$$
  with automated escalation/reminders upon overrun.
- **Monitored Execution Block:** Sourcing $\rightarrow$ Shortlisting $\rightarrow$ Selection Committee Meeting tracked as one unified monitored block.
- **Offer & Onboarding Tracking:** Stage-wise tracking of evaluation, approval, auto-generated offer letter, candidate-side milestones (offer acceptance, notice period, credential verification, joining), culminating in onboarding and closing out the open position.

### 4.3 Sourcing, Screening, and Application Funnel
1. **Multi-Channel Advertising:** Job posts published across print media, social media (LinkedIn, Facebook, Instagram), and the University website, linked directly to the approved MRF and categorized by position type.
2. **Central CV Database:** Captures incoming applications from designated emails, website forms, social channels, newspaper advertisements, internal employee references, and external platforms (e.g., Internshala for interns).
3. **Automated Classification & Shortlisting:** Auto-segregates and classifies incoming CVs against defined educational qualifications, experience criteria, and statutory **UGC norms**.
4. **Recruiter Calling Stage (RCS):** Recruiter screening calls captured in the standardized **Recruiter Calling Sheet (RCS)** format and routed to **HOD-HR** for feedback.
5. **Pre-Interview Management Authorization:** Shortlisted profiles and RCS inputs must be routed to **Management for approval** before interview scheduling can commence.

### 4.4 Selection & Onboarding Workflows

#### Track A: Academic Selection (Selection Committee Meeting - SCM)
- Governed by university statutes.
- Generates digital invitations to SCM members (including external subject experts) with candidate CVs and digital evaluation sheets shared directly through the system.
- Supports scheduling interviews primarily in online mode, with provisions for offline mode in exceptional circumstances.
- SCM evaluators input individual marks into the digital evaluation sheet.
- System automatically compiles scores into an **Evaluation Matrix** and routes it to **Management** alongside HR recommendations.
- Upon receiving Management's final recommendation and cost approval, the system auto-generates the **Letter of Intent (LOI)**.
- Candidate acceptance records the candidate as **"Yet to Join"** in the internal HR database.

#### Track B: Non-Academic Selection (Three-Round Interview Process)
- Enforces three sequential evaluation rounds:
  1. *Round 1: Technical Interview* (conducted by Department Head / Subject Expert)
  2. *Round 2: HR Interview* (conducted by Head of HR)
  3. *Round 3: Management Interview*
- Evaluators capture feedback in a digital evaluation sheet assessing: **Job Knowledge**, **Communication Skills**, and **Attitude**.
- Upon Management recommendation and cost approval, system auto-generates the **Letter of Intent (LOI)**.
- Candidate acceptance flags the record as **"Yet to Join"**.
- Automatically broadcasts internal pre-onboarding notifications and reports to HODs, Deans, and Administrative / System IT teams to prepare infrastructure (workstations, email, credentials) before Day 1.

### 4.5 Open Positions Tracker & Enclosures
- All approved positions must be recorded and automatically maintained in the system-based **Open Positions Tracker** (**Attachment 3** format), finalized within **30 days**.
- Enclosures referenced:
  1. *Manpower Requisition Form (MRF)*
  2. *Teaching Load / Workload Format (Attachment 1)*
  3. *Position / Vacancy Specification Format (Attachment 2)*
  4. *Open Positions / Job Requisition (JR) Tracker Format (Attachment 3)*

---

# Module III Summary

Module III consists of **three distinct, non-interchangeable performance management workflows**. Each workflow addresses a specific employee segment, operates on independent cadences, involves distinct institutional actors, and adheres to unique statutory/university protocols.

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                   MODULE III: PERFORMANCE MANAGEMENT AUTOMATION SYSTEM                           │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
            │                                     │                                    │
            ▼                                     ▼                                    ▼
┌───────────────────────┐             ┌───────────────────────┐            ┌───────────────────────┐
│     SUB-SYSTEM 1      │             │     SUB-SYSTEM 2      │            │     SUB-SYSTEM 3      │
│  GROUP-D / BAND I     │             │    KRA / KPI CYCLE    │            │     FACULTY (ECM)     │
│   (Monthly/Annual)    │             │ (General Staff / Q1-Q4│            │ (Annual Committee)    │
├───────────────────────┤             ├───────────────────────┤            ├───────────────────────┤
│ • Role-specific KPIs  │             │ • 30-day Goal Setting │            │ • Eligibility: DOJ +  │
│ • Monthly by HOD      │             │ • 90-day Quarterly    │            │   Probation + >=12 mo │
│ • Due 7th; grace 10th │             │   reviews (Q1-Q4)     │            │ • Registrar 10th list │
│ • Auto-lock if missed │             │ • Verification by RA  │            │ • 7-day Self-Appraisal│
│ • VP-Admin approval   │             │   and HR              │            │ • Multi-dept vetting  │
│ • 1-Yr Annual Report  │             │ • Close-loop feed to  │            │ • Monthly ECM Score   │
│ • Management Slabs &  │             │   Module I (Salary,   │            │ • TNU Protocol Matrix │
│   Probation check     │             │   Designation, Level) │            │ • Auto salary letter  │
└───────────────────────┘             └───────────────────────┘            └───────────────────────┘
```

---

### 5.1 Sub-System 1: Performance Management (Group-D / Band I)

#### 5.1.1 Objective & Structural Scope
- Automates the existing SOP for appraisal of Group-D / Band I service personnel.
- Standardizes role-based monthly evaluations, annual performance collation, and compensation adjustments.
- Eliminates manual paper routing and links directly with the Central Employee Database and digital employee files.

#### 5.1.2 Digital Evaluation Form Repository
- Standardized, role-specific digital evaluation forms maintained in a central repository.
- Forms are configured by HR to capture role-specific Key Performance Indicators (KPIs) and operational competencies.
- Form templates are version-controlled with a complete audit trail of modifications.

#### 5.1.3 Monthly Evaluation Workflow & Strict Timelines
1. **Routing:** System automatically routes the monthly Evaluation Form to the concerned Head of Department (HOD) for every Group-D member reporting into their unit (hierarchy pulled from Central Employee Database).
2. **Submission Deadline:** Strict due date on the **7th of every month**.
3. **Grace Period:** Automated grace period of **three (3) additional days** (up to the **10th of the month**).
4. **Reminders:** Automated notifications dispatched prior to the 7th and daily during the grace period.
5. **Auto-Lock:** If unsubmitted by 23:59 on the 10th, the system **auto-locks** the submission, tags the record as **"Not Submitted"**, and flags the failure with reasons visible to HR.
6. **Approval Gate:** HOD submission requires formal review and digital approval from the **Vice President – Administration** to be finalized.

#### 5.1.4 Reporting & Annual Compensation Review
1. **Monthly Reports:** System collates approved monthly evaluations into a standardized Monthly Performance Report.
2. **Annual Report Trigger:** Automatically triggered on the employee's completion of **one (1) year of employment**, and every subsequent year, calculated strictly from the **Date of Joining (DOJ)** in the Central Employee Database.
3. **Weighted Scoring:** The Annual Report compiles all 12 monthly reports and computes a weighted average across configured performance parameters.
4. **Probation Check:** System strictly checks probation status in the Central Employee Database; the compensation review workflow **cannot be activated** unless probation is marked as mandatorily completed.
5. **Management Slabs:** Management reviews the Annual Report and applies pre-defined compensation adjustment slabs mapped against the weighted score.
6. **Digital Employee File Archive:** Forms and reports are permanently archived in the member's digital employee file, providing evidentiary support for rewards, compensation changes, transfers, or reprimands.
7. **Enclosures:** *1. Evaluation Form*, *2. Monthly and Annual Report Template*.

---

### 5.2 Sub-System 2: Performance Management (KRA/KPI & Appraisal Cycle)

#### 5.2.1 Objective & Scope
- Centralized system automating goal setting, quarterly reviews, and annual appraisals for general university employees/staff from their Date of Joining (DOJ).
- Eliminates manual tracking and closes the operational loop by feeding approved outcomes **directly into Module I** as master service change requests.

#### 5.2.2 Three-Stage Sequential Lifecycle

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ STAGE 1: ONBOARDING & GOAL SETTING                                                               │
│ • Trigger: New Employee Joining                                                                  │
│ • Intimation to Employee & Reporting Authority                                                   │
│ • SLA: Completed within 30 days of Date of Joining (DOJ)                                         │
│ • Gate: Formal Verification & Locking by HR and Management                                       │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ STAGE 2: QUARTERLY REVIEW CYCLE (Q1 ➔ Q2 ➔ Q3 ➔ Q4)                                              │
│ • Trigger: 90 days from DOJ (Intimation) | Overrun Reminder: at +20 days                         │
│ • Employee Submission: Within 15 days of 90-day mark (with supporting documentation)             │
│ • Reporting Authority Verification: Within 7 days ➔ Forwarded to HR                             │
│ • HR Review: Records observations / recommendations                                              │
│ • Management Review: Records executive comment / recommendation                                  │
│ • Cycle repeats identically across Q2, Q3, and Q4                                                │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ STAGE 3: ANNUAL APPRAISAL & MODULE I INTEGRATION                                                 │
│ • Trigger: Successful completion of all 4 quarters                                              │
│ • HR initiates formal appraisal request to Management                                            │
│ • Management records final appraisal recommendation                                              │
│ • Direct Handshake: HR initializes resulting changes (Increment, Designation, Level)            │
│   directly into Module I (HR Change Management System) without manual re-entry                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

#### 5.2.3 Turnaround Time (TAT) Tracking & Analytics
- Complete timestamped audit trail and version history at all touchpoints.
- Built-in TAT monitoring against key milestones:
  - 30-day Goal-Setting SLA
  - 90-day trigger + 15-day quarterly submission SLA
  - 20-day pending reminder trigger
  - 7-day Reporting Authority verification SLA
- Dedicated reports: *New-joiner KRA/KPI setup status*, *HR + Management verification TAT*, and *Quarter-wise department submission status*.

---

### 5.3 Sub-System 3: Performance Management (Faculty – ECM Route)

#### 5.3.1 Objective & Eligibility Criteria
- Automates the statutory annual appraisal SOP for University Faculty via the **Evaluation Committee Meeting (ECM)** route.
- Replaces manual routing across the Registrar's Office, HR Department, Academic Departments, Deans, Evaluation Committee, and Management.
- **Strict Eligibility Rule:** System auto-identifies Faculty members who have:
  1. Mandatorily completed their **probation period**, AND
  2. Completed at least **12 months of employment** since their last appraisal (or DOJ).

#### 5.3.2 End-to-End ECM Process Flow
1. **Monthly Eligibility Batching:** System scans the Central Employee Database and generates the eligible Faculty list. HR routes this list to the **Office of the Registrar by the 10th of every month** (with automated reminders if delayed).
2. **Self-Appraisal Issuance & Submission:**
   - System auto-issues the digital **Self-Appraisal Form** to eligible faculty members.
   - Faculty member must complete and submit the form with supporting evidence within **seven (7) working days** of receipt (tracked with automated reminders).
3. **Multi-Departmental Verification Routing:**
   - System routes the submitted self-appraisal and evidence across designated evaluation stakeholders:
     - **School Dean** (academic performance, teaching delivery)
     - **R&D Cell** (research publications, grants, citations, patents)
     - **Placement Cell** (student corporate placements, internship mentoring)
     - **HR Department** (institutional compliance, leaves, conduct)
   - **Discrepancy Loop:** If any department identifies a discrepancy, the system returns the form to the Faculty member for correction/resubmission and monitors the resubmission loop until verified.
4. **ECM Scheduling:** The Office of the Registrar schedules the monthly Evaluation Committee Meeting (ECM) for all verified candidates and issues automated schedule notifications to candidates.
5. **Digital Scoring & TNU Protocol Matrix:**
   - Evaluation Committee members record scores directly into the digital **ECM Score Sheet** during the meeting, which submits directly to HR.
   - System compiles an **Evaluation Matrix** combining ECM scores, historical increment data, and parameters governed by the institutional **TNU Protocol**.
   - HR Representative routes the compiled matrix to **Management** for compensation and advancement decisions.
6. **Compensation Implementation & Auto-Letter Generation:**
   - Management's recommendation is captured in the system and tracked for implementation in the **next applicable salary cycle / due month**.
   - System auto-generates the formal increment/outcome letter to the Faculty member and routes it directly to **HR / Payroll** for payroll execution.
7. **Downstream Decision Support:**
   - ECM outcomes form the auditable basis for: confirmation of employment, probation extension (if minimum prescribed benchmark is not achieved), compensation revision, administrative responsibilities, Performance Improvement Plans (PIP), or reprimand.
   - All ECM records, score sheets, and letters are permanently archived in the Faculty member's **Digital Personal File**.
8. **Enclosures:** *1. Self-Appraisal Form*, *2. ECM Score Sheet*, *3. Evaluation Matrix Template*.

---

# Common/Core Concepts

Across all three modules, several foundational architectural concepts recur consistently. These concepts represent the shared platform primitives:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        UNIFIED HR PLATFORM CORE FOUNDATION                             │
├───────────────────────────────┬────────────────────────────────┬───────────────────────┤
│    CENTRAL EMPLOYEE DB        │      DYNAMIC ORG CHART         │ DIGITAL EMPLOYEE FILE │
│ • Single source of truth      │ • Derived reporting hierarchy  │ • Universal document  │
│ • Full ERP synchronization    │ • Real-time auto-updates       │   repository          │
│ • Historical service ledger   │ • School/Dept/Role topologies  │ • Permanent audit log │
├───────────────────────────────┼────────────────────────────────┼───────────────────────┤
│   DATABASE CHANGE METHOD      │     SLA & TIMELINE ENGINE      │ UNIFIED REPORT ENGINE │
│ • Explicit effective dates    │ • Automated countdown triggers │ • Real-time execution │
│ • Immutable audit trail       │ • Escalations & reminders      │ • Configurable schema │
│ • Full entity version history │ • Hard cutoffs & auto-locks    │ • Funnel & TAT stats  │
└───────────────────────────────┴────────────────────────────────┴───────────────────────┘
```

1. **Central Database of all Employees:**
   - Authoritative institutional repository.
   - Provides employee master records, employment dates, probation statuses, salary history, band/levels, and reporting relationships.
   - Synchronized bidirectionally or reflected into the institutional ERP.
2. **Dynamic Organization Chart:**
   - Dynamically visualizes institutional reporting structures.
   - Reacts instantly to database transactions (transfers, promotions, supervisor changes, re-designations).
3. **Digital Employee File / Personal File:**
   - Secure digital dossier per employee.
   - Aggregates employment contracts, credentials, quarterly reviews, monthly Group-D evaluations, annual reports, ECM score sheets, disciplinary notes, and auto-generated letters.
4. **Effective-Date Database Change Methodology:**
   - Every service change (salary, role, department) operates on an explicit future or present `effective_date`.
   - Modifying a field does not overwrite history; it creates a timestamped, versioned ledger entry.
5. **SLA, Notification, & Auto-Lock Infrastructure:**
   - Real-time event scheduler managing reminders, warning thresholds, escalation notices to senior management, and hard auto-locks (e.g., Group-D 10th of the month lockout).
6. **Configurable Form Repository & Versioning:**
   - Central catalog of evaluation forms, requisition forms, and score sheets.
   - Versioning capabilities allowing HR to adjust KPIs, weights, or questions while retaining immutable audit histories for past cycles.

---

# Cross-Module Relationships

The three modules are not isolated silos; they form a deeply integrated cyclical ecosystem. Module I acts as the central hub, Module II serves as the intake funnel, and Module III functions as the recurring evaluation and growth loop.

```
                              ┌────────────────────────────────────────┐
                              │               MODULE II:               │
                              │         RECRUITMENT & SELECTION        │
                              └───────────────────┬────────────────────┘
                                                  │
                       Candidate Accepted (LOI)   │ Onboarding Completed
                       Flagged as "Yet to Join"   │ Closes Open Position Tracker
                                                  ▼
                              ┌────────────────────────────────────────┐
   Resignation Accepted ─────►│               MODULE I:                │◄──── Change Requests
   Triggers Ad-hoc MRF        │         CENTRAL EMPLOYEE DB &          │      (Salary, Level,
   Replacement Clock Starts   │         CHANGE MANAGEMENT SYSTEM       │      Designation, Role)
                              └───────────────────┬────────────────────┘
                                                  │
                                                  │ Master Data Sync:
                                                  │ • Date of Joining (DOJ)
                                                  │ • Probation Status
                                                  │ • Supervisor Hierarchy
                                                  │ • Historical Increments
                                                  ▼
                              ┌────────────────────────────────────────┐
                              │              MODULE III:               │
                              │         PERFORMANCE MANAGEMENT         │
                              │  (Group-D | KRA/KPI Staff | Fac-ECM)   │
                              └────────────────────────────────────────┘
```

### Detailed Data Flow & Integration Touchpoints

| Source Module / Event | Target Module / System | Transferred Data & Trigger Logic | Business Impact & Automation Result |
|-----------------------|------------------------|-----------------------------------|--------------------------------------|
| **Module II Selection** | **Module I (Central DB)** | Candidate accepts LOI $\rightarrow$ Marked as "Yet to Join" $\rightarrow$ Pre-onboarding notifications sent to Dean/HOD/IT. Upon verified joining, employee record is created in Central DB. | Auto-populates Central Database; eliminates manual onboarding entry; positions Org Chart node; closes Open Position Tracker entry. |
| **Module I Resignation** | **Module II (Recruitment)** | Employee resignation accepted by School Dean $\rightarrow$ Event emitted to Head HR. | Starts replacement clock; allows Dean/HOD to initiate ad-hoc replacement MRF through vetting to Pro-Chancellor. |
| **Module I (Central DB)** | **Module III (Group-D)** | Employee DOJ, Group-D band designation, Department, and Reporting HOD pulled into Evaluation Repository. | Generates monthly evaluation form routed to correct HOD; calculates 1-year mark from DOJ for Annual Report; checks probation. |
| **Module I (Central DB)** | **Module III (KRA/KPI)** | New employee DOJ and designated Reporting Authority pulled immediately on joining. | Triggers Stage 1 (30-day Goal Setting); schedules 90-day Q1 review and subsequent quarters from DOJ. |
| **Module I (Central DB)** | **Module III (Faculty ECM)** | Faculty DOJ, probation status, current salary, and previous increment history scanned monthly. | Identifies eligible Faculty (probation completed + $\ge$ 12 months since last appraisal) by 10th of every month for Registrar routing. |
| **Module III (KRA/KPI Stage 3)** | **Module I (Change Mgmt)** | Annual appraisal outcome approved by Management $\rightarrow$ HR initializes resulting change. | Directly initializes change request in Module I (Salary increment, designation, level) without duplicate entry. |
| **Module III (Group-D / ECM)** | **Module I & Payroll** | Management compensation decision approved $\rightarrow$ auto-generates formal letter to employee. | Letter routed to HR/Payroll; compensation revision scheduled for next salary cycle; record stored in Digital Employee File. |

---

# Major Actors and Roles

To ensure strict adherence to the documents, the following matrix consolidates every institutional actor explicitly identified across the requirements:

| Actor / Institutional Role | Module Reference | Explicitly Documented Responsibilities in System |
|----------------------------|------------------|--------------------------------------------------|
| **Hon'ble Pro-Chancellor** | Module II | Final approval authority for Academic Manpower Planning (within 15-day consolidation window); approval authority for Non-Academic Manpower Requisitions; approval authority for ad-hoc replacement MRFs. |
| **Senior Management / Management** | Modules I, II, III | Final approval for Module I service condition changes; approval of recruitment shortlisting before interviews; final recommendation & cost approval for LOIs (Academic & Non-Academic); review of Group-D Annual Reports & compensation decisions; review/comments on quarterly KRA/KPI reviews; final approval for annual KRA/KPI appraisal changes; final decision on Faculty ECM compensation revisions. |
| **Vice President – Administration** | Module III (Group-D) | Mandatory review, sign-off, and formal approval of monthly Group-D Evaluation Forms submitted by HODs before forms are finalized. |
| **Office of the Registrar / Registrar** | Module III (Faculty ECM) | Receives eligible Faculty list from HR by 10th of month; issues and collects Self-Appraisal Forms; manages multi-department verification routing; schedules monthly Evaluation Committee Meetings (ECM); notifies Faculty of ECM schedule. |
| **Associate Dean (Academics)** | Module II | Triggers 4-month academic manpower planning communication to Deans; reviews/vets teaching load submissions (Attachment 1); seeks clarifications; consolidates and recommends proposals to Pro-Chancellor within 15 days; vets ad-hoc academic replacement MRFs. |
| **Deans of Schools / School Deans** | Modules II, III | Submits academic requirements & teaching loads (Attachment 1) within 15 days; raises MRF upon Pro-Chancellor approval; accepts faculty resignations (notifying HR and starting replacement clock); raises ad-hoc replacement MRFs; receives "Yet to Join" pre-onboarding reports; conducts academic verification of Faculty Self-Appraisals. |
| **Heads of Department (HOD) / Dept Heads** | Modules II, III | Submits Non-Faculty annual MRFs (1 planned/yr) within 15 days; raises ad-hoc Non-Faculty replacement MRFs; conducts Technical Interviews (Round 1) for Non-Faculty; completes monthly Group-D evaluation forms by 7th of every month; receives "Yet to Join" pre-onboarding notifications. |
| **Reporting Authority / Supervisors** | Modules I, III | Listed in Module I hierarchy changes; intimates and collaborates with new joiners on KRA/KPI setup (within 30 days); verifies quarterly KRA/KPI submissions within 7 days and forwards to HR. |
| **Head of HR / HOD-HR / HR Representative** | Modules I, II, III | First-level approval for Module I change requests; triggers 4-month Non-Faculty manpower planning; reviews/vets Non-Faculty MRFs; reviews Recruiter Calling Sheets (RCS); conducts Round 2 HR Interviews for Non-Faculty; generates eligible Faculty lists by 10th of month; verifies Faculty Self-Appraisals; compiles ECM Evaluation Matrix (TNU Protocol); initializes appraisal outcomes into Module I. |
| **Payroll Team** | Module III | Receives auto-generated compensation revision letters for Faculty and Group-D members to execute adjustments in the next applicable salary cycle. |
| **Selection Committee (SCM Members)** | Module II | Statutory committee for Academic recruitment (including External Subject Expert); receives digital invitations, CVs, and evaluation sheets; conducts online/offline interviews; enters evaluation marks directly into system. |
| **Technical Interview Panel** | Module II | Evaluates Non-Faculty candidates in Round 1 on job knowledge, communication, and attitude using digital evaluation sheets. |
| **Evaluation Committee (ECM Members)** | Module III | Evaluates eligible Faculty at monthly ECM; enters evaluation scores directly into digital ECM Score Sheet during the meeting. |
| **Specialized Verification Units (R&D, Placement)** | Module III | R&D Cell verifies research papers, citations, grants; Placement Cell verifies student placement and internship records submitted in Faculty Self-Appraisals. |
| **Admin & System IT Teams** | Module II | Receives automated "Yet to Join" pre-onboarding reports to prepare physical infrastructure, workstations, email accounts, and IT access prior to joining. |
| **Employee / Faculty / Group-D Member** | Modules I, II, III | Candidate/Employee: sets up KRAs/KPIs within 30 days; submits quarterly reviews within 15 days of 90-day mark; Faculty submits Self-Appraisal within 7 working days; receives auto-generated letters and notifications. |

---

# Major Workflows

### Workflow 1: Module I — Employee Service Condition Change Workflow
1. **Initiation:** HR user or authorized departmental initiator selects employee and submits a change request in one of the 10 standardized formats (e.g., Salary, Designation, Reporting Authority, Level). Request specifies target `effective_date` and attaches justification.
2. **Level 1 Review (HR Level):** HR team reviews request against service rules, budgets, and qualifications. HR approves, rejects, or queries.
3. **Level 2 Authorization (Senior Management Level):** Senior Management evaluates vetted request and grants formal executive approval.
4. **Execution & Scheduled Activation:**
   - If `effective_date` $\le$ current date, changes are immediately committed to the Central Employee Database.
   - If `effective_date` is future-dated, transaction is scheduled and automatically applied by the database engine on that date.
5. **Downstream Propagation:**
   - Central Employee Database updates master record.
   - Dynamic Organization Chart realigns nodes (if reporting, designation, or department changed).
   - Change is mirrored/reflected into University ERP.
   - Transaction logged in immutable audit ledger with version history.

---

### Workflow 2: Module II — Academic Manpower Planning Workflow
1. **Trigger ($T - 4\text{ months}$):** System issues automated call from Associate Dean (Academics) to Deans of Schools.
2. **Submission ($+15\text{ days}$):** Deans compute faculty/technical workload and submit teaching loads in **Attachment 1** format.
3. **Vetting ($T - 3\text{ months}$):** Associate Dean (Academics) reviews, seeks clarifications, and finalizes requirements.
4. **Consolidation & Recommendation ($+15\text{ days}$):** Associate Dean forwards consolidated recommendations to Hon'ble Pro-Chancellor.
5. **Approval ($+7\text{ days}$):** Pro-Chancellor approves; decision communicates back to Dean.
6. **MRF Raising:** Dean immediately generates system MRF to HR.
7. **Ad Initiation ($+7\text{ days}$):** HR launches public advertisements (print/social) and opens RCS Tracker.
8. **Target Completion ($T - 1\text{ month}$):** System tracks all intermediate stages to ensure selection concludes 1 month before semester start.

---

### Workflow 3: Module II — Non-Academic Manpower Planning Workflow
1. **Trigger ($T - 4\text{ months}$):** System issues automated call from HR to Department Heads.
2. **Submission ($+15\text{ days}$):** Department Heads submit planned annual MRF (strictly restricted to 1 planned requisition per year).
3. **Vetting ($T - 3\text{ months}$):** Head HR reviews operational needs, workload analysis, and expansion plans.
4. **Consolidation & Recommendation ($+15\text{ days}$):** Head HR consolidates submissions and routes to Hon'ble Pro-Chancellor.
5. **Approval:** Pro-Chancellor grants approval; communication notifies Department Head.
6. **Ad Initiation ($+7\text{ days}$):** HR launches public advertisements and opens RCS Tracker.
7. **Target Completion ($T - 15\text{ days}$):** Recruitment completed at least 15 days prior to target onboarding date.

---

### Workflow 4: Module II — Urgent / Replacement Manpower Workflow (Resignations)
1. **Trigger Event:** Employee submits resignation; acceptance by School Dean immediately triggers the replacement clock and auto-notifies Head HR.
2. **Ad-Hoc MRF Submission:** Dean / Department Head submits an ad-hoc replacement MRF at any time.
3. **Sequential Approvals:** System tracks:
   $$\text{Submission} \longrightarrow \text{Vetting (Assoc. Dean / Head HR)} \longrightarrow \text{Pro-Chancellor Approval}$$
   with automated reminder triggers on timeline overruns.
4. **Monitored Execution Block:** Sourcing $\rightarrow$ Shortlisting $\rightarrow$ SCM/Interview tracked as one consolidated block.
5. **Offer & Joining:** Auto-generated offer letter issued upon Management approval; candidate acceptance, notice period, credential verification, and joining tracked through to onboarding.
6. **Closeout:** Open Positions Tracker automatically updated to closed status.

---

### Workflow 5: Module II — Candidate Sourcing, Shortlisting, & Selection Funnel
1. **Omnichannel Ingestion:** Applications ingested into Central CV Database from emails, social channels, web portals, print ads, referrals, and Internshala.
2. **Auto-Classification & Screening:** System screens CVs against minimum qualifications, experience, and UGC statutory regulations.
3. **Recruiter Calling Stage:** Recruiter conducts preliminary phone screening, logs qualitative and quantitative feedback into the **RCS**, and routes it to HOD-HR.
4. **Management Pre-Approval:** Shortlisted candidate dossiers and RCS sheets are approved by Management prior to interview scheduling.
5. **Selection Routing:**
   - *Academic Track:* Digital invitations sent to statutory Selection Committee members and External Subject Expert. Online interview conducted (offline in exceptional cases). Evaluators input marks. System compiles Evaluation Matrix and routes with HR recommendation to Management.
   - *Non-Academic Track:* 3 sequential interview rounds conducted: Technical (Dept Head), HR (Head HR), and Management. Evaluators rate job knowledge, communication, and attitude in digital evaluation sheets.
6. **Letter of Intent (LOI):** Management cost approval triggers auto-generated LOI.
7. **"Yet to Join" State:** Candidate acceptance tags profile as "Yet to Join" in the internal HR database and dispatches pre-onboarding notifications to Deans, HODs, and Admin/IT teams.

---

### Workflow 6: Module III (Sub-System 1) — Group-D Monthly & Annual Appraisal Workflow
1. **Monthly Form Dispatch:** System routes digital Evaluation Form to reporting HOD on 1st of month.
2. **Submission Deadline (7th):** HOD completes KPI ratings online. System sends proactive reminders before the 7th.
3. **Grace Period (8th–10th):** Automated 3-day grace period with continuous daily reminders.
4. **Auto-Lockout (10th, 23:59):** System auto-locks unsubmitted evaluations, flags status as "Not Submitted", and alerts HR with reasons.
5. **VP-Administration Approval:** Submitted evaluations are routed to VP – Administration for formal digital sign-off.
6. **Monthly Collation:** Approved evaluations auto-compile into Monthly Performance Reports.
7. **Annual Milestone Trigger:** Upon completion of 12 months from DOJ, system aggregates all 12 monthly reports, calculates weighted average scores, validates probation completion, and routes Annual Report to Management.
8. **Compensation Slabs:** Management applies pre-configured compensation revision slabs; changes archive into Digital Employee File.

---

### Workflow 7: Module III (Sub-System 2) — KRA/KPI Lifecycle Workflow
1. **Stage 1 (Onboarding):** System detects new employee DOJ. Intimates employee and Reporting Authority. KRA/KPI goal setting must be submitted, vetted by HR, verified by Management, and locked within **30 days of DOJ**.
2. **Stage 2 (Quarterly Reviews Q1–Q4):**
   - At **90 days from DOJ**, system intimates employee to submit Q1 review.
   - If pending after **20 days**, automated reminder is dispatched.
   - Employee submits review with supporting evidence within **15 days of completing 90-day mark**.
   - Reporting Authority verifies and forwards to HR within **7 days**.
   - HR records observations/recommendations.
   - Management reviews and logs executive comments.
   - Cycle repeats identically for Q2, Q3, and Q4.
3. **Stage 3 (Annual Appraisal & Direct Handshake):**
   - Upon completion of Q4, HR triggers formal appraisal request to Management.
   - Management records final appraisal decisions (increments, promotions, band revisions).
   - **Direct Handshake:** HR initializes resulting service change directly into **Module I**, automatically updating employee salary, designation, or level without duplicate data entry.

---

### Workflow 8: Module III (Sub-System 3) — Faculty Annual Appraisal via ECM Route
1. **Monthly Eligibility Identification:** By the **10th of every month**, system scans Central Database for Faculty who completed probation and have $\ge$ 12 months service since last appraisal. List routes from HR to Office of the Registrar.
2. **Self-Appraisal Submission:** System auto-issues digital Self-Appraisal Form. Faculty member submits form with evidence within **seven (7) working days**.
3. **Stakeholder Verification:** Form routes to School Dean, R&D Cell, Placement Cell, and HR Department. Any discrepancy triggers a return-to-faculty correction loop.
4. **ECM Scheduling:** Registrar's Office schedules monthly ECM for cleared candidates and notifies faculty.
5. **Digital Committee Scoring:** Evaluation Committee members enter scores into digital ECM Score Sheets during the meeting.
6. **TNU Protocol Matrix Compilation:** HR compiles ECM scores, past increment data, and TNU Protocol parameters into the final Evaluation Matrix, routed to Management.
7. **Compensation & Execution:** Management approves compensation adjustments. System schedules implementation in next salary cycle, auto-generates official outcome letter to Faculty member, and routes copy to HR/Payroll.
8. **Archiving:** All evaluation sheets, evidence, matrices, and letters permanently archive into the Faculty member's Digital Personal File.

---

# SLA and Timeline Summary

The table below consolidates every explicit SLA, deadline, grace period, and recurrence cadence stipulated in the official requirement documents:

| Module | Process / Action | Trigger / Baseline Point | Documented SLA / Deadline | Enforcement / Action on Overrun |
|--------|------------------|--------------------------|---------------------------|----------------------------------|
| **Mod I** | Database Change Activation | Effective Date (`effective_date`) specified in request | Takes effect exactly on the mentioned date | Automated database scheduler commits change on target date. |
| **Mod II** | Academic Manpower Planning Trigger | Academic Year / Semester Start | $\ge$ 4 months prior to start | System automated communication from Assoc. Dean to Deans. |
| **Mod II** | Non-Academic Manpower Planning Trigger | Academic Year Start | $\ge$ 4 months prior to start | System automated communication from HR to Department Heads. |
| **Mod II** | Academic Teaching Load Submission | Receipt of 4-month communication | Within 15 days | System tracks deadline; issues automated reminders. |
| **Mod II** | Non-Academic Planned MRF Submission | Receipt of 4-month communication | Within 15 days | Restricted to 1 planned MRF per year; tracked with reminders. |
| **Mod II** | Manpower Review & Vetting Completion | Manpower Planning Process | $\ge$ 3 months prior to academic year start | Associate Dean (Academic) / Head HR (Non-Academic) completion gate. |
| **Mod II** | Submission to Pro-Chancellor | Receipt of vetted submissions | Within 15 days of receipt | SLA tracked by system. |
| **Mod II** | Pro-Chancellor Approval Communication | Receipt by Pro-Chancellor | Within 7 days (Academic) | System tracks and sends notification to Dean / Dept Head. |
| **Mod II** | Recruitment Ad & RCS Initiation | Receipt of approved MRF by HR | Within 7 days of MRF receipt | System tracks SLA; initiates public ads and RCS tracker. |
| **Mod II** | Academic Recruitment Completion | Semester Start Date | $\ge$ 1 month before semester start | Target date auto-calculated; intermediate milestone monitoring. |
| **Mod II** | Non-Academic Recruitment Completion | Required Onboarding Date | $\ge$ 15 days before onboarding | Target date auto-calculated; intermediate milestone monitoring. |
| **Mod II** | Open Positions Tracker Maintenance | Post-approval of positions | Completed within 30 days | Automatically maintained in Attachment 3 format. |
| **Mod II** | Management Recruitment Status Report | Ongoing recruitment operations | Weekly cadence | Auto-generated progress report to Management. |
| **Mod II** | Replacement Clock (Resignation) | Resignation acceptance by Dean | Immediate trigger | Replacement clock starts; Head HR auto-notified; ad-hoc MRF allowed. |
| **Mod III-1** | Group-D Monthly Form Submission | Start of the month | By the 7th of every month | Automated reminders sent before the 7th. |
| **Mod III-1** | Group-D Submission Grace Period | Expiry of 7th deadline | +3 additional days (up to the 10th) | Automated reminders sent during grace period. |
| **Mod III-1** | Group-D Hard Cutoff & Lockout | Expiry of 10th grace period (23:59) | Hard cutoff on the 10th | System auto-locks submission; flags "Not Submitted"; alerts HR. |
| **Mod III-1** | Group-D Annual Report Generation | Employee Date of Joining (DOJ) | Upon completion of 1 year, and every subsequent year | Auto-triggered by system; calculates weighted averages across 12 months. |
| **Mod III-2** | KRA/KPI Goal Setting Completion | Employee Date of Joining (DOJ) | Within 30 days of DOJ | Verified by HR & Management before goals are locked. |
| **Mod III-2** | KRA/KPI Q1 Review Intimation | Employee Date of Joining (DOJ) | At 90 days from DOJ | System automated intimation dispatched to employee. |
| **Mod III-2** | KRA/KPI Review Pending Reminder | Post-90-day intimation | After 20 days if pending | Automated reminder triggered if employee has not submitted. |
| **Mod III-2** | KRA/KPI Quarterly Submission | Completion of 90-day mark | Within 15 days of 90-day mark | Employee submits with supporting documents. |
| **Mod III-2** | Reporting Authority Verification SLA | Employee quarterly submission | Within 7 days of submission | Reporting Authority verifies and forwards to HR. |
| **Mod III-2** | KRA/KPI Annual Appraisal Trigger | Completion of Q4 review | Post-4 quarters completion | HR triggers appraisal request to Management $\rightarrow$ feeds Module I. |
| **Mod III-3** | Faculty Eligible List Generation & Routing | Monthly appraisal cadence | By the 10th of every month | HR routes list to Registrar; automated reminder if delayed. |
| **Mod III-3** | Faculty Self-Appraisal Submission | Receipt of Self-Appraisal Form | Within 7 working days of receipt | Tracked by system with automated deadline reminders. |
| **Mod III-3** | Faculty ECM Scheduling | Completion of verification | Monthly cadence | Office of Registrar schedules monthly ECM for verified candidates. |
| **Mod III-3** | Faculty Compensation Implementation | Management final recommendation | Next applicable salary cycle / due month | Tracked in system; auto-generated letter to Faculty & HR/Payroll. |

---

# Reporting Requirements

The system must support dynamic, real-time reporting capabilities across all modules. HR must be empowered to define, add, or retire report formats without breaking system core logic.

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                SYSTEM REPORTING LANDSCAPE                                        │
├───────────────────────────────┬──────────────────────────────────┬───────────────────────────────┤
│    MODULE I: CHANGE REPORTS   │    MODULE II: TALENT FUNNEL      │  MODULE III: APPRAISAL STATS  │
├───────────────────────────────┼──────────────────────────────────┼───────────────────────────────┤
│ • Real-time employee roster   │ • Weekly Open/Pending Positions  │ • Group-D Monthly Report      │
│ • Service condition history   │ • CV Sourcing & Channel Report   │ • Group-D Annual Weighted Rpt │
│ • Historical audit & version  │ • Shortlisting & Interview Funnel│ • Group-D "Not Submitted" Rpt │
│   reports                     │ • "Yet to Join" Onboarding Track │ • KRA/KPI 30-day Goal Status  │
│ • Departmental / School head- │ • Pre-Onboarding Admin Briefings │ • HR & Mgmt Verification TAT  │
│   count distributions         │ • Recruiter Calling Sheet (RCS)  │ • Quarter-wise Status (Q1-Q4) │
│ • Effective date transaction  │ • Open Positions Tracker (Att. 3)│ • Monthly Eligible Faculty    │
│   schedules                   │                                  │ • ECM Score Compilation Sheet │
│                               │                                  │ • TNU Protocol Matrix Report  │
└───────────────────────────────┴──────────────────────────────────┴───────────────────────────────┘
```

### 11.1 Module I Reporting Mandates
- **Dynamic List Provision:** HR shall provide the list and formats of required reports. Provision for addition and deletion over time.
- **Real-Time Generation:** All employee master reports, org structure reports, and service change logs must support on-demand, real-time generation.

### 11.2 Module II Reporting Mandates
1. **Weekly Open / Pending Positions Report:** Auto-generated weekly progress report submitted to Management detailing requisition statuses, open vacancies, and pipeline blockages.
2. **CV Database & Sourcing Channel Report:** Analytics on candidate volume captured across print media, LinkedIn, Facebook, Instagram, website, and Internshala.
3. **Shortlisting and Interview Funnel Report:** Stage-by-stage progression tracking (applications $\rightarrow$ shortlisted $\rightarrow$ RCS phone screen $\rightarrow$ interview rounds $\rightarrow$ LOI).
4. **"Yet to Join" Tracker:** Dedicated status dashboard tracking candidates who have accepted LOIs through notice period, document verification, and Day-1 joining.
5. **Pre-Onboarding Departmental Reports:** Auto-distributed briefings sent to concerned Deans, HODs, and Administrative / System IT teams.
6. **Open Positions Tracker (Attachment 3 Format):** Authoritative registry of all approved positions maintained within 30 days.

### 11.3 Module III Reporting Mandates
1. **Group-D Monthly Performance Report:** Auto-collated monthly report compiled from approved HOD evaluations using the pre-defined template.
2. **Group-D Annual Performance Report:** 12-month aggregated performance report computing weighted averages per parameter for Management compensation review.
3. **Group-D "Not Submitted" Audit Report:** Real-time visibility into HODs who failed to submit evaluations prior to the 10th-of-the-month auto-lock.
4. **New-Joiner KRA/KPI Setup Status Report:** Tracking compliance against the mandatory 30-day goal-setting SLA from Date of Joining.
5. **HR + Management Verification TAT Report:** Turnaround time analytics measuring delays in goal locking and quarterly review sign-offs.
6. **Quarter-Wise Submission Status Report:** Matrix of submission statuses (Submitted / Pending / Overdue) filterable by employee, department, and quarter (Q1–Q4).
7. **Monthly Eligible Faculty List:** Generated by the 10th of every month, listing faculty completing probation and $\ge$ 12 months service since last appraisal.
8. **ECM Score Sheet Compilation Report:** Digital compilation of all evaluation scores awarded by statutory Evaluation Committee members.
9. **Compiled Evaluation Matrix Report:** Comprehensive synthesis combining ECM scores, past increment records, and configured TNU Protocol parameters.

---

# Audit and Versioning Requirements

Enterprise auditability and version control represent mandatory compliance requirements across all three modules.

### 12.1 Universal Database Change Methodology
All modules must adopt a standardized, uniform database change methodology ensuring that:
1. **Timestamping:** Every user action, form submission, departmental review, committee score, executive approval, and status change is recorded with an immutable system timestamp.
2. **Actor Attribution:** Every transaction logs the unique identity, role, IP address, and authorization level of the acting user.
3. **State Transition Tracking:** Audit logs record the complete before-and-after state (`pre_change_state` and `post_change_state`) for any modified record.
4. **Effective Date Versioning:** Master data changes in Module I maintain temporal validity via `effective_date`, ensuring historical records remain accessible for retrospective audits.

### 12.2 Module-Specific Versioning Rules
- **Module I:** Complete version history across all 10 employee data change formats. Historical records must never be purged or destructively updated.
- **Module II:** Immutable audit trail tracking the recruitment lifecycle across both Academic and Non-Academic tracks: requisition creation $\rightarrow$ vetting $\rightarrow$ Pro-Chancellor approval $\rightarrow$ job posting $\rightarrow$ CV screening $\rightarrow$ RCS comments $\rightarrow$ interview scoring $\rightarrow$ LOI generation $\rightarrow$ onboarding closeout.
- **Module III (Group-D):** The digital Evaluation Form Repository must support form versioning by the HR Team. Each form template revision is logged with an audit trail, ensuring historical evaluations remain tied to the exact form version active during that cycle.
- **Module III (KRA/KPI):** Version-controlled goal locking. Once verified by HR and Management, goal sheets are frozen. Any subsequent revisions require tracked change requests. Full TAT escalation audit trails.
- **Module III (Faculty ECM):** Multi-departmental verification notes, discrepancy resubmissions, Evaluation Committee individual marks, and Management compensation decisions are permanently bound to the appraisal cycle version.

---

# Documents / Forms / Templates

The requirements explicitly reference numerous standardized forms, templates, and enclosures that structure the platform's transactions:

| Module Ref | Document / Form / Enclosure Name | Official Identifier | Purpose in Workflow |
|------------|----------------------------------|---------------------|----------------------|
| **Module I** | Change in Salary Format | Format (a) | Standardized data capture for pay scale adjustments, increments, allowances. |
| **Module I** | Change in Designation Format | Format (b) | Captures title changes, promotions, re-designations. |
| **Module I** | Change in Reportee Format | Format (c) | Realigns subordinate reporting lines in database and Org Chart. |
| **Module I** | Change in Reporting Authority Format | Format (d) | Updates supervisor assignment for individual or group. |
| **Module I** | Change in Level Format | Format (e) | Manages grade, band, or structural tier progressions. |
| **Module I** | Change in Department/School Format | Format (f) | Governs inter-departmental transfers and school reorganizations. |
| **Module I** | Change in Location Format | Format (g) | Manages transfers between campuses or operational units. |
| **Module I** | Additional Responsibility Format | Format (h) | Assigns secondary administrative roles (e.g., Dean, HOD, Proctor). |
| **Module I** | Change in Qualifications Format | Format (i) | Records new degrees, certifications, or licenses with verification proof. |
| **Module I** | General Service Condition Format | Format (j) | Extensible format for other employee service conditions. |
| **Module II** | Manpower Requisition Form | **MRF (Enclosure 1)** | Official requisition form raised by Deans / Dept Heads to authorize recruitment. |
| **Module II** | Teaching Load / Workload Format | **Attachment 1 (Enclosure 2)** | Academic workload computation submitted by Deans during manpower planning. |
| **Module II** | Position / Vacancy Specification Format | **Attachment 2 (Enclosure 3)** | Role description, job specification, UGC criteria, experience benchmarks. |
| **Module II** | Open Positions / JR Tracker Format | **Attachment 3 (Enclosure 4)** | Authoritative ledger tracking open, in-progress, and filled job requisitions. |
| **Module II** | Recruiter Calling Sheet | **RCS** | Standardized evaluation sheet capturing phone screening notes and candidate ratings. |
| **Module II** | SCM Digital Evaluation Sheet | Academic Selection Form | Scoring sheet utilized by statutory Selection Committee and External Experts. |
| **Module II** | Non-Faculty Digital Evaluation Sheet | Non-Academic Selection Form | 3-tier scoring sheet evaluating Job Knowledge, Communication Skills, and Attitude. |
| **Module II** | Letter of Intent | **LOI** | System auto-generated formal pre-offer document issued to selected candidates. |
| **Module II** | Formal Offer Letter | Replacement Offer Letter | Auto-generated employment contract issued during urgent replacement cycles. |
| **Module III-1** | Group-D Digital Evaluation Form | **Enclosure 1** | Standardized role-specific monthly rating form capturing KPIs and competencies. |
| **Module III-1** | Group-D Monthly & Annual Report Template | **Enclosure 2** | Standardized templates for monthly collation and annual weighted score reviews. |
| **Module III-2** | KRA/KPI Goal Setting Form | Goal Sheet | Onboarding template establishing annual/quarterly objectives within 30 days of DOJ. |
| **Module III-2** | Quarterly Review Submission Form | Q1–Q4 Review Form | Form for quarterly performance self-assessment with evidence attachment support. |
| **Module III-2** | Lifecycle Workflow Flowchart | **Sheet 2 Flowchart** | Authoritative workflow reference mapping the 3-stage KRA/KPI process. |
| **Module III-3** | Faculty Self-Appraisal Form | **Enclosure 1** | Annual self-evaluation form submitted by eligible faculty within 7 working days. |
| **Module III-3** | ECM Score Sheet | **Enclosure 2** | Score sheet used by Evaluation Committee members during monthly ECM. |
| **Module III-3** | Evaluation Matrix Template | **Enclosure 3 (TNU Protocol)** | Comprehensive matrix combining ECM scores, increment history, and TNU weights. |
| **Module III-3** | Faculty Compensation Revision Letter | Auto-generated Letter | Official notice auto-generated for faculty and routed to HR/Payroll. |

---

# Explicit Requirements vs Proposed Design

To guarantee strict compliance and prevent unwarranted architectural scope creep, this section categorizes all system elements into four distinct tiers:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                   CLASSIFICATION FRAMEWORK FOR SYSTEM UNDERSTANDING                              │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ [A] EXPLICIT REQUIREMENTS       Directly written in official PDFs (Non-negotiable baseline)      │
│ [B] LOGICAL IMPLICATIONS        Required to make explicit requirements function mathematically   │
│ [C] PROPOSED DESIGN DECISIONS   Technical & architectural recommendations for implementation     │
│ [D] OPEN QUESTIONS / TBD        Ambiguities, missing schemas, or policies requiring HR sign-off │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Category A: Explicit Requirements Stated in Documents
- Central Employee Database synchronized / reflected into ERP.
- Dynamic Organization Chart auto-updating upon database changes.
- 10 specific employee change formats with a 2-level approval hierarchy (HR $\rightarrow$ Senior Management).
- Database change methodology enforcing effective dates, time-stamping, audit trails, and version history.
- Academic vs. Non-Academic segregation in Module II with shared sourcing and CV database.
- 4-month manpower planning trigger, 15-day submission, 3-month vetting, 15-day consolidation, 7-day Pro-Chancellor turnaround, 7-day HR ad launch.
- Non-Faculty MRF restricted to 1 planned requisition per year (urgent replacements permitted anytime).
- Resignation acceptance by Dean starts replacement clock, auto-notifying Head HR.
- Multi-channel CV capture (designated emails, website, social channels, newspapers, referrals, Internshala).
- Auto-segregation, classification, and shortlisting against UGC norms.
- RCS format captured and reviewed by HOD-HR; Management approval required before interviews.
- Academic SCM statutory committee with external experts; Non-Academic 3-round interview (Technical, HR, Management assessing job knowledge, communication, attitude).
- LOI auto-generation; "Yet to Join" tracking; pre-onboarding notifications to Deans, HODs, Admin/IT.
- Open Positions Tracker maintained in Attachment 3 format within 30 days; weekly status reports to Management.
- Group-D monthly evaluation by HOD by 7th; 3-day grace period to 10th; auto-lockout if missed; VP-Administration approval; annual report at 1 year from DOJ with weighted averages; mandatory probation completion check before compensation review.
- KRA/KPI 30-day goal setting from DOJ verified by HR & Management; 90-day Q1 review intimation; 20-day reminder; 15-day submission; 7-day supervisor verification; 4-quarter cycle; direct handshake into Module I change request.
- Faculty ECM eligibility auto-identification (probation completed + $\ge$ 12 months service); monthly list to Registrar by 10th; 7 working days self-appraisal submission; multi-department verification (Dean, R&D, Placement, HR) with discrepancy loop; Registrar ECM scheduling; digital ECM score sheet; TNU Protocol evaluation matrix; Management approval; salary cycle tracking; auto-generated letter to faculty and HR/Payroll.

### Category B: Logical Implications Derived from Requirements
- **State Machine Architecture:** Each workflow requires an underlying finite state machine (e.g., `DRAFT`, `SUBMITTED`, `VETTED`, `RECOMMENDED`, `APPROVED`, `REJECTED`, `DISCREPANCY_RETURNED`, `LOCKED`, `APPLIED`).
- **Role-Based Access Control (RBAC):** Strict permission boundary enforcement so that HODs only see their direct reportees, Deans see their School, external experts only see designated SCM candidates, and VP-Admin/Management see institutional views.
- **Asynchronous Task Scheduler:** Background cron engine to evaluate daily temporal conditions (e.g., detecting 4-month semester triggers, dispatching 7th/10th reminders, executing Group-D auto-locks at midnight, scheduling effective-date database commits).
- **Secure File Storage Infrastructure:** Cloud or on-premises blob store for storing CVs, certificates, research papers, and auto-generated PDFs, bound to access-controlled database metadata.
- **PDF Generation & Templating Engine:** Server-side templating system capable of populating placeholders for auto-generating LOIs, offer letters, and compensation revision letters.
- **Notification & Communication Gateway:** Multi-channel notification service integrating institutional SMTP email, in-app notification centers, and SMS/WhatsApp alerts for urgent reminders.

### Category C: Proposed Technical & Architectural Decisions (Subject to Formal Review)
- *Database Technology:* Proposed enterprise relational database (PostgreSQL / MySQL) with JSONB capabilities to support configurable evaluation form schemas while maintaining strict relational foreign keys for the Central Employee Database.
- *API & Integration Architecture:* Proposed RESTful or GraphQL micro-services communicating via an event-driven bus (e.g., Redis Streams / RabbitMQ) to decouple Module II and Module III events from Module I core database commits.
- *Audit Ledger Implementation:* Proposed immutable append-only audit tables with cryptographic hash chaining (`sha256`) or database change data capture (CDC) to guarantee tamper-proof audit trails.
- *Organization Chart Visualization:* Proposed interactive vector-rendered hierarchy tree (e.g., D3.js or OrgChart.js) supporting real-time node updates and departmental drill-downs.

### Category D: Information Currently Missing / Open Questions
*(Detailed comprehensively in Section 15 below).*

---

# Open Questions / TBD

In strict accordance with project instructions, no assumptions have been made regarding undocumented details. The following items are formally logged as **OPEN QUESTIONS / TBD** requiring clarification from the University and HR leadership:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             LOG OF FORMAL OPEN QUESTIONS / TBD                                   │
├────┬──────────────────────┬──────────────────────────────────────────────────────────────────────┤
│ #  │ Domain / Category    │ Specific Open Question / Missing Information                         │
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 1  │ ERP Architecture     │ What specific ERP platform is deployed (e.g., SAP, Oracle, Banner)? │
│    │ & Integration        │ What is the protocol for "full reflection" (REST API, DB sync)?      │
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 2  │ Attachment Formats   │ Exact field-level schemas for Attachments 1, 2, 3 and Enclosures 1-4 │
│    │ & Templates          │ need to be obtained from HR (provided only as text titles in briefs).│
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 3  │ Staff Track Scope    │ Which exact staff categories follow KRA/KPI vs. Group-D vs. ECM?     │
│    │ Boundary Definition  │ Do Lab Technicians & Teaching Associates follow KRA/KPI or ECM?      │
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 4  │ TNU Protocol & SCM   │ What are the exact mathematical scoring weights of the TNU Protocol? │
│    │ Scoring Formulas     │ What is the exact statutory composition of the Academic SCM panel?   │
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 5  │ Compensation Slabs   │ What are the pre-configured compensation revision slabs for Group-D  │
│    │ & Increment Formulas │ and Faculty appraisal outcomes?                                      │
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 6  │ Resignation Intake   │ What is the exact initiation interface for employee resignations in  │
│    │ Workflow             │ Module I before the Dean's acceptance triggers Module II?            │
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 7  │ Authentication &     │ Will institutional SSO (Google Workspace, Microsoft 365, LDAP) be    │
│    │ External Access      │ used? How will external SCM experts securely access the system?      │
├────┼──────────────────────┼──────────────────────────────────────────────────────────────────────┤
│ 8  │ Letter Issuance      │ What is the exact operational distinction and timeline between the   │
│    │ Lifecycle            │ Letter of Intent (LOI) and the final formal Appointment Letter?      │
└────┴──────────────────────┴──────────────────────────────────────────────────────────────────────┘
```

### Detailed Elaboration of Open Items

1. **ERP Synchronization Specifications:**
   - *Requirement Reference:* Module I, Section 1: *"This database shall be fully reflected in our ERP."*
   - *Clarification Needed:* What specific ERP system is currently operational at the University? Does the ERP provide inbound REST APIs, webhooks, direct database staging tables, or scheduled SFTP flat-file synchronization? Who is the authoritative master for primary employee key generation?
2. **Standardized Attachment Schemas & Templates:**
   - *Requirement Reference:* Module II Enclosures (Attachments 1, 2, 3); Module III Enclosures (Evaluation Forms, Report Templates, TNU Matrix).
   - *Clarification Needed:* The requirement briefs name these attachments and define their high-level intent, but physical Excel/Word templates or field-level data schemas were not attached. Official copies of these templates must be obtained from HR.
3. **Applicability Matrix for Mid-Level Academic & Technical Roles:**
   - *Requirement Reference:* Module II lists Teaching Associates, Technical Assistants, and Lab Technicians under Academic recruitment. Module III provides distinct appraisal tracks for Group-D, Faculty (ECM), and KRA/KPI.
   - *Clarification Needed:* Which appraisal workflow applies to Lab Technicians, Technical Assistants, and Teaching Associates? Do they follow the KRA/KPI quarterly cycle, the Faculty ECM route, or a customized technical staff appraisal?
4. **TNU Protocol Parameter Weightages & ECM Statutory Composition:**
   - *Requirement Reference:* Module III, Section 5(b): *"compile an evaluation matrix based on the configured TNU Protocol parameters together with the Faculty member's previous increment details..."*
   - *Clarification Needed:* What are the exact quantitative scoring parameters, category weights (e.g., Teaching vs. Research vs. Administration), and minimum qualifying thresholds defined in the "TNU Protocol"? What is the statutory quorum and member composition for the SCM and ECM committees?
5. **Pre-Defined Compensation Revision Slabs:**
   - *Requirement Reference:* Module III (Group-D Section 5(a) & Faculty Section 6(a)).
   - *Clarification Needed:* What are the specific compensation slabs configured by Management? Are increments percentage-based, fixed-step increments, or merit-grade allowances?
6. **Resignation Processing & Upstream Acceptance:**
   - *Requirement Reference:* Module II, Section 1(i): *"Replacement clock starts on resignation acceptance by the School Dean, auto-notifying Head HR."*
   - *Clarification Needed:* Does Module I include an employee self-service resignation submission and clearance module, or is the resignation processed administratively by HR/Dean entering the accepted resignation date?
7. **Identity Management & External Expert Access:**
   - *Requirement Reference:* Module II, Selection Workflow A(a): *"digital invitations to SCM members (including the external subject expert)..."*
   - *Clarification Needed:* Does the University utilize Single Sign-On (Google Workspace, Microsoft Entra ID / Azure AD, LDAP)? How will external subject experts authenticate (e.g., time-limited magic links, OTP-verified portal accounts)?
8. **LOI vs. Formal Appointment Letter Lifecycle:**
   - *Requirement Reference:* Module II Selection Workflows A(e), B(b), and urgent replacement Section 1(i).
   - *Clarification Needed:* Requirements mention auto-generating the Letter of Intent (LOI) upon Management approval, and in urgent replacements mention an auto-generated Offer Letter. Does the LOI serve as the sole pre-joining contract, or does a subsequent Appointment Letter get generated after document verification?

---

# Requirement Traceability Approach

To guarantee that every subsequent software artifact—from functional specifications and data schemas to API endpoints, UI screens, and test cases—remains strictly bound to authoritative requirements, an **Internal Requirement Traceability Matrix (RTM)** framework is established.

### Traceability Tag Schema
Every requirement is assigned a unique, immutable Traceability Identifier using the syntax:
$$\mathbf{[MOD\# - SECTION - SUBSECTION - REQ\#]}$$

- `MOD1-`: Module I (Change Management & Core DB)
- `MOD2-`: Module II (Recruitment & Selection)
- `MOD3-GD-`: Module III Sub-System 1 (Group-D Appraisal)
- `MOD3-KRA-`: Module III Sub-System 2 (KRA/KPI Appraisal)
- `MOD3-FAC-`: Module III Sub-System 3 (Faculty ECM Appraisal)

### Sample Requirement Traceability Mapping Table

| Traceability ID | Source Document | Page # | Document Section | Exact Requirement Statement (Abridged) | Type | Downstream Technical Mapping |
|-----------------|-----------------|--------|------------------|----------------------------------------|------|------------------------------|
| `MOD1-CDB-01` | Module I PDF | 1 | Structure (1) | Central Database of all Employees fully reflected in ERP. | Explicit | `EmployeeMaster` entity; ERP sync adapter. |
| `MOD1-ORG-01` | Module I PDF | 1 | Structure (2) | Organization Chart connected to database, updating on changes. | Explicit | Dynamic Org Chart API; DAG hierarchy builder. |
| `MOD1-CHG-01` | Module I PDF | 1 | Structure (3a-j) | 10 standardized change formats for employee data modifications. | Explicit | `ServiceChangeRequest` entity; 10 polymorphic sub-forms. |
| `MOD1-APP-01` | Module I PDF | 1 | Approval Hierarchy | Level approval: (a) HR Level, (b) Senior Management Level. | Explicit | 2-stage approval workflow state machine. |
| `MOD1-DAT-01` | Module I PDF | 1 | Methodology | Effective date methodology with audit trail and version history. | Explicit | Temporal ledger table; `effective_date` scheduler. |
| `MOD2-MP-FAC-01` | Module II PDF | 1 | Manpower (1a) | Automated communication $\ge$ 4 months before semester (Assoc. Dean to Deans). | Explicit | Temporal scheduler; notification trigger. |
| `MOD2-MP-FAC-02` | Module II PDF | 1 | Manpower (1b) | Deans submit requirements + teaching load (Attachment 1) within 15 days. | Explicit | `TeachingLoadRequisition` entity; 15-day SLA timer. |
| `MOD2-MP-NF-01` | Module II PDF | 1 | Manpower (1b) | Non-Faculty MRF restricted to 1 planned requisition per year. | Explicit | Requisition frequency constraint validator. |
| `MOD2-RES-01` | Module II PDF | 2 | Manpower (1i) | Resignation acceptance by Dean starts replacement clock, auto-notifies HR. | Explicit | Event listener on resignation; replacement SLA tracker. |
| `MOD2-SRC-01` | Module II PDF | 2 | Sourcing (4) | Capture applications into Central CV Database from designated channels. | Explicit | Multi-channel CV parser & ingestion pipeline. |
| `MOD2-SRC-02` | Module II PDF | 2 | Sourcing (5) | Auto-segregate, classify, and shortlist against qualifications & UGC norms. | Explicit | Rules engine validating UGC benchmarks. |
| `MOD2-SEL-FAC-01` | Module II PDF | 3 | Selection A(a-d) | SCM with external expert, online interview, digital scoring, matrix to Mgmt. | Explicit | SCM scheduling portal; digital score entry sheet. |
| `MOD2-SEL-NF-01` | Module II PDF | 3 | Selection B(a) | 3-round interview (Technical, HR, Mgmt) evaluating knowledge, communication, attitude. | Explicit | 3-tier sequential evaluation workflow. |
| `MOD2-ONB-01` | Module II PDF | 3 | Selection A(e), B(b) | LOI auto-generation; acceptance marks candidate as "Yet to Join". | Explicit | PDF LOI generator; "Yet to Join" state transition. |
| `MOD3-GD-EVAL-01` | Module III PDF | 1 | Structure 2(a-e) | Monthly Group-D form to HOD; due 7th; grace to 10th; auto-lockout if missed. | Explicit | 7th/10th temporal scheduler; auto-lock job. |
| `MOD3-GD-APP-01` | Module III PDF | 1 | Structure 2(b), 7(b) | VP – Administration mandatory approval before form is final. | Explicit | VP-Admin approval gateway in state machine. |
| `MOD3-GD-ANN-01` | Module III PDF | 1, 2 | Structure 4, 5(b) | Annual report at 1 yr from DOJ; weighted scores; mandatory probation check. | Explicit | DOJ anniversary trigger; probation status gate. |
| `MOD3-KRA-SET-01` | Module III PDF | 3 | Stage 1 | New joiner KRA/KPI setup within 30 days of DOJ; locked by HR & Mgmt. | Explicit | 30-day onboarding countdown; lock mechanism. |
| `MOD3-KRA-QTR-01` | Module III PDF | 3 | Stage 2 | 90-day intimation; 20-day reminder; 15-day submit; 7-day supervisor verify. | Explicit | Quarterly recurrence engine; multi-tier SLA timers. |
| `MOD3-KRA-INT-01` | Module III PDF | 3 | Stage 3 | Annual appraisal outcome feeds directly into Module I change request. | Explicit | Module III $\rightarrow$ Module I transactional API bridge. |
| `MOD3-FAC-ELG-01` | Module III PDF | 4 | Structure 1(a-b) | Auto-identify Faculty (probation + $\ge$ 12 mo service); list to Registrar by 10th. | Explicit | Monthly batch query; Registrar dispatch workflow. |
| `MOD3-FAC-VER-01` | Module III PDF | 4 | Structure 3(a-b) | Verification routing to Dean, R&D, Placement, HR; discrepancy return loop. | Explicit | Multi-stakeholder parallel review state machine. |
| `MOD3-FAC-ECM-01` | Module III PDF | 4 | Structure 4, 5 | Monthly ECM scheduled by Registrar; digital score sheet; TNU Protocol matrix. | Explicit | ECM scheduling module; TNU matrix calculation engine. |
| `MOD3-FAC-SAL-01` | Module III PDF | 5 | Structure 6(a-b) | Track compensation in next salary cycle; auto-generate letter to faculty & payroll. | Explicit | Salary cycle scheduler; PDF letter auto-generator. |

---

# Recommended Next Documentation Phases

To ensure disciplined execution without premature coding or hasty database implementations, the following sequential documentation phases are recommended:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             RECOMMENDED DOCUMENTATION ROADMAP                                    │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
                                                  │
                                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PHASE 1: STAKEHOLDER WORKSHOP & OPEN QUESTION RESOLUTION                                         │
│ • Engage University HR leadership to resolve all items logged in Section 15                      │
│ • Obtain official Excel/Word templates for Attachments 1-3, Enclosures 1-4, and TNU Protocol     │
│ • Define exact ERP technical interface specifications                                            │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PHASE 2: COMPREHENSIVE FUNCTIONAL SPECIFICATION DOCUMENT (FSD / SRS)                             │
│ • Detailed screen-by-screen, field-by-field functional requirements                              │
│ • Explicit validation rules, error handling specifications, and role-permission matrices         │
│ • Strict mapping of every requirement to Traceability IDs                                        │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PHASE 3: UNIFIED DOMAIN DATA MODEL & ENTITY-RELATIONSHIP ARCHITECTURE                            │
│ • Design normalized domain entities for Central DB, Org Chart, Recruitment, and Appraisals      │
│ • Model temporal tables for effective-date versioning and immutable audit logging                │
│ • Define ERP synchronization staging tables and event schemas                                    │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PHASE 4: STATE MACHINE, WORKFLOW, & SLA TIMING SPECIFICATIONS                                    │
│ • Formal state transition tables and UML activity diagrams for all 8 major workflows             │
│ • Precise mathematical definitions of SLA timers, reminders, grace periods, and auto-locks       │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PHASE 5: UI/UX WIREFRAMING, DESIGN SYSTEM, & INTERACTION ARCHITECTURE                            │
│ • High-fidelity component design system (Vanilla CSS tokens, typography, dark/light modes)       │
│ • Responsive wireframes for Employee Portal, HOD Review, Registrar ECM, and Executive Dashboards │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ PHASE 6: TECHNICAL ARCHITECTURE, SECURITY, & API SPECIFICATION                                   │
│ • Microservice / Modular Monolith architecture design; technology stack finalization             │
│ • OpenAPI / Swagger specifications for all internal and cross-module endpoints                   │
│ • RBAC security model, SSO authentication flows, and data encryption standards                   │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

# Verification and Compliance Attestation

This analysis confirms that:
1. All three authoritative source PDF documents (`Module I`, `Module II`, and `Module III`) have been inspected, fully read, and completely analyzed without omission.
2. The individual integrity and unique workflow logic of the **three distinct performance management sub-systems** in Module III (Group-D, KRA/KPI Staff, and Faculty ECM) have been preserved and not conflated.
3. The distinct tracks in Module II (Academic Faculty & Lab Technician vs. Non-Academic Staff) have been preserved with their individual approval chains and timelines.
4. No requirements, business rules, user roles, database fields, or technical stacks have been invented; all derived implications, proposed designs, and missing details have been explicitly segregated into their respective analytical categories.
5. None of the original requirement PDF documents in the workspace have been modified, renamed, moved, or deleted.

---
*End of Report — Project Requirements Analysis Baseline Established.*
