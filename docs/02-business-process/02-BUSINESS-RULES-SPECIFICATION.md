# Business Rules Specification
## University HR Change Management & Automation System

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-02-BRS-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **System Phase** | Phase 2 — Consolidated Business Rules Catalogue |
| **Document Status** | Approved Canonical Business Rules Baseline |
| **Date** | October 2026 |
| **Coverage** | 60 Complete Business Rules across Modules I, II, III, Shared, and Cross-Module |
| **Authoritative Sources** | `source-requirements/` (Official Requirement Briefs & Baseline Analysis) |

---

## 1. Executive Summary & Rule Architecture

This catalogue consolidates every authoritative **Business Rule** and **Decision Point** operating across the University HR Change Management & Automation System. These rules represent non-negotiable institutional invariants, policy constraints, statutory council mandates, and administrative gating controls.

### Summary Rule Count:
- **Module I (Core Master & Service Changes):** 8 Rules (`BR-M1-001` to `BR-M1-008`)
- **Module II (Recruitment Automation):** 22 Rules (`BR-M2-001` to `BR-M2-022`)
- **Module III (Performance Management):** 21 Rules (`BR-M3-001` to `BR-M3-021`)
- **Shared Enterprise Platform:** 4 Rules (`BR-ENT-001` to `BR-ENT-004`)
- **Cross-Module Integration:** 5 Rules (`BR-XMOD-001` to `BR-XMOD-005`)
- **Total Invariant Business Rules:** **60 Rules**

---

## 2. Module I Business Rules (Core Master & Service Changes)

| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M1-001`** | **Central Database Authority & Uniqueness:** Central Employee Database is the sole authoritative master; each employee must possess exactly one unique Employee Code. | Profile creation or query | IF identical national identity or primary credential exists, duplicate is rejected. | Master integrity preserved; duplicates strictly barred. | `[A]` |
| **`BR-M1-002`** | **Dynamic Organization Chart Reflection:** Any approved change to department, supervisor, designation, or role must reflect in active org hierarchy. | Effective-date activation | IF change affects structural edges or titles, hierarchy updates on effective date. | Real-time institutional org chart without manual diagram edits. | `[A]` |
| **`BR-M1-003`** | **Fixed 10 Service Change Formats Invariant:** Service changes restricted exclusively to the 10 approved formats: (1) Salary, (2) Designation, (3) Reportee, (4) Supervisor, (5) Level, (6) Department, (7) Location, (8) Additional Responsibility, (9) Qualifications, (10) Other. | Change request initiation | IF proposed change does not map to one of 10 formats, submission is barred. | Standardized change governance; ad-hoc untracked alterations prevented. | `[A]` |
| **`BR-M1-004`** | **Mandatory Two-Level Sequential Approval:** Every change must undergo sequential Level-1 HR Review followed by Level-2 Senior Management Approval. | Change request workflow | IF request lacks Level-1 HR recommendation, Senior Management cannot view or approve. | Strict administrative hierarchy preserved; no bypass of HR vetting. | `[A]` |
| **`BR-M1-005`** | **Atomic Effective-Date Activation:** Approved changes take legal effect on `effective_date`; future changes remain scheduled, retrospective changes apply without mutating historical audits. | Arrival of effective date | IF `current_date < effective_date`, status is Scheduled; IF `current_date >= effective_date`, status is Active. | Payroll and operational systems synchronize on sanctioned calendar date. | `[A]` |
| **`BR-M1-006`** | **Immutable Audit Trail Invariant:** Every creation, modification, approval, rejection, or lockout must write an indelible audit record with actor ID, timestamp, and diffs. | Any state alteration | IF state change occurs, write indelible audit log; deletion or mutation is strictly barred. | Complete regulatory traceability and legal accountability. | `[A]` |
| **`BR-M1-007`** | **Administrative Allowance Subject to HR Policy:** Assignment of Additional Responsibility (Format 8) does not confer automatic financial compensation; allowance subject to explicit HR sanction. | Format 8 processing | IF additional responsibility assigned, mark allowance field subject to HR policy sanction. | Prevents unauthorized financial commitments. | `[E]` |
| **`BR-M1-008`** | **Real-Time Dynamic Reporting Invariant:** Institutional reports, executive summaries, and rosters must be generated dynamically from current active database records. | Report query execution | Compute from active master records and audit history without static spreadsheet dependencies. | Real-time administrative visibility into workforce demographics. | `[A]` |

---

## 3. Module II Business Rules (Recruitment Automation)

### 3.1 Track 1: Academic Recruitment Rules
| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M2-001`** | **Segregation of Academic and Non-Academic Tracks:** Academic and non-academic paths must remain strictly separate in governance, timelines, committees, and criteria. | Manpower requisition initiation | IF requisition is for teaching post, route through Academic Track; staff workflows cannot be applied. | UGC and statutory council compliance; academic meritocracy maintained. | `[A]` |
| **`BR-M2-002`** | **Academic Manpower Planning 4-Month Lead Time:** Planning initiated at least 4 months prior to semester commencement. | Calendar milestone: 4 months pre-sem | IF calendar reaches 4 months prior to semester, trigger Academic Planning workflow. | Guarantees sufficient institutional lead time for statutory search and selection. | `[A]` |
| **`BR-M2-003`** | **Dean 15-Day Submission Window:** School Deans must submit academic manpower requirements and teaching loads within 15 calendar days. | Planning initiation alert | IF Dean submission > 15 days, flag overdue and escalate to Pro-Chancellor. | Prevents planning bottlenecks in academic departments. | `[A]` |
| **`BR-M2-004`** | **HR Academic Vetting 3-Month Window:** HR conducts curriculum, workload, and student-faculty ratio vetting across a 3-month window. | Receipt of Dean requisitions | IF vetting duration exceeds 3 months, escalate alerts to Head HR and Registrar. | Thorough scrutiny of faculty-student ratios and teaching workload norms. | `[A]` |
| **`BR-M2-005`** | **Academic Manpower Consolidation 15-Day Window:** HR consolidates requirements into Master Academic Plan within 15 days following vetting completion. | Vetting completion | IF consolidation > 15 days, flag plan submission to Pro-Chancellor as delayed. | Unified institutional recruitment requisition. | `[A]` |
| **`BR-M2-006`** | **Pro-Chancellor Sanction 7-Day Window:** Approval or modification by Pro-Chancellor communicated within 7 calendar days. | Plan submission to Pro-Chancellor | IF approval > 7 days, dispatch executive reminder. | Authorizes immediate recruitment advertisement launch. | `[A]` |
| **`BR-M2-007`** | **Academic Recruitment Completion 1-Month Lead Time:** Entire academic recruitment process must conclude at least 1 month prior to semester. | Recruitment cycle progress | IF hiring incomplete 1 month pre-semester, issue high-priority staffing alert to Management. | Guarantees faculty presence on Day 1 of classes without curriculum disruption. | `[A]` |
| **`BR-M2-014`** | **Mandatory Statutory SCM Panel & External Expert:** Academic faculty selections must be conducted by statutory Selection Committee including external subject expert. | SCM panel formation | IF panel lacks approved external expert, SCM proceedings are invalid. | UGC and statutory charter compliance; unbiased academic evaluation. | `[A]` |
| **`BR-M2-015`** | **Academic Digital Scoring & Selection Matrix:** Academic candidates evaluated across standardized criteria via Digital Scoring Matrix; no unrecorded selection permitted. | SCM interview evaluation | Committee members record scores digitally in SCM matrix; subjective unrecorded selection barred. | Objective, transparent, and auditable academic selection records. | `[A]` |

### 3.2 Track 2: Non-Academic Recruitment Rules
| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M2-008`** | **Non-Academic Planning 4-Month Lead Time:** Non-academic planning initiated at least 4 months prior to target onboarding date. | Calendar: 4 months pre-onboarding | IF calendar reaches 4 months prior, trigger Non-Academic Planning workflow. | Orderly administrative staffing and budget provisioning. | `[A]` |
| **`BR-M2-009`** | **Non-Academic Annual Quota (1 Planned MRF Per Year):** Non-academic departments entitled to exactly one planned MRF per department per year. | Submission of planned MRF | IF department attempts second planned MRF in same year, submission is barred. | Prevents unbudgeted administrative expansion; enforces disciplined planning. | `[A]` |
| **`BR-M2-010`** | **Non-Academic 15-Day Submission Timeline:** Department heads must submit annual MRF within 15 calendar days of trigger. | Planning trigger notification | IF submission > 15 days, flag overdue and escalate to Registrar. | Timely compilation of university staff requirements. | `[A]` |
| **`BR-M2-011`** | **Non-Academic Recruitment Initiation 7-Day Window:** Recruitment execution initiated within 7 calendar days of requisition approval. | Approval of non-academic requisition | IF recruitment not launched within 7 days, alert Head HR. | Rapid sourcing execution following executive sanction. | `[A]` |
| **`BR-M2-012`** | **Non-Academic Recruitment Completion 15-Day Lead Time:** Selection concluded at least 15 days prior to onboarding date. | Selection cycle progress | IF hiring incomplete 15 days pre-joining, alert department head and HR Operations. | Adequate time for onboarding logistics, equipment, and orientation. | `[A]` |
| **`BR-M2-016`** | **Mandatory Three-Round Sequential Evaluation:** Non-academic candidates evaluated through Round 1 (Technical), Round 2 (HR), and Round 3 (Management). | Candidate interview scheduling | IF candidate has not cleared Round $N$, cannot be scheduled for Round $N+1$. | Rigorous multi-stage vetting; technical, behavioral, and management alignment. | `[A]` |
| **`BR-M2-017`** | **Non-Academic Assessment Dimensions:** Candidate evaluation across all rounds must assess Job Knowledge, Communication, and Attitude. | Scoring interview rounds 1–3 | IF evaluation sheet lacks scores for all three dimensions, submission rejected as incomplete. | Comprehensive evaluation of technical competency and cultural fit. | `[A]` |

### 3.3 Track 3: Urgent Replacement Rules
| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M2-013`** | **Urgent Replacement Exemption on Resignation:** Acceptance of resignation by School Dean immediately entitles department to an urgent replacement MRF, exempt from annual quota. | Resignation acceptance by Dean in Mod I | IF Dean resignation acceptance verified, open urgent replacement MRF and start countdown. | Prevents academic vacancy crises; circumvents 4-month cycle restrictions. | `[A]` |

### 3.4 Track 4: Sourcing, Screening & Registries
| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M2-018`** | **LOI Issuance & Candidate Acceptance Invariant:** Formal employment commitments extended exclusively through authorized LOI; onboarding cannot proceed without signed acceptance. | Selection approval | IF candidate has not signed and submitted LOI acceptance, onboarding handshake is barred. | Legal and contractual clarity prior to employment commencement. | `[A]` |
| **`BR-M2-019`** | **Yet-to-Join Lifecycle Tracking:** Candidates who accepted LOI monitored continuously in Yet-to-Join registry until physical reporting or withdrawal. | LOI acceptance | IF candidate reaches DOJ, transition to Joined or No-Show; pre-joining engagement logged. | Minimizes Day-1 dropouts; enables rapid waitlist activation on default. | `[A]` |
| **`BR-M2-020`** | **Central CV Database Invariant:** All resumes ingested, indexed, and deduplicated in central searchable talent repository. | CV receipt from portal/referral | IF CV received, index by qualification, discipline, experience; apply deduplication. | University-wide talent asset preservation; rapid sourcing for urgent vacancies. | `[A]` |
| **`BR-M2-021`** | **Recruiter Calling Sheet (RCS) Gateway:** Every telephonic screening interaction recorded in RCS; candidates cannot advance to interview without active RCS record. | Recruiter phone contact | IF candidate lacks RCS record with "Screened & Shortlisted", scheduling interview is blocked. | Auditable preliminary screening; recruiter accountability. | `[A]` |
| **`BR-M2-022`** | **Open Positions Tracker Maintenance (Attachment 3):** Open positions tracked in standardized format, maintained within 30-day cycle, summarized weekly. | Requisition approval or closure | IF vacancy status changes, update Attachment 3 tracker immediately; produce weekly summary. | Continuous leadership visibility into institutional hiring progress. | `[A]` |

---

## 4. Module III Business Rules (Performance Management)

### 4.1 Subsystem 1: Group-D / Band-I Performance Rules
| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M3-001`** | **Group-D Monthly Due Date (7th of Month):** Monthly evaluation forms dispatched on 1st, formally due by 7th of every calendar month. | Calendar: 1st of month | IF unsubmitted on 7th, notify supervisor that submission is entering grace period. | Predictable monthly appraisal cadence for support and operational staff. | `[A]` |
| **`BR-M3-002`** | **Group-D Grace Period (8th to 10th of Month):** Automated grace period extends from 8th to 10th with daily reminders to supervisors. | Calendar: 8th, 9th, 10th | IF evaluation pending between 8th and 10th, dispatch daily reminders. | Supervisory flexibility while maintaining month-end closure schedules. | `[A]` |
| **`BR-M3-003`** | **Group-D Auto-Lockout on 10th at Cutoff:** Monthly evaluations unsubmitted by end of grace period on 10th are locked automatically; late submission barred. | Calendar: 10th at 23:59 | IF unsubmitted at cutoff on 10th, transition to Locked / Overdue; editing disabled. | Eliminates evaluation delays; enforces monthly administrative discipline. | `[A]` |
| **`BR-M3-004`** | **VP-Administration Exclusive Approval Authority:** Group-D evaluations require explicit review and approval by VP-Administration; no other role can substitute. | Submission of monthly forms | IF monthly evaluation submitted, route exclusively to VP-Administration for sign-off. | Centralized institutional oversight and parity across operational units. | `[A]` |
| **`BR-M3-005`** | **Group-D Monthly Collation (Enclosure 2):** Approved monthly scores collated into standardized Enclosure 2 format across defined parameters. | VP-Admin monthly approval | IF monthly scores approved, collate into Enclosure 2 monthly performance ledger. | Standardized longitudinal performance tracking across 12-month cycle. | `[A]` |
| **`BR-M3-006`** | **Group-D Annual Evaluation at 1-Year from DOJ:** Annual review conducted exactly at 1-year anniversary of DOJ, based on 12-month parameter-weighted averages. | Employee reaches 1 year of DOJ | IF employee completes 12 active months, compile parameter-weighted annual scorecard. | Objective annual appraisal reflecting consistent year-long performance. | `[A]` |
| **`BR-M3-007`** | **Mandatory Group-D Probation Verification Gate:** Annual compensation reviews require prior verification of probation clearance; probationers cannot receive increments. | 1-year annual evaluation | IF probation status != Completed in Module I, annual compensation review is barred. | Prevents unearned salary increments prior to confirmed regularization. | `[A]` |
| **`BR-M3-008`** | **Group-D Pre-Defined Compensation Slabs:** Annual salary adjustments determined strictly through institutional pre-defined increment slabs. | 1-year evaluation approval | IF annual score satisfies threshold, calculate revision per approved institutional slabs. | Transparent, uniform compensation adjustments without arbitrary discretion. | `[A]` |

### 4.2 Subsystem 2: General Staff KRA/KPI Performance Rules
| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M3-009`** | **30-Day Onboarding Goal-Setting Window:** KRAs and KPIs established within 30 calendar days of employee Date of Joining. | Employee Date of Joining | IF goals not submitted within 30 days of DOJ, dispatch alert to supervisor and HR. | Immediate alignment between new staff members and institutional objectives. | `[A]` |
| **`BR-M3-010`** | **Joint HR and Management Goal Approval:** Finalized KRAs and KPIs must receive joint review and sign-off by both HR and Management before locking. | Submission of agreed KRAs/KPIs | IF goals lack joint sign-off from both HR and Management, goal sheet remains unlocked. | Strategic consistency and parity across university administrative departments. | `[A]` |
| **`BR-M3-011`** | **Quarterly Q1–Q4 Review Cadence & Windows:** Staff evaluations operate across Q1–Q4 with 90d intimation, 20d reminder, 15d employee submission, 7d supervisor verification. | Quarterly milestone | IF employee does not submit within 15 days, flag overdue; supervisor gets 7 days to verify. | Structured, continuous quarterly performance evaluation and feedback. | `[A]` |
| **`BR-M3-012`** | **Reporting Authority Review & Management Governance:** Supervisor reviews quarterly self-appraisals; HR provides observations; Management conducts governance review. | Quarterly review submission | IF review verified by supervisor, route through HR observations to Management sign-off. | Balanced governance combining direct supervision with executive oversight. | `[A]` |
| **`BR-M3-013`** | **Annual Consolidation & Direct Module I Handshake:** Final annual performance rating consolidates Q1–Q4 scores and triggers in-flight Module I Service Change Request. | Completion of Q4 cycle | IF consolidated score warrants promotion/increment, generate Module I Change Request. | Automated transition from performance evaluation to service record update. | `[A]` |

### 4.3 Subsystem 3: Faculty ECM Performance Rules
| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-M3-014`** | **Dual Statutory Faculty Eligibility Criteria:** Faculty appraisal eligibility requires: (1) Probation completed = TRUE, AND (2) Service tenure $\ge$ 12 months. | Monthly eligibility scan | IF (Probation Completed = TRUE) AND (Tenure >= 12 Months), flag eligible; ELSE ineligible. | Rigorous compliance with university statutes and UGC service tenure norms. | `[A]` |
| **`BR-M3-015`** | **Monthly 10th Faculty Eligibility Scan & Registrar Routing:** Faculty eligibility evaluated on 10th of every month; certified roster routed to Registrar. | Calendar: 10th of every month | IF calendar reaches 10th, execute batch eligibility scan and send certified roster to Registrar. | Reliable monthly throughput for rolling faculty appraisal anniversaries. | `[A]` |
| **`BR-M3-016`** | **Faculty Self-Appraisal 7-Working-Day Window:** Notified faculty members must formulate, attach evidentiary documents, and submit self-appraisal within 7 working days. | Receipt of appraisal notice | IF submission > 7 working days, dispatch automated reminders and alert Dean. | Timely submission of academic achievements, publications, and feedback. | `[A]` |
| **`BR-M3-017`** | **Four-Unit Parallel Independent Verification:** Submitted faculty dossiers undergo independent, simultaneous verification by Dean, R&D Cell, Placement Cell, and HR. | Dossier submission | Parallel verification tasks dispatched to all 4 units; all 4 mandatory before ECM routing. | Comprehensive multi-faceted vetting of teaching, research, and service. | `[A]` |
| **`BR-M3-018`** | **Circular Discrepancy & Resubmission Loop:** Verifying units can return queries; faculty has fixed correction window while verified sections remain locked. | Discrepancy flagged by unit | IF unit flags discrepancy, return dossier with query; locked sections protected. | Fair administrative hearing and evidentiary accuracy prior to committee review. | `[A]` |
| **`BR-M3-019`** | **Monthly ECM Scoring (Enclosure 2):** Fully verified dossiers evaluated by monthly Executive Committee Meeting applying standardized Digital Scoring Matrix. | All 4 verifications certified | IF all 4 verifications complete, docket candidate for upcoming monthly ECM session. | Formal academic committee assessment under statutory governance. | `[A]` |
| **`BR-M3-020`** | **TNU Protocol Matrix Compilation (Enclosure 3):** Final ECM scores mapped against institutional benchmark matrix (Enclosure 3) to formulate advancement recommendations. | ECM score finalization | IF ECM scores finalized, map candidate against TNU Protocol criteria matrix. | Objective, criteria-driven advancement recommendations submitted to Management. | `[A]` |
| **`BR-M3-021`** | **Management Decision in Next Salary Cycle & Auto-Letter:** Compensation decisions implemented in next monthly salary cycle; auto-generate increment letter and archive dossier. | Management executive approval | IF Management approves, increment takes effect in next salary cycle; letter auto-generated. | Immediate payroll execution and permanent institutional documentation. | `[A]` |

---

## 5. Shared Enterprise Governance Rules

| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-ENT-001`** | **Three Subsystem Independence Invariant:** Group-D, General Staff KRA, and Faculty ECM operate as three distinct, autonomous subsystems; merging is strictly prohibited. | Performance workflow execution | IF appraisal initiated, route strictly within employee's designated subsystem. | Preserves specialized evaluation methodologies tailored to distinct cadres. | `[A]` |
| **`BR-ENT-002`** | **Elimination of Duplicate Data Entry Invariant:** Any verified data change, onboarding, or milestone in any module must automatically propagate to connected records. | Cross-module event or update | IF approved event occurs in Mod I, II, or III, downstream connected records update automatically. | Eliminates human data-entry errors, administrative overhead, and divergence. | `[A]` |
| **`BR-ENT-003`** | **Role-Based Authorization & Segregation of Duties:** System access strictly governed by authenticated roles; no user may approve their own requisition, evaluation, or change. | User action attempt | IF role lacks authorization OR user is subject/initiator of transaction, execution denied. | Institutional segregation of duties and prevention of conflicts of interest. | `[A]` |
| **`BR-ENT-004`** | **Audit Trail Immutability & Indelibility:** Every institutional transaction, decision, score, approval, rejection, and lockout must write an indelible audit log record. | Any state alteration | IF transaction completes, commit audit log with actor ID, timestamp, diffs, and transaction ID. | Complete legal defensibility, regulatory compliance, and post-audit verifiability. | `[A]` |

---

## 6. Cross-Module Integration Rules

| Rule ID | Rule Statement | Context / Trigger | Decision Gating Condition | Operational Outcome | Class |
|---|---|---|---|---|:---:|
| **`BR-XMOD-001`** | **Candidate Onboarding Master Instantiation:** Selected candidate accepts LOI and completes Day-1 joining in Module II; Module I automatically instantiates master employee record. | Candidate Day-1 verification | IF Day-1 joining verified, Module I generates Master Record, Dossier, and Org node via `BP-XMOD-001`. | Instantaneous transition from candidate to employee without administrative delay. | `[A]` |
| **`BR-XMOD-002`** | **Resignation Acceptance Urgent Replacement Trigger:** Acceptance of resignation by School Dean in Module I immediately notifies Head HR and starts Module II replacement countdown. | Dean resignation acceptance in Mod I | IF Dean accepts resignation, Module II opens urgent replacement MRF via `BP-XMOD-002`. | Immediate sourcing mobilization to prevent academic curriculum interruption. | `[A]` |
| **`BR-XMOD-003`** | **Universal Master Baseline for Performance:** Module I Central Database is the single source of truth for all DOJ, probation status, department, and supervisor data consumed by Module III. | Performance eligibility or routing | IF Module III evaluates eligibility, consume directly from Module I master records via `BP-XMOD-003`. | Guarantees performance eligibility and routing are 100% aligned with master records. | `[A]` |
| **`BR-XMOD-004`** | **Appraisal Outcome Service Change Governance:** Approved appraisal outcomes from Module III inject Service Change Requests into Module I, subject to Level-1 & Level-2 approvals. | Executive appraisal approval | IF appraisal approves increment/promotion, inject Module I Change Request via `BP-XMOD-004`. | Eliminates manual re-entry while upholding Module I statutory two-level governance. | `[A]` |
| **`BR-XMOD-005`** | **Organizational Realignment Dynamic Routing Update:** When employee reporting hierarchy updates in Module I, Module III dynamically realigns active supervisory evaluation inboxes. | Effective-date org activation in Mod I | IF reporting hierarchy changes in Mod I, update active evaluation routing via `BP-XMOD-005`. | Ensures performance reviews route to active supervisor while preserving historical integrity. | `[B]` |
