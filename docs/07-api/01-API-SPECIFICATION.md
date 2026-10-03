# REST API & Real-Time WebSocket Specification
## University HR Change Management & Automation System

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-07-API-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **System Phase** | Phase 5 — API Interface & Contract Specification |
| **Document Status** | Approved Canonical API Specification |
| **Date** | October 2026 |
| **Base URL** | `https://hrms.university.edu/api/v1` |
| **Protocol** | HTTPS (REST) & WSS (Socket.IO v4) |
| **Authoritative Sources** | `docs/03-functional-requirements/`, `docs/04-system-architecture/`, `docs/05-database/` |

---

## 1. Global API Standards & Conventions

### 1.1 Transport & Format Standards
- **Protocol:** HTTPS only with TLS 1.3.
- **Data Exchange Format:** JSON (`application/json; charset=utf-8`) for all endpoints except binary uploads (`multipart/form-data`).
- **Date/Time Standard:** ISO 8601 UTC format (`YYYY-MM-DDTHH:mm:ss.sssZ`).
- **Date-Only Standard:** `YYYY-MM-DD` (used for `effective_date`, `dob`, `joining_date`).
- **Idempotency:** State-modifying requests (`POST`, `PUT`, `PATCH`) support optional `X-Idempotency-Key: <UUID>` header.

### 1.2 Authentication & Authorization Header
All protected endpoints require an HTTP Bearer JWT token:
```http
Authorization: Bearer <JWT_ACCESS_TOKEN>
```

### 1.3 Standard Response Envelope
All API responses follow a unified envelope format:

#### Success Response Envelope (HTTP 200 / 201)
```json
{
  "success": true,
  "statusCode": 200,
  "message": "Resource retrieved successfully",
  "data": { ... },
  "meta": {
    "timestamp": "2026-10-03T16:45:00.000Z",
    "requestId": "req-9b1deb4d-3b7d-4bad-9bdd-2b0d7b3dcb6d",
    "pagination": {
      "currentPage": 1,
      "pageSize": 20,
      "totalRecords": 142,
      "totalPages": 8
    }
  }
}
```

#### Error Response Envelope (HTTP 4xx / 5xx)
```json
{
  "success": false,
  "statusCode": 400,
  "errorCode": "VALIDATION_FAILED",
  "message": "Input validation failed on one or more fields",
  "errors": [
    {
      "field": "effectiveDate",
      "issue": "Effective date cannot be prior to current active service period"
    }
  ],
  "meta": {
    "timestamp": "2026-10-03T16:45:01.000Z",
    "requestId": "req-9b1deb4d-3b7d-4bad-9bdd-2b0d7b3dcb6d"
  }
}
```

---

## 2. Authentication & Session Endpoints (`/api/v1/auth`)

| Method | Endpoint | Description | Auth Required | Allowed Roles |
|---|---|---|:---:|---|
| `POST` | `/api/v1/auth/login` | Authenticate user using employee code/email and password. Returns Access Token & sets HttpOnly Refresh Token cookie. | No | Public |
| `POST` | `/api/v1/auth/refresh` | Rotate and issue a new 15-minute Access Token using valid Refresh Token cookie. | No | Public (Cookie) |
| `POST` | `/api/v1/auth/logout` | Revoke active Refresh Token and clear session cookies. | Yes | All Roles |
| `GET` | `/api/v1/auth/me` | Retrieve authenticated user profile, active roles, and granular permissions. | Yes | All Roles |

---

## 3. Module I: HR Change Management & Core DB Endpoints

### 3.1 Employee Directory & Personal Dossiers
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `GET` | `/api/v1/employees` | Search and filter active/separated employee directory. Query params: `page`, `limit`, `search`, `departmentId`, `cadre`, `status`. | `HR_ADMIN`, `DEAN`, `HOD`, `REGISTRAR`, `PRO_CHANCELLOR` |
| `GET` | `/api/v1/employees/:id` | Retrieve comprehensive profile for target employee (service, academic, reporting lines). | `HR_ADMIN`, Supervisor, Self |
| `GET` | `/api/v1/employees/:id/dossier` | Retrieve chronological Digital Employee Dossier items with signed storage URLs. | `HR_ADMIN`, `REGISTRAR`, `PRO_CHANCELLOR` |
| `POST` | `/api/v1/employees/:id/resign` | School Dean records formal resignation acceptance, setting notice period and triggering `BP-XMOD-002`. | `DEAN`, `HR_ADMIN` |

### 3.2 Dynamic Organization Chart
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `GET` | `/api/v1/org-chart` | Retrieve dynamic organization hierarchy tree. Cached in Redis; served in sub-second response time (`REQ-MOD1-04`). | All Authenticated Users |
| `GET` | `/api/v1/org-chart/sub-tree/:nodeId` | Retrieve specific school or departmental subtree hierarchy. | All Authenticated Users |

### 3.3 Service Condition Change Requests (Formats a through j)
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `POST` | `/api/v1/change-requests` | Initiate new service change request under one of 10 formats (`SALARY`, `DESIGNATION`, `REPORTEE`, etc.) with `effective_date`. | `HR_ADMIN`, `HOD`, `DEAN` |
| `GET` | `/api/v1/change-requests` | List change requests with status filters (`PENDING_HR`, `PENDING_MGMT`, `APPROVED_SCHEDULED`). | `HR_ADMIN`, `PRO_CHANCELLOR` |
| `GET` | `/api/v1/change-requests/:id` | Retrieve single change request detail with before/after state diff and attachments. | `HR_ADMIN`, Approvers, Initiator |
| `POST` | `/api/v1/change-requests/:id/approve-hr` | Level-1 HR Operations recommendation and endorsement (`BP-M1-005`). | `HR_ADMIN` |
| `POST` | `/api/v1/change-requests/:id/approve-mgmt` | Level-2 Senior Management executive sanction (`BP-M1-005`). Strictly requires Level-1 HR sign-off (`BR-M1-004`). | `PRO_CHANCELLOR`, `REGISTRAR` |
| `POST` | `/api/v1/change-requests/:id/reject` | Reject change request with mandatory remarks and return to initiator. | `HR_ADMIN`, `PRO_CHANCELLOR` |

---

## 4. Module II: Recruitment & Talent Acquisition Endpoints

### 4.1 Manpower Planning & Sourcing
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `POST` | `/api/v1/requisitions/academic` | School Dean submits semester academic requirements and teaching loads (Attachment 1) within 15-day SLA (`REQ-MOD2-03`). | `DEAN` |
| `POST` | `/api/v1/requisitions/non-academic` | Department Head submits annual staff MRF; enforces 1-MRF annual quota (`BR-M2-009`). | `HOD` |
| `GET` | `/api/v1/requisitions` | List all manpower requisitions with track filters (`ACADEMIC`, `NON_ACADEMIC`, `URGENT_REPLACEMENT`). | `HR_ADMIN`, `PRO_CHANCELLOR` |
| `POST` | `/api/v1/requisitions/:id/sanction` | Pro-Chancellor executive review and approval (7-day turnaround SLA, `REQ-MOD2-05`). | `PRO_CHANCELLOR` |
| `GET` | `/api/v1/vacancies/tracker` | Retrieve Open Positions Tracker (Attachment 3 / Enclosure 4) with days-open metrics (`REQ-MOD2-10`). | `HR_ADMIN`, `PRO_CHANCELLOR` |
| `POST` | `/api/v1/candidates/cv-upload` | Ingest candidate application and CV; executes automated UGC statutory criteria screening (`REQ-MOD2-11`, `12`). | Public / Recruiter |
| `POST` | `/api/v1/screenings/rcs` | Log initial Recruiter Calling Sheet (RCS) telephonic evaluation and communication score (`REQ-MOD2-13`). | `HR_ADMIN`, Recruiter |

### 4.2 Interviews, Selection & Onboarding
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `POST` | `/api/v1/interviews/scm/score` | Selection Committee panel members (including External Subject Expert) submit digital scoring matrix (`REQ-MOD2-16`). | `SCM_MEMBER`, `EXTERNAL_EXPERT` |
| `POST` | `/api/v1/interviews/staff/score` | Submit Non-Academic 3-Round interview evaluation across Job Knowledge, Communication, Attitude (`REQ-MOD2-18`). | Interview Panel Members |
| `POST` | `/api/v1/offers/loi` | Auto-generate and issue official Letter of Intent (LOI) to selected candidate (`REQ-MOD2-19`). | `HR_ADMIN` |
| `POST` | `/api/v1/offers/loi/:id/accept` | Candidate electronically accepts LOI and uploads signed acceptance; transitions to "Yet to Join" (`REQ-MOD2-20`). | Candidate / Recruiter |
| `GET` | `/api/v1/onboarding/yet-to-join` | Retrieve "Yet to Join" dashboard tracking candidate notice periods and joining schedules (`REQ-REP-04`). | `HR_ADMIN` |
| `POST` | `/api/v1/onboarding/verify-day1` | Verify candidate Day-1 physical reporting and certificates; executes `BP-XMOD-001` to instantiate Central DB record. | `HR_ADMIN` |

---

## 5. Module III: Performance Management Endpoints

### 5.1 Subsystem 1: Group-D / Band-I Performance
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `GET` | `/api/v1/performance/group-d/monthly` | Retrieve active monthly evaluation forms for reporting Group-D staff (dispatched on 1st). | `HOD`, Supervisor |
| `POST` | `/api/v1/performance/group-d/monthly/:id/evaluate` | Supervisor submits monthly evaluation scores (due 7th; grace period to 10th; auto-locks at 23:59 on 10th, `BR-M3-003`). | `HOD`, Supervisor |
| `POST` | `/api/v1/performance/group-d/monthly/:id/approve-vp` | Exclusive approval sign-off by VP-Administration (`BR-M3-004`). | `VP_ADMIN` |
| `GET` | `/api/v1/performance/group-d/annual/:employeeId` | Retrieve 1-year anniversary weighted average scorecard and probation gate verification (`REQ-MOD3-08`, `09`). | `HR_ADMIN`, `VP_ADMIN` |

### 5.2 Subsystem 2: General Staff KRA/KPI
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `POST` | `/api/v1/performance/kra/goals` | Configure new joiner KRA/KPI goal sheet within 30 days of Date of Joining (`REQ-MOD3-10`). | Employee, Supervisor |
| `POST` | `/api/v1/performance/kra/goals/:id/lock` | Joint HR and Management sign-off freezing goal sheet targets for cycle (`REQ-MOD3-11`). | `HR_ADMIN`, `PRO_CHANCELLOR` |
| `POST` | `/api/v1/performance/kra/quarterly/:id/self-appraisal` | Employee submits quarterly self-review achievements against locked KPIs (`REQ-MOD3-12`). | Employee |
| `POST` | `/api/v1/performance/kra/quarterly/:id/supervisor-review` | Supervisor submits quarterly assessment and performance remarks within 7-day SLA. | Supervisor |

### 5.3 Subsystem 3: Faculty Annual Appraisal via ECM Route
| Method | Endpoint | Description | Allowed Roles |
|---|---|---|---|
| `GET` | `/api/v1/performance/faculty/eligibility` | Automated 10th-of-month scan listing faculty with probation completed and $\ge$ 12 months service (`REQ-MOD3-14`). | `REGISTRAR`, `HR_ADMIN` |
| `POST` | `/api/v1/performance/faculty/self-appraisal` | Eligible faculty submits comprehensive self-appraisal dossier (Enclosure 1) within 7 working days (`REQ-MOD3-15`). | `FACULTY` |
| `POST` | `/api/v1/performance/faculty/verification/:unit` | Parallel verification submission by Dean, Director R&D, Placement Cell, or HR (`REQ-MOD3-16`). | `DEAN`, `RD_DIRECTOR`, `PLACEMENT_HEAD`, `HR_ADMIN` |
| `POST` | `/api/v1/performance/faculty/ecm/score` | Monthly Evaluation Committee Meeting members enter digital scores (Enclosure 2) and compile TNU Matrix (`REQ-MOD3-17`, `18`). | `ECM_MEMBER` |
| `POST` | `/api/v1/performance/faculty/sanction` | Management sanctions increment; executes in next salary cycle with auto-generated revision letter (`REQ-MOD3-19`). | `PRO_CHANCELLOR` |

---

## 6. Real-Time WebSocket Events (Socket.IO v4)

Clients connect to `wss://hrms.university.edu/socket.io/` with JWT authentication in query/auth headers.

### 6.1 Server-to-Client Event Catalogue
| Event Name | Room Scope | Payload Schema | Description |
|---|---|---|---|
| `org-tree:invalidated` | `system:broadcast` | `{ "timestamp": "...", "reason": "DESIGNATION_CHANGED", "affectedNodeId": "..." }` | Instructs client tree canvas to invalidate local cache and re-fetch subtree. |
| `notification:pushed` | `user:{userId}` | `{ "id": "...", "title": "...", "body": "...", "link": "...", "priority": "HIGH" }` | Pushes instant user notification toast and increments unread badge. |
| `evaluation:locked` | `role:HOD` | `{ "month": "2026-10-01", "lockedCount": 12, "cutoffTime": "..." }` | Fired at 23:59 on 10th notifying HODs of automated lockout. |
| `sla:warning` | `user:{userId}` | `{ "taskId": "...", "dueInHours": 24, "type": "DEAN_REQUISITION_DUE" }` | Alerts actor of impending SLA expiration. |
