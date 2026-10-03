# Security & Role-Based Access Control (RBAC) Specification
## University HR Change Management & Automation System

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-08-SEC-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **System Phase** | Phase 6 — Security, Identity & Access Governance Specification |
| **Document Status** | Approved Canonical Security Baseline |
| **Date** | October 2026 |
| **Authentication Standard** | Stateless JWT (RS256) with Refresh Token Rotation |
| **Authorization Standard** | Granular Multi-Role RBAC with Row-Level Scoping |
| **Authoritative Sources** | `docs/01-requirements/`, `docs/02-business-process/`, `docs/04-system-architecture/` |

---

## 1. Security Architecture & Identity Governance

### 1.1 Authentication Architecture
The system enforces enterprise-grade identity controls:
- **Primary Credentials:** Institutional Email or Employee Code paired with bcrypt-hashed passwords (cost factor 12).
- **Stateless Access Tokens (JWT):** Short-lived tokens (15-minute expiration) signed using asymmetric RS256 private keys.
- **Refresh Token Rotation:** Long-lived tokens (7-day sliding expiration) stored in `HttpOnly`, `Secure`, `SameSite=Strict` cookies. Upon usage, the previous refresh token is immediately invalidated and replaced.
- **Single Sign-On (SSO) Ready:** Configured to integrate with institutional Google Workspace / Microsoft Entra ID via SAML 2.0 / OIDC (`REQ-TBD-07`).
- **External Subject Expert Gateway:** Time-limited, cryptographically signed magic links with two-factor SMS/Email OTP verification for external SCM panel members (`REQ-EXT-05`).

### 1.2 Principle of Least Privilege & Separation of Duties
1. **No Self-Approval Invariant (`BR-ENT-003`):** The system strictly bars users from approving, vetting, or recommending their own service change requests, leave applications, or performance evaluations.
2. **Sequential Gate Protection (`BR-M1-004`):** Level-2 Senior Management approval endpoints physically verify that Level-1 HR recommendation has been committed to the database. Bypass is impossible at the API layer.
3. **Departmental Data Scoping:** Deans and HODs are confined to viewing employee profiles, requisitions, and appraisals within their designated academic schools and departments.

---

## 2. Master 16-Actor Permission Matrix

The system governs permissions across all 16 institutional roles:

```
Legend:
C = Create / Initiate | R = Read / View | U = Update / Edit | D = Soft Delete | A = Approve / Sanction | - = Barred
```

| Domain Resource | `ACT-PRO` (Chancellor) | `ACT-VC` (Vice-Chan) | `ACT-REG` (Registrar) | `ACT-VPA` (VP Admin) | `ACT-HHR` (Head HR) | `ACT-HRO` (HR Ops) | `ACT-ADE` (Assoc Dean) | `ACT-DEA` (Dean) | `ACT-HOD` (HOD) | `ACT-EXP` (Ext Expert) | `ACT-SCM` (SCM Panel) | `ACT-ECM` (ECM Panel) | `ACT-FAC` (Faculty) | `ACT-STF` (Staff) | `ACT-GPD` (Group D) | `ACT-SYS` (System) |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **Employee Master (`mod1`)** | R | R | R | R | R, U | C, R, U | R (Dept) | R (School)| R (Dept) | - | - | - | R (Self) | R (Self) | - | U, Sync |
| **Dynamic Org Chart** | R | R | R | R | R | R | R | R | R | - | - | - | R | R | - | Recalc |
| **Digital Dossier** | R | R | R | R | R | C, R, U | - | - | - | - | - | - | R (Self) | R (Self) | - | Archive |
| **Change Request (L1 HR)** | - | - | - | - | **A**, R | C, R, U | - | C, R | C, R | - | - | - | - | - | - | - |
| **Change Request (L2 Mgmt)**| **A**, R | **A**, R | **A**, R | - | - | R | - | - | - | - | - | - | - | - | - | Auto-Act |
| **Resignation Acceptance** | R | R | R | - | I | I | - | **A**, C | - | - | - | - | - | - | - | Handshake |
| **Academic Manpower Req** | **A**, R | R | R | - | R, Vett | R | C, R | C, R | - | - | - | - | - | - | - | Trigger |
| **Non-Academic Manpower** | **A**, R | - | R | R | R, Vett | R | - | - | C, R | - | - | - | - | - | - | Quota Chk |
| **Central CV Database** | R | - | - | - | R | C, R, U | - | - | - | - | - | - | - | - | - | Screen |
| **SCM Scoring Matrix** | R | **A**, R | R | - | R | R | R | R | R | **Score**| **Score** | - | - | - | - | Rank |
| **Non-Acad 3-Round Score** | R | - | - | - | R | R | - | - | Score (R1)| - | - | - | - | - | - | Rank |
| **Letter of Intent (LOI)** | **A**, R | - | R | - | R | C, R | - | I | I | - | - | - | - | - | - | PDF Gen |
| **Group-D Monthly Review** | R | - | - | **A**, R | R | R | - | - | C, R, U | - | - | - | - | - | - | Auto-Lock |
| **Group-D Annual Review** | - | - | - | **A**, R | R | R | - | - | - | - | - | - | - | - | - | W-Avg Calc |
| **Staff KRA Goal Locking** | **A**, R | - | - | - | **A**, R | R | - | R | C, R, U | - | - | - | - | C, R (Self)| - | Lock |
| **Staff Quarterly Review** | R | - | - | - | R | R | - | R | R, U | - | - | - | - | C, R (Self)| - | Remind |
| **Faculty Self-Appraisal** | - | - | - | - | R | R | - | - | - | - | - | - | C, R (Self)| - | - | Eligibility |
| **Faculty 4-Unit Vetting** | - | - | - | - | Vett (HR)| - | - | Vett (Dean)| - | - | - | - | - | - | - | Dispute Loop |
| **Faculty ECM Scoring** | **A**, R | R | R | - | R | R | - | - | - | - | - | **Score** | - | - | - | TNU Matrix |
| **Audit Logs** | R | R | R | - | R | - | - | - | - | - | - | - | - | - | - | Write-Only|
| **ERP Sync Outbox** | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | Process |

---

## 3. Data Protection & Privacy Governance

### 3.1 Sensitive Personal Data Masking
| Sensitive Field | Data Classification | Database Storage | Masking Rules on Display | Authorized Roles for Raw View |
|---|---|---|---|---|
| `basic_salary`, `ctc`, `allowances` | Highly Confidential | Encrypted at Rest | Masked as `₹ ••••••` on general lists | `HR_ADMIN`, `PRO_CHANCELLOR`, Self (Own Record) |
| `national_id` (Aadhaar / Passport) | Sensitive Personal | Salted Hash / Encrypted | Masked as `XXXX-XXXX-1234` | `HR_ADMIN` (Verification only) |
| `password_hash` | Critical Security | bcrypt (Salt cost 12) | Never returned in any API response | Zero Access (One-way hash) |
| `interview_scorecards` | Confidential | Plain Relational | Restricted until committee sign-off | Panel Members, `HR_ADMIN`, Management |
| `performance_ratings` | Confidential | Plain Relational | Hidden from peers; visible to supervisors | Evaluating Supervisor, HR, Management, Self |

### 3.2 Row-Level Security (RLS) Policy Implementation
PostgreSQL Row-Level Security policies enforce institutional departmental boundaries at the database kernel level:
```sql
-- Example: HOD Row-Level Security on Group-D Monthly Evaluations
CREATE POLICY hod_group_d_isolation_policy ON mod3_performance.group_d_monthly_evaluations
FOR ALL TO application_user
USING (
  supervisor_id = current_setting('app.current_user_id')::uuid
  OR EXISTS (
    SELECT 1 FROM shared_platform.user_roles ur
    WHERE ur.user_id = current_setting('app.current_user_id')::uuid
    AND ur.role_code IN ('ROLE_HR_ADMIN', 'ROLE_VP_ADMIN', 'ROLE_PRO_CHANCELLOR')
  )
);
```

---

## 4. Audit Trail & Non-Repudiation Policy

1. **Non-Destructive Operations:** SQL `DELETE` is physically revoked on master and transactional tables. Records are soft-deleted via `is_deleted = TRUE`, `deleted_at = NOW()`, `deleted_by = :userId`.
2. **Immutable Audit Ledger:** Every state change automatically triggers an insert into `shared_platform.audit_logs`. The table permissions are strictly `INSERT` and `SELECT`; `UPDATE` and `DELETE` privileges are permanently revoked.
3. **Cryptographic File Verification:** All uploaded documents (CVs, degrees, letters) generate a SHA-256 cryptographic checksum stored in metadata. Any tampering in Object Storage triggers an integrity exception.
