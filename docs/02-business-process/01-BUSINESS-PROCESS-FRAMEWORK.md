# Business Process Framework & Operational Model
## University HR Change Management & Automation System

**Document Identifier:** `DOC-02-BPF-01`  
**Phase:** Phase 2 — Business Process Documentation (Documentation-Only)  
**Location:** `docs/02-business-process/01-BUSINESS-PROCESS-FRAMEWORK.md`  
**Status:** Approved Framework Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Framework Purpose & Architectural Principles

The **Business Process Framework** establishes the standardized conceptual architecture, governance rules, lifecycle conventions, and actor taxonomy used across all business process definitions within the University HR Change Management & Automation System.

### 1.1 Core Principles

1. **Institutional Business Fidelity:**  
   Processes reflect the actual operating realities, governance hierarchies, statutory academic standards (e.g., UGC norms), and executive oversight structures of the University as established in the authoritative source requirement briefs.
2. **Technology Independence:**  
   Processes describe *what* institutional activities occur, *who* is responsible, *what* rules govern decisions, and *when* actions must be completed. They do not reference software-level mechanics (such as REST API routes, Socket.IO channels, SQL table mutations, or queue worker configurations).
3. **Strict Separation of Operational Tracks:**  
   Distinct administrative tracks established by university policy (notably Academic vs. Non-Academic recruitment and the three distinct performance evaluation tracks) must never be merged into artificial, generic workflows.
4. **The Anti-Invention Mandate:**  
   No operational rules, committee quorums, quantitative scoring formulas, monetary compensation brackets, or authorization tiers may be invented. Where institutional requirements are silent, items are explicitly designated as **`[E] TBD / Open Decision`** cross-referenced to the project's master TBD log ([`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md)).

---

## 2. Process Building Blocks

Every business process documented within this system is composed of fourteen (14) standardized architectural building blocks:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             STANDARDIZED BUSINESS PROCESS ANATOMY                                │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   [ 1. TRIGGER ] ──────► [ 2. PRECONDITIONS & INPUTS ] ──────► [ 3. BUSINESS ACTIVITIES ]        │
│   (Temporal/Event/Admin)  (Master Records, Dossiers, Forms)    (Evaluations, Vetting, Reviews)   │
│                                                                              │                   │
│                                                                              ▼                   │
│   [ 6. OUTPUTS & AUDIT ] ◄── [ 5. APPROVAL GATES ] ◄────────── [ 4. DECISION POINTS ]            │
│   (Letters, Records, Log)    (HR, Mgmt, VP, Dean, SCM)          (Compliance, Thresholds, Slabs)  │
│             │                                                                                    │
│             ├──────────────────────────────┬─────────────────────────────┐                       │
│             ▼                              ▼                             ▼                       │
│   [ 7. SLA & DEADLINES ]        [ 8. ESCALATIONS ]            [ 9. CROSS-MODULE HANDOFFS ]       │
│   (Business Cutoffs, Grace)     (Reminders, Lockouts, Alerts) (Core DB, Requisitions, Handshakes)│
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 2.1 Process Trigger
The operational event that initiates the business process:
- **Temporal Triggers:** Calendar-based milestones (e.g., semester planning 4 months prior, 1st of month form dispatch, 7th of month deadline, 10th-of-month eligibility scans, 1-year DOJ anniversaries).
- **Event-Driven Triggers:** State changes resulting from prior workflows (e.g., Dean accepting a resignation, candidate accepting an LOI, employee completing onboarding).
- **Administrative Triggers:** Manual initiation by authorized personnel (e.g., HR officer initiating a service change request).

### 2.2 Process Actors
Institutional individuals, committees, or organizational units that participate in the process. Actors are strictly limited to those explicitly established in the source requirement briefs (see Section 3).

### 2.3 Process Inputs & Preconditions
The tangible business data, physical documents, digital files, and prerequisite operational states required before the process can execute (e.g., active employee record, verified teaching load calculation, approved MRF).

### 2.4 Business Activities
The discrete operational tasks, evaluations, reviews, data verifications, or committee proceedings executed by participants during the workflow.

### 2.5 Decision Points
Operational evaluation gates where the flow of work branches based on verified criteria (e.g., UGC compliance check, probation completion status, discrepancy identified during dossier review).

### 2.6 Approval Points & Hierarchies
Mandatory governance sign-offs executed by designated authorities:
- **Sequential Two-Level Approval:** HR Review followed strictly by Senior Management Approval (Module I).
- **Executive Sign-Off:** Vice President – Administration approval for Group-D evaluations (Module III).
- **Statutory Committee Sign-Off:** Selection Committee Meeting (SCM) approval for faculty appointments (Module II).
- **Institutional Governance Sign-Off:** Pro-Chancellor approval for manpower requisitions (Module II).

### 2.7 Process Outputs & Deliverables
The tangible institutional deliverables produced upon workflow completion (e.g., updated Central Database record, signed Letter of Intent, compiled Evaluation Matrix, formal compensation revision letter, dynamic Org Chart realignment).

### 2.8 SLA & Business Deadlines
Institutional turnaround commitments, submission windows, and statutory cutoffs.  
*Governance Rule:* Business deadlines (e.g., 7th of the month, 10th-of-month grace cutoff, 15 days for Dean submission) represent institutional policy rules and are strictly distinguished from technical execution timings (e.g., automated midnight cron jobs or queue dispatch schedules).

### 2.9 Reminders & Escalations
Structured communication protocols triggered when approaching or breaching SLA deadlines (e.g., daily reminder notices on the 8th, 9th, and 10th of the month for delinquent Group-D evaluations, automated escalation to the Office of the Registrar).

### 2.10 Exceptions & Alternate Paths
Documented deviations from standard operating procedure (e.g., urgent replacement hiring bypassing annual manpower quotas, discrepancy return loops during faculty appraisal verification). Unspecified exception paths are classified as `[E] TBD`.

### 2.11 Cross-Module Handoffs
Formal operational interfaces where data or responsibility transitions to another module (e.g., Module II LOI acceptance instantiating a Module I employee record, Module III annual appraisal results initializing a Module I change request).

### 2.12 Completion Criteria
The unambiguous institutional conditions that signify full legal and operational conclusion of the process.

### 2.13 Audit & Institutional Records
The non-destructive historical evidence, before/after snapshots, approval timestamps, and signatory attributions that must be preserved for compliance and governance.

---

## 3. Authoritative Actor Taxonomy & Governance Roles

In strict adherence to the Anti-Invention Mandate, actors participating in business processes are derived strictly from the official source requirement briefs:

| Actor / Authority Name | Official Source Origin | Institutional Governance Role & Scope of Authority |
|---|---|---|
| **Employee** | All Modules | Any active, confirmed, or probationary staff member or faculty member of the University. Submits self-appraisals and reviews personal dossiers. |
| **HR / HR Department / Head HR** | All Modules | Institutional human resources department. Conducts initial compliance vetting, consolidates manpower plans, administers evaluation forms, and executes Level-1 approvals. |
| **HOD (Head of Department)** | Modules I, II, III | Academic or non-academic department head. Submits annual non-academic MRFs, evaluates Group-D staff monthly, conducts initial candidate screening. |
| **Dean (School Dean)** | Modules I, II, III | Executive academic head of a university School. Submits academic manpower requirements and teaching loads, verifies faculty self-appraisals, accepts faculty resignations. |
| **Associate Dean** | Module II | Academic administrative officer who initiates the advance semester manpower planning call to School Deans 4 months prior to semester start. |
| **Registrar / Office of the Registrar** | Module III | Chief administrative officer of the University. Receives monthly eligible faculty appraisal lists, confirms eligibility, and schedules monthly Evaluation Committee Meetings (ECM). |
| **Vice President – Administration** | Module III | Senior executive authority holding mandatory digital sign-off and approval power over monthly Group-D staff performance evaluations. |
| **Senior Management / Management** | All Modules | Executive leadership of the University (Pro-Chancellor, Vice Chancellor, Governing Body). Exercises final approval over service changes, recruitment, and compensation revisions. |
| **Pro-Chancellor** | Module II | Apex university authority holding mandatory approval power over consolidated Academic and Non-Academic Manpower Requisition Forms (MRFs). |
| **Vice Chancellor** | Module II | Apex academic officer of the University who chairs the statutory Selection Committee Meeting (SCM) for academic appointments. |
| **Statutory Selection Committee (SCM)**| Module II | Statutory committee comprising Vice Chancellor, School Dean, HOD, and External Subject Expert responsible for evaluating faculty candidates. |
| **External Subject Expert** | Module II | Independent academic specialist from an external institution invited to evaluate faculty candidates during statutory SCM proceedings. |
| **Recruiter / Recruitment Function** | Module II | Operational HR personnel responsible for multi-channel candidate sourcing, initial phone screening, Recruiter Calling Sheet (RCS) maintenance, and logistics. |
| **Director, R&D Cell** | Module III | University research authority who conducts parallel verification of faculty research publications, sponsored grants, and patents during the ECM appraisal route. |
| **Head, Placement Cell** | Module III | University placement officer who conducts parallel verification of faculty student placement records, internships, and corporate linkages during the ECM route. |
| **Reporting Authority / Supervisor** | Modules I, III | Direct administrative or academic manager assigned to an employee. Participates in KRA/KPI goal setting, quarterly review verifications, and operational workflows. |

---

## 4. Actor Responsibility Matrix Across Functional Domains

| Actor | Module I (Change Mgmt) | Module II (Recruitment) | Module III (Performance) | Cross-Module Handoffs |
|---|:---:|:---:|:---:|:---:|
| **Employee** | Target of service change | Candidate applicant | Submits self-reviews (KRA, ECM)| Receives promotion/salary change |
| **HR Department** | Level-1 Reviewer & Verifier | Vetting, Sourcing, RCS, Ads | Form collation, eligibility scan | Ingests new joiners, applies changes |
| **HOD** | Submits department changes | Submits annual non-acad MRF | Monthly Group-D evaluator | Reports staff turnover |
| **School Dean** | Verifies school transfers | Submits teaching loads & MRFs | Verifies faculty self-appraisal | Resignation acceptance starts clock |
| **Associate Dean** | Consulted on academic moves | Initiates 4-mo manpower call | N/A | Coordinates faculty requirements |
| **Registrar** | Master record coordination | Statutory documentation | Receives eligibility list, runs ECM| Communicates statutory changes |
| **VP – Administration** | N/A | Consulted on admin staffing | Mandatory Group-D sign-off gate | Approves support staff revisions |
| **Senior Management** | Level-2 Final Approval Gate | Pre-approves RCS, Final hires | Approves annual increments & slabs | Final compensation authorization |
| **Pro-Chancellor** | Executive governance | Final approval for all MRFs | Executive governance | Authorizes institutional hiring |
| **Selection Committee (SCM)**| N/A | Statutory faculty evaluation | N/A | Recommends selected faculty |
| **External Expert** | N/A | Independent marks scoring | N/A | Ensures statutory academic rigor |
| **R&D Cell** | N/A | N/A | Verifies faculty publications | Validates research credentials |
| **Placement Cell** | N/A | N/A | Verifies student placement data | Validates placement performance |
| **Reporting Authority** | Initiates subordinate changes| Evaluates non-acad rounds | Sets & verifies quarterly KRAs | Notified of team service changes |

---

## 5. Standard Business Process Documentation Template

All business processes across Documents 02, 03, 04, and 05 adhere strictly to the following 20-point architectural specification template:

```markdown
### Process Identifier: BP-[MODULE]-[TRACK]-[NUMBER]
**Process Name:** [Formal Descriptive Title]

1. **Module / Operational Track:** [Module I, Module II (Academic/Non-Academic/Urgent), Module III (Subsystem 1/2/3), or Cross-Module]
2. **Business Purpose:** [Why the process exists and what institutional value it delivers]
3. **Operational Trigger:** [Exact event, calendar date, or administrative action that initiates the workflow]
4. **Prerequisites & Entry Conditions:** [Prerequisite states, approved records, or verified milestones required]
5. **Primary Actors:** [Lead institutional participants directly responsible for executing activities]
6. **Supporting Actors:** [Secondary participants, reviewers, verifiers, or observers]
7. **Business Inputs & Documentation:** [Forms, enclosures, dossiers, and data structures entering the process]
8. **Sequential Business Activities:**
   - Step 1: [Operational action]
   - Step 2: [Operational action]
   - Step 3: [Operational action]
9. **Decision Points & Evaluation Rules:** [Criteria-based branching gates, statutory checks, and thresholds]
10. **Approval Points & Governance Gates:** [Mandatory sign-offs, role authorities, and sequential hierarchies]
11. **Institutional Outputs & Deliverables:** [Updated master records, signed letters, compiled matrices, reports]
12. **Operational SLA & Business Deadlines:** [Explicit turnaround commitments, calendar cutoffs, and submission windows]
13. **Reminders, Escalations & Lockouts:** [Automated notification cadences, escalation paths, and hard lockouts]
14. **Exception Handling & Alternate Paths:** [Documented operational exceptions and dispute resolution procedures]
15. **Cross-Module Interactions & Handoffs:** [Downstream data transfers and lifecycle handshakes to other modules]
16. **Process Completion Criteria:** [Unambiguous institutional conditions signifying full conclusion]
17. **Audit & Compliance Requirements:** [Immutable logging, versioning, and before/after snapshot requirements]
18. **Authoritative Source References:** [Direct citations to requirement briefs and sections]
19. **Classification:** [`[A] Explicit`, `[B] Logical Implication`, `[C] Approved Technical Decision`]
20. **Controlled Open Decisions (TBD):** [Unresolved policy, schema, or formula items mapped to the TBD register]
```

---

## 6. Business Deadline vs. Technical Scheduling Distinction

To eliminate architectural ambiguity and prevent technical implementation details from distorting business rules, this framework establishes a strict conceptual boundary between **Business Deadlines** and **Technical Schedulers**:

| Dimension | Institutional Business Rule | Technical Architecture Execution |
|---|---|---|
| **Definition** | An institutional policy deadline, regulatory cutoff, or governance SLA governing human action. | The automated software mechanism, cron job, or worker executing system tasks at specific system times. |
| **Ownership** | Academic Council, University Policy, HR Governance, Statutory UGC Regulations. | System Architect, Software Engineering Team, Technical Baseline. |
| **Example 1: Group-D Cutoff** | **Business Deadline:** Group-D evaluations are due by the 7th of the month, with an automated grace period extending through the 10th. Unsubmitted forms are locked. | **Technical Scheduler:** A background worker executes an auto-lock update at 23:59 on the 10th of the month ([`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)). |
| **Example 2: Effective Date** | **Business Deadline:** Approved employee service changes take legal and operational effect on their specified `effective_date`. | **Technical Scheduler:** A scheduled background job commits future-dated changes to active master tables at 00:00 midnight of the effective date. |
| **Example 3: Faculty Eligibility** | **Business Deadline:** Faculty appraisal eligibility is evaluated on the 10th of every month. | **Technical Scheduler:** A batch query worker runs monthly to evaluate eligibility criteria against PostgreSQL master tables. |

---
*End of Document — Business Process Framework & Operational Model.*
