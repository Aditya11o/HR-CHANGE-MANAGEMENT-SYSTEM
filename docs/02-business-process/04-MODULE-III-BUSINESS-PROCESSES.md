# Module III Business Processes — Performance Management Automation
## University HR Change Management & Automation System

**Document Identifier:** `DOC-02-BPM-04`  
**Phase:** Phase 2 — Business Process Documentation (Documentation-Only)  
**Location:** `docs/02-business-process/04-MODULE-III-BUSINESS-PROCESSES.md`  
**Status:** Approved Business Process Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Module Overview & Three-Subsystem Segregation

Module III automates institutional performance appraisal across the University.

> [!IMPORTANT]
> **Strict Operational Separation of Three Performance Subsystems:**  
> The University operates three distinct, non-interchangeable performance management subsystems tailored to specific employment cadres and governance protocols. Under no circumstances are these subsystems merged into a generic appraisal workflow:
> 1. **Subsystem 1 (Group-D / Band-I Support Staff):** Monthly evaluation by HODs; strict due date on the 7th; 3-day grace period to the 10th with daily reminders (8th, 9th, 10th); hard auto-lockout on the 10th; mandatory digital sign-off by the **Vice President – Administration**; automated monthly collation (Enclosure 2); annual 12-month weighted aggregation at 1 year from Date of Joining (DOJ); and a mandatory **Probation Verification Gate**.
> 2. **Subsystem 2 (General Staff KRA/KPI Appraisal Cycle):** 3-stage sequential cadence: Stage 1 (Onboarding goal setting within 30 days of DOJ locked jointly by HR and Management); Stage 2 (Quarterly Q1–Q4 reviews with 90-day intimation, 20-day reminder, 15-day employee submission, and 7-day supervisor verification); and Stage 3 (Annual consolidation with **direct handshake into Module I** for promotion/salary revisions).
> 3. **Subsystem 3 (Faculty Annual Appraisal — ECM Route):** Monthly eligibility batch scanning on the 10th (probation completed + $\ge$ 12 months service); routing of eligible list to the **Office of the Registrar**; digital Self-Appraisal (Enclosure 1) submitted within **7 working days**; parallel verification across four units (**School Dean**, **Director R&D Cell**, **Placement Cell**, **HR Department**) with a circular discrepancy return loop; monthly **Evaluation Committee Meeting (ECM)** with digital score sheets (Enclosure 2); compilation of the **TNU Protocol Matrix** (Enclosure 3); Management compensation decision implemented in the next salary cycle; automated compensation letter generation; and permanent archiving in the Digital Personal File.

---

## 2. Itemized Business Process Directory

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                          MODULE III BUSINESS PROCESS INVENTORY                                   │
├───────────────────┬──────────────────────────────────────────────────┬───────────────────────────┤
│ Process ID        │ Process Name                                     │ Classification & Source   │
├───────────────────┼──────────────────────────────────────────────────┼───────────────────────────┤
│ **SUBSYSTEM 1**   │ **GROUP-D / BAND-I SUPPORT STAFF**               │                           │
│ `BP-M3-GD-001`    │ Monthly Evaluation Form Dispatch & HOD Assignment│ `[A]` Group-D Brief Sec 1 │
│ `BP-M3-GD-002`    │ Monthly Submission Window & Grace Period (7th/10t│ `[A]` Group-D Brief Sec 2 │
│ `BP-M3-GD-003`    │ 10th-of-Month Auto-Lockout & Non-Compliance Flag │ `[A]` Group-D Brief Sec 2 │
│ `BP-M3-GD-004`    │ Executive Approval Gateway — VP-Admin Sign-Off   │ `[A]` Group-D Brief Sec 2 │
│ `BP-M3-GD-005`    │ Monthly Collation & HR Performance Report        │ `[A]` Group-D Brief Sec 3 │
│ `BP-M3-GD-006`    │ Group-D Annual Evaluation & Score Aggregation    │ `[A]` Group-D Brief Sec 4 │
│ `BP-M3-GD-007`    │ Mandatory Support Staff Probation Verification   │ `[A]` Group-D Brief Sec 5 │
│ `BP-M3-GD-008`    │ Support Staff Annual Compensation Review         │ `[A]` Group-D Brief Sec 5 │
├───────────────────┼──────────────────────────────────────────────────┼───────────────────────────┤
│ **SUBSYSTEM 2**   │ **GENERAL STAFF KRA/KPI APPRAISAL CYCLE**        │                           │
│ `BP-M3-KRA-001`   │ Onboarding Goal Setting & Joint Locking (30 Days)│ `[A]` KRA/KPI Stage 1     │
│ `BP-M3-KRA-002`   │ Quarterly Review Cycle Initiation (Q1–Q4)        │ `[A]` KRA/KPI Stage 2     │
│ `BP-M3-KRA-003`   │ Quarterly Submission & Supervisor Verification   │ `[A]` KRA/KPI Stage 2     │
│ `BP-M3-KRA-004`   │ Quarterly HR Observations & Management Review    │ `[A]` KRA/KPI Stage 2     │
│ `BP-M3-KRA-005`   │ Annual Consolidation & Module I Direct Handshake │ `[A]` KRA/KPI Stage 3     │
├───────────────────┼──────────────────────────────────────────────────┼───────────────────────────┤
│ **SUBSYSTEM 3**   │ **FACULTY ANNUAL APPRAISAL (ECM ROUTE)**         │                           │
│ `BP-M3-FAC-001`   │ Monthly Faculty Eligibility Batch Scan (10th)    │ `[A]` Faculty Brief Sec 1 │
│ `BP-M3-FAC-002`   │ Eligible Faculty List Generation & Registrar Rte │ `[A]` Faculty Brief Sec 1 │
│ `BP-M3-FAC-003`   │ Faculty Self-Appraisal Submission (7 Working Days│ `[A]` Faculty Brief Sec 2 │
│ `BP-M3-FAC-004`   │ 4-Unit Parallel Verification (Dean/R&D/Place/HR) │ `[A]` Faculty Brief Sec 3 │
│ `BP-M3-FAC-005`   │ Circular Discrepancy Flagging & Resubmission Loop│ `[A]` Faculty Brief Sec 3 │
│ `BP-M3-FAC-006`   │ Evaluation Committee Meeting (ECM) Digital Score │ `[A]` Faculty Brief Sec 4 │
│ `BP-M3-FAC-007`   │ TNU Protocol Evaluation Matrix Compilation       │ `[A]` Faculty Brief Sec 5 │
│ `BP-M3-FAC-008`   │ Management Decision & Salary Cycle Implementation│ `[A]` Faculty Brief Sec 6 │
│ `BP-M3-FAC-009`   │ Automated Letter Generation & Personal File Arch │ `[A]` Faculty Brief Sec 6 │
└───────────────────┴──────────────────────────────────────────────────┴───────────────────────────┘
```

---

## 3. Subsystem 1: Group-D / Band-I Support Staff Performance (Processes 001–008)

### Process Identifier: BP-M3-GD-001
**Process Name:** Monthly Evaluation Form Dispatch & HOD Assignment

1. **Module / Operational Track:** Module III — Subsystem 1 (Group-D / Band-I Support Staff).
2. **Business Purpose:** Generate and assign standardized monthly performance evaluation forms (Enclosure 1) to Department Heads for all reporting support staff members.
3. **Operational Trigger:** Temporal calendar trigger on the **1st day of every calendar month**.
4. **Prerequisites & Entry Conditions:** Active Group-D employee records in Module I Central Database linked to active HOD reporting supervisors (`BP-XMOD-003`).
5. **Primary Actors:** System Dispatch Engine, Department Heads (HODs / Evaluators).
6. **Supporting Actors:** HR Department (Monitor).
7. **Business Inputs & Documentation:** Active Group-D staff roster, standardized Group-D Evaluation Form (Enclosure 1) containing role-specific operational competencies (discipline, punctuality, task execution, cleanliness, reliability).
8. **Sequential Business Activities:**
   - Step 1: On the 1st of the month, system queries Module I for all active Group-D personnel.
   - Step 2: System instantiates an individual digital Enclosure 1 form for each staff member for the preceding monthly cycle.
   - Step 3: Forms are automatically routed to the task queue of the respective reporting HOD.
   - Step 4: System initiates the monthly submission tracking clock with a target due date of the 7th.
9. **Decision Points & Evaluation Rules:** Verification of active employment status; exclusion of separated or suspended staff.
10. **Approval Points & Governance Gates:** Automated administrative dispatch based on approved master data.
11. **Institutional Outputs & Deliverables:** Assigned monthly evaluation forms in HOD pending queue; active monthly evaluation cycle record.
12. **Operational SLA & Business Deadlines:** Forms dispatched on the **1st of the month**; due date set to the **7th of the month** (`REQ-MOD3-01`, `REQ-MOD3-02`, `REQ-SLA-05`).
13. **Reminders, Escalations & Lockouts:** Automated notification delivered to HOD upon form assignment.
14. **Exception Handling & Alternate Paths:** If an employee transferred departments during the month, the form routes to the HOD where the employee served the majority of the cycle.
15. **Cross-Module Interactions & Handoffs:** Consumes master employee and reporting supervisor edges from Module I (`BP-XMOD-003`).
16. **Process Completion Criteria:** Forms successfully assigned to reporting HODs with active submission tracking.
17. **Audit & Compliance Requirements:** Form dispatch timestamps, assigned HOD IDs, and target staff IDs logged.
18. **Authoritative Source References:** Group-D Brief, Section 1 and Section 2(a); [`REQ-MOD3-01`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-05`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Enclosure 1 field schema is classified under `REQ-TBD-02`.

---

### Process Identifier: BP-M3-GD-002
**Process Name:** Monthly Submission Window & Grace Period (Due 7th, Grace to 10th)

1. **Module / Operational Track:** Module III — Subsystem 1 (Group-D).
2. **Business Purpose:** Enforce a structured submission timeline with automated grace period management and escalating reminder notices for monthly support staff evaluations.
3. **Operational Trigger:** Arrival of the evaluation cycle due date (**7th of the month**) and subsequent grace period dates (**8th, 9th, and 10th**).
4. **Prerequisites & Entry Conditions:** Assigned Enclosure 1 forms pending in HOD queue (`BP-M3-GD-001`).
5. **Primary Actors:** Department Heads (HODs / Evaluators).
6. **Supporting Actors:** HR Department (Monitoring Desk).
7. **Business Inputs & Documentation:** Assigned Enclosure 1 forms, monthly observational performance data.
8. **Sequential Business Activities:**
   - Step 1: HOD evaluates reporting staff and enters ratings across standardized operational parameters.
   - Step 2: HOD signs and submits completed evaluations on or before the **7th of the month**.
   - Step 3: For forms remaining unsubmitted after 23:59 on the 7th, the system initiates the **automated 3-day grace period** (extending from the 8th through the 10th of the month).
   - Step 4: The system dispatches **daily automated reminder notifications** to delinquent HODs on the **8th, 9th, and 10th of the month**.
   - Step 5: HOD may submit pending forms at any point during the grace period without administrative penalty.
9. **Decision Points & Evaluation Rules:** Calendar date evaluation: Is submission within primary window (<= 7th)? Is submission within grace window (8th–10th)?
10. **Approval Points & Governance Gates:** HOD digital sign-off and submission.
11. **Institutional Outputs & Deliverables:** Submitted Group-D Monthly Evaluation moving to `PENDING_VP_APPROVAL` status.
12. **Operational SLA & Business Deadlines:** Strict due date on the **7th of the month**; grace period terminates at end of day on the **10th of the month** (`REQ-MOD3-02`, `REQ-MOD3-03`, `REQ-SLA-06`).
13. **Reminders, Escalations & Lockouts:** Daily high-priority reminders dispatched on the 8th, 9th, and 10th; warning banner highlights impending lockout.
14. **Exception Handling & Alternate Paths:** None. The grace period is universal and automated.
15. **Cross-Module Interactions & Handoffs:** Submitted forms advance to Executive Approval Gateway (`BP-M3-GD-004`).
16. **Process Completion Criteria:** Form successfully submitted by HOD prior to grace period expiration.
17. **Audit & Compliance Requirements:** Submission timestamp, grace period flag, and reminder delivery logs recorded.
18. **Authoritative Source References:** Group-D Brief, Section 2(c, d); [`REQ-MOD3-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD3-03`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-06`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-GD-003
**Process Name:** 10th-of-Month Auto-Lockout Enforcement & Non-Compliance Flagging

1. **Module / Operational Track:** Module III — Subsystem 1 (Group-D).
2. **Business Purpose:** Enforce institutional accountability by automatically locking delinquent monthly evaluations at the expiration of the grace period and logging non-compliance audit records against defaulting HODs.
3. **Operational Trigger:** Expiration of the grace period on the **10th of the month** (`REQ-MOD3-04`).
4. **Prerequisites & Entry Conditions:** Assigned Enclosure 1 forms remaining in `PENDING_SUBMISSION` status as of the end of the 10th of the month.
5. **Primary Actors:** System Governance Engine / Background Worker (`[C] Approved Technical Decision`).
6. **Supporting Actors:** HR Department (Compliance Desk), Defaulting Department Heads.
7. **Business Inputs & Documentation:** Unsubmitted Enclosure 1 form records, HOD user profiles.
8. **Sequential Business Activities:**
   - Step 1: At the close of the 10th of the month, the system evaluates all pending monthly Group-D evaluation forms.
   - Step 2: System executes a **hard administrative lock**, permanently revoking the HOD's capability to edit or submit the evaluation.
   - Step 3: Form status is permanently updated to **`NOT_SUBMITTED`**.
   - Step 4: System generates an institutional Non-Compliance Audit Record linking the delinquent HOD, the affected staff member, and the evaluation month.
   - Step 5: System dispatches formal non-compliance notices to Head HR and the Vice President – Administration (`REQ-REP-07`).
9. **Decision Points & Evaluation Rules:** Strict calendar cutoff check: Form unsubmitted after 10th-of-month grace period.
10. **Approval Points & Governance Gates:** Automated institutional policy enforcement; lock cannot be lifted by the HOD.
11. **Institutional Outputs & Deliverables:** Locked evaluation record tagged `NOT_SUBMITTED`; real-time Non-Compliance Incident Record in HR Compliance Dashboard (`REQ-REP-07`).
12. **Operational SLA & Business Deadlines:** Institutional business cutoff occurs at the **close of the 10th of the month**. *(Technical execution timing at 23:59 is governed by the approved architecture baseline [C])*.
13. **Reminders, Escalations & Lockouts:** Immediate escalation memo delivered to Vice President – Administration and Head HR detailing defaulting departments.
14. **Exception Handling & Alternate Paths:** Locked forms can only be unlocked via extraordinary written administrative sanction from the Vice President – Administration.
15. **Cross-Module Interactions & Handoffs:** Non-compliance records archive in HOD's administrative file; annual report worker handles missing months via imputation policies (`BP-M3-GD-006`).
16. **Process Completion Criteria:** Delinquent forms transitioned to `NOT_SUBMITTED` and non-compliance reports generated.
17. **Audit & Compliance Requirements:** Exact lockout timestamp, system execution log, and defaulting HOD attribution permanently archived.
18. **Authoritative Source References:** Group-D Brief, Section 2(e); [`REQ-MOD3-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-07`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement` (technical execution timing at 23:59 is `[C] Approved Technical Decision`).
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-GD-004
**Process Name:** Executive Approval Gateway — Vice President – Administration Sign-Off

1. **Module / Operational Track:** Module III — Subsystem 1 (Group-D Executive Governance).
2. **Business Purpose:** Enforce mandatory apex administrative oversight and formal executive validation on all submitted monthly support staff evaluations.
3. **Operational Trigger:** HOD submission of a monthly Group-D evaluation (`BP-M3-GD-002`).
4. **Prerequisites & Entry Conditions:** Completed Enclosure 1 form in `PENDING_VP_APPROVAL` status.
5. **Primary Actors:** Vice President – Administration (Apex Approving Authority).
6. **Supporting Actors:** Submitting HOD, Head HR.
7. **Business Inputs & Documentation:** Completed Enclosure 1 evaluation form, HOD ratings, qualitative comments, historical monthly scores.
8. **Sequential Business Activities:**
   - Step 1: VP – Administration accesses monthly executive approval queue.
   - Step 2: Executive reviews HOD evaluation scores against institutional performance standards and inter-departmental parity.
   - Step 3: VP – Administration executes formal determination:
     - **Approve:** Formally signs off on the monthly evaluation.
     - **Return:** Returns evaluation to HOD with directives for rating reconsideration or clarification.
   - Step 4: Approved evaluation transitions to `FINALIZED` status.
9. **Decision Points & Evaluation Rules:** Executive validation of scoring consistency and fairness.
10. **Approval Points & Governance Gates:** Mandatory VP – Administration Approval Gate (`REQ-MOD3-05`). No Group-D evaluation is legally valid or final without this executive sign-off.
11. **Institutional Outputs & Deliverables:** Finalized Monthly Group-D Evaluation record bearing VP – Administration digital signature.
12. **Operational SLA & Business Deadlines:** Executive review targeted within 5 business days of HOD submission.
13. **Reminders, Escalations & Lockouts:** Pending monthly approvals surfaced on executive dashboard.
14. **Exception Handling & Alternate Paths:** Returned evaluations allow HOD resubmission with amended scores within a 48-hour response window.
15. **Cross-Module Interactions & Handoffs:** Approved monthly records feed Monthly Collation (`BP-M3-GD-005`) and Annual Aggregation (`BP-M3-GD-006`).
16. **Process Completion Criteria:** Formal digital signature of Vice President – Administration affixed to evaluation record.
17. **Audit & Compliance Requirements:** Executive signatory ID, approval timestamp, and review remarks permanently archived.
18. **Authoritative Source References:** Group-D Brief, Section 2(b); [`REQ-MOD3-05`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-GD-005
**Process Name:** Monthly Evaluation Collation & HR Performance Report Generation

1. **Module / Operational Track:** Module III — Subsystem 1 (Collation & Analytics).
2. **Business Purpose:** Consolidate approved monthly evaluations across all university departments into an authoritative Monthly Performance Report (Enclosure 2 Template) for HR and executive leadership.
3. **Operational Trigger:** Finalization of monthly evaluations by VP – Administration (`BP-M3-GD-004`).
4. **Prerequisites & Entry Conditions:** Approved monthly evaluations across active departments.
5. **Primary Actors:** HR Department (Analytics Desk), System Collation Engine.
6. **Supporting Actors:** Vice President – Administration.
7. **Business Inputs & Documentation:** Approved Enclosure 1 records, locked non-compliance records, Enclosure 2 (Monthly Performance Report Template).
8. **Sequential Business Activities:**
   - Step 1: System compiles institutional dataset of all monthly evaluations for the target month.
   - Step 2: System populates the standardized **Enclosure 2 Monthly Performance Report**.
   - Step 3: Report aggregates department-wise submission rates, compliance counts, parameter averages, and non-compliance summaries.
   - Step 4: Report is formally delivered to HR Leadership and the Vice President – Administration.
9. **Decision Points & Evaluation Rules:** Complete inclusion check (ensuring every active staff member is accounted for as either evaluated or flagged `NOT_SUBMITTED`).
10. **Approval Points & Governance Gates:** Automated compilation; formal sign-off by Head HR.
11. **Institutional Outputs & Deliverables:** Comprehensive Monthly Performance Report (Enclosure 2); downloadable Excel/PDF datasets (`REQ-REP-05`).
12. **Operational SLA & Business Deadlines:** Report compiled and published within 3 business days following completion of VP approvals.
13. **Reminders, Escalations & Lockouts:** N/A.
14. **Exception Handling & Alternate Paths:** Disputed submissions noted in report commentary.
15. **Cross-Module Interactions & Handoffs:** Provides monthly performance history feeding employee dossier in Module I (`BP-M1-003`).
16. **Process Completion Criteria:** Monthly Enclosure 2 Report compiled, signed, and published to HR repository.
17. **Audit & Compliance Requirements:** Report generation timestamp, compiled dataset hash, and distribution log archived.
18. **Authoritative Source References:** Group-D Brief, Section 3; [`REQ-MOD3-06`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-05`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Enclosure 2 template field schema is classified under `REQ-TBD-02`.

---

### Process Identifier: BP-M3-GD-006
**Process Name:** Group-D Annual Evaluation Trigger & 12-Month Score Aggregation

1. **Module / Operational Track:** Module III — Subsystem 1 (Annual Aggregation).
2. **Business Purpose:** Automatically trigger the annual performance appraisal upon an employee reaching one (1) year of employment (and subsequent years) based on Date of Joining (DOJ), computing parameter-wise weighted averages across all 12 monthly reports.
3. **Operational Trigger:** Calendar milestone reaching **one (1) year of employment** (and annual anniversaries thereafter) calculated from the employee's Date of Joining (DOJ).
4. **Prerequisites & Entry Conditions:** Active Group-D employee record; 12 preceding monthly evaluation cycles logged.
5. **Primary Actors:** System Analytics Engine / Background Worker (`[C] Approved Technical Decision`), HR Department (Appraisal Desk).
6. **Supporting Actors:** Reporting HOD, Vice President – Administration.
7. **Business Inputs & Documentation:** Twelve (12) approved monthly Enclosure 1 evaluations, monthly Enclosure 2 collations, employee master profile.
8. **Sequential Business Activities:**
   - Step 1: System monitors employee DOJ records and detects 1-year employment anniversary milestone (`REQ-MOD3-07`).
   - Step 2: System queries and extracts the twelve (12) monthly evaluation scorecards covering the 1-year evaluation period.
   - Step 3: System compiles the **Annual Performance Report** (`REQ-REP-06`).
   - Step 4: System computes **parameter-wise weighted average scores** across the 12-month period for each operational competency (task execution, punctuality, reliability, etc.) (`REQ-MOD3-08`).
   - Step 5: System calculates overall cumulative annual composite rating.
   - Step 6: Annual Report routes to the Mandatory Probation Verification Gate (`BP-M3-GD-007`).
9. **Decision Points & Evaluation Rules:** Verification that 12 full monthly records exist; application of institutional weighted scoring algorithm.
10. **Approval Points & Governance Gates:** Automated milestone compilation; verified by HR Appraisal Officer.
11. **Institutional Outputs & Deliverables:** Comprehensive Group-D Annual Performance Report containing 12-month trend charts, parameter averages, and composite annual score (`REQ-REP-06`).
12. **Operational SLA & Business Deadlines:** Annual Report generated on or before the employee's annual DOJ anniversary date.
13. **Reminders, Escalations & Lockouts:** Incomplete monthly histories (due to past unsubmitted evaluations) flag HR Appraisal Desk for policy-based score handling.
14. **Exception Handling & Alternate Paths:** For staff on approved long medical leaves, annual window adjusts proportionally in accordance with university service regulations.
15. **Cross-Module Interactions & Handoffs:** Consumes DOJ master date from Module I (`BP-XMOD-003`); advances report to Probation Gate (`BP-M3-GD-007`).
16. **Process Completion Criteria:** Annual Report fully compiled with validated 12-month parameter averages.
17. **Audit & Compliance Requirements:** Calculation formulas, monthly input data points, and compilation timestamp archived.
18. **Authoritative Source References:** Group-D Brief, Section 4(a, b); [`REQ-MOD3-07`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD3-08`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-06`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Parameter mathematical scoring weights are classified under `REQ-TBD-04`.

---

### Process Identifier: BP-M3-GD-007
**Process Name:** Mandatory Support Staff Probation Verification Gate

1. **Module / Operational Track:** Module III — Subsystem 1 (Statutory Compliance Gate).
2. **Business Purpose:** Enforce a strict statutory verification gate ensuring that unconfirmed support staff or staff with uncompleted probation cannot advance to annual compensation review.
3. **Operational Trigger:** Compilation of the Group-D Annual Performance Report (`BP-M3-GD-006`).
4. **Prerequisites & Entry Conditions:** Completed Annual Performance Report.
5. **Primary Actors:** System Policy Engine, HR Department (Compliance Officer).
6. **Supporting Actors:** Vice President – Administration.
7. **Business Inputs & Documentation:** Annual Performance Report, employee probation status record from Module I Central Database.
8. **Sequential Business Activities:**
   - Step 1: System queries Module I master record to verify the employee's formal probation completion status (`probation_completed = TRUE`).
   - Step 2: System evaluates probation gate rule:
     - **Probation Formally Completed:** Employee successfully clears gate; dossier advances to Compensation Review (`BP-M3-GD-008`).
     - **Probation Still Pending / Active / Extended:** System enforces **hard administrative halt**. Workflow stops immediately; employee is barred from compensation revision review.
   - Step 3: For blocked employees, system generates formal probation review notification to HR Leadership and HOD to determine probation confirmation or extension.
9. **Decision Points & Evaluation Rules:** Strict binary gate: Is `probation_completed` officially confirmed as `TRUE` in the employee service ledger?
10. **Approval Points & Governance Gates:** Mandatory Statutory Compliance Gate (`REQ-MOD3-09`). The system strictly prohibits bypassing this gate under any administrative role.
11. **Institutional Outputs & Deliverables:** Validated gate clearance certificate OR formal Probation Non-Confirmation Halt Memo.
12. **Operational SLA & Business Deadlines:** Executed synchronously upon Annual Report compilation.
13. **Reminders, Escalations & Lockouts:** Unconfirmed staff approaching 1-year milestone trigger advance probation assessment reminders to HOD at month 11.
14. **Exception Handling & Alternate Paths:** If probation is extended by Management, annual compensation review is deferred until formal probation clearance is recorded in Module I.
15. **Cross-Module Interactions & Handoffs:** Inspects probation status in Module I (`BP-XMOD-003`); advances confirmed staff to Compensation Review (`BP-M3-GD-008`).
16. **Process Completion Criteria:** Formal verification of probation clearance logged in appraisal dossier.
17. **Audit & Compliance Requirements:** Verification query timestamp, source record reference, and gate determination archived.
18. **Authoritative Source References:** Group-D Brief, Section 5(b); [`REQ-MOD3-09`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-GD-008
**Process Name:** Support Staff Annual Compensation Review & Outcome Archiving

1. **Module / Operational Track:** Module III — Subsystem 1 (Compensation Governance).
2. **Business Purpose:** Review the completed Annual Report against Management's pre-defined compensation revision slabs, record final executive decisions, and permanently archive outcomes in the employee dossier.
3. **Operational Trigger:** Successful clearance of the Probation Verification Gate (`BP-M3-GD-007`).
4. **Prerequisites & Entry Conditions:** Annual Performance Report cleared by probation gate; active pre-defined compensation slabs.
5. **Primary Actors:** Senior Management (Compensation Approving Authority), Vice President – Administration.
6. **Supporting Actors:** Head HR, Finance Controller.
7. **Business Inputs & Documentation:** Completed Annual Report with 12-month parameter averages, current base salary, Management pre-defined compensation revision slabs (`REQ-TBD-05`).
8. **Sequential Business Activities:**
   - Step 1: Senior Management and VP – Administration review the candidate's Annual Report composite score.
   - Step 2: Management maps the candidate's score against institutional pre-defined compensation slabs (e.g., exemplary performance slab, standard increment slab, performance improvement / freeze slab).
   - Step 3: Management logs formal executive decision:
     - Specific annual salary increment percentage or fixed monetary revision.
     - Confirmation of title or grade progression (if applicable).
   - Step 4: Executive decision is digitally signed.
   - Step 5: System executes automated handshake, injecting formal service change request into Module I (`BP-XMOD-004`).
   - Step 6: Complete annual appraisal dossier is permanently archived in the employee's Digital Personal File (`BP-M1-003`).
9. **Decision Points & Evaluation Rules:** Application of pre-defined compensation slabs based on annual aggregate score.
10. **Approval Points & Governance Gates:** Apex Management Compensation Approval Gate.
11. **Institutional Outputs & Deliverables:** Signed Annual Compensation Review Order; archived appraisal dossier; initiated Module I Change Request.
12. **Operational SLA & Business Deadlines:** Compensation review completed within 15 business days of annual anniversary.
13. **Reminders, Escalations & Lockouts:** Pending compensation reviews alert HR Leadership.
14. **Exception Handling & Alternate Paths:** Exceptional performance exceeding standard slabs may be awarded special executive merit allowance.
15. **Cross-Module Interactions & Handoffs:** Injects formal Change Request (Format a / Format e) directly into Module I without manual re-entry (`BP-XMOD-004`).
16. **Process Completion Criteria:** Management compensation order signed, Module I change initiated, and records archived.
17. **Audit & Compliance Requirements:** Executive signatures, applied slab formula reference, and differential salary order permanently preserved.
18. **Authoritative Source References:** Group-D Brief, Section 5(a); [`REQ-MOD3-09`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-INT-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Quantitative monetary values and percentage brackets of pre-defined compensation slabs are classified under `REQ-TBD-05`.

---

## 4. Subsystem 2: General Staff KRA/KPI Appraisal Cycle (Processes 009–013)

### Process Identifier: BP-M3-KRA-001
**Process Name:** Onboarding Goal Setting & Joint Locking Window (30 Days from DOJ)

1. **Module / Operational Track:** Module III — Subsystem 2 (General Staff KRA/KPI — Stage 1).
2. **Business Purpose:** Ensure every newly appointed general staff member configures standardized Key Result Areas (KRAs) and Key Performance Indicators (KPIs) in collaboration with their Reporting Authority, formally verified and locked by HR and Management within 30 days of joining.
3. **Operational Trigger:** Creation of an active employee record in Module I Central Database (`BP-XMOD-001`).
4. **Prerequisites & Entry Conditions:** Active staff member profile; assigned Reporting Authority.
5. **Primary Actors:** Employee (New Joiner), Reporting Authority (Supervisor), HR Department (Verifier), Senior Management (Locking Authority).
6. **Supporting Actors:** Department Head.
7. **Business Inputs & Documentation:** Job description, departmental operational goals, standardized KRA/KPI Goal Sheet template.
8. **Sequential Business Activities:**
   - Step 1: Upon new employee creation, the system **initiates a strict 30-day countdown timer** from Date of Joining (DOJ) (`REQ-MOD3-10`, `REQ-SLA-07`).
   - Step 2: Employee and Reporting Authority collaborate to draft 3 to 5 core KRAs with measurable quarterly KPIs, metrics, and targets.
   - Step 3: Reporting Authority endorses and submits drafted goal sheet to HR.
   - Step 4: HR verifies that goals align with institutional standards and job level expectations.
   - Step 5: Goal sheet is submitted to **Senior Management** for executive review.
   - Step 6: Upon joint review, **HR and Management formally lock the Goal Sheet** (`REQ-MOD3-11`, `REQ-AUD-04`).
   - Step 7: Goal sheet is frozen; targets cannot be modified during the evaluation cycle without tracked formal amendment.
9. **Decision Points & Evaluation Rules:** Verification that KPIs are measurable, time-bound, and aligned with departmental objectives.
10. **Approval Points & Governance Gates:** Mandatory Joint Goal-Locking Gate (`REQ-MOD3-11`). Requisite sign-offs from both HR and Senior Management.
11. **Institutional Outputs & Deliverables:** Formal, Version-Locked KRA/KPI Goal Sheet establishing performance baseline for the annual cycle.
12. **Operational SLA & Business Deadlines:** Entire goal setting and locking process completed within **thirty (30) days from Date of Joining (DOJ)** (`REQ-MOD3-10`, `REQ-SLA-07`).
13. **Reminders, Escalations & Lockouts:** Daily countdown reminders dispatched on Day 15, Day 20, and Day 25; escalation to Head HR if unfinalized at Day 28.
14. **Exception Handling & Alternate Paths:** Mid-cycle role reassignments require formal submission of a Goal Revision Request, subject to re-locking by HR and Management.
15. **Cross-Module Interactions & Handoffs:** Triggered by Module I new joiner event (`BP-XMOD-001`); establishes targets for Quarterly Review Cycles (`BP-M3-KRA-002`).
16. **Process Completion Criteria:** Goal sheet digitally locked by both HR and Management.
17. **Audit & Compliance Requirements:** Immutable version locking; snapshot of frozen targets, signatory IDs, and lock timestamps archived (`REQ-AUD-04`).
18. **Authoritative Source References:** KRA/KPI Brief, Stage 1; [`REQ-MOD3-10`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD3-11`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-07`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-AUD-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Specific KPI scoring schema template is classified under `REQ-TBD-02`.

---

### Process Identifier: BP-M3-KRA-002
**Process Name:** Quarterly Review Cycle Initiation & Milestone Scheduling (Q1–Q4)

1. **Module / Operational Track:** Module III — Subsystem 2 (General Staff KRA/KPI — Stage 2).
2. **Business Purpose:** Orchestrate the recurring quarterly performance appraisal milestones across four sequential quarters (Q1, Q2, Q3, Q4), enforcing advance notifications and reminder cadences.
3. **Operational Trigger:** Temporal milestone reaching **90 days from DOJ** (and subsequent 90-day intervals for Q2, Q3, and Q4).
4. **Prerequisites & Entry Conditions:** Locked KRA/KPI Goal Sheet (`BP-M3-KRA-001`).
5. **Primary Actors:** System Recurrence Engine / Background Scheduler (`[C] Approved Technical Decision`).
6. **Supporting Actors:** Employee, Reporting Authority, HR Department.
7. **Business Inputs & Documentation:** Locked Goal Sheet, quarterly milestone calendar.
8. **Sequential Business Activities:**
   - Step 1: System calculates quarterly milestone date at **90 days from DOJ** (and subsequent quarterly multiples).
   - Step 2: System dispatches formal **90-Day Intimation Notification** to employee and Reporting Authority, opening the quarterly evaluation window (`REQ-MOD3-12`, `REQ-SLA-08`).
   - Step 3: System monitors submission progress against quarterly deadline.
   - Step 4: If employee submission remains pending, system dispatches an automated **20-Day Reminder Alert** (`REQ-MOD3-12`, `REQ-SLA-08`).
   - Step 5: Process repeats identically across Q1, Q2, Q3, and Q4 cycles.
9. **Decision Points & Evaluation Rules:** Calendar calculation check: Has 90 days elapsed since DOJ/prior quarter mark?
10. **Approval Points & Governance Gates:** Automated schedule trigger.
11. **Institutional Outputs & Deliverables:** Active Quarterly Review Form in employee dashboard; dispatched intimation and reminder notices.
12. **Operational SLA & Business Deadlines:** Intimation issued at **90 days from DOJ**; reminder dispatched at **20 days pending** (`REQ-MOD3-12`, `REQ-SLA-08`).
13. **Reminders, Escalations & Lockouts:** Automated 20-day reminder notice delivered to employee and supervisor.
14. **Exception Handling & Alternate Paths:** Authorized medical leaves adjust quarterly window in accordance with university policy.
15. **Cross-Module Interactions & Handoffs:** Advances employee to Quarterly Self-Review Submission (`BP-M3-KRA-003`).
16. **Process Completion Criteria:** Quarterly review cycle formally opened and notifications delivered.
17. **Audit & Compliance Requirements:** Milestone dates, intimation timestamps, and reminder logs preserved.
18. **Authoritative Source References:** KRA/KPI Brief, Stage 2; [`REQ-MOD3-12`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-08`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-KRA-003
**Process Name:** Quarterly Self-Review Submission & Supervisor Verification (15 Days / 7 Days)

1. **Module / Operational Track:** Module III — Subsystem 2 (General Staff KRA/KPI — Stage 2).
2. **Business Purpose:** Enable employees to submit quarterly self-evaluations with documentary evidence, followed by rigorous verification and scoring by the Reporting Authority within defined SLA windows.
3. **Operational Trigger:** Receipt of the 90-Day Quarterly Review Intimation (`BP-M3-KRA-002`).
4. **Prerequisites & Entry Conditions:** Active quarterly evaluation window; locked goal sheet.
5. **Primary Actors:** Employee (Self-Evaluator), Reporting Authority / Supervisor (Verifier).
6. **Supporting Actors:** HR Department (Monitor).
7. **Business Inputs & Documentation:** Quarterly Review Form, self-ratings, achievement narratives, uploaded documentary evidence (work samples, completion reports, project sign-offs).
8. **Sequential Business Activities:**
   - Step 1: Employee accesses digital Quarterly Review Form.
   - Step 2: Employee logs self-evaluation scores against locked KPIs, provides narrative justifications, and uploads supporting evidence.
   - Step 3: Employee formally submits self-review within the mandatory **15-day submission window**.
   - Step 4: System routes submitted dossier to the **Reporting Authority / Supervisor**.
   - Step 5: Reporting Authority reviews employee self-ratings, examines uploaded evidence, enters supervisor scores, and logs qualitative performance feedback.
   - Step 6: Reporting Authority formally submits verified quarterly review to HR within the mandatory **7-day supervisor verification window**.
9. **Decision Points & Evaluation Rules:** Supervisor validation of self-ratings against objective documentary evidence.
10. **Approval Points & Governance Gates:** Formal digital verification sign-off by Reporting Authority.
11. **Institutional Outputs & Deliverables:** Verified Quarterly Review Record containing joint ratings, qualitative feedback, and attached evidence.
12. **Operational SLA & Business Deadlines:** Employee submission within **15 days** of review trigger; Supervisor verification within **7 days** of employee submission (`REQ-MOD3-12`, `REQ-SLA-08`).
13. **Reminders, Escalations & Lockouts:** Daily countdown reminders dispatched during final 3 days of employee and supervisor windows; delinquent verifications alert HOD.
14. **Exception Handling & Alternate Paths:** Supervisor may return self-review to employee for missing evidence, initiating a 48-hour correction window.
15. **Cross-Module Interactions & Handoffs:** Routes verified dossier to HR and Management Review (`BP-M3-KRA-004`).
16. **Process Completion Criteria:** Formal digital verification submitted by Reporting Authority.
17. **Audit & Compliance Requirements:** Employee submission timestamp, supervisor verification timestamp, rating differentials, and uploaded evidence checksums archived.
18. **Authoritative Source References:** KRA/KPI Brief, Stage 2; [`REQ-MOD3-12`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-08`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-KRA-004
**Process Name:** Quarterly HR Compliance Observations & Management Executive Review

1. **Module / Operational Track:** Module III — Subsystem 2 (General Staff KRA/KPI — Stage 2).
2. **Business Purpose:** Provide administrative compliance auditing by HR and executive oversight by Senior Management on quarterly staff appraisals.
3. **Operational Trigger:** Submission of verified quarterly review by Reporting Authority (`BP-M3-KRA-003`).
4. **Prerequisites & Entry Conditions:** Completed supervisor verification.
5. **Primary Actors:** HR Department (Compliance Reviewer), Senior Management (Executive Reviewer).
6. **Supporting Actors:** Reporting Authority, Employee.
7. **Business Inputs & Documentation:** Completed quarterly review dossier, supervisor ratings, uploaded work evidence.
8. **Sequential Business Activities:**
   - Step 1: HR Department conducts compliance review, verifying adherence to institutional rating distributions and SLA timelines, and **records formal HR observations** in the dossier.
   - Step 2: Dossier routes to **Senior Management**.
   - Step 3: Senior Management reviews employee progress, examines supervisor and HR notes, and **records executive comments**.
   - Step 4: Quarterly review cycle is formally closed and locked.
   - Step 5: Feedback and finalized quarterly ratings are made accessible to the employee and supervisor.
9. **Decision Points & Evaluation Rules:** HR compliance check; Management strategic assessment.
10. **Approval Points & Governance Gates:** Quarterly executive review sign-off.
11. **Institutional Outputs & Deliverables:** Closed, fully endorsed Quarterly Performance Record.
12. **Operational SLA & Business Deadlines:** HR observations within 5 days; Management review within 5 days.
13. **Reminders, Escalations & Lockouts:** N/A.
14. **Exception Handling & Alternate Paths:** Significant rating disparities between self-rating and supervisor score trigger HR mediation.
15. **Cross-Module Interactions & Handoffs:** Archived quarterly record feeds Annual Consolidation upon Q4 completion (`BP-M3-KRA-005`).
16. **Process Completion Criteria:** Formal closure of quarterly cycle with HR observations and Management comments logged.
17. **Audit & Compliance Requirements:** Signatory IDs, review comments, and closure timestamps preserved.
18. **Authoritative Source References:** KRA/KPI Brief, Stage 2; [`REQ-MOD3-12`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-KRA-005
**Process Name:** Annual KRA/KPI Appraisal Consolidation & Module I Direct Handshake

1. **Module / Operational Track:** Module III — Subsystem 2 (General Staff KRA/KPI — Stage 3 & Cross-Module Handshake).
2. **Business Purpose:** Aggregate four quarterly review outcomes (Q1–Q4) into a comprehensive annual performance evaluation, capture Management's final recommendation, and execute an automated direct handshake into Module I for applicable salary, designation, or level adjustments.
3. **Operational Trigger:** Formal closure of the Quarter 4 (Q4) review cycle (`BP-M3-KRA-004`).
4. **Prerequisites & Entry Conditions:** Closed Q1, Q2, Q3, and Q4 review records for the evaluation year.
5. **Primary Actors:** Senior Management (Final Decision Authority), HR Department (Appraisal Desk).
6. **Supporting Actors:** Reporting Authority, Employee.
7. **Business Inputs & Documentation:** Q1–Q4 quarterly scorecards, cumulative annual score aggregation, employee service history, departmental staffing budget.
8. **Sequential Business Activities:**
   - Step 1: System compiles **Annual KRA/KPI Summary Dossier**, aggregating ratings across all four quarters into a single institutional score.
   - Step 2: System triggers formal annual appraisal request to **Senior Management**.
   - Step 3: Senior Management evaluates annual performance and logs final executive recommendation:
     - **Annual Increment:** Percentage or monetary salary revision.
     - **Designation Change:** Merit promotion or role elevation.
     - **Level Promotion:** Band/grade progression.
     - **Performance Maintenance / Improvement Plan:** Retaining current terms.
   - Step 4: **Direct Handshake:** The system automatically executes a transactional call into **Module I (ChangeManagementModule)**, instantiating a formal Change Request (Format a, b, and/or e) populated with approved values **without manual data re-entry** (`REQ-MOD3-13`, `REQ-INT-04`).
   - Step 5: Complete annual appraisal dossier is permanently archived in the employee's Digital Personal File (`BP-M1-003`).
9. **Decision Points & Evaluation Rules:** Senior Management determination of performance merit against institutional promotion and compensation policies.
10. **Approval Points & Governance Gates:** Apex Management Annual Appraisal Approval Gate.
11. **Institutional Outputs & Deliverables:** Signed Annual KRA/KPI Performance Order; auto-instantiated Module I Change Request in `SUBMITTED` status; archived digital dossier.
12. **Operational SLA & Business Deadlines:** Annual consolidation and handshake executed within 15 business days of Q4 closure.
13. **Reminders, Escalations & Lockouts:** Pending annual decisions alert Chancellor's Secretariat.
14. **Exception Handling & Alternate Paths:** If Management determines no change in service terms, the record archives without initiating a Module I change request.
15. **Cross-Module Interactions & Handoffs:** Directly initializes formal Change Request in Module I (`BP-M1-004`, `BP-XMOD-004`); archives records in Digital Dossier (`BP-M1-003`).
16. **Process Completion Criteria:** Module I Change Request successfully instantiated with confirmed transaction reference.
17. **Audit & Compliance Requirements:** Executive sign-off, annual score aggregation formulas, and cross-module handshake transaction IDs permanently archived.
18. **Authoritative Source References:** KRA/KPI Brief, Stage 3; [`REQ-MOD3-13`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-INT-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Quantitative promotion criteria and compensation revision slabs are classified under `REQ-TBD-05`.

---

## 5. Subsystem 3: Faculty Annual Performance Appraisal — ECM Route (Processes 014–022)

### Process Identifier: BP-M3-FAC-001
**Process Name:** Monthly Faculty Appraisal Eligibility Identification (10th-of-Month Scanner)

1. **Module / Operational Track:** Module III — Subsystem 3 (Faculty ECM Route).
2. **Business Purpose:** Automatically identify all faculty members eligible for annual performance appraisal and statutory compensation review based on regulatory service milestones.
3. **Operational Trigger:** Temporal calendar trigger on the **10th day of every calendar month**.
4. **Prerequisites & Entry Conditions:** Active faculty employment records in Module I Central Database (`BP-XMOD-003`).
5. **Primary Actors:** System Eligibility Scanner / Batch Worker (`[C] Approved Technical Decision`).
6. **Supporting Actors:** HR Department (Appraisal Desk).
7. **Business Inputs & Documentation:** Central Employee Database records, Date of Joining (DOJ), probation completion flags, date of last appraisal.
8. **Sequential Business Activities:**
   - Step 1: On the 10th of every month, system executes automated eligibility query against Module I.
   - Step 2: System evaluates mandatory statutory eligibility criteria:
     - `probation_completed = TRUE` (Mandatory confirmation check)
     - `(current_date - last_appraisal_date) >= 12 months` (OR `(current_date - DOJ) >= 12 months` if first annual appraisal)
   - Step 3: System compiles verified list of faculty members satisfying both conditions.
   - Step 4: System transitions eligible candidates into active appraisal tracking for the monthly cohort.
9. **Decision Points & Evaluation Rules:** Strict statutory eligibility rules:
   - Is probation confirmed as completed?
   - Has at least 12 months elapsed since last appraisal (or DOJ)?
10. **Approval Points & Governance Gates:** Automated query execution based on approved master service data.
11. **Institutional Outputs & Deliverables:** Identified cohort of eligible faculty members; automated eligibility log.
12. **Operational SLA & Business Deadlines:** Executed on the **10th of every month** (`REQ-MOD3-14`, `REQ-REP-08`).
13. **Reminders, Escalations & Lockouts:** Zero-eligible cohorts logged with audit confirmation.
14. **Exception Handling & Alternate Paths:** Faculty with disputed probation or appraisal dates flagged for manual HR reconciliation.
15. **Cross-Module Interactions & Handoffs:** Consumes master employee service dates and probation status from Module I (`BP-XMOD-003`).
16. **Process Completion Criteria:** Eligible faculty cohort identified and validated.
17. **Audit & Compliance Requirements:** Query execution timestamp, evaluated employee count, and matched candidate list archived.
18. **Authoritative Source References:** Faculty ECM Brief, Section 1; [`REQ-MOD3-14`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-08`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Operational appraisal track definitions for Teaching Associates and Lab Technicians are classified under `REQ-TBD-03`.

---

### Process Identifier: BP-M3-FAC-002
**Process Name:** Eligible Faculty List Generation & Registrar Routing

1. **Module / Operational Track:** Module III — Subsystem 3 (Faculty ECM Route).
2. **Business Purpose:** Generate the official Monthly Eligible Faculty List and transmit it from HR to the Office of the Registrar with automated escalation tracking.
3. **Operational Trigger:** Successful execution of the monthly eligibility batch scan (`BP-M3-FAC-001`).
4. **Prerequisites & Entry Conditions:** Verified cohort of eligible faculty members.
5. **Primary Actors:** HR Department (Appraisal Desk / Head HR), Registrar / Office of the Registrar (Recipient Authority).
6. **Supporting Actors:** Senior Management.
7. **Business Inputs & Documentation:** Eligible faculty list, department/school affiliations, DOJ, date of last appraisal, current salary and designation.
8. **Sequential Business Activities:**
   - Step 1: System compiles the official **Monthly Eligible Faculty List** (`REQ-REP-08`).
   - Step 2: Head HR reviews and formally endorses the monthly list.
   - Step 3: System automatically transmits the endorsed list from HR to the **Office of the Registrar**.
   - Step 4: Registrar's office verifies the cohort and executes confirmation.
   - Step 5: System monitors Registrar confirmation; if delayed, automated escalation notifications are dispatched to Senior Management (`REQ-MOD3-14`).
9. **Decision Points & Evaluation Rules:** Registrar verification of statutory eligibility and absence of ongoing disciplinary proceedings.
10. **Approval Points & Governance Gates:** Formal endorsement by Head HR and confirmation sign-off by Registrar.
11. **Institutional Outputs & Deliverables:** Confirmed Monthly Eligible Faculty List; routing transmittal memo.
12. **Operational SLA & Business Deadlines:** List transmitted on or before the **10th of the month**; Registrar confirmation targeted within 3 business days (`REQ-MOD3-14`).
13. **Reminders, Escalations & Lockouts:** Automated escalation alert delivered to Vice Chancellor / Senior Management if Registrar confirmation exceeds SLA window.
14. **Exception Handling & Alternate Paths:** Faculty members facing formal disciplinary inquiry may be deferred by Registrar with documented statutory memo.
15. **Cross-Module Interactions & Handoffs:** Registrar confirmation triggers automatic issuance of Self-Appraisal Forms (`BP-M3-FAC-003`).
16. **Process Completion Criteria:** Formal digital confirmation logged by Office of the Registrar.
17. **Audit & Compliance Requirements:** Transmittal timestamp, recipient acknowledgment, and escalation logs archived.
18. **Authoritative Source References:** Faculty ECM Brief, Section 1; [`REQ-MOD3-14`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-FAC-003
**Process Name:** Faculty Self-Appraisal Form Issuance & Submission Window (7 Working Days)

1. **Module / Operational Track:** Module III — Subsystem 3 (Faculty ECM Route).
2. **Business Purpose:** Issue standardized digital Self-Appraisal Forms (Enclosure 1) to confirmed eligible faculty members and enforce a strict 7-working-day submission window with mandatory documentary evidence upload.
3. **Operational Trigger:** Formal confirmation of the eligible faculty list by the Office of the Registrar (`BP-M3-FAC-002`).
4. **Prerequisites & Entry Conditions:** Faculty member confirmed on official eligible list.
5. **Primary Actors:** Eligible Faculty Member (Self-Appraiser).
6. **Supporting Actors:** HR Department (Appraisal Desk).
7. **Business Inputs & Documentation:** Standardized Faculty Self-Appraisal Form (Enclosure 1), academic teaching schedules, research publication reprints, grant award letters, student feedback summaries, patent certificates, placement assistance records.
8. **Sequential Business Activities:**
   - Step 1: System automatically issues digital Enclosure 1 form to each eligible faculty member.
   - Step 2: System **initiates a strict countdown timer of seven (7) working days** (`REQ-MOD3-15`, `REQ-SLA-09`).
   - Step 3: Faculty member completes self-appraisal sections:
     - Part A: Academic & Pedagogical Contributions (teaching hours, courses taught, lab development).
     - Part B: Research, Publications & Scholarly Activity (UGC-CARE/Scopus indexed papers, citations, books).
     - Part C: Sponsored Research & Consultancy (grant funding, patents, industry projects).
     - Part D: Institutional Service, Placements & Student Mentorship.
   - Step 4: Faculty member uploads mandatory documentary evidence for every claimed contribution.
   - Step 5: Faculty member digitally signs and submits completed dossier within 7 working days.
9. **Decision Points & Evaluation Rules:** Verification that mandatory evidence attachments are provided for all claimed publications and grants.
10. **Approval Points & Governance Gates:** Faculty member digital signature and submission.
11. **Institutional Outputs & Deliverables:** Submitted Faculty Self-Appraisal Dossier with attached evidentiary documents.
12. **Operational SLA & Business Deadlines:** Mandatory submission within **seven (7) working days** of notification receipt (`REQ-MOD3-15`, `REQ-SLA-09`).
13. **Reminders, Escalations & Lockouts:** Daily countdown reminders delivered to faculty member; urgent alerts on Days 5, 6, and 7.
14. **Exception Handling & Alternate Paths:** Failure to submit within 7 working days results in deferral of appraisal to subsequent cycle unless granted medical waiver by Registrar.
15. **Cross-Module Interactions & Handoffs:** Submitted dossier initiates Multi-Departmental Parallel Verification (`BP-M3-FAC-004`).
16. **Process Completion Criteria:** Self-appraisal form and all mandatory attachments successfully submitted.
17. **Audit & Compliance Requirements:** Submission timestamp, uploaded file checksums, and countdown logs preserved.
18. **Authoritative Source References:** Faculty ECM Brief, Section 2; [`REQ-MOD3-15`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-09`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Enclosure 1 standardized schema is classified under `REQ-TBD-02`.

---

### Process Identifier: BP-M3-FAC-004
**Process Name:** Multi-Departmental Parallel Verification Workflow (Dean, R&D, Placement, HR)

1. **Module / Operational Track:** Module III — Subsystem 3 (Parallel Academic Verification).
2. **Business Purpose:** Distribute the submitted faculty appraisal dossier simultaneously across four specialized institutional verification units to rigorously audit claimed contributions prior to committee evaluation.
3. **Operational Trigger:** Faculty submission of Self-Appraisal Dossier (`BP-M3-FAC-003`).
4. **Prerequisites & Entry Conditions:** Submitted Enclosure 1 dossier with uploaded evidence attachments.
5. **Primary Actors (Four Parallel Verification Units):**
   - **Unit 1 — School Dean:** Verifies teaching contact hours, syllabus coverage, student feedback scores, and departmental academic contributions.
   - **Unit 2 — Director, R&D Cell:** Verifies indexed publications (UGC-CARE / Scopus / SCI), journal impact factors, citations, sponsored research grant sanctioned amounts, and patent filings.
   - **Unit 3 — Head, Placement Cell:** Verifies faculty contributions to student placement drives, industry internship facilitation, and corporate liaison activities.
   - **Unit 4 — HR Department:** Verifies leave records, statutory biometric attendance compliance, administrative allowances, and disciplinary clearance.
6. **Supporting Actors:** Faculty Member (Subject of verification).
7. **Business Inputs & Documentation:** Submitted Self-Appraisal form, uploaded evidence files, institutional student feedback repository, R&D grant ledgers, central placement records, biometric attendance logs.
8. **Sequential Business Activities:**
   - Step 1: System dispatches dossier simultaneously into the verification queues of all four units.
   - Step 2: Each verifier independently audits claimed points against institutional records and uploaded evidence.
   - Step 3: Each verifier enters verified score and qualitative validation remarks.
   - Step 4: Each verifier executes one of two determinations:
     - **Verified / Endorsed:** Confirms accuracy of claimed points.
     - **Flag Discrepancy:** Identifies unverified claims or deficient evidence, initiating the Discrepancy Loop (`BP-M3-FAC-005`).
   - Step 5: System monitors parallel completion; all four units must complete verification before dossier can advance to ECM scheduling.
9. **Decision Points & Evaluation Rules:** Verification against institutional records: Are journal papers indexed in approved lists? Are grant figures confirmed by finance?
10. **Approval Points & Governance Gates:** Digital sign-off executed independently by each of the four verifiers (Dean, Director R&D, Placement Head, HR Officer).
11. **Institutional Outputs & Deliverables:** Quadruple-verified Faculty Appraisal Dossier with signed validation sheets.
12. **Operational SLA & Business Deadlines:** Parallel verification completed within **7 business days** of dossier receipt (`REQ-MOD3-16`).
13. **Reminders, Escalations & Lockouts:** Daily SLA reminders to verifiers; pending verifications escalate to Registrar.
14. **Exception Handling & Alternate Paths:** Any single verifier flagging a discrepancy pauses forward progression and triggers the Discrepancy Loop (`BP-M3-FAC-005`).
15. **Cross-Module Interactions & Handoffs:** Verified dossier advances to ECM Scheduling (`BP-M3-FAC-006`).
16. **Process Completion Criteria:** Formal verification sign-offs successfully logged by all four verification authorities.
17. **Audit & Compliance Requirements:** Individual verifier IDs, verified point adjustments, and validation timestamps permanently archived.
18. **Authoritative Source References:** Faculty ECM Brief, Section 3; [`REQ-MOD3-16`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-FAC-005
**Process Name:** Circular Discrepancy Flagging & Resubmission Review Loop

1. **Module / Operational Track:** Module III — Subsystem 3 (Dispute & Resubmission Governance).
2. **Business Purpose:** Provide a fair, tracked, circular discrepancy loop allowing verifiers to flag unsubstantiated claims and giving faculty members a structured deadline to rectify discrepancies or provide supplementary evidence.
3. **Operational Trigger:** A verifier (Dean, R&D, Placement, or HR) flags a discrepancy during parallel verification (`BP-M3-FAC-004`).
4. **Prerequisites & Entry Conditions:** Specific discrepancy remarks entered with identified deficit item.
5. **Primary Actors:** Flagging Verifier (Dean, R&D, Placement, or HR), Faculty Member (Resubmitter).
6. **Supporting Actors:** Office of the Registrar (Dispute Arbitrator).
7. **Business Inputs & Documentation:** Flagged discrepancy notice, original claimed item, specific verifier objection remarks, supplementary evidence files.
8. **Sequential Business Activities:**
   - Step 1: System halts forward progression to ECM and transitions dossier to `DISCREPANCY_FLAGGED` status.
   - Step 2: System generates and delivers formal **Discrepancy Notice** to the faculty member detailing the specific disputed claim and verifier remarks (`REQ-MOD3-16`).
   - Step 3: System initiates a tracked **resubmission deadline** (e.g., 5 working days).
   - Step 4: Faculty member reviews objection and takes action:
     - **Option A (Provide Evidence):** Uploads clarifying documentation or supplementary proof.
     - **Option B (Amend Claim):** Withdraws or reduces claimed points to match verified reality.
   - Step 5: Faculty member resubmits amended dossier.
   - Step 6: System routes amended dossier **strictly back to the specific verifier who flagged the discrepancy**.
   - Step 7: Verifier re-audits resubmission:
     - **Satisfied:** Clears discrepancy flag; dossier resumes parallel workflow.
     - **Unresolved:** If discrepancy persists after resubmission, verifier locks final verified points at their audited determination with formal explanatory memo.
9. **Decision Points & Evaluation Rules:** Verifier re-assessment: Does supplementary evidence resolve the disputed claim?
10. **Approval Points & Governance Gates:** Verifier sign-off clearing the discrepancy flag.
11. **Institutional Outputs & Deliverables:** Resubmitted dossier; discrepancy resolution memo.
12. **Operational SLA & Business Deadlines:** Faculty resubmission within **5 working days**; verifier re-audit within **48 hours** of resubmission.
13. **Reminders, Escalations & Lockouts:** Daily reminders to faculty member; failure to resubmit within SLA results in automatic forfeiture of the disputed points.
14. **Exception Handling & Alternate Paths:** Persistent irreconcilable disputes escalate to the Registrar for final administrative determination.
15. **Cross-Module Interactions & Handoffs:** Cleared dossiers return to Parallel Verification (`BP-M3-FAC-004`) to finalize approval for ECM Scheduling.
16. **Process Completion Criteria:** Discrepancy flag officially cleared by the flagging verifier or adjudicated by Registrar.
17. **Audit & Compliance Requirements:** Complete discrepancy thread, faculty response text, uploaded supplementary files, and resolution timestamps archived.
18. **Authoritative Source References:** Faculty ECM Brief, Section 3; [`REQ-MOD3-16`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M3-FAC-006
**Process Name:** Evaluation Committee Meeting (ECM) Scheduling & Digital Score Entry

1. **Module / Operational Track:** Module III — Subsystem 3 (Statutory Committee Evaluation).
2. **Business Purpose:** Orchestrate the monthly Evaluation Committee Meeting (ECM) scheduled by the Registrar and capture real-time individual digital scores from statutory committee members during live proceedings.
3. **Operational Trigger:** Clearance and verification of all candidate dossiers by all four verification units (`BP-M3-FAC-004`).
4. **Prerequisites & Entry Conditions:** Verified faculty appraisal dossiers in `VERIFIED_FOR_ECM` status.
5. **Primary Actors:** Registrar / Office of the Registrar (Scheduling Authority), Statutory ECM Committee Members.
6. **Supporting Actors:** Evaluated Faculty Member, HR Representative / Secretary.
7. **Business Inputs & Documentation:** Quadruple-verified appraisal dossiers, digital ECM Score Sheet (Enclosure 2), candidate teaching and research portfolios.
8. **Sequential Business Activities:**
   - Step 1: Office of the Registrar schedules the monthly Evaluation Committee Meeting (ECM) for verified candidates.
   - Step 2: System issues meeting notices and digital dossier packs to statutory ECM committee members.
   - Step 3: ECM convenes; candidate presents annual achievements, research progress, and pedagogical innovations.
   - Step 4: Each committee member accesses their assigned **Digital ECM Score Sheet (Enclosure 2)**.
   - Step 5: Committee members enter individual marks across statutory evaluation parameters (teaching effectiveness, research impact, academic leadership, institutional service).
   - Step 6: Committee members digitally sign and submit completed scorecards during the meeting.
9. **Decision Points & Evaluation Rules:** Committee assessment of candidate presentation, scholarly vigor, and institutional contribution.
10. **Approval Points & Governance Gates:** Digital submission of individual scorecards by statutory ECM members.
11. **Institutional Outputs & Deliverables:** Completed digital Enclosure 2 Score Sheets for each candidate from all participating committee members.
12. **Operational SLA & Business Deadlines:** ECM scheduled monthly; all individual score entries completed during the live meeting proceedings (`REQ-MOD3-17`).
13. **Reminders, Escalations & Lockouts:** Unsubmitted scorecards block matrix compilation; alert displayed on Registrar's console.
14. **Exception Handling & Alternate Paths:** Candidate unable to attend due to certified emergency rescheduled to following month's ECM.
15. **Cross-Module Interactions & Handoffs:** Individual digital scores feed directly into TNU Protocol Matrix Compilation (`BP-M3-FAC-007`).
16. **Process Completion Criteria:** ECM concluded and all individual digital score sheets submitted.
17. **Audit & Compliance Requirements:** Meeting minutes, committee attendance roster, individual scoring records, and submission timestamps archived.
18. **Authoritative Source References:** Faculty ECM Brief, Section 4; [`REQ-MOD3-17`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Enclosure 2 score sheet template is classified under `REQ-TBD-02`; statutory ECM committee quorum composition is classified under `REQ-TBD-04`.

---

### Process Identifier: BP-M3-FAC-007
**Process Name:** TNU Protocol Evaluation Matrix Compilation & Synthesis

1. **Module / Operational Track:** Module III — Subsystem 3 (Matrix Synthesis & Executive Preparation).
2. **Business Purpose:** Systematically synthesize ECM committee marks, previous compensation increment history, and statutory TNU Protocol parameters into an authoritative Evaluation Matrix (Enclosure 3) for executive compensation review.
3. **Operational Trigger:** Submission of all individual digital scorecards from the live ECM (`BP-M3-FAC-006`).
4. **Prerequisites & Entry Conditions:** Completed Enclosure 2 scorecards from all committee evaluators; historical increment records from Module I.
5. **Primary Actors:** System Synthesis Engine, HR Representative / Appraisal Desk.
6. **Supporting Actors:** Office of the Registrar, Senior Management.
7. **Business Inputs & Documentation:** Raw committee scores, candidate's complete 3-year compensation and increment history from Module I, statutory TNU Protocol parameter weightages (`REQ-TBD-04`), Enclosure 3 (Evaluation Matrix Template).
8. **Sequential Business Activities:**
   - Step 1: System computes weighted composite scores combining verified verification points and live ECM committee marks.
   - Step 2: System queries Module I and extracts the faculty member's historical salary increments, promotions, and effective dates over preceding review cycles.
   - Step 3: System compiles **Enclosure 3 (Evaluation Matrix)**, juxtaposing:
     - Candidate verified operational points across the four domains.
     - Live ECM committee marks and qualitative remarks.
     - Historical increment progression and current compensation level.
     - Computed composite score against statutory TNU Protocol benchmarks.
   - Step 4: HR Representative reviews and certifies the compiled matrix.
   - Step 5: Evaluation Matrix is formally routed to **Senior Management** for executive compensation determinations (`REQ-MOD3-18`).
9. **Decision Points & Evaluation Rules:** Verification of mathematical synthesis accuracy and complete historical increment integration.
10. **Approval Points & Governance Gates:** Certification sign-off executed by HR Representative.
11. **Institutional Outputs & Deliverables:** Comprehensive TNU Protocol Evaluation Matrix (Enclosure 3) submitted to Senior Management.
12. **Operational SLA & Business Deadlines:** Matrix compiled within **24 hours** following ECM conclusion (`REQ-MOD3-18`).
13. **Reminders, Escalations & Lockouts:** Pending matrices alert Chancellor's Secretariat.
14. **Exception Handling & Alternate Paths:** Mathematical discrepancies in score compilation trigger automated recalculation flag for HR review.
15. **Cross-Module Interactions & Handoffs:** Consumes historical increment data from Module I (`BP-XMOD-003`); submits matrix to Management Decision (`BP-M3-FAC-008`).
16. **Process Completion Criteria:** Enclosure 3 Matrix certified and successfully delivered to Senior Management queue.
17. **Audit & Compliance Requirements:** Calculation formulas, source score hashes, historical salary inputs, and compilation timestamps archived.
18. **Authoritative Source References:** Faculty ECM Brief, Section 5; [`REQ-MOD3-18`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Precise mathematical weightage formulas, scoring bands, and normalization algorithms of the TNU Protocol are classified under `REQ-TBD-04`.

---

### Process Identifier: BP-M3-FAC-008
**Process Name:** Management Decision & Salary Cycle Implementation Tracking

1. **Module / Operational Track:** Module III — Subsystem 3 (Executive Decision & Payroll Scheduling).
2. **Business Purpose:** Capture Senior Management's final decision on faculty compensation revisions and schedule approved adjustments for execution in the next applicable monthly salary cycle.
3. **Operational Trigger:** Receipt of the certified TNU Protocol Evaluation Matrix (`BP-M3-FAC-007`).
4. **Prerequisites & Entry Conditions:** Certified Enclosure 3 Matrix in `PENDING_MANAGEMENT_DECISION` status.
5. **Primary Actors:** Senior Management (Pro-Chancellor, Vice Chancellor, Executive Authority).
6. **Supporting Actors:** Head HR, Finance Controller.
7. **Business Inputs & Documentation:** Enclosure 3 Evaluation Matrix, university faculty compensation budget, academic promotion criteria.
8. **Sequential Business Activities:**
   - Step 1: Senior Management reviews the compiled Evaluation Matrix, examining candidate scores, past increments, and committee comments.
   - Step 2: Senior Management executes formal determination:
     - **Sanction Compensation Revision:** Approves specific percentage or fixed annual increment.
     - **Sanction Promotion:** Approves designation elevation (e.g., Assistant to Associate Professor) and salary band progression.
     - **Performance Maintenance / Deferral:** Defers increment with directives for performance improvement.
   - Step 3: Management digitally signs the approved compensation order.
   - Step 4: System registers the approved increment and schedules implementation **in the next applicable salary cycle** (`REQ-MOD3-19`).
   - Step 5: System executes automated handshake, injecting formal change request into Module I (`BP-XMOD-004`).
9. **Decision Points & Evaluation Rules:** Executive determination based on institutional academic excellence criteria and financial capacity.
10. **Approval Points & Governance Gates:** Apex Management Compensation Approval Gate (`REQ-MOD3-19`).
11. **Institutional Outputs & Deliverables:** Signed Executive Compensation Decision; scheduled salary cycle adjustment record; initiated Module I Change Request.
12. **Operational SLA & Business Deadlines:** Management determination executed within 5 business days; implementation scheduled strictly for the **next applicable monthly salary cycle** (`REQ-MOD3-19`).
13. **Reminders, Escalations & Lockouts:** Unscheduled salary adjustments alert Payroll Supervisor.
14. **Exception Handling & Alternate Paths:** Delayed management decisions past payroll cutoffs schedule arrears calculations in following cycle.
15. **Cross-Module Interactions & Handoffs:** Triggers Automated Letter Generation (`BP-M3-FAC-009`) and Module I Service Change (`BP-XMOD-004`).
16. **Process Completion Criteria:** Management order signed and implementation date scheduled in next salary cycle.
17. **Audit & Compliance Requirements:** Executive signatory ID, approved compensation values, effective date, and approval timestamp permanently preserved.
18. **Authoritative Source References:** Faculty ECM Brief, Section 6(a); [`REQ-MOD3-19`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Quantitative compensation slabs and increment percentages are classified under `REQ-TBD-05`.

---

### Process Identifier: BP-M3-FAC-009
**Process Name:** Automated Compensation Revision Letter Generation & Digital Dossier Archiving

1. **Module / Operational Track:** Module III — Subsystem 3 (Document Generation & Archival).
2. **Business Purpose:** Automatically generate the official institutional compensation revision letter, dispatch it to the faculty member and payroll desk, and permanently archive all appraisal artifacts in the Digital Personal File.
3. **Operational Trigger:** Senior Management authorization of faculty compensation revision (`BP-M3-FAC-008`).
4. **Prerequisites & Entry Conditions:** Formally approved compensation revision decision with scheduled salary cycle.
5. **Primary Actors:** System Document Generation Engine, HR Department (Records Desk).
6. **Supporting Actors:** Faculty Member (Recipient), Institutional Payroll Desk.
7. **Business Inputs & Documentation:** Approved compensation order, revised salary breakdown, standardized Faculty Increment Letter template (`REQ-DOC-05`).
8. **Sequential Business Activities:**
   - Step 1: System auto-generates official **Faculty Compensation Revision Letter** populated with faculty member name, employee ID, school/department, revised designation, updated basic/gross salary, effective date, and executive congratulations (`REQ-DOC-05`).
   - Step 2: Letter is digitally signed by Registrar / Head HR.
   - Step 3: Official digital letter is delivered to:
     - **Faculty Member:** Via secure digital portal delivery and email notification.
     - **HR / Payroll Desk:** For monthly payroll adjustment processing.
   - Step 4: System permanently archives the entire annual appraisal dossier (Self-Appraisal, evidence files, verifier validation sheets, ECM scorecards, TNU Matrix, Management order, and Revision Letter) into the faculty member's **Digital Personal File in Module I** (`BP-M1-003`).
9. **Decision Points & Evaluation Rules:** Verification of generated letter figures against approved Management decision memo.
10. **Approval Points & Governance Gates:** Automated generation; certified digital signature applied by authorized institutional signatory.
11. **Institutional Outputs & Deliverables:** Official Faculty Compensation Revision Letter (PDF); permanently archived appraisal record in Digital Personal File.
12. **Operational SLA & Business Deadlines:** Letter generated and delivered within **48 hours** of Management decision; archival executed synchronously (`REQ-MOD3-19`, `REQ-DOC-05`).
13. **Reminders, Escalations & Lockouts:** Delivery confirmation tracked; undelivered letters alert HR Helpdesk.
14. **Exception Handling & Alternate Paths:** Physical hard-copy letter printed and signed for faculty members requesting physical documentation.
15. **Cross-Module Interactions & Handoffs:** Concludes the annual performance lifecycle and archives permanent records in Module I (`BP-M1-003`).
16. **Process Completion Criteria:** Official letter delivered, confirmed received, and full dossier permanently archived.
17. **Audit & Compliance Requirements:** Letter PDF, cryptographic SHA-256 hash, delivery timestamps, and complete longitudinal dossier archived under WORM principles (`REQ-AUD-01`).
18. **Authoritative Source References:** Faculty ECM Brief, Section 6(b); [`REQ-MOD3-19`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-DOC-05`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---
*End of Document — Module III Business Processes.*
