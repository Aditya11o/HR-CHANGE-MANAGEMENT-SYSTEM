# University HR Change Management & Automation System
## Central Documentation Portal & System Architecture

Welcome to the authoritative documentation portal for the **University HR Change Management & Automation System**. This repository documents the complete end-to-end specifications, workflows, architecture, database models, design tokens, API interfaces, security policies, verification plans, and DevOps runbooks for the university's HR digital platform.

---

## 1. System Vision & Architecture Overview

The platform serves as the unified **digital backbone** for the employee lifecycle, connecting three core functional modules and shared platform services:

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#1e293b', 'primaryTextColor': '#f8fafc', 'primaryBorderColor': '#38bdf8', 'lineColor': '#64748b', 'secondaryColor': '#0f172a', 'tertiaryColor': '#1e293b'}}}%%
flowchart TD
    %% -------------------------------------------------------------
    %% STYLING DEFINITIONS
    %% -------------------------------------------------------------
    classDef modPurple fill:#2e1065,stroke:#a855f7,stroke-width:2px,color:#f8fafc;
    classDef modBlue fill:#0c4a6e,stroke:#38bdf8,stroke-width:2px,color:#f8fafc;
    classDef modGreen fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#f8fafc;
    classDef databaseNode fill:#1e1b4b,stroke:#818cf8,stroke-width:3px,color:#ffffff;
    classDef decisionNode fill:#701a75,stroke:#f472b6,stroke-width:2px,color:#ffffff;
    classDef actionNode fill:#1e293b,stroke:#94a3b8,stroke-width:1.5px,color:#ffffff;

    %% -------------------------------------------------------------
    %% MODULE II: TALENT ACQUISITION
    %% -------------------------------------------------------------
    subgraph MOD2 ["MODULE II: TALENT ACQUISITION & WORKFORCE PLANNING"]
        direction TB
        M2_REQ["<b>Manpower Planning & Requisitions</b><br/><i>• Academic: 4-Month Pre-Semester Lead<br/>• Non-Academic: Annual Headcount Quota</i>"]:::modPurple
        M2_SRC["<b>Omnichannel Ingestion & UGC Vetting</b><br/><i>• Portal, Job Boards & Campus Drives<br/>• UGC 2018 Minimum Eligibility Filter</i>"]:::modPurple
        M2_SEL["<b>Statutory Selection & Evaluation</b><br/><i>• Academic: Selection Committee Meeting (SCM)<br/>• Non-Academic: 3-Round Assessment Matrix</i>"]:::modPurple
        M2_LOI["<b>Offer & LOI Issuance</b><br/><i>• Automated Formal Letter of Intent<br/>• Pipeline & Notice Period Tracking</i>"]:::modPurple

        M2_REQ --> M2_SRC --> M2_SEL --> M2_LOI
    end

    %% -------------------------------------------------------------
    %% MODULE I: CORE REPOSITORY & CHANGE MANAGEMENT ENGINE
    %% -------------------------------------------------------------
    subgraph MOD1 ["MODULE I: CORE REPOSITORY & SERVICE CHANGE ENGINE"]
        direction TB
        M1_CDB[("<b>Central Employee Master Database</b><br/><i>Authoritative Single Source of Truth<br/>(Bidirectional University ERP Sync)</i>")]:::databaseNode
        M1_ORG["<b>Dynamic Org Chart</b><br/><i>Interactive Hierarchy Canvas<br/>Instant Structural Realignment</i>"]:::modBlue
        M1_DOS["<b>Digital Employee Dossier</b><br/><i>Longitudinal Career History<br/>Immutable Statutory Records</i>"]:::modBlue
        M1_CHG["<b>10 Standardized Change Formats</b><br/><i>Salary, Designation, Supervisor,<br/>Dept, Level, Additional Duty</i>"]:::modBlue
        M1_APP{"<b>2-Level Sequential Approval</b><br/>• Level 1: HR Operations<br/>• Level 2: Senior Management"}:::decisionNode
        M1_EFF["<b>Effective Date Scheduler</b><br/><i>Automated Midnight Activation<br/>& Retrospective Journaling</i>"]:::actionNode

        M1_CDB <===> M1_ORG
        M1_CDB <===> M1_DOS
        M1_CHG --> M1_APP
        M1_APP -- " Approved " --> M1_EFF
        M1_EFF ==> M1_CDB
    end

    %% -------------------------------------------------------------
    %% MODULE III: PERFORMANCE MANAGEMENT ENGINE
    %% -------------------------------------------------------------
    subgraph MOD3 ["MODULE III: 3-TRACK PERFORMANCE MANAGEMENT ENGINE"]
        direction TB
        M3_GPD["<b>Track 1: Group-D / Band-I Staff</b><br/><i>• Monthly HOD Rating (1st–7th)<br/>• 8th–10th Grace -> 23:59 Auto-Lock<br/>• VP-Administration Final Approval</i>"]:::modGreen
        M3_KRA["<b>Track 2: General Administrative Staff</b><br/><i>• 30-Day Joint KRA/KPI Goal-Lock<br/>• Q1–Q4 Quarterly Review Cadence<br/>• Annual Consolidated Score Formulation</i>"]:::modGreen
        M3_ECM["<b>Track 3: University Faculty</b><br/><i>• Monthly 10th Eligibility Scan (≥12m)<br/>• 4-Unit Verification (Dean, R&D, Place, HR)<br/>• Statutory ECM Panel & TNU Matrix</i>"]:::modGreen
    end

    %% -------------------------------------------------------------
    %% INTER-MODULE LIFECYCLE HANDSHAKES
    %% -------------------------------------------------------------
    M2_LOI ==>|"<b>BP-XMOD-001: Day-1 Onboarding</b><br/><i>Converts Candidate -> Active Employee</i>"| M1_CDB
    M1_CDB ==>|"<b>BP-XMOD-003: Master Employment Baseline</b><br/><i>Syncs Eligibility, Grades & Hierarchy</i>"| MOD3
    MOD3 ==>|"<b>BP-XMOD-004: Appraisal Outcome Handshake</b><br/><i>Injects Verified Increments / Promotions</i>"| M1_CHG
    M1_CDB -.->|"<b>BP-XMOD-002: Resignation Bypass</b><br/><i>Auto-Generates Urgent Replacement MRF</i>"| M2_REQ
```

---

## 2. Master Documentation Directory (Complete End-to-End Suite)

The documentation is organized into ten cohesive, production-grade domain folders:

| # | Domain | Canonical Document | Description | Key Invariants Covered |
|---|---|---|---|---|
| **01** | **Requirements** | [`01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) | Unified Software Requirements Specification (SRS). | • 104 Atomic Requirements (`REQ-01` to `REQ-104`)<br>• 11 Baseline TBDs (`REQ-TBD-01` to `11`)<br>• Stakeholder Decisions (`CONF-01` to `10`)<br>• Full Traceability Matrix |
| **02** | **Business Processes** | [`02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md) | Comprehensive Business Process & Workflow Manual. | • 59 End-to-End Processes (`BP-M1`, `BP-M2`, `BP-M3`, `BP-XMOD`)<br>• 16-Actor Taxonomy & RACI Matrix<br>• Automated SLA Countdown Matrix |
| **02** | **Business Rules** | [`02-business-process/02-BUSINESS-RULES-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md) | Authoritative Catalogue of Institutional Governance Rules. | • 60 Invariant Business Rules (`BR-M1`, `BR-M2`, `BR-M3`, `BR-ENT`, `BR-XMOD`)<br>• Auto-Lockouts, Quotas & Gating Logic |
| **03** | **Functional Specs** | [`03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md) | Granular Functional Requirements Document (FRD). | • 152 Functional Requirements (`MOD1-REQ`, `MOD2-REQ`, `MOD3-REQ`, `SHR-REQ`)<br>• Inputs, State Transitions & Error Handling |
| **04** | **System Architecture** | [`04-system-architecture/01-SYSTEM-ARCHITECTURE-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/01-SYSTEM-ARCHITECTURE-SPECIFICATION.md) | Modular Monolith Architecture Specification. | • Next.js App Router & Vanilla CSS Modules<br>• NestJS Modular Monolith & Domain Event Bus<br>• BullMQ Queues, Redis Caching & Transactional Outbox |
| **04** | **Architecture Decision** | [`04-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md) | Approved Architectural Decision Record (ADR). | • Formal Technical Approval for Socket.IO Real-Time Push |
| **05** | **Database Design** | [`05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md) | Relational Schema Specification & Data Architecture. | • Single PostgreSQL Instance with 4 Domain Schemas<br>• 33 Primary Conceptual Entities (`ENT-*`)<br>• 41 Relational Foreign Key Mappings (`REL-*`)<br>• Indexing Strategy & Temporal Versioning |
| **05** | **Data Dictionary** | [`05-database/02-LOGICAL-DATA-DICTIONARY.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/02-LOGICAL-DATA-DICTIONARY.md) | Canonical Logical Data Dictionary. | • 344 Logical Attributes Specification across all 33 Entities with Data Types, Nullability, and Descriptions |
| **06** | **Design Tokens & UI** | [`06-design/DESIGN.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/06-design/DESIGN.md) | Official UI Design Tokens & Theme Specification. | • Curated Palette, Inter Typography, Elevation, Surface Containers & Component Rules |
| **07** | **API Contracts** | [`07-api/01-API-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-api/01-API-SPECIFICATION.md) | REST API & Real-Time WebSocket Specification. | • REST Endpoints for Auth, Modules I–III & Admin<br>• Request/Response Envelopes, Error Codes<br>• Socket.IO Events & Inbound/Outbound Payloads |
| **08** | **Security & RBAC** | [`08-security/01-SECURITY-AND-RBAC-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-security/01-SECURITY-AND-RBAC-SPECIFICATION.md) | Security, Identity & Access Governance Specification. | • Master 16-Actor Permission Matrix (CRUD/A)<br>• Stateless JWT Lifecycle & Refresh Rotation<br>• PII/Salary Masking & Row-Level Security (RLS) |
| **09** | **Testing & QA** | [`09-testing/01-TEST-STRATEGY-AND-VERIFICATION-PLAN.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/09-testing/01-TEST-STRATEGY-AND-VERIFICATION-PLAN.md) | Test Strategy & Quality Verification Plan. | • Multi-Tier Testing Pyramid (Unit, Integ, E2E)<br>• 7 Critical Path Test Suites (10th Auto-Lock, 2-Level Approvals, Quotas, SCM Quorum) |
| **10** | **DevOps & Deploy** | [`10-deployment/01-DEPLOYMENT-AND-DEVOPS-GUIDE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/10-deployment/01-DEPLOYMENT-AND-DEVOPS-GUIDE.md) | Infrastructure, Deployment & Operations Guide. | • Production Docker Compose Specification<br>• Complete `.env.example` Mapping<br>• Database Schema Migration Runbook & Backups |

---

## 3. Reading Guide by Stakeholder Role

- **University Leadership & Mentors:**
  - Start with Section 1 of the [SRS](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) for institutional goals and scope boundaries.
  - Review Section 5 of the [SRS](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) for the Stakeholder Confirmation Register (`CONF-01` to `CONF-10`).
- **Software Engineers & Developers:**
  - Read [System Architecture](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/01-SYSTEM-ARCHITECTURE-SPECIFICATION.md) for technology stack invariants, NestJS modular patterns, and queue setups.
  - Read [API Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-api/01-API-SPECIFICATION.md) for REST and WebSocket contracts.
  - Review [Design Tokens](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/06-design/DESIGN.md) for color palettes, typography, and styling variables.
  - Reference [Database Design](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md) and [Data Dictionary](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/02-LOGICAL-DATA-DICTIONARY.md) before writing DDL, migrations, or ORM entities.
- **QA & Verification Engineers:**
  - Read [Test Strategy](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/09-testing/01-TEST-STRATEGY-AND-VERIFICATION-PLAN.md) for critical path verification scenarios, automated test setup, and quality gates.
- **DevOps & Sysadmins:**
  - Read [Deployment Guide](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/10-deployment/01-DEPLOYMENT-AND-DEVOPS-GUIDE.md) for Docker Compose, environment configs, healthcheck probes, and backup schedules.
- **HR Administrators & Business Analysts:**
  - Review the [Business Process Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md) for step-by-step workflow stages, RACI matrices, and SLA timelines.
  - Review the [Business Rules Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md) for all 60 institutional policies, quota limits, and auto-lockout conditions.
  - Review [Security & RBAC](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-security/01-SECURITY-AND-RBAC-SPECIFICATION.md) for role permissions.

---

## 4. Source Evidence Repository (`source-requirements/`)

The [`source-requirements/`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/) directory remains the permanent, untouched legal and institutional source of truth containing:
- **`source-requirements/Module-I/`**: Official Module I Requirement Briefs & Complete Narratives (PDF).
- **`source-requirements/Module-II/`**: Official Module II Recruitment SOPs, Narratives, and Visual Diagrams (PDF/JPEG).
- **`source-requirements/Module-III/`**: Official Module III Performance Management Briefs, Subsystems, and Workflows (PDF/JPEG).
- **`source-requirements/PROJECT_REQUIREMENTS_ANALYSIS.md`**: Foundational inception requirements extraction.
- **`source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md`**: Master approved technology architecture baseline.

---

## 5. Proprietary & Confidential Notice

**Copyright (c) 2026 The Neotia University. All Rights Reserved.**

All specifications, process flows, data dictionaries, and architectural artifacts in this documentation suite are the confidential and proprietary intellectual property of **The Neotia University**. 

Unauthorized downloading, cloning, forking, reproduction, or distribution without prior explicit written authorization from the repository owner is strictly forbidden and subject to formal legal action.

**Official Inquiries:** [halderaditya632@gmail.com](mailto:halderaditya632@gmail.com)
