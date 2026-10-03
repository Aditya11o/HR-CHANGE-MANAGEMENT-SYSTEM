# Business Process Specification
## University HR Change Management & Automation System

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-02-BPS-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **System Phase** | Phase 2 — Consolidated Business Process & Workflow Specification |
| **Document Status** | Approved Canonical Business Process Baseline |
| **Date** | October 2026 |
| **Coverage** | 59 End-to-End Processes across Module I, II, III & Cross-Module, RACI Matrix, SLA Framework |
| **Authoritative Sources** | `source-requirements/` (Module I, II, III Briefs & Visual Workflows) |

---

## 1. Executive Framework & Actor Taxonomy

### 1.1 Purpose
This specification documents the complete, end-to-end operational workflows and business process lifecycles across the University HR Change Management & Automation System. It defines the sequence of operational steps, actor interactions, decision gateways, timing SLAs, exception loops, and cross-module handshakes.

### 1.2 Institutional Actor Taxonomy
The system governs interactions among 16 primary institutional actors:

| Actor Code | Role Title | Institutional Scope & Governance Function |
|---|---|---|
| `ACT-PRO` | Pro-Chancellor / Management | Apex executive authority; final sanction for academic manpower and high-impact appointments. |
| `ACT-VC` | Vice-Chancellor | Statutory head; chairs academic Selection Committee Meetings (SCM) and ECMs. |
| `ACT-REG` | Registrar | Statutory university administrator; oversees institutional notices, ECM dockets, and official orders. |
| `ACT-VPA` | Vice President – Administration | Exclusive approval authority for Group-D / Band-I monthly performance reviews. |
| `ACT-HHR` | Head – Human Resources | Oversees HR operations, manpower planning consolidation, interview approvals, and change vetting. |
| `ACT-HRO` | HR Operations Officer | Executes day-to-day data entry, service change initiation, recruiter calling sheets, and dossier management. |
| `ACT-ADE` | Associate Dean (Academics) | Academic coordinator; initiates manpower planning with School Deans and vets teaching load models. |
| `ACT-DEA` | School Dean | Academic executive head; calculates faculty requirements (Attachment 1) and accepts resignations. |
| `ACT-HOD` | Head of Department | Departmental administrator; conducts Group-D reviews, submits non-academic MRFs, and supervises staff. |
| `ACT-EXP` | External Subject Expert | Independent domain specialist participating in statutory academic Selection Committees (SCM). |
| `ACT-SCM` | Selection Committee Member | Statutory committee member participating in faculty interview panels and digital scoring. |
| `ACT-ECM` | Evaluation Committee Member | Statutory evaluation committee member assessing faculty annual appraisal dossiers. |
| `ACT-FAC` | Academic Faculty Member | Teaching and research staff submitting annual self-appraisals and qualification update requests. |
| `ACT-STF` | General Administrative Staff | Operational and technical staff setting KRA/KPI goals and submitting quarterly self-reviews. |
| `ACT-GPD` | Group-D / Band-I Staff | Maintenance, security, and facility staff evaluated on a monthly cadence by departmental supervisors. |
| `ACT-SYS` | Automated System Engine | Automated background worker managing SLA countdowns, grace periods, auto-locks, and sync outboxes. |

### 1.3 RACI Responsibility Matrix
- **R (Responsible):** The role that executes the task.
- **A (Accountable):** The sole decision-maker with final sign-off authority.
- **C (Consulted):** Domain experts or advisors providing inputs.
- **I (Informed):** Roles notified upon state transitions or milestone completions.

---

## 2. Module I — HR Change Management Processes (`BP-M1-001` to `BP-M1-011`)

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                MODULE I: CHANGE WORKFLOW LIFECYCLE                               │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
  [HR Operations / Initiator]
          │ 1. Initiate Change Request (Formats a-j) + Attach Proof
          ▼
  [Level-1: HR Operations Review]
          │ 2. Vets Policy Compliance, Comp Band, Hierarchy Realignment
          ├─────────────────────────┐
      [Rejected]                [Approved]
          ▼                         ▼
  [Return to Initiator]    [Level-2: Senior Management Approval]
                                    │ 3. Final Executive Sanction
                                    ├─────────────────────────┐
                                [Rejected]                [Approved]
                                    ▼                         ▼
                            [Return to HR]         [Scheduled State (effective_date)]
                                                              │ 4. Background Processor
                                                              ▼
                                                   [Active Master Update]
                                                   • Central DB Committed
                                                   • Org Chart Realigned
                                                   • Dossier Archived
                                                   • ERP Outbox Event Emitted
```

### `BP-M1-001`: Employee Profile Creation & Onboarding Intake
- **Trigger:** Selected candidate completes Day-1 joining verification in Module II (`BP-XMOD-001`).
- **Actors:** HR Operations (`ACT-HRO` - R), Head HR (`ACT-HHR` - A), System (`ACT-SYS` - R).
- **Process Steps:**
  1. System receives validated onboarding payload from Module II containing candidate personal, educational, and compensation records.
  2. System mints a globally unique Employee Code and provisions the initial Central Database record (`ENT-MOD1-01`).
  3. System anchors the employee node to their designated department, designation, and reporting supervisor.
  4. System initializes the immutable Digital Personal Dossier (`ENT-MOD1-03`) and archives uploaded onboarding documents.
  5. System enqueues an ERP Master Employee Synchronization event in the transactional outbox (`ENT-SHR-08`).

### `BP-M1-002`: Dynamic Organization Hierarchy Maintenance & Rendering
- **Trigger:** Effective-date activation of any change in designation, reporting authority, reportee, or department.
- **Actors:** System (`ACT-SYS` - R), Head HR (`ACT-HHR` - I).
- **Process Steps:**
  1. Background worker triggers organizational realignment upon change request activation.
  2. Hierarchy tree traverser recalculates parent-child edges and subtree depths.
  3. Tree cache is invalidated and rebuilt in Redis with sub-second response times (`REQ-MOD1-04`).
  4. Real-time WebSocket event (`org-tree:updated`) is broadcast to connected clients to refresh visual canvas.

### `BP-M1-003`: Digital Personal Dossier Maintenance & File Aggregation
- **Trigger:** Employee profile update, service change approval, or annual appraisal completion.
- **Actors:** HR Operations (`ACT-HRO` - R), System (`ACT-SYS` - R).
- **Process Steps:**
  1. Event listener captures completed lifecycle event (LOI, increment letter, evaluation scorecard, degree certificate).
  2. System writes document metadata, SHA-256 hash, and object storage URL to `ENT-MOD1-03`.
  3. Longitudinal timeline view is updated, preserving non-destructive historical inspection.

### `BP-M1-004`: Service Condition Change Request Initiation
- **Trigger:** Requirement to alter employee service terms under Formats (a) through (j).
- **Actors:** HR Operations (`ACT-HRO` - R), Initiator (`ACT-HRO` / `ACT-HOD` - R).
- **Process Steps:**
  1. Initiator selects target employee and specifies one of the 10 approved change formats:
     - *(a) Salary*, *(b) Designation*, *(c) Reportee*, *(d) Reporting Authority*, *(e) Level*, *(f) Department*, *(g) Location*, *(h) Additional Responsibility*, *(i) Qualifications*, *(j) Other Service Condition*.
  2. Form captures current values, proposed values, mandatory `effective_date`, business rationale, and evidentiary attachments.
  3. System validates input constraints, prevents overlapping in-flight changes, and transitions status to `PENDING_HR_REVIEW`.

### `BP-M1-005`: Two-Level Sequential Approval Workflow
- **Trigger:** Submission of change request in `BP-M1-004`.
- **Actors:** HR Reviewer (`ACT-HHR` - R), Senior Management (`ACT-PRO` - A).
- **Process Steps:**
  1. *Level-1 (HR Operations Review):* HR verifies policy compliance, compensation bands, and qualification validity.
     - If rejected: Returned to initiator with comments.
     - If approved: Endorsed and escalated to Level-2.
  2. *Level-2 (Senior Management Approval):* Management reviews business justification and institutional impact.
     - If rejected: Returned to HR with remarks.
     - If approved: Request transitions to `APPROVED_SCHEDULED`.

### `BP-M1-006`: Effective-Date Scheduling & Activation Engine
- **Trigger:** Scheduled date arrives for an `APPROVED_SCHEDULED` change request.
- **Actors:** Automated System Engine (`ACT-SYS` - R).
- **Process Steps:**
  1. Daily midnight batch scheduler identifies requests where `effective_date <= CURRENT_DATE`.
  2. System commits updates to active employee master record in an atomic database transaction.
  3. Dynamic Org Chart is updated, employee dossier receives official notification, and request transitions to `ACTIVE`.

### `BP-M1-007`: Change Execution & Transactional ERP Event Emission
- **Trigger:** Atomic database commit in `BP-M1-006`.
- **Actors:** Automated System Engine (`ACT-SYS` - R).
- **Process Steps:**
  1. Within the same database transaction as the master update, an ERP sync payload is written to `ENT-SHR-08`.
  2. Asynchronous poller consumes outbox entry and transmits update to University ERP platform.
  3. System logs transmission receipt and updates sync status to `ACKNOWLEDGED`.

### `BP-M1-008`: Immutable Audit Ledger & Version History Management
- **Trigger:** Any create, update, approve, reject, or lock transaction across the system.
- **Actors:** Automated System Engine (`ACT-SYS` - R).
- **Process Steps:**
  1. Audit interceptor captures actor ID, IP address, timestamp, table name, before-diff, and after-diff.
  2. Interceptor writes append-only record to `ENT-SHR-02`. Mutation or deletion is physically barred.

### `BP-M1-009`: Dynamic Management Reporting & Analytics Query Execution
- **Trigger:** HR administrator or executive runs custom or canned workforce report.
- **Actors:** HR Administrator (`ACT-HRO` - R), Pro-Chancellor / Registrar (`ACT-PRO` / `ACT-REG` - I).
- **Process Steps:**
  1. User specifies filters (department, cadre, tenure, gender, qualification, vacancy status).
  2. System executes read-optimized SQL query against active database state.
  3. System renders interactive grid and enables structured export to XLSX / CSV.

### `BP-M1-010`: Additional Responsibility Assignment & Tenure Tracking (Format 3h)
- **Trigger:** Faculty or staff assigned secondary institutional role (Dean, HOD, Proctor, Warden).
- **Actors:** HR Operations (`ACT-HRO` - R), Senior Management (`ACT-PRO` - A).
- **Process Steps:**
  1. Change request initiated under Format (h) specifying secondary title, department, start date, and tenure.
  2. Primary post remains active; secondary role node is linked to org hierarchy without unseating primary node.
  3. Administrative allowances (if any) are flagged subject to HR policy sanction (`REQ-TBD-09`).

### `BP-M1-011`: Employee Resignation Recording & Departmental Handoff
- **Trigger:** Employee tenders resignation and School Dean formally accepts it.
- **Actors:** School Dean (`ACT-DEA` - R), Head HR (`ACT-HHR` - I), System (`ACT-SYS` - R).
- **Process Steps:**
  1. Dean logs formal resignation acceptance into Module I with effective separation date.
  2. System marks employee status `RESIGNED_SERVING_NOTICE`.
  3. System immediately invokes cross-module handshake `BP-XMOD-002` to trigger urgent recruitment replacement.

---

## 3. Module II — Recruitment & Selection Processes (`BP-M2-001` to `BP-M2-020`)

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               MODULE II: RECRUITMENT LIFECYCLE                                   │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
  [4 Months Prior to Semester] ──► Associate Dean Triggers Academic Manpower Planning
          │
          ▼
  [Deans Submit Attachment 1 (15 Days)] ──► Teaching Load Calculation
          │
          ▼
  [HR 3-Month Vetting Window] ──► Curriculum, Cadre-Ratio & Student-Faculty Checks
          │
          ▼
  [Pro-Chancellor Approval (7 Days)] ──► Public Ad Launch within 7 Days
          │
          ▼
  [Omnichannel CV Ingestion] ──► UGC Norms Shortlisting ──► Recruiter Calling Sheet (RCS)
          │
          ├────────────────────────────────────────┬───────────────────────────────────────┐
          ▼ (Academic Track)                       ▼ (Non-Academic Track)                  ▼ (Urgent)
  [Statutory SCM Panel]                   [3-Round Interviews]                    [Resignation Trigger]
  • VC, Dean, HOD, External Expert        • R1: Technical Panel                   • Immediate Ad-hoc MRF
  • Digital Scoring Matrix                • R2: HR Assessment                     • Bypass Annual Quota
          │                               • R3: Management Review                         │
          ├────────────────────────────────────────┴───────────────────────────────────────┘
          ▼
  [Management Final Sanction] ──► Auto-Generate Letter of Intent (LOI)
          │
          ▼
  [Candidate Accepts LOI] ──► "Yet to Join" Pipeline ──► Day-1 Onboarding Handshake to Module I
```

### Academic Manpower Planning Sub-Workflow (`BP-M2-001` to `BP-M2-006`)
- **`BP-M2-001` (Calendar Trigger):** System triggers Academic Manpower Planning 4 months before semester, dispatching planning templates to all School Deans (`REQ-MOD2-02`).
- **`BP-M2-002` (Dean Submission):** Deans compute semester teaching loads using Attachment 1 and submit requisitions within 15 calendar days (`REQ-MOD2-03`).
- **`BP-M2-003` (HR Vetting Window):** HR conducts comprehensive 3-month vetting of curriculum requirements, student-faculty ratios, and cadre allocations (`REQ-MOD2-04`).
- **`BP-M2-004` (Consolidation):** HR consolidates approved requirements into Master Manpower Plan (Enclosures 1 & 3) within 15 days of vetting completion.
- **`BP-M2-005` (Pro-Chancellor Sanction):** Consolidated plan submitted to Pro-Chancellor with mandatory 7-day turnaround SLA (`REQ-MOD2-05`).
- **`BP-M2-006` (Public Advertisement):** HR launches public recruitment advertisements across print and digital media within 7 days of Pro-Chancellor sanction (`REQ-MOD2-06`).

### Non-Academic Manpower Planning Sub-Workflow (`BP-M2-007` to `BP-M2-010`)
- **`BP-M2-007` (Annual Initiation):** HR initiates annual administrative staffing planning 4 months prior to financial year / onboarding date (`REQ-MOD2-07`).
- **`BP-M2-008` (Annual Requisition Quota):** Department Heads submit planned MRFs within 15 days; system strictly enforces quota of one (1) planned MRF per department per year (`BR-M2-009`).
- **`BP-M2-009` (Approval & Initiation):** Approved non-academic requisitions trigger sourcing within 7 days of management approval.
- **`BP-M2-010` (Completion Window):** Non-academic hiring concluded at least 15 days prior to target onboarding date (`BR-M2-012`).

### Sourcing, Screening & Selection (`BP-M2-011` to `BP-M2-020`)
- **`BP-M2-011` (Urgent Replacement):** Resignation acceptance by Dean bypasses annual quota, immediately opening an urgent replacement MRF and starting the countdown clock (`REQ-MOD2-08`).
- **`BP-M2-012` (Open Positions Tracker):** System maintains authoritative vacancy ledger (Attachment 3 / Enclosure 4), generating weekly executive briefings (`REQ-MOD2-10`, `REQ-REP-03`).
- **`BP-M2-013` (CV Ingestion):** CVs ingested across website, job boards, emails, and Internshala into Central CV Database with duplicate deduplication (`REQ-MOD2-11`).
- **`BP-M2-014` (UGC Shortlisting):** Resumes segregated by academic qualifications, experience, and statutory UGC guidelines (`REQ-MOD2-12`).
- **`BP-M2-015` (RCS Phone Screening):** Recruiters conduct initial telephonic screening, recording communication scores, current CTC, and remarks in Recruiter Calling Sheet (`REQ-MOD2-13`).
- **`BP-M2-016` (Academic SCM Panel):** Statutory committee convened with VC, Dean, HOD, and mandatory External Subject Expert; members record scores in digital matrix (`REQ-MOD2-15`, `REQ-MOD2-16`).
- **`BP-M2-017` (Non-Academic 3-Round Selection):** Candidates evaluated sequentially across Round 1 (Technical), Round 2 (HR), and Round 3 (Management) on Job Knowledge, Communication, Attitude (`REQ-MOD2-17`, `REQ-MOD2-18`).
- **`BP-M2-018` (Executive Sanction):** Compiled selection matrix submitted to Management for compensation and budget clearance.
- **`BP-M2-019` (LOI Generation):** System auto-generates official Letter of Intent (LOI) populated with candidate terms, probation period, and salary breakdown (`REQ-MOD2-19`).
- **`BP-M2-020` (Yet to Join Tracking):** Candidates accepting LOI tracked through notice periods, initiating pre-joining logistics, equipment requests, and Day-1 handoff (`REQ-MOD2-20`).

---

## 4. Module III — Performance Management Processes (`BP-M3-001` to `BP-M3-022`)

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             MODULE III: THREE INDEPENDENT TRACKS                                 │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
  [Subsystem 1: Group-D / Band-I Monthly & Annual Reviews]
  • 1st of Month: Forms Dispatched ──► 7th: Due Date ──► 8th–10th: Grace Period
  • 10th Cutoff: Auto-Lockout Flag ──► VP-Admin Sign-Off ──► Enclosure 2 Collation
  • 1-Year Milestone: 12-Month Weighted Average ──► Probation Gate ──► Pre-Defined Slab Increment

  [Subsystem 2: General Staff KRA/KPI Lifecycle]
  • 30 Days from DOJ: Goal Sheet Setup ──► Joint HR & Management Goal Lock
  • Quarterly Cadence (Q1–Q4): 90d Intimation ──► 20d Reminder ──► 15d Self-Appraisal ──► 7d Review
  • Annual Consolidation: Q1–Q4 Synthesis ──► Direct Service Change Injection to Module I

  [Subsystem 3: Faculty Annual Appraisal via Statutory ECM Route]
  • Monthly 10th Scan: Probation Completed + >= 12 Months Service ──► Certified List to Registrar
  • 7 Working Days: Faculty Self-Appraisal Submission (Enclosure 1)
  • 4-Unit Parallel Verification: Dean, Director R&D, Placement Cell, HR (Dispute Loop)
  • Monthly ECM Session: Statutory Panel Digital Scoring (Enclosure 2)
  • TNU Benchmark Matrix (Enclosure 3) ──► Management Sanction in Next Salary Cycle + Auto-Letter
```

### Subsystem 1: Group-D / Band-I Performance (`BP-M3-001` to `BP-M3-008`)
- **`BP-M3-001` (Dispatch):** Monthly digital Evaluation Form dispatched on 1st of month to evaluating supervisor/HOD.
- **`BP-M3-002` (7th Due Date):** Supervisor evaluates attendance, conduct, task diligence, and hygiene; formal due date on 7th.
- **`BP-M3-003` (Grace & Lockout):** Automated 3-day grace period (8th, 9th, 10th) with daily reminders. At 23:59 on 10th, unsubmitted forms auto-lock and flag non-compliance (`REQ-MOD3-04`).
- **`BP-M3-004` (VP-Admin Approval):** Submitted monthly forms route exclusively to VP-Administration for executive sign-off (`REQ-MOD3-05`).
- **`BP-M3-005` (Monthly Collation):** System collates approved evaluations into Enclosure 2 format for HR.
- **`BP-M3-006` (1-Year Anniversary Milestone):** Exactly 1 year from employee DOJ, system compiles 12-month parameter-weighted average scores (`REQ-MOD3-07`, `REQ-MOD3-08`).
- **`BP-M3-007` (Probation Verification):** System verifies probation clearance; unconfirmed staff cannot receive increments (`REQ-MOD3-09`).
- **`BP-M3-008` (Slab Compensation Update):** System applies institutional pre-defined compensation increment slab and triggers Module I change request (`REQ-TBD-05`).

### Subsystem 2: General Staff KRA/KPI (`BP-M3-009` to `BP-M3-013`)
- **`BP-M3-009` (30-Day Goal Setting):** New administrative joiners configure KRA/KPI Goal Sheets with supervisor within 30 days of joining (`REQ-MOD3-10`).
- **`BP-M3-010` (Joint Lock):** Goal sheets reviewed jointly by HR and Management, freezing targets for the annual cycle (`REQ-MOD3-11`).
- **`BP-M3-011` (Quarterly Review Cadence):** Automated quarterly schedule (Q1–Q4): 90-day advance notice, 20-day reminder, 15-day employee self-review window, 7-day supervisor verification (`REQ-MOD3-12`).
- **`BP-M3-012` (HR Observations):** HR reviews quarterly progress, flags support needs, and submits summary to Management.
- **`BP-M3-013` (Annual Outcome Handshake):** Consolidated annual performance rating triggers in-flight Module I Service Change Request for promotion or salary increment (`REQ-MOD3-13`).

### Subsystem 3: Faculty ECM Performance (`BP-M3-014` to `BP-M3-022`)
- **`BP-M3-014` (Monthly 10th Scan):** Automated engine runs on 10th of every month, scanning for faculty who completed probation and have $\ge$ 12 months service; certified roster sent to Registrar (`REQ-MOD3-14`).
- **`BP-M3-015` (7-Day Self-Appraisal):** Eligible faculty submit digital self-appraisal dossier with publications, workload, and student feedback within 7 working days (`REQ-MOD3-15`).
- **`BP-M3-016` (4-Unit Parallel Verification):** Dossier routed simultaneously to School Dean (academic work), Director R&D (research/patents), Placement Cell (corporate linkages), and HR (leave/conduct) (`REQ-MOD3-16`).
- **`BP-M3-017` (Discrepancy Dispute Loop):** Verifying units can return queries for evidentiary correction; faculty has fixed correction window while verified sections remain locked (`BR-M3-018`).
- **`BP-M3-018` (Monthly ECM Convening):** Registrar dockets verified dossiers for monthly Executive Committee Meeting; panel enters scores into digital Enclosure 2 scorecards (`REQ-MOD3-17`).
- **`BP-M3-019` (TNU Benchmark Matrix):** Scores mapped against TNU Protocol criteria matrix (Enclosure 3) to formulate increment or promotion recommendations (`REQ-MOD3-18`).
- **`BP-M3-020` (Management Sanction):** Executive leadership reviews matrix and sanctions increments.
- **`BP-M3-021` (Next Salary Cycle Execution):** Increment applied in upcoming payroll cycle; system auto-generates official compensation revision letter (`REQ-MOD3-19`).
- **`BP-M3-022` (Dossier Archival):** Full appraisal record, scoring sheets, and signed revision letter archived into Digital Employee File in Module I.

---

## 5. Cross-Module Integration Workflows (`BP-XMOD-001` to `BP-XMOD-006`)

| Process ID | Name | Trigger | Source $\rightarrow$ Target | Outcome |
|---|---|---|---|---|
| `BP-XMOD-001` | Candidate Onboarding Handshake | Day-1 Joining Verification | Mod II $\rightarrow$ Mod I | Auto-instantiates master employee code, Central DB record, org tree node, and digital dossier. |
| `BP-XMOD-002` | Resignation Urgent Replacement | Dean Resignation Acceptance | Mod I $\rightarrow$ Mod II | Alerts Head HR and immediately opens urgent replacement MRF countdown. |
| `BP-XMOD-003` | Master Baseline Data Feed | Daily / Continuous | Mod I $\rightarrow$ Mod III | Provides authoritative DOJ, probation status, department, and supervisor hierarchy. |
| `BP-XMOD-004` | Appraisal Outcome Service Change | Annual Appraisal Approval | Mod III $\rightarrow$ Mod I | Injects formal Service Change Request into Module I, routed for Level-1 & Level-2 approvals. |
| `BP-XMOD-005` | Dynamic Org Realignment | Org Structure Modification | Mod I $\rightarrow$ Mod III | Updates in-flight performance evaluation routing to new supervisor. |
| `BP-XMOD-006` | Transactional ERP Outbox Sync | Master Record Activation | Mod I $\rightarrow$ University ERP | Writes sync event to transactional outbox; poller guarantees delivery. |

---

## 6. Comprehensive SLA and Escalation Matrix

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 AUTOMATED SLA COUNTDOWN MATRIX                                   │
├───────────────┬───────────────────────────────┬──────────────────┬───────────────────────────────┤
│ SLA CODE      │ PROCESS / ACTION              │ WINDOW / TIMER   │ ESCALATION PATHWAY            │
├───────────────┼───────────────────────────────┼──────────────────┼───────────────────────────────┤
│ `SLA-M2-01`   │ Academic Planning Trigger     │ 4 Months Pre-Sem │ Alert to Associate Dean / HR  │
│ `SLA-M2-02`   │ Dean Attachment 1 Submission  │ 15 Calendar Days │ Escalation to Pro-Chancellor  │
│ `SLA-M2-03`   │ HR Curriculum Vetting         │ 3-Month Window   │ Alert to Head HR & Registrar  │
│ `SLA-M2-04`   │ Pro-Chancellor Sanction       │ 7-Day Turnaround │ Executive Briefing to Mgmt    │
│ `SLA-M2-05`   │ Public Advertisement Launch   │ 7 Calendar Days  │ Escalation to Head HR         │
│ `SLA-M2-06`   │ Academic Hiring Concluded     │ 1 Month Pre-Sem  │ High-Priority Staffing Alert  │
│ `SLA-M2-07`   │ Non-Academic Planning Trigger │ 4 Months Pre-Join│ Reminder to Department Heads  │
│ `SLA-M2-08`   │ Non-Academic MRF Submission   │ 15 Calendar Days │ Escalation to Registrar       │
│ `SLA-M2-09`   │ Non-Academic Ad Launch        │ 7 Calendar Days  │ Escalation to Head HR         │
│ `SLA-M2-10`   │ Non-Academic Hiring Concluded │ 15 Days Pre-Join │ Logistics Alert to Dept Head  │
│ `SLA-M3-01`   │ Group-D Monthly Due Date      │ 7th of Month     │ Transition to Grace Period    │
│ `SLA-M3-02`   │ Group-D Daily Reminders       │ 8th, 9th, 10th   │ Daily Alert to Supervisor/HOD │
│ `SLA-M3-03`   │ Group-D Auto-Lockout          │ 10th at 23:59    │ Non-Compliance Flag to HR     │
│ `SLA-M3-04`   │ Staff KRA Goal-Setting        │ 30 Days from DOJ │ Escalation to Supervisor & HR │
│ `SLA-M3-05`   │ Staff Quarterly Self-Review   │ 15 Calendar Days │ Overdue Flag to Supervisor    │
│ `SLA-M3-06`   │ Staff Supervisor Verification │ 7 Calendar Days  │ Escalation to HR Operations   │
│ `SLA-M3-07`   │ Faculty Eligibility Scan      │ 10th of Month    │ Roster Dispatched to Registrar│
│ `SLA-M3-08`   │ Faculty Self-Appraisal Form   │ 7 Working Days   │ Reminder to Faculty & Dean    │
│ `SLA-M3-09`   │ Faculty Increment Execution   │ Next Salary Cycle│ Payroll Discrepancy Escalation│
└───────────────┴───────────────────────────────┴──────────────────┴───────────────────────────────┘
```
