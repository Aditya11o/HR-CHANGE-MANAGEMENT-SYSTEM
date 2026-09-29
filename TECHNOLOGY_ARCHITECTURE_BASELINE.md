# University HR Change Management & Automation System
# Technology Architecture Baseline

**Document Name:** `TECHNOLOGY_ARCHITECTURE_BASELINE.md`  
**Status:** Approved Technical Architecture Baseline  
**Project:** University HR Change Management & Automation System (Modules I, II, & III)  
**Authoritative Requirements Baseline:** [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md)  
**Date of Baseline Approval:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

# 1. Purpose and Scope

### 1.1 Purpose
This document establishes the official, approved **Technical Architecture Baseline** for the University HR Change Management & Automation System. Its primary purpose is to define the technical parameters, architectural style, component boundaries, data management principles, and integration contracts that will govern all subsequent documentation phases—including Functional Specifications (FSD/SRS), Domain Models, Database Schemas (ERD), API Specifications, UI/UX Design Specifications, and Deployment Plans.

This baseline bridges the authoritative business and functional requirements documented in [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) with sound, scalable, and maintainable software engineering practices.

### 1.2 Scope
This technical architecture baseline governs the entire solution lifecycle across the three currently commissioned modules and cross-cutting shared capabilities:
- **Module I — HR Change Management & Automation System:** Central Employee Database, Dynamic Organization Chart, 10 employee data change formats, 2-level approval hierarchy, effective-date scheduling engine, audit trail, version history, and ERP reflection.
- **Module II — Recruitment & Selection Automation System:** Academic Manpower Planning (Faculty & Lab Technicians), Non-Academic Manpower Planning (Staff), Urgent Replacement (Resignation) pipeline, Open Positions Tracker, multi-channel sourcing, Central CV Database, automated screening against UGC norms, Recruiter Calling Sheet (RCS), Statutory Selection Committee Meetings (SCM), 3-round Non-Faculty interviews, Letter of Intent (LOI) generation, and "Yet to Join" onboarding integration.
- **Module III — Performance Management Automation System:** Preservation and independent technical execution of three distinct appraisal tracks:
  1. *Group-D / Band I Monthly & Annual Appraisal Workflow*
  2. *KRA/KPI Appraisal Lifecycle (General Staff)*
  3. *Faculty Annual Appraisal via Evaluation Committee Meeting (ECM Route)*
- **Shared Platform Infrastructure:** Identity & Access Management (IAM), Role-Based Access Control (RBAC), Workflow & State Machine Engine, SLA & Timeline Engine, Asynchronous Job Scheduler, Notification Management, Document & File Storage, Audit & Versioning Engine, Real-Time Reporting, and Real-Time Communication Layer (Socket.IO).

### 1.3 Governance Directive
No subsequent functional or technical document may introduce architectural patterns, frameworks, or database engines that contradict this approved baseline without formal change-control approval. Application scaffolding, database migration creation, and code implementation are strictly prohibited during this documentation-only phase.

---

# 2. Architecture Principles

The design of the system is guided by twelve core architectural principles:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             CORE ARCHITECTURAL PRINCIPLES                                        │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 1. Requirement-Driven Design  │ 2. Modular Monolith Architecture│ 3. Strict Separation of Concerns│
│ • Architecture derived from   │ • Clean domain boundaries      │ • Decoupled UI, API, domain,   │
│   authoritative documents     │ • In-process high cohesion     │   and persistence layers        │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 4. Security & Least Privilege │ 5. Comprehensive Auditability  │ 6. End-to-End Traceability      │
│ • Zero trust within domains   │ • Immutable append-only logs   │ • Every component mapped to     │
│ • Strict role-based scoping   │ • Temporal before/after states │   explicit Requirement IDs      │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 7. Relational Data Integrity  │ 8. Workflow Consistency        │ 9. High Reusability & DRY       │
│ • ACID guarantees via Postgres│ • Explicit state machines      │ • Shared engines for SLAs,      │
│ • Strict foreign key topology │ • Guarded state transitions    │   workflows, and notifications  │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 10. Maintainability & Quality │ 11. Pragmatic Scalability      │ 12. Controlled Extensibility    │
│ • Strong typing (TypeScript)  │ • Stateless app instances      │ • Dynamic form schemas &        │
│ • Self-documenting modularity │ • Dedicated background queues  │   configurable report views     │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

1. **Requirement-Driven Architecture:** Every architectural module, data flow, and service boundary must map directly to an explicit requirement or a necessary logical implication established in [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md). No unrequested technical complexity may be introduced.
2. **Modular Monolith Architecture:** The backend is architected as a cohesive, single-deployable Modular Monolith. Strict module boundaries, clear public interfaces, and encapsulated internal domain logic ensure high cohesion and low coupling without the distributed systems overhead of microservices.
3. **Strict Separation of Concerns:** Clear demarcation between Presentation (Next.js), Application/Domain Logic (NestJS), Persistence (PostgreSQL), Caching/Queueing (Redis), and File Storage (Object Storage).
4. **Security by Design:** Enforce authentication, fine-grained Role-Based Access Control (RBAC), row-level data scoping, and encrypted transport/storage across all layers. External actors (such as statutory SCM experts) must be strictly isolated to their assigned evaluation records.
5. **Comprehensive Auditability & Temporal History:** No historical data is ever destructively overwritten. Every master data change, evaluation score, and approval action must be time-stamped, attributed to an actor, and version-controlled with effective-date temporal tracking.
6. **End-to-End Traceability:** Architectural components, database entities, and API contracts must retain traceable links back to source requirement IDs (`MOD1-*`, `MOD2-*`, `MOD3-*`).
7. **Relational Data Integrity:** ACID transaction guarantees are strictly enforced via PostgreSQL. Relational foreign keys and unique constraints maintain consistency across employee masters, org hierarchies, and recruitment funnels.
8. **Workflow Consistency:** All multi-step processes (change requests, requisition vetting, multi-stage interviews, monthly evaluations, quarterly KRA reviews, and ECM approvals) are modeled as deterministic finite state machines with strict transition guards.
9. **Component Reusability:** Core capabilities—such as the SLA engine, reminder scheduler, notification dispatcher, document manager, and audit logger—are implemented as reusable core services consumed uniformly by all functional modules.
10. **Maintainability & Strong Typing:** End-to-end type safety using TypeScript across frontend and backend minimizes runtime errors and provides clear data contracts.
11. **Pragmatic Scalability:** Stateless application processes scale horizontally behind a reverse proxy, while I/O-heavy operations (PDF rendering, email dispatching, SLA monitoring) are offloaded to asynchronous background workers.
12. **Controlled Extensibility:** Evaluation forms, report definitions, and change formats must support configuration and versioning by authorized HR administrators without requiring codebase rewrites.

---

# 3. Approved Technology Stack

The following technology selections represent the official and approved architectural baseline:

| Layer | Approved Technology | Architectural Purpose | Status | Technical Notes |
|---|---|---|---|---|
| **Frontend Framework** | **Next.js** | Server-Side Rendering (SSR), Static Site Generation (SSG), and Client-Side Hydration for responsive HR dashboards, portals, and applicant review interfaces. | **APPROVED BASELINE** | React-based, utilizing App Router architecture with clean separation of Server and Client components. |
| **Frontend Language** | **TypeScript** | Strict compile-time type safety across UI components, state management, form handlers, and API client DTOs. | **APPROVED BASELINE** | Shared types/interfaces aligned with backend API contracts. |
| **Styling & Design** | **Vanilla CSS + CSS Modules + CSS Variables** | Scoped component styling, design token management (color palettes, typography, spacing, elevations), and dynamic light/dark theming. | **APPROVED BASELINE** | Full visual control without utility framework lock-in. Zero CSS runtime overhead; strictly scoped via `*.module.css`. |
| **UI Component System** | **Custom Design System** | Bespoke, accessible, university-branded UI library (data tables, modals, workflow steppers, org tree renderers, score sheets). | **APPROVED BASELINE** | Designed specifically for University workflows. Eliminates third-party template bloat and enforces accessibility standards. |
| **Backend Framework** | **NestJS** | Enterprise-grade, modular Node.js framework providing dependency injection, routing, validation pipes, interceptors, and guards. | **APPROVED BASELINE** | Implements the Modular Monolith pattern with strong domain encapsulation and structured module boundaries. |
| **Backend Language** | **TypeScript** | Strongly-typed enterprise application programming language across all backend controllers, services, repositories, and domain models. | **APPROVED BASELINE** | Strict mode enabled; enforces interface compliance and compile-time verification. |
| **API Protocol** | **REST API** | Standardized, resource-oriented HTTP/JSON communication protocol for client-to-server and integration interactions. | **APPROVED BASELINE** | OpenAPI / Swagger specification documentation for all endpoints; strict DTO validation via class-validator. |
| **Real-Time Communication Layer** | **Socket.IO (over WebSocket)** | Server-to-client live event push for approval queue counters, SLA warnings, dynamic org-chart invalidation, and in-app alerts. | **APPROVED BASELINE** | NestJS Gateway (@nestjs/platform-socket.io) + socket.io-client. Scales horizontally via @socket.io/redis-adapter. Ephemeral notification channel; REST remains primary. |
| **Primary Database** | **PostgreSQL** | Relational System of Record providing ACID compliance, complex joins, foreign keys, temporal logging, and JSONB for configurable forms. | **APPROVED BASELINE** | Supports robust indexing, transactional consistency, window functions for reporting, and row-level locking. |
| **Caching & In-Memory Store** | **Redis** | High-performance in-memory data store for caching reference data (org tree, role permissions) and backing job queues. | **APPROVED BASELINE** | Key-value caching with TTLs; distributed locking where needed; backing broker for asynchronous workers. |
| **Background Queue / Workers** | **Background Workers / Scheduler (e.g., BullMQ / NestJS Schedule)** | Asynchronous execution of temporal SLA countdowns, auto-locks, reminder notifications, PDF generation, and ERP sync. | **APPROVED BASELINE** | Decouples long-running and periodic background jobs from synchronous HTTP request/response lifecycles. |
| **Document & Object Storage** | **Object Storage (S3-Compatible API)** | Scalable, durable binary storage for candidate resumes, research papers, evaluation evidence, and auto-generated PDF letters. | **APPROVED BASELINE** | Application manages metadata in PostgreSQL; binary files stored in object storage accessed via time-limited presigned URLs. |
| **Notification Infrastructure** | **Notification Service** | Multi-channel dispatch engine for transactional emails, system alerts, SLA warnings, and calendar invitations. | **APPROVED BASELINE** | Queue-backed, asynchronous dispatch with templating engine and delivery audit logs. |
| **Audit & Versioning** | **Audit & Versioning Service** | Immutable append-only audit trail capturing actor, timestamp, prior state, updated state, and temporal effective dates. | **APPROVED BASELINE** | Embedded within PostgreSQL via dedicated audit tables and entity interceptors. |
| **Reporting & Analytics** | **Reporting Layer** | Aggregation and compilation engine for real-time dashboards, Excel exports, and statutory compliance reports. | **APPROVED BASELINE** | Optimized SQL read-views, aggregation queries, and streaming tabular exports. |

---

# 4. Explicitly Rejected / Excluded Technologies

To ensure architectural clarity, consistency, and focus, the following technologies and architectural styles are **explicitly excluded from the current baseline**:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                EXCLUDED FROM CURRENT BASELINE                                    │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│        TAILWIND CSS           │            SHADCN UI           │    MICROSERVICES ARCHITECTURE   │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ • Excluded in favor of        │ • Excluded in favor of a       │ • Excluded in favor of a        │
│   Vanilla CSS, CSS Modules,   │   custom-crafted University UI │   Modular Monolith              │
│   and CSS Custom Properties   │   Component / Design System    │ • Eliminates distributed txns,  │
│ • Guarantees complete scoping │ • Tailored specifically to     │   network latency, and complex  │
│   and custom visual identity  │   academic workflow ergonomics │   operational overhead          │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

### 4.1 Tailwind CSS
- **Status:** **EXCLUDED FROM CURRENT BASELINE**.
- **Architectural Rationale:** The approved frontend design architecture mandates **Vanilla CSS**, **CSS Modules** (`*.module.css`), and **CSS Variables** (Custom Properties) organized into a structured Design System. This decision ensures:
  1. Complete isolation and scoping of styles to specific UI components without global utility class namespace pollution.
  2. Direct control over semantic design tokens (typography scales, formal university brand palettes, spacing grids, and high-contrast accessibility themes).
  3. Clean, readable JSX markup unencumbered by lengthy utility class strings.
  4. Elimination of third-party CSS build plugins and toolchain dependencies.
- **Future Re-evaluation:** This exclusion applies strictly to the current approved baseline. If a future enterprise standard mandates utility CSS, it may be evaluated under formal change control.

### 4.2 Shadcn UI
- **Status:** **EXCLUDED FROM CURRENT BASELINE**.
- **Architectural Rationale:** Pre-packaged component libraries like Shadcn UI are optimized for generic SaaS applications and carry assumptions regarding utility styling (Tailwind) and generic layout paradigms. In contrast, the University HR platform demands:
  1. Specialized, enterprise-academic UI primitives (e.g., hierarchical Organization Chart visualizers, multi-member statutory Evaluation Matrix score sheets, multi-stage approval steppers, and multi-channel CV intake kanbans).
  2. Full ownership of component accessibility (WCAG 2.1 AA), focus management, keyboard navigation, and semantic HTML structure.
  3. Seamless integration with our approved CSS Modules and CSS Variables token architecture.
- **Future Re-evaluation:** Excluded from the current baseline; custom components will be built to precise functional specifications.

### 4.3 Microservices Architecture
- **Status:** **EXCLUDED FROM CURRENT BASELINE**.
- **Architectural Rationale:** Decomposing the system into distributed microservices at this stage is fundamentally rejected due to:
  1. *Unjustified Distributed Systems Complexity:* Microservices introduce network latency, distributed transaction failure modes (requiring 2-Phase Commit or Saga orchestrators), eventual consistency anomalies, and significant operational/DevOps overhead.
  2. *Cross-Domain Data Integrity:* Key university business processes—such as finalizing an annual appraisal outcome and immediately feeding it into Module I master employee records—require atomic database transactions (`ACID`). A Modular Monolith allows these operations to occur within a single database transaction boundary.
  3. *Organizational Alignment:* The current scale, development team structure, and deployment requirements are optimal for a highly disciplined **Modular Monolith**.
- **Modular Monolith as the Strategic Choice:** The system will enforce strict logical module boundaries within NestJS. If, in the future, a specific domain (e.g., CV Sourcing & Parsing) experiences disproportionate compute load, its clean boundaries will allow it to be extracted into a separate service without re-architecting the entire application.

---

# 5. High-Level System Architecture

The following diagram illustrates the complete high-level system architecture, showing the interaction between client actors, the frontend presentation layer, the REST API gateway, the NestJS Modular Monolith backend, the persistence tier, and supporting infrastructure:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                       USER ACCESS CHANNELS                                       │
│    (HR Admins, Deans, HODs, Faculty, Staff, Group-D Supervisors, Management, External Experts)  │
└───────────────────────────────────────────────┬──────────────────────────────────────────────────┘
                                                │ HTTPS / WSS
                                                ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               NEXT.JS FRONTEND PRESENTATION TIER                                 │
│  ┌─────────────────────────┐  ┌───────────────────────────┐  ┌────────────────────────────────┐  │
│  │   Server Components     │  │     Client Components     │  │      Custom Design System      │  │
│  │   (SSR Dashboards,      │  │     (Interactive Forms,   │  │   (CSS Modules, CSS Variables, │  │
│  │    Rosters, Read Views) │  │      Score Sheets, Trees) │  │    University Brand Tokens)    │  │
│  └─────────────────────────┘  └───────────────────────────┘  └────────────────────────────────┘  │
└───────────────────────────────────────────────┬──────────────────────────────────────────────────┘
                                                │ REST API (JSON / HTTPS)
                                                ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             NESTJS MODULAR MONOLITH BACKEND TIER                                 │
│                                                                                                  │
│  ┌────────────────────────────────────────────────────────────────────────────────────────────┐  │
│  │                         API GATEWAY / MIDDLEWARE LAYER                                     │  │
│  │   • Global Authentication Guard (JWT / Session)     • Role & Permission Guards (RBAC)      │  │
│  │   • Validation Pipes (DTO Schema Enforcement)       • Audit Logging Interceptor            │  │
│  └─────────────────────────────────────────────┬──────────────────────────────────────────────┘  │
│                                                │                                                 │
│  ┌─────────────────────────────────────────────┴──────────────────────────────────────────────┐  │
│  │                             CORE DOMAIN MODULES (IN-PROCESS)                               │  │
│  │  ┌─────────────────────────┐  ┌───────────────────────────┐  ┌───────────────────────────┐ │  │
│  │  │   EmployeeCoreModule    │  │   OrganizationModule      │  │  ChangeManagementModule   │ │  │
│  │  │  (Central Master DB)    │  │  (Dynamic Org Chart)      │  │  (10 Formats, Effective)  │ │  │
│  │  └─────────────────────────┘  └───────────────────────────┘  └───────────────────────────┘ │  │
│  │  ┌─────────────────────────┐  ┌───────────────────────────┐  ┌───────────────────────────┐ │  │
│  │  │   RecruitmentModule     │  │   CandidateCvModule       │  │  PerformanceMgmtModule    │ │  │
│  │  │ (Manpower, SCM, 3-Round)│  │ (Multi-Channel, Screening)│  │ (Group-D, KRA, Fac-ECM)   │ │  │
│  │  └─────────────────────────┘  └───────────────────────────┘  └───────────────────────────┘ │  │
│  │  ┌─────────────────────────┐  ┌───────────────────────────┐  ┌───────────────────────────┐ │  │
│  │  │   WorkflowEngineModule  │  │   SlaTimelineModule       │  │    ErpAdapterModule       │ │  │
│  │  │ (State Machine, Approvals│ │ (Timers, Cutoffs, Locks)  │  │  (ERP Reflection / Sync)  │ │  │
│  │  └─────────────────────────┘  └───────────────────────────┘  └───────────────────────────┘ │  │
│  └─────────────────────────────────────────────┬──────────────────────────────────────────────┘  │
│                                                │                                                 │
│  ┌─────────────────────────────────────────────┴──────────────────────────────────────────────┐  │
│  │                             SHARED INFRASTRUCTURE SERVICES                                 │  │
│  │   • AuditService          • NotificationService        • DocumentService (Object Store)    │  │
│  │   • ReportingService      • PdfGenerationService       • CacheService (Redis)              │  │
│  └───────────────────────┬─────────────────────┬──────────────────────┬───────────────────────┘  │
└──────────────────────────┼─────────────────────┼──────────────────────┼──────────────────────────┘
                           │                     │                      │
                           ▼                     ▼                      ▼
┌───────────────────────────────┐ ┌───────────────────────────┐ ┌──────────────────────────────────┐
│      POSTGRESQL DATABASE      │ │      REDIS CACHE & QUEUE  │ │      OBJECT STORAGE (S3-COMP)    │
│  • System of Record           │ │  • Reference Data Cache   │ │  • Candidate Resumes / CVs       │
│  • Master Employee Ledger     │ │  • Org Tree Cache         │ │  • Appraisal Supporting Evidence │
│  • Transactional State Data   │ │  • BullMQ Background Jobs │ │  • Generated Letters (LOI, ECM)  │
│  • Temporal Audit Logs        │ │  • Distributed Locks      │ │  • Standardized Form Templates   │
│  • Configurable Form Schemas  │ │  • Session Revocation     │ │  • Presigned URL Secure Access   │
└───────────────────────────────┘ └─────────────┬─────────────┘ └──────────────────────────────────┘
                                                │
                                                ▼
                                  ┌───────────────────────────┐
                                  │   BACKGROUND WORKERS      │
                                  │  • SLA Countdown Monitor  │
                                  │  • 7th/10th Lockout Cron  │
                                  │  • Effective Date Engine  │
                                  │  • Outbound Email Dispatch│
                                  │  • Async PDF Compiler     │
                                  │  • ERP Sync Event Worker  │
                                  └───────────────────────────┘
```

---

# 6. Backend Modular Architecture

Within the NestJS Modular Monolith, domain boundaries are strictly maintained. Modules communicate through explicit service interfaces, shared TypeScript DTOs, or in-process domain events. Direct cross-module database writes are strictly prohibited.

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                          LOGICAL BACKEND MODULES & DOMAIN BOUNDARIES                             │
├────────────────────┬─────────────────────────────────────────────────────────────────────────────┤
│ Module Name        │ Architectural Responsibility & Bounded Context                              │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **IamModule**      │ Authentication, JWT issuance, session lifecycle, password policies, MFA,    │
│                    │ RBAC role assignment, and external expert secure temporary token handling.  │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **EmployeeCore**   │ Master Employee Database, employee identity, demographic data, service       │
│ **Module**         │ history, current compensation, band/grade, probation status, and DOJ.       │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **Organization**   │ University organizational hierarchy, Schools, Departments, Programs,        │
│ **Module**         │ designation topologies, and dynamic parent-child reporting lines.           │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **ChangeManagement**│ Lifecycle of all 10 employee service-condition change formats, effective-   │
│ **Module**         │ date scheduling engine, and downstream propagation to master tables.        │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **Recruitment**    │ Manpower planning (Academic & Non-Academic), ad-hoc replacement workflow,   │
│ **Module**         │ MRF lifecycle, SCM committee coordination, 3-round interviews, LOIs.        │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **CandidateCv**    │ Omnichannel CV intake, central CV database, automatic classification,       │
│ **Module**         │ criteria/UGC compliance screening, and Recruiter Calling Sheet (RCS) engine. │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **Performance**    │ Orchestrator for performance domains, encapsulating 3 distinct sub-modules: │
│ **ManagementModule**│ (1) Group-D Monthly/Annual, (2) KRA/KPI Staff, and (3) Faculty ECM.        │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **WorkflowEngine** │ Generic, configurable finite state machine executing status transitions,     │
│ **Module**         │ approval hierarchies, role-based transition guards, and approval history.   │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **SlaTimeline**    │ Calculation and monitoring of deadlines, warning thresholds, escalation    │
│ **Module**         │ triggers, grace periods, and hard auto-locks across all workflows.          │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **Notification**   │ Multi-channel notification dispatch (Email, In-App alerts), message         │
│ **Module**         │ templating, delivery queueing, retry logic, and dispatch logging.          │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **DocumentModule** │ File upload validation, object storage abstraction, metadata indexing,     │
│                    │ access authorization, and secure presigned URL generation.                  │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **AuditModule**    │ Global change interception, immutable append-only audit logging, before/    │
│                    │ after state diffing, actor attribution, and historical version queries.     │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **ReportingModule**│ Real-time and scheduled aggregation queries, dynamic report generation,     │
│                    │ export formatting (Excel/CSV/JSON), and recruitment/appraisal funnel stats.  │
├────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ **ErpAdapterModule**│ Outbound event staging, transformation to ERP schema, idempotent dispatch,  │
│                    │ synchronization status tracking, and reconciliation retry mechanisms.       │
└────────────────────┴─────────────────────────────────────────────────────────────────────────────┘
```

### Module Encapsulation Rule
Each module encapsulates its own:
- **Controllers:** Handling HTTP requests, validating incoming DTOs, and mapping responses.
- **Services:** Executing business rules, transactions, and domain validations.
- **Repositories / Entities:** Managing PostgreSQL relational mappings within its domain schema.
- **DTOs:** Defining strongly-typed request and response contracts.
- **Events:** Emitting domain events (e.g., `EmployeeResignedEvent`, `AppraisalApprovedEvent`, `CandidateAcceptedLoiEvent`) across the in-process NestJS event bus to trigger cross-module workflows cleanly.

---

# 7. Module I Technical Mapping

The requirements of Module I (HR Change Management & Automation System) are mapped to technical components as follows:

| Functional Requirement | Traceability ID | Architectural Component | Backend Module | Persistence / Infrastructure | Technical Execution Pattern |
|---|---|---|---|---|---|
| **Central Database of all Employees** | `MOD1-CDB-01` | Master Employee Entity & Ledger | `EmployeeCoreModule` | PostgreSQL (`employees`, `employee_service_history`) | Single source of truth. ACID transactional updates. Relational foreign keys for department, designation, and reporting supervisor. |
| **Dynamic Organization Chart** | `MOD1-ORG-01` | Org Hierarchy Builder & Visualizer API | `OrganizationModule` | PostgreSQL + Redis (Tree Cache) | Adjacency list / closure table hierarchy model. Real-time cache invalidation on reporting changes. D3-compatible hierarchical JSON output. |
| **10 Service Change Formats** | `MOD1-CHG-01` | Polymorphic Change Request Engine | `ChangeManagementModule` | PostgreSQL (`change_requests`, `change_details_jsonb`) | Standardized base entity with type-specific validation pipes for Salary, Designation, Reportee, Supervisor, Level, School, Location, etc. |
| **2-Level Approval Hierarchy** | `MOD1-APP-01` | Two-Stage Approval State Machine | `WorkflowEngineModule` | PostgreSQL (`workflow_instances`, `approval_actions`) | Sequential state transitions: `SUBMITTED` → `HR_REVIEW` → `MANAGEMENT_APPROVAL` → `APPROVED`. Role guards enforce authorization. |
| **Effective-Date Processing** | `MOD1-DAT-01` | Temporal Scheduler & Activation Engine | `ChangeManagementModule` + `SlaTimelineModule` | Background Worker (BullMQ / Cron) | Requests with future `effective_date` stored in `APPROVED_PENDING_ACTIVATION`. Daily midnight worker commits active changes to master tables. |
| **Audit Trail & Version History** | `MOD1-DAT-01` | Immutable Audit Ledger & Version Interceptor | `AuditModule` | PostgreSQL (`audit_logs`, `entity_versions`) | NestJS interceptor captures `user_id`, timestamp, IP, `pre_state`, and `post_state`. Snapshot stored on every update. |
| **ERP Reflection / Integration** | `MOD1-CDB-01` | ERP Outbound Event Adapter | `ErpAdapterModule` | PostgreSQL (`erp_outbox`) + Worker | Transactional Outbox Pattern: committing change writes an outbox record; background worker delivers payload to ERP with retry and backoff. |
| **Real-Time Reporting** | `MOD1-REP-01` | Dynamic Query Builder & View Engine | `ReportingModule` | PostgreSQL Views + Read Queries | Direct indexed queries against master and history tables. Dynamic filtering, column selection, and CSV/Excel streaming. |

---

# 8. Module II Technical Mapping

Module II (Recruitment & Selection Automation System) encompasses two distinct recruitment pipelines, an urgent replacement path, shared candidate sourcing, statutory interview processes, and pre-onboarding integrations:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               MODULE II TECHNICAL ARCHITECTURE                                   │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                 SHARED SOURCING & CV ENGINE                                      │
│   • Ingestion Gateway (Webhooks, Email Parser, File Uploads, Referral Forms)                     │
│   • Central CV Storage (Object Storage + PostgreSQL `candidates` metadata)                       │
│   • Rules Engine: Automated UGC Norms & Educational Criteria Screening                           │
│   • Recruiter Calling Sheet (RCS) Sub-Module & HOD-HR Review Queue                                │
├────────────────────────────────┬─────────────────────────────────┬───────────────────────────────┤
│    ACADEMIC TRACK (SCM)        │     NON-ACADEMIC TRACK          │      URGENT REPLACEMENT       │
├────────────────────────────────┼─────────────────────────────────┼───────────────────────────────┤
│ • 4-Month Semester Trigger     │ • 4-Month Annual Trigger        │ • Resignation Event Hook      │
│ • Teaching Load (Att. 1) Vetting│ • Annual MRF (1 planned/year)   │ • Replacement Clock Engine    │
│ • Pro-Chancellor Approval Gate │ • Head HR & Pro-Chancellor Gate │ • Fast-track Ad-hoc MRF       │
│ • Statutory SCM Invitation     │ • 3-Round Interview Engine:     │ • Monitored SCM / Interview   │
│   Portal & External Tokens     │   (Technical, HR, Management)   │   Execution Block             │
│ • Digital Scoring & Matrix     │ • Multi-attribute Score Sheets  │ • Onboarding Closeout &       │
│   Compilation (Management)     │ • Direct LOI Auto-Generation    │   Open Positions Sync         │
└────────────────────────────────┴─────────────────────────────────┴───────────────────────────────┘
```

### Detailed Component Mapping

| Functional Requirement | Traceability ID | Architectural Component | Backend Module | Persistence / Infrastructure | Technical Execution Pattern |
|---|---|---|---|---|---|
| **Academic Manpower Planning** | `MOD2-MP-FAC-01`, `MOD2-MP-FAC-02` | Semester Requisition Engine | `RecruitmentModule` | PostgreSQL (`manpower_plans`, `teaching_loads`) | Scheduled 4-month trigger. 15-day submission deadline. Associate Dean vetting >= 3 months prior. 15-day consolidation to Pro-Chancellor. |
| **Non-Academic Manpower Planning** | `MOD2-MP-NF-01` | Annual Requisition Engine | `RecruitmentModule` | PostgreSQL (`manpower_plans`, `mrfs`) | Annual 4-month trigger. Enforces strict limit of 1 planned MRF per department per year. Head HR vetting → Pro-Chancellor approval. |
| **Urgent Replacement Workflow** | `MOD2-RES-01` | Resignation Replacement Tracker | `RecruitmentModule` + `SlaTimelineModule` | PostgreSQL + Background Workers | Ingests `EmployeeResignedEvent` from Module I. Starts replacement countdown timer. Manages ad-hoc MRF through approval and sourcing. |
| **Open Positions Tracker** | `MOD2-POS-01` | Requisition Ledger (Attachment 3) | `RecruitmentModule` | PostgreSQL (`open_positions_tracker`) | Auto-updated on MRF approval (within 30 days). Real-time position status (`OPEN`, `SOURCING`, `INTERVIEWING`, `OFFERED`, `FILLED`). |
| **Central CV Database & Sourcing** | `MOD2-SRC-01` | Multi-Channel Intake Pipeline | `CandidateCvModule` | PostgreSQL (`candidates`, `applications`) + Object Storage | Parses and stores candidate profiles from email, social, website, referrals, and Internshala. Deduplication by email/phone. |
| **Screening & UGC Norms** | `MOD2-SRC-02` | Automated Screening Engine | `CandidateCvModule` | PostgreSQL + Rules Service | Rules-based filter evaluating degree qualification, minimum years of experience, and UGC compliance flags. |
| **Recruiter Calling Stage (RCS)** | `MOD2-RCS-01` | Recruiter Calling Sub-System | `CandidateCvModule` | PostgreSQL (`recruiter_call_records`) | Form for telephonic interview logging. Routes candidate dossier to HOD-HR for review and Management for pre-interview sign-off. |
| **Academic Selection (SCM)** | `MOD2-SEL-FAC-01` | Statutory SCM Portal | `RecruitmentModule` + `IamModule` | PostgreSQL (`selection_committees`, `scm_scores`) | Generates secure digital invitations and time-limited tokens for external subject experts. Online interview marks entry; auto-compiles Evaluation Matrix. |
| **Non-Academic Selection** | `MOD2-SEL-NF-01` | Three-Round Interview Engine | `RecruitmentModule` | PostgreSQL (`interview_rounds`, `round_scores`) | Sequential workflow: Round 1 (Technical) → Round 2 (HR) → Round 3 (Management). Captures scores for Job Knowledge, Communication, Attitude. |
| **LOI Generation & "Yet to Join"** | `MOD2-ONB-01` | Offer Generator & Pre-Onboarding Tracker | `RecruitmentModule` + `DocumentModule` | PostgreSQL + Object Storage | Auto-renders Letter of Intent PDF from template upon Management cost approval. Acceptance marks candidate as "Yet to Join"; notifies Deans, HODs, IT. |

---

# 9. Module III Technical Mapping

Module III comprises **three distinct, non-interchangeable performance management sub-systems**. In strict adherence to requirements, these workflows are maintained as separate domain services within the `PerformanceManagementModule`.

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                   MODULE III: PERFORMANCE MANAGEMENT ARCHITECTURE                                │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
            │                                     │                                    │
            ▼                                     ▼                                    ▼
┌───────────────────────┐             ┌───────────────────────┐            ┌───────────────────────┐
│     SUB-SYSTEM 1      │             │     SUB-SYSTEM 2      │            │     SUB-SYSTEM 3      │
│  GROUP-D / BAND I     │             │    KRA / KPI CYCLE    │            │     FACULTY (ECM)     │
│   (Monthly/Annual)    │             │  (General Staff / Q1) │            │ (Annual Committee)    │
├───────────────────────┤             ├───────────────────────┤            ├───────────────────────┤
│ • Monthly Form Engine │             │ • 30-Day Goal Setting │            │ • Auto-Eligibility   │
│ • 7th/10th Lockout    │             │ • 90-Day Review Engine│            │   Scanner (10th/mo)   │
│   Background Worker   │             │ • Q1-Q4 Recurrence    │            │ • 7-Day Self-Appraisal│
│ • VP-Admin Sign-Off   │             │ • TAT Analytics Engine│            │ • Multi-Dept Vetting  │
│ • Annual Weighted Calc│             │ • Direct Handshake    │            │ • Digital ECM Sheet   │
│ • Slabs & Probation   │             │   into Module I       │            │ • TNU Protocol Matrix │
└───────────────────────┘             └───────────────────────┘            └───────────────────────┘
```

---

### 9.1 Sub-System 1: Performance Management (Group-D / Band I)
- **Evaluation Form Repository:** Managed by `PerformanceManagementModule.GroupDService`. Configurable JSONB form schema capturing role-specific KPIs and operational competencies. Versioned in PostgreSQL (`group_d_form_templates`) with an immutable audit log (`MOD3-GD-EVAL-01`).
- **Monthly Evaluation Dispatch:** Scheduled cron on the 1st of every month instantiates forms for all active Group-D staff, pulling departmental reporting lines from `EmployeeCoreModule`.
- **SLA, Reminders, and Hard Auto-Lock:**
  - Due date: 7th of the month.
  - Automated grace period: up to the 10th.
  - Daily reminder jobs dispatch notifications to delinquent HODs.
  - **Auto-Lock Worker:** At 23:59 on the 10th, an automated background worker executes:
    `UPDATE evaluations SET status = 'NOT_SUBMITTED', locked = TRUE WHERE status = 'PENDING' AND period = :current_month`
    Flags record for HR review with failure reason (`MOD3-GD-EVAL-01`).
- **Approval Gateway:** HOD submissions enter `PENDING_VP_APPROVAL` state. Formal approval from **Vice President – Administration** is enforced via role guard before the evaluation is finalized (`MOD3-GD-APP-01`).
- **Collation & Annual Review Engine:**
  - Monthly reports auto-compiled from approved evaluations.
  - **Annual Report Trigger:** Worker detects completion of 1 year from Date of Joining (`DOJ`). Aggregates 12 monthly reports and computes parameter-weighted average scores (`MOD3-GD-ANN-01`).
  - **Probation Check:** Workflow queries `EmployeeCoreModule`; execution halts if probation is not mandatorily marked as completed.
  - **Compensation Slabs:** Management reviews the Annual Report and applies pre-configured compensation revision slabs. Outcomes archive into the Digital Employee File.

---

### 9.2 Sub-System 2: Performance Management (KRA/KPI Appraisal Cycle)
- **Lifecycle Engine:** Managed by `PerformanceManagementModule.KraKpiService`. Executes the 3-stage sequential flow:
  1. *Stage 1 (Onboarding Goal Setting):* Event hook on new employee creation in `EmployeeCoreModule`. Generates KRA/KPI setup task for employee and Reporting Authority. Strict **30-day countdown timer** from DOJ. Enforces formal verification and locking by HR and Management (`MOD3-KRA-SET-01`).
  2. *Stage 2 (Quarterly Review Cycle Q1–Q4):*
     - Scheduled trigger at **90 days from DOJ** intimates employee for Q1 review.
     - **20-Day Reminder Worker:** Dispatches alert if submission remains pending at `90 + 20` days (110 days from DOJ).
     - Employee submission window: within 15 days of 90-day mark (with document upload to Object Storage).
     - Supervisor verification window: 7-day SLA to verify and route to HR.
     - HR records observations; Management records executive comments.
     - Cycle repeats identically across Q2, Q3, and Q4 (`MOD3-KRA-QTR-01`).
  3. *Stage 3 (Annual Appraisal & Direct Handshake):*
     - Upon completion of Q4, system triggers formal appraisal request to Management.
     - Management logs final recommendation (increment, designation change, level promotion).
     - **Direct Handshake:** System executes an in-process transactional call to `ChangeManagementModule`, creating a formal Module I Change Request automatically without manual data re-entry (`MOD3-KRA-INT-01`).
- **TAT Analytics:** Background worker calculates turnaround times against the 30-day goal-setting SLA, 90-day review SLA, and 7-day supervisor verification SLA, rendering real-time performance analytics for HR.

---

### 9.3 Sub-System 3: Performance Management (Faculty – ECM Route)
- **Eligibility Scanner:** Managed by `PerformanceManagementModule.FacultyEcmService`.
  - Runs on the **10th of every month**. Queries PostgreSQL for Faculty matching:
    - `probation_completed = TRUE`
    - `(current_date - last_appraisal_date) >= 12 months`
  - Generates the eligible Faculty list and routes it from HR to the **Office of the Registrar** with automated escalation if delayed (`MOD3-FAC-ELG-01`).
- **Self-Appraisal & Verification Workflow:**
  - Auto-issues Self-Appraisal Form upon Registrar confirmation.
  - Faculty must submit form with evidence within **7 working days** (countdown tracked with daily reminders).
  - Parallel routing to verification units: **School Dean**, **R&D Cell**, **Placement Cell**, and **HR Department**.
  - **Discrepancy Loop:** Verifiers can flag discrepancies, returning the dossier to the Faculty member with tracked resubmission deadlines (`MOD3-FAC-VER-01`).
- **ECM Scheduling & Digital Score Sheet:**
  - Registrar schedules the monthly Evaluation Committee Meeting (ECM) for verified candidates.
  - Committee members enter individual scores into digital ECM Score Sheets during the meeting.
- **TNU Protocol Matrix & Compensation Engine:**
  - System compiles the **Evaluation Matrix** by synthesizing ECM scores, past increment history, and statutory TNU Protocol parameters.
  - Matrix routed through HR Representative to Management for final compensation decisions (`MOD3-FAC-ECM-01`).
  - **Execution & Auto-Letter:** System schedules approved revisions in the next applicable salary cycle, auto-generates the formal increment letter, routes it to HR/Payroll, and permanently archives all artifacts in the Faculty member's Digital Personal File (`MOD3-FAC-SAL-01`).

---

# 10. Core Shared Services

Core shared services provide reusable, cross-cutting infrastructure across all domain modules within the Modular Monolith:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                   CORE SHARED SERVICES                                           │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 1. Authentication (IAM)       │ 2. Role-Based Access Control   │ 3. Workflow Engine              │
│ • Secure JWT & session tokens │ • Fine-grained permissions     │ • Finite state machine executor │
│ • Password security & lockout │ • Role hierarchy & resource    │ • Transition guards & approval  │
│ • External expert magic links │   scoping (Dean/HOD/Mgmt)      │   history tracking              │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 4. SLA & Timeline Engine      │ 5. Asynchronous Scheduler      │ 6. Notification Service         │
│ • Target date calculations    │ • BullMQ job queues            │ • Multi-channel templated alert │
│ • Warning alerts & reminders  │ • Cron triggers (7th/10th)     │   dispatch (Email, In-App)      │
│ • Hard cutoffs & auto-locks   │ • Effective-date job executor  │ • Delivery tracking & retries   │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 7. Document Management        │ 8. Audit & Versioning Service  │ 9. Reporting Engine             │
│ • Object storage abstraction  │ • Append-only audit logging    │ • Dynamic aggregation queries   │
│ • Antivirus & MIME validation │ • Full before/after entity     │ • Real-time funnel metrics      │
│ • Secure presigned URL access │   state diffs & version trees  │ • Streaming tabular data export │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 10. PDF Generation Service    │ 11. ERP Integration Layer      │ 12. Real-Time Gateway (Socket.IO│
│ • Headless document renderer  │ • Transactional outbox engine  │ • Server-to-client event push   │
│ • Dynamic template population │ • Idempotent sync dispatcher   │ • Redis Pub/Sub adapter         │
│ • Tamper-evident letter print │ • Retry & reconciliation logs  │ • Invalidation & badge alerts   │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

### Architectural Responsibilities

1. **Authentication (IAM):** Manages user credentials, password hashing (Argon2/Bcrypt), session management, JWT token issuance with short expiry, and secure time-limited token links for external statutory SCM experts.
2. **Role-Based Access Control (RBAC):** Enforces fine-grained permissions across API routes and service methods. Supports hierarchical roles (e.g., Management, Vice President, Registrar, Dean, HOD, Faculty, Staff, Recruiter) and resource-level scoping (e.g., a Dean can only access records within their School).
3. **Workflow Engine:** Generic finite state machine managing entity lifecycle states (`DRAFT`, `SUBMITTED`, `UNDER_REVIEW`, `APPROVED`, `REJECTED`, `DISCREPANCY_RETURNED`, `LOCKED`). Evaluates role guards, validates prerequisite fields, and captures approval signatures.
4. **SLA & Timeline Engine:** Calculates business deadlines (e.g., 4 months prior to semester, 15-day requisition window, 30-day goal-setting SLA, 7th/10th of the month lockout). Dispatches pre-deadline reminders and executes automated escalations.
5. **Scheduler:** Background worker engine running periodic crons and delayed jobs. Handles midnight effective-date commits, monthly Group-D auto-locks, KRA/KPI quarterly reminders, and faculty eligibility scans.
6. **Notification Service:** Asynchronous notification dispatcher utilizing queue-backed workers. Merges dynamic payload data into standardized templates and delivers transactional emails and in-app dashboard alerts.
7. **Document Storage:** Storage abstraction interface (`FileStorageService`) decoupling domain logic from physical storage. Enforces MIME-type validation, size limits, SHA-256 integrity checksums, and time-limited presigned URL access.
8. **Audit Service:** Centralized interceptor capturing all database mutations. Writes immutable records to `audit_logs` containing `actor_id`, `actor_role`, `timestamp`, `ip_address`, `action_type`, `entity_name`, `entity_id`, and JSON state diffs.
9. **Reporting Engine:** High-performance reporting service executing optimized SQL aggregation queries and database views. Generates real-time dashboard statistics and streams tabular reports (XLSX, CSV).
10. **PDF / Document Generation Service:** Server-side templating engine rendering official university documents (LOIs, Appointment Letters, ECM Outcome Notices, Group-D Monthly Reports) into immutable, digitally verifiable PDFs.
11. **ERP Integration Layer:** Manages synchronization with the institutional ERP. Implements a reliable Transactional Outbox pattern to guarantee eventual consistency and auditability without blocking web requests.
12. **Real-Time Communication Gateway (Socket.IO):** Bi-directional WebSocket gateway delivering live event notifications, approval queue badge counters, org-chart cache invalidation triggers, and SLA lockout warnings to connected Next.js clients. Uses Redis Pub/Sub for horizontal scaling; preserves PostgreSQL as sole system of record.

---

# 11. Data Architecture Principles

Detailed physical entity-relationship diagrams (ERDs) and table definitions are explicitly deferred to the upcoming Data Architecture phase. However, the system's data layer must strictly adhere to the following architecture principles:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 DATA ARCHITECTURE PRINCIPLES                                     │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 1. PostgreSQL as Single SoR   │ 2. Strict Referential Integrity│ 3. Temporal Effective-Date Model│
│ • ACID transactional baseline │ • Foreign keys across domains  │ • Valid-from & valid-to ranges  │
│ • JSONB for configurable forms│ • Normalized 3NF master data   │ • Future-dated change schedules │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 4. Immutable Audit Ledger     │ 5. Separation: Binary vs Meta  │ 6. Clear Domain Data Ownership  │
│ • Append-only audit tables    │ • Database stores metadata only│ • Each domain module owns its   │
│ • No destructive hard deletes │ • Binaries in Object Storage   │   schema; cross-domain via API  │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

1. **PostgreSQL as System of Record (SoR):** PostgreSQL is the definitive, authoritative data store for all university employee, recruitment, and performance master records.
2. **Strict Referential Integrity:** Foreign key constraints are enforced across all core relational entities (e.g., an employee must belong to a valid Department; an evaluation must link to a valid Employee). Master reference tables maintain normalized third-normal-form (3NF) structures.
3. **Temporal & Effective-Date Modeling:** Master records subject to service condition changes maintain temporal attributes (`effective_date`, `valid_from`, `valid_to`, `is_active`). Historical records are never overwritten; state changes create new versioned records or ledger entries.
4. **Immutable Audit Ledger:** All state-changing events write to dedicated append-only audit tables. Hard database deletions are prohibited across business entities; records utilize soft-deletion flags (`deleted_at`) with complete audit trails.
5. **Separation of Binary Files and Metadata:** Binary files (PDF resumes, research attachments, generated letters) are **never** stored as database BLOBs. Binaries reside in Object Storage; PostgreSQL stores only file metadata (storage key, bucket, file name, MIME type, file size, SHA-256 hash, upload timestamp, and owning entity ID).
6. **Configurable Dynamic Schemas via JSONB:** While master structures remain strictly relational, dynamic forms with versioned parameters (such as Group-D role-specific KPIs, RCS questionnaires, and TNU Protocol matrices) utilize validated PostgreSQL `JSONB` columns with JSON Schema validation guards.
7. **Domain Data Ownership:** Each backend module maintains logical ownership over its database tables (e.g., `EmployeeCoreModule` owns `employees`; `RecruitmentModule` owns `manpower_requisitions`). Modules may not execute raw SQL writes into tables owned by other domains.

---

# 12. Integration Architecture

The following matrix documents the conceptual integration boundaries, distinguishing confirmed requirements, proposed technical mechanisms, and items requiring university confirmation (TBD):

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               INTEGRATION ARCHITECTURE TOPOLOGY                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
                                                 │
          ┌──────────────────────────────────────┼──────────────────────────────────────┐
          │                                      │                                      │
          ▼                                      ▼                                      ▼
┌───────────────────┐                  ┌───────────────────┐                  ┌───────────────────┐
│ MODULE II ➔ MOD I │                  │ MODULE I ➔ MOD III│                  │ MODULE III ➔ MOD I│
│ Onboarding Event: │                  │ Master Data Sync: │                  │ Appraisal Output: │
│ LOI Accepted ➔    │                  │ Employee DOJ,     │                  │ Increment, Level, │
│ Create Master DB  │                  │ Probation Status, │                  │ Promotion ➔ Create│
│ Record & Org Node │                  │ Reporting Lines   │                  │ Change Request    │
└─────────┬─────────┘                  └─────────┬─────────┘                  └─────────┬─────────┘
          │                                      │                                      │
          └──────────────────────────────────────┼──────────────────────────────────────┘
                                                 │
                                                 ▼
                               ┌───────────────────────────────────┐
                               │       MODULE I ➔ ERP ENGINE       │
                               │   Outbox Pattern ➔ Reliable Sync  │
                               │   (REST / Staging DB / SFTP TBD)  │
                               └───────────────────────────────────┘
```

| Integration Boundary | Business Event / Trigger | Data Transferred | Architectural Classification | Technical Mechanism |
|---|---|---|---|---|
| **Module II → Module I** | Candidate accepts LOI; completes pre-onboarding verification. | Candidate master data, role, department, salary, DOJ, level. | **Confirmed Requirement** | Internal domain service call. Creates master employee record, assigns Org Chart node, and marks open position as filled. |
| **Module I → Module II** | Resignation accepted by School Dean. | Resigning employee ID, position, school, acceptance timestamp. | **Confirmed Requirement** | In-process domain event (`EmployeeResignedEvent`). Starts replacement countdown clock and alerts Head HR. |
| **Module I → Module III** | Scheduled appraisal triggers (Monthly Group-D, Quarterly KRA, Monthly ECM). | Employee ID, DOJ, probation status, department, supervisor, historical salary. | **Confirmed Requirement** | In-process query service. Provides authoritative master data for eligibility identification and form routing. |
| **Module III → Module I** | Annual appraisal finalized (KRA/KPI Stage 3, Group-D review, Faculty ECM). | Approved increment, new designation, updated grade/level, effective date. | **Confirmed Requirement** | In-process transactional API call. Automatically initializes formal Change Request in Module I without manual re-entry. |
| **Module I → Institutional ERP** | Approved service change or new employee record committed. | Employee master delta, salary revision, designation, effective date. | **Confirmed Requirement** *(Interface Details TBD)* | Transactional Outbox Pattern. Events written to `erp_outbox` table, consumed by background worker for reliable external delivery. |
| **Application → Notification Gateway** | SLA warning, reminder, form assignment, approval alert. | Recipient email/ID, template ID, dynamic variables, priority. | **Confirmed Requirement** *(Provider TBD)* | Asynchronous Redis queue (BullMQ). Notification worker dispatches payloads via SMTP/API gateway with retry logic. |
| **Application → Object Storage** | CV upload, appraisal evidence upload, letter generation. | Binary byte stream, metadata, SHA-256 hash. | **Confirmed Requirement** *(Target TBD)* | `DocumentService` utilizing S3-compatible client. Stores binary, returns object key; client reads via presigned URL. |

---

# 13. Security Architecture Baseline

The security architecture implements defense-in-depth principles across authentication, authorization, data protection, and auditability:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                SECURITY ARCHITECTURE BASELINE                                    │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 1. Identity & Authentication  │ 2. Role-Based Access Control   │ 3. External SCM Expert Isolation│
│ • Secure session / JWT tokens │ • Hierarchical RBAC model      │ • Single-use, time-limited magic│
│ • Argon2 password hashing     │ • Row-level departmental and   │   tokens strictly scoped to     │
│ • Institutional SSO (TBD)     │   school data scoping guards   │   assigned candidates only      │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 4. Data Protection & Cryptography│ 5. Secure Document Access   │ 6. Immutable Security Auditing  │
│ • TLS 1.3 encryption in transit│ • Object storage private by def│ • Every login, permission check,│
│ • AES-256 encryption at rest  │ • Time-limited presigned URLs  │   and data modification logged  │
│ • Sensitive field masking     │ • Strict authorization before  │ • Tamper-evident, append-only   │
│   (Salaries, PII, PAN/Govt ID)│   generating presigned links   │   audit tables in PostgreSQL    │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

### 13.1 Identity & Authentication
- **User Authentication:** Enforces secure credential verification using industry-standard hashing (Argon2id or Bcrypt with cost factor >= 12).
- **Session Tokens:** Stateless JSON Web Tokens (JWT) for API authorization with short lifespans (e.g., 15 minutes), paired with cryptographically secure, rotating refresh tokens stored in Redis with revocation capabilities.
- **Institutional Single Sign-On (SSO):** The architecture is designed to integrate with institutional Identity Providers (Google Workspace, Microsoft Entra ID / 365, or LDAP/SAML). The specific SSO provider is classified as **TBD** pending University IT confirmation.

### 13.2 Authorization & Role-Based Access Control (RBAC)
- **Granular Role Hierarchy:** System enforces distinct permissions for:
  - *Institutional Executives:* Hon'ble Pro-Chancellor, Senior Management, Vice President – Administration, Registrar.
  - *Academic Leadership:* Associate Dean (Academics), Deans of Schools.
  - *Departmental Leadership:* Heads of Department (HODs), Reporting Authorities.
  - *Administrative & HR Staff:* Head of HR, HR Representatives, Recruiters, Payroll Team, System/IT Admin.
  - *Committee Members:* Statutory Selection Committee (SCM) members, Evaluation Committee (ECM) members.
  - *Employees:* Teaching Faculty, Technical Assistants, Staff, Group-D Staff.
- **Row-Level Resource Scoping:** RBAC guards enforce contextual data boundaries:
  - HODs can only access evaluations and requisitions pertaining to their department.
  - Deans can only view academic workloads and faculty records within their School.
  - An employee can only view their own appraisal forms and digital personal file.

### 13.3 External Statutory Expert Isolation
- Statutory Selection Committee Meetings (SCM) require participation from External Subject Experts who do not possess university employee credentials.
- **Secure Isolation Architecture:** External experts are granted secure, time-limited, cryptographically signed magic access tokens delivered via verified email.
- **Scoping Restriction:** The token grants read-only access strictly to the resumes and digital evaluation sheets of assigned candidates for that specific SCM session. External experts have zero access to university employee databases or internal systems.

### 13.4 Data Protection & Confidentiality
- **In Transit:** All HTTP communication is strictly enforced over **TLS 1.3** with HSTS enabled. Unencrypted HTTP requests are rejected at the reverse proxy.
- **At Rest:** Database storage volumes and object storage buckets enforce **AES-256** encryption at rest.
- **Field-Level Confidentiality:** Sensitive compensation figures, performance reprimands, and personally identifiable information (PII) are masked in standard UI views and restricted to authorized Senior Management and HR roles.

---

# 14. Scalability and Reliability

The system achieves enterprise-grade scalability and high availability within the Modular Monolith paradigm:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                  SCALABILITY & RELIABILITY MODEL                                 │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ 1. Stateless App Instances    │ 2. Database Performance        │ 3. Asynchronous Task Offloading │
│ • Next.js and NestJS run as   │ • PostgreSQL connection pool   │ • Heavy I/O tasks (PDF compile, │
│   stateless containers        │ • Composite indexes on search  │   email blasts, SLA evaluations)│
│ • Horizontal scaling behind   │   and temporal date columns    │   processed by BullMQ workers   │
│   reverse proxy load balancer │ • Read replicas for reporting  │ • Zero web thread blocking      │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ 4. Distributed Redis Caching  │ 5. Graceful Degradation        │ 6. Fault-Tolerant File Storage  │
│ • Caches Org Chart tree, role │ • Circuit breakers on external │ • Object storage multi-zone     │
│   permissions, form templates │   ERP and email endpoints      │   durability                    │
│ • Sub-millisecond read times  │ • Failed jobs retry with expo- │ • Checksum validation on every  │
│   for high-frequency routes   │   nential backoff into DLQ     │   upload and download           │
└───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┘
```

1. **Stateless Compute Scaling:** Both Next.js frontend and NestJS backend processes operate statelessly. Session states are maintained via JWTs and Redis. Application nodes can scale horizontally behind a load balancer without sticky-session constraints.
2. **PostgreSQL Optimization:**
   - Dedicated connection pooling (via PgBouncer or native NestJS connection pools).
   - Strategic composite indexing on high-frequency query paths (`employee_id`, `department_id`, `status`, `effective_date`, `created_at`).
   - Ability to attach read replicas for read-heavy reporting queries if analytics volume expands.
3. **Asynchronous Background Offloading:** Time-intensive operations—such as multi-channel CV ingestion, bulk PDF letter generation, SLA escalation checks, and ERP synchronization—are offloaded to Redis-backed background workers (BullMQ), preventing HTTP thread starvation.
4. **Caching Strategy:** Frequently read, rarely changed structures (such as the dynamic Organization Chart tree, departmental lists, and active form templates) are cached in Redis with strict event-driven invalidation hooks.
5. **Resilience & Fault Tolerance:** Background tasks implement exponential backoff retry policies with Dead Letter Queues (DLQ) for failed jobs (e.g., external email server timeouts or ERP downtime), ensuring zero transaction loss.

---

# 15. Deployment Architecture

The deployment architecture is vendor-neutral, containerized, and deployable on modern cloud infrastructure (AWS, Azure, GCP) or university on-premises virtualized infrastructure:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             CONCEPTUAL DEPLOYMENT TOPOLOGY                                       │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
                                                 │
                                                 ▼
                               ┌───────────────────────────────────┐
                               │   REVERSE PROXY / LOAD BALANCER   │
                               │   (TLS 1.3 Termination, WAF)      │
                               └─────────────────┬─────────────────┘
                                                 │
                        ┌────────────────────────┴────────────────────────┐
                        │                                                 │
                        ▼                                                 ▼
        ┌───────────────────────────────┐                 ┌───────────────────────────────┐
        │   NEXT.JS FRONTEND CLUSTER    │                 │    NESTJS BACKEND CLUSTER     │
        │   (Stateless Web Pods / VMs)  │                 │    (Modular Monolith API)     │
        │   • Server Components         │                 │    • REST API Endpoints       │
        │   • Static Asset Serving      │                 │    • Domain Modules           │
        └───────────────────────────────┘                 └───────────────┬───────────────┘
                                                                          │
                                         ┌────────────────────────────────┼───────────────────────────────┐
                                         │                                │                               │
                                         ▼                                ▼                               ▼
                         ┌───────────────────────────────┐ ┌──────────────────────────────┐ ┌──────────────────────────┐
                         │      MANAGED POSTGRESQL       │ │        MANAGED REDIS         │ │    BACKGROUND WORKERS    │
                         │   • Primary (Read/Write)      │ │   • In-Memory Cache Store    │ │   • SLA & Auto-Lock Pods │
                         │   • Read Replica (Reporting)  │ │   • BullMQ Queue Broker      │ │   • PDF Generation Pods  │
                         │   • Automated Daily Snapshots │ │   • Distributed Locks        │ │   • ERP Outbox Workers   │
                         └───────────────────────────────┘ └──────────────────────────────┘ └──────────────────────────┘
                                                                                                          │
                                         ┌────────────────────────────────────────────────────────────────┘
                                         ▼
                         ┌───────────────────────────────┐ ┌──────────────────────────────┐
                         │   S3-COMPATIBLE OBJECT STORE  │ │  OUTBOUND NOTIFICATION GW    │
                         │   • MinIO / AWS S3 / Azure    │ │  • SMTP Mail Server (TBD)    │
                         │   • Resumes, Evidence, Letters│ │  • SMS / WhatsApp GW (TBD)   │
                         └───────────────────────────────┘ └──────────────────────────────┘
```

### Component Isolation
- **Application Runtime:** Containerized via Docker / OCI containers. Next.js and NestJS run as isolated, horizontally scalable containers.
- **Database Services:** Managed PostgreSQL cluster configured with automated WAL archiving, daily point-in-time recovery (PITR), and private virtual network isolation.
- **Queue & Cache Services:** Redis cluster deployed in a private network segment.
- **File Storage:** S3-compatible object storage (MinIO for on-premise, AWS S3, or Azure Blob Storage).
- **Vendor Decisions:** Specific hosting provider (On-Premises private cloud vs Public Cloud) is classified as **TBD** pending University infrastructure sign-off.

---

# 16. Real-Time Communication Architecture

### 16.1 Purpose
This section establishes the official real-time communication strategy, architectural boundaries, and protocol selections for the University HR Change Management & Automation System. Its purpose is to define how live updates, workflow status changes, SLA warnings, and dynamic organizational reflections are delivered to connected web clients while strictly preserving the integrity, security, and modular monolith architecture of the platform.

### 16.2 Business Need
Throughout the university's operations across Modules I, II, and III, multiple workflows require timely operational visibility:
- **Dynamic Organization Structure (Module I):** When employee reassignments, promotions, or departmental transfers are approved, users viewing the interactive Organization Chart require prompt reflection of updated reporting hierarchies without manual page refreshes.
- **Pending Approvals & Live Counters (Modules I, II, & III):** HR Officers, Deans, and Executive Management oversee sequential approval queues. Live counter badges and status transitions prevent bottlenecks and eliminate stale pending lists.
- **Recruitment Trackers & Candidate Movement (Module II):** The 30-day Open Positions Tracker and "Yet to Join" pre-onboarding pipeline demand timely synchronization across Deans, HODs, HR recruiters, and IT administrators as candidates accept Letters of Intent (LOIs).
- **Time-Sensitive SLA Warnings & Auto-Lockouts (Module III):** Group-D monthly evaluations enforce a strict 10th-of-the-month lockout (23:59). Active evaluators require urgent visual warnings as deadlines approach. Similarly, quarterly KRA/KPI reviews and Faculty ECM schedules require timely in-app notifications.

### 16.3 Real-Time vs. REST Architectural Distinction
To avoid architectural ambiguity, a strict separation of concerns is maintained between the synchronous **REST API** and the **Real-Time Push Layer**:

```
                                  Next.js Frontend
                                         │
                    ┌────────────────────┴────────────────────┐
                    │                                         │
                 REST API                              Real-Time Layer
            (HTTP/HTTPS Requests)                   (Socket.IO WebSocket)
                    │                                         │
                    └────────────────────┬────────────────────┘
                                         │
                                  NestJS Modular
                                     Monolith
                                         │
                    ┌────────────────────┼────────────────────┐
                    │                    │                    │
               PostgreSQL              Redis               Workers
            System of Record        Cache/Queue           Scheduler
              (ACID State)          & Pub/Sub             (BullMQ)
```

1. **REST API (Primary Interaction Channel):**
   - Authoritative channel for all client-to-server commands, state mutations, and transactional workflows.
   - Handles all CRUD operations, form submissions, change request creations, multi-level approvals, and rejections.
   - Handles all master data queries, paginated lists, complex SQL reports, Excel/CSV exports, and file uploads/downloads.
   - Initial page hydration: Next.js pages always fetch their full initial state via authenticated REST endpoints.
2. **Real-Time Layer (Server-to-Client Notification Channel):**
   - Strictly a **server-to-client push channel** for lightweight invalidation signals, badge counter deltas, and in-app alerts.
   - Transmits ephemeral event notifications (e.g., `approval.pending`, `orgchart.updated`, `sla.warning`).
   - Does **NOT** execute business transactions or mutations.
   - Does **NOT** store business state.
   - Acts as an invalidation trigger prompting the client to re-fetch authoritative data via REST when needed.

### 16.4 Real-Time Use Case Catalogue
Every functional use case across the three modules requiring timely visibility is categorized below:

| Functional Domain | Operational Use Case | Primary Protocol | Real-Time Push Mechanism | Background Worker Role | Classification |
|---|---|:---:|:---:|:---:|:---:|
| **Module I** | Dynamic Org Chart realignments & reporting tree updates | `[REST]` (Fetch tree) | `[REAL-TIME PUSH]` (`orgchart.updated` triggers branch re-fetch) | Invalidate Redis cache | `[COMBINATION]` |
| **Module I** | Employee service-change approval status transitions | `[REST]` (Submit approval) | `[REAL-TIME PUSH]` (`approval.completed` updates status badge) | Write audit log; effective date check | `[COMBINATION]` |
| **Module I** | Midnight effective-date scheduled activation | `[REST]` (Fetch profile) | `[REAL-TIME PUSH]` (`employee.activated` pushes notification to HR) | `[BACKGROUND]` (BullMQ cron commits at 00:00) | `[COMBINATION]` |
| **Module I** | Pending approval counter indicators (HR & Management) | `[REST]` (Fetch approvals) | `[REAL-TIME PUSH]` (`approval.pending` increments counter badge) | None | `[COMBINATION]` |
| **Module I** | Digital employee file updates & document archiving | `[REST]` (Upload file) | `[REAL-TIME PUSH]` (`employee.file.updated` alerts viewing HR staff) | Checksum & virus validation | `[COMBINATION]` |
| **Module II** | Recruitment requisition (MRF) workflow transitions | `[REST]` (Submit MRF) | `[REAL-TIME PUSH]` (`recruitment.updated` updates pipeline view) | SLA timer initialization | `[COMBINATION]` |
| **Module II** | Open Positions Tracker (Attachment 3) live updates | `[REST]` (Fetch tracker) | `[REAL-TIME PUSH]` (`recruitment.tracker.updated` triggers row update) | Weekly digest collation | `[COMBINATION]` |
| **Module II** | Candidate pipeline status movement (Screening, RCS, Interview)| `[REST]` (Move stage) | `[REAL-TIME PUSH]` (`candidate.status.changed` updates stage view) | Automated screening engine | `[COMBINATION]` |
| **Module II** | Interview scheduling, panelist assignments, and SCM updates | `[REST]` (Save schedule) | `[REAL-TIME PUSH]` (`interview.scheduled` sends toast to panelists) | `[BACKGROUND]` (Email invitation dispatch) | `[COMBINATION]` |
| **Module II** | "Yet-to-Join" pre-onboarding tracking upon LOI acceptance | `[REST]` (Accept LOI) | `[REAL-TIME PUSH]` (`onboarding.accepted` alerts Deans, HODs, IT) | `[BACKGROUND]` (Creates Master DB record) | `[COMBINATION]` |
| **Module II** | Recruitment SLA warning alerts (15-day MRF, 7-day Pro-Chancellor) | `[REST]` (View dashboard) | `[REAL-TIME PUSH]` (`sla.warning` renders amber/red visual banner) | `[BACKGROUND]` (BullMQ evaluates breach threshold) | `[COMBINATION]` |
| **Module III** | Group-D monthly evaluation pending indicators for HODs | `[REST]` (Fetch forms) | `[REAL-TIME PUSH]` (`appraisal.groupd.pending` increments pending badge)| Monthly form generation on 1st | `[COMBINATION]` |
| **Module III** | Group-D 10th-of-month auto-lockout countdown & warning | `[REST]` (Submit form) | `[REAL-TIME PUSH]` (`sla.lockout.warning` pushes urgent modal alert) | `[BACKGROUND]` (Worker locks unsubmitted at 23:59)| `[COMBINATION]` |
| **Module III** | VP-Administration Group-D monthly sign-off reflection | `[REST]` (Submit sign-off) | `[REAL-TIME PUSH]` (`appraisal.groupd.approved` updates final status) | Aggregates annual score record | `[COMBINATION]` |
| **Module III** | KRA/KPI pending review counters (30-day setup, quarterly reviews) | `[REST]` (Fetch reviews) | `[REAL-TIME PUSH]` (`appraisal.kra.pending` increments pending badge) | SLA timer monitoring | `[COMBINATION]` |
| **Module III** | Quarterly KRA status transitions (Employee → Supervisor) | `[REST]` (Submit verify) | `[REAL-TIME PUSH]` (`appraisal.kra.updated` notifies employee) | Quarterly milestone scheduler | `[COMBINATION]` |
| **Module III** | Faculty ECM live score compilation & matrix display | `[REST]` (Submit score) | `[REAL-TIME PUSH]` (`appraisal.ecm.score.updated` updates live matrix) | Compiles TNU Protocol scores | `[COMBINATION]` |
| **Module III** | Faculty eligibility list notification (monthly 10th batch run) | `[REST]` (View list) | `[REAL-TIME PUSH]` (`appraisal.faculty.eligible` alerts HR & Registrar) | `[BACKGROUND]` (Monthly 10th batch scanner) | `[COMBINATION]` |
| **Shared** | Universal in-app notification delivery (bell alerts & toasts) | `[REST]` (Fetch history) | `[REAL-TIME PUSH]` (`notification.created` delivers toast & badge) | `[BACKGROUND]` (Persists notification record) | `[COMBINATION]` |
| **Shared** | Universal approval queue counter badges across all modules | `[REST]` (Fetch queue) | `[REAL-TIME PUSH]` (`queue.counter.updated` pushes delta counter) | None | `[COMBINATION]` |
| **Shared** | Universal SLA reminders, countdowns, and escalation warnings | `[REST]` (View alerts) | `[REAL-TIME PUSH]` (`sla.warning` displays banner alert to supervisor) | `[BACKGROUND]` (BullMQ timer evaluates escalation)| `[COMBINATION]` |
| **Shared** | Workflow state transitions across all entities | `[REST]` (Execute command) | `[REAL-TIME PUSH]` (`workflow.state.changed` broadcasts to room) | Audit log record written | `[COMBINATION]` |
| **Shared** | Audit trail & security event monitoring | `[REST]` (Query audit) | `[REAL-TIME PUSH]` (Reserved strictly for critical security alerts) | `[BACKGROUND]` (Interceptors record audit log) | `[REST]` / `[PUSH]` |

### 16.5 Technology Evaluation
The architectural working group evaluated **Native WebSocket (`ws`)** versus **Socket.IO** across twelve rigorous engineering criteria:
1. **Fit with Next.js Frontend:** Socket.IO provides a dedicated, lightweight client (`socket.io-client`) that cleanly integrates with React's component lifecycle via custom context providers and hooks. Native WebSocket requires bespoke connection lifecycle wrappers, reconnect loops, and message parsing logic.
2. **Fit with NestJS Backend:** NestJS provides first-class support for Socket.IO via `@nestjs/platform-socket.io` and `@nestjs/websockets`. Gateway decorators (`@WebSocketGateway()`, `@SubscribeMessage()`, `@WebSocketServer()`) map natively onto Socket.IO namespaces and rooms.
3. **Server-to-Client Event Delivery:** Socket.IO provides named event multiplexing out of the box, allowing distinct, strongly-typed event handlers. Native WebSocket requires custom application-level framing and JSON parsing wrappers.
4. **Reconnection Support:** Socket.IO features battle-tested automatic reconnection with configurable exponential backoff and randomized jitter, maintaining client state through transient network blips and workstation sleep cycles. Native WebSocket requires building and maintaining custom heartbeat and retry algorithms.
5. **Connection Lifecycle Management:** Socket.IO provides declarative lifecycle hooks (`connect`, `disconnect`, `connect_error`, `reconnect_attempt`) with built-in heartbeat ping/pong mechanisms to promptly detect half-open TCP sockets.
6. **Authentication & Authorization Integration:** Socket.IO supports token transmission during the connection handshake (`auth: { token }`). NestJS `WsGuard` inspects this token before accepting the connection, preventing unauthenticated clients from consuming server resources.
7. **Room and Channel Support:** Socket.IO natively implements server-side rooms (`socket.join('user:123')`, `socket.join('dept:cse')`, `socket.join('role:dean')`). This provides the exact departmental and role-based scoping required by University HR operations. Native WebSocket requires engineering a bespoke in-memory pub/sub routing registry.
8. **Horizontal Scaling:** Clustered NestJS instances require cross-node event propagation. Socket.IO provides the official, mature `@socket.io/redis-adapter`, which uses Redis Pub/Sub to distribute room broadcasts across application nodes without custom messaging infrastructure. Native WebSocket requires building a custom Redis Pub/Sub bridge.
9. **Redis Integration:** Reuses the existing, approved Redis infrastructure ([`TDR-06`](#tdr-06-redis-for-caching-and-queue-orchestration)) without introducing additional brokers.
10. **Operational Complexity:** Socket.IO runs embedded inside the NestJS process, sharing the HTTP server port (or utilizing a dedicated gateway port) and requiring zero standalone messaging daemons.
11. **Suitability for HR Workflows:** HR change management is a workflow-driven system characterized by low-to-medium event volumes (notifications, counter updates, invalidation signals), where developer ergonomics, room semantics, and reconnect reliability far outweigh micro-optimizations of raw frame overhead.
12. **Documentation & Maintainability:** Socket.IO is one of the most widely documented, stable, and community-tested real-time libraries in the Node.js/TypeScript ecosystem.

### 16.6 Socket.IO vs. Native WebSocket Comparison

| Evaluation Dimension | Native WebSocket (`ws` / `@nestjs/platform-ws`) | Socket.IO (`@nestjs/platform-socket.io`) | Architectural Impact for University HR System |
|---|---|---|---|
| **Protocol Overhead** | Extremely low (raw RFC 6455 frames). | Low (Engine.IO framing wrapper around WebSocket). | Negligible impact at enterprise HR workflow transaction volumes. |
| **Reconnection Handling** | Manual implementation required (timers, backoff, jitter). | **Built-in automatic reconnection** with backoff & jitter. | **Decisive Advantage:** Eliminates bespoke client retry state machines. |
| **Heartbeat / Health Check** | Custom ping/pong message framing required. | **Built-in periodic heartbeats** (ping/pong). | Promptly cleans up stale connections on campus WiFi roaming. |
| **Room / Channel Abstraction**| None (must implement custom connection-to-room registry). | **Native server-side rooms and namespaces**. | **Decisive Advantage:** Directly satisfies RBAC and departmental isolation. |
| **Multi-Node Redis Scaling** | Custom Redis Pub/Sub subscription & dispatch code needed. | **Turnkey `@socket.io/redis-adapter`**. | **Decisive Advantage:** Scales Modular Monolith across nodes effortlessly. |
| **Transport Fallback** | Fails if corporate/campus proxy blocks raw WebSocket. | **Automatic fallback to HTTP long-polling**. | Guarantees connectivity across restrictive institutional networks. |
| **NestJS Ecosystem Fit** | Supported via platform adapter; requires manual room code.| **First-class native driver** with full decorator support. | Cleanest alignment with NestJS Modular Monolith patterns. |

### 16.7 Approved Architecture Decision
Based on the comprehensive technology evaluation and operational suitability analysis:

> **Socket.IO is the APPROVED real-time communication technology (`[C] Approved Technical Decision`) for the application-level server-to-client real-time channel within the NestJS Modular Monolith and Next.js frontend.**

### 16.8 Security & Authorization
The real-time communication architecture enforces zero-trust security principles:
1. **Pre-Connection Handshake Authentication:** Clients must transmit a valid JWT / Bearer token within the `auth` payload during the initial Socket.IO connection handshake. A NestJS `WsGuard` validates the token before the connection is accepted. Unauthenticated connection attempts are immediately rejected.
2. **RBAC Room Authorization:** Upon successful authentication, the gateway inspects the user's role and departmental scope, enrolling the socket strictly into authorized rooms:
   - Personal Room: `user:<user_id>` (private alerts, personal change requests).
   - Departmental Room: `dept:<department_id>` (departmental change requests, HOD alerts).
   - Institutional Role Room: `role:<role_name>` (e.g., `role:hr_officer`, `role:dean`, `role:management`).
3. **Departmental & Data Privacy Isolation:** Sockets are forbidden from joining arbitrary rooms. Users never receive another department's confidential HR, compensation, or performance data simply because they maintain an active WebSocket connection.
4. **Least-Privilege Event Payloads:** Event payloads contain only lightweight entity identifiers, event types, and timestamps (e.g., `{ entityId: 'cr-104', type: 'SALARY_CHANGE', status: 'PENDING_APPROVAL' }`). Payloads **never contain sensitive HR data** (salary figures, PAN/Aadhaar numbers, performance ratings). Connected clients fetch authorized detailed data via authenticated REST endpoints.
5. **Connection Lifecycle Auditability:** Gateway connection events, authorization failures, and disconnections are logged for security compliance.
6. **Identity Provider Baseline:** Specific enterprise SSO provider integration remains classified as `[E] TBD` (`REQ-TBD-07a`). Handshake authentication relies on the abstracted `AuthModule` JWT contract.

### 16.9 Reliability, Consistency & State Synchronization
The real-time layer is governed by the following reliability invariants:
1. **PostgreSQL as Single Source of Truth:** Business operations always commit state to PostgreSQL first. Real-time events are post-commit notifications. A missed real-time event never causes data corruption or loss of business records.
2. **Transactional Event Flow:**
   ```
   Business Operation (REST Client Command)
           ↓
   Transactional State Update in PostgreSQL (ACID Commit)
           ↓
   Persist Authoritative State & Write Audit Log
           ↓
   Publish Real-Time Event via Socket.IO Gateway (and Redis Pub/Sub)
           ↓
   Connected Clients Invalidate Local View & Fetch Authoritative Data via REST
   ```
3. **Reconnection State Recovery:** If a client disconnects due to network interruptions, workstation sleep, or tab switching, it executes an automated recovery sequence upon reconnect:
   - Re-fetches current unread notification count via REST.
   - Re-fetches pending approval queue counts via REST.
   - Triggers SWR / React Query cache invalidation for the active view.
4. **At-Most-Once Push Delivery:** Socket.IO operates as a best-effort server push channel. Because full authoritative state is always recoverable through REST reads, complex distributed message brokers or client-side acknowledgment queues are not required for real-time push.

### 16.10 Scaling Architecture
The real-time layer scales seamlessly from development to multi-node production:
1. **Single Application Instance:** In development, testing, and single-container deployments, the Socket.IO gateway runs in-memory within the NestJS process, maintaining connected sockets and rooms in local memory.
2. **Horizontally Scaled Application Instances:** In production clusters where multiple NestJS Modular Monolith containers run behind a reverse proxy (e.g., Nginx, Traefik, AWS ALB):
   - **Sticky Sessions:** The reverse proxy is configured with cookie-based session affinity for the initial Socket.IO handshake to ensure connection upgrades terminate on the same node.
   - **Redis Pub/Sub Adapter:** The gateway utilizes `@socket.io/redis-adapter` connected to the managed Redis cluster. When an event is emitted to a room on Node A, the adapter publishes it to Redis Pub/Sub, delivering it to Node B and Node C for broadcast to their locally connected clients.
   - **Modular Monolith Preserved:** Scaling is achieved purely at the container level; the architecture remains strictly a Modular Monolith without microservices.

### 16.11 Relationship with Redis
- Redis acts exclusively as **supporting infrastructure**:
  1. In-memory cache store (hierarchical org tree, user role permissions).
  2. Persistent queue broker for BullMQ background workers.
  3. Pub/Sub distribution backbone for `@socket.io/redis-adapter`.
  4. Distributed coordination and atomic locks for scheduled cron jobs.
- **Redis is NOT the System of Record.** If Redis is restarted or evicted, no employee records, change histories, or approval audits are lost.

### 16.12 Relationship with Background Workers / Scheduler
- Asynchronous tasks and time-based business rules are executed exclusively by **Background Workers (BullMQ)**:
  - Midnight effective-date activation processing (`MOD1-DAT-01`).
  - Monthly Group-D auto-lockout enforcement at 23:59 on the 10th (`MOD3-GD-EVAL-01`).
  - Quarterly KRA/KPI reminder sequences (90/20/15/7 days) (`MOD3-KRA-QTR-01`).
  - Monthly 10th faculty appraisal eligibility batch scans (`MOD3-FAC-ELG-01`).
  - Asynchronous PDF document compilation and ERP synchronization outbox dispatch.
- **Worker-to-Gateway Handshake:** When a background worker completes a milestone or detects an approaching SLA breach, it dispatches an event via the shared Socket.IO Gateway (or Redis Pub/Sub), delivering an immediate live alert to online users while queuing external notifications (email/SMS).

### 16.13 Conceptual Event Model
The real-time layer utilizes a domain-prefixed naming strategy.

> [!IMPORTANT]
> The event names below represent a **conceptual architecture model (`[D] Proposed Detail`)**. They do NOT constitute final API contracts. Final event payload schemas and DTOs will be defined in upcoming specification phases.

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             CONCEPTUAL REAL-TIME EVENT TAXONOMY                                  │
├─────────────────────┬─────────────────────────────────┬──────────────────────────────────────────┤
│ Event Concept       │ Target Room / Audience          │ Conceptual Purpose                       │
├─────────────────────┼─────────────────────────────────┼──────────────────────────────────────────┤
│ `orgchart.updated`  │ `dept:<dept_id>`, `role:hr`     │ Invalidate client-side org tree branch   │
│ `employee.updated`  │ `user:<emp_id>`, `role:hr`      │ Notify employee profile modification     │
│ `approval.pending`  │ `role:approver`, `user:<id>`    │ Increment pending approval queue counter │
│ `approval.completed`│ `user:<initiator_id>`           │ Notify change request final approval     │
│ `recruitment.updated`│ `role:recruiter`, `dept:<id>`  │ Requisition stage update                 │
│ `candidate.status`  │ `role:recruiter`, `panel:<id>`  │ Candidate stage transition in pipeline   │
│ `appraisal.updated` │ `user:<emp_id>`, `user:<sup_id>`│ Performance appraisal workflow advance   │
│ `sla.warning`       │ `user:<assignee_id>`, `role:mgr`│ Pre-deadline breach warning banner       │
│ `notification.new`  │ `user:<user_id>`                │ Universal in-app notification bell toast │
└─────────────────────┴─────────────────────────────────┴──────────────────────────────────────────┘
```

### 16.14 Future Implementation Dependencies
Implementation of the real-time layer is deferred until subsequent documentation phases conclude:
1. **Phase 08 (Database Architecture):** Physical database entity modeling for in-app notifications and approval queues.
2. **Phase 09 (API Specification):** Formal REST endpoints and AsyncAPI event schema definitions.
3. **Phase 10 (UI/UX Design System):** Toast alert visual styling, live badge counters, and real-time org-chart visual transition animations.
4. **Phase 13 (Deployment Specification):** Reverse proxy WebSocket upgrade configuration and Redis cluster adapter parameters.

### 16.15 Open / TBD Decisions
The following real-time infrastructure parameters remain open:
1. **Enterprise SSO Identity Provider (`REQ-TBD-07a`):** Handshake authentication leverages the abstracted JWT contract pending institutional IdP confirmation.
2. **Outbound Notification Gateways (`REQ-TBD-10`):** External SMTP server credentials and SMS gateway providers for multi-channel notification dispatch.
3. **Campus Network Proxy Policies:** Physical confirmation of university network proxy handling of WebSocket protocols.

### 16.16 Traceability to Source Requirements
The real-time communication architecture is directly traced to authoritative source requirements:
- `MOD1-ORG-01` / `REQ-MOD1-04`: Dynamic Org Chart live reflection → `orgchart.updated` event.
- `MOD1-APP-01` / `REQ-MOD1-16`: 2-Level approval queue indicators → `approval.pending` event.
- `MOD1-DAT-01` / `REQ-MOD1-19`: Effective-date scheduled activation → `employee.activated` event.
- `MOD2-POS-01` / `REQ-MOD2-09`: Open Positions Tracker live visibility → `recruitment.tracker.updated` event.
- `MOD2-ONB-01` / `REQ-MOD2-20`: Yet-to-Join pre-onboarding alerts → `onboarding.accepted` event.
- `MOD3-GD-EVAL-01` / `REQ-MOD3-04`: Group-D 10th lockout SLA warnings → `sla.lockout.warning` event.
- `MOD3-KRA-QTR-01` / `REQ-MOD3-12`: KRA quarterly reminder notifications → `appraisal.kra.updated` event.
- `MOD3-FAC-ECM-01` / `REQ-MOD3-17`: Faculty ECM live score display → `appraisal.ecm.score.updated` event.
- `REQ-SLA-01` through `REQ-SLA-10`: Universal in-app alerts and escalations → `notification.new` & `sla.warning` events.

---

# 17. Technology Decision Records (TDRs)

The following Technical Decision Records document the specific engineering justifications for each approved technology:

### TDR-01: Modular Monolith vs. Microservices Architecture
- **Decision:** Adopt a **Modular Monolith** architecture for the backend.
- **Context:** The University HR platform encompasses three deeply interrelated modules (Change Management, Recruitment, Performance) that share a core employee database, an organizational chart, and transactional state handshakes.
- **Technical Justification:**
  1. *Transactional Atomicity:* Workflows such as feeding an annual appraisal outcome directly into Module I master records require atomic database transactions (`ACID`). A Modular Monolith allows these within a single database transaction, eliminating complex distributed two-phase commits.
  2. *Operational Simplicity:* Eliminates network latency, distributed service meshes, inter-service authentication overhead, and complex container orchestration.
  3. *Clean Domain Encapsulation:* NestJS enforces strict module boundaries. If a specific component (e.g., CV Ingestion) requires separate scaling in the future, it can be extracted cleanly without re-architecting the entire platform.

### TDR-02: Next.js with TypeScript for Frontend
- **Decision:** Select **Next.js** (TypeScript) as the presentation framework.
- **Context:** The system requires responsive, high-performance web dashboards for diverse users (executives, HR officers, Deans, faculty, external experts) with varying network conditions.
- **Technical Justification:**
  1. *Server-Side Rendering (SSR):* Renders complex dashboards, rosters, and evaluation matrices on the server, significantly reducing initial page load times on university workstations.
  2. *Type Safety:* TypeScript guarantees compile-time contract compliance with backend DTOs, reducing UI runtime bugs.
  3. *App Router Architecture:* Enables clean separation between static layout templates and interactive client components.

### TDR-03: Vanilla CSS + CSS Modules + CSS Variables vs. Utility Frameworks
- **Decision:** Use **Vanilla CSS**, **CSS Modules**, and **CSS Variables**; explicitly exclude Tailwind CSS and Shadcn UI.
- **Context:** The platform requires a bespoke, accessible, university-branded visual design with custom components (org chart trees, evaluation matrices, SLA steppers).
- **Technical Justification:**
  1. *Scoped Component Styling:* CSS Modules eliminate global namespace collisions and accidental style leakage across modules.
  2. *Semantic Token Architecture:* CSS Variables provide a centralized design token system (brand typography, official university colors, spacing units, elevation tokens) that natively supports theming and high-contrast modes without build-time utility overhead.
  3. *Clean Codebase:* Avoids cluttered HTML class strings, third-party framework lock-in, and breaking changes from external design dependencies.

### TDR-04: NestJS with TypeScript for Backend
- **Decision:** Adopt **NestJS** (TypeScript) for the backend service layer.
- **Context:** Enterprise academic operations require structured, maintainable backend code capable of enforcing strict business rules, complex validation, and modular encapsulation.
- **Technical Justification:**
  1. *Native Modular Architecture:* NestJS provides an enterprise architecture out of the box (Modules, Providers, Controllers, Dependency Injection) perfectly matching the Modular Monolith pattern.
  2. *Robust Ecosystem:* First-class support for validation pipes (class-validator), Guards for RBAC, Interceptors for audit logging, and background task queues (BullMQ).
  3. *OpenAPI Compliance:* Native Swagger integration ensures API documentation is automatically generated from code annotations.

### TDR-05: PostgreSQL as Primary Database
- **Decision:** Select **PostgreSQL** as the primary relational database.
- **Context:** The system acts as the institutional single source of truth, managing strict employee master data, multi-level approvals, temporal change logs, and dynamic form templates.
- **Technical Justification:**
  1. *ACID Compliance & Reliability:* Guarantees complete data integrity across all service modifications and financial compensation adjustments.
  2. *Hybrid Relational + JSONB:* Supports strict relational schemas for employee masters and foreign keys, while providing high-performance `JSONB` indexing for configurable evaluation form templates and dynamic questionnaires.
  3. *Advanced Temporal & Window Query Capabilities:* Native support for window functions, common table expressions (CTEs), and range types, ideal for organizational hierarchy queries and temporal effective-date tracking.

### TDR-06: Redis for Caching and Queue Orchestration
- **Decision:** Integrate **Redis** for in-memory caching and background job queuing.
- **Context:** The platform requires real-time SLA tracking, periodic reminder cron jobs, asynchronous PDF compilation, and fast reads for hierarchical org charts.
- **Technical Justification:**
  1. *Sub-Millisecond Read Latency:* Caches dynamic org chart hierarchies and user role permissions, dramatically offloading repetitive queries from PostgreSQL.
  2. *Robust Queue Backing (BullMQ):* Provides persistent, reliable queuing for background workers handling SLA countdowns, auto-locks, email dispatch, and ERP synchronization.
  3. *Distributed Synchronization:* Enables atomic distributed locks for scheduled tasks running across clustered application instances.

### TDR-07: Socket.IO for Server-to-Client Real-Time Communication
- **Decision:** Adopt **Socket.IO** (over WebSocket) as the approved real-time communication technology (`[C] Approved Technical Decision`) for server-to-client event delivery.
- **Context:** University HR operations require timely visibility into approval queues, SLA warnings, dynamic org-chart invalidations, and candidate pipeline changes without aggressive polling.
- **Technical Justification:**
  1. *NestJS Native Support:* Built-in `@nestjs/platform-socket.io` module provides clean decorator-driven gateways (`@WebSocketGateway()`, `@SubscribeMessage()`) fully integrated with dependency injection and RBAC execution contexts.
  2. *Reconnection Resilience:* Out-of-the-box automatic reconnection with backoff and jitter gracefully handles workstation sleep cycles, WiFi roaming, and temporary network drops.
  3. *Native Room Scoping:* Built-in server-side rooms (`user:`, `dept:`, `role:`) directly enforce institutional RBAC and departmental confidentiality without custom subscription registry code.
  4. *Turnkey Horizontal Scaling:* Official `@socket.io/redis-adapter` utilizes existing Redis infrastructure for multi-node event distribution without requiring external message brokers or microservices.
  5. *Transport Fallback:* Gracefully degrades to HTTP long-polling if restrictive campus network firewalls terminate raw WebSocket connections.

---

# 18. Requirement Traceability

The following matrix provides comprehensive, technology-level traceability mapping every authoritative requirement identifier from [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) to its corresponding architectural component and technology implementation:

| Requirement ID | Authoritative Requirement Summary | Architecture Component | Technology Stack Piece | Architectural & Implementation Notes |
|---|---|---|---|---|
| `MOD1-CDB-01` | Central Database of all Employees fully reflected in ERP. | `EmployeeCoreModule` + `ErpAdapterModule` | PostgreSQL + NestJS + BullMQ Worker | Master table in PostgreSQL; transactional outbox pattern to synchronize state to ERP asynchronously with delivery confirmation. |
| `MOD1-ORG-01` | Organization Chart connected to database, updating on changes. | `OrganizationModule` | NestJS + PostgreSQL + Redis + Next.js Tree Component | Adjacency list/closure table in Postgres; Redis tree cache invalidated upon employee supervisor/department changes. |
| `MOD1-CHG-01` | Standardized formats for 10 employee data change categories. | `ChangeManagementModule` | NestJS + PostgreSQL (`change_requests`) | Polymorphic change entity with type-specific validation pipes for Salary, Designation, Reportee, Supervisor, Level, School, etc. |
| `MOD1-APP-01` | 2-Level approval hierarchy (HR Level → Senior Management). | `WorkflowEngineModule` | NestJS + PostgreSQL State Machine | Two-tier sequential state transitions: `HR_REVIEW` → `SENIOR_MANAGEMENT_APPROVAL`. Role-based guards enforce approvals. |
| `MOD1-DAT-01` | Effective-date processing, timestamped audit trail, version history. | `ChangeManagementModule` + `AuditModule` | NestJS Interceptors + PostgreSQL + Scheduled Worker | Temporal `effective_date` scheduling worker. Append-only `audit_logs` table capturing user, timestamp, IP, and JSON diffs. |
| `MOD1-REP-01` | Real-time and configurable HR report generation. | `ReportingModule` | PostgreSQL Views + Next.js Server Components | Parameterized SQL read-views with dynamic filtering, real-time query execution, and streaming Excel/CSV export. |
| `MOD2-MP-FAC-01` | Academic manpower planning trigger >= 4 months before semester. | `RecruitmentModule` + `SlaTimelineModule` | NestJS Scheduler + BullMQ Worker | Scheduled cron monitors semester start dates; auto-dispatches workload assessment call from Assoc. Dean to Deans. |
| `MOD2-MP-FAC-02` | Deans submit requirements + teaching load (Attachment 1) within 15 days. | `RecruitmentModule` + `DocumentModule` | NestJS + PostgreSQL + Next.js Form | 15-day SLA countdown tracker with daily reminder jobs. Teaching load capture supporting document evidence attachment. |
| `MOD2-MP-NF-01` | Non-Faculty MRF restricted to 1 planned requisition per year. | `RecruitmentModule` | NestJS Business Logic Guard + PostgreSQL | Database constraint and domain validation rule preventing > 1 planned MRF submission per department per academic year. |
| `MOD2-RES-01` | Resignation acceptance by Dean starts replacement clock; alerts HR. | `RecruitmentModule` + `EmployeeCoreModule` | In-Process Event Bus (`EmployeeResignedEvent`) | Event hook starts replacement timer, triggers Head HR notification, and opens fast-track ad-hoc MRF pipeline. |
| `MOD2-POS-01` | Open Positions Tracker (Attachment 3) maintained within 30 days. | `RecruitmentModule` | PostgreSQL (`open_positions_tracker`) | Position registry automatically populated upon MRF approval; tracks lifecycle status from sourcing through onboarding. |
| `MOD2-SRC-01` | Multi-channel CV intake into central CV Database. | `CandidateCvModule` + `DocumentModule` | NestJS Intake Gateway + Object Storage | Ingests CVs from email, website, social links, referrals, and Internshala. Deduplicates candidate profiles by email/phone. |
| `MOD2-SRC-02` | Automated CV segregation, classification, and UGC norms screening. | `CandidateCvModule` | NestJS Rules Engine Service | Evaluates structured candidate inputs against position educational qualifications, experience criteria, and statutory UGC rules. |
| `MOD2-RCS-01` | Recruiter Calling Sheet (RCS) captured and routed to HOD-HR & Management. | `CandidateCvModule` + `WorkflowEngineModule` | Next.js RCS Form + NestJS Service | Standardized screening questionnaire; captures recruiter ratings; routes dossier to HOD-HR and Management for pre-interview sign-off. |
| `MOD2-SEL-FAC-01`| Statutory SCM selection with external expert, online scoring, matrix to Mgmt. | `RecruitmentModule` + `IamModule` | Next.js SCM Portal + Tokenized Auth | Digital invitations with time-limited tokens for external experts. Online scoring sheet; auto-compiles Evaluation Matrix. |
| `MOD2-SEL-NF-01` | Non-Academic 3-round interview (Technical, HR, Management). | `RecruitmentModule` | NestJS Multi-Round Workflow | Sequential 3-stage interview scoring: Round 1 (Technical) → Round 2 (HR) → Round 3 (Management). Evaluates knowledge, communication, attitude. |
| `MOD2-ONB-01` | Letter of Intent (LOI) auto-generation; "Yet to Join" pre-onboarding tracking. | `RecruitmentModule` + `PdfService` + `Notification` | NestJS PDF Templating + Object Storage | Auto-renders official LOI PDF upon Management approval. Acceptance transitions status to "Yet to Join"; notifies Deans, HODs, IT Admin. |
| `MOD3-GD-EVAL-01`| Group-D monthly form to HOD; due 7th; grace to 10th; auto-lockout if missed. | `PerformanceManagementModule.GroupD` | NestJS Cron + BullMQ Worker + Postgres | Monthly form dispatch to HODs. Automated reminders. Background worker auto-locks unsubmitted evaluations at 23:59 on the 10th. |
| `MOD3-GD-APP-01` | VP – Administration mandatory sign-off on monthly Group-D evaluation. | `WorkflowEngineModule` | NestJS RBAC Guard + State Machine | Enforces formal approval gate by Vice President – Administration before monthly evaluation is marked finalized. |
| `MOD3-GD-ANN-01` | Group-D annual report at 1 yr from DOJ; weighted scores; probation check. | `PerformanceManagementModule.GroupD` | NestJS Analytics Service + PostgreSQL | Worker detects 1-year DOJ anniversary; aggregates 12 monthly reports; computes weighted average; validates probation completion. |
| `MOD3-KRA-SET-01`| KRA/KPI setup within 30 days of DOJ; locked by HR & Management. | `PerformanceManagementModule.KraKpi` | NestJS Onboarding Event Hook + SLA Timer | Onboarding event starts 30-day goal-setting countdown. Form verified and locked by HR and Management. |
| `MOD3-KRA-QTR-01`| 90-day review intimation; 20-day reminder; 15-day submit; 7-day supervisor verify. | `PerformanceManagementModule.KraKpi` + `SlaTimeline` | NestJS Recurrence Engine + BullMQ | Multi-tier SLA scheduler managing 90-day triggers, 20-day reminders, 15-day employee submission, and 7-day supervisor verification. |
| `MOD3-KRA-INT-01`| Annual appraisal outcome feeds directly into Module I change request. | `ChangeManagementModule` + `KraKpiService` | In-Process Transactional Service Call | Direct integration handshake: approved appraisal initializes Module I Change Request (salary/level/designation) without re-entry. |
| `MOD3-FAC-ELG-01`| Auto-identify eligible Faculty (probation + >= 12 mo service); list by 10th. | `PerformanceManagementModule.FacultyEcm` | Scheduled PostgreSQL Query Worker | Monthly 10th batch scanner identifies eligible Faculty; routes list from HR to Registrar with escalation tracking. |
| `MOD3-FAC-VER-01`| Multi-department verification routing (Dean, R&D, Placement, HR) & discrepancy loop. | `PerformanceManagementModule.FacultyEcm` | NestJS Parallel Workflow Engine | Distributes self-appraisal dossier across 4 verification units. Implements return-to-faculty discrepancy resubmission loop. |
| `MOD3-FAC-ECM-01`| Monthly ECM scheduled by Registrar; digital score sheet; TNU Protocol matrix. | `PerformanceManagementModule.FacultyEcm` | Next.js ECM Portal + Scoring Engine | Registrar scheduling portal; digital score entry during meeting; compiles Evaluation Matrix with TNU weights and increment history. |
| `MOD3-FAC-SAL-01`| Implement compensation in next salary cycle; auto-generate letter to faculty/payroll. | `PerformanceManagementModule.FacultyEcm` + `PdfService` | Temporal Scheduler + PDF Generator | Tracks implementation in next salary cycle; auto-generates official outcome letter to Faculty and HR/Payroll; archives to Personal File. |
| `MOD1-ORG-RT-01` | Dynamic Org Chart real-time cache invalidation on reporting changes. | `OrganizationModule` + `RealTimeGateway` | Socket.IO + Redis Pub/Sub + Next.js Tree | `orgchart.updated` push event invalidates client-side tree cache, prompting targeted REST re-fetch. |
| `MOD1-APP-RT-01` | 2-Level approval queue live counter badges and status transitions. | `WorkflowEngineModule` + `RealTimeGateway` | Socket.IO + NestJS Gateway | `approval.pending` and `approval.completed` events update live badge counters without manual reload. |
| `MOD2-POS-RT-01` | Open Positions Tracker live status update across recruitment milestones. | `RecruitmentModule` + `RealTimeGateway` | Socket.IO + Next.js Tracker Component | `recruitment.tracker.updated` pushes row updates as vacancies transition across sourcing and interview stages. |
| `MOD2-ONB-RT-01` | "Yet-to-Join" pre-onboarding instant notification upon LOI acceptance. | `RecruitmentModule` + `RealTimeGateway` | Socket.IO + Next.js Toast Provider | `onboarding.accepted` broadcasts onboarding initiation to Deans, HODs, and IT Admin. |
| `MOD3-GD-SLA-01` | Group-D 10th-of-month auto-lockout countdown & urgent visual warnings. | `PerformanceManagementModule.GroupD` + `RealTimeGateway` | Socket.IO + BullMQ Worker | `sla.lockout.warning` pushes urgent modal alert before 23:59 lockout on the 10th. |
| `MOD3-FAC-RT-01` | Faculty ECM live score sheet compilation and matrix display to Management. | `PerformanceManagementModule.FacultyEcm` + `RealTimeGateway` | Socket.IO + Next.js ECM Portal | `appraisal.ecm.score.updated` synchronizes committee evaluation scores in real-time during meetings. |
| `SHR-SLA-RT-01`  | Universal in-app SLA alerts, countdown reminders, and escalation banners. | `SlaTimelineModule` + `RealTimeGateway` | Socket.IO + BullMQ Scheduler | `sla.warning` renders visual amber/red alert banners for pending tasks approaching deadlines. |

---

# 19. Architecture Risks and Open Decisions

To maintain strict architectural discipline, already-approved decisions (Next.js, TypeScript, Vanilla CSS, NestJS, PostgreSQL, Redis, Modular Monolith) are **finalized** and are **not** open decisions.

The following genuine unresolved items are formally cataloged as open decisions requiring University and IT stakeholder confirmation:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            GENUINE OPEN ARCHITECTURAL DECISIONS                                  │
├────┬─────────────────────────────┬──────────────────────────────────────────────────────────────┤
│ #  │ Domain / Category           │ Specific Open Decision & Architectural Impact                │
├────┼─────────────────────────────┼──────────────────────────────────────────────────────────────┤
│ 1  │ **ERP Integration**         │ Exact technical protocol for ERP reflection (REST API,       │
│    │ **Interface Protocol**      │ direct staging database tables, or batch SFTP flat-files).   │
├────┼─────────────────────────────┼──────────────────────────────────────────────────────────────┤
│ 2  │ **Institutional Identity**  │ Specific University SSO provider to integrate (Google        │
│    │ **Provider (IdP / SSO)**    │ Workspace, Microsoft Entra ID / Office 365, or LDAP/SAML).   │
├────┼─────────────────────────────┼──────────────────────────────────────────────────────────────┤
│ 3  │ **External Expert**         │ Exact delivery and secondary verification method for SCM     │
│    │ **Authentication Detail**   │ external experts (magic link only vs. magic link + SMS OTP). │
├────┼─────────────────────────────┼──────────────────────────────────────────────────────────────┤
│ 4  │ **Object Storage**          │ Deployment target for S3-compatible storage (On-premises     │
│    │ **Deployment Target**       │ MinIO cluster vs. Managed Cloud Object Store AWS S3 / Azure).│
├────┼─────────────────────────────┼──────────────────────────────────────────────────────────────┤
│ 5  │ **Transactional Messaging** │ Dedicated university SMTP mail gateway parameters and        │
│    │ **Gateways**                │ prospective SMS / WhatsApp gateway provider for urgent alerts.│
├────┼─────────────────────────────┼──────────────────────────────────────────────────────────────┤
│ 6  │ **TNU Protocol Exact**      │ Precise mathematical weightage formulas, scoring bands, and  │
│    │ **Mathematical Formulas**   │ normalization algorithms for the Faculty ECM matrix.         │
└────┴─────────────────────────────┴──────────────────────────────────────────────────────────────┘
```

### Risk Mitigation Strategies
1. **ERP Protocol Uncertainty:** Mitigated by implementing the **Transactional Outbox Pattern** in `ErpAdapterModule`. The core system commits state changes locally regardless of the external ERP protocol. When the ERP interface is finalized, only the outbox dispatcher adapter requires configuration.
2. **SSO Identity Provider Uncertainty:** Mitigated by utilizing an abstracted Passport.js / NestJS Auth strategy pattern. Local credential authentication serves as the development/fallback baseline while SSO strategy plugs in seamlessly upon IdP confirmation.
3. **Object Storage Target Uncertainty:** Mitigated by utilizing standard S3 SDK abstractions (`@aws-sdk/client-s3`). MinIO, AWS S3, Ceph, and Azure Blob (via S3 gateway) share identical API contracts.

---

# 20. Future Documentation Dependencies

This baseline document establishes the technical foundation for the project. In accordance with the documentation roadmap, the following technical specifications will be produced in subsequent documentation phases:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             FUTURE DOCUMENTATION ROADMAP                                         │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
                                                  │
                                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 1. FUNCTIONAL SPECIFICATION DOCUMENT (FSD / SRS)                                                 │
│    • Detailed screen-by-screen, field-by-field functional requirements and business rules        │
│    • Explicit validation rules, error handling specifications, and role-permission matrices      │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 2. DOMAIN DATA MODEL & ENTITY-RELATIONSHIP ARCHITECTURE (ERD)                                    │
│    • Full entity definitions, relational schemas, foreign key topologies, and constraints        │
│    • PostgreSQL table specifications, temporal columns, and JSONB schemas for dynamic forms      │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 3. WORKFLOW & STATE MACHINE SPECIFICATIONS                                                       │
│    • Formal state transition tables and UML state diagrams for all 8 major workflows             │
│    • Transition guards, approval signatures, and SLA timeout escalation logic                    │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 4. REST API INTERFACE SPECIFICATION (OPENAPI / SWAGGER)                                          │
│    • Comprehensive endpoint specifications, request/response DTO schemas, and HTTP status codes  │
│    • Authentication headers, pagination patterns, and error response standards                   │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 5. UI/UX DESIGN SYSTEM & WIREFRAME SPECIFICATION                                                 │
│    • Design tokens (CSS Variables: colors, typography, spacing, elevation)                       │
│    • CSS Modules component library specifications and responsive wireframe layouts               │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 6. SECURITY & ACCESS CONTROL SPECIFICATION                                                       │
│    • Fine-grained RBAC permission matrix (Role-to-Endpoint mapping)                              │
│    • Data protection policies, PII encryption rules, and external expert security specifications │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 7. REPORTING & ANALYTICS SPECIFICATION                                                           │
│    • Data dictionary for all statutory and operational reports across Modules I, II, and III     │
│    • SQL aggregation view designs and export format specifications                               │
└─────────────────────────────────┬────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 8. DEPLOYMENT & INFRASTRUCTURE SPECIFICATION                                                     │
│    • Docker container topology, reverse proxy configuration, environment variable dictionary    │
│    • Database backup/restore procedures, Redis clustering, and monitoring/logging setup          │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

*Note: Application coding, database migration scripting, and UI prototyping remain strictly prohibited until these documentation dependencies are completed and approved.*

---

# 21. Architecture Governance

To guarantee absolute fidelity to requirements and architectural integrity, the following governance rules are established:

### 20.1 Strict Prohibitions
1. **No Code Implementation:** No TypeScript, JavaScript, HTML, or SQL code may be created for application execution during documentation phases.
2. **No Database Migration Scripting:** Database schemas may not be instantiated or migrated in PostgreSQL during documentation phases.
3. **No Dependency Installation:** `package.json` modifications, `npm install`, or dependency additions are strictly prohibited until documentation phases conclude.
4. **No Unauthorized Framework Additions:** Under no circumstances may Tailwind CSS, Shadcn UI, or distributed microservices architectures be reintroduced into project documentation.
5. **No Requirement Alteration:** The original PDF requirement briefs and [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) remain the authoritative source of truth. No business rules, institutional roles, or workflows may be invented or modified.

### 20.2 Architectural Change Control
Any proposed modification to this Technical Architecture Baseline must undergo formal review:
- The proposer must document the technical justification, impact on requirement traceability, and operational trade-offs.
- The modification must receive explicit stakeholder approval before being incorporated into this document.

### 20.3 Consistency Attestation
This baseline has been subjected to a comprehensive internal consistency review against [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md). It is certified that:
- Every functional requirement across Modules I, II, and III maps directly to an approved architectural component.
- The three performance management tracks of Module III are maintained as completely distinct sub-systems without conflation.
- The dual-track (Academic vs. Non-Academic) recruitment pipelines of Module II are preserved with their specific statutory approval hierarchies and SLA countdowns.
- The database change methodology, effective dates, and audit trail mandates of Module I are fully supported by the temporal PostgreSQL and Redis background worker architecture.

---
*End of Document — Approved Technology Architecture Baseline Established.*
