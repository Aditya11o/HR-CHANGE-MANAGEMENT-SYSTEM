# Functional Requirements Document Index
## University HR Change Management & Automation System

**Document Identifier:** `DOC-03-FRD-INDEX`  
**Phase:** Phase 3 — Functional Requirements Specification (Documentation-Only)  
**Location:** `docs/03-functional-requirements/00-FRD-INDEX.md`  
**Status:** Approved Functional Requirements Baseline Index  
**Date:** September 29, 2026  

---

## 1. Document Purpose

This document serves as the master index, navigation guide, and governing framework for the Functional Requirements Document (FRD) suite of the University HR Change Management & Automation System. 

The primary objective of this phase is to define **WHAT the system must do** from a functional, operational, and user perspective across all authorized modules, without premature technical implementation. Specifically:
- **This phase defines WHAT the system must do:** It establishes explicit business logic, workflows, functional behaviors, input/output requirements, state transitions, validation rules, notifications, SLAs, and reporting requirements.
- **It does NOT define database implementation details:** No final relational schemas, table DDL, foreign key scripts, or database migration code are defined here.
- **It does NOT define REST endpoint implementation:** No controller code, HTTP route handlers, payload serialization implementations, or middleware code are created here.
- **It does NOT define final UI implementation:** No React/Next.js components, JSX layouts, CSS Module stylesheets, or UI wireframe assets are implemented here.
- **It does NOT define source code:** No executable application code or package configurations are introduced.
- **Subsequent phases will transform these approved functional requirements** into detailed Database Schemas (ERD), Workflow State Machine Specifications, REST API Interface Specifications, UI/UX Design System Specifications, Security Matrices, Testing & QA Plans, and Deployment Specifications.

---

## 2. Functional Requirements Documentation Scope

The Functional Requirements documentation suite encompasses the entire functional boundary of the University HR Change Management & Automation System across three functional modules and the shared platform foundation:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                         FUNCTIONAL REQUIREMENTS SUITE ARCHITECTURE                               │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                00-FRD-INDEX.md (Master Index & Governance)                       │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 01-MODULE-I-FUNCTIONAL-       │ 02-MODULE-II-FUNCTIONAL-       │ 03-MODULE-III-FUNCTIONAL-       │
│    REQUIREMENTS.md            │    REQUIREMENTS.md             │    REQUIREMENTS.md              │
│ • Central Employee Database   │ • Academic Manpower Planning   │ • Sub-System 1: Group-D / Band I│
│ • Dynamic Org Chart           │ • Non-Academic Manpower Plan   │   Monthly/Annual Appraisal      │
│ • Digital Employee File       │ • Urgent Replacement (Resign)  │ • Sub-System 2: General Staff   │
│ • 10 Service Change Formats   │ • Open Positions Tracker       │   KRA/KPI Lifecycle (Q1-Q4)     │
│ • 2-Level Approval Hierarchy  │ • Omnichannel CV Sourcing      │ • Sub-System 3: Faculty Annual  │
│ • Effective-Date Processing   │ • UGC Norms Screening          │   Appraisal via ECM Route       │
│ • Audit Trail & Versioning    │ • Recruiter Calling Sheet (RCS)│ • Preserved Independence of     │
│ • ERP Reflection Boundary     │ • Statutory SCM & 3-Round Inter│   all 3 Performance Workflows   │
│ • Real-time Reports           │ • LOI & "Yet to Join" Tracking │ • Direct Handshake into Mod I   │
├───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┤
│                            04-SHARED-FUNCTIONAL-REQUIREMENTS.md                                  │
│ • Common Master Data Primitives • Cross-Cutting Workflow Engine • Universal SLA / Timeline Engine│
│ • Unified Notification Engine • Central Form Repository • Security & RBAC Functional Rules       │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Authoritative Sources

This Functional Requirements suite is authored strictly based upon the following authoritative primary documents:
1. **[`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md):** Authoritative baseline analysis of the original requirement briefs, capturing all explicit rules, workflows, SLAs, and open questions.
2. **[`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md):** Approved technical architecture baseline defining the Next.js, NestJS Modular Monolith, PostgreSQL, Redis, and Object Storage architectural baseline.
3. **Original Official Requirement Documents (Preserved at Workspace Root):**
   - [`27-07-26 - Revised HR Change Management & Automation System-Module I.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/27-07-26%20-%20Revised%20HR%20Change%20Management%20&%20Automation%20System-Module%20I.pdf)
   - [`Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf)
   - [`Requirement_Brief_Module_III_Performance_Management_Automation_System.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/Requirement_Brief_Module_III_Performance_Management_Automation_System.pdf)

---

## 4. Relationship to `PROJECT_REQUIREMENTS_ANALYSIS.md`

`PROJECT_REQUIREMENTS_ANALYSIS.md` serves as the primary requirements baseline that established:
- The initial requirement extraction from the raw PDFs.
- The synthesis of cross-module relationships and data flows.
- The catalog of all 16 major actors and roles.
- The consolidated SLA and timeline matrix.
- The identification of the initial 24 Traceability Identifiers (`MOD1-*`, `MOD2-*`, `MOD3-*`).
- The formal catalog of 8 Open Questions requiring university clarification.

The Functional Requirements Document suite builds directly upon this baseline by decomposing those high-level requirements into atomic, verifiable, and implementable functional specifications for each module.

---

## 5. Relationship to `TECHNOLOGY_ARCHITECTURE_BASELINE.md`

`TECHNOLOGY_ARCHITECTURE_BASELINE.md` established the approved technical parameters governing all subsequent phases:
- **Frontend:** Next.js (App Router, TypeScript) with Vanilla CSS, CSS Modules (`*.module.css`), CSS Variables, and a Custom Design System. (Tailwind CSS and Shadcn UI are explicitly excluded from the current baseline).
- **Backend:** NestJS (TypeScript) implementing a REST API within an encapsulated **Modular Monolith** architecture. (Microservices are explicitly excluded from the current baseline).
- **Persistence & Infrastructure:** PostgreSQL as System of Record, Redis for caching and BullMQ queues, Object Storage for binaries, and dedicated background workers for SLAs and effective-date processing.

The FRD suite respects these architectural boundaries: functional requirements specify behavior and data contracts that directly align with these approved components without violating modular encapsulation.

---

## 6. Functional Requirements Classification Framework

To guarantee transparency, prevent scope creep, and avoid silently converting assumptions into business rules, every requirement in the FRD suite is rigorously labeled using the following classification taxonomy:

| Classification Marker | Classification Name | Definition & Governance Rule |
|---|---|---|
| **`[A] EXPLICIT REQUIREMENT`** | Explicit Requirement | Directly stated in the authoritative source requirement briefs or PDFs. Non-negotiable baseline requirement. |
| **`[B] LOGICAL IMPLICATION`** | Logical Implication | Not verbatim in the text, but mathematically and logically necessary to execute an explicit requirement (e.g., transition states, validation guards, prerequisite checks). |
| **`[C] APPROVED TECHNICAL DECISION`** | Approved Technical Decision | Architectural decision already approved and documented in `TECHNOLOGY_ARCHITECTURE_BASELINE.md` (e.g., Modular Monolith, PostgreSQL SoR, Redis BullMQ queues). |
| **`[D] PROPOSED DETAIL`** | Proposed Detail | Suggested functional design detail or user experience behavior proposed to complete a workflow, subject to stakeholder review before final sign-off. |
| **`[E] TBD / OPEN DECISION`** | TBD / Open Decision | Information missing from source documents, ambiguous policy, or unconfirmed institutional parameters requiring formal confirmation from University/HR leadership. |

---

## 7. Module I Document Overview
- **File:** [`01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md)
- **Scope:** Central Employee Database, Dynamic Organization Chart, Digital Employee File, 10 Service Change Formats (Salary, Designation, Reportee, Reporting Authority, Level, Department/School, Location, Additional Responsibility, Qualifications, Other Conditions), Change Request Lifecycle, 2-Level Approval (HR $\rightarrow$ Senior Management), Effective Date Processing, Audit Trail, Version History, ERP Reflection, Notifications/SLAs, and Real-Time Reporting.

---

## 8. Module II Document Overview
- **File:** [`02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md)
- **Scope:** Academic Manpower Planning (Faculty & Lab Techs), Non-Academic Manpower Planning (Staff), Urgent Replacement Pipeline (Resignations), MRF Lifecycle, Open Positions Tracker (Attachment 3), Multichannel Sourcing, Central CV Database, Automated Screening & UGC Norms, Recruiter Calling Sheet (RCS), Statutory Selection Committee Meetings (SCM), External Subject Expert Participation, Non-Academic 3-Round Interviews, Candidate Scoring, Management Pre-Approval, Letter of Intent (LOI), and "Yet to Join" Tracking. Preserves strict separation between Academic and Non-Academic tracks.

---

## 9. Module III Document Overview
- **File:** [`03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md)
- **Scope:** Independent functional specifications for three non-interchangeable performance management sub-systems:
  1. *Sub-System 1 (Group-D / Band I):* Monthly evaluation, 7th due date, 3-day grace period, daily reminders, auto-lock on 10th, VP-Admin approval, annual report at 1 year from DOJ, weighted parameter calculation, probation gate, Management compensation review, and employee file archive.
  2. *Sub-System 2 (General Staff KRA/KPI):* 30-day onboarding goal setting, HR & Management locking, quarterly review cycle (Q1–Q4) with 90-day triggers, 20-day reminders, 15-day submission, 7-day supervisor verification, HR review, Management comment, annual appraisal outcome, and direct Module I change request initialization.
  3. *Sub-System 3 (Faculty ECM Route):* Monthly eligibility identification (probation + $\ge 12$ months service), 10th list to Registrar, 7 working days self-appraisal submission, parallel multi-department verification (Dean, R&D, Placement, HR) with discrepancy resubmission loop, monthly ECM scheduling, digital score sheet, TNU Protocol evaluation matrix, Management decision, next salary cycle implementation, auto-letter generation, and personal file archive.

---

## 10. Shared Functional Requirements Document Overview
- **File:** [`04-SHARED-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md)
- **Scope:** Cross-cutting platform primitives utilized across all modules: Central Employee Data schema guidelines, Organizational Structure DAG logic, Digital Employee File repository rules, Authentication & Session standards, Role-Based Access Control (RBAC) matrix, Universal Workflow & State Machine framework, SLA & Timeline scheduler rules, Multi-channel Notification infrastructure, Document storage & checksum rules, Audit & Versioning engine, Real-time Reporting query engine, Cross-module event handshakes, ERP Integration outbox pattern, and Central Dynamic Form Repository.

---

## 11. Requirement Traceability Approach

Traceability is maintained through unique identifiers:
- Base identifiers originate from `PROJECT_REQUIREMENTS_ANALYSIS.md` (e.g., `MOD1-CDB-01`, `MOD2-MP-FAC-01`, `MOD3-GD-EVAL-01`).
- Detailed functional requirements derived logically from these baselines are designated with structured sub-identifiers (e.g., `MOD1-CDB-REQ-01`, `MOD2-REC-REQ-05`, `MOD3-FAC-REQ-03`, `SHR-REQ-01`).
- Every requirement references its source document, section, page, classification type (`[A]` through `[E]`), and downstream dependency.

---

## 12. Documentation Status

| Document | Title | Status |
|---|---|---|
| `00-FRD-INDEX.md` | Functional Requirements Document Index | **APPROVED BASELINE** |
| `01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md` | Module I — HR Change Management & Automation | **DRAFTED / IN REVIEW** |
| `02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md` | Module II — Recruitment & Selection Automation | **DRAFTED / IN REVIEW** |
| `03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md` | Module III — Performance Management Automation | **DRAFTED / IN REVIEW** |
| `04-SHARED-FUNCTIONAL-REQUIREMENTS.md` | Shared Functional Requirements | **DRAFTED / IN REVIEW** |

---

## 13. Future Dependencies

The completion and approval of this Functional Requirements Document suite directly gates the following subsequent documentation phases:
1. **Phase 4: Domain Model & Entity Relationship Architecture (`docs/08-database/`):** Translating functional entities into formal relational schemas, constraints, and temporal tables.
2. **Phase 5: Workflow & State Machine Specifications (`docs/06-workflows/`):** Formal state transition tables and UML statecharts for all 8 major business processes.
3. **Phase 6: REST API Interface Specifications (`docs/09-api/`):** Defining OpenAPI/Swagger endpoint contracts, request/response DTOs, and error codes.
4. **Phase 7: UI/UX Design System & Wireframe Specifications (`docs/10-ui-ux/`):** Designing CSS Variables tokens, CSS Modules component specs, and page wireframes.
5. **Phase 8: Security & Access Control Matrix (`docs/11-security/`):** Detailed role-to-permission mapping and data isolation rules.
6. **Phase 9: Testing, Verification, & QA Specifications (`docs/14-testing/`):** Acceptance criteria, test cases, and compliance verification suites.

---
*End of Functional Requirements Index.*
