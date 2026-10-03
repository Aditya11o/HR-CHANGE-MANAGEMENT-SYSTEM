# University HR Change Management & Automation System

[![Architecture](https://img.shields.io/badge/Architecture-Modular%20Monolith-indigo.svg)](#system-architecture)
[![Frontend](https://img.shields.io/badge/Frontend-Next.js%20(App%20Router)-black.svg)](#technology-stack)
[![Styling](https://img.shields.io/badge/Styling-Vanilla%20CSS%20%7C%20CSS%20Modules-blue.svg)](#technology-stack)
[![Backend](https://img.shields.io/badge/Backend-NestJS%20(TypeScript)-ea284e.svg)](#technology-stack)
[![Database](https://img.shields.io/badge/Database-PostgreSQL%2016-336791.svg)](#technology-stack)
[![Real--Time](https://img.shields.io/badge/Real--Time-Socket.IO%20v4-010101.svg)](#technology-stack)
[![Documentation](https://img.shields.io/badge/Documentation-100%25%20Canonical-success.svg)](#documentation-sitemap)

> An enterprise-grade, institutional HR automation platform designed to serve as the single source of truth for university employee lifecycles, talent acquisition, dynamic organizational structures, two-level change approvals, and statutory academic performance evaluations.

---

## 1. Executive Overview

The **University HR Change Management & Automation System** eliminates administrative friction, insulates the university against statutory audit vulnerabilities, and automates deadline-driven academic and administrative operations across three cohesive modules:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   INSTITUTIONAL SYSTEM VISION                                    │
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

### Core Problems Solved
- **Elimination of Duplicate Data Entry:** Updates in employee service conditions or recruitment milestones automatically synchronize across digital personal dossiers, organization hierarchies, and the central university ERP.
- **Dynamic Organization Chart:** Instant, sub-second visual realignment of reporting trees upon designation, supervisor, or departmental modifications without manual diagramming.
- **Statutory Academic Compliance:** Strict segregation of Academic (UGC-compliant SCM panel with mandatory external experts) and Non-Academic (3-Round interviews) hiring tracks.
- **Three Independent Performance Tracks:** Group-D monthly ratings with automated 10th-of-month auto-lockouts, General Staff quarterly KRA/KPI cycles, and Faculty annual appraisals via statutory Evaluation Committee Meetings (ECM).

---

## 2. Institutional Invariants at a Glance

The entire engineering and documentation baseline is strictly grounded in frozen institutional mandates:

| Metric | Count | Governance Specification |
|---|:---:|---|
| **Atomic System Requirements** | **104** | [`docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) |
| **End-to-End Business Processes** | **59** | [`docs/02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md) |
| **Invariant Business Rules** | **60** | [`docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md) |
| **Granular Functional Specs (FRD)**| **152** | [`docs/03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md) |
| **Primary Conceptual Entities** | **33** | [`docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md) |
| **Relational Entity Mappings** | **41** | [`docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md) |
| **Logical Data Attributes** | **344** | [`docs/05-database/02-LOGICAL-DATA-DICTIONARY.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/02-LOGICAL-DATA-DICTIONARY.md) |
| **Institutional Governance Actors** | **16** | [`docs/08-security/01-SECURITY-AND-RBAC-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-security/01-SECURITY-AND-RBAC-SPECIFICATION.md) |

---

## 3. Repository Architecture

```
d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM\
│
├── README.md                                          ◄ [This Master Portal]
│
├── source-requirements/                               ◄ [PERMANENT LEGAL & INSTITUTIONAL SOURCE OF TRUTH]
│   ├── Module-I/                                      ◄ Official Requirement Briefs & Narrative Workflows (PDF)
│   ├── Module-II/                                     ◄ Recruitment Requirement Briefs, Narratives & Diagrams
│   ├── Module-III/                                    ◄ Performance Requirement Briefs & Workflow Diagrams
│   ├── PROJECT_REQUIREMENTS_ANALYSIS.md              ◄ Foundational Inception Requirements Extraction
│   └── TECHNOLOGY_ARCHITECTURE_BASELINE.md           ◄ Authoritative Technology Stack Baseline
│
└── docs/                                              ◄ [CANONICAL 10-DOMAIN DOCUMENTATION SUITE]
    ├── README.md                                      ◄ Detailed Documentation Sitemap & Reading Guide
    ├── 01-requirements/                               ◄ Software Requirements Specification (SRS)
    ├── 02-business-process/                           ◄ Business Processes, Workflows, RACI & Business Rules
    ├── 03-functional-requirements/                    ◄ Functional Requirements Document (152 FRDs)
    ├── 04-system-architecture/                        ◄ Modular Monolith Architecture & Real-Time ADR
    ├── 05-database/                                   ◄ Database Relational Design & 344-Attribute Data Dictionary
    ├── 06-design/                                     ◄ Official UI Design Tokens & Theme Specification
    ├── 07-api/                                        ◄ REST API Contracts & Socket.IO Event Payloads
    ├── 08-security/                                   ◄ 16-Actor Permission Matrix, JWT & Row-Level Security
    ├── 09-testing/                                    ◄ Test Strategy & 7 Critical Path Verification Suites
    └── 10-deployment/                                 ◄ Docker Compose, Environment Config & DevOps Runbook
```

---

## 4. Documentation Sitemap

The documentation is organized into 10 clean, focused domains:

| Domain | Specification Document | Key Contents & Responsibilities |
|---|---|---|
| **01. Requirements** | [Software Requirements Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/SOFTWARE-REQUIREMENTS-SPECIFICATION.md) | 104 Atomic Requirements, In-Scope/Out-of-Scope boundaries, Traceability Matrix, 11 Baseline TBDs, and `CONF-01` to `10` decisions. |
| **02. Processes** | [Business Process Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-SPECIFICATION.md) | 59 End-to-End Processes across Modules I, II, III & Cross-Module, 16-Actor RACI matrix, and automated SLA countdown matrix. |
| **02. Rules** | [Business Rules Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md) | 60 Invariant Business Rules, auto-lockout criteria, quota limits, and two-level approval gating controls. |
| **03. Functional** | [Functional Requirements Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md) | 152 Functional Requirements (`MOD1-REQ`, `MOD2-REQ`, `MOD3-REQ`, `SHR-REQ`), validation pipes, state transitions, and error handling. |
| **04. Architecture** | [System Architecture Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/01-SYSTEM-ARCHITECTURE-SPECIFICATION.md) | Modular Monolith topology, NestJS architecture, Next.js frontend, BullMQ background queues, Redis caching, and ERP outbox. |
| **04. ADR** | [Real-Time Communication ADR](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/04-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md) | Approved Architectural Decision Record selecting Socket.IO for live Org Chart invalidation and notifications. |
| **05. Database** | [Database Design & Schema Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md) | Single PostgreSQL engine with 4 domain schemas, 33 entities, 41 relationships, relational schema profiles, and indexing strategy. |
| **05. Dictionary** | [Logical Data Dictionary](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/05-database/02-LOGICAL-DATA-DICTIONARY.md) | Exhaustive 344-attribute specification covering all 33 entities with logical data types, nullability, defaults, and validations. |
| **06. Design** | [Official Design Tokens & Tokens Guide](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/06-design/DESIGN.md) | Official UI Design Tokens: curated palette, Inter typography, elevation, surface container hierarchies, and component styling rules. |
| **07. API** | [REST API & WebSocket Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-api/01-API-SPECIFICATION.md) | REST endpoint contracts (`/api/v1`), request/response JSON schemas, error handling envelopes, and Socket.IO events. |
| **08. Security** | [Security & RBAC Specification](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-security/01-SECURITY-AND-RBAC-SPECIFICATION.md) | Master 16-Actor Permission Matrix, JWT token lifecycle, sensitive salary masking, and Row-Level Security (RLS). |
| **09. Testing** | [Test Strategy & Verification Plan](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/09-testing/01-TEST-STRATEGY-AND-VERIFICATION-PLAN.md) | Multi-tier testing pyramid, automated CI/CD tooling, and 7 critical path test suites (10th auto-lock, 2-level approvals, SCM quorum). |
| **10. DevOps** | [Deployment & DevOps Guide](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/10-deployment/01-DEPLOYMENT-AND-DEVOPS-GUIDE.md) | Production Docker Compose configuration, `.env.example` parameter mapping, database migration runbook, and backup policies. |

---

## 5. Technology Stack

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   PRODUCTION TECHNOLOGY STACK                                    │
├───────────────────────────┬──────────────────────────────────────────────────────────────────────┤
│ Frontend Application      │ Next.js (App Router, React 19, TypeScript)                           │
│ Frontend Styling          │ Vanilla CSS, CSS Modules (*.module.css), CSS Variables (No Tailwind)│
│ Backend API Engine        │ NestJS (TypeScript, Modular Monolith Architecture)                   │
│ Relational Database       │ PostgreSQL 16 (Single DB with 4 Logical Domain Schemas)              │
│ Cache & Background Queues │ Redis 7 + BullMQ (SLA Countdowns, Auto-Lockouts, Background Sync)    │
│ Real-Time Communication   │ Socket.IO v4 (WebSocket with Long-Polling Fallback & Room Channels)  │
│ Binary Document Storage   │ S3-Compatible Object Store (MinIO in local dev, AWS S3 in prod)      │
│ Container Orchestration   │ Docker & Docker Compose                                              │
└───────────────────────────┴──────────────────────────────────────────────────────────────────────┘
```

---

## 6. Quick Start & Local Setup

### Prerequisites
- [Node.js](https://nodejs.org/) (v20 LTS or higher)
- [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/)
- [Git](https://git-scm.com/)

### Step 1: Clone the Repository
```bash
git clone https://github.com/University/HR-CHANGE-MANAGEMENT-SYSTEM.git
cd HR-CHANGE-MANAGEMENT-SYSTEM
```

### Step 2: Spin Up Infrastructure Containers
Start PostgreSQL, Redis, and MinIO via Docker Compose:
```bash
docker compose up -d database redis object-store
```

### Step 3: Configure Environment Variables
Copy and customize the environment file:
```bash
cp .env.example .env
```
*(Reference [`docs/10-deployment/01-DEPLOYMENT-AND-DEVOPS-GUIDE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/10-deployment/01-DEPLOYMENT-AND-DEVOPS-GUIDE.md) for full parameter definitions).*

### Step 4: Run Migrations and Seed Master Data
```bash
npm run migration:run
npm run seed:institutional-baseline
```

### Step 5: Start Local Development Servers
```bash
# Start backend API (Port 4000)
npm run start:backend:dev

# Start frontend application (Port 3000)
npm run start:frontend:dev
```
Access the application at `http://localhost:3000` and API documentation at `http://localhost:4000/api/v1`.

---

## 7. Institutional Governance & Compliance

- **University Grants Commission (UGC) Norms:** Faculty recruitment, statutory selection panels (SCM), and annual performance assessments strictly observe national higher education regulatory guidelines.
- **Audit Defensibility:** Complete, immutable, append-only audit ledgers guarantee that every personnel modification is reconstructible and legally defensible.
- **Separation of Duties:** Built-in RBAC prevents self-approval and enforces sequential two-level sign-offs across academic and administrative hierarchies.

---

## 8. License & Ownership

Confidential & Proprietary. Developed for University Administration & Human Resources Operations. All rights reserved.
