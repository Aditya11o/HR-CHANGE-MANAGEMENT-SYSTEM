# Requirements TBD and Open Decisions Log
## University HR Change Management & Automation System

**Document Identifier:** `DOC-01-TBD-05`  
**Phase:** Phase 1 — Requirements Engineering & Specification (Documentation-Only)  
**Location:** `docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`  
**Status:** Approved Controlled TBD Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Document Purpose

This document provides a formal, controlled register of all unresolved requirements, ambiguous specifications, missing physical templates, and open institutional policy decisions across the University HR Change Management & Automation System.

In strict compliance with enterprise engineering standards and the **Anti-Invention Mandate**, missing business rules, mathematical weights, or third-party platforms are **never guessed or fabricated**. Instead, they are cataloged herein under classification **`[E] TBD / Open Decision`**, with precise attribution, operational impact analysis, and assigned institutional decision owners.

---

## 2. Summary of Open Items & Catalogue Mapping

| TBD ID | Topic / Domain | Affected Module | Decision Owner | Requirement Catalogue Mapping | Status |
|---|---|---|---|---|---|
| `REQ-TBD-01` | ERP Synchronization Architecture & Protocol | Module I / Shared | University IT / ERP Team | Standalone Requirement **`REQ-EXT-03`** (`[E]`) | **OPEN** |
| `REQ-TBD-02` | Standardized Attachment & Enclosure Schemas | Modules II & III | HR Department / Deans | Qualifies **`REQ-DOC-02`** & **`REQ-DOC-03`** | **OPEN** |
| `REQ-TBD-03` | Staff Appraisal Track Boundary Definitions | Modules II & III | HR Leadership / Registrar | Qualifies **`REQ-MOD3-10`** & **`REQ-MOD3-14`** | **OPEN** |
| `REQ-TBD-04` | TNU Protocol Parameter Weights & Quorums | Module III (Faculty) | Academic Council / Registrar | Qualifies **`REQ-MOD2-15`** & **`REQ-MOD3-18`** | **OPEN** |
| `REQ-TBD-05` | Pre-Defined Compensation Revision Slabs | Module III (GD & Fac) | Senior Management / Finance | Qualifies **`REQ-MOD3-09`** & **`REQ-MOD3-19`** | **OPEN** |
| `REQ-TBD-06` | Resignation Upstream Intake & Clearance | Modules I & II | HR Leadership / Deans | Qualifies **`REQ-MOD2-08`** & **`REQ-INT-02`** | **OPEN** |
| `REQ-TBD-07` | Enterprise SSO & External Expert Access | Enterprise Security | University IT / Security | Standalone Requirements **`REQ-EXT-04`** & **`REQ-EXT-05`** (`[E]`) | **OPEN** |
| `REQ-TBD-08` | LOI vs. Formal Appointment Letter Lifecycle | Module II (Onboarding) | HR Department / Legal | Qualifies **`REQ-MOD2-19`** & **`REQ-DOC-04`** | **OPEN** |
| `REQ-TBD-09` | Administrative Allowance for Secondary Roles | Module I (Format h) | HR Leadership / Finance | Qualifies **`REQ-MOD1-13`** & **`REQ-MOD1-14`** | **OPEN** |
| `REQ-TBD-10` | Outbound Communication Gateways & Relays | Shared Infrastructure | University IT / Systems | Qualifies **`REQ-SLA-10`** | **OPEN** |
| `REQ-TBD-11` | Document Retention & Archival Lifecycle | Enterprise Compliance | Registrar / Legal Counsel | Qualifies **`REQ-AUD-01`** & **`REQ-DOC-06`** | **OPEN** |

---

## 3. Detailed Itemization of Open Items

### `REQ-TBD-01`: ERP Synchronization Architecture & Protocol
- **Topic:** University ERP Platform Identification and Outbound/Inbound Sync Specifications.
- **Requirement Reference:** Module I Brief, Structure (1): *"This database shall be fully reflected in our ERP."*
- **Why It Is Unresolved:** The requirement brief mandates complete ERP reflection but does not state which ERP software is deployed (e.g., SAP ERP, Oracle PeopleSoft, Ellucian Banner, or a custom in-house ERP) or the technical integration protocol (RESTful webhooks, direct database staging tables, or scheduled SFTP batch flat-files).
- **Affected Module / Document:** Module I Core DB, `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md` (`SHR-ERP-REQ-03`).
- **Decision Owner:** University Chief Information Officer (CIO) / ERP Technical Lead.
- **Dependency & Downstream Impact:** Blocks detailed interface specifications in Phase 09 (API Specifications) and outbound payload modeling in Phase 08 (Database ERD).
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-02`: Standardized Attachment & Enclosure Schemas
- **Topic:** Field-Level Schemas and Physical Templates for Recruitment and Appraisal Enclosures.
- **Requirement Reference:**  
  - Module II: Attachment 1 (Teaching Load), Attachment 2 (Vacancy Spec), Attachment 3 (Open Positions Tracker), Enclosure 1 (MRF), Recruiter Calling Sheet (RCS).
  - Module III: Enclosure 1 (Group-D Evaluation Form), Enclosure 2 (Group-D Monthly/Annual Report), KRA Goal Sheet, Enclosure 1 (Faculty Self-Appraisal), Enclosure 2 (ECM Score Sheet), Enclosure 3 (Evaluation Matrix).
- **Why It Is Unresolved:** The source briefs reference these attachments by formal titles and describe their workflow roles, but physical copies of the Excel, Word, or PDF templates were not included in the source requirements.
- **Affected Module / Document:** Modules II and III, `docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`, `03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`.
- **Decision Owner:** Head of Human Resources / Academic Deans Committee.
- **Dependency & Downstream Impact:** Field-level database column definitions in Phase 08 (Database ERD) and dynamic form rendering schemas in Phase 10 (UI/UX Design System) require these exact templates.
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-03`: Staff Appraisal Track Boundary Definitions
- **Topic:** Workflow Routing and Track Allocation for Mid-Level Academic and Technical Staff.
- **Requirement Reference:**  
  - Module II, Section 1(a) categorizes Teaching Associates, Technical Assistants, and Laboratory Technicians under the Academic hiring umbrella.
  - Module III defines three distinct appraisal tracks: Group-D / Band I Staff, General Staff KRA/KPI, and Faculty Annual Appraisal via ECM.
- **Why It Is Unresolved:** The briefs do not specify which appraisal workflow applies to Lab Technicians, Technical Assistants, and Teaching Associates. It is unclear whether they participate in the quarterly KRA/KPI review, the Faculty ECM route, or an adapted technical staff evaluation.
- **Affected Module / Document:** Module III Performance Management, `docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`.
- **Decision Owner:** Registrar / Head of Human Resources.
- **Dependency & Downstream Impact:** Determines workflow state machine routing rules in Phase 06 and user role definitions in Phase 05.
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-04`: TNU Protocol Parameter Weights & Committee Quorums
- **Topic:** Mathematical Weightages of the TNU Protocol and Statutory Quorum Compositions.
- **Requirement Reference:**  
  - Module III, Section 5(b): *"compile an evaluation matrix based on the configured TNU Protocol parameters together with the Faculty member's previous increment details..."*
  - Module II, Selection A(a): *"digital invitations to SCM members (including the external subject expert)..."*
- **Why It Is Unresolved:** The source briefs mandate using the "TNU Protocol" but do not provide the mathematical scoring formulas, parameter percentage weights (e.g., Teaching Load vs. Research Publications vs. Student Feedback vs. Institutional Service), or statutory minimum quorums for SCM and ECM meetings.
- **Affected Module / Document:** Module II Selection and Module III Faculty Appraisal.
- **Decision Owner:** Vice Chancellor / Academic Council / Registrar.
- **Dependency & Downstream Impact:** Blocks evaluation matrix computation algorithms in Phase 08 (Database) and scoring calculation APIs in Phase 09.
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-05`: Pre-Defined Compensation Revision Slabs
- **Topic:** Quantitative Compensation Slabs for Group-D and Faculty Performance Revisions.
- **Requirement Reference:**  
  - Module III, Group-D Section 5(a): *"review the completed Annual Report against Management's pre-defined compensation slabs..."*
  - Module III, Faculty Section 6(a): *"Management's final decision on the revision of the Faculty member's compensation..."*
- **Why It Is Unresolved:** The briefs establish that Management makes compensation revision decisions based on pre-defined slabs, but the monetary values, percentage increment brackets, or step-grade tables are not documented.
- **Affected Module / Document:** Module III Sub-Systems 1 and 3.
- **Decision Owner:** Senior Management / University Finance Committee.
- **Dependency & Downstream Impact:** Financial calculation rules in Phase 06 and compensation review UI displays in Phase 10.
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-06`: Resignation Upstream Intake & Clearance Interface
- **Topic:** Employee Self-Service Resignation Initiation and Clearance Processing in Module I.
- **Requirement Reference:** Module II, Section 1(i): *"Replacement clock starts on resignation acceptance by the School Dean, auto-notifying Head HR."*
- **Why It Is Unresolved:** The requirement specifies that the replacement clock starts upon the Dean's acceptance of a resignation, but does not define how the resignation is initially submitted in Module I (e.g., employee self-service submission, administrative entry by HR, or paper memorandum upload) or whether inter-departmental clearances (library, lab, finance) precede the replacement trigger.
- **Affected Module / Document:** Module I Core DB and Module II Manpower Planning.
- **Decision Owner:** Head of Human Resources.
- **Dependency & Downstream Impact:** State machine design in Phase 06 (Workflows) and form definitions in Phase 10 (UI/UX).
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-07`: Enterprise SSO & External Expert Access
- **Topic:** Identity Provider Protocol and Secure Authentication for External Selection Committee Experts.
- **Requirement Reference:** Module II, Selection Workflow A(a): *"digital invitations to SCM members (including the external subject expert)..."*
- **Why It Is Unresolved:** The university's central Identity Provider (Google Workspace, Microsoft Entra ID / 365, or campus LDAP/Active Directory) is not specified. Furthermore, external subject experts (who do not possess institutional email addresses) require a secure access mechanism (such as time-limited signed tokens or OTP portals) that has not been formally selected.
- **Affected Module / Document:** Enterprise Security, `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md` (`SHR-TBD-01`).
- **Decision Owner:** University IT Infrastructure / Security Team.
- **Dependency & Downstream Impact:** Security architecture and IAM specifications in Phase 11.
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-08`: LOI vs. Formal Appointment Letter Lifecycle
- **Topic:** Contractual Lifecycle and Handoff between Letter of Intent (LOI) and Appointment Letter.
- **Requirement Reference:** Module II Selection Workflows A(e), B(b), and urgent replacement Section 1(i).
- **Why It Is Unresolved:** The brief specifies auto-generating a Letter of Intent (LOI) upon Management approval, and in urgent replacements mentions generating an Offer Letter. It does not define whether the LOI is the sole pre-joining instrument, or whether a distinct formal Appointment Letter is generated post-document verification upon physical joining.
- **Affected Module / Document:** Module II Selection & Onboarding.
- **Decision Owner:** HR Department / University Legal Counsel.
- **Dependency & Downstream Impact:** Pre-onboarding workflow FSM in Phase 06 and PDF templating in Phase 09.
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-09`: Administrative Allowance for Additional Responsibilities
- **Topic:** Policy Rules Governing Financial Allowances for Secondary Roles.
- **Requirement Reference:** Module I Brief, Structure 3(h) / `MOD1-CHG-REQ-15`.
- **Why It Is Unresolved:** While assigning additional responsibilities (Dean, HOD, Proctor, Warden) is explicitly supported via Format (h), whether specific roles carry mandatory administrative allowances or honorariums is subject to university service rules and is not defined in the source briefs.
- **Affected Module / Document:** Module I Core DB, `docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md` (`MOD1-CHG-REQ-15`).
- **Decision Owner:** HR Leadership / Finance Directorate.
- **Dependency & Downstream Impact:** Field mapping in Format 3(h) and salary ledger integration in Phase 08.
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-10`: Outbound Communication Gateways & Relays
- **Topic:** Host Configurations and Gateways for Institutional Email, SMS, and WhatsApp Reminders.
- **Requirement Reference:** Universal SLA and Notification Engine (`SHR-NTF-REQ-01` to `03`).
- **Why It Is Unresolved:** The requirement briefs mandate multi-tier reminder sequences and notifications, but specific SMTP host settings, sender aliases, or SMS/WhatsApp gateway APIs have not been provided.
- **Affected Module / Document:** Shared Notification Engine, `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md` (`SHR-TBD-02`).
- **Decision Owner:** University Systems Administrator / IT Support.
- **Dependency & Downstream Impact:** Phase 12 (Notifications & SLA Engine).
- **Status:** **`[E] TBD / OPEN`**

---

### `REQ-TBD-11`: Document Retention & Archival Lifecycle
- **Topic:** Statutory Retention Schedules for Candidate CVs, Scorecards, and Audit Logs.
- **Requirement Reference:** Universal Compliance and Document Management (`SHR-DOC-REQ-01` to `03`, `SHR-AUD-REQ-01`).
- **Why It Is Unresolved:** Regulatory retention periods (e.g., minimum years to retain rejected candidate CVs, SCM evaluation marks, or historical employee change logs) under university bylaws or national data protection laws have not been codified.
- **Affected Module / Document:** Enterprise Compliance & Storage, `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md` (`SHR-TBD-04`).
- **Decision Owner:** University Registrar / Legal Compliance Directorate.
- **Dependency & Downstream Impact:** Data archival and retention cleanup scripts in Phase 08 and Phase 11.
- **Status:** **`[E] TBD / OPEN`**

---

## 4. Reconciliation with Requirement Catalogue (`DOC-01-CAT-02`)

The eleven (11) open items documented in this register correspond directly to the system requirements established in [`02-REQUIREMENT-CATALOGUE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md) as follows:

1. **Standalone Atomic System Requirements (`[E]` in Catalogue - 3 items):**
   - `REQ-TBD-01` is formally catalogued as **`REQ-EXT-03`** (ERP Synchronization Physical Protocol & Transport Architecture).
   - `REQ-TBD-07` is formally catalogued as two distinct security integration requirements:
     - **`REQ-EXT-04`** (Institutional Single Sign-On Identity Provider Integration Protocol).
     - **`REQ-EXT-05`** (External Subject Expert Remote Evaluation Access Mechanism).

2. **Policy, Formula, and Schema Open Decisions (8 items):**
   The remaining eight items represent institutional policy rules, mathematical formulas, or physical document schemas that qualify existing catalogue requirements rather than functioning as separate software requirements:
   - `REQ-TBD-02` parameterizes `REQ-DOC-02` and `REQ-DOC-03` (field-level template schemas).
   - `REQ-TBD-03` parameterizes `REQ-MOD3-10` and `REQ-MOD3-14` (appraisal track boundary definitions).
   - `REQ-TBD-04` parameterizes `REQ-MOD2-15` and `REQ-MOD3-18` (TNU protocol scoring weights and committee quorums).
   - `REQ-TBD-05` parameterizes `REQ-MOD3-09` and `REQ-MOD3-19` (pre-defined compensation revision slabs).
   - `REQ-TBD-06` parameterizes `REQ-MOD2-08` and `REQ-INT-02` (resignation upstream intake interface).
   - `REQ-TBD-08` parameterizes `REQ-MOD2-19` and `REQ-DOC-04` (LOI vs. formal appointment letter lifecycle).
   - `REQ-TBD-09` parameterizes `REQ-MOD1-13` and `REQ-MOD1-14` (administrative allowances for secondary roles).
   - `REQ-TBD-10` parameterizes `REQ-SLA-10` (outbound email SMTP relay and SMS gateway credentials).
   - `REQ-TBD-11` parameterizes `REQ-AUD-01` and `REQ-DOC-06` (statutory document retention and archival schedules).

This explicit structure guarantees that every open item is accounted for without inflating the count of atomic system requirements.

---
*End of Document — Requirements TBD and Open Decisions Log.*
