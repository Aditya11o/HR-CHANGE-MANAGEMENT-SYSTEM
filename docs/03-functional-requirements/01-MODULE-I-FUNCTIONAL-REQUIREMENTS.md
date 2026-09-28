# Module I — HR Change Management & Automation
## Functional Requirements Specification

**Document Identifier:** `DOC-03-FRD-MOD-01`  
**Phase:** Phase 3 — Functional Requirements Specification (Documentation-Only)  
**Location:** `docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`  
**Status:** Approved Functional Baseline  
**Authoritative Baseline:** [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) & [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)  
**Source Requirement:** `27-07-26 - Revised HR Change Management & Automation System-Module I.pdf`  
**Date:** September 29, 2026  

---

## 1. Purpose

The purpose of Module I is to establish an authoritative, centralized, web-based HR Change Management & Automation System that acts as the single source of truth for all employee service-related data, organizational reporting lines, and service condition changes across the University. 

The system eliminates duplicate data entry across administrative units, guarantees that every approved modification is automatically reflected across connected records, organizational charts, reports, documents, and digital personal files, and maintains an immutable, time-stamped audit trail with effective-date scheduling.

---

## 2. Scope

Module I governs:
1. The **Central Employee Database** containing master records of all university personnel.
2. The dynamic, automatically updating **Organization Chart**.
3. The **Digital Employee File** archiving historical records and change documentation.
4. Standardized change request lifecycles across **10 service change categories**:
   - Salary Change
   - Designation Change
   - Reportee Change
   - Reporting Authority Change
   - Level Change
   - Department / School Change
   - Location Change
   - Additional Responsibility
   - Qualification Change
   - Other Service Condition
5. The **2-Level Approval Hierarchy** (HR Level $\rightarrow$ Senior Management Level).
6. **Effective Date Processing** for scheduling present and future-dated changes.
7. Comprehensive **Audit Trail & Version History** tracking before/after states.
8. Master data **ERP Reflection** synchronization.
9. Dynamic, real-time **HR Reporting**.

---

## 3. Actors and Roles

The following actors and roles are explicitly involved in Module I operations:

| Actor / Role | Description & Documented Authority | Source Reference | Classification |
|---|---|---|---|
| **HR Team / HR Level** | Operational HR administrators responsible for initiating or vetting service condition change requests, validating compliance against service rules, and approving at Level 1. | Module I, Structure 3 & Approval Hierarchy (a) | `[A] EXPLICIT REQUIREMENT` |
| **Senior Management Level** | Institutional executive leadership (e.g., Vice-Chancellor, Pro-Chancellor, Registrar, Managing Leadership) possessing final institutional approval authority for service condition changes at Level 2. | Module I, Approval Hierarchy (b) | `[A] EXPLICIT REQUIREMENT` |
| **University Employee** | Active faculty, staff, or personnel whose service conditions, reporting lines, compensation, and qualifications are maintained within the database. | Module I, Structure 1 & 3 | `[A] EXPLICIT REQUIREMENT` |
| **Reporting Authority / Supervisor** | Supervisory role assigned to manage reportees; modified via change formats (c) and (d). | Module I, Structure 3(c, d) | `[A] EXPLICIT REQUIREMENT` |
| **Department / School Leadership** | Deans of Schools and Heads of Department whose organizational units are modified via format (f). | Module I, Structure 3(f) | `[A] EXPLICIT REQUIREMENT` |

---

## 4. Central Employee Database

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             CENTRAL EMPLOYEE DATABASE CONCEPT                                    │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ • Institutional Single Source of Truth for all personnel data                                    │
│ • Fully reflected in University ERP                                                              │
│ • Drives dynamic Org Chart, Digital Personal Files, and Downstream Modules (II & III)            │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

- **`MOD1-CDB-REQ-01` [A] Single Source of Truth:** The system shall maintain a centralized database of all university employees, serving as the sole authoritative repository for employee service records.
- **`MOD1-CDB-REQ-02` [A] Elimination of Duplicate Data Entry:** Every approved change made in the Central Employee Database shall automatically propagate across connected HR records, organizational structures, reports, documents, and employee files without manual re-entry.
- **`MOD1-CDB-REQ-03` [A] Full ERP Reflection:** The Central Employee Database shall be fully reflected in the University's ERP system.
- **`MOD1-CDB-REQ-04` [B] Relational Master Fields:** The database shall maintain core service attributes including Employee ID, Full Name, Current Designation, Current Department/School, Current Level/Band, Current Salary/Pay Structure, Reporting Authority, Date of Joining (DOJ), Probation Status, and Location. *(Exact field-level schema is governed by `[E] TBD` pending University HR confirmation).*
- **`MOD1-CDB-REQ-05` [B] Employee Status Lifecycle:** The database shall track employee operational status (e.g., Active, On Probation, Confirmed, Resigned, Retired) with strict referential integrity.

---

## 5. Dynamic Organization Chart

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            DYNAMIC ORGANIZATION CHART LOGIC                                      │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Central Employee Database Modifications ──► Event Trigger ──► Real-Time Org Chart Node Re-align   │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

- **`MOD1-ORG-REQ-01` [A] Connected Org Chart:** The system shall provide an Organization Chart directly connected to the Central Employee Database.
- **`MOD1-ORG-REQ-02` [A] Automated Updating:** The Organization Chart shall automatically update whenever changes occur in the Central Employee Database (e.g., updates to reporting lines, designations, departments, or supervisory roles).
- **`MOD1-ORG-REQ-03` [B] Hierarchical Tree Traversal:** The Organization Chart shall support multi-level hierarchical visualization, allowing authorized users to navigate from executive leadership down to schools, departments, programs, and individual reportees.
- **`MOD1-ORG-REQ-04` [B] Real-Time Hierarchy Responsiveness:** The organizational hierarchy shall render with high performance and sub-second responsiveness, ensuring immediate, real-time reflection across visual tree structures upon any approved change in reporting authority, designation, or department (caching architecture governed by the approved technical baseline).

---

## 6. Employee Digital File

- **`MOD1-FIL-REQ-01` [A] Connected Employee Files:** The system shall maintain a digital employee file for every employee, automatically updated upon approval of service-related changes.
- **`MOD1-FIL-REQ-02` [B] Historical Service Dossier:** The digital file shall consolidate all approved service change letters, job description updates, additional responsibility assignment letters, and qualification certificates.
- **`MOD1-FIL-REQ-03` [B] Cross-Module Document Aggregation:** The digital file shall automatically receive and store appraisal forms, monthly/annual reports, and outcome letters from Module III, as well as onboarding documents from Module II.

---

## 7. Employee Service Change Management (10 Formats)

The system shall support standardized digital change formats across ten specific categories:

### 7.1 Salary Change
- **`MOD1-CHG-REQ-01` [A] Format 3(a) — Change in Salary:** The system shall provide a standardized format to process adjustments in compensation package, basic salary, allowances, or pay structure.
- **`MOD1-CHG-REQ-02` [B] Salary Change Data Capture:** The format shall capture current salary, proposed salary, reason/justification for revision, effective date, and supporting authorization documents.

### 7.2 Designation Change
- **`MOD1-CHG-REQ-03` [A] Format 3(b) — Change in Designation:** The system shall provide a standardized format to process promotions, title realignments, or re-designations.
- **`MOD1-CHG-REQ-04` [B] Designation Propagation:** Upon approval and reaching the effective date, the updated designation shall immediately reflect on the employee master, Org Chart node, and official documents.

### 7.3 Reportee Change
- **`MOD1-CHG-REQ-05` [A] Format 3(c) — Change in Reportee:** The system shall provide a standardized format to reassign one or more subordinate employees to a new or existing supervisor.
- **`MOD1-CHG-REQ-06` [B] Bulk Reportee Reassignment:** The system shall support both individual and bulk reassignment of reportees (e.g., during organizational restructuring).

### 7.4 Reporting Authority Change
- **`MOD1-CHG-REQ-07` [A] Format 3(d) — Change in Reporting Authority:** The system shall provide a standardized format to modify the designated supervisory authority for an employee.
- **`MOD1-CHG-REQ-08` [B] Org Chart Node Realignment:** Modifying the reporting authority shall automatically update parent-child node relationships in the dynamic Organization Chart.

### 7.5 Level Change
- **`MOD1-CHG-REQ-09` [A] Format 3(e) — Change in Level:** The system shall provide a standardized format to record changes in employee structural tier, job level, or employment band.
- **`MOD1-CHG-REQ-10` [B] Band/Level Validation:** The format shall validate the proposed level against configured university grading scales.

### 7.6 Department / School Change
- **`MOD1-CHG-REQ-11` [A] Format 3(f) — Change in Department/School:** The system shall provide a standardized format to process inter-departmental transfers and school reassignment.
- **`MOD1-CHG-REQ-12` [B] Dual Impact Handling:** The format shall automatically handle concurrent changes in departmental reporting lines and physical location if applicable.

### 7.7 Location Change
- **`MOD1-CHG-REQ-13` [A] Format 3(g) — Change in Location:** The system shall provide a standardized format to record changes in campus, office building, or geographic work location.

### 7.8 Additional Responsibility Added
- **`MOD1-CHG-REQ-14` [A] Format 3(h) — Additional Responsibility Added:** The system shall provide a standardized format to assign secondary institutional roles (e.g., Dean, Head of Department, Proctor, Warden, Committee Chair, Cell Coordinator) without removing primary designations.
- **`MOD1-CHG-REQ-15` [B] Secondary Role Tracking:** The system shall track effective start dates and expected tenures associated with the additional responsibility; whether any administrative allowance is associated with specific additional responsibilities is subject to HR policy confirmation and is classified as **[E] TBD**.

### 7.9 Change in Qualifications
- **`MOD1-CHG-REQ-16` [A] Format 3(i) — Change in Qualifications:** The system shall provide a standardized format to record the attainment of higher academic degrees, post-doctoral qualifications, statutory certifications, or professional licenses.
- **`MOD1-CHG-REQ-17` [B] Document Verification Attachment:** The format shall mandate the attachment of digital copies of verified degree certificates or transcripts.

### 7.10 Any Other Employee Service Condition
- **`MOD1-CHG-REQ-18` [A] Format 3(j) — Other Service Conditions:** The system shall provide an extensible format to record any other employee service condition related to fields in the database.
- **`MOD1-CHG-REQ-19` [B] Extensible Schema:** The format shall utilize dynamic field capture while maintaining the standardized two-level approval hierarchy and audit trail.

---

## 8. Change Request Lifecycle

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               CHANGE REQUEST LIFECYCLE                                           │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
                                                 │
                                                 ▼
                                     ┌───────────────────────┐
                                     │      1. INITIATED     │ (Drafted by HR / Authorized User)
                                     └───────────┬───────────┘
                                                 │ Submit
                                                 ▼
                                     ┌───────────────────────┐
                                     │  2. PENDING_HR_LEVEL  │ (Vetting & Policy Check)
                                     └───────────┬───────────┘
                                                 │ HR Approval
                                                 ▼
                                     ┌───────────────────────┐
                                     │ 3. PENDING_SENIOR_MGMT│ (Executive Authorization)
                                     └───────────┬───────────┘
                                                 │ Senior Mgmt Approval
                                                 ▼
                                     ┌───────────────────────┐
               ┌─────────────────────┤      4. APPROVED      ├─────────────────────┐
               │ If Effective Date   └───────────────────────┘ If Effective Date   │
               │ <= Current Date                               > Current Date      │
               ▼                                                                   ▼
┌─────────────────────────────┐                                     ┌─────────────────────────────┐
│    5. COMMITTED_ACTIVE      │                                     │ 6. APPROVED_PENDING_SCHEDULE│
│ • Master DB Record Updated  │                                     │ • Staged in Scheduler Queue │
│ • Org Chart Re-aligned      │                                     │ • Midnight worker activates │
│ • ERP Outbox Emitted        │                                     │   on effective date         │
└─────────────────────────────┘                                     └─────────────────────────────┘
```

- **`MOD1-LIF-REQ-01` [B] Finite State Machine:** Every change request shall transition through explicit, deterministic lifecycle states (`INITIATED`, `PENDING_HR_APPROVAL`, `PENDING_SENIOR_MGMT_APPROVAL`, `APPROVED_PENDING_ACTIVATION`, `COMMITTED_ACTIVE`, `REJECTED`, `CANCELLED`).
- **`MOD1-LIF-REQ-02` [B] Rejection and Query Handling:** If rejected at Level 1 or Level 2, the reviewer must provide mandatory written remarks; the initiator shall be notified and the record archived as `REJECTED`.

---

## 9. Two-Level Approval Hierarchy

- **`MOD1-APP-REQ-01` [A] Level Approval Hierarchy:** All employee service condition changes shall strictly navigate a formal two-level approval hierarchy:
  1. *Level 1:* At HR Level
  2. *Level 2:* At Senior Management Level
- **`MOD1-APP-REQ-02` [B] Role-Based Gating:** The system shall prevent Level 2 authorization until Level 1 approval is formally committed and recorded in the audit trail.
- **`MOD1-APP-REQ-03` [B] Segregation of Duties:** An initiator cannot grant self-approval; Level 1 and Level 2 approvals must be executed by distinct authenticated actors holding appropriate institutional roles.

---

## 10. Effective Date Processing

- **`MOD1-EFF-REQ-01` [A] Database Change Methodology:** The system shall implement a database change methodology ensuring that any approved change comes into effect strictly from the specified mentioned date (`effective_date`).
- **`MOD1-EFF-REQ-02` [B] Immediate vs. Future-Dated Activation:**
  - If `effective_date` $\le$ `current_date`, approved changes shall be committed to the master record immediately upon Level 2 approval.
  - If `effective_date` > `current_date`, the request remains in `APPROVED_PENDING_ACTIVATION` state until the scheduled date.
- **`MOD1-EFF-REQ-03` [A/C] Scheduled Activation Processing:** (Explicit Business Rule [A]) An approved change shall become effective on the specified effective date (`effective_date`); (Approved Technical Execution [C]) The technical activation timing shall be executed via automated background/scheduled processing that evaluates pending approved requests matching the effective date, commits updates to the master database, realigns the Org Chart, emits ERP synchronization events, and dispatches stakeholder notifications.

---

## 11. Audit Trail

- **`MOD1-AUD-REQ-01` [A] Mandatory Audit Trail:** There shall be an immutable audit trail capturing every database modification, change request submission, review, approval, rejection, and system-automated activation.
- **`MOD1-AUD-REQ-02` [B] Audit Payload Specification:** Every audit log entry shall record:
  1. Unique Transaction UUID
  2. Timestamp (UTC and Local University Time)
  3. Authenticated Actor ID and Institutional Role
  4. Client IP Address and User Agent
  5. Action Type (CREATE, SUBMIT, APPROVE, REJECT, SCHEDULE_ACTIVATE)
  6. Target Employee ID
  7. Exact Pre-Change State (`pre_state_json`)
  8. Exact Post-Change State (`post_state_json`)
- **`MOD1-AUD-REQ-03` [C] Append-Only Storage:** Audit records shall be stored in append-only PostgreSQL tables protected against administrative tampering or modification.

---

## 12. Version History

- **`MOD1-VER-REQ-01` [A] Version History:** The system shall maintain complete version history across all employee service condition records.
- **`MOD1-VER-REQ-02` [B] Temporal Ledger Modeling:** Modifying an employee record shall not overwrite historical data; it shall create a new versioned entry with explicit `valid_from` and `valid_to` timestamps, allowing retrospective historical audits at any historical point in time.

---

## 13. ERP Reflection

- **`MOD1-ERP-REQ-01` [A] Master Data Reflection:** The Central Employee Database shall be fully reflected in the University's ERP system.
- **`MOD1-ERP-REQ-02` [B] Automated Synchronization:** Every approved and activated service condition change shall trigger an outbound synchronization event to the ERP.
- **`MOD1-ERP-REQ-03` [C] Transactional Outbox Pattern:** Outbound ERP events shall be written to an `erp_outbox` table within the same database transaction as the master record update, guaranteeing zero data loss if the external ERP endpoint experiences intermittent unavailability.
- **`MOD1-ERP-REQ-04` [E] ERP Technical Protocol (TBD):** The specific communication protocol (REST API, database staging tables, or batch SFTP) is subject to `[E] TBD` pending University IT confirmation.

---

## 14. Notifications and SLA Behaviour

- **`MOD1-NTF-REQ-01` [B] Workflow Dispatch Notifications:** The system shall automatically notify HR Level reviewers upon change request initiation, Senior Management upon HR Level clearance, and the initiator upon final approval or rejection.
- **`MOD1-NTF-REQ-02` [B] Activation Notification:** The system shall notify the employee, their reporting authority, and departmental leadership upon effective-date activation of any designation, salary, or reporting line change.
- **`MOD1-NTF-REQ-03` [D] Review SLA Tracking:** Proposed SLA timers shall monitor pending approvals at HR Level (e.g., 3 working days) and Senior Management Level (e.g., 5 working days) with automated reminder alerts before escalation.

---

## 15. Reporting Requirements

- **`MOD1-REP-REQ-01` [A] HR Report Formats:** HR shall provide the lists and formats of various reports required to be generated.
- **`MOD1-REP-REQ-02` [A] Extensibility of Reports:** The system shall provide provisions for addition and deletion of reports over time without requiring core application rewrites.
- **`MOD1-REP-REQ-03` [A] Real-Time Report Generation:** Provision for generation of real-time reports shall be present.
- **`MOD1-REP-REQ-04` [B] Standard Baseline Reports:** The system shall natively generate:
  1. *Master Employee Service Roster* (filterable by school, department, level, designation)
  2. *Historical Service Condition Change Report* (by date range, change type, actor)
  3. *Pending Change Request Pipeline Report* (by approval stage and age)
  4. *Scheduled Effective-Date Activation Report* (upcoming future-dated changes)

---

## 16. Functional Requirement Catalogue

| Requirement ID | Section | Requirement Title | Classification | Source Brief Ref |
|---|---|---|---|---|
| `MOD1-CDB-REQ-01` | 4 | Single Source of Truth Master DB | `[A] EXPLICIT` | Module I, Background & Objective |
| `MOD1-CDB-REQ-02` | 4 | Elimination of Duplicate Data Entry | `[A] EXPLICIT` | Module I, Background & Objective |
| `MOD1-CDB-REQ-03` | 4 | Full ERP Reflection | `[A] EXPLICIT` | Module I, Structure (1) |
| `MOD1-CDB-REQ-04` | 4 | Core Relational Master Attributes | `[B] LOGICAL` | Derived from Structure (1 & 3) |
| `MOD1-ORG-REQ-01` | 5 | Connected Dynamic Org Chart | `[A] EXPLICIT` | Module I, Structure (2) |
| `MOD1-ORG-REQ-02` | 5 | Automated Org Chart Realignment | `[A] EXPLICIT` | Module I, Structure (2) |
| `MOD1-ORG-REQ-03` | 5 | Hierarchical Tree Traversal | `[B] LOGICAL` | Derived from Structure (2) |
| `MOD1-FIL-REQ-01` | 6 | Connected Digital Employee File | `[A] EXPLICIT` | Module I, Background & Objective |
| `MOD1-FIL-REQ-02` | 6 | Historical Service Dossier Aggregation | `[B] LOGICAL` | Derived from Objective |
| `MOD1-CHG-REQ-01` | 7.1 | Salary Change Format | `[A] EXPLICIT` | Module I, Structure 3(a) |
| `MOD1-CHG-REQ-03` | 7.2 | Designation Change Format | `[A] EXPLICIT` | Module I, Structure 3(b) |
| `MOD1-CHG-REQ-05` | 7.3 | Reportee Change Format | `[A] EXPLICIT` | Module I, Structure 3(c) |
| `MOD1-CHG-REQ-07` | 7.4 | Reporting Authority Change Format | `[A] EXPLICIT` | Module I, Structure 3(d) |
| `MOD1-CHG-REQ-09` | 7.5 | Level Change Format | `[A] EXPLICIT` | Module I, Structure 3(e) |
| `MOD1-CHG-REQ-11` | 7.6 | Department/School Change Format | `[A] EXPLICIT` | Module I, Structure 3(f) |
| `MOD1-CHG-REQ-13` | 7.7 | Location Change Format | `[A] EXPLICIT` | Module I, Structure 3(g) |
| `MOD1-CHG-REQ-14` | 7.8 | Additional Responsibility Format | `[A] EXPLICIT` | Module I, Structure 3(h) |
| `MOD1-CHG-REQ-16` | 7.9 | Qualification Change Format | `[A] EXPLICIT` | Module I, Structure 3(i) |
| `MOD1-CHG-REQ-18` | 7.10 | Other Service Condition Format | `[A] EXPLICIT` | Module I, Structure 3(j) |
| `MOD1-LIF-REQ-01` | 8 | Change Request Finite State Machine | `[B] LOGICAL` | Derived from Structure (3) & Approvals |
| `MOD1-APP-REQ-01` | 9 | Two-Level Approval Hierarchy | `[A] EXPLICIT` | Module I, Level Approval Hierarchy (a, b) |
| `MOD1-APP-REQ-02` | 9 | Role-Based Gating & Order Enforcement | `[B] LOGICAL` | Derived from Approval Hierarchy |
| `MOD1-EFF-REQ-01` | 10 | Effective Date Database Methodology | `[A] EXPLICIT` | Module I, Methodology |
| `MOD1-EFF-REQ-03` | 10 | Scheduled Activation Processing | `[A/C] EXPLICIT/TECH` | Tech Architecture Baseline, Section 7 |
| `MOD1-AUD-REQ-01` | 11 | Immutable Audit Trail | `[A] EXPLICIT` | Module I, Methodology |
| `MOD1-AUD-REQ-02` | 11 | Audit Payload State Diffing | `[B] LOGICAL` | Derived from Audit Requirement |
| `MOD1-VER-REQ-01` | 12 | Complete Version History | `[A] EXPLICIT` | Module I, Methodology |
| `MOD1-ERP-REQ-01` | 13 | Full Reflection in ERP | `[A] EXPLICIT` | Module I, Structure (1) |
| `MOD1-ERP-REQ-03` | 13 | Transactional Outbox Pattern | `[C] APPROVED TECH` | Tech Architecture Baseline, Section 7 |
| `MOD1-REP-REQ-01` | 15 | HR Provision of Report Formats | `[A] EXPLICIT` | Module I, Reports |
| `MOD1-REP-REQ-02` | 15 | Extensibility (Add/Delete Reports) | `[A] EXPLICIT` | Module I, Reports |
| `MOD1-REP-REQ-03` | 15 | Real-Time Report Generation | `[A] EXPLICIT` | Module I, Reports |

---

## 17. Requirement Traceability

| Functional Requirement ID | Source Document Reference | Base Traceability ID (`PROJECT_REQUIREMENTS_ANALYSIS.md`) | Downstream Phase Dependency |
|---|---|---|---|
| `MOD1-CDB-REQ-01` to `05` | Module I PDF, Page 1, Section 1 | `MOD1-CDB-01` | Phase 4 (ERD: `employees` table), Phase 6 (API: `GET /employees`) |
| `MOD1-ORG-REQ-01` to `04` | Module I PDF, Page 1, Section 2 | `MOD1-ORG-01` | Phase 4 (ERD: hierarchy DAG), Phase 7 (UI: Org Tree component) |
| `MOD1-CHG-REQ-01` to `19` | Module I PDF, Page 1, Section 3(a-j) | `MOD1-CHG-01` | Phase 4 (ERD: `change_requests`), Phase 6 (API: `POST /changes`) |
| `MOD1-APP-REQ-01` to `03` | Module I PDF, Page 1, Approvals | `MOD1-APP-01` | Phase 5 (Workflows: 2-stage approval state machine) |
| `MOD1-EFF-REQ-01` to `03` | Module I PDF, Page 1, Methodology | `MOD1-DAT-01` | Phase 5 (Scheduler: midnight activation worker) |
| `MOD1-AUD-REQ-01` to `03` | Module I PDF, Page 1, Methodology | `MOD1-DAT-01` | Phase 4 (ERD: `audit_logs`), Phase 8 (Security: tamper logging) |
| `MOD1-VER-REQ-01` to `02` | Module I PDF, Page 1, Methodology | `MOD1-DAT-01` | Phase 4 (ERD: `entity_versions` temporal ledger) |
| `MOD1-ERP-REQ-01` to `04` | Module I PDF, Page 1, Section 1 | `MOD1-CDB-01` | Phase 4 (ERD: `erp_outbox`), Phase 6 (API: ERP webhook/sync) |
| `MOD1-REP-REQ-01` to `04` | Module I PDF, Page 1, Reports | `MOD1-REP-01` | Phase 6 (API: `/reports`), Phase 7 (UI: Report viewer) |

---

## 18. Open Questions / TBD

The following items are officially classified as **`[E] TBD / OPEN DECISION`** requiring confirmation from University leadership:

1. **`MOD1-TBD-01` ERP Integration Protocol:** What exact technical integration interface is exposed by the University ERP (REST API endpoints, direct database staging tables, or batch flat-files)? Who generates the primary Employee ID key?
2. **`MOD1-TBD-02` Standardized Field Lists for Change Formats:** What are the exact field-level validation rules for each of the 10 change formats (e.g., minimum salary step increments, mandatory attachments per change type)?
3. **`MOD1-TBD-03` Organizational Unit Topology:** Does the University support dual reporting lines (e.g., administrative reporting to Dean and functional reporting to Research Director), or is reporting strictly a single-parent hierarchy?
4. **`MOD1-TBD-04` Specific Report Format Definitions:** Official Excel/PDF templates for the initial report catalog referenced in Section 15 must be provided by the HR team.

---
*End of Module I Functional Requirements Specification.*
