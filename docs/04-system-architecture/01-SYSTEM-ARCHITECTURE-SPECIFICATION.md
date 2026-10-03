# System Architecture Specification
## University HR Change Management & Automation System

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-04-ARCH-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **System Phase** | Phase 1.5 & Phase 4 — Consolidated System Architecture Specification |
| **Document Status** | Approved Canonical Architecture Baseline |
| **Date** | October 2026 |
| **Architectural Pattern** | Modular Monolith (NestJS Backend + Next.js Frontend) |
| **Authoritative Sources** | `source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md` & `ADR-001` |

---

## 1. Architectural Principles & System Context

### 1.1 Architectural Style: The Modular Monolith
The University HR Change Management & Automation System is architected as an enterprise-grade **Modular Monolith**. 

Rather than deploying distributed microservices—which introduce network latency, distributed transaction complexity, and excessive DevOps overhead for an institutional HR platform—the system encapsulates distinct business modules within a single deployable application unit. Strong logical boundaries, encapsulated domain schemas, and in-memory event buses enforce decoupling between modules.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#1e293b', 'primaryTextColor': '#f8fafc', 'primaryBorderColor': '#38bdf8', 'lineColor': '#64748b'}}}%%
flowchart TD
    %% Styling Classes
    classDef clientNode fill:#1e1b4b,stroke:#818cf8,stroke-width:2px,color:#f8fafc;
    classDef feNode fill:#0c4a6e,stroke:#38bdf8,stroke-width:2px,color:#f8fafc;
    classDef beModNode fill:#1e293b,stroke:#94a3b8,stroke-width:2px,color:#f8fafc;
    classDef sharedNode fill:#312e81,stroke:#a855f7,stroke-width:2px,color:#f8fafc;
    classDef dbNode fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#f8fafc;
    classDef redisNode fill:#450a0a,stroke:#f87171,stroke-width:2px,color:#fecaca;
    classDef s3Node fill:#451a03,stroke:#fb923c,stroke-width:2px,color:#fff7ed;
    classDef erpNode fill:#1e293b,stroke:#e2e8f0,stroke-width:2px,stroke-dasharray: 5 5,color:#ffffff;

    subgraph CLIENTS ["CLIENT WORKSTATION TIER"]
        direction LR
        CLI_WEB["<b>Web Browser</b><br/><i>(Desktop / Tablet)</i>"]:::clientNode
        CLI_MOB["<b>Mobile / PWA Client</b><br/><i>(Responsive View)</i>"]:::clientNode
    end

    subgraph FRONTEND ["FRONTEND TIER: NEXT.JS APP ROUTER"]
        direction TB
        FE_APP["<b>Next.js App Router Application</b><br/>━━━━━━━━━━━━━━━━━━━━━━━━━━━━━<br/>• Server-Side Rendering (SSR) & React Server Components (RSC)<br/>• Bespoke Design System with Vanilla CSS & CSS Modules (<code>*.module.css</code>)<br/>• Real-Time Client Socket (<code>socket.io-client</code>) for Live Org Trees & Badges"]:::feNode
    end

    subgraph BACKEND ["BACKEND TIER: NESTJS MODULAR MONOLITH"]
        direction TB
        subgraph MODULES ["Domain Business Modules (Encapsulated)"]
            direction LR
            MOD1["<b>Module I: Core & Change</b><br/>• Central Master DB (ERP Synced)<br/>• Dynamic Org Chart Engine<br/>• 10 Change Formats (a)–(j)<br/>• 2-Level Sequential Approvals"]:::beModNode
            MOD2["<b>Module II: Talent Acquisition</b><br/>• Academic & Staff Manpower<br/>• UGC Sourcing & RCS Calling<br/>• Statutory SCM & 3-Round Panels<br/>• LOI & Notice Period Tracking"]:::beModNode
            MOD3["<b>Module III: Performance Engine</b><br/>• Group-D Monthly & Grace (7th/10th)<br/>• Staff KRA/KPI Cycles (Q1–Q4)<br/>• Faculty Statutory ECM Route<br/>• TNU Increment Formulation"]:::beModNode
        end

        subgraph PLATFORM ["Shared Enterprise Platform Services"]
            direction LR
            SVC_AUTH["RBAC & JWT Guards"]:::sharedNode
            SVC_AUDIT["Immutable Audit Interceptor"]:::sharedNode
            SVC_BUS["In-Memory Domain Event Bus<br/><i>(EventEmitter2)</i>"]:::sharedNode
            SVC_WS["Socket.IO Real-Time Gateway"]:::sharedNode
            SVC_OUTBOX["Transactional Outbox Worker"]:::sharedNode
        end

        MODULES ==> SVC_BUS
        SVC_BUS ==> SVC_WS
        SVC_BUS ==> SVC_OUTBOX
    end

    subgraph PERSISTENCE ["DATA & INFRASTRUCTURE TIER"]
        direction LR
        DB[("<b>PostgreSQL 16</b><br/>• 33 Conceptual Entities<br/>• 41 Relational Mappings<br/>• Transactional Outbox Ledger<br/>• Append-Only Audit Logs")]:::dbNode
        REDIS[("<b>Redis 7 + BullMQ</b><br/>• Dynamic Org Subtree Cache<br/>• SLA Countdown Queues<br/>• 10th Monthly Auto-Lock Cron<br/>• Outbox Dispatch Workers")]:::redisNode
        S3[("<b>S3 / MinIO Store</b><br/>• CVs & Candidate Dossiers<br/>• Statutory SCM PDFs & LOIs<br/>• Qualification Documents")]:::s3Node
    end

    ERP[("<b>University ERP System</b><br/><i>(External System of Record)</i>")]:::erpNode

    %% Inter-Tier Connections
    CLIENTS ==>|"HTTPS / REST API & WSS (Socket.IO)"| FRONTEND
    FRONTEND ==>|"Authenticated REST & WebSocket Handshake"| BACKEND
    BACKEND ==>|"ACID Relational Transactions"| DB
    BACKEND ==>|"Sub-second Cache & Message Queue"| REDIS
    BACKEND ==>|"Presigned Binary Document I/O"| S3
    SVC_OUTBOX -.->|"Guaranteed Eventual Consistency Sync"| ERP
```

---

## 2. Technology Stack Selection & Baseline Invariants

| Layer | Selected Technology | Architectural Rationale & Standards |
|---|---|---|
| **Frontend Framework** | **Next.js (App Router, React 19, TypeScript)** | High performance, server-side rendering for data-heavy administrative views, deep linking, and automated bundle splitting. |
| **Styling & CSS Architecture** | **Vanilla CSS + CSS Modules (`*.module.css`)** | Maximum styling control, zero runtime CSS bloat, scoped styles per component, bespoke University Design System using CSS Variables. Tailwind CSS is strictly excluded. |
| **Backend Framework** | **NestJS (TypeScript)** | Enterprise TypeScript architecture, dependency injection, modular domain isolation, built-in validation pipes, and robust ecosystem for WebSockets and queues. |
| **Primary Database** | **PostgreSQL** | ACID relational transactions, JSONB for flexible change schemas, strong referential integrity, and high-throughput query performance. |
| **In-Memory Cache & Queues** | **Redis + BullMQ** | Sub-second caching for dynamic organization trees; reliable persistent queues with retry mechanisms for notifications and cron tasks. |
| **Real-Time Communication** | **Socket.IO** | Bi-directional event push, WebSocket with automatic HTTP long-polling fallback, room-based channel routing, heartbeat reconnection (`ADR-001`). |
| **Binary Object Storage** | **S3-Compatible Object Store** | Complete separation of binary files (CVs, qualification documents, LOI PDFs) from relational database records. Relational tables store metadata and SHA-256 hashes only. |

---

## 3. Real-Time Communication Architecture (Socket.IO)

Per the approved **`ADR-001-REAL-TIME-COMMUNICATION.md`**, Socket.IO provides the real-time event pipeline for institutional operations:

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#1e293b', 'primaryTextColor': '#f8fafc', 'primaryBorderColor': '#38bdf8', 'lineColor': '#64748b'}}}%%
sequenceDiagram
    autonumber
    actor Client as Next.js Client
    participant GW as NestJS Socket.IO Gateway
    participant Bus as Domain Event Bus (EventEmitter2)
    participant Mod as Business Domain Module
    participant DB as PostgreSQL / Redis

    Note over Client, GW: 1. Authenticated WSS Handshake
    Client->>GW: Connect WSS (auth: { token: BearerJWT })
    GW->>GW: WsGuard verifies JWT & extracts Actor Roles
    GW->>Client: 200 OK Connected
    GW->>GW: Auto-enroll in Scoped Rooms: user:{id}, dept:{deptId}, role:{role}

    Note over Mod, DB: 2. Core Business Transaction Executes
    Mod->>DB: Commit Service Change / Lock Evaluation
    DB-->>Mod: Transaction Committed Successfully

    Note over Mod, Client: 3. Real-Time View Invalidation Dispatch
    Mod->>Bus: emit('service_change.activated', payload)
    Bus->>GW: handleDomainEvent(payload)
    GW->>Client: socket.to('dept:CS').emit('org-tree:invalidated', { nodeId })
    GW->>Client: socket.to('user:emp_101').emit('notification:pushed', { title: 'Promotion Effective' })
    
    Note over Client: Client refetches updated subtree via REST without full reload!
```

### 3.1 Room & Namespace Architecture
1. **User Personal Room (`user:{userId}`):** Personal notifications, SLA reminders, document verification return queries, and task assignments.
2. **Departmental Room (`dept:{deptId}`):** Department-wide announcements, vacancy updates, and recruitment milestones.
3. **Role-Based Room (`role:{roleCode}`):** High-priority alerts to Deans, HR Operations, or Senior Management.
4. **Global System Room (`system:broadcast`):** University-wide maintenance announcements and emergency broadcasts.

### 3.2 Key Real-Time Events
- `org-tree:invalidated`: Triggered upon effective-date activation of designation/supervisor/dept changes; instructs client tree canvas to invalidate local cache and re-fetch active subtree.
- `notification:pushed`: Pushes instant task assignments and SLA warning toasts without full page refreshes.
- `evaluation:locked`: Real-time notification dispatched at 23:59 on 10th of month to evaluating supervisors whose Group-D submissions have been locked.

---

## 4. Background Job Scheduling & Asynchronous Queues

All time-sensitive, schedule-driven, and compute-heavy operations are offloaded to **BullMQ** running on Redis:

| Queue Name | Job Responsibility | Frequency / Trigger | Failure / Retry Policy |
|---|---|---|---|
| `sla-countdown-queue` | Monitors deadlines for Deans (15d), Pro-Chancellor (7d), Faculty (7d), Staff (15d). | Recurring 15-minute cron | 3 retries, exponential backoff, alerts admin on dead letter. |
| `group-d-lockout-queue` | Executes auto-lockout for unsubmitted Group-D forms on 10th of month at 23:59 IST. | Exact monthly schedule (10th 23:59) | Critical job; executes with idempotent locking and emits HR non-compliance alert. |
| `effective-date-activation` | Scans for approved service changes where `effective_date <= CURRENT_DATE` and commits them. | Daily at 00:01 IST | Transactional commit; rolls back on failure and alerts HR. |
| `erp-sync-outbox-queue` | Polls transactional outbox and dispatches updates to University ERP platform. | Poller every 30 seconds | At-least-once delivery; exponential backoff up to 24 hours. |
| `notification-dispatch-queue` | Dispatches outbound SMTP emails and transactional SMS notifications. | Immediate event push | 5 retries, rate-limited to avoid gateway throttling. |

---

## 5. Security, Identity & Data Governance

### 5.1 Authentication & RBAC
- Stateless **JSON Web Tokens (JWT)** with short-lived access tokens (15 minutes) and rotating refresh tokens stored in HTTP-only, Secure cookies.
- Granular **Role-Based Access Control (RBAC)** enforced at the controller level via NestJS Guards (`@Roles('HR_ADMIN', 'DEAN', 'REGISTRAR')`).
- Strict segregation of duties: No user may approve their own requisition, evaluation, or change request (`BR-ENT-003`).

### 5.2 Immutable Audit Ledger
- All master mutations intercept through a database middleware capturing:
  - `actor_id`: Authenticated user performing action.
  - `ip_address`: Source IP address.
  - `table_name`: Target database table.
  - `action_type`: `INSERT`, `UPDATE`, `SOFT_DELETE`, `STATE_TRANSITION`.
  - `before_state`: Complete JSON snapshot prior to mutation.
  - `after_state`: Complete JSON snapshot following mutation.
  - `timestamp`: UTC microsecond timestamp.
- Audit table permissions are restricted to `INSERT` and `SELECT` only; `UPDATE` and `DELETE` SQL grants are revoked at the PostgreSQL engine level.

---

## 6. Integration Architecture: Transactional Outbox Pattern

To synchronize employee master data with the University ERP without distributed transaction failures, the system implements the **Transactional Outbox Pattern**:

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#1e293b', 'primaryTextColor': '#f8fafc', 'primaryBorderColor': '#38bdf8', 'lineColor': '#64748b'}}}%%
sequenceDiagram
    autonumber
    participant App as Change Engine
    participant DB as PostgreSQL Database
    participant Worker as BullMQ Outbox Worker
    participant ERP as University ERP Platform

    Note over App, DB: Phase 1: Atomic Local Transaction
    App->>DB: BEGIN TRANSACTION
    App->>DB: 1. UPDATE mod1_core.employees SET designation = 'Prof', salary = 180000
    App->>DB: 2. UPDATE mod1_core.org_nodes SET supervisor_id = 'dean_01'
    App->>DB: 3. INSERT INTO shared_platform.outbox_events (payload, status: 'PENDING')
    App->>DB: COMMIT TRANSACTION
    DB-->>App: Committed Atomically (Zero Distributed Inconsistency)

    Note over Worker, ERP: Phase 2: Asynchronous Guaranteed Outbox Dispatch
    Worker->>DB: SELECT * FROM outbox_events WHERE status = 'PENDING' ORDER BY created_at ASC
    DB-->>Worker: Return Pending Event Records
    Worker->>ERP: POST /api/v1/erp/employee-sync (Payload)
    alt ERP Transmission Success
        ERP-->>Worker: 200 OK { status: 'SYNCHRONIZED' }
        Worker->>DB: UPDATE outbox_events SET status = 'DELIVERED', updated_at = NOW()
    else ERP Unreachable or Network Timeout
        ERP--xWorker: 503 Service Unavailable / Timeout
        Worker->>DB: UPDATE outbox_events SET retry_count = retry_count + 1
        Note over Worker: Re-enqueue with Exponential Backoff (Up to 10 Attempts)
    end
```
