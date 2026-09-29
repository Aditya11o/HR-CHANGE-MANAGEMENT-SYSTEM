# Business Process SLA and Escalation Framework
## Authoritative Institutional Timelines, Submission Windows, Grace Periods, and Escalation Matrix

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/02-business-process/07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md` |
| **System Phase** | Phase 2 — Business Process Documentation |
| **Project** | University HR Change Management & Automation System |
| **Status** | `PROPOSED BASELINE` |
| **Scope** | Operational Service Level Agreements (SLAs), Business Cutoffs, and Escalation Rules |
| **Authoritative Sources** | Module I, Module II, and Module III Official Requirement Briefs; `PROJECT_REQUIREMENTS_ANALYSIS.md`; `docs/01-requirements/`; `docs/03-functional-requirements/` |
| **Technology Independence** | Strictly Technology-Neutral — Distinguishes Business Governance Deadlines from Technical Schedulers |

---

## 1. Executive Summary & SLA Governance Model

In an enterprise academic institution, operational efficiency, regulatory compliance, and employee trust depend upon predictable, transparent timelines. The University HR Change Management & Automation System enforces rigorous **Service Level Agreements (SLAs)** across all three modules to ensure administrative accountability, eliminate processing backlogs, and prevent academic disruptions.

### Core Governance Principles
1. **Source-Supported Fidelity:** Every timeline, calendar cutoff, grace period, and submission window documented herein is directly anchored in the official requirement briefs. No arbitrary or invented deadlines have been introduced.
2. **Business Deadline vs. Technical Execution Separation:** In accordance with [`01-BUSINESS-PROCESS-FRAMEWORK.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-FRAMEWORK.md), an institutional **business deadline** (e.g., "7th of the month due date", "10th of the month lockout") represents an administrative policy rule governing human stakeholders. The underlying **technical scheduler** (e.g., cron worker executing at 23:59) is an architecture mechanism that automates enforcement without altering the business rule.
3. **Escalation & Accountability:** Missed deadlines or stalled approval stages trigger structured notifications, reminders, and executive escalations to prevent administrative deadlock.

---

## 2. Business SLA Master Register by Domain

### Section A: Module I — Central Master & Service Changes

| Process Identifier & Name | Operational Trigger | Responsible Actor | Business Target SLA | Grace Period | Reminders & Escalation Path | Lockout / Final Action | Source Reference |
|---|---|---|---|---|---|---|---|
| **`BP-M1-004`** Employee Service Change Initiation | Employee or HR initiates 1 of 10 service change formats | Initiator (HR Operations / Employee) | Immediate formulation & submission | None | Submission reminders if drafted but unsubmitted after 5 days | Unsubmitted drafts auto-archived after 30 days | Mod I Brief Structure 3 |
| **`BP-M1-005`** Level-1 HR Verification | Service change request submitted | HR Reviewer / Head HR | Within 48–72 hours of submission | None | Alert to Head HR after 72 hours; daily reminder thereafter | Pending request escalated to Registrar if inactive > 7 days | Mod I Brief Structure 4 & 5 |
| **`BP-M1-006`** Level-2 Senior Management Approval | Level-1 HR recommendation signed | Senior Management / Registrar / VC | Within 5 working days (prior to payroll cutoff) | None | Alert to Management Secretariat on Day 4; high-priority notification on Day 7 | Request placed on executive agenda; no automatic bypass permitted | Mod I Brief Structure 4 & 5 |
| **`BP-M1-007`** Effective-Date Activation | Arrival of scheduled `effective_date` | System Master Authority / HR Ops | Operational at 00:00 midnight of effective date | None | System alert if effective-date job encounters exception | Master record activated; immutable audit entry committed | Mod I Brief Structure 3 & 4 |
| **`BP-M1-002`** Org Chart Hierarchy Reflection | Effective-date activation of structural change | System Master Authority | Immediate upon effective-date activation | None | Audit alert if unlinked reporting nodes are detected | Real-time organizational structure re-rendered | Mod I Brief Structure 2 |
| **`BP-M1-003`** Digital Dossier Ingestion | Candidate Day-1 onboarding verification | HR Onboarding Executive | Within 24 hours of physical joining report | 48 hours for document clarification | Reminder to HR Onboarding if dossier is incomplete after 24 hours | Dossier locked upon verification; flagged for compliance | Mod I Brief Background |
| **`BP-M1-009`** ERP Payroll Synchronization | Effective-date activation of salary/grade change | System Integration / HR Ops | Transmitted prior to monthly payroll cutoff | None | Real-time administrative exception alert to HR if ERP unreachable | Outbox event committed; pending transmission flagged | Mod I Brief Background |

---

### Section B: Module II — Academic Recruitment & SCM Selection

| Process Identifier & Name | Operational Trigger | Responsible Actor | Business Target SLA | Grace Period | Reminders & Escalation Path | Lockout / Final Action | Source Reference |
|---|---|---|---|---|---|---|---|
| **`BP-M2-ACAD-001`** Academic Planning Initiation | Calendar milestone: 4 months prior to semester | Academic Council / HR Head | At least 4 months prior to semester commencement | None | Planning countdown alerts dispatched to Deans and Leadership | Planning cycle officially opened for university schools | Mod II Brief Section 1; `REQ-MOD2-02` |
| **`BP-M2-ACAD-002`** Dean Manpower Requisition Submission | Academic planning initiation notice | School Deans | Within 15 calendar days of trigger | None | Reminder on Day 10; urgent escalation alert to Pro-Chancellor on Day 16 | Requisition portal closes; late submissions require VC approval | Mod II Brief Section 1; `REQ-MOD2-04` |
| **`BP-M2-ACAD-003`** HR Academic Requisition Vetting | Receipt of Dean academic requisitions | HR Department | 3-month vetting window | None | Milestone alerts at 30, 60, and 75 days to Head HR and Registrar | Vetting report closed; passed to consolidation | Mod II Brief Section 1; `REQ-MOD2-05` |
| **`BP-M2-ACAD-004`** Academic Requisition Consolidation | Conclusion of HR 3-month vetting window | HR Department | Within 15 calendar days of vetting closure | None | Reminder on Day 10 to Head HR; escalation on Day 16 | Consolidated Master Plan finalized for Pro-Chancellor | Mod II Brief Section 1; `REQ-MOD2-06` |
| **`BP-M2-ACAD-005`** Pro-Chancellor Approval Communication | Submission of Consolidated Academic Plan | Pro-Chancellor / Senior Management | Within 7 calendar days of submission | None | Daily reminder to Secretariat from Day 5; high-priority alert on Day 8 | Formal approval order issued authorizing advertisement | Mod II Brief Section 1; `REQ-MOD2-07` |
| **`BP-M2-ACAD-006`** Academic Advertisement & Sourcing Launch | Pro-Chancellor approval order issued | Recruitment Team / HR | Within 7 calendar days of approval | None | Daily alert to Recruitment Lead if ads are not live by Day 5 | Public advertisement and portal opening completed | Mod II Brief Section 1; `REQ-MOD2-11` |
| **`BP-M2-ACAD-007`** Application Screening & Longlisting | Public advertisement publication | Recruiter / Dean Screening Panel | Ongoing rolling screening; finalized within 15 days of ad close | 3 days | Alert to Dean if candidate dossiers remain unreviewed after 10 days | Screened applicants locked into SCM pool or rejection register | Mod II Brief Section 2 |
| **`BP-M2-ACAD-008`** SCM Interview Panel Scheduling | Shortlist approved by Dean & HR | Recruitment Coordinator | Convened with at least 7 days advance notice to experts | None | Daily confirmation tracking for External Subject Experts | Quorum confirmed; unconfirmed panels rescheduled | Mod II Brief Section 2; `REQ-MOD2-13` |
| **`BP-M2-ACAD-009`** SCM Digital Scoring & Matrix Evaluation | SCM interview proceedings | Statutory Selection Committee & External Expert | Real-time digital scoring during interview session | None | Committee Chair ensures all scorecards submitted before adjournment | SCM Selection Matrix sealed and signed digitally | Mod II Brief Section 2; `REQ-MOD2-14` |
| **`BP-M2-ACAD-010`** Management Selection Approval | SCM Selection Matrix compiled | Management / Pro-Chancellor | Within 5 working days of SCM conclusion | None | Alert to Management Secretariat on Day 4 | Formal appointment approval minute signed | Mod II Brief Section 2 |
| **`BP-M2-ACAD-011`** Academic LOI Issuance & Acceptance | Selection approval minute signed | Recruitment Team / Candidate | LOI issued within 48 hours; Candidate response within 7–14 days | 3 days upon written request | Reminders on Day 3 and Day 1 before offer expiration | Unaccepted offer expires; position offered to waitlisted candidate | Mod II Brief Section 2; `REQ-MOD2-17` |
| **`BP-M2-ACAD-012`** Yet-to-Join Tracking & Recruitment Close | Candidate accepts LOI | Recruitment Coordinator / Candidate | Concluded at least 1 month prior to semester commencement | None | Weekly engagement check-ins; high-priority alert if unfilled 45 days prior | Handshake `BP-XMOD-001` executed on Day 1 of joining | Mod II Brief Section 1 & 2; `REQ-MOD2-08` |

---

### Section C: Module II — Non-Academic Recruitment & Three-Round Selection

| Process Identifier & Name | Operational Trigger | Responsible Actor | Business Target SLA | Grace Period | Reminders & Escalation Path | Lockout / Final Action | Source Reference |
|---|---|---|---|---|---|---|---|
| **`BP-M2-NACAD-001`** Non-Academic Planning Initiation | Calendar milestone: 4 months prior to onboarding | HR Department / Department Heads | At least 4 months prior to required onboarding | None | Planning cycle launch notification dispatched to all non-academic units | Annual planned MRF submission window opened | Mod II Brief Section 1; `REQ-MOD2-02` |
| **`BP-M2-NACAD-002`** Annual Planned MRF Submission | Non-academic planning initiation notice | Department Heads | Within 15 calendar days of trigger | None | Reminder on Day 10; escalation to Registrar on Day 16 | Annual MRF portal locks (Strict quota: 1 planned MRF/dept/year) | Mod II Brief Section 1; `REQ-MOD2-09`, `10` |
| **`BP-M2-NACAD-003`** Non-Academic Vetting & Approval | Receipt of non-academic annual MRF | HR / Registrar / Management | Concluded within 30 calendar days | None | Bi-weekly status reviews by Head HR | Approved requisition quota sanctioned for department | Mod II Brief Section 1 |
| **`BP-M2-NACAD-004`** Non-Academic Recruitment Initiation | Formal MRF approval order issued | Recruitment Team | Within 7 calendar days of approval | None | Alert to Head HR on Day 5 if recruiter unassigned | Sourcing channels activated and vacancy posted | Mod II Brief Section 1; `REQ-MOD2-11` |
| **`BP-M2-NACAD-005`** RCS Phone Screening & Shortlisting | Application ingestion from CV Database | Recruiter | Within 5 working days of application receipt | None | Daily recruiter backlog monitoring by Recruitment Lead | Candidate marked "Shortlisted for Round 1" or "Rejected" | Mod II Brief Section 2; `REQ-MOD2-20` |
| **`BP-M2-NACAD-006`** Three-Round Sequential Selection | Shortlist approved | Technical Panel (R1), HR (R2), Management (R3) | Entire 3-round evaluation completed within 15 working days | None | Interview completion alerts; Round $N$ must clear before Round $N+1$ | Three-dimension evaluation sheet compiled and signed | Mod II Brief Section 2; `REQ-MOD2-15`, `16` |
| **`BP-M2-NACAD-007`** Non-Academic LOI & Recruitment Close | Round 3 Management sign-off | Recruitment Lead / Candidate | Concluded at least 15 calendar days prior to onboarding | None | Candidate check-ins; escalation if unfilled 20 days prior to onboarding | LOI accepted; candidate ready for Day-1 onboarding | Mod II Brief Section 1 & 2; `REQ-MOD2-12` |

---

### Section D: Module II — Urgent Replacement Recruitment

| Process Identifier & Name | Operational Trigger | Responsible Actor | Business Target SLA | Grace Period | Reminders & Escalation Path | Lockout / Final Action | Source Reference |
|---|---|---|---|---|---|---|---|
| **`BP-M2-URG-001`** Urgent Replacement Recruitment | Formal resignation acceptance by Dean in Module I | School Dean, Head HR, Recruitment Lead | Sourcing launched within 24 hours; position filled prior to departure | None | Daily countdown clock notifications to Head HR; weekly executive briefing | Ad-hoc MRF closed upon successful candidate joining (`BP-XMOD-001`) | Mod II Brief Section 1(i); `REQ-MOD2-03` |

---

### Section E: Module III — Subsystem 1: Group-D / Band-I Performance

| Process Identifier & Name | Operational Trigger | Responsible Actor | Business Target SLA | Grace Period | Reminders & Escalation Path | Lockout / Final Action | Source Reference |
|---|---|---|---|---|---|---|---|
| **`BP-M3-GD-001`** Monthly Evaluation Dispatch | Calendar: 1st of every calendar month | System Automation | Dispatched on 1st of the month | None | System monitoring verifies 100% dispatch to supervisors | Monthly evaluation forms active in supervisor inboxes | Mod III Brief Subsystem 1; `REQ-MOD3-01` |
| **`BP-M3-GD-002`** Monthly Supervisor Submission | Monthly evaluation form dispatch | Reporting Supervisor | Due by the 7th of the month | 8th through 10th of the month | Automated daily reminders dispatched on 8th, 9th, and 10th of the month | Unsubmitted form enters grace period on 8th | Mod III Brief Subsystem 1; `REQ-MOD3-01`, `02` |
| **`BP-M3-GD-003`** Monthly Evaluation Auto-Lockout | End of grace period on 10th of the month | System Automation | Business Deadline: 10th of the month | None (Cutoff at end of 10th) | System alert to VP-Administration summarizing locked overdue forms | Form locked; supervisor editing disabled; requires admin unlock | Mod III Brief Subsystem 1; `REQ-MOD3-03` |
| **`BP-M3-GD-004`** VP-Administration Monthly Approval | Submission / lockout of monthly evaluations | VP-Administration | Within 5 calendar days of lock (by 15th of month) | None | Reminder alert to VP-Administration on 13th of month | Formal monthly approval sign-off committed | Mod III Brief Subsystem 1; `REQ-MOD3-04` |
| **`BP-M3-GD-005`** Monthly Collation (Enclosure 2) | VP-Administration monthly approval | System Automation | Collated within 24 hours of VP approval | None | System checks verify all parameter scores collated | Updated longitudinal Enclosure 2 ledger entry committed | Mod III Brief Subsystem 1; `REQ-MOD3-05` |
| **`BP-M3-GD-006`** Annual Review Compilation at 1-Yr DOJ | Employee reaches 1-year anniversary of DOJ | HR Operations / System | Compiled on exact 1-year DOJ anniversary | None | Anniversary alert sent to HR Operations 15 days in advance | 12-month parameter-weighted scorecard generated | Mod III Brief Subsystem 1; `REQ-MOD3-06` |
| **`BP-M3-GD-007`** Probation Verification Gate | Annual evaluation compilation | HR Operations / Module I | Verified prior to compensation review | None | Alert to HR if probation status remains unconfirmed at 1 year | Probation verified; clearance unlocks compensation increment | Mod III Brief Subsystem 1; `REQ-MOD3-07` |
| **`BP-M3-GD-008`** Annual Slabs & Management Decision | Annual scorecard & probation verified | Management / VP-Administration | Decided within 15 calendar days of compilation | None | Executive reminder if pending decision > 10 days | Pre-defined slabs applied; Module I Change Request injected | Mod III Brief Subsystem 1; `REQ-MOD3-08` |

---

### Section F: Module III — Subsystem 2: General Staff KRA/KPI Performance

| Process Identifier & Name | Operational Trigger | Responsible Actor | Business Target SLA | Grace Period | Reminders & Escalation Path | Lockout / Final Action | Source Reference |
|---|---|---|---|---|---|---|---|
| **`BP-M3-KRA-001`** Onboarding Goal-Setting | Employee confirmed Date of Joining (DOJ) | Employee, Supervisor, HR | Within 30 calendar days of DOJ | None | Reminder alert on Day 20 to Supervisor and HR Operations | Form locked upon joint HR & Management approval sign-off | Mod III Brief Subsystem 2 Stage 1; `REQ-MOD3-09` |
| **`BP-M3-KRA-002`** Quarterly Cycle Initiation | Quarterly calendar milestone (Q1–Q4) | System Automation | 90-day intimation; 20-day pre-cycle reminder | None | Advance notification alerts sent to all enrolled staff and supervisors | Quarterly appraisal cycle officially active | Mod III Brief Subsystem 2 Stage 2; `REQ-MOD3-10` |
| **`BP-M3-KRA-003`** Quarterly Self-Appraisal Submission | Opening of quarterly appraisal cycle | General Staff Employee | Within 15 calendar days of cycle opening | None | Automated reminder on Day 10; final warning on Day 14 | Self-appraisal portal locks; overdue alert to Supervisor | Mod III Brief Subsystem 2 Stage 2; `REQ-MOD3-11` |
| **`BP-M3-KRA-003`** Supervisor Quarterly Verification | Submission of employee self-appraisal | Reporting Authority / Supervisor | Within 7 calendar days of submission | None | Reminder on Day 5; overdue escalation to HR on Day 8 | Verification completed; forwarded to HR observations | Mod III Brief Subsystem 2 Stage 2; `REQ-MOD3-11` |
| **`BP-M3-KRA-004`** HR Observations & Management Review | Supervisor verification completed | HR Department & Senior Management | Within 10 working days of supervisor sign-off | None | Reminder to HR on Day 7; management executive summary on Day 10 | Quarterly review approved and committed to annual ledger | Mod III Brief Subsystem 2 Stage 2; `REQ-MOD3-12` |
| **`BP-M3-KRA-005`** Annual Consolidation & Handshake | Conclusion of Q4 quarterly review cycle | Performance Committee / Management | Within 15 calendar days of Q4 closure | None | Executive status dashboard reviewed by Vice-Chancellor | Consolidated rating approved; Handshake `BP-XMOD-004` triggered | Mod III Brief Subsystem 2 Stage 3; `REQ-MOD3-13` |

---

### Section G: Module III — Subsystem 3: Faculty ECM Performance

| Process Identifier & Name | Operational Trigger | Responsible Actor | Business Target SLA | Grace Period | Reminders & Escalation Path | Lockout / Final Action | Source Reference |
|---|---|---|---|---|---|---|---|
| **`BP-M3-FAC-001`** Monthly Eligibility Batch Scan | Calendar: 10th of every calendar month | System Automation | Executed on 10th of the month | None | System alert if zero eligible faculty found or query fails | Eligible roster compiled per dual statutory criteria | Mod III Brief Subsystem 3; `REQ-MOD3-14`, `15` |
| **`BP-M3-FAC-002`** Registrar Roster Verification & Release | Completion of monthly 10th eligibility scan | Registrar | Within 2 working days (by 12th of month) | None | Reminder to Registrar on 11th; escalation on 13th | Certified roster released; appraisal notifications issued | Mod III Brief Subsystem 3; `REQ-MOD3-15` |
| **`BP-M3-FAC-003`** Faculty Self-Appraisal Submission | Receipt of appraisal release notification | Eligible Faculty Member | Within 7 working days of notification | None | Automated reminders on Working Days 4 and 6 | Self-appraisal locked; overdue alert sent to School Dean | Mod III Brief Subsystem 3; `REQ-MOD3-16` |
| **`BP-M3-FAC-004`** 4-Unit Parallel Verification | Submission of faculty self-appraisal | Dean, R&D Cell, Placement Cell, HR Dept | Within 10 working days (simultaneous parallel) | None | Automated reminder on Day 7; daily escalation thereafter | All 4 verifications must complete before ECM docketing | Mod III Brief Subsystem 3; `REQ-MOD3-17` |
| **`BP-M3-FAC-005`** Discrepancy Clarification Loop | Verifying unit raises data query | Faculty Member & Verifying Unit | Clarification submitted within 3–5 working days | None | Reminder on Day 3 to faculty member; alert to Dean on Day 6 | Clarification accepted or disputed score sealed | Mod III Brief Subsystem 3; `REQ-MOD3-17` |
| **`BP-M3-FAC-006`** Monthly ECM Docketing & Session | All 4 parallel verifications certified | Executive Committee (ECM) | Docketed 5 days prior; session held in final week of month | None | Docket distributed to members 3 days in advance | Candidate evaluated; Digital Scoring Matrix signed | Mod III Brief Subsystem 3; `REQ-MOD3-18` |
| **`BP-M3-FAC-007`** TNU Protocol Matrix & Management Decision | Conclusion of ECM evaluation session | Management / Governing Council | Decided within 5 working days of ECM session | None | Reminder to Management Secretariat on Day 3 | Formal increment/promotion decision approved | Mod III Brief Subsystem 3; `REQ-MOD3-19`, `20` |
| **`BP-M3-FAC-008`** Salary Cycle Increment & Letter Generation | Management compensation decision signed | HR Operations / System | Implemented in upcoming monthly salary cycle | None | Real-time alert to HR Payroll if pending 3 days before payroll cutoff | Increment letter auto-generated; digital file archived | Mod III Brief Subsystem 3; `REQ-MOD3-20` |

---

## 3. Shared SLA & Notification Escalation Mechanics

Across all three modules, system-generated notifications and escalations operate on strict governance rules:

### A. Notification Delivery Channels & Response Targets
1. **Real-Time In-App Alerts:** Dispatched immediately upon state transitions, task assignments, and approval requests. Required institutional acknowledgment: within active session or next login.
2. **Asynchronous System Email Notifications:** Dispatched concurrently with task creation, critical milestones, overdue warnings, and executive escalations.
3. **Escalation Notification Tiers:**
   - **Tier 1 (Courtesy Reminder):** Dispatched at 50%–75% of elapsed SLA window to the directly responsible actor.
   - **Tier 2 (Overdue Warning):** Dispatched at 100% of elapsed SLA window to the responsible actor and their immediate administrative superior.
   - **Tier 3 (Executive Escalation):** Dispatched if overdue state persists > 48 hours beyond deadline to Institutional Leadership (Registrar, Head HR, or Vice-Chancellor).

### B. Hard Administrative Lockouts
1. **Group-D Monthly Lockout (`BR-M3-003`):** Hard business deadline on the 10th of the month. Forms unsubmitted at the cutoff are permanently locked from supervisor editing. Re-opening requires formal written justification and administrative unlock authorization from VP-Administration.
2. **Faculty Self-Appraisal Lockout (`BR-M3-016`):** Hard business deadline at the expiration of 7 working days. Late submissions are locked and deferred to the subsequent monthly eligibility cycle unless granted written extension by the Registrar.
3. **Non-Academic Annual MRF Portal Lockout (`BR-M2-009`):** Hard business deadline at the expiration of 15 calendar days from planning launch. Portal strictly locks submission, enforcing the institutional quota of exactly one planned MRF per department per year.

---

## 4. Business Deadline vs. Technical Execution Separation Matrix

To eliminate any ambiguity during subsequent technical design and implementation, the following matrix explicitly contrasts the institutional business SLA with its technical execution counterpart:

| Operational Area | Institutional Business Deadline | Technical Execution Timing / Architecture Mechanism |
|---|---|---|
| **Group-D Monthly Evaluation Cutoff** | **Business Deadline:** 7th of month due date; grace period expires at close of business on 10th of month. Unsubmitted forms are locked. | **Technical Scheduler:** A scheduled background job runs at 23:59 on the 10th of the month, updating pending form statuses to `LOCKED_OVERDUE` ([`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)). |
| **Faculty ECM Eligibility Batch** | **Business Deadline:** Faculty eligibility is evaluated on the 10th of every calendar month. | **Technical Scheduler:** A monthly batch query executes during low-traffic maintenance hours on the 10th to scan PostgreSQL employee master records against eligibility rules. |
| **Effective-Date Activation** | **Business Deadline:** Approved employee changes take legal effect on the specified `effective_date`. | **Technical Scheduler:** A midnight cron worker executes daily at 00:00:00, migrating approved future-dated records into active master status and emitting outbox events. |
| **Urgent Replacement Countdown** | **Business Deadline:** Urgent replacement recruitment must conclude prior to the departing employee's last working day or semester start. | **Technical Scheduler:** A daily event scheduler decrements remaining days in the active countdown register and dispatches alert payloads. |
| **Quarterly KRA Cycle Transitions** | **Business Deadline:** 90-day intimation, 20-day reminder, 15-day submission window, 7-day supervisor verification. | **Technical Scheduler:** Background time-based queue jobs evaluate calendar dates against quarter boundaries (Q1–Q4) and transition cycle phase flags. |

---
*End of Document — Business Process SLA and Escalation Framework.*
