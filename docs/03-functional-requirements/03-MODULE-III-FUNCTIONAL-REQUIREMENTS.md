# Module III — Performance Management Automation
## Functional Requirements Specification

**Document Identifier:** `DOC-03-FRD-MOD-03`  
**Phase:** Phase 3 — Functional Requirements Specification (Documentation-Only)  
**Location:** `docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`  
**Status:** Approved Functional Baseline  
**Authoritative Baseline:** [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) & [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)  
**Source Requirement:** `Requirement_Brief_Module_III_Performance_Management_Automation_System.pdf`  
**Date:** September 29, 2026  

---

## 1. Purpose

The purpose of Module III is to digitize, standardize, and automate the University's performance management and appraisal workflows, replacing manual, paper-, and email-based evaluation routing with a system-driven, auditable platform linked directly to the Central Employee Database (Module I).

In strict adherence to the authoritative requirements, Module III preserves **three completely independent performance management subsystems**. These workflows operate on distinct cadences, apply to specific employee segments, enforce unique statutory and institutional approval hierarchies, and must **never** be merged or conflated.

---

## 2. Scope

Module III encompasses three distinct, non-interchangeable performance management tracks:
1. **Subsystem 1: Group-D / Band I Monthly & Annual Appraisal System:**
   - Role-specific Key Performance Indicators (KPIs) and operational competencies.
   - Monthly evaluation by Heads of Department (HODs) with strict deadlines (7th) and grace periods (10th).
   - Automated reminders and midnight auto-lockout for non-submission.
   - Formal sign-off and approval by the Vice President – Administration.
   - Annual report collation at 12 months from Date of Joining (DOJ), weighted average scoring, mandatory probation completion gate, and Management compensation slabs.
2. **Subsystem 2: General Staff KRA/KPI Lifecycle:**
   - Onboarding goal setting within 30 days of Date of Joining (DOJ), verified and locked by HR and Management.
   - Quarterly review cycle (Q1, Q2, Q3, Q4) with 90-day triggers, 20-day pending reminders, 15-day employee submission window, 7-day supervisor verification, HR review, and Management comments.
   - Annual appraisal outcome and **direct handshake into Module I** (initializing salary, designation, and level change requests without re-entry).
3. **Subsystem 3: Faculty Annual Performance Appraisal (ECM Route):**
   - Statutory annual evaluation for Faculty who completed probation and $\ge 12$ months service since last appraisal.
   - Monthly eligibility batching and list routing to the Office of the Registrar by the 10th of every month.
   - 7 working days Self-Appraisal Form submission with evidentiary documentation.
   - Multi-departmental verification routing across School Dean, R&D Cell, Placement Cell, and HR Department, including discrepancy correction and resubmission tracking.
   - Monthly Evaluation Committee Meeting (ECM) scheduling by the Registrar.
   - Digital ECM Score Sheet entry during the meeting and compilation of the **TNU Protocol Evaluation Matrix** incorporating past increment history.
   - Management compensation decisions, implementation tracking in the next salary cycle, auto-generation of official outcome letters, and archiving in the Digital Personal File.

---

## 3. Actors and Roles

The following actors and roles are explicitly defined across the three performance subsystems:

| Actor / Role | Subsystem Reference | Documented Authority & Responsibilities | Source Reference | Classification |
|---|---|---|---|---|
| **Vice President – Administration** | Group-D (Subsystem 1) | Mandatory digital review, sign-off, and formal approval of monthly Group-D evaluation forms submitted by HODs before forms are finalized. | Module III, Group-D Section 2(b), 7(b) | `[A] EXPLICIT REQUIREMENT` |
| **Heads of Department (HOD) / Reporting Authority** | Group-D (Subsystem 1) | Completes and submits monthly digital evaluation forms for all reporting Group-D members by the 7th of every month. | Module III, Group-D Section 2(a, b), 7(a) | `[A] EXPLICIT REQUIREMENT` |
| **Office of the Registrar / Registrar** | Faculty ECM (Subsystem 3) | Receives eligible Faculty list by 10th of month; auto-issues and collects Self-Appraisal Forms; coordinates multi-departmental verification routing; schedules monthly ECMs; notifies Faculty of ECM schedule. | Module III, Faculty ECM Section 1(b), 2(a), 4(a, b), 8(b) | `[A] EXPLICIT REQUIREMENT` |
| **Senior Management / Management** | Subsystems 1, 2, 3 | Reviews Group-D Annual Reports and decides compensation revision based on slabs; verifies and locks KRA/KPI goals; reviews quarterly reviews (Q1-Q4); approves annual KRA/KPI appraisal outcomes; decides Faculty compensation revisions based on TNU Protocol ECM matrix. | Module III, Group-D 4(c), 5(a), 7(c); KRA Stage 1, 2, 3; Faculty ECM 5(c), 6(a), 8(f) | `[A] EXPLICIT REQUIREMENT` |
| **Head of HR / HR Representative / HR Team** | Subsystems 1, 2, 3 | Configures and versions Group-D evaluation forms; receives monthly collated reports; verifies KRA/KPI goals; reviews quarterly KRA submissions; triggers annual KRA appraisal to Management; feeds approved changes directly into Module I; generates monthly eligible Faculty list by 10th; conducts HR verification of Faculty self-appraisals; compiles ECM evaluation matrix (TNU Protocol); routes outcome letters to Payroll. | Module III, Group-D 1(a, b), 3(b); KRA Stage 1, 2, 3; Faculty ECM 1(b), 3(a), 5(a, c), 6(b), 8(a, e) | `[A] EXPLICIT REQUIREMENT` |
| **Reporting Authority / Supervisors** | General Staff KRA/KPI (Subsystem 2) | Collaborates with new joiners on KRA/KPI goal setting within 30 days of DOJ; verifies employee quarterly review submissions within 7 days and forwards to HR. | Module III, KRA Stage 1, Stage 2 | `[A] EXPLICIT REQUIREMENT` |
| **Evaluation Committee (ECM Members)** | Faculty ECM (Subsystem 3) | Statutory evaluation panel evaluating eligible Faculty at the monthly ECM; enters evaluation scores directly into the digital ECM Score Sheet during the meeting. | Module III, Faculty ECM Section 5(a), 8(d) | `[A] EXPLICIT REQUIREMENT` |
| **School Dean** | Faculty ECM (Subsystem 3) | Conducts academic verification of submitted Faculty Self-Appraisals (teaching delivery, curriculum, student feedback). | Module III, Faculty ECM Section 3(a), 8(c) | `[A] EXPLICIT REQUIREMENT` |
| **R&D Cell** | Faculty ECM (Subsystem 3) | Conducts research verification of Faculty Self-Appraisals (publications, indexing, research grants, citations, patents). | Module III, Faculty ECM Section 3(a), 8(c) | `[A] EXPLICIT REQUIREMENT` |
| **Placement Cell** | Faculty ECM (Subsystem 3) | Conducts institutional verification of student corporate placements, internship mentoring, and industry linkages submitted in Faculty Self-Appraisals. | Module III, Faculty ECM Section 3(a), 8(c) | `[A] EXPLICIT REQUIREMENT` |
| **Group-D / Band I Member** | Group-D (Subsystem 1) | Operational service personnel evaluated monthly by HOD; eligible for annual compensation review upon probation completion. | Module III, Group-D Section A | `[A] EXPLICIT REQUIREMENT` |
| **General Employee / Staff Member** | General Staff KRA/KPI (Subsystem 2) | Sets up KRAs/KPIs within 30 days of DOJ; submits quarterly reviews with supporting documents within 15 days of 90-day mark. | Module III, KRA Stage 1, Stage 2 | `[A] EXPLICIT REQUIREMENT` |
| **Faculty Member** | Faculty ECM (Subsystem 3) | Eligible faculty completing probation and $\ge 12$ months service; completes Self-Appraisal Form within 7 working days; attends ECM. | Module III, Faculty ECM Section 1, 2 | `[A] EXPLICIT REQUIREMENT` |
| **Payroll Team** | Subsystems 1, 3 | Receives auto-generated compensation adjustment notices to execute payroll adjustments in the next applicable salary cycle. | Module III, Faculty ECM Section 6(b) | `[A] EXPLICIT REQUIREMENT` |

---

## 4. Group-D / Band I Monthly and Annual Appraisal

*(Strictly Independent Subsystem 1)*

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                         GROUP-D MONTHLY & ANNUAL EVALUATION TIMELINE                             │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 1ST OF THE MONTH              │ 7TH OF THE MONTH               │ 8TH – 10TH OF THE MONTH         │
│ System auto-routes digital    │ Strict HOD submission due date.│ Automated 3-day grace period.   │
│ evaluation form to HOD.       │ Reminders sent prior to 7th.   │ Daily automated reminders sent. │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 10TH AT 23:59 (AUTO-LOCK)     │ APPROVAL GATE                  │ 1-YEAR DOJ ANNIVERSARY          │
│ System auto-locks unsubmitted │ Vice President – Administration│ Auto-triggers Annual Report;    │
│ forms; flags "Not Submitted"; │ digital sign-off required for  │ computes weighted averages;     │
│ visible to HR with reason.    │ finalization.                  │ checks probation completion.    │
├───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┤
│ COMPENSATION REVIEW: Management applies pre-defined slabs; outcome stored in Digital File.       │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 4.1 Monthly Evaluation
- **`MOD3-GD-REQ-01` [A] Digital Evaluation Form Repository:** The system shall maintain a digital Evaluation Form Repository, linked to the Central Employee Database (Module I), containing a standardized Evaluation Form per Group-D role (**Enclosure 1**).
- **`MOD3-GD-REQ-02` [A] Role-Specific KPIs & Competencies:** The Evaluation Form shall be configurable by the HR Team and shall capture role-specific Key Performance Indicators (KPIs) and operational competencies.
- **`MOD3-GD-REQ-03` [A] Form Versioning & Audit Trail:** The system shall allow the HR Team to update and version the form; each version shall be logged with an audit trail.
- **`MOD3-GD-REQ-04` [A] Monthly HOD Routing:** The system shall route a monthly Evaluation Form to the Head of Department (HOD) for each Group-D member reporting into their department (department and reporting hierarchy pulled dynamically from the Central Employee Database).

### 4.2 Submission Deadline
- **`MOD3-GD-REQ-05` [A] 7th of Month Due Date:** The system shall enforce a strict submission due date of the **7th of every month** for HODs.

### 4.3 Grace Period
- **`MOD3-GD-REQ-06` [A] 3-Day Automated Grace Period:** The system shall provide an automated grace period of **three (3) additional days** (up to the **10th of the month**).

### 4.4 Reminder Behaviour
- **`MOD3-GD-REQ-07` [A] Automated Notifications & Reminders:** The system shall send automated reminders to the HOD before the due date (prior to the 7th) and daily during the grace period (8th, 9th, 10th).

### 4.5 Auto-Lock
- **`MOD3-GD-REQ-08` [A] Hard Cutoff & Auto-Lockout:** If the form is not submitted within the grace period, the system shall **auto-lock** submission for that month at 23:59 on the 10th and flag the evaluation as **"Not Submitted"** for that Group-D member, with the record and failure reason visible to HR.

### 4.6 VP-Administration Approval
- **`MOD3-GD-REQ-09` [A] Mandatory VP Approval Gate:** The HOD shall complete and submit the form online; submission shall require formal digital sign-off / approval from the **Vice President – Administration** before it is treated as final.
- **`MOD3-GD-REQ-10` [A] Monthly Report Collation:** The system shall automatically collate all submitted and approved monthly Evaluation Forms into a Monthly Performance Report for each Group-D member (**Enclosure 2 Template**), made available to HR without manual compilation.

### 4.7 Annual Report
- **`MOD3-GD-REQ-11` [A] 1-Year Milestone Trigger:** The system shall automatically trigger generation of an Annual Report for each Group-D member upon completion of one (1) year of employment, and upon completion of every subsequent year of employment, based strictly on the Date of Joining (DOJ) held in the Central Employee Database.

### 4.8 Weighted Average
- **`MOD3-GD-REQ-12` [A] Weighted Parameter Calculation:** The Annual Report shall collate all Monthly Reports for the year and compute a weighted average for each performance parameter, as per weights configured by HR / Management.
- **`MOD3-GD-REQ-13` [A] Management Review Routing:** The compiled Annual Report shall be routed to Management for formal review.

### 4.9 Probation Gate
- **`MOD3-GD-REQ-14` [A] Mandatory Probation Verification:** The system shall check the member's probation status (from the Central Employee Database) and **shall not activate the compensation-change workflow unless the probation period is marked as mandatorily completed**.

### 4.10 Compensation Revision
- **`MOD3-GD-REQ-15` [A] Management Compensation Slabs:** Based on the Annual Report, the system shall support a Management decision / review on compensation change, applying pre-defined compensation slabs configured by Management against the weighted performance score.
- **`MOD3-GD-REQ-16` [A] Digital Employee File Archiving:** Every Evaluation Form, Monthly Report, and Annual Report shall be automatically stored against the respective Group-D member's digital employee file, serving as an immutable reference for rewards, compensation changes, transfers, or reprimands.

---

## 5. General Staff KRA/KPI Lifecycle

*(Strictly Independent Subsystem 2)*

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 KRA/KPI LIFECYCLE (3 STAGES)                                     │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ STAGE 1: ONBOARDING GOAL SETTING                                                                 │
│ • Trigger: New Employee Joining (from Central DB) ──► Intimation to Employee & Supervisor        │
│ • SLA: Goal setting completed within 30 days of Date of Joining (DOJ)                            │
│ • Gate: Formal verification & locking by HR and Management                                       │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ STAGE 2: QUARTERLY REVIEW CYCLE (Q1 ➔ Q2 ➔ Q3 ➔ Q4)                                              │
│ • 90 Days from DOJ: System intimates Q1 submission | +20 Days: Reminder if pending               │
│ • Employee Submission: Within 15 days of 90-day mark with supporting evidence                   │
│ • Supervisor Verification: Within 7 days ──► Forwarded to HR                                     │
│ • HR Review: Records observations / recommendations                                              │
│ • Management Review: Records executive comment / recommendation                                  │
│ • Cycle repeats identically across Q2, Q3, and Q4                                                │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ STAGE 3: ANNUAL APPRAISAL & MODULE I HANDSHAKE                                                   │
│ • Post-Q4: HR triggers formal appraisal request to Management                                    │
│ • Management records final appraisal recommendation                                              │
│ • Direct Handshake: HR initializes change (salary, designation, level) directly in Module I      │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 5.1 Goal Setting
- **`MOD3-KRA-REQ-01` [A] Onboarding Trigger:** On new employee joining, the system shall generate an automated intimation to the employee and their Reporting Authority to establish Key Result Areas (KRAs) and Key Performance Indicators (KPIs).

### 5.2 30-Day Requirement
- **`MOD3-KRA-REQ-02` [A] 30-Day Completion SLA:** Goal setting (KRAs/KPIs) must be completed within thirty (30) days of the employee's Date of Joining (DOJ).
- **`MOD3-KRA-REQ-03` [A] HR & Management Verification Lock:** Established goals shall undergo formal verification by HR and Management before being locked in the system.

### 5.3 Quarterly Reviews
- **`MOD3-KRA-REQ-04` [A] 4-Quarter Evaluation Cycle:** The system shall automate a four-quarter review cycle (Q1, Q2, Q3, Q4) tracking performance over the 12-month period from DOJ.

### 5.4 Q1
- **`MOD3-KRA-REQ-05` [A] 90-Day Intimation & 20-Day Reminder:** The system shall issue an intimation at ninety (90) days from DOJ to submit the 1st quarter review, with an automated reminder triggered after twenty (20) days if submission is pending.

### 5.5 Q2, 5.6 Q3, 5.7 Q4
- **`MOD3-KRA-REQ-06` [A] Identical Recurrent Flow:** The review workflow shall repeat identically for the 2nd, 3rd, and 4th quarters, each anchored to their respective quarterly anniversary from DOJ.

### 5.8 Employee Submission
- **`MOD3-KRA-REQ-07` [A] 15-Day Submission Window:** The employee shall submit their self-review along with supporting documents within fifteen (15) days of completing the 90-day mark.

### 5.9 Reporting Authority Verification
- **`MOD3-KRA-REQ-08` [A] 7-Day Supervisor Verification SLA:** The Reporting Authority shall verify the employee's submission and forward it to HR within seven (7) days of receipt.

### 5.10 HR Review
- **`MOD3-KRA-REQ-09` [A] HR Observations:** HR shall review the verified submission and record formal change requests, recommendations, or operational observations.

### 5.11 Management Review
- **`MOD3-KRA-REQ-10` [A] Executive Sign-Off:** Submissions shall be routed to Management for review; Management shall record executive comments and recommendations.

### 5.12 Annual Outcome
- **`MOD3-KRA-REQ-11` [A] Annual Appraisal Trigger:** After completion of all four (4) quarters, HR shall trigger the consolidated appraisal request to Management.
- **`MOD3-KRA-REQ-12` [A] Final Management Recommendation:** Management shall record final appraisal recommendations (increments, promotions, band adjustments).

### 5.13 Module I Integration
- **`MOD3-KRA-REQ-13` [A] Direct Handshake into Module I:** HR shall initialize the resulting service change requirement (e.g., increment, designation, level) **directly in the Module I – HR Change Management System, closing the operational loop without duplicate data re-entry**.
- **`MOD3-KRA-REQ-14` [A] Turnaround Time (TAT) Analytics:** The system shall track timestamped audit trails and TAT metrics at every stage (30-day goal-setting SLA, 90-day + 15-day quarterly SLA, 20-day reminder trigger, 7-day supervisor SLA).

---

## 6. Faculty ECM Workflow

*(Strictly Independent Subsystem 3)*

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               FACULTY ANNUAL ECM WORKFLOW                                        │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. Eligibility Scan: Monthly 10th check (Probation Complete + >= 12 Months Service)              │
│ 2. HR routes Eligible List to Office of the Registrar by the 10th of every month                 │
│ 3. Registrar issues Self-Appraisal Form; Faculty submits within 7 working days with evidence     │
│ 4. Parallel Verification: School Dean, R&D Cell, Placement Cell, HR Dept (Discrepancy Loop)     │
│ 5. Registrar schedules monthly ECM for verified candidates; notifies Faculty                     │
│ 6. Evaluation Committee scores via Digital ECM Score Sheet during meeting                        │
│ 7. HR compiles Evaluation Matrix (TNU Protocol parameters + past increment history) ──► Mgmt    │
│ 8. Management decides compensation revision                                                      │
│ 9. Execution: Scheduled in next salary cycle; auto-generates letter to Faculty & HR/Payroll      │
│ 10. Archiving: Stored permanently in Faculty Digital Personal File                               │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 6.1 Eligibility
- **`MOD3-FAC-REQ-01` [A] Strict Eligibility Criteria:** The system shall automatically identify Faculty members who have:
  1. Mandatorily completed their probation period, AND
  2. Completed at least twelve (12) months of employment since their last appraisal (or DOJ), using master data from the Central Employee Database (Module I).

### 6.2 Eligibility List
- **`MOD3-FAC-REQ-02` [A] Automated List Generation:** The system shall automatically generate the eligible Faculty list on a monthly basis.

### 6.3 Registrar Routing
- **`MOD3-FAC-REQ-03` [A] 10th of Month Routing to Registrar:** The system shall route the eligible Faculty list from HR to the Office of the Registrar by the **10th of every month**, with an automated reminder if routing is delayed.

### 6.4 Self-Appraisal
- **`MOD3-FAC-REQ-04` [A] Auto-Issuance of Self-Appraisal:** The system shall auto-issue the standardized Self-Appraisal Form (**Enclosure 1**) to each eligible Faculty member.
- **`MOD3-FAC-REQ-05` [A] 7 Working Days Submission SLA:** The Faculty member shall submit the completed Self-Appraisal Form within **seven (7) working days** of receipt; the system shall track this timeline and dispatch reminders as the deadline approaches.

### 6.5 Evidence Submission
- **`MOD3-FAC-REQ-06` [A] Evidentiary Attachment Support:** The system shall mandate the upload of supporting documentation (research publications, teaching portfolios, patent certificates, student mentoring logs) alongside the Self-Appraisal Form.

### 6.6 Dean Verification
- **`MOD3-FAC-REQ-07` [A] School Dean Review:** Submitted forms shall route to the concerned School Dean for verification of teaching load, curriculum delivery, and academic contributions.

### 6.7 R&D Verification
- **`MOD3-FAC-REQ-08` [A] Research & Development Cell Review:** Submitted forms shall route to the R&D Cell for verification of research papers, indexing (Scopus/WoS), funded projects, and patents.

### 6.8 Placement Verification
- **`MOD3-FAC-REQ-09` [A] Corporate Relations & Placement Review:** Submitted forms shall route to the Placement Cell for verification of student placement mentoring and corporate linkages.

### 6.9 HR Verification
- **`MOD3-FAC-REQ-10` [A] HR Compliance Check:** Submitted forms shall route to the HR Department for administrative verification (leaves, compliance, institutional conduct).

### 6.10 Discrepancy and Resubmission
- **`MOD3-FAC-REQ-11` [A] Discrepancy Correction Loop:** Where any verifying unit identifies a discrepancy, the system shall return the form to the concerned Faculty member for correction / updated resubmission, and shall monitor the resubmission loop until verification is complete.

### 6.11 ECM Scheduling
- **`MOD3-FAC-REQ-12` [A] Monthly ECM Scheduling:** The system shall enable the Office of the Registrar to schedule the monthly Evaluation Committee Meeting (ECM) for all verified Faculty members.
- **`MOD3-FAC-REQ-13` [A] Candidate Notification:** The system shall notify each concerned Faculty member of their confirmed ECM date, time, and session details.

### 6.12 Digital Score Sheet
- **`MOD3-FAC-REQ-14` [A] Committee Scoring Sheet:** The system shall provide a digital ECM Score Sheet (**Enclosure 2**) for the Evaluation Committee to record scores during the meeting, submitted directly to the HR Department.

### 6.13 Evaluation Matrix
- **`MOD3-FAC-REQ-15` [A] TNU Protocol Matrix Compilation:** The system shall compile an Evaluation Matrix based on configured **TNU Protocol parameters** combined with the Faculty member's previous increment details held in the system (**Enclosure 3 Template**).
- **`MOD3-FAC-REQ-16` [A] Management Submission:** The compiled evaluation matrix shall be routed by the system to Management, through the HR Representative, for recommendation on compensation change.

### 6.14 Management Decision
- **`MOD3-FAC-REQ-17` [A] Multi-Faceted Outcome Support:** The ECM result and Management decision shall form a system-linked basis for:
  - Confirmation of employment
  - Extension of probation (where the minimum prescribed score is not achieved)
  - Rewards and recognition
  - Compensation revision
  - Additional institutional responsibilities
  - Performance Improvement Plan (PIP)
  - Formal reprimand

### 6.15 Salary Cycle
- **`MOD3-FAC-REQ-18` [A] Next Salary Cycle Tracking:** The system shall capture Management's recommendation on compensation and shall track its implementation in the next applicable salary cycle / due month.

### 6.16 Auto-Letter
- **`MOD3-FAC-REQ-19` [A] Auto-Generated Outcome Notice:** The system shall auto-generate the official outcome letter to the concerned Faculty member and route it directly to HR / Payroll for issuance and payroll execution.

### 6.17 Digital Personal File
- **`MOD3-FAC-REQ-20` [A] Permanent Personal File Integration:** The appraisal / ECM result, evaluation matrix, score sheets, and auto-generated letters shall be automatically archived against the concerned Faculty member's digital personal file.

---

## 7. Notifications and SLA Behaviour

- **`MOD3-NTF-REQ-01` [B] Group-D Notification Cadence:** Reminders sent prior to 7th; daily reminders on 8th, 9th, 10th; lockout notification on 10th midnight; notification to VP-Administration upon form submission.
- **`MOD3-NTF-REQ-02` [B] KRA/KPI Notification Cadence:** 30-day onboarding countdown alerts; 90-day quarterly review intimation; 20-day pending alert; 7-day supervisor verification countdown.
- **`MOD3-NTF-REQ-03` [B] Faculty ECM Notification Cadence:** Monthly 10th Registrar alert; daily reminders during 7-day self-appraisal window; discrepancy alerts; confirmed ECM schedule notice; outcome letter notification.

---

## 8. Reporting Requirements

The system shall generate the following mandatory reports:
1. **Group-D Reports:**
   - *Monthly Performance Report* (per member and collated department-wide)
   - *Annual Performance Report* (weighted score calculations)
   - *"Not Submitted" Audit Report* (HOD non-submission tracking)
2. **KRA/KPI Reports:**
   - *New-Joiner KRA/KPI Setup Status Report* (compliance against 30-day SLA)
   - *HR + Management Verification TAT Report*
   - *Quarter-Wise Submission Status Report* (Submitted / Pending / Overdue by department and employee)
3. **Faculty ECM Reports:**
   - *Monthly Eligible Faculty List* (generated by 10th of every month)
   - *ECM Score Sheet Compilation Report*
   - *Compiled Evaluation Matrix Report* (TNU Protocol parameters per appraisal cycle)

---

## 9. Functional Requirement Catalogue

| Requirement ID | Section | Requirement Title | Classification | Source Brief Ref |
|---|---|---|---|---|
| `MOD3-GD-REQ-01` | 4.1 | Digital Form Repository (Enclosure 1) | `[A] EXPLICIT` | Group-D Section 1 |
| `MOD3-GD-REQ-02` | 4.1 | Role-Specific KPIs & Competencies | `[A] EXPLICIT` | Group-D Section 1(a) |
| `MOD3-GD-REQ-03` | 4.1 | Form Versioning with Audit Trail | `[A] EXPLICIT` | Group-D Section 1(b) |
| `MOD3-GD-REQ-04` | 4.1 | Monthly HOD Form Routing from Central DB | `[A] EXPLICIT` | Group-D Section 2(a) |
| `MOD3-GD-REQ-05` | 4.2 | 7th of Month Submission Due Date | `[A] EXPLICIT` | Group-D Section 2(c) |
| `MOD3-GD-REQ-06` | 4.3 | 3-Day Automated Grace Period (Up to 10th) | `[A] EXPLICIT` | Group-D Section 2(c) |
| `MOD3-GD-REQ-07` | 4.4 | Pre-Due Date & Grace Period Reminders | `[A] EXPLICIT` | Group-D Section 2(d) |
| `MOD3-GD-REQ-08` | 4.5 | Auto-Lockout & "Not Submitted" Flag | `[A] EXPLICIT` | Group-D Section 2(e) |
| `MOD3-GD-REQ-09` | 4.6 | VP – Administration Approval Sign-Off | `[A] EXPLICIT` | Group-D Section 2(b) |
| `MOD3-GD-REQ-10` | 4.6 | Monthly Report Collation (Enclosure 2) | `[A] EXPLICIT` | Group-D Section 3 |
| `MOD3-GD-REQ-11` | 4.7 | Annual Report 1-Year Milestone Trigger | `[A] EXPLICIT` | Group-D Section 4(a) |
| `MOD3-GD-REQ-12` | 4.8 | Weighted Average Score Computation | `[A] EXPLICIT` | Group-D Section 4(b) |
| `MOD3-GD-REQ-13` | 4.8 | Annual Report Routing to Management | `[A] EXPLICIT` | Group-D Section 4(c) |
| `MOD3-GD-REQ-14` | 4.9 | Mandatory Probation Verification Gate | `[A] EXPLICIT` | Group-D Section 5(b) |
| `MOD3-GD-REQ-15` | 4.10| Management Pre-Defined Compensation Slabs | `[A] EXPLICIT` | Group-D Section 5(a) |
| `MOD3-GD-REQ-16` | 4.10| Digital Employee File Integration | `[A] EXPLICIT` | Group-D Section 6(a, b) |
| `MOD3-KRA-REQ-01` | 5.1 | Onboarding KRA/KPI Intimation Trigger | `[A] EXPLICIT` | KRA Stage 1 |
| `MOD3-KRA-REQ-02` | 5.2 | 30-Day Goal Setting SLA from DOJ | `[A] EXPLICIT` | KRA Stage 1 |
| `MOD3-KRA-REQ-03` | 5.2 | HR & Management Verification Lock | `[A] EXPLICIT` | KRA Stage 1 |
| `MOD3-KRA-REQ-04` | 5.3 | Four-Quarter Review Lifecycle | `[A] EXPLICIT` | KRA Stage 2 |
| `MOD3-KRA-REQ-05` | 5.4 | Q1 90-Day Intimation & 20-Day Reminder | `[A] EXPLICIT` | KRA Stage 2 |
| `MOD3-KRA-REQ-06` | 5.5 | Recurrent Q2, Q3, Q4 Quarterly Cycles | `[A] EXPLICIT` | KRA Stage 2 |
| `MOD3-KRA-REQ-07` | 5.8 | 15-Day Employee Submission Window | `[A] EXPLICIT` | KRA Stage 2 |
| `MOD3-KRA-REQ-08` | 5.9 | 7-Day Supervisor Verification SLA | `[A] EXPLICIT` | KRA Stage 2 |
| `MOD3-KRA-REQ-09` | 5.10| HR Review & Observation Logging | `[A] EXPLICIT` | KRA Stage 2 |
| `MOD3-KRA-REQ-10` | 5.11| Management Review & Executive Comments | `[A] EXPLICIT` | KRA Stage 2 |
| `MOD3-KRA-REQ-11` | 5.12| Annual Appraisal Request Trigger | `[A] EXPLICIT` | KRA Stage 3 |
| `MOD3-KRA-REQ-12` | 5.12| Final Management Appraisal Decision | `[A] EXPLICIT` | KRA Stage 3 |
| `MOD3-KRA-REQ-13` | 5.13| Direct Handshake into Module I System | `[A] EXPLICIT` | KRA Stage 3 |
| `MOD3-KRA-REQ-14` | 5.13| Audit Trail & TAT Analytics Engine | `[A] EXPLICIT` | KRA Stage 3 & Reports |
| `MOD3-FAC-REQ-01` | 6.1 | Strict Eligibility (Probation + $\ge 12$ mo) | `[A] EXPLICIT` | Faculty ECM Section 1(a) |
| `MOD3-FAC-REQ-02` | 6.2 | Automated Eligible List Generation | `[A] EXPLICIT` | Faculty ECM Section 1(b) |
| `MOD3-FAC-REQ-03` | 6.3 | 10th of Month List Routing to Registrar | `[A] EXPLICIT` | Faculty ECM Section 1(b) |
| `MOD3-FAC-REQ-04` | 6.4 | Auto-Issuance of Self-Appraisal Form | `[A] EXPLICIT` | Faculty ECM Section 2(a) |
| `MOD3-FAC-REQ-05` | 6.4 | 7 Working Days Submission SLA | `[A] EXPLICIT` | Faculty ECM Section 2(b) |
| `MOD3-FAC-REQ-06` | 6.5 | Mandatory Evidence Document Upload | `[A] EXPLICIT` | Faculty ECM Section 2(b) |
| `MOD3-FAC-REQ-07` | 6.6 | School Dean Academic Verification | `[A] EXPLICIT` | Faculty ECM Section 3(a) |
| `MOD3-FAC-REQ-08` | 6.7 | R&D Cell Research Verification | `[A] EXPLICIT` | Faculty ECM Section 3(a) |
| `MOD3-FAC-REQ-09` | 6.8 | Placement Cell Linkages Verification | `[A] EXPLICIT` | Faculty ECM Section 3(a) |
| `MOD3-FAC-REQ-10` | 6.9 | HR Compliance Verification | `[A] EXPLICIT` | Faculty ECM Section 3(a) |
| `MOD3-FAC-REQ-11` | 6.10| Discrepancy Correction & Resubmission Loop | `[A] EXPLICIT` | Faculty ECM Section 3(b) |
| `MOD3-FAC-REQ-12` | 6.11| Monthly ECM Registrar Scheduling | `[A] EXPLICIT` | Faculty ECM Section 4(a) |
| `MOD3-FAC-REQ-13` | 6.11| Candidate Schedule Notification | `[A] EXPLICIT` | Faculty ECM Section 4(b) |
| `MOD3-FAC-REQ-14` | 6.12| Digital ECM Score Sheet (Enclosure 2) | `[A] EXPLICIT` | Faculty ECM Section 5(a) |
| `MOD3-FAC-REQ-15` | 6.13| TNU Protocol Evaluation Matrix (Enclosure 3) | `[A] EXPLICIT` | Faculty ECM Section 5(b) |
| `MOD3-FAC-REQ-16` | 6.13| Matrix Routing to Management via HR | `[A] EXPLICIT` | Faculty ECM Section 5(c) |
| `MOD3-FAC-REQ-17` | 6.14| Multi-Faceted Outcome Support (PIP, Slabs) | `[A] EXPLICIT` | Faculty ECM Section 7(a) |
| `MOD3-FAC-REQ-18` | 6.15| Next Salary Cycle Execution Tracking | `[A] EXPLICIT` | Faculty ECM Section 6(a) |
| `MOD3-FAC-REQ-19` | 6.16| Auto-Generated Outcome Notice to Payroll | `[A] EXPLICIT` | Faculty ECM Section 6(b) |
| `MOD3-FAC-REQ-20` | 6.17| Permanent Personal File Integration | `[A] EXPLICIT` | Faculty ECM Section 7(b) |

---

## 10. Requirement Traceability

| Functional Requirement ID | Source Document Reference | Base Traceability ID (`PROJECT_REQUIREMENTS_ANALYSIS.md`) | Downstream Phase Dependency |
|---|---|---|---|
| `MOD3-GD-REQ-01` to `16` | Module III PDF, Page 1-2, Group-D Sections 1-8 | `MOD3-GD-EVAL-01`, `MOD3-GD-APP-01`, `MOD3-GD-ANN-01` | Phase 5 (Workflows: Group-D 7th/10th scheduler, VP-Admin gate) |
| `MOD3-KRA-REQ-01` to `14` | Module III PDF, Page 3, KRA Sections 1-3 | `MOD3-KRA-SET-01`, `MOD3-KRA-QTR-01`, `MOD3-KRA-INT-01` | Phase 5 (Workflows: KRA/KPI Q1-Q4 engine & Mod I direct handshake) |
| `MOD3-FAC-REQ-01` to `20` | Module III PDF, Page 4-5, Faculty Sections 1-9 | `MOD3-FAC-ELG-01`, `MOD3-FAC-VER-01`, `MOD3-FAC-ECM-01`, `MOD3-FAC-SAL-01` | Phase 5 (Workflows: Faculty 10th scanner, parallel review, ECM matrix) |

---

## 11. Open Questions / TBD

The following items are officially classified as **`[E] TBD / OPEN DECISION`** requiring confirmation from University leadership:

1. **`MOD3-TBD-01` Group-D Pre-Defined Compensation Slabs:** What exact increment formulas, salary band steps, or percentage slabs are configured by Management for Group-D ratings?
2. **`MOD3-TBD-02` TNU Protocol Exact Mathematical Scoring Model:** What are the exact category weights (Teaching vs. Research vs. Administration), maximum marks, and minimum benchmark scores defined in the university's "TNU Protocol"?
3. **`MOD3-TBD-03` Staff Track Boundary Definition:** Which exact staff designations follow the KRA/KPI quarterly cycle vs. Group-D vs. ECM? Do Technical Assistants and Teaching Associates follow KRA/KPI or ECM?
4. **`MOD3-TBD-04` Physical Template Files (Enclosures 1, 2, 3):** Official Word/Excel templates for Group-D Evaluation Forms, KRA Goal Sheets, Faculty Self-Appraisal Forms, and ECM Score Sheets must be obtained from HR.

---
*End of Module III Functional Requirements Specification.*
