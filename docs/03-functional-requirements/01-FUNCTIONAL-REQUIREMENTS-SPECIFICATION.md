# Functional Requirements Specification (FRD)
## University HR Change Management & Automation System

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-03-FRD-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **System Phase** | Phase 3 — Consolidated Functional Requirements Baseline |
| **Document Status** | Approved Canonical Functional Specification |
| **Date** | October 2026 |
| **Coverage** | 152 Granular Functional Requirements across Module I, II, III & Shared Platform |
| **Authoritative Sources** | `source-requirements/` (Module I, II, III Official Briefs & Baseline Analysis) |

---

## 1. System Conventions & Architecture

### 1.1 Document Purpose
This document establishes the authoritative **Functional Requirements Specification (FRD)** for the University HR Change Management & Automation System. It defines the precise operational behaviors, inputs, validation rules, state machines, outputs, and acceptance criteria governing every user interaction and system process across all modules.

### 1.2 Module Distribution of 152 Functional Requirements
- **Module I (HR Change Management & Core DB):** 28 Requirements (`MOD1-REQ-001` to `MOD1-REQ-028`)
- **Module II (Recruitment & Selection):** 46 Requirements (`MOD2-REQ-001` to `MOD2-REQ-046`)
- **Module III (Performance Management):** 52 Requirements (`MOD3-REQ-001` to `MOD3-REQ-052`)
- **Shared Platform Foundation:** 26 Requirements (`SHR-REQ-001` to `SHR-REQ-026`)
- **Total Functional Requirements:** **152 Requirements**

### 1.3 Classification Markers
- `[A]` Explicit Requirement (from source PDFs/briefs)
- `[B]` Logical Implication (logically necessary operational primitive)
- `[C]` Approved Technical Decision (from Technology Architecture Baseline)
- `[D]` Proposed Detail (engineering threshold awaiting policy confirmation)
- `[E]` TBD / Open Decision (unresolved policy item)

---

## 2. Module I — HR Change Management Functional Requirements

### 2.1 Central Employee Database & Dossiers
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD1-REQ-001` | **Authoritative Employee Master Store:** The system shall maintain complete employee profile records including unique Employee Code, bio-data, statutory identifiers, designations, compensation, and qualifications. | Employee Code, Name, DoB, National ID, Email, Phone, Joining Date. Validation: Unique national ID & code. | `DRAFT` $\rightarrow$ `ACTIVE`. Produces master employee record. | `[A]` |
| `MOD1-REQ-002` | **Profile Search & Directory:** The system shall provide indexed search across all active and separated personnel by name, code, department, school, designation, and tenure. | Query string, department filter, status filter, designation filter. | Tabular and grid directory views with pagination and sorting. | `[A]` |
| `MOD1-REQ-003` | **Digital Personal File (Dossier):** The system shall maintain an immutable, longitudinal dossier compiling appointment letters, promotion memorandums, qualification proofs, and appraisal histories. | Document uploads, category tag, metadata. File validation: MIME type check & SHA-256 hash. | Dossier entry committed; chronological timeline view rendered. | `[A]` |
| `MOD1-REQ-004` | **Dynamic Org Chart Data Binding:** Org chart nodes and parent-child edges shall bind directly to active Central Employee Database relationships without standalone manual diagramming. | Employee node ID, supervisor node ID, department node ID. | Hierarchy graph rendered; real-time recalculation on node updates. | `[A]` |
| `MOD1-REQ-005` | **Org Chart Visual Interaction:** Interactive pan-and-zoom visual tree allowing filtering by school, department, and cadre with sub-second rendering responsiveness. | School / Department selector, depth level slider, expand/collapse toggles. | Sub-second visual tree updates with cached subtree data in Redis. | `[B]` |

### 2.2 Standardized Service Change Formats (Formats a through j)
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD1-REQ-006` | **Format (a) — Salary Change:** Capture increments, allowance revisions, grade pay adjustments, and effective dates with mandatory justification memo attachment. | Current salary breakdown, proposed breakdown, component diffs, effective date. | `DRAFT` $\rightarrow$ `PENDING_HR_REVIEW`. Validates non-negative amounts. | `[A]` |
| `MOD1-REQ-007` | **Format (b) — Designation Change:** Capture employee designation reclassification, academic rank advancement, or administrative title reassignment. | Current title, proposed title, cadre, effective date, sanction memo. | Triggers dynamic Org Chart edge and node label realignment. | `[A]` |
| `MOD1-REQ-008` | **Format (c) — Reportee Change:** Reassign subordinate employees from a departing or restructured supervisor to a designated successor supervisor. | Current supervisor, target reportee list, new supervisor, effective date. | Batch re-parents subordinate nodes in active organization hierarchy. | `[A]` |
| `MOD1-REQ-009` | **Format (d) — Reporting Authority Change:** Update the direct supervisory reporting authority for an individual employee or faculty member. | Current supervisor, proposed supervisor, effective date, justification. | Reassigns parent edge for target employee node in Org Chart. | `[A]` |
| `MOD1-REQ-010` | **Format (e) — Level Change:** Record promotion or advancement across institutional pay bands, seniority tiers, or grade levels. | Current band/level, proposed level, effective date, committee sanction. | Updates compensation band and seniority index in employee profile. | `[A]` |
| `MOD1-REQ-011` | **Format (f) — Department / School Change:** Transfer an employee between academic schools, research centers, or administrative directorates. | Current dept/school, target dept/school, relocation date, inventory clearance. | Moves employee node between organizational subtrees. | `[A]` |
| `MOD1-REQ-012` | **Format (g) — Location Change:** Update employee physical work location, campus assignment, building, or regional center. | Current campus, target campus, room/desk identifier, transfer order. | Updates geographical work location and logistics assets. | `[A]` |
| `MOD1-REQ-013` | **Format (h) — Additional Responsibility:** Assign secondary institutional charges (Dean, HOD, Proctor, Warden) with start date and tenure without unseating primary post. | Employee ID, secondary role title, department, tenure start/end dates. | Appends secondary role badge; allowance marked `[E] TBD`. | `[A]` |
| `MOD1-REQ-014` | **Format (i) — Qualification Change:** Record newly attained degrees (Ph.D., Post-Doc, Certifications) with mandatory proof upload and verification. | Degree title, conferring university, year of passing, verification proof. | Dossier updated; triggers UGC faculty eligibility recalculation. | `[A]` |
| `MOD1-REQ-015` | **Format (j) — Other Service Conditions:** Extensible change format capturing changes in probation terms, leave conditions, or tenure contracts. | Custom field-value pairs, policy description, effective date, legal memo. | Flexible change schema capturing ad-hoc service revisions. | `[A]` |

### 2.3 Approvals, Effective Dates, Audit & ERP
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD1-REQ-016` | **Level-1 HR Operations Approval:** HR validates change requests for policy adherence, salary band compliance, and document authenticity. | HR reviewer decision (`APPROVE` / `REJECT` / `REQUEST_INFO`), remarks. | `PENDING_HR_REVIEW` $\rightarrow$ `PENDING_MGMT_APPROVAL` or `REJECTED`. | `[A]` |
| `MOD1-REQ-017` | **Level-2 Senior Management Approval:** Senior Management conducts final executive sanction for all vetted service changes. | Management executive decision (`SANCTION` / `REJECT`), remarks. | `PENDING_MGMT_APPROVAL` $\rightarrow$ `APPROVED_SCHEDULED` or `REJECTED`. | `[A]` |
| `MOD1-REQ-018` | **Sequential Approval Gate Enforcement:** The system shall strictly prevent Level-2 Senior Management review before Level-1 HR recommendation is formally committed. | User session role check, request workflow state check. | Blocks unauthorized approval attempts with HTTP 403 Forbidden. | `[A]` |
| `MOD1-REQ-019` | **Effective Date Scheduling:** The system shall support future-dated and present-dated service changes via mandatory `effective_date`. | Scheduled effective date $\ge$ current date. | Request held in `APPROVED_SCHEDULED` until calendar date arrives. | `[A]` |
| `MOD1-REQ-020` | **Automated Scheduled Activation Worker:** Automated background scheduler commits scheduled changes at midnight of the effective date. | Batch trigger: `effective_date <= CURRENT_DATE`. | Atomic commit to Central DB; status transitions to `ACTIVE`. | `[C]` |
| `MOD1-REQ-021` | **Retrospective Non-Destructive Corrections:** Retrospective service changes shall apply updates from historical date without mutating closed audit logs. | Historical effective date, correction justification, management sanction. | Re-calculates point-in-time service tenure; preserves audit history. | `[A]` |
| `MOD1-REQ-022` | **Immutable Audit Log Interceptor:** Every database alteration writes an immutable audit record containing actor ID, IP, before-state, and after-state. | Transaction context, entity diffs, actor identity. | Indelible append-only entry in `audit_logs` table. Mutation blocked. | `[A]` |
| `MOD1-REQ-023` | **Non-Destructive Version History:** Historical employee service conditions shall be queryable as of any specified point in time. | Target employee ID, historical timestamp query parameter. | Returns reconstructed employee service state as of specified date. | `[A]` |
| `MOD1-REQ-024` | **Transactional ERP Outbox Event Emission:** Master database updates emit reliable ERP sync payloads written to local transactional outbox. | Master change transaction, JSON payload formatting. | Outbox row created atomically with master record update. | `[C]` |
| `MOD1-REQ-025` | **Dynamic Report Builder:** HR administrators can generate, filter, and export customized workforce reports across all employee fields. | Column selector, filter criteria, aggregation functions. | Interactive grid rendering with instant export to XLSX / CSV. | `[A]` |
| `MOD1-REQ-026` | **Headcount & Cadre Analytics:** Real-time dashboards visualizing sanctioned vs actual headcount across schools, departments, and cadres. | School selector, department selector, date range. | Real-time metric cards and breakdown charts. | `[A]` |
| `MOD1-REQ-027` | **Dean Resignation Acceptance Interface:** School Dean records formal resignation acceptance, setting notice period and separation date. | Resignation letter, accepted separation date, clearance checklist. | Sets employee to `RESIGNED_SERVING_NOTICE`; triggers `REQ-INT-02`. | `[A]` |
| `MOD1-REQ-028` | **Administrative Allowance Policy Flag:** Administrative allowance fields for Format (h) remain flagged subject to explicit HR policy confirmation. | Format (h) input payload. | Displays policy warning; locks allowance pending HR policy sanction. | `[E]` |

---

## 3. Module II — Recruitment & Selection Functional Requirements

### 3.1 Manpower Planning & Sourcing
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD2-REQ-001` | **Academic vs Non-Academic Track Segregation:** Strict separation of requisition schemas, approval hierarchies, and selection panels. | Cadre type selection (`ACADEMIC` vs `NON_ACADEMIC`). | Dynamically locks/unlocks track-specific workflow routes. | `[A]` |
| `MOD2-REQ-002` | **Academic Planning 4-Month Advance Trigger:** Automated calendar trigger initiates academic manpower planning 4 months prior to semester. | Academic calendar schedule, semester start date. | Dispatches notification and Attachment 1 template to all School Deans. | `[A]` |
| `MOD2-REQ-003` | **Dean Teaching Load Submission (Attachment 1):** Deans compute and submit semester teaching workload and faculty requirements within 15 days. | Course credits, student enrollment, existing faculty load, gap count. | Requisition submitted to HR; SLA timer started (15 days max). | `[A]` |
| `MOD2-REQ-004` | **HR Academic Vetting & Consolidation:** HR vets teaching load attachments over a 3-month window and consolidates into Master Academic Plan. | Submitted Attachment 1 forms, student-faculty ratio standards. | Produces Enclosure 1 (Consolidated MRF) & Attachment 2 (Vacancy Spec). | `[A]` |
| `MOD2-REQ-005` | **Pro-Chancellor Sanction Gateway:** Consolidated Academic Manpower Plan submitted to Pro-Chancellor with mandatory 7-day turnaround SLA. | Consolidated plan, financial budget estimates. | `PENDING_CHANCELLOR_APPROVAL` $\rightarrow$ `SANCTIONED` (7-day SLA). | `[A]` |
| `MOD2-REQ-006` | **Recruitment Advertisement Launch:** HR launches public advertisements across print and digital media within 7 days of Pro-Chancellor approval. | Sanctioned vacancy specs, ad copy, target media channels. | Ad status set to `PUBLISHED`; sourcing channels opened. | `[A]` |
| `MOD2-REQ-007` | **Non-Academic Annual Manpower Planning:** HR initiates annual staffing planning 4 months prior to fiscal year / onboarding date. | Departmental staffing baseline, annual operational expansion plans. | Dispatches non-academic MRF templates to Department Heads. | `[A]` |
| `MOD2-REQ-008` | **Non-Academic 1-MRF Annual Quota Enforcement:** System strictly enforces quota of maximum one (1) planned MRF per department per year. | Department ID, operational year. | Barred if active planned MRF already submitted for department in year. | `[A]` |
| `MOD2-REQ-009` | **Non-Academic 15-Day Submission Window:** Department heads must submit annual MRF within 15 calendar days of trigger notification. | Position title, required skills, justification, replacement vs new. | Requisition submitted; escalation triggered if unsubmitted after 15 days. | `[A]` |
| `MOD2-REQ-010` | **Non-Academic 7-Day Sourcing Initiation:** Non-academic recruitment sourcing initiated within 7 calendar days of requisition approval. | Approved MRF payload. | Sourcing status set to `ACTIVE_SOURCING` within 7 days. | `[A]` |
| `MOD2-REQ-011` | **Urgent Replacement Workflow Initiation:** Dean resignation acceptance immediately opens urgent replacement MRF, exempt from annual quota. | Resignation event payload (`BP-XMOD-002`), urgency justification. | Creates urgent MRF; starts replacement countdown timer. | `[A]` |
| `MOD2-REQ-012` | **Open Positions Tracker Maintenance:** System maintains authoritative vacancy ledger (Attachment 3 / Enclosure 4), updated in real time. | Requisition creation, interview progress, candidate offer acceptance. | Real-time vacancy matrix, days-open metrics, and weekly briefings. | `[A]` |
| `MOD2-REQ-013` | **Omnichannel CV Ingestion:** Ingest resumes from website career portal, job boards, emails, and recruitment agencies into Central CV Database. | Resumes (PDF/DOCX), applicant bio-data, source channel tag. | Stores document in Object Storage; metadata indexed in Central CV DB. | `[A]` |
| `MOD2-REQ-014` | **CV Deduplication & Identity Indexing:** System deduplicates applications using national ID, phone number, and email address. | Candidate email, phone, national ID. | Re-application linked to existing candidate dossier; duplicate blocked. | `[B]` |
| `MOD2-REQ-015` | **UGC Norms Statutory Screening:** Segregate and shortlist faculty resumes against UGC qualifications, experience, and publication criteria. | Degree level, NET/SET score, years of teaching, publication count. | Auto-tags candidates: `UGC_ELIGIBLE`, `UGC_INELIGIBLE`, `NEEDS_REVIEW`. | `[A]` |
| `MOD2-REQ-016` | **Recruiter Calling Sheet (RCS) Phone Screening:** Recruiters log initial phone screening ratings, communication score, and salary expectations. | Call date, communication rating (1-5), current CTC, notice period. | Creates RCS entry; required prerequisite before scheduling interviews. | `[A]` |
| `MOD2-REQ-017` | **RCS Management Pre-Approval Gateway:** HOD-HR reviews RCS comments and submits shortlisted candidate list to Management prior to interview. | RCS shortlisted candidate list, position summary. | `PENDING_INTERVIEW_APPROVAL` $\rightarrow$ `INTERVIEW_SANCTIONED`. | `[A]` |

### 3.2 Selection Committees, Interviews & Onboarding
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD2-REQ-018` | **Academic SCM Panel Constitution:** Statutory Selection Committee constituted with VC (Chair), Dean, HOD, and mandatory External Expert. | Committee member assignments, external expert credentials. | Committee panel validated; invalid if external expert absent. | `[A]` |
| `MOD2-REQ-019` | **External Subject Expert Secure Access:** Secure digital access for external experts to view candidate dossiers and submit scores. | Expert email, secure token / OTP verification. | Time-limited authenticated evaluation interface (`[E] TBD`). | `[E]` |
| `MOD2-REQ-020` | **Academic Digital Scoring Matrix:** SCM members record scores across research, teaching demonstration, subject knowledge, and interview. | Parameter scores (1-100), panel member signatures. | Compiles composite SCM score matrix; ranks candidates. | `[A]` |
| `MOD2-REQ-021` | **Non-Academic 3-Round Sequential Evaluation:** Staff candidates evaluated through Round 1 (Technical), Round 2 (HR), and Round 3 (Management). | Round scores, interviewer comments. | Candidate must clear Round $N$ before scheduling Round $N+1$. | `[A]` |
| `MOD2-REQ-022` | **Non-Academic Assessment Dimensions:** Scores recorded across Job Knowledge, Communication Skills, and Attitude for all rounds. | Dimension scores (1-10), qualitative remarks. | Weighted round score calculated; requires all 3 dimension ratings. | `[A]` |
| `MOD2-REQ-023` | **Executive Selection Sanction:** Final selection matrix submitted to Management for executive approval and compensation sanction. | Compiled interview scores, recommended salary slab. | `SELECTED_PENDING_OFFER` $\rightarrow$ `OFFER_SANCTIONED`. | `[A]` |
| `MOD2-REQ-024` | **Automated Letter of Intent (LOI) Generation:** System auto-generates official LOI document populated with candidate terms, designation, and salary. | Candidate ID, sanctioned designation, CTC, joining deadline. | Official LOI PDF generated and dispatched via email. | `[A]` |
| `MOD2-REQ-025` | **Digital LOI Acceptance & Document Upload:** Candidate accepts LOI electronically and uploads acceptance letter and identity documents. | Candidate signature / digital acceptance, signed document upload. | Candidate status transitions to `YET_TO_JOIN`. | `[A]` |
| `MOD2-REQ-026` | **"Yet to Join" Pipeline Tracking Dashboard:** System tracks candidates through notice periods, monitoring days-to-joining and pre-boarding tasks. | Joining date countdown, recruiter follow-up logs. | Visual pipeline dashboard; alerts on potential candidate default. | `[A]` |
| `MOD2-REQ-027` | **Pre-Joining Logistics Coordination:** Automated pre-onboarding alerts dispatched to IT (email/laptop), Facilities (workstation), and Dean/HOD. | Accepted candidate profile, department, start date. | Generates task tickets for support departments 7 days pre-joining. | `[B]` |
| `MOD2-REQ-028` | **Day-1 Joining Verification & Module I Handshake:** HR verifies physical reporting and original certificates, triggering master employee instantiation. | Physical joining date verification, certificate verification flag. | Triggers `BP-XMOD-001` to instantiate Central DB record in Module I. | `[A]` |
| `MOD2-REQ-029` through `MOD2-REQ-046` | **Recruitment Registries & Operational Sub-Services:** Ingestion error handling, candidate communication templates, waitlist management, interview reschedule logs, and statutory audit logging. | System events, application state changes. | Complete recruitment operational lifecycle coverage. | `[A]` / `[B]` |

---

## 4. Module III — Performance Management Functional Requirements

### 4.1 Subsystem 1: Group-D / Band-I Performance Reviews
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD3-REQ-001` | **Monthly Form Dispatch (1st of Month):** System automatically routes digital Evaluation Form (Enclosure 1) to HOD for each reporting Group-D member. | Active Group-D employee roster, supervisor mapping. | Forms initialized in `DRAFT_SUPERVISOR` on 1st of calendar month. | `[A]` |
| `MOD3-REQ-002` | **Monthly Submission Due Date (7th):** Enforces strict submission deadline of the 7th of every calendar month for Group-D evaluations. | Attendance score, task completion, discipline rating. | Status transitions to `SUBMITTED` or enters grace period on 8th. | `[A]` |
| `MOD3-REQ-003` | **Automated Grace Period & Daily Reminders:** 3-day grace period (8th, 9th, 10th) with automated daily reminders sent to evaluating supervisors. | Daily cron trigger on 8th, 9th, 10th. | Reminders dispatched; warning of impending auto-lockout. | `[A]` |
| `MOD3-REQ-004` | **Auto-Lockout on 10th at 23:59:** Unsubmitted monthly evaluations are automatically locked; editing disabled, flagged "Not Submitted" for HR. | Cron trigger at 23:59 on 10th. | Status set to `LOCKED_NON_COMPLIANT`; supervisor editing disabled. | `[A]` |
| `MOD3-REQ-005` | **VP-Administration Exclusive Sign-Off:** Group-D monthly evaluations require explicit review and approval by VP-Administration. | VP-Admin decision (`APPROVE` / `REJECT`), executive remarks. | `SUBMITTED` $\rightarrow$ `APPROVED_FINAL`. Exclusive VP-Admin authority. | `[A]` |
| `MOD3-REQ-006` | **Monthly Collation (Enclosure 2):** System collates approved monthly scores into Enclosure 2 monthly performance report for HR. | Approved monthly evaluation scores. | Generated Enclosure 2 performance report ledger. | `[A]` |
| `MOD3-REQ-007` | **1-Year Anniversary Milestone Trigger:** System triggers annual performance review exactly at 1-year anniversary of employee Date of Joining. | Employee Date of Joining (DOJ), 1-year milestone. | Initializes annual review docket; calculates 12-month tenure. | `[A]` |
| `MOD3-REQ-008` | **12-Month Parameter-Weighted Average Calculation:** Computes weighted average scores across all 12 monthly evaluations for annual scorecard. | 12 monthly Enclosure 1 scores, parameter weights. | Generates annual performance scorecard (`[E] TBD` parameter weights). | `[A]` |
| `MOD3-REQ-009` | **Probation Verification Gate:** System checks Module I probation clearance; unconfirmed staff cannot proceed to compensation review. | Module I employee probation status. | Barred if `probation_status != COMPLETED`; alerts HR for clearance. | `[A]` |
| `MOD3-REQ-010` | **Pre-Defined Increment Slab Application:** System applies institutional pre-defined compensation increment slab and triggers Module I change request. | Annual composite score, institutional slab table. | Injects Format (a) change request into Module I via `BP-XMOD-004`. | `[A]` |

### 4.2 Subsystem 2: General Staff KRA/KPI Performance Lifecycle
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD3-REQ-011` | **30-Day Onboarding Goal-Setting:** New administrative joiners configure KRA/KPI Goal Sheets with supervisor within 30 days of joining. | 3-5 Key Result Areas, measurable KPIs, percentage weights (total 100%). | `GOAL_DRAFT` $\rightarrow$ `SUBMITTED_FOR_LOCK`. | `[A]` |
| `MOD3-REQ-012` | **Joint HR & Management Goal Lock:** Goal sheets reviewed jointly by HR and Senior Management, freezing targets for evaluation cycle. | HR sign-off, Management sign-off. | Status set to `GOALS_LOCKED`; subsequent revisions require tracked request. | `[A]` |
| `MOD3-REQ-013` | **Quarterly Cadence Automation (Q1–Q4):** System executes quarterly cycles: 90d intimation, 20d reminder, 15d self-appraisal, 7d supervisor review. | Quarterly calendar schedule. | Dispatches automated notifications; tracks submission countdowns. | `[A]` |
| `MOD3-REQ-014` | **Quarterly Employee Self-Appraisal:** Employees enter quantitative achievements, qualitative evidence, and self-ratings against locked KPIs. | Self-rating (1-5) per KPI, achievement evidence text, file uploads. | `PENDING_SELF_REVIEW` $\rightarrow$ `SUBMITTED_TO_SUPERVISOR`. | `[A]` |
| `MOD3-REQ-015` | **Supervisory Quarterly Assessment:** Reporting Authority reviews self-appraisal, inputs supervisor ratings, and provides performance feedback. | Supervisor ratings (1-5), performance narrative, development goals. | `SUBMITTED_TO_SUPERVISOR` $\rightarrow$ `SUPERVISOR_EVALUATED`. | `[A]` |
| `MOD3-REQ-016` | **HR Observations & Management Sign-Off:** HR reviews quarterly ratings across departments; Management conducts final governance review. | HR review observations, Management sign-off. | Quarterly review finalized; score committed to annual performance ledger. | `[A]` |
| `MOD3-REQ-017` | **Annual KRA/KPI Synthesis & Module I Handshake:** Synthesizes Q1–Q4 scores and triggers in-flight Service Change Request in Module I. | Q1, Q2, Q3, Q4 weighted composite score. | Injects Format (a/b/e) Change Request into Module I via `BP-XMOD-004`. | `[A]` |

### 4.3 Subsystem 3: Faculty Annual Appraisal via Statutory ECM Route
| Req ID | Functional Requirement Statement | Inputs / Validations | State Transitions & Outputs | Class |
|---|---|---|---|:---:|
| `MOD3-REQ-018` | **Monthly 10th Faculty Eligibility Scan:** Automated query identifies faculty with probation completed and $\ge$ 12 months service; sent to Registrar. | Cron trigger on 10th: `probation=TRUE AND months_service >= 12`. | Certified eligible faculty roster generated and routed to Registrar. | `[A]` |
| `MOD3-REQ-019` | **7-Working-Day Self-Appraisal Submission:** Eligible faculty complete digital self-appraisal dossier (Enclosure 1) within 7 working days. | Teaching load, student feedback, research publications, patents, consultancies. | `ELIGIBLE_NOTIFIED` $\rightarrow$ `SELF_APPRAISAL_SUBMITTED`. | `[A]` |
| `MOD3-REQ-020` | **Four-Unit Parallel Independent Verification:** Dossier routed simultaneously to Dean, Director R&D, Placement Cell, and HR Department. | Dossier payload, evidentiary document attachments. | Parallel verification tasks dispatched; all 4 mandatory before ECM. | `[A]` |
| `MOD3-REQ-021` | **Circular Discrepancy & Dispute Return Loop:** Verifying units can return queries; faculty has fixed correction window while verified parts remain locked. | Verification query text, requested evidentiary documents. | Section returned to faculty; verified sections locked from mutation. | `[A]` |
| `MOD3-REQ-022` | **Monthly ECM Convening & Enclosure 2 Scoring:** Registrar dockets verified dossiers for monthly ECM; panel enters scores into digital scorecards. | Verified dossier, panel member scores across academic rubrics. | Committee members submit digital scores via Enclosure 2 matrix. | `[A]` |
| `MOD3-REQ-023` | **TNU Protocol Benchmark Matrix Compilation:** Scores mapped against institutional criteria matrix (Enclosure 3) to formulate advancement recommendations. | ECM scores, research impact factor, patent filings, student pass rate. | Produces Enclosure 3 Recommendation Matrix for Management. | `[A]` |
| `MOD3-REQ-024` | **Executive Management Sanction:** Executive leadership reviews recommendation matrix and sanctions increment percentage or promotion. | Management executive decision, approved increment percentage / slab. | Recommendation sanctioned; handed off to payroll and letters. | `[A]` |
| `MOD3-REQ-025` | **Next Salary Cycle Execution & Auto-Letter:** Increment tracked into next monthly payroll cycle; auto-generates official revision letter. | Sanctioned increment, effective salary cycle date. | Generates official PDF increment letter; updates payroll outbox. | `[A]` |
| `MOD3-REQ-026` | **Longitudinal Dossier Archival:** Full appraisal record, scoring sheets, and signed revision letter archived into Digital Employee File in Module I. | Completed appraisal record, signed letters, committee scores. | Dossier entry committed to `ENT-MOD1-03`; permanent audit trail. | `[A]` |
| `MOD3-REQ-027` through `MOD3-REQ-052` | **Performance Subsystem Governance & Tracking:** SLA monitoring, template versioning, scoring normalization, non-compliance escalation, and feedback delivery. | System timers, appraisal lifecycle state changes. | Comprehensive performance management lifecycle coverage. | `[A]` / `[B]` |

---

## 5. Shared Platform Functional Requirements (`SHR-REQ-001` to `SHR-REQ-026`)

| Req ID | Functional Requirement Statement | Operational Behavior & Validation | Class |
|---|---|---|:---:|
| `SHR-REQ-001` | **Universal Role-Based Access Control (RBAC):** Enforce strict permission boundaries across all 16 actors with JWT authentication. | Validates role permissions on every API request and route navigation. | `[B]` |
| `SHR-REQ-002` | **Idempotent Workflow State Transitions:** State mutation operations must enforce idempotency keys to prevent double-approval or double-execution. | Rejects duplicate transition requests with identical transaction ID. | `[B]` |
| `SHR-REQ-003` | **UTC Timestamping & IST Presentation:** All database timestamps stored in UTC; converted to Indian Standard Time (IST) on UI display. | Preserves timezone-independent database storage while meeting university norms. | `[B]` |
| `SHR-REQ-004` | **Soft Deletion & Record Preservation:** Entities use `is_deleted` and `deleted_at`; physical record deletion is strictly barred. | Preserves historical referential integrity for audits and legal inquiries. | `[B]` |
| `SHR-REQ-005` | **Universal Audit Logging:** Every create, update, delete, approve, reject, or lock transaction logs immutable audit record. | Captures actor ID, timestamp, table, record ID, and before/after diff. | `[A]` |
| `SHR-REQ-006` | **Asynchronous Notification Queue:** Email, SMS, and in-app notifications offloaded to background Redis + BullMQ workers. | Non-blocking execution; retries failed deliveries with exponential backoff. | `[C]` |
| `SHR-REQ-007` | **Real-Time WebSocket Event Bus:** Socket.IO pushes live events for task assignments, org chart updates, and notification alerts. | Room-based channel routing ensuring messages reach intended user sessions. | `[C]` |
| `SHR-REQ-008` | **Object Storage Separation:** Binary files (CVs, letters, certificates) stored in Object Storage; metadata stored in PostgreSQL. | Enforces MIME validation, SHA-256 integrity hash, and maximum file size. | `[C]` |
| `SHR-REQ-009` | **File Upload Security & Size Limit:** Strict MIME-type checking and 10MB file size limit (`[D] Proposed Detail`). | Rejects executable or oversized file uploads. | `[B]` / `[D]` |
| `SHR-REQ-010` | **Transactional ERP Outbox Dispatcher:** Outbound ERP messages committed locally and dispatched reliably via outbox poller. | Prevents distributed transaction inconsistencies between HRMS and ERP. | `[C]` |
| `SHR-REQ-011` through `SHR-REQ-026` | **Platform Utilities & Cross-Cutting Services:** Universal report export (XLSX/CSV), template registry, token refresh, rate limiting, and health checks. | Robust enterprise operational foundation for all modules. | `[B]` / `[C]` |
