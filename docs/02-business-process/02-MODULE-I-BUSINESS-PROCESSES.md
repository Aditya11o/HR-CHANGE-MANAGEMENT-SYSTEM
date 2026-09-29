# Module I Business Processes — HR Change Management & Core DB
## University HR Change Management & Automation System

**Document Identifier:** `DOC-02-BPM-02`  
**Phase:** Phase 2 — Business Process Documentation (Documentation-Only)  
**Location:** `docs/02-business-process/02-MODULE-I-BUSINESS-PROCESSES.md`  
**Status:** Approved Business Process Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Module Overview & Operational Scope

Module I (HR Change Management & Automation System) serves as the institutional single source of truth for all employee data across the University. It governs:
1. The **Central Employee Database** containing comprehensive service, personal, academic, and structural records.
2. The **Dynamic Organization Chart** directly connected to the database, reflecting real-time organizational hierarchies.
3. The **Digital Employee File / Longitudinal Dossier** maintaining permanent historical records.
4. The **Standardized Employee Service Change Management Process** covering ten (10) distinct operational formats.
5. The **Mandatory Two-Level Approval Hierarchy** (Level 1: HR Review $\rightarrow$ Level 2: Senior Management Approval).
6. **Effective-Date Processing** for prospective, retroactive, and current service modifications.
7. **Immutable Audit Trails and Version History** guaranteeing complete administrative accountability.
8. **Institutional ERP Synchronization** ensuring bidirectional consistency.
9. **Real-Time Operational and Compliance Reporting**.

---

## 2. Itemized Business Processes

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            MODULE I BUSINESS PROCESS INVENTORY                                   │
├─────────────┬────────────────────────────────────────────────────────┬───────────────────────────┤
│ Process ID  │ Process Name                                           │ Traceability Mapping      │
├─────────────┼────────────────────────────────────────────────────────┼───────────────────────────┤
│ `BP-M1-001` │ Central Employee Database Management                   │ `REQ-MOD1-01`, `REQ-ENT-01│
│ `BP-M1-002` │ Dynamic Organization Structure Management              │ `REQ-MOD1-02`, `REQ-MOD1-03│
│ `BP-M1-003` │ Digital Employee File / Longitudinal Dossier           │ `REQ-MOD1-05`             │
│ `BP-M1-004` │ Employee Service Change Request Initiation (10 Formats)│ `REQ-MOD1-06` to `16`     │
│ `BP-M1-005` │ Two-Level Approval Hierarchy — Level 1: HR Review      │ `REQ-MOD1-17`             │
│ `BP-M1-006` │ Two-Level Approval Hierarchy — Level 2: Senior Mgmt    │ `REQ-MOD1-17`             │
│ `BP-M1-007` │ Effective-Date Processing & Master Activation          │ `REQ-MOD1-18`, `REQ-MOD1-19│
│ `BP-M1-008` │ Service Record Audit Logging & Version History         │ `REQ-AUD-01`, `REQ-AUD-02`│
│ `BP-M1-009` │ University ERP Synchronization & Outbound Reflection   │ `REQ-EXT-01`, `REQ-EXT-03`│
│ `BP-M1-010` │ Real-Time HR Operational & Compliance Reporting        │ `REQ-REP-01`, `REQ-REP-02`│
└─────────────┴────────────────────────────────────────────────────────┴───────────────────────────┘
```

---

### Process Identifier: BP-M1-001
**Process Name:** Central Employee Database Management & Master Record Maintenance

1. **Module / Operational Track:** Module I — Core Database & Master Data Management.
2. **Business Purpose:** Establish and maintain an authoritative, non-redundant institutional single source of truth for all employee service records, personal details, academic credentials, and institutional structures across the University.
3. **Operational Trigger:**  
   - Formal onboarding of a newly appointed employee following successful selection in Module II (`BP-XMOD-001`).
   - Administrative instantiation of an institutional record by authorized HR personnel.
4. **Prerequisites & Entry Conditions:** Verified identity credentials, signed Letter of Intent (LOI) / appointment documentation, and verified pre-onboarding checks.
5. **Primary Actors:** HR Department (Operations / Master Data Custodian).
6. **Supporting Actors:** School Deans, Department Heads, Institutional ERP Custodians.
7. **Business Inputs & Documentation:** Candidate dossier, educational certificates, identity proofs, signed offer acceptance, appointment letter details.
8. **Sequential Business Activities:**
   - Step 1: HR initiates employee record creation upon onboarding verification.
   - Step 2: System captures core identity, contact details, statutory credentials, academic degrees, and UGC qualification status.
   - Step 3: Record links to organizational primitives: primary department/school, academic/non-academic designation, initial compensation band/level, and reporting supervisor.
   - Step 4: System generates permanent University Employee ID and instantiates the active employee profile.
9. **Decision Points & Evaluation Rules:** Verification of mandatory statutory documents; validation that assigned department and supervisor exist in active institutional structure.
10. **Approval Points & Governance Gates:** Initial master record confirmation executed by authorized HR Officer.
11. **Institutional Outputs & Deliverables:** Active Master Employee Record in the Central Database; initial Digital Employee Dossier; active node in institutional reporting tree.
12. **Operational SLA & Business Deadlines:** Record established on or before Day-1 of employment.
13. **Reminders, Escalations & Lockouts:** Unverified or incomplete documentation alerts HR onboarding desk.
14. **Exception Handling & Alternate Paths:** Incomplete documents flag provisional status pending mandatory compliance window.
15. **Cross-Module Interactions & Handoffs:** Ingests candidate data from Module II (`BP-XMOD-001`); provides authoritative master data feed to Module III (`BP-XMOD-003`).
16. **Process Completion Criteria:** Employee record marked `ACTIVE` in Central Database and successfully linked to the organizational hierarchy.
17. **Audit & Compliance Requirements:** Initial master creation logged with timestamp, user ID, and source document hashes. Soft deletion only; physical deletion strictly prohibited (`REQ-ENT-05`).
18. **Authoritative Source References:** Module I Brief, Structure (1); [`REQ-MOD1-01`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-ENT-01`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Specific ERP synchronization protocol is classified under `REQ-TBD-01`.

---

### Process Identifier: BP-M1-002
**Process Name:** Dynamic Organization Structure Realignment & Hierarchy Maintenance

1. **Module / Operational Track:** Module I — Organizational Hierarchy Management.
2. **Business Purpose:** Maintain a living, dynamic organizational hierarchy directly connected to the Central Employee Database, ensuring real-time alignment of reporting structures and eliminating manual org chart maintenance.
3. **Operational Trigger:**  
   - Formal approval and effective activation of an employee service change involving designation, reportees, reporting authority, level, or department/school (`BP-M1-007`).
   - Creation of a new academic school, department, or administrative unit by University Management.
4. **Prerequisites & Entry Conditions:** Fully approved service change request (`BP-M1-006`) with an active effective date.
5. **Primary Actors:** HR Department (System Administrator).
6. **Supporting Actors:** School Deans, Department Heads, Senior Management.
7. **Business Inputs & Documentation:** Approved Change Request Form (Format b, c, d, e, or f) containing prior reporting edge and newly approved reporting edge.
8. **Sequential Business Activities:**
   - Step 1: Upon activation of the approved change, the system identifies structural modifications (supervisor change, departmental transfer, subordinate reassignment).
   - Step 2: System dynamically severs prior structural parent-child relationships and establishes verified new relationships.
   - Step 3: Subordinate branches and reporting subtrees are automatically re-anchored to the updated supervisory node without orphaned records.
   - Step 4: The dynamic organization structure updates immediately across all administrative views.
9. **Decision Points & Evaluation Rules:** Hierarchy loop prevention check (verifying that reassigning a supervisor does not create a circular reporting dependency).
10. **Approval Points & Governance Gates:** Changes inherit authorization strictly from the underlying Two-Level Approval Hierarchy (`BP-M1-005`, `BP-M1-006`); no ad-hoc manual hierarchy edits permitted.
11. **Institutional Outputs & Deliverables:** Realigned dynamic organization chart; updated reporting paths for appraisal and approval routing.
12. **Operational SLA & Business Deadlines:** Immediate reflection upon arrival of effective date (`REQ-MOD1-04`).
13. **Reminders, Escalations & Lockouts:** Circular hierarchy detection blocks activation and alerts HR Administrator for immediate correction.
14. **Exception Handling & Alternate Paths:** If a reporting supervisor departs without an immediate replacement, subordinates temporarily report to the interim HOD/Dean in accordance with institutional policy.
15. **Cross-Module Interactions & Handoffs:** Updated reporting lines immediately realign Module III evaluation routing (`BP-XMOD-005`).
16. **Process Completion Criteria:** Organization chart hierarchy rendered with 100% relational integrity and zero disconnected active employee nodes.
17. **Audit & Compliance Requirements:** Structural changes logged with before/after parent node IDs, timestamp, and authorizing change request ID.
18. **Authoritative Source References:** Module I Brief, Structure (2); [`REQ-MOD1-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD1-03`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD1-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement` (real-time responsiveness is `[B] Logical Implication`).
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M1-003
**Process Name:** Digital Employee File / Longitudinal Dossier Maintenance

1. **Module / Operational Track:** Module I — Records & Document Governance.
2. **Business Purpose:** Provide a secure, longitudinal, digital employee dossier maintaining permanent historical service records, physical document attachments, appraisal outcomes, and compensation history.
3. **Operational Trigger:**  
   - Instantiation of active employee profile (`BP-M1-001`).
   - Execution of approved service changes (`BP-M1-007`).
   - Finalization of annual performance appraisals (`BP-M3-GD-008`, `BP-M3-KRA-005`, `BP-M3-FAC-009`).
4. **Prerequisites & Entry Conditions:** Active or archived employee record in Central Database.
5. **Primary Actors:** HR Department (Records Custodian).
6. **Supporting Actors:** Individual Employee (Read-Only access to personal file), Auditing Authorities.
7. **Business Inputs & Documentation:** Onboarding documents, qualification certificates, promotion orders, increment letters, signed appraisal scorecards, disciplinary records.
8. **Sequential Business Activities:**
   - Step 1: System establishes digital dossier structure upon employee creation.
   - Step 2: System continuously aggregates transactional milestones into chronological service history.
   - Step 3: Verified digital enclosures and evidence files are attached with metadata categorization.
   - Step 4: System preserves historical version snapshots of every service modification.
9. **Decision Points & Evaluation Rules:** Document validation check (ensuring MIME-type validity, size compliance, and integrity checksum).
10. **Approval Points & Governance Gates:** Document attachment verification by HR Officer.
11. **Institutional Outputs & Deliverables:** Comprehensive, single-pane Digital Personal File accessible to authorized HR officers and the employee.
12. **Operational SLA & Business Deadlines:** Documents archived within 24 hours of milestone approval.
13. **Reminders, Escalations & Lockouts:** Missing mandatory compliance attachments flagged during annual reviews.
14. **Exception Handling & Alternate Paths:** Disputed records require formal administrative review by HR Leadership.
15. **Cross-Module Interactions & Handoffs:** Ingests LOI and onboarding files from Module II (`BP-XMOD-001`); ingests official appraisal letters from Module III (`BP-XMOD-004`).
16. **Process Completion Criteria:** Digital Personal File continuously synchronized with zero unlinked transactions.
17. **Audit & Compliance Requirements:** Immutable logging; read access audits tracked; document retention policy governed by institutional compliance schedule (`REQ-TBD-11`).
18. **Authoritative Source References:** Module I Brief, Objective; [`REQ-MOD1-05`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-DOC-06`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Institutional document retention and legal archival schedule is classified under `REQ-TBD-11`.

---

### Process Identifier: BP-M1-004
**Process Name:** Employee Service Change Request Initiation (10 Standardized Formats)

1. **Module / Operational Track:** Module I — Change Management Operations.
2. **Business Purpose:** Standardize and digitize the initiation of all employee service modifications across ten (10) prescribed institutional categories, eliminating paper-based forms and unstructured requests.
3. **Operational Trigger:**  
   - Administrative proposal for employee promotion, transfer, or structural revision by HR or Reporting Authority.
   - Annual performance appraisal outcome requiring compensation or designation adjustment (`BP-XMOD-004`).
   - Employee submission of updated educational qualifications.
4. **Prerequisites & Entry Conditions:** Active employee profile in Central Database; verified business justification.
5. **Primary Actors:** HR Department (Initiator), Reporting Authority / HOD / Dean (Proposer).
6. **Supporting Actors:** Individual Employee (for qualification updates).
7. **Business Inputs & Documentation:** Standardized digital change format corresponding to the specific request type:
   - **Format (a) — Change in Salary:** Increments, base pay revisions, special allowances, band adjustments (`REQ-MOD1-06`).
   - **Format (b) — Change in Designation:** New academic or administrative job title (`REQ-MOD1-07`).
   - **Format (c) — Change in Reportee:** Reallocation of direct reporting subordinates (`REQ-MOD1-08`).
   - **Format (d) — Change in Reporting Authority:** Reassignment of primary supervisor / reporting edge (`REQ-MOD1-09`).
   - **Format (e) — Change in Level:** Grade/level/band promotion (`REQ-MOD1-10`).
   - **Format (f) — Change in Department / School:** Organizational transfer between academic or administrative units (`REQ-MOD1-11`).
   - **Format (g) — Change in Location:** Campus, branch, or physical workstation transfer (`REQ-MOD1-12`).
   - **Format (h) — Additional Responsibility Added:** Appointment to secondary institutional role (e.g., Dean, HOD, Proctor, Warden, Coordinator) with effective start date and tenure (`REQ-MOD1-13`, `REQ-MOD1-14`). *(Administrative allowance is subject to HR policy confirmation, `REQ-TBD-09`)*.
   - **Format (i) — Change in Qualifications:** Acquisition of higher degree (Ph.D., Postdoc, NET/SLET, professional certification) with mandatory document proof upload (`REQ-MOD1-15`).
   - **Format (j) — Any Other Service Condition:** Extensible format for institutional modifications not covered by Formats (a)–(i) (`REQ-MOD1-16`).
8. **Sequential Business Activities:**
   - Step 1: Initiator selects target employee and applicable change format (a through j).
   - Step 2: System pre-populates current state from master record (pre-change value).
   - Step 3: Initiator inputs proposed new state (post-change value), business justification, and mandatory `effective_date`.
   - Step 4: Mandatory supporting documentation is uploaded (e.g., degree certificates for Format i, executive appointment order for Format h).
   - Step 5: System validates completeness and submits the request to Level-1 HR Review (`BP-M1-005`).
9. **Decision Points & Evaluation Rules:** Validation that proposed change adheres to institutional grading rules, qualification criteria, and effective date constraints.
10. **Approval Points & Governance Gates:** Submission locks the request from further ad-hoc edits and routes it into the mandatory Two-Level Approval Hierarchy.
11. **Institutional Outputs & Deliverables:** Formal Digital Change Request record in `SUBMITTED` status with timestamped snapshot of current vs. proposed values.
12. **Operational SLA & Business Deadlines:** Submission prior to monthly payroll cutoffs or scheduled academic semester transitions.
13. **Reminders, Escalations & Lockouts:** Pending unsubmitted drafts automatically expire after institutional inactivity threshold.
14. **Exception Handling & Alternate Paths:** Urgent structural realignments may be flagged for expedited executive handling.
15. **Cross-Module Interactions & Handoffs:** Directly ingests approved appraisal outcomes from Module III without manual re-entry (`BP-XMOD-004`).
16. **Process Completion Criteria:** Change request successfully instantiated and pending Level-1 HR Review.
17. **Audit & Compliance Requirements:** Full before/after differential snapshot captured; identity of initiator recorded.
18. **Authoritative Source References:** Module I Brief, Structure 3(a–j); [`REQ-MOD1-06`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md) through [`REQ-MOD1-16`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Institutional policy on administrative allowances for additional responsibilities is classified under `REQ-TBD-09`.

---

### Process Identifier: BP-M1-005
**Process Name:** Two-Level Approval Hierarchy — Level 1: HR Review & Vetting

1. **Module / Operational Track:** Module I — Governance & Approval Hierarchy.
2. **Business Purpose:** Enforce mandatory first-line administrative, regulatory, and policy vetting for all employee service change requests before executive escalation.
3. **Operational Trigger:** Submission of any standardized change request Formats (a) through (j) (`BP-M1-004`).
4. **Prerequisites & Entry Conditions:** Change request in `SUBMITTED` status with complete differential payload and attached documentation.
5. **Primary Actors:** HR Department (HR Reviewer / Verifier).
6. **Supporting Actors:** Request Initiator, Department Head.
7. **Business Inputs & Documentation:** Change Request dossier, employee service history, attached supporting evidence, institutional policy norms.
8. **Sequential Business Activities:**
   - Step 1: HR Reviewer inspects proposed modification against university staffing policies, pay scales, and qualification norms.
   - Step 2: Reviewer verifies authenticity of uploaded documentary proof (e.g., verifying Ph.D. certificate against UGC recognition standards for Format i).
   - Step 3: Reviewer verifies effective date feasibility and financial budgetary alignment.
   - Step 4: HR Reviewer executes one of three formal governance determinations:
     - **Recommend / Approve Level 1:** Advances request to Level 2 (Senior Management).
     - **Return for Clarification:** Returns request to initiator with mandatory explanatory remarks.
     - **Reject:** Formally terminates request with documented justification.
9. **Decision Points & Evaluation Rules:** Verification against policy criteria: Is qualification accredited? Does salary match approved scale? Does effective date comply with notice requirements?
10. **Approval Points & Governance Gates:** Level-1 Approval Gate. The system strictly prohibits bypassing Level-1 HR review; requests cannot route directly to Senior Management.
11. **Institutional Outputs & Deliverables:** Verified change dossier transitioning to `PENDING_MANAGEMENT_APPROVAL` status with HR review remarks and digital sign-off.
12. **Operational SLA & Business Deadlines:** HR review completed within standard institutional window (e.g., 5 business days from submission).
13. **Reminders, Escalations & Lockouts:** Pending queue counter badges alert HR desk; aged requests escalate to Head HR.
14. **Exception Handling & Alternate Paths:** Returned requests allow initiator resubmission with amended documentation without re-creating the request ID.
15. **Cross-Module Interactions & Handoffs:** Provides verified compliance gate for cross-module changes originating from Module III (`BP-XMOD-004`).
16. **Process Completion Criteria:** Formal digital execution of Level-1 approval sign-off.
17. **Audit & Compliance Requirements:** Reviewer identity, decision outcome, review comments, and timestamp recorded in immutable audit ledger.
18. **Authoritative Source References:** Module I Brief, Approval Hierarchy (a); [`REQ-MOD1-17`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M1-006
**Process Name:** Two-Level Approval Hierarchy — Level 2: Senior Management Final Approval

1. **Module / Operational Track:** Module I — Executive Governance.
2. **Business Purpose:** Provide apex executive oversight and final institutional authorization for all service condition modifications, salary revisions, and organizational reassignments.
3. **Operational Trigger:** Successful Level-1 HR recommendation and sign-off (`BP-M1-005`).
4. **Prerequisites & Entry Conditions:** Change request in `PENDING_MANAGEMENT_APPROVAL` status with verified HR Level-1 endorsement.
5. **Primary Actors:** Senior Management (Pro-Chancellor, Vice Chancellor, Registrar, or designated Executive Authority).
6. **Supporting Actors:** Head HR, Financial Controller.
7. **Business Inputs & Documentation:** Complete change dossier including initial request, attached verification evidence, HR Level-1 review observations, and financial/budgetary impact summary.
8. **Sequential Business Activities:**
   - Step 1: Senior Management accesses executive approval queue.
   - Step 2: Executive evaluates institutional necessity, budgetary implications, and strategic alignment of the proposed change.
   - Step 3: Executive executes formal decision:
     - **Approve:** Formally authorizes the service change.
     - **Return:** Sends request back to HR with directives for modification or re-negotiation.
     - **Reject:** Formally rejects the request with final executive remarks.
9. **Decision Points & Evaluation Rules:** Executive discretion based on university financial capacity, academic leadership requirements, and institutional strategy.
10. **Approval Points & Governance Gates:** Level-2 Final Approval Gate. This is the apex approval; once granted, the change is legally authorized.
11. **Institutional Outputs & Deliverables:** Authorized change request marked `APPROVED` (or `APPROVED_PENDING_ACTIVATION` if effective date is future-dated); formal notification dispatched to HR and employee.
12. **Operational SLA & Business Deadlines:** Executive review targeted within standard turnaround commitment.
13. **Reminders, Escalations & Lockouts:** Urgent pending approvals surfaced via executive notification indicators.
14. **Exception Handling & Alternate Paths:** Rejection terminates the change lifecycle; employee and initiator are formally notified with reasons.
15. **Cross-Module Interactions & Handoffs:** Triggers Effective-Date Activation (`BP-M1-007`) and Org Chart realignment (`BP-M1-002`).
16. **Process Completion Criteria:** Formal digital execution of Level-2 Senior Management sign-off.
17. **Audit & Compliance Requirements:** Executive signatory ID, approval timestamp, and final remarks recorded in immutable ledger.
18. **Authoritative Source References:** Module I Brief, Approval Hierarchy (b); [`REQ-MOD1-17`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M1-007
**Process Name:** Effective-Date Scheduling & Master Activation Processing

1. **Module / Operational Track:** Module I — Temporal Master Data Processing.
2. **Business Purpose:** Enforce temporal integrity by activating approved service changes precisely on their legally mandated `effective_date`, natively supporting future-dated, current, and retrospective adjustments.
3. **Operational Trigger:**  
   - Final Senior Management approval of a change request (`BP-M1-006`).
   - Arrival of the scheduled calendar date matching an approved change's `effective_date`.
4. **Prerequisites & Entry Conditions:** Change request in `APPROVED` status with verified `effective_date`.
5. **Primary Actors:** System Temporal Engine / Background Scheduler (`[C] Approved Technical Decision`).
6. **Supporting Actors:** HR Department (Monitor), Institutional Payroll Desk.
7. **Business Inputs & Documentation:** Approved Change Request record containing differential fields, employee ID, and `effective_date`.
8. **Sequential Business Activities:**
   - Step 1: Upon Senior Management approval, system evaluates the `effective_date` parameter:
     - **Future-Dated (`effective_date > current_date`):** Record transitions to `APPROVED_PENDING_ACTIVATION`. Master database remains unchanged; pending change is scheduled.
     - **Immediate / Current (`effective_date = current_date`):** Record transitions to `ACTIVATED`; master database is updated immediately.
     - **Retrospective / Backdated (`effective_date < current_date`):** Record transitions to `ACTIVATED`; master database updates immediately with retrospective flags generated for payroll reconciliation.
   - Step 2: When the calendar date reaches the scheduled `effective_date`, the system automatically commits the approved values to the active Central Employee Database record.
   - Step 3: Dynamic Organization Chart realignments are immediately executed if structural fields changed (`BP-M1-002`).
   - Step 4: Digital Personal File updates and outbox synchronization triggers are emitted.
9. **Decision Points & Evaluation Rules:** Calendar date matching evaluation; verification that employee remains active at time of activation.
10. **Approval Points & Governance Gates:** Governed strictly by the prior Two-Level Approval; activation is an automated execution of approved policy.
11. **Institutional Outputs & Deliverables:** Committed master record updates in Central Database; realigned Organization Chart; payroll notification.
12. **Operational SLA & Business Deadlines:** Master changes take operational effect on the calendar date specified by `effective_date`. *(Technical execution timing at 00:00 midnight is governed by the approved architecture baseline [C])*.
13. **Reminders, Escalations & Lockouts:** Automated notification delivered to HR upon successful activation; anomalies alert HR Systems Administrator.
14. **Exception Handling & Alternate Paths:** If an employee separates prior to a future effective date, the pending scheduled activation is automatically cancelled.
15. **Cross-Module Interactions & Handoffs:** Triggers dynamic org chart realignment (`BP-M1-002`) and outbound ERP synchronization (`BP-M1-009`).
16. **Process Completion Criteria:** Change request status marked `ACTIVATED`, master records updated, and audit ledger closed.
17. **Audit & Compliance Requirements:** Timestamped activation event logged capturing exact execution timestamp, affected fields, and effective date.
18. **Authoritative Source References:** Module I Brief, Methodology; [`REQ-MOD1-18`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD1-19`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement` (automated scheduled processing is `[C] Approved Technical Decision`).
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M1-008
**Process Name:** Service Record Audit Trail Logging & Version History Maintenance

1. **Module / Operational Track:** Module I — Audit, Compliance & Version Control.
2. **Business Purpose:** Maintain an immutable, non-destructive audit ledger and complete version history of all employee service modifications, ensuring regulatory compliance and legal defensibility.
3. **Operational Trigger:** Any creation, modification, approval, rejection, or activation of employee records or change requests.
4. **Prerequisites & Entry Conditions:** Triggering administrative or system transaction.
5. **Primary Actors:** System Audit Engine (`[C] Approved Technical Decision`).
6. **Supporting Actors:** HR Compliance Officer, Internal / Statutory Auditors.
7. **Business Inputs & Documentation:** Transaction metadata: actor ID, IP address, timestamp, prior state (pre-image), updated state (post-image), change reason.
8. **Sequential Business Activities:**
   - Step 1: System captures atomic differential before and after any data mutation.
   - Step 2: System writes an immutable, append-only audit record linking actor, exact timestamp, and serialized JSON diff.
   - Step 3: For master employee changes, system increments the entity version number, preserving previous versions in historical archives.
   - Step 4: Audit records are locked against physical editing, overwriting, or deletion.
9. **Decision Points & Evaluation Rules:** Verification that write operations are append-only.
10. **Approval Points & Governance Gates:** Automated system-level governance; audit logs cannot be suppressed or bypassed by any user role.
11. **Institutional Outputs & Deliverables:** Comprehensive audit log; longitudinal version history reconstructable at any historical point in time.
12. **Operational SLA & Business Deadlines:** Synchronous with the initiating business transaction.
13. **Reminders, Escalations & Lockouts:** Audit write failure halts the business transaction, preserving data integrity.
14. **Exception Handling & Alternate Paths:** In the event of audit storage degradation, transactions are blocked until the audit ledger is confirmed writable.
15. **Cross-Module Interactions & Handoffs:** Provides universal audit framework across Modules I, II, and III.
16. **Process Completion Criteria:** Audit record committed to permanent immutable storage.
17. **Audit & Compliance Requirements:** Write-once, read-many (WORM) principles; physical deletion strictly prohibited (`REQ-ENT-05`).
18. **Authoritative Source References:** Module I Brief, Methodology; [`REQ-AUD-01`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-AUD-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Retention lifecycle schedule is classified under `REQ-TBD-11`.

---

### Process Identifier: BP-M1-009
**Process Name:** University ERP Synchronization & Outbound Reflection

1. **Module / Operational Track:** Module I — Institutional Enterprise Integration.
2. **Business Purpose:** Ensure that the Central Employee Database is fully reflected and synchronized with the University Enterprise Resource Planning (ERP) platform without manual re-entry.
3. **Operational Trigger:** Commitment and activation of any master employee change or new employee creation (`BP-M1-001`, `BP-M1-007`).
4. **Prerequisites & Entry Conditions:** Activated master record update in Central Database.
5. **Primary Actors:** System Integration Layer (`[C] Approved Technical Decision`), HR Systems Administrator.
6. **Supporting Actors:** University IT / ERP Custodians.
7. **Business Inputs & Documentation:** Activated employee master delta: employee ID, salary components, designation, department, structural role, effective date.
8. **Sequential Business Activities:**
   - Step 1: Upon master activation, system prepares the outbound synchronization payload.
   - Step 2: System registers the update in the transactional outbound integration ledger.
   - Step 3: Integration worker dispatches payload to University ERP interface.
   - Step 4: System captures delivery acknowledgment and ERP transaction reference.
9. **Decision Points & Evaluation Rules:** Verification of successful transmission and receipt confirmation from ERP.
10. **Approval Points & Governance Gates:** Automated execution following approved Level-2 Senior Management sign-off.
11. **Institutional Outputs & Deliverables:** Synchronized ERP master record; logged delivery confirmation receipt.
12. **Operational SLA & Business Deadlines:** Synchronization completed in alignment with daily institutional payroll and ERP update schedules.
13. **Reminders, Escalations & Lockouts:** Delivery retry mechanism with alerting to HR Systems Administrator upon repeated interface failures.
14. **Exception Handling & Alternate Paths:** If ERP endpoint is unavailable, outbound payloads persist in outbound queue without transactional loss, retrying automatically upon connection restoration.
15. **Cross-Module Interactions & Handoffs:** Bridges core HR records to university-wide financial and administrative modules.
16. **Process Completion Criteria:** Confirmed acknowledgment received from University ERP.
17. **Audit & Compliance Requirements:** Outbound payload, transmission timestamp, and ERP response receipt archived in integration audit log.
18. **Authoritative Source References:** Module I Brief, Structure (1); [`REQ-EXT-01`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-EXT-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-EXT-03`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement` (transactional outbox pattern is `[C] Approved Technical Decision`).
20. **Controlled Open Decisions (TBD):** Exact technical protocol (REST API, staging tables, or SFTP) is classified under `REQ-TBD-01`.

---

### Process Identifier: BP-M1-010
**Process Name:** Real-Time HR Operational & Statutory Compliance Reporting

1. **Module / Operational Track:** Module I — Analytics & Reporting Engine.
2. **Business Purpose:** Provide real-time operational visibility, management dashboards, and statutory compliance reports dynamically executed against the Central Employee Database.
3. **Operational Trigger:** Administrative request by HR personnel, scheduled management reporting cadence, or statutory audit review.
4. **Prerequisites & Entry Conditions:** Authorized access credentials with appropriate RBAC reporting permissions.
5. **Primary Actors:** HR Department (Reporting Analyst / Administrator), Senior Management.
6. **Supporting Actors:** Academic Deans, Statutory Regulatory Bodies (UGC / NAAC / NIRF).
7. **Business Inputs & Documentation:** Parameterized filter criteria (department, school, designation, grade level, tenure, date ranges).
8. **Sequential Business Activities:**
   - Step 1: User selects desired report template (e.g., Active Staff Roster, Departmental Headcount, Service Modification Audit, Diversity/Category Distribution).
   - Step 2: User applies dynamic filtering parameters.
   - Step 3: System compiles real-time dataset reflecting current master state.
   - Step 4: System renders interactive tabular view with export capabilities to Excel (XLSX) and CSV formats.
9. **Decision Points & Evaluation Rules:** Role-based data masking rules (e.g., masking confidential financial or personal identity fields based on viewer permissions).
10. **Approval Points & Governance Gates:** Role-based authorization enforced prior to query execution.
11. **Institutional Outputs & Deliverables:** Real-time operational dashboards, compiled compliance reports, downloadable Excel/CSV datasets.
12. **Operational SLA & Business Deadlines:** Real-time execution upon request.
13. **Reminders, Escalations & Lockouts:** N/A.
14. **Exception Handling & Alternate Paths:** Query timeout protection on complex historical trend queries.
15. **Cross-Module Interactions & Handoffs:** Consolidates data originating across Modules I, II, and III.
16. **Process Completion Criteria:** Report generated, rendered, and successfully exported.
17. **Audit & Compliance Requirements:** Report generation queries logged in access audit log.
18. **Authoritative Source References:** Module I Brief, Reports; [`REQ-REP-01`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-09`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement` (export formatting is `[B] Logical Implication`).
20. **Controlled Open Decisions (TBD):** None.

---
*End of Document — Module I Business Processes.*
