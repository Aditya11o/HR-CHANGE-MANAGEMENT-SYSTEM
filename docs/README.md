# University HR Change Management & Automation System
## Central Documentation Portal & System Architecture

Welcome to the authoritative documentation portal for the **University HR Change Management & Automation System**. This repository documents the complete end-to-end specifications, workflows, architecture, database models, and governance rules for the university's HR digital platform.

---

## 1. System Vision & Architecture Overview

The platform serves as the unified **digital backbone** for the employee lifecycle, connecting three core functional modules and shared platform services:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   INSTITUTIONAL SYSTEM ARCHITECTURE                              │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                               MODULE II: TALENT ACQUISITION                                      │
│  Academic & Non-Academic Manpower Requisitions ──► Sourcing ──► Screening ──► Selection ──► LOI │
└──────────────────────────────────────────┬───────────────────────────────────────────────────────┘
                                           │ Onboarding Handshake (BP-XMOD-001)
                                           ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                     MODULE I: CORE REPOSITORY & CHANGE MANAGEMENT ENGINE                         │
│  Central Employee DB (ERP Synced) ◄──► Dynamic Org Chart ◄──► Digital Employee Files (Dossiers) │
│  10 Change Formats ──► 2-Level Approvals (HR ➔ Senior Mgmt) ──► Effective Date Versioning       │
└──────────────────────────────────────────┬───────────────────────────────────────────────────────┘
                     ▲                     │ Master Data Feed (BP-XMOD-003)
                     │                     ▼
┌────────────────────┴─────────────────────────────────────────────────────────────────────────────┐
│                           MODULE III: PERFORMANCE MANAGEMENT ENGINE                              │
│  • Subsystem 1: Group-D Monthly Ratings (7th/10th auto-lock) & Annual Weighted Averages          │
│  • Subsystem 2: Staff KRA/KPI Onboarding (30-day lock) & Quarterly Reviews (Q1-Q4)               │
│  • Subsystem 3: Faculty Annual Appraisal via Statutory ECM Route (Monthly Eligibility 10th)      │
│  Approved Outcomes Auto-Feed into Module I Service Change Requests (BP-XMOD-004)                 │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Master Documentation Directory (Canonical Specifications)

The documentation is organized into five clean core domain folders:

| Domain | Document | Description | Key Invariants Preserved |
|---|---|---|---|
| **01. Requirements** | [`01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) | Unified Software Requirements Specification (SRS). | • 104 Atomic Requirements (`REQ-01` to `REQ-104`)<br>• 11 Baseline TBDs (`REQ-TBD-01` to `11`)<br>• Stakeholder Decisions (`CONF-01` to `10`)<br>• Full Requirements Traceability Matrix |
| **02. Business Processes** | [`02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md) | Comprehensive Business Process & Workflow Manual. | • 59 End-to-End Processes (`BP-M1`, `BP-M2`, `BP-M3`, `BP-XMOD`)<br>• 16-Actor Taxonomy & RACI Responsibility Matrix<br>• Comprehensive SLA Countdown & Escalation Matrix |
| **02. Business Rules** | [`02-business-process/02-BUSINESS-RULES-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md) | Authoritative Catalogue of Institutional Governance Rules. | • 60 Invariant Business Rules (`BR-M1`, `BR-M2`, `BR-M3`, `BR-ENT`, `BR-XMOD`)<br>• Auto-Lockouts, Quotas & Gating Logic |
| **03. Functional Specs** | [`03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md) | Granular Functional Requirements Document (FRD). | • 152 Functional Requirements (`MOD1-REQ`, `MOD2-REQ`, `MOD3-REQ`, `SHR-REQ`)<br>• State Machines, Validation Rules & Error Handling |
| **04. Architecture** | [`04-system-architecture/01-SYSTEM-ARCHITECTURE-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/01-SYSTEM-ARCHITECTURE-SPECIFICATION.md) | Enterprise Modular Monolith Architecture Specification. | • Next.js App Router & Custom Vanilla CSS Design System<br>• NestJS Modular Monolith & Domain Event Bus<br>• BullMQ Background Queues & Transactional Outbox |
| **04. Architecture Decision** | [`04-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md) | Approved Architectural Decision Record (ADR). | • Formal Technical Approval for Socket.IO Real-Time Push |
| **05. Database Design** | [`05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md) | Relational Schema Specification & Data Architecture. | • Single PostgreSQL Engine with 4 Domain Schemas<br>• 33 Primary Conceptual Entities (`ENT-*`)<br>• 41 Relational Foreign Key Mappings (`REL-*`)<br>• Indexing Strategy & Temporal Versioning |
| **05. Data Dictionary** | [`05-database/02-LOGICAL-DATA-DICTIONARY.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/02-LOGICAL-DATA-DICTIONARY.md) | Canonical Logical Data Dictionary. | • Complete 344 Logical Attributes Specification across all 33 Entities with Data Types, Nullability, and Descriptions |

---

## 3. Reading Guide by Stakeholder Role

- **University Leadership & Mentors:**
  - Start with Section 1 of the [SRS](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) for institutional goals and scope boundaries.
  - Review Section 5 of the [SRS](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) for the Stakeholder Confirmation Register (`CONF-01` to `CONF-10`).
- **Software Engineers & Developers:**
  - Read [System Architecture](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/01-SYSTEM-ARCHITECTURE-SPECIFICATION.md) for technology stack invariants, NestJS modular patterns, and queue setups.
  - Read [Functional Requirements](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md) for detailed inputs, state machines, and error handling.
  - Reference [Database Design](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md) and [Data Dictionary](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/02-LOGICAL-DATA-DICTIONARY.md) before writing DDL, migrations, or ORM entities.
- **HR Administrators & Business Analysts:**
  - Review the [Business Process Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md) for step-by-step workflow stages, RACI matrices, and SLA timelines.
  - Review the [Business Rules Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md) for all 60 institutional policies, quota limits, and auto-lockout conditions.

---

## 4. Source Evidence Repository (`source-requirements/`)

The [`source-requirements/`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/) directory remains the permanent, untouched legal and institutional source of truth containing:
- **`source-requirements/Module-I/`**: Official Module I Requirement Briefs & Complete Narratives (PDF).
- **`source-requirements/Module-II/`**: Official Module II Recruitment SOPs, Narratives, and Visual Diagrams (PDF/JPEG).
- **`source-requirements/Module-III/`**: Official Module III Performance Management Briefs, Subsystems, and Workflows (PDF/JPEG).
- **`source-requirements/PROJECT_REQUIREMENTS_ANALYSIS.md`**: Foundational inception requirements extraction.
- **`source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md`**: Master approved technology architecture baseline.
