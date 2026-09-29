# Combined Stakeholder Requirement Delta Review
## Unified Reconciliation of Post-Release Stakeholder Narratives and Complete Workflows Across Modules I, II, and III

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md` |
| **System Phase** | Phase 2 Post-Release / Unified Stakeholder Delta Reconciliation |
| **Project** | University HR Change Management & Automation System |
| **Status** | `UNIFIED DELTA REVIEW COMPLETE — AWAITING STAKEHOLDER DECISION` |
| **Scope** | Enterprise-Wide Synthesis of Post-Release Stakeholder Materials Across Module I, Module II, and Module III |
| **Primary Comparison Set** | `docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md`; `docs/01-requirements/08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md`; Original Official Module I, II, III Requirement PDFs; Newly Supplied Stakeholder Narratives & Workflow Diagrams; `PROJECT_REQUIREMENTS_ANALYSIS.md`; `docs/01-requirements/`; `docs/02-business-process/`; `docs/03-functional-requirements/`; `TECHNOLOGY_ARCHITECTURE_BASELINE.md` |
| **File Safety** | Strictly Analysis-Only — Zero Existing Baseline Files Modified; Baseline Remains Frozen |

---

## 1. Purpose

This document provides the authoritative, unified **Stakeholder Requirement Delta Review** for the University HR Change Management & Automation System. It synthesizes, normalizes, and reconciles the detailed findings of the separate post-release delta analyses performed for:
- **Module I (HR Change Management):** Evaluated in `docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md`.
- **Module II (Recruitment & Selection Automation):** Evaluated in `docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md`.
- **Module III (Performance Management Automation):** Evaluated in `docs/01-requirements/08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md`.

The primary objectives of this unified review are:
1. **Consolidate all candidate changes, clarifications, extensions, and exceptions** across the entire university system into a single canonical change register.
2. **De-duplicate cross-cutting platform capabilities** (such as Central Employee Database master authority, Digital Employee Dossier integration, immutable audit trails, and configurable reporting) that appear repeatedly across individual module narratives and diagrams.
3. **Analyze cross-module lifecycle impacts** across all three functional boundaries (Module I $\leftrightarrow$ Module II, Module I $\leftrightarrow$ Module III, and Module II $\leftrightarrow$ Module III).
4. **Formulate a definitive Conflict Matrix** identifying every policy tension or divergence between the original official requirement PDFs and the new stakeholder materials, marking them strictly as `NEEDS STAKEHOLDER CONFIRMATION`.
5. **Establish a Master Stakeholder Confirmation List** and a **Master Consolidated TBD Register** to govern the upcoming stakeholder review session.
6. **Provide a clear, controlled change sequence** and baseline count assessment *before* any updates are applied to established project baselines.

---

## 2. Baseline Status

The project requirements and business process baselines were formally established, audited, and frozen prior to the receipt of today's stakeholder materials:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                              FROZEN PROJECT BASELINE STATUS                            │
├───────────────────────────────────┬────────────────────────────────────────────────────┤
│ Phase 1 Requirement Catalogue     │ docs/01-requirements/02-REQUIREMENT-CATALOGUE.md   │
│                                   │ (Frozen at 104 Atomic Requirements: 88 [A], 8 [B], │
│                                   │ 4 [C], 1 [D], 3 [E])                               │
├───────────────────────────────────┼────────────────────────────────────────────────────┤
│ Phase 1 Official TBD Register     │ docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN- │
│                                   │ DECISIONS.md (Frozen at 11 TBD Items: REQ-TBD-01   │
│                                   │ through REQ-TBD-11)                                │
├───────────────────────────────────┼────────────────────────────────────────────────────┤
│ Phase 2 Business Process Baseline │ docs/02-business-process/ (Frozen at 59 Business   │
│                                   │ Processes, 60 Business Rules, Master SLA Matrix)   │
├───────────────────────────────────┼────────────────────────────────────────────────────┤
│ Phase 3 Functional Requirements   │ docs/03-functional-requirements/ (Frozen at MOD1,   │
│                                   │ MOD2, MOD3, and Shared FRDs)                       │
├───────────────────────────────────┼────────────────────────────────────────────────────┤
│ Approved Technology Baseline      │ TECHNOLOGY_ARCHITECTURE_BASELINE.md & ADR-001      │
│                                   │ (Approved Stack: Next.js, NestJS, PostgreSQL)      │
└───────────────────────────────────┴────────────────────────────────────────────────────┘
```

> **Mandatory Governance Invariant:**  
> The existing baseline remains the **frozen historical baseline**. Zero baseline files have been modified. No candidate change, new requirement ID, or TBD item identified herein shall be incorporated into the official documentation until formal stakeholder confirmation is completed.

---

## 3. Stakeholder Materials Reviewed

This unified review synthesizes four new primary stakeholder assets provided by university leadership and mentors:

1. **Asset 1 — Module I Complete Narrative & Workflow:**  
   `Module_1_HR_Change_Management_Narrative_Complete.docx` (and companion PDF) with embedded visual workflow diagram `Module 1 – HR Change Management & Automation System Complete Workflow` (15 stages, pre-validation checks, 2-level approval branches, and 7 explicit exception conditions).
2. **Asset 2 — Module II Complete Narrative & Workflow:**  
   `Module_2_Recruitment_Selection_Narrative_Complete.docx` (and companion PDF) with embedded visual workflow diagram `Module 2 – Recruitment & Selection Automation System Complete Workflow` (21 numbered stages, dual academic/non-academic routing, urgent replacement flow, Step 13 Management Approval for Interview, and 5-stage pre-onboarding milestones).
3. **Asset 3 — Module III Complete Workflow Diagram:**  
   `Module_3_Performance_Management_Automation_System.jpeg` visualising Track A (Group-D Monthly/Annual), Track B (General Staff Quarterly KRA/KPI), Track C (Faculty Monthly ECM with 7 outcome types), and Shared Sections D, E, F, G.
4. **Intermediate Review Artifacts:**  
   `docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md` (Module I & II Deltas) and `docs/01-requirements/08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md` (Module III Deltas).

---

## 4. Analysis Method & Classification Taxonomy

All findings from the intermediate reports were extracted, normalized, and classified into standardized analytical categories:

| Analytical Category | Operational Definition | Baseline Action |
|---|---|---|
| **ALREADY COVERED** | The concept, role, rule, or timeline is already fully captured in existing documentation without substantive discrepancy. | Reaffirms baseline design; no update required. |
| **NEW EXPLICIT REQUIREMENT** | The new material introduces a concrete requirement, governance gate, or role not previously specified in the official PDFs. | Candidate ID assigned (`CAND-REQ-*`); pending approval. |
| **CLARIFICATION** | The requirement existed, but the new material provides crucial operational detail, explicit sub-steps, or clearer interpretation. | Refine existing process or FRD description upon approval. |
| **POTENTIAL CONFLICT** | The new material appears inconsistent with an existing documented requirement, role assignment, or timing. | Flagged in Conflict Matrix; marked `NEEDS STAKEHOLDER CONFIRMATION`. |
| **NEW EXCEPTION / SPECIAL CONDITION** | The new material introduces an explicit alternate path, exception flow, or edge case not previously documented. | Incorporate into exception catalogue and workflow branching logic. |
| **TBD / INCOMPLETE** | The new material names an important concept or policy condition, but explicitly notes that detailed rules, formulas, or thresholds must not be invented by developers. | Catalogued in Master TBD Register (`REQ-TBD-*`). |

Project classification tags preserve the established standard:
- `[A]` Explicit Requirement (directly stated in source materials)
- `[B]` Logical Implication (structurally necessary deduction)
- `[C]` Approved Technical Decision (architecture baseline)
- `[D]` Proposed Detail (provisional implementation specification)
- `[E]` TBD / Open Decision (unresolved policy or formula)

---

## 5. Consolidated Delta Register (Normalized Master Catalogue)

The following master register normalizes all 37 individual delta findings across Module I (9 items), Module II (13 items), and Module III (15 items) into a unified reference catalogue:

| Delta ID | Module | Stakeholder Source Element | Delta Classification | Req Class | Existing Traceability (REQ / BP / FRD) | Impact Level | Primary Documentation Layer Affected | TBD / Confirmation Required? |
|---|---|---|---|---|---|---|---|---|
| **`DLT-01`** | Mod I | Box 3: Multi-factor Pre-Submission Validation Checks | NEW EXPLICIT REQUIREMENT | `[A]` | `REQ-MOD1-12` / `BP-M1-004` / `MOD1-CHG-REQ-12` | MEDIUM | `01-reqs`, `02-business-process`, `03-frd` | No (`CAND-REQ-M1-VAL`) |
| **`DLT-02`** | Mod I | Box 4: HR Review Clarification Loop with Comments | CLARIFICATION | `[A]` | `REQ-MOD1-06` / `BP-M1-005` / `MOD1-APP-REQ-02` | LOW | `02-business-process` | No (`CAND-REQ-M1-CLAR`) |
| **`DLT-03`** | Mod I | Box 5: Management Clarification Return to HR | CLARIFICATION | `[A]` | `REQ-MOD1-06` / `BP-M1-006` / `MOD1-APP-REQ-03` | LOW | `02-business-process` | No |
| **`DLT-04`** | Mod I | Box 6 & 7: "Approved (Yet to be Effective)" & "Scheduled" Statuses | CLARIFICATION | `[A]` | `REQ-MOD1-07` / `BP-M1-007` / `MOD1-EFF-REQ-01` | LOW | `02-business-process`, Architecture | No |
| **`DLT-05`** | Mod I | Box 12, Para 56–63: Multiple / Conflicting Changes Policy | TBD / INCOMPLETE | `[E]` | None / `BP-M1-004` / `MOD1-CHG-REQ-12` | HIGH | `01-reqs`, `05-tbds`, `03-frd` | **YES (`REQ-TBD-12`)** |
| **`DLT-06`** | Mod I | Box 12, Para 63: Change Cancellation / Withdrawal Policy | TBD / INCOMPLETE | `[E]` | None / `BP-M1-004` / None | MEDIUM | `01-reqs`, `05-tbds`, `02-business-process` | **YES (`REQ-TBD-13`)** |
| **`DLT-07`** | Mod I | Para 20: Standardized Return & Rejection Reason Taxonomy | TBD / INCOMPLETE | `[E]` | `REQ-MOD1-06` / `BP-M1-005` / `MOD1-APP-REQ-04` | LOW | `01-reqs`, `05-tbds` | **YES (`REQ-TBD-14`)** |
| **`DLT-08`** | Mod I | Box 2: Authorized Initiator Scope ("HR/Admin/Dept per policy") | CLARIFICATION | `[A]` | `REQ-MOD1-05` / `BP-M1-004` / `MOD1-CHG-REQ-01` | MEDIUM | `01-reqs`, `02-business-process` | Confirmation (CONF-01) |
| **`DLT-09`** | Mod I | Box 14: Configurable Dynamic Reporting (Add/Delete reports) | ALREADY COVERED | `[A]` | `REQ-REP-01`–`04` / `BP-M1-010` / `MOD1-REP-REQ-01` | NONE | None (Reaffirms design) | No |
| **`DLT-10`** | Mod II | Step 1, Para 5: Associate Dean (Academics) Manpower Planning Role | NEW EXPLICIT REQUIREMENT | `[A]` | `REQ-MOD2-02` / `BP-M2-ACAD-001` / `MOD2-MPL-REQ-01` | MEDIUM | `01-reqs`, `02-business-process` | Confirmation (CONF-02) |
| **`DLT-11`** | Mod II | Step 1, 2, 6, 14A: Lab Technician Placed in Academic Track | POTENTIAL CONFLICT | `[A]` | `REQ-MOD2-01` / `BP-M2-ACAD-001` / `MOD2-REC-REQ-01` | HIGH | `01-reqs`, `02-business-process`, `03-frd` | **CONFIRMATION (CONF-03)** |
| **`DLT-12`** | Mod II | Step 2, Para 8: Academic Vetting Split (Assigned to Assoc Dean) | POTENTIAL CONFLICT | `[A]` | `REQ-MOD2-05` / `BP-M2-ACAD-003` / `MOD2-MPL-REQ-03` | HIGH | `01-reqs`, `02-business-process` | **CONFIRMATION (CONF-04)** |
| **`DLT-13`** | Mod II | Step 2: Vetting Clarification Return Loop | CLARIFICATION | `[A]` | `REQ-MOD2-05` / `BP-M2-ACAD-003` / `MOD2-MPL-REQ-03` | LOW | `02-business-process` | No |
| **`DLT-14`** | Mod II | Step 3: Joint Consolidation by Assoc Dean (Academics) / Head HR | CLARIFICATION | `[A]` | `REQ-MOD2-06` / `BP-M2-ACAD-004` / `MOD2-MPL-REQ-04` | LOW | `02-business-process` | No |
| **`DLT-15`** | Mod II | Step 6: MRF Creation Timing Asymmetry (Faculty post-approval) | CLARIFICATION | `[A]` | `REQ-MOD2-06` / `BP-M2-ACAD-006` / `MOD2-MPL-REQ-04` | MEDIUM | `02-business-process`, `03-frd` | No |
| **`DLT-16`** | Mod II | Step 5A: Urgent MRF Fast-Track Vetting & Pro-Chancellor Approval | CLARIFICATION / EXCEPTION | `[A]` | `REQ-MOD2-03` / `BP-M2-URG-001` / `MOD2-URG-REQ-01` | MEDIUM | `02-business-process` | No |
| **`DLT-17`** | Mod II | Step 9: Ingestion Scope (Internshala, Instagram, Facebook) | CLARIFICATION | `[A]` | `REQ-MOD2-19` / `BP-M2-TRK-001` / `MOD2-CDB-REQ-01` | LOW | `02-business-process` | No |
| **`DLT-18`** | Mod II | Para 22: Shortlisting Disqualification Algorithms TBD | TBD / INCOMPLETE | `[E]` | `REQ-MOD2-14` / `BP-M2-ACAD-007` / `MOD2-SCM-REQ-02` | MEDIUM | `01-reqs`, `05-tbds` | **YES (`REQ-TBD-15`)** |
| **`DLT-19`** | Mod II | Step 13: Mandatory Management Approval for Interview | NEW EXPLICIT REQUIREMENT | `[A]` | None / `BP-M2-ACAD-008` / `MOD2-SEL-REQ-01` | HIGH | `01-reqs`, `02-business-process`, `03-frd` | **CONFIRMATION (CONF-05)** |
| **`DLT-20`** | Mod II | Step 14A, Para 30: Online Interview Panel Scheduling as Default | CLARIFICATION | `[A]` | `REQ-MOD2-13` / `BP-M2-ACAD-008` / `MOD2-SCM-REQ-01` | LOW | `02-business-process` | No |
| **`DLT-21`** | Mod II | Step 14A: Post-SCM Formal HR Recommendation Review | NEW EXPLICIT REQUIREMENT | `[A]` | `REQ-MOD2-14` / `BP-M2-ACAD-010` / `MOD2-SCM-REQ-02` | MEDIUM | `01-reqs`, `02-business-process` | Confirmation (CONF-06) |
| **`DLT-22`** | Mod II | Step 18, Para 48–50: Five-Stage Pre-Onboarding Milestone Tracking | NEW EXPLICIT REQUIREMENT | `[A]` | `REQ-MOD2-18` / `BP-M2-ACAD-012` / `MOD2-YTJ-REQ-01` | MEDIUM | `01-reqs`, `02-business-process`, `03-frd` | **YES (`REQ-TBD-16`)** |
| **`DLT-23`** | Mod III | Box 1: Form Repository Role-Specific KPI Configuration | CLARIFICATION | `[A]` | `REQ-MOD3-01` / `BP-M3-GD-001` / `MOD3-GD-REQ-01` | LOW | `02-business-process`, `03-frd` | No |
| **`DLT-24`** | Mod III | Box 2 & 3: Monthly Group-D Routing to HOD (Completes & Submits) | POTENTIAL CONFLICT | `[A]` | `REQ-MOD3-01` / `BP-M3-GD-002` / `MOD3-GD-REQ-01` | MEDIUM | `02-business-process`, `03-frd` | **CONFIRMATION (CONF-07)** |
| **`DLT-25`** | Mod III | Box 4: Exclusive VP-Administration Approval | ALREADY COVERED | `[A]` | `REQ-MOD3-04` / `BP-M3-GD-004` / `MOD3-GD-REQ-04` | NONE | None (Reaffirms design) | No |
| **`DLT-26`** | Mod III | Box 5: Submission Timeline (7th Due, 10th Grace, Auto-Lock) | ALREADY COVERED | `[A]` | `REQ-MOD3-01`–`03` / `BP-M3-GD-002`–`003` | NONE | None (Reaffirms design) | No |
| **`DLT-27`** | Mod III | Box 5: "Not Submitted" Status with Mandatory Reason Capture | CLARIFICATION / EXCEPTION | `[A]` | `REQ-MOD3-03` / `BP-M3-GD-003` / `MOD3-GD-REQ-03` | LOW | `01-reqs`, `02-business-process`, `05-tbds` | **YES (`REQ-TBD-20`)** |
| **`DLT-28`** | Mod III | Box 7: Annual Report at 1-Year DOJ with Weighted Average | ALREADY COVERED | `[A]` | `REQ-MOD3-06` / `BP-M3-GD-006` / `MOD3-GD-REQ-06` | NONE | None (Reaffirms design) | No (`REQ-TBD-09` preserved) |
| **`DLT-29`** | Mod III | Box 8: Predefined Slabs & Mandatory Probation Clearance Gate | ALREADY COVERED | `[A]` | `REQ-MOD3-07`–`08` / `BP-M3-GD-007`–`008` | NONE | None (Reaffirms design) | No (`REQ-TBD-05` preserved) |
| **`DLT-30`** | Mod III | Box 1–3: Staff 30-Day Onboarding Goal Setting & Joint Lock | ALREADY COVERED | `[A]` | `REQ-MOD3-09` / `BP-M3-KRA-001` / `MOD3-KRA-REQ-01` | NONE | None (Reaffirms design) | No |
| **`DLT-31`** | Mod III | Box 4: Staff Quarterly Q1–Q4 Review Cycle Cadence | ALREADY COVERED | `[A]` | `REQ-MOD3-10`–`12` / `BP-M3-KRA-002`–`004` | NONE | None (Reaffirms design) | No |
| **`DLT-32`** | Mod III | Box 4: Staff Reminder Wording ("automatic reminder after 20d") | CLARIFICATION | `[A]` | `REQ-MOD3-10` / `BP-M3-KRA-002` / `MOD3-KRA-REQ-02` | LOW | `02-business-process` | Confirmation (CONF-08) |
| **`DLT-33`** | Mod III | Box 6: Direct Module I Handshake for Approved Increments | ALREADY COVERED | `[A]` | `REQ-INT-04` / `BP-XMOD-004` / `MOD3-KRA-REQ-05` | NONE | None (Reaffirms design) | No |
| **`DLT-34`** | Mod III | Box 1–3: Faculty Dual Eligibility & 7-Working-Day Submission | ALREADY COVERED | `[A]` | `REQ-MOD3-14`–`16` / `BP-M3-FAC-001`–`003` | NONE | None (Reaffirms design) | No |
| **`DLT-35`** | Mod III | Box 4: Multi-Unit Verification ("and other stakeholders") | CLARIFICATION / EXTENSION | `[B]` | `REQ-MOD3-17` / `BP-M3-FAC-004` / `MOD3-FAC-REQ-04` | LOW | `02-business-process` | Confirmation (CONF-09) |
| **`DLT-36`** | Mod III | Box 5 & 7: Registrar ECM Scheduling & Previous Increments in Matrix | CLARIFICATION | `[A]` | `REQ-MOD3-18`–`19` / `BP-M3-FAC-006`–`007` | MEDIUM | `01-reqs`, `02-business-process` | No (`CAND-REQ-M3-REGSCHED`) |
| **`DLT-37`** | Mod III | Box 10: Expanded 7-Outcome ECM Taxonomy (PIP, Reprimand, etc.) | NEW EXPLICIT REQUIREMENT | `[A]` | `REQ-MOD3-20` / `BP-M3-FAC-008` / `MOD3-FAC-REQ-08` | HIGH | `01-reqs`, `02-business-process`, `03-frd` | **CONFIRMATION (CONF-10 & TBDs)** |

---

## 6. Duplicate & Overlap Consolidation

Across the three individual delta analyses, several cross-cutting capabilities and enterprise governance requirements appeared repeatedly in different modules. To prevent documentation bloat and ensure architectural consistency, these items are consolidated into canonical enterprise requirements:

```
                         ┌────────────────────────────────────────────────────────┐
                         │       CONSOLIDATED ENTERPRISE PLATFORM CAPABILITIES    │
                         └───────────────────────────┬────────────────────────────┘
                                                     │
         ┌───────────────────┬───────────────────────┼───────────────────────┬───────────────────┐
         ▼                   ▼                       ▼                       ▼                   ▼
   [Master CDB Feed]  [Digital Dossier]      [Immutable Audit]      [Dynamic Reports]    [Module I Injection]
   (Mod I Boxes 1,9;  (Mod I Box 11;         (Mod I Box 13;         (Mod I Box 14;       (Mod I Formats 1,2,5;
    Mod II Step 19;    Mod II Step 19;        Mod II Step 21;        Mod II Step 20;      Mod III Track B Box 6;
    Mod III Box 1,G)   Mod III Section D)     Mod III Section E)     Mod III Section F)   Mod III Track C Box 9)
```

1. **Central Employee Database Master Authority:**  
   - *Source Appearances:* Module I Box 1 & 9; Module II Step 19; Module III Track A Box 1, Section G.
   - *Canonical Synthesis:* Module I Central Database is the exclusive master record authority. Module II instantiates records upon Day-1 onboarding; Module III continuously consumes employee master attributes (DOJ, probation clearance, supervisor hierarchy) to drive all performance scheduling.
2. **Digital Employee Dossier Integration:**  
   - *Source Appearances:* Module I Box 11; Module II Step 19; Module III Section D.
   - *Canonical Synthesis:* Every pre-employment certificate, signed LOI, monthly evaluation form, quarterly KRA review, ECM scorecard, and increment letter must be permanently indexed into the employee's central digital dossier (`BP-M1-003`).
3. **Immutable Audit Trail & Version History:**  
   - *Source Appearances:* Module I Box 13; Module II Step 21; Module III Section E.
   - *Canonical Synthesis:* Enterprise-wide immutability standard: all transactions, approvals, rejections, lockouts, and edits across Modules I, II, and III must write an indelible audit log with actor ID, timestamp, and before/after snapshots (`BR-ENT-004`).
4. **Configurable Real-Time Reporting Platform:**  
   - *Source Appearances:* Module I Box 14; Module II Step 20; Module III Section F.
   - *Canonical Synthesis:* System supports dynamic, configurable reporting where HR can add or delete report templates without code modifications. Real-time query execution across active master data and audit ledgers.
5. **Appraisal Outcomes $\rightarrow$ Module I Service Change Request Injection:**  
   - *Source Appearances:* Module I Structure 3; Module III Track B Box 6; Module III Track C Box 9; Handshake `BP-XMOD-004`.
   - *Canonical Synthesis:* Approved annual increments and promotions across all three performance tracks automatically inject formal Service Change Requests into Module I (Formats 1, 2, or 5), preserving mandatory Level-1 HR and Level-2 Senior Management approval.

---

## 7. Cross-Module Impact Matrix

The unified analysis confirms five authoritative cross-module business relationships connecting the functional modules:

| Inter-Module Handshake | Source Module | Target Module | Institutional Event / Information Transferred | Business Purpose & Receiving Process | Documentation Layers Impacted | Confirmation / TBD Status |
|---|---|---|---|---|---|---|
| **`BP-XMOD-001`** Onboarding Handshake | Module II (Recruitment) | Module I (Central Master) | Selected candidate verified Day-1 joining $\rightarrow$ Candidate profile, identity credentials, degree certificates, approved designation, salary, reporting supervisor. | Instantiates active Master Record (`BP-M1-001`), creates Dossier (`BP-M1-003`), places Org Chart node (`BP-M1-002`), closes vacancy in Open Positions Tracker (`BP-M2-TRK-002`). | `01-reqs` (`REQ-INT-01`), `02-business-process`, `03-frd`, Database | Fully Confirmed (Preserved) |
| **`BP-XMOD-002`** Resignation Replacement | Module I (Central Master) | Module II (Recruitment) | Dean formally accepts employee resignation in Module I $\rightarrow$ Vacated post details, last working day, Dean's replacement justification. | Triggers urgent replacement countdown clock; initiates fast-track vetting (Assoc Dean / Head HR) and Pro-Chancellor approval (`BP-M2-URG-001`). | `01-reqs` (`REQ-INT-02`), `02-business-process`, `03-frd` | Confirmed (Step 5A refined) |
| **`BP-XMOD-003`** Master Baseline Feed | Module I (Central Master) | Module III (Performance) | Continuous feed of Employee Code, employment cadre, DOJ, probation clearance status, department, and active supervisor hierarchy node. | Authoritative baseline driving Group-D monthly scheduling, Staff 30-day goal timers, and Faculty monthly 10th dual-criteria eligibility scans (`BP-M3-GD-001`, `KRA-001`, `FAC-001`). | `01-reqs` (`REQ-INT-03`), `02-business-process`, `03-frd` | Fully Confirmed (Preserved) |
| **`BP-XMOD-004`** Appraisal Outcome Injection | Module III (Performance) | Module I (Central Master) | Approved annual appraisal outcome $\rightarrow$ Employee ID, approved scores, recommended salary revision (Format 1), designation promotion (Format 2), or level change (Format 5). | Automatically injects formal Service Change Request in Module I, pre-populating verified evaluation records and routing to Level-1 HR and Level-2 Senior Management approval (`BP-M1-004`). | `01-reqs` (`REQ-INT-04`), `02-business-process`, `03-frd` | Fully Confirmed (Preserved) |
| **`BP-XMOD-005`** Org Realignment Propagation | Module I (Central Master) | Module III (Performance) | Effective-date activation of department transfer (Format 6), reporting authority change (Format 4), or org chart restructuring. | Dynamically realigns active supervisory evaluation inboxes in Module III while locking and preserving historical evaluation integrity under past supervisors. | `01-reqs`, `02-business-process`, `03-frd` | Confirmed (`REQ-TBD-04` preserved) |

---

## 8. Consolidated Conflict Matrix

The following conflict register consolidates every significant policy tension, role divergence, or timing ambiguity identified between the original official requirement PDFs and the new stakeholder materials:

| Conflict ID | Operational Topic | Existing Baseline Position | New Stakeholder Material Position | Source Divergence Rationale | Potential System & Governance Impact | Stakeholder Decision Required |
|---|---|---|---|---|---|---|
| **`CONF-01`** | **Academic Manpower Vetting Authority** | Original Module II PDF Sec 1 and `REQ-MOD2-05` assign academic requisition vetting to **HR Department** (3-month window). | Module II Narrative Para 8 & Diagram Step 2 state requisitions for Faculty & Lab Tech go for vetting to **Associate Dean (Academics)**. | Introduces Associate Dean as primary academic vetting authority, separating it from Head HR (who vets Non-Faculty). | Realigns workflow approval inboxes and governance hierarchy for academic manpower planning. | **CONFIRM:** Does Associate Dean (Academics) vet academic requisitions *in place of* HR, or *jointly with* HR? |
| **`CONF-02`** | **Lab Technician Cadre Alignment** | Baseline categorized Lab Technicians under Non-Academic / Technical staff subject to 3-round interview. | Module II Diagram Steps 1, 2, 6, 14A explicitly classify **"Faculty & Lab Technician"** together under Academic Track. | Lab Technicians are grouped with teaching faculty for planning, vetting by Associate Dean, Dean MRF raising, and SCM interview. | Re-routes Lab Technician hiring from 3-round interview to Statutory Selection Committee with external experts. | **CONFIRM:** Are Lab Technicians officially evaluated by the Selection Committee (Academic) rather than 3 rounds (Non-Academic)? |
| **`CONF-03`** | **Management Approval for Interview (Step 13)** | Earlier baseline moved directly from Recruiter Calling Sheet (RCS) shortlisting to interview scheduling. | Module II Diagram Step 13 introduces mandatory **"Management Approval for Interview"** prior to scheduling interviews. | Adds an explicit executive approval gate over candidate shortlists before interview panels can be convened. | Adds a new approval bottleneck; recruiters cannot issue interview calls without prior Management sign-off. | **CONFIRM:** Is executive Management approval mandatory for *all* shortlisted candidates before interviews, or only senior tiers? |
| **`CONF-04`** | **Group-D Evaluating Actor (HOD vs. Supervisor)** | `BP-M3-GD-002` described the evaluating actor as "Reporting Supervisor / Evaluating Supervisor". | Module III Diagram Box 2 & 3 explicitly states forms are routed to **HOD** who **"Completes & Submits"** online. | Assigns direct evaluation responsibility to the Head of Department rather than intermediate shift supervisors or foremen. | In large departments, routing all operational staff forms directly to HOD may create month-end submission delays. | **CONFIRM:** Does HOD personally complete and submit Group-D forms, or does immediate supervisor draft for HOD endorsement? |

---

## 9. Master Stakeholder Confirmation List

The following master confirmation register merges and prioritizes all institutional decisions requiring formal stakeholder sign-off:

| Confirmation ID | Module / Domain | Governance Question | Why Confirmation Is Needed | Affected Documents | Priority | Recommended Decision Owner |
|---|---|---|---|---|---|---|
| **`CONF-01`** | Mod II (Academic) | Does **Associate Dean (Academics)** vet academic requisitions *in place of* HR, or *jointly with* HR? | Resolves vetting inbox routing and authority chain in academic manpower planning. | `01-reqs`, `02-business-process` | **HIGH** | Pro-Chancellor / Registrar |
| **`CONF-02`** | Mod II (Academic) | Is **Lab Technician** officially governed under the **Academic Track** (SCM Selection) rather than Non-Academic (3 Rounds)? | Determines whether technical lab cadres require external statutory selection committees. | `01-reqs`, `02-business-process`, `03-frd` | **HIGH** | Academic Council / HR Head |
| **`CONF-03`** | Mod II (Common) | Is executive **Management Approval for Interview (Step 13)** mandatory for *all* candidates before interview scheduling? | Establishes whether recruiters can schedule interviews directly or must await executive clearance. | `01-reqs`, `02-business-process`, `03-frd` | **HIGH** | Senior Management / HR Head |
| **`CONF-04`** | Mod II (Academic) | Does the system enforce a formal **HR Recommendation review post-SCM** before Management cost approval? | Determines whether SCM scorecards route to HR or directly to Management for appointment. | `01-reqs`, `02-business-process` | **MEDIUM** | Head HR |
| **`CONF-05`** | Mod III (Group-D) | Does **HOD** directly complete Group-D evaluations, or does immediate supervisor draft for HOD endorsement? | Defines role assignment, evaluation inboxes, and operational feasibility for support cadres. | `02-business-process`, `03-frd` | **MEDIUM** | VP-Administration / HR Head |
| **`CONF-06`** | Mod III (Staff) | Does the Staff quarterly reminder fire **20 days before quarter end**, **Day 20 of quarter**, or **after Day 15 submission window**? | Resolves timing ambiguity in automated notification scheduler. | `02-business-process`, `07-sla` | **LOW** | HR Operations |
| **`CONF-07`** | Mod III (Faculty) | Does **"and other stakeholders"** in Faculty verification mandate configurable verification routing units (e.g. IQAC)? | Determines if the 4 verifying bodies are permanently hardcoded or dynamically configurable. | `02-business-process`, `03-frd` | **LOW** | Registrar / Dean Academics |
| **`CONF-08`** | Mod III (Faculty) | Does the University confirm the inclusion of **PIP, Reprimand, and Probation Extension** as formal ECM appraisal outcomes? | Expands Module III into disciplinary/probationary governance; requires policy threshold definitions. | `01-reqs`, `02-business-process`, `03-frd` | **HIGH** | Governing Council / Vice-Chancellor |

---

## 10. Master Consolidated TBD Register

The master TBD register consolidates the 11 original project TBD items (`REQ-TBD-01` to `REQ-TBD-11`) with the 9 newly identified stakeholder TBD items (`REQ-TBD-12` to `REQ-TBD-20`):

### Section A: Original Project TBD Items (Preserved Unchanged)
| TBD ID | Module / Area | Description & Unresolved Institutional Scope | Status & Scope |
|---|---|---|---|
| **`REQ-TBD-01`** | Module I | Resignation intake mechanism and employee self-service separation workflow. | `[E]` Catalogued as `REQ-EXT-03` |
| **`REQ-TBD-02`** | Module I | Enterprise ERP synchronization transport protocol (REST webhook vs. SFTP/staging table). | `[E]` Catalogued as `REQ-EXT-03` |
| **`REQ-TBD-03`** | Module I | Historical service record migration strategy and legacy cutover data scope. | `[E]` Day-forward baseline preserved |
| **`REQ-TBD-04`** | Module III | Mid-cycle supervisor transfer evaluation attribution guidelines (pro-rata vs. full). | `[E]` Governance policy TBD |
| **`REQ-TBD-05`** | Module III | Group-D predefined compensation slab amounts and increment rupee values. | `[E]` University compensation policy |
| **`REQ-TBD-06`** | Module II | Academic Statutory SCM digital scoring parameter percentage weights. | `[E]` Statutory committee guidelines |
| **`REQ-TBD-07`** | Module II | Non-Academic three-round assessment dimension percentage weights and thresholds. | `[E]` HR selection policy |
| **`REQ-TBD-08`** | Module III | Faculty ECM TNU Protocol matrix benchmark thresholds and percentage cutoffs. | `[E]` Institutional benchmark policy |
| **`REQ-TBD-09`** | Module III | Group-D 12-month parameter-weighted averaging formula and coefficients. | `[E]` HR performance policy |
| **`REQ-TBD-10`** | Module I | Additional Responsibility (Format 8) administrative allowance policy confirmation. | `[E]` Explicitly uncalculated |
| **`REQ-TBD-11`** | Module II | SCM External Subject Expert identity verification and digital access mechanism. | `[E]` Catalogued as `REQ-EXT-05` |

### Section B: New Stakeholder-Derived TBD Items (Added from Delta Analyses)
| TBD ID | Module / Area | Description & Stakeholder Source Reference | Status & Scope |
|---|---|---|---|
| **`REQ-TBD-12`** | Module I | **Simultaneous & Conflicting Change Resolution Policy:** Rules governing two concurrent requests affecting the same employee (Narrative Para 56–63). | `[E]` Mandatory anti-invention item |
| **`REQ-TBD-13`** | Module I | **Change Request Cancellation / Withdrawal Authority:** Permissions and allowable stages for withdrawing in-flight requests (Diagram Box 12). | `[E]` HR governance policy |
| **`REQ-TBD-14`** | Module I | **Standardized Reason Taxonomy for Clarification & Rejection:** Dropdown reason codes for returning or rejecting requests (Narrative Para 20). | `[E]` HR operational standards |
| **`REQ-TBD-15`** | Module II | **Qualification & Experience Shortlisting Thresholds & UGC Norms:** Definition of strict vs. advisory screening filters (Narrative Para 22). | `[E]` Mandatory anti-invention item |
| **`REQ-TBD-16`** | Module II | **Pre-Onboarding Milestone Exception Rules:** Policy rules for candidate notice period extensions, verification failures, and dropouts (Narrative Para 50). | `[E]` Recruitment operational policy |
| **`REQ-TBD-17`** | Module III | **Performance Improvement Plan (PIP) Workflow & Criteria:** PIP duration, review milestones, mentor roles, and exit consequences (Diagram Box 10). | `[E]` University HR governance |
| **`REQ-TBD-18`** | Module III | **Formal Reprimand Policy & Governance Impact:** Issuance criteria, service record flags, and increment bar periods (Diagram Box 10). | `[E]` University disciplinary policy |
| **`REQ-TBD-19`** | Module III | **Probation Extension Score Thresholds & Max Duration:** Minimum score cutoff for confirmation and max extension duration (Diagram Box 10). | `[E]` University probation policy |
| **`REQ-TBD-20`** | Module III | **Group-D "Not Submitted" Reason Taxonomy & Re-open Authority:** Standardized overdue reason codes and administrative unlock protocol (Diagram Box 5). | `[E]` VP-Admin operational policy |

---

## 11. Documentation Impact Matrix

The following matrix assesses the downstream impact of candidate changes across all project documentation layers:

| System Documentation Layer | Impact Level | Primary Documents Affected | Required Future Modifications Upon Confirmation |
|---|---|---|---|
| **Requirements Layer** (`docs/01-requirements/`) | **HIGH** | `01-PROJECT-REQUIREMENTS-SPECIFICATION.md`<br>`02-REQUIREMENT-CATALOGUE.md`<br>`03-SCOPE-AND-BOUNDARIES.md`<br>`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`<br>`06-REQUIREMENTS-QUALITY-REVIEW.md` | - Add candidate requirement IDs (`CAND-REQ-M1-VAL`, `CAND-REQ-M2-INTAPP`, `CAND-REQ-M3-OUTCOMES`, etc.).<br>- Expand TBD register from 11 to 20 items.<br>- Re-reconcile mathematical requirement counts. |
| **Business Process Layer** (`docs/02-business-process/`) | **HIGH** | `01-BUSINESS-PROCESS-FRAMEWORK.md`<br>`02-MODULE-I-BUSINESS-PROCESSES.md`<br>`03-MODULE-II-BUSINESS-PROCESSES.md`<br>`04-MODULE-III-BUSINESS-PROCESSES.md`<br>`06-BUSINESS-RULES-AND-DECISION-POINTS.md`<br>`07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md` | - Update Actor Taxonomy (Associate Dean).<br>- Refine `BP-M1-004`–`007` with pre-validation and 7 exceptions.<br>- Refine `BP-M2-ACAD` and `NACAD` with Step 13, Lab Tech, and 5 pre-onboarding milestones.<br>- Refine `BP-M3-FAC-008` with 7-outcome taxonomy.<br>- Update Business Rules catalogue and SLA matrix. |
| **Functional Requirements** (`docs/03-functional-requirements/`) | **HIGH** | `01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`<br>`02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`<br>`03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md` | - Add functional specifications for pre-validation rules, Step 13 interview approvals, 5-stage pre-onboarding, and PIP/reprimand tracking. |
| **Architecture Baseline** (`TECHNOLOGY_ARCHITECTURE_BASELINE.md`) | **LOW / INDIRECT** | Core architecture baseline & ADR-001 | - Update workflow state machine definitions to accommodate new intermediate states (`CLARIFICATION_REQUIRED`, `MGMT_INTERVIEW_APPROVAL_PENDING`, `APPROVED_YET_EFFECTIVE`).<br>- Core technical stack (Next.js, NestJS, PostgreSQL) remains 100% unaffected. |
| **Future Detailed Workflows** (`docs/06-workflows/`) | **HIGH** | To be authored in Phase 6 | - Detail the 15-stage Module I flow, 21-stage Module II flow, and 10-stage Faculty ECM flow. |
| **Database & Domain Models** (`docs/04-database/`) | **DOWNSTREAM** | To be authored in Phase 4 | - Accommodate new candidate status enums, PIP tracking entities, and interview approval audit records. |

---

## 12. Candidate Change Priorities

Candidate changes are categorized into strict governance priority tiers to guide the upcoming review:

| Priority Tier | Description & Criteria | Candidate Changes Included | Action Required |
|---|---|---|---|
| **P0 — Must Confirm Before Baseline Update** | Fundamental governance gates, role ownership, or track classifications that alter approval hierarchies. | `CONF-01` (Academic Vetting Role)<br>`CONF-02` (Lab Tech Track)<br>`CONF-03` (Step 13 Interview Approval)<br>`CONF-04` (Group-D HOD Role)<br>`CONF-08` (ECM Outcomes Scope) | Formal executive sign-off required from University Leadership before any baseline updates. |
| **P1 — Important for Process Refinement** | Operational enhancements and formal candidate requirements that extend workflow functionality. | `CAND-REQ-M1-VAL` (Pre-Validation)<br>`CAND-REQ-M2-HRREC` (Post-SCM HR Review)<br>`CAND-REQ-M2-PREONB` (5 Pre-Onboarding Stages)<br>`CAND-REQ-M3-REGSCHED` (Registrar ECM Sched)<br>Module I 7 Exception Branches | Incorporate into requirements catalogue and business processes upon P0 confirmation. |
| **P2 — Documentation Clarifications** | Naming refinements, visual clarification loops, and standard status labels. | Standardized Statuses (`APPROVED_YET_EFFECTIVE`, `SCHEDULED`, `Not Submitted`)<br>HR & Mgmt Clarification Loops<br>Sourcing Ingestion Channel Names | Refine existing process texts and descriptions during planned documentation update. |
| **P3 — Future Implementation Details** | Technical validation messages, state machine transitions, and database schema mappings. | System validation error codes<br>Downstream queue event mappings<br>State machine transition tables | Defer to Phase 4 (Database) and Phase 6 (Workflows). |

---

## 13. Baseline Count Assessment

The established baseline counts compare against the candidate change set as follows:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        BASELINE COUNT STABILITY & RECONCILIATION                       │
├───────────────────────────────┬──────────────────────────┬─────────────────────────────┤
│ Metric / Artifact Dimension   │ Frozen Baseline Count    │ Candidate Post-Review Count │
├───────────────────────────────┼──────────────────────────┼─────────────────────────────┤
│ Atomic System Requirements    │ 104 Atomic Requirements  │ 104 Frozen + 6 Candidate    │
│                               │                          │ Requirements (Total: 110)   │
├───────────────────────────────┼──────────────────────────┼─────────────────────────────┤
│ TBD / Open Decisions          │ 11 TBD Items             │ 11 Preserved + 9 Candidate  │
│                               │ (REQ-TBD-01 to 11)       │ TBDs (Total: 20 TBDs)       │
├───────────────────────────────┼──────────────────────────┼─────────────────────────────┤
│ End-to-End Business Processes │ 59 Business Processes    │ 59 Macro Processes Preserved│
│                               │ (Docs 02 to 05)          │ (Internal Steps Refined)    │
├───────────────────────────────┼──────────────────────────┼─────────────────────────────┤
│ Formal Business Rules         │ 60 Business Rules        │ 60 Preserved + 4 Candidate  │
│                               │ (Doc 06)                 │ Rules (Total: 64 Rules)     │
└───────────────────────────────┴──────────────────────────┴─────────────────────────────┘
```

> **Formal Declaration:**  
> The existing baseline (104 atomic requirements and 59 business processes) **remains the frozen historical baseline**. It is neither replaced nor invalidated by this document. Once stakeholder confirmation on the P0 decisions is achieved, a controlled, auditable baseline update will be executed to advance the official baseline.

---

## 14. Recommended Controlled Change Sequence

To guarantee enterprise documentation integrity, prevent unauthorized baseline drift, and ensure seamless traceability across all phases, the following sequential execution model is recommended:

```
 [1. ALL STAKEHOLDER MATERIALS RECEIVED] (Module I, II, III Narratives & Diagrams)
                 │
                 ▼
 [2. COMPLETE DELTA REVIEWS AUTHORED] (Docs 07, 08, and 09 in docs/01-requirements/)
                 │
                 ▼
 [3. FORMAL STAKEHOLDER REVIEW & SIGN-OFF] ◄── [CURRENT MILESTONE — AWAITING REVIEW]
   - Resolve P0 Conflicts (CONF-01 to CONF-08)
   - Confirm Candidate Requirements & TBD Register
                 │
                 ▼
 [4. CONTROLLED REQUIREMENT BASELINE UPDATE]
   - Update docs/01-requirements/01, 02, 03, 05, 06
   - Reconcile Atomic Count (104 -> 110) and TBD Count (11 -> 20)
                 │
                 ▼
 [5. AFFECTED BUSINESS PROCESS BASELINE UPDATE]
   - Refine docs/02-business-process/01, 02, 03, 04, 06, 07, 08
   - Incorporate 21-step Mod II, 15-step Mod I, and 10-step Mod III flows
                 │
                 ▼
 [6. FUNCTIONAL REQUIREMENTS BASELINE UPDATE]
   - Refine docs/03-functional-requirements/01, 02, 03, 04
                 │
                 ▼
 [7. QUALITY ASSURANCE AUDIT & RE-FREEZE]
   - Re-audit all cross-references, traceability matrices, and classification tallies
                 │
                 ▼
 [8. PROCEED TO NEXT DOCUMENTATION PHASE]
   - Phase 4: Database Schema & Entity Documentation (docs/04-database/)
```

---

## 15. Final Status & Summary of Findings

| Dimension / Metric | Quantitative Summary | Status / Verdict |
|---|---|---|
| **Consolidated Delta Register Items** | **37 total items** | Fully catalogued and cross-mapped |
| **Already Covered Items** | **11 items** | Reaffirms baseline architecture |
| **New Explicit Requirements** | **6 candidate requirements** | Candidate IDs provisionally assigned |
| **Operational Clarifications** | **12 items** | Detailed steps and labels refined |
| **Potential Conflicts** | **4 critical policy conflicts** | Isolated in Conflict Matrix (`CONF-01` to `04`) |
| **New Exceptions / Special Conditions** | **9 explicit exception flows** | 7 Module I exceptions + 2 Module III flows |
| **Consolidated TBD Items** | **20 total TBD items** | 11 original preserved + 9 new stakeholder items |
| **Impact Level Breakdown** | **High: 5, Medium: 10, Low: 11, None: 11** | Full distribution documented |
| **Cross-Module Handshakes Analyzed** | **5 handshakes (`BP-XMOD-001` to `005`)** | 100% reconciled and reaffirmed |
| **Stakeholder Confirmations Required** | **8 formal decision items** | Master Confirmation List ready for review |
| **Baseline Stability** | **104-REQ & 59-BP baselines remain frozen** | Zero unauthorized mutations applied |
| **Documentation Safety** | **Zero existing files modified** | Strictly analysis-only execution |

---
*End of Document — Combined Stakeholder Requirement Delta Review.*
