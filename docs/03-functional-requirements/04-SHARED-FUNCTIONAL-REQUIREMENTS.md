# Shared Functional Requirements
## Functional Requirements Specification

**Document Identifier:** `DOC-03-FRD-SHR-04`  
**Phase:** Phase 3 — Functional Requirements Specification (Documentation-Only)  
**Location:** `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md`  
**Status:** Approved Functional Baseline  
**Authoritative Baseline:** [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) & [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)  
**Date:** September 29, 2026  

---

## 1. Purpose

The purpose of this document is to specify the **shared, cross-cutting functional requirements** that provide the operational foundation across Module I (Change Management), Module II (Recruitment & Selection), and Module III (Performance Management).

These shared capabilities ensure architectural cohesion, eliminate operational redundancy, preserve data integrity, and guarantee that all modules operate on a unified platform foundation.

---

## 2. Central Employee Data

- **`SHR-CDB-REQ-01` [A] Universal Master Reference:** All modules shall reference the Central Employee Database as the single source of truth for employee identity, employment status, designation, department, and reporting lines.
- **`SHR-CDB-REQ-02` [A] Elimination of Duplicate Re-Entry:** Master data created or updated in any module (e.g., candidate onboarding in Module II, appraisal promotion in Module III) shall update the central master record without manual re-keying.
- **`SHR-CDB-REQ-03` [B] Read-Only Shared Data Contracts:** Downstream modules (Module II, Module III) shall query master employee records via standardized in-process contracts without performing direct unvalidated database writes.

---

## 3. Organization Structure

- **`SHR-ORG-REQ-01` [A] Dynamic Unified Hierarchy:** The system shall maintain a single, dynamic organizational structure connecting Schools, Departments, Administrative Units, and parent-child supervisory relationships.
- **`SHR-ORG-REQ-02` [A] Event-Driven Real-Time Realignment:** Whenever an approved change in reporting authority, department transfer, or promotion occurs, the organizational structure shall update in real time.
- **`SHR-ORG-REQ-03` [B] Workflow Routing Dependency:** All approval routing engines (e.g., routing Group-D forms to HODs, routing KRA reviews to supervisors, routing academic requisitions to Deans) shall resolve recipient actors dynamically from this organizational hierarchy.

---

## 4. Digital Employee File

- **`SHR-FIL-REQ-01` [A] Consolidated Employee Dossier:** The system shall maintain an integrated Digital Employee File for every university employee.
- **`SHR-FIL-REQ-02` [A] Cross-Module Document Storage:** The Digital Employee File shall automatically ingest, index, and archive:
  1. *From Module I:* All approved service change request records, designation letters, and salary revision notices.
  2. *From Module II:* Initial CV, application forms, verified educational certificates, interview score sheets, and accepted LOI / Appointment Letters.
  3. *From Module III:* Group-D monthly/annual reports, KRA/KPI quarterly submissions, Faculty Self-Appraisals, ECM Score Sheets, evaluation matrices, and compensation outcome letters.
- **`SHR-FIL-REQ-03` [B] Immutable Historical Ledger:** Documents stored in the Digital Employee File shall be read-only and permanently linked to the employee's unique identifier.

---

## 5. Authentication

- **`SHR-AUT-REQ-01` [B] Unified Identity Service:** The system shall enforce authenticated access for all administrative users, academic leaders, faculty members, and staff.
- **`SHR-AUT-REQ-02` [C] Tokenized & Session Security:** Internal authentication shall utilize secure, encrypted sessions and JSON Web Tokens (JWT) with automatic expiration and revocation capabilities.
- **`SHR-AUT-REQ-03` [A] External Statutory Expert Access:** The system shall provide secure digital invitations and time-limited tokenized access for external statutory experts (such as SCM members), strictly restricted to assigned candidate dossiers.
- **`SHR-AUT-REQ-04` [E] Institutional SSO Provider (TBD):** Integration with the University's primary Single Sign-On (Google Workspace, Microsoft Entra ID / Office 365, or LDAP) is subject to `[E] TBD` pending University IT confirmation.

---

## 6. Role-Based Access Control (RBAC)

- **`SHR-RBC-REQ-01` [B] Hierarchical RBAC Framework:** The system shall enforce fine-grained role-based access control governing permissions across all modules.
- **`SHR-RBC-REQ-02` [B] Contextual Row-Level Data Scoping:**
  - *HOD Scope:* Access restricted strictly to departmental employees, candidates, and evaluations.
  - *Dean Scope:* Access restricted to school-wide academic workload, faculty evaluations, and requisitions.
  - *Executive Scope:* Institutional access across all schools and units (Pro-Chancellor, Senior Management, VP-Administration, Registrar).
  - *Employee Self-Service Scope:* Personal file, self-evaluations, and personal change requests only.

---

## 7. Workflow and Approval Framework

- **`SHR-WFL-REQ-01` [B] Universal Finite State Machine (FSM):** All multi-step processes across Modules I, II, and III shall execute on a standardized workflow engine enforcing explicit states and transition guards.
- **`SHR-WFL-REQ-02` [A] Immutable Approval Signing:** Every approval or rejection action shall record the acting user ID, role, exact timestamp, and mandatory written comments in the transaction audit log.
- **`SHR-WFL-REQ-03` [B] Delegation and Escalation Hooks:** The workflow engine shall support automated escalation when review SLAs are breached.

---

## 8. SLA and Timeline Management

- **`SHR-SLA-REQ-01` [A] Unified Timeline Engine:** The system shall provide a centralized SLA and timeline engine calculating and tracking all deadlines, countdown timers, grace periods, and cutoffs across all modules.
- **`SHR-SLA-REQ-02` [A] Automated Background Monitoring:** Background workers shall evaluate pending tasks continuously against configured SLA targets (e.g., 4-month semester triggers, 15-day submission windows, 7-day turnaround SLAs, 7th/10th of month cutoffs).
- **`SHR-SLA-REQ-03` [A] System-Enforced Hard Auto-Locks:** Where mandated by policy (such as Group-D evaluation submission by the 10th of the month), the SLA engine shall execute automated system lockouts and flag delinquent records.

---

## 9. Notifications

- **`SHR-NTF-REQ-01` [A] Multi-Channel Notification Infrastructure:** The system shall dispatch automated notifications across configured channels (transactional email, in-app dashboard alerts).
- **`SHR-NTF-REQ-02` [A] Event-Driven Notification Triggers:** Notifications shall automatically fire upon:
  1. *Task Assignment:* New form assigned to HOD, Dean, or Supervisor.
  2. *SLA Proximity Warnings:* Pre-due date reminders (e.g., before the 7th for Group-D, before 15-day MRF window expires, before 7-day Faculty self-appraisal deadline).
  3. *Overrun Escalations:* Alerts on timeline breaches.
  4. *Workflow Approvals:* Final clearance notifications.
- **`SHR-NTF-REQ-03` [C] Queue-Backed Dispatch:** Notification dispatch shall be offloaded to asynchronous background queues (BullMQ) to prevent blocking user web requests.

---

## 10. Document and File Management

- **`SHR-DOC-REQ-01` [C] Separation of Binary Storage & Database Metadata:** Binary files (CVs, degree certificates, research evidence, PDF letters) shall be stored in Object Storage; PostgreSQL shall store only metadata, access permissions, and checksums.
- **`SHR-DOC-REQ-02` [B/D] File Upload Security & Validation:** All file uploads shall undergo strict MIME-type validation and SHA-256 integrity hashing ([B] Logical Implication); the specific file size limit (e.g., max 10MB per document) is classified as **[D] Proposed Detail** (a proposed operational threshold subject to University IT confirmation, not an official university policy).
- **`SHR-DOC-REQ-03` [C] Time-Limited Presigned Access:** Authorized users shall access stored documents via secure, time-limited presigned URLs.

---

## 11. Audit and Version History

- **`SHR-AUD-REQ-01` [A] Universal Database Change Methodology:** The system shall enforce a uniform database change methodology across Modules I, II, and III, ensuring that every master change, requisition, candidate score, and evaluation review is time-stamped with a complete audit trail and version history.
- **`SHR-AUD-REQ-02` [A] Non-Destructive Versioning:** Data modifications shall never destructively overwrite prior states; historical states shall be retained with temporal validity timestamps.
- **`SHR-AUD-REQ-03` [B] Tamper-Evident Append-Only Logging:** Audit logs shall be write-once, append-only, and protected against modification by any system user.

---

## 12. Reporting

- **`SHR-REP-REQ-01` [A] Extensible Reporting Engine:** The system shall support a dynamic reporting engine allowing HR administrators to add, modify, or retire report formats over time without software code changes.
- **`SHR-REP-REQ-02` [A] Real-Time Report Execution:** All operational reports (employee rosters, open positions, appraisal funnels, TAT analytics) shall support real-time execution against current database state.
- **`SHR-REP-REQ-03` [B] Standard Export Formats:** Reports shall support structured data export in Excel (XLSX) and CSV formats.

---

## 13. Cross-Module Data Flow

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             CROSS-MODULE INTEGRATION FLOWS                                       │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. MODULE II ──► MODULE I: Accepted LOI / Onboarding ──► Creates Master Employee & Org Node      │
│ 2. MODULE I ──► MODULE II: Resignation Accepted ──► Starts Replacement Clock & Ad-Hoc MRF        │
│ 3. MODULE I ──► MODULE III: Master Data Sync (DOJ, Probation, Supervisor, Salary History)        │
│ 4. MODULE III ──► MODULE I: Appraisal Outcomes (Salary, Level, Designation) ──► Mod I Change     │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

- **`SHR-INT-REQ-01` [A] Module II to Module I (Onboarding Handshake):** When a candidate accepts an LOI and completes onboarding, the system shall automatically create the employee master record in the Central Employee Database and insert their position into the dynamic Org Chart.
- **`SHR-INT-REQ-02` [A] Module I to Module II (Resignation Trigger):** When an employee resignation is accepted by the School Dean in Module I, the system shall automatically notify Head HR and start the Module II urgent replacement countdown clock.
- **`SHR-INT-REQ-03` [A] Module I to Module III (Appraisal Master Sync):** Module III shall dynamically consume employee DOJ, probation completion status, current department, and reporting authority from Module I to drive appraisal eligibility and form routing.
- **`SHR-INT-REQ-04` [A] Module III to Module I (Appraisal Outcome Handshake):** Approved annual appraisal outcomes (KRA/KPI promotions, Group-D compensation adjustments, Faculty ECM revisions) shall feed directly into Module I as formal service condition change requests without duplicate manual re-entry.

---

## 14. ERP Integration Boundary

- **`SHR-ERP-REQ-01` [A] Complete ERP Reflection:** The Central Employee Database shall be fully reflected and synchronized with the University ERP.
- **`SHR-ERP-REQ-02` [C] Transactional Outbox Pattern:** Outbound ERP synchronization payloads shall be written to an immutable outbox table within the same transaction as the local master data update, ensuring reliable eventual consistency.
- **`SHR-ERP-REQ-03` [E] ERP Protocol & Endpoint (TBD):** The physical integration protocol (REST API, database-level staging sync, or SFTP batch files) is subject to `[E] TBD` pending University IT confirmation.

---

## 15. Configuration and Form Repository

- **`SHR-CFG-REQ-01` [A] Central Digital Form Catalog:** The system shall provide a centralized, HR-configurable repository for all standardized forms and templates:
  - Module I Change Formats (a through j)
  - Module II MRF, Teaching Load (Attachment 1), Vacancy Specification (Attachment 2), and RCS
  - Module III Group-D Evaluation Form (Enclosure 1), KRA Goal Sheets, Faculty Self-Appraisal Form, and ECM Score Sheet
- **`SHR-CFG-REQ-02` [A] Form Versioning with Audit Trail:** The HR Team shall be empowered to update evaluation parameters, KPIs, and scoring weights; each modification shall create a new versioned template with an immutable audit log, preserving historical evaluation integrity.

---

## 16. Common Functional Requirements

- **`SHR-CMN-REQ-01` [B] Internationalization & Date Standards:** All system timestamps shall be stored in UTC with display rendering in Local University Time (IST). Date formatting shall adhere to standard academic conventions.
- **`SHR-CMN-REQ-02` [B] Soft Deletion Standard:** Master records and transactional submissions shall never be physically deleted; records shall utilize soft-deletion flags (`deleted_at`) with complete audit trails.
- **`SHR-CMN-REQ-03` [B] Idempotent State Transitions:** All workflow state transition APIs shall be idempotent, preventing duplicate approvals or double-execution of financial compensation changes.

---

## 17. Requirement Traceability

| Functional Requirement ID | Scope Category | Authoritative Baseline Traceability ID | Downstream Phase Dependency |
|---|---|---|---|
| `SHR-CDB-REQ-01` to `03` | Central Master DB | `MOD1-CDB-01` | Phase 4 (ERD: `employees`), Phase 6 (API) |
| `SHR-ORG-REQ-01` to `03` | Dynamic Org Chart | `MOD1-ORG-01` | Phase 4 (ERD: hierarchy DAG), Phase 7 (UI) |
| `SHR-FIL-REQ-01` to `03` | Digital Employee File | `MOD1-FIL-01`, `MOD3-GD-ANN-01` | Phase 4 (ERD: `employee_dossier_files`) |
| `SHR-AUT-REQ-01` to `04` | Authentication & Security | `MOD2-SEL-FAC-01` | Phase 8 (Security: IAM & Magic Link Tokens) |
| `SHR-RBC-REQ-01` to `02` | RBAC & Data Scoping | Universal Baseline | Phase 8 (Security: Role-to-Permission Matrix) |
| `SHR-WFL-REQ-01` to `03` | Workflow Engine | Universal Baseline | Phase 5 (Workflows: Generic FSM Specification) |
| `SHR-SLA-REQ-01` to `03` | SLA & Timeline Engine | `MOD2-MP-FAC-01`, `MOD3-GD-EVAL-01` | Phase 5 (Workflows: SLA countdown engine) |
| `SHR-NTF-REQ-01` to `03` | Notifications | Universal Baseline | Phase 6 (API: Notification dispatch queue) |
| `SHR-DOC-REQ-01` to `03` | Document Management | Universal Baseline | Phase 4 (ERD: `document_metadata`), Phase 8 (Storage) |
| `SHR-AUD-REQ-01` to `03` | Audit & Versioning | `MOD1-DAT-01` | Phase 4 (ERD: `audit_logs`, `entity_versions`) |
| `SHR-REP-REQ-01` to `03` | Dynamic Reporting | `MOD1-REP-01`, `MOD2-REP-01` | Phase 7 (UI: Reporting dashboard) |
| `SHR-INT-REQ-01` to `04` | Cross-Module Data Flows | `MOD2-ONB-01`, `MOD3-KRA-INT-01` | Phase 5 (Workflows: Event-driven handshakes) |
| `SHR-ERP-REQ-01` to `03` | ERP Outbox Reflection | `MOD1-CDB-01` | Phase 4 (ERD: `erp_outbox`), Phase 6 (API) |
| `SHR-CFG-REQ-01` to `02` | Form Repository | `MOD3-GD-EVAL-01` | Phase 4 (ERD: `form_templates_jsonb`) |

---

## 18. Open Questions / TBD

The following cross-cutting items are officially classified as **`[E] TBD / OPEN DECISION`** requiring confirmation from University leadership:

1. **`SHR-TBD-01` Enterprise Identity Provider (IdP):** What specific institutional SSO mechanism will be integrated (Google Workspace, Microsoft Entra ID / 365, or campus LDAP/SAML)?
2. **`SHR-TBD-02` Outbound Notification Gateways:** What are the host configurations and credentials for the university's outbound SMTP relay server? Will SMS / WhatsApp gateway APIs be provided for high-priority reminders?
3. **`SHR-TBD-03` Object Storage Target Infrastructure:** Will Object Storage be hosted on an on-premises S3-compatible cluster (such as MinIO / Ceph) or an external managed cloud object store (AWS S3 / Azure Blob)?
4. **`SHR-TBD-04` Document Retention & Archival Policies:** What is the statutory retention duration for rejected candidate CVs, historical evaluation scorecards, and audit logs under university regulations?

---
*End of Shared Functional Requirements Specification.*
