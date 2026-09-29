# Cross-Module Business Processes
## Institutional Life-Cycle Handshakes & Inter-Module Process Interactions

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/02-business-process/05-CROSS-MODULE-BUSINESS-PROCESSES.md` |
| **System Phase** | Phase 2 — Business Process Documentation |
| **Project** | University HR Change Management & Automation System |
| **Status** | `PROPOSED BASELINE` |
| **Scope** | Cross-Module Business Interactions (Module I ↔ Module II ↔ Module III) |
| **Authoritative Sources** | Module I, Module II, and Module III Official Requirement Briefs; `PROJECT_REQUIREMENTS_ANALYSIS.md`; `docs/01-requirements/`; `docs/03-functional-requirements/` |
| **Technology Independence** | Strictly Technology-Neutral — No REST APIs, DB Schemas, Payloads, WebSockets, or Worker Implementations |

---

## 1. Executive Summary & Cross-Module Operational Architecture

The University HR Change Management & Automation System operates across three functional pillars:
1. **Module I:** Core Employee Master Database, Dynamic Organizational Structure, Digital Dossier, and 10-Format Service Change Workflow.
2. **Module II:** Academic Manpower Planning & Statutory Selection, Non-Academic Multi-Round Selection, Urgent Resignation-Triggered Replacement, and CV/Positions Registries.
3. **Module III:** Three Autonomous Performance Subsystems (Group-D Monthly/Annual, General Staff Quarterly KRA/KPI, and Faculty Monthly ECM Appraisals).

While each module enforces rigorous institutional autonomy and specialized domain governance, institutional operations require seamless lifecycle continuity. In accordance with Core Enterprise Requirement `REQ-ENT-02` (elimination of duplicate data entry and manual re-keying), the system establishes **five authoritative cross-module business handshakes**.

These handshakes define institutional procedures, data flows, operational triggers, and governance conditions connecting processes across module boundaries. They are documented here strictly at the **business process level**, completely independent of underlying technical integration mechanisms (such as messaging queues, database transactions, or API endpoints).

```
   ┌─────────────────────────────────────────────────────────────────────────────────────────┐
   │                                MODULE II: RECRUITMENT                                    │
   │  ┌───────────────────────┐                                 ┌─────────────────────────┐  │
   │  │ Academic Selection    │                                 │ Urgent Replacement      │  │
   │  │ Non-Academic Rounds   │                                 │ Recruitment Clock       │  │
   │  └──────────┬────────────┘                                 └────────────▲────────────┘  │
   └─────────────┼───────────────────────────────────────────────────────────┼───────────────┘
                 │ Handshake 1: Onboarding (`BP-XMOD-001`)                   │ Handshake 2: Resignation
                 │ Selected Candidate → New Master Record                    │ Accepted → Urgent MRF
                 ▼                                                           │ (`BP-XMOD-002`)
   ┌─────────────────────────────────────────────────────────────────────────┴───────────────┐
   │                                MODULE I: CENTRAL MASTER                                  │
   │  ┌───────────────────────────────────────────────────────────────────────────────────┐  │
   │  │ Central Employee Database (CDB)  │ Dynamic Org Chart │ Digital Dossier            │  │
   │  │ 10-Format Service Change Workflow: HR Review → Senior Management Approval         │  │
   │  └──────────┬───────────────────────────────────────────────────────────▲────────────┘  │
   └─────────────┼───────────────────────────────────────────────────────────┼───────────────┘
                 │ Handshake 3: Master Data Feed (`BP-XMOD-003`)             │ Handshake 4: Appraisal
                 │ DOJ, Probation, Hierarchy → Eligibility Baseline          │ Increment/Promotion
                 │                                                           │ (`BP-XMOD-004`)
                 │ Handshake 5: Org Restructure / Transfer                   │
                 │ Hierarchy Realignment → Routing Update (`BP-XMOD-005`)    │
                 ▼                                                           │
   ┌─────────────────────────────────────────────────────────────────────────┴───────────────┐
   │                               MODULE III: PERFORMANCE                                    │
   │  ┌───────────────────────┐   ┌───────────────────────┐   ┌───────────────────────────┐  │
   │  │ Subsystem 1: Group-D  │   │ Subsystem 2: Staff    │   │ Subsystem 3: Faculty ECM  │  │
   │  │ Monthly/Annual Review │   │ Quarterly KRA/KPI     │   │ Eligibility / Scoring     │  │
   │  └───────────────────────┘   └───────────────────────┘   └───────────────────────────┘  │
   └─────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Cross-Module Process Master Register

| Process ID | Process Name | Source Module | Target Module | Institutional Handshake Purpose | Source Requirements | Class |
|---|---|---|---|---|---|---|
| **`BP-XMOD-001`** | Candidate Onboarding to Central Employee Master Record Generation | Module II (Recruitment) | Module I (Central Master) | Automatically instantiates new permanent employee master record, digital dossier, and org chart node upon candidate onboarding verification. | Mod II Brief Sec 1–2; Mod I Brief Objective; `REQ-INT-01`, `SHR-INT-REQ-01`, `REQ-ENT-02` | `[A]` |
| **`BP-XMOD-002`** | Resignation Acceptance to Urgent Replacement Position Initiation | Module I (Central Master) | Module II (Recruitment) | Automatically triggers urgent replacement countdown clock and alerts Head HR when an employee resignation is formally accepted by Dean. | Mod II Brief Sec 1(i); Mod I CDB; `REQ-INT-02`, `SHR-INT-REQ-02`, `MOD2-URG-REQ-01` | `[A]` |
| **`BP-XMOD-003`** | Employee Master Baseline and Hierarchy Provisioning to Performance Subsystems | Module I (Central Master) | Module III (Performance) | Continuously feeds employee Date of Joining, probation status, department, and supervisory hierarchy to drive eligibility and routing. | Mod I Brief Background; Mod III Briefs Subsystems 1–3; `REQ-INT-03`, `SHR-INT-REQ-03`, `REQ-ENT-02` | `[A]` |
| **`BP-XMOD-004`** | Performance Outcome Service Change Initiation into Central Records | Module III (Performance) | Module I (Central Master) | Automatically injects formal Module I Service Change Requests for salary, designation, or level adjustments following approved annual appraisals. | Mod III Brief Stage 3 & TNU Protocol; Mod I Brief Structure 3; `REQ-INT-04`, `SHR-INT-REQ-04`, `MOD3-KRA-REQ-05` | `[A]` |
| **`BP-XMOD-005`** | Organization Realignment and Supervisor Transfer to Performance Routing Update | Module I (Central Master) | Module III (Performance) | Automatically updates active and pending supervisory review routing across performance subsystems when org structure or reporting authority changes. | Mod I Brief Structure 2 & 3(d); Mod III Briefs Subsystems 1–3; `MOD1-ORG-REQ-01`, `MOD1-CHG-REQ-04`, `REQ-INT-03` | `[B]` |

---

## 3. Detailed Cross-Module Process Specifications

```markdown
### Process Identifier: BP-XMOD-001
**Process Name:** Candidate Onboarding to Central Employee Master Record Generation

1. **Module / Operational Track:** Cross-Module Integration (Module II Recruitment → Module I Central Employee Database).
2. **Business Purpose:** To transition a selected candidate from pre-employment recruitment status into active institutional employment without duplicate data entry, manual re-keying, or administrative delay, establishing a single authoritative employee dossier and organizational node.
3. **Operational Trigger:** Candidate signs and accepts Letter of Intent (LOI) / Offer Letter, reports on the confirmed Date of Joining (DOJ), and successfully completes Day-1 physical/digital joining verification with the HR Department.
4. **Prerequisites & Entry Conditions:**
   - Formal candidate selection approved via Statutory SCM (Academic) or Management Round 3 (Non-Academic).
   - Issued LOI accepted by the candidate with confirmed joining date.
   - Verified joining report submitted to HR Department.
5. **Primary Actors:** Candidate, Recruiter / Recruitment Coordinator, HR Onboarding Executive, Head HR.
6. **Supporting Actors:** School Dean / Department Head (accepting department), Senior Management (institutional appointment signatory).
7. **Business Inputs & Documentation:**
   - Candidate Selection Dossier (SCM Matrix or Non-Academic 3-Round Evaluation Sheet).
   - Signed LOI / Offer Acceptance Form.
   - Verified Candidate Profile (Full Name, Date of Birth, Contact Details, Permanent Address, Identity Proofs).
   - Educational & Professional Credentials (Degree certificates, UGC NET/GATE proofs, experience letters).
   - Statutory Enclosures & Clearances (Medical fitness certificate, character certificates, background check).
   - Approved Job Parameters (Official Designation, Department/School, Level/Band, Initial Salary Structure, Reporting Authority).
8. **Sequential Business Activities:**
   - Step 1: Candidate reports to HR Department on scheduled Date of Joining and submits original physical credentials for verification against digital records.
   - Step 2: HR Onboarding Executive marks candidate status as "Reported & Verified" in the recruitment tracking system (`BP-M2-ACAD-012` or `BP-M2-NACAD-007`).
   - Step 3: System initiates Cross-Module Handshake `BP-XMOD-001`, transmitting the complete verified recruitment dossier to Module I.
   - Step 4: Module I instantiates a new Central Employee Master Record (`BP-M1-001`) and assigns a permanent, unique University Employee Code.
   - Step 5: Module I creates the Digital Employee File / Dossier (`BP-M1-003`), attaching all pre-employment certificates, CV, LOI, and joining documents.
   - Step 6: Module I places the employee node into the Dynamic Organization Structure (`BP-M1-002`) under the specified Department/School and linked directly to the designated Reporting Authority.
   - Step 7: Module II updates the Open Positions Tracker (`BP-M2-TRK-002`), marking the requisitioned vacancy as "Position Filled" and recording recruitment cycle duration.
   - Step 8: Module I emits joining confirmation to the Dean/HOD and triggers downstream operational orientations.
9. **Decision Points & Evaluation Rules:**
   - Verification Gate: If original documents diverge from recruitment submission, onboarding is paused pending HR review; if verified, master record creation proceeds automatically.
   - Quota Fulfillment Rule: The filled position is reconciled against the department's approved annual manpower quota.
10. **Approval Points & Governance Gates:**
    - Day-1 Joining Verification Sign-off by Head HR / Designated Onboarding Authority.
    - Final Appointment Confirmation by Senior Management / Registrar.
11. **Institutional Outputs & Deliverables:**
    - New Active Permanent Employee Record in Module I Central Employee Database.
    - Permanent University Employee Code.
    - Fully populated Digital Employee Dossier (`BP-M1-003`).
    - Active Organizational Node in Dynamic Hierarchy (`BP-M1-002`).
    - Closed Vacancy Status in Module II Open Positions Tracker (`BP-M2-TRK-002`).
12. **Operational SLA & Business Deadlines:**
    - Master record generation and dossier creation must occur within 24 hours of verified Day-1 reporting.
    - Dynamic organization chart reflection must take immediate operational effect upon record activation.
13. **Reminders, Escalations & Lockouts:**
    - If Day-1 joining is marked but master record is pending verification after 24 hours, automated alerts escalate to Head HR.
14. **Exception Handling & Alternate Paths:**
    - *Candidate No-Show on Confirmed DOJ:* Candidate marked "Failed to Join" in Module II Yet-to-Join Tracker; no Module I record is created; vacancy is returned to active sourcing or waitlist pool.
    - *Discrepancy in Original Documents:* Joining held in abeyance; 7-day compliance window granted to candidate.
15. **Cross-Module Interactions & Handoffs:**
    - Source: Module II (Recruitment Tracking).
    - Target: Module I (Central Master Database & Dynamic Org Chart).
    - Subsequent Downstream: Module I newly created record feeds Module III Performance Management via `BP-XMOD-003` to initialize probationary monitoring.
16. **Process Completion Criteria:**
    - Employee master record is active in Central Database.
    - Unique Employee Code is assigned.
    - Dossier contains all pre-employment enclosures.
    - Employee is visible in institutional organization chart.
17. **Audit & Compliance Requirements:**
    - Immutable audit trail linking the new Employee Code to the original Module II Recruitment Requisition ID, SCM Selection Reference, and HR Onboarding Sign-off.
18. **Authoritative Source References:**
    - Module II Requirement Brief Section 1 & Section 2.
    - Module I Requirement Brief: Background & Objective ("eliminate duplicate data entry").
    - `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`: `REQ-INT-01` (`SHR-INT-REQ-01`), `REQ-ENT-02`.
    - `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md`: `SHR-INT-REQ-01`.
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):**
    - None for standard onboarding handshake. (ERP integration protocol details handled separately under `BP-M1-009` / `REQ-TBD-02`).
```

---

```markdown
### Process Identifier: BP-XMOD-002
**Process Name:** Resignation Acceptance to Urgent Replacement Position Initiation

1. **Module / Operational Track:** Cross-Module Integration (Module I Central Master → Module II Urgent Recruitment).
2. **Business Purpose:** To eliminate academic curriculum interruption and operational downtime by immediately triggering an urgent replacement recruitment cycle the moment an employee resignation is formally accepted by institutional leadership.
3. **Operational Trigger:** Formal acceptance of an academic or critical non-academic employee's resignation by the School Dean / Competent Authority in Module I.
4. **Prerequisites & Entry Conditions:**
   - Active employee record in Module I Central Database.
   - Resignation letter formally processed and accepted by School Dean / Competent Authority.
   - Department Dean confirms that the vacated post is vital and cannot remain vacant until the next annual planning cycle.
5. **Primary Actors:** School Dean, Head HR, Recruiter / Recruitment Coordinator.
6. **Supporting Actors:** Resigning Employee, Senior Management / Pro-Chancellor.
7. **Business Inputs & Documentation:**
   - Approved Resignation Acceptance Order signed by School Dean.
   - Resigning Employee Master Record Details (Official Designation, Department/School, Specialization/Subjects Taught, Salary Band).
   - Agreed Effective Separation Date / Last Working Day.
   - Dean's Urgent Replacement Justification Note.
8. **Sequential Business Activities:**
   - Step 1: School Dean formally records resignation acceptance in Module I employee service records.
   - Step 2: Module I initiates Cross-Module Handshake `BP-XMOD-002`, dispatching an immediate urgent replacement notice to Module II.
   - Step 3: Module II instantiates an ad-hoc Urgent Manpower Requisition Form (MRF) (`BP-M2-URG-001`), bypassing standard annual manpower planning quota restrictions.
   - Step 4: System starts the urgent replacement countdown clock in Module II, targeting position fulfillment prior to the employee's last working day or semester start.
   - Step 5: High-priority notification is dispatched to Head HR and the Recruitment Team detailing the vacated post parameters and urgent timelines.
   - Step 6: Module II registers the vacancy in the Open Positions Tracker (`BP-M2-TRK-002`) with the mandatory flag "Urgent Replacement — Priority 1".
   - Step 7: Recruitment Team immediately queries the Central CV Database (`BP-M2-TRK-001`) for pre-screened matching candidates and initiates expedited multi-channel sourcing (`BP-M2-ACAD-007` or `BP-M2-NACAD-004`).
9. **Decision Points & Evaluation Rules:**
   - Replacement Eligibility Rule: Resignation acceptance automatically entitles the department to an urgent replacement MRF, exempt from the "one planned MRF per department per year" non-academic restriction (`REQ-MOD2-09`).
   - Timeline Calculation Rule: Replacement clock is calibrated against the resigning employee's notice period (typically 30–90 days).
10. **Approval Points & Governance Gates:**
    - Resignation Acceptance Sign-off by School Dean / Competent Authority.
    - Urgent MRF Ratification by Head HR and Pro-Chancellor / Senior Management.
11. **Institutional Outputs & Deliverables:**
    - Active Urgent Replacement MRF in Module II.
    - Active Urgent Countdown Clock.
    - High-Priority Urgent Position Entry in Open Positions Tracker.
    - HR Alert and Sourcing Directive.
12. **Operational SLA & Business Deadlines:**
    - Handshake transmission from Module I resignation acceptance to Module II MRF generation: Immediate / within 4 hours.
    - Recruitment team sourcing initiation: Within 24 hours of notification.
    - Replacement target fulfillment: Position filled at least 15 days before the departing employee's last working day or semester commencement.
13. **Reminders, Escalations & Lockouts:**
    - Daily countdown alerts sent to Recruitment Team and Head HR tracking remaining days until employee separation.
    - Weekly executive escalation to Senior Management if no qualified candidates reach the interview stage within 15 days of resignation notice.
14. **Exception Handling & Alternate Paths:**
    - *Dean Recommends Non-Replacement:* If Dean determines the position can be absorbed through internal workload reallocation, Dean marks "Replacement Not Required"; Handshake `BP-XMOD-002` is suppressed, and position is decommissioned upon separation.
    - *Resignation Withdrawn:* If resignation withdrawal is officially sanctioned by Competent Authority prior to separation, the urgent MRF in Module II is cancelled and noted in audit history.
15. **Cross-Module Interactions & Handoffs:**
    - Source: Module I (Central Employee Database / Separation Tracking).
    - Target: Module II (Urgent Replacement Recruitment Lifecycle `BP-M2-URG-001`).
    - Feedback Loop: When urgent replacement candidate is hired, `BP-XMOD-001` generates the new employee record in Module I.
16. **Process Completion Criteria:**
    - Urgent MRF created and active in Module II.
    - Vacancy logged in Open Positions Tracker.
    - Recruitment countdown running.
17. **Audit & Compliance Requirements:**
    - Cross-module linkage tying the urgent requisition directly to the resigning employee's service record, resignation acceptance date, and Dean's justification.
18. **Authoritative Source References:**
    - Module II Requirement Brief Section 1(i) ("Resignation acceptance by Dean triggers urgent replacement requirement").
    - Module I Requirement Brief: Central Employee Database.
    - `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`: `REQ-INT-02` (`SHR-INT-REQ-02`), `REQ-MOD2-03`, `REQ-MOD2-09`.
    - `docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`: `MOD2-URG-REQ-01`.
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):**
    - `REQ-TBD-01`: Institutional resignation intake mechanism and employee self-service separation workflow pending university policy specification (cross-module handshake activates strictly upon Dean's formal acceptance).
```

---

```markdown
### Process Identifier: BP-XMOD-003
**Process Name:** Employee Master Baseline and Hierarchy Provisioning to Performance Subsystems

1. **Module / Operational Track:** Cross-Module Integration (Module I Central Master → Module III Performance Subsystems).
2. **Business Purpose:** To provide Module III performance tracks with continuous, authoritative employee master data (Date of Joining, probation status, current department, and reporting supervisor hierarchy), guaranteeing that appraisal eligibility calculations, goal-setting timers, and evaluation routing are 100% accurate and synchronized with organizational reality.
3. **Operational Trigger:** 
   - Real-time event: Activation of new employee record (`BP-XMOD-001`) or approval of an employee service change (department transfer, reporting authority change, promotion, probation clearance).
   - Scheduled evaluation scan: Monthly 10th eligibility evaluation for Faculty ECM (`BP-M3-FAC-001`), monthly 1st dispatch for Group-D (`BP-M3-GD-001`), or quarterly cycle opening for Staff KRA/KPI (`BP-M3-KRA-002`).
4. **Prerequisites & Entry Conditions:**
   - Active, approved employee records in Module I Central Employee Database.
   - Valid structural alignment in Module I Dynamic Organization Chart.
5. **Primary Actors:** Module I Master Records Authority (HR Operations), Performance System Administrators.
6. **Supporting Actors:** School Deans, Department Heads, Reporting Supervisors.
7. **Business Inputs & Documentation:**
   - Active Employee Master Record Attributes:
     - Unique Employee Code and Full Name.
     - Employment Classification (Group-D / Band-I, General Staff, Academic Faculty).
     - Confirmed Date of Joining (DOJ).
     - Current Probation Status (On Probation / Probation Completed) and Clearance Date.
     - Assigned School / Department and Official Designation.
     - Active Primary Reporting Authority / Supervisor Node.
     - Last Approved Appraisal / Service Change Effective Date.
8. **Sequential Business Activities:**
   - Step 1: Module I acts as the single authoritative source of truth for all employee master attributes and reporting relationships.
   - Step 2: Upon master record creation or modification, Module I provisions updated baseline data to Module III.
   - Step 3: **Subsystem 1 (Group-D) Consumption:** Module III uses active Group-D roster and supervisor assignments to dispatch monthly evaluation forms on the 1st of every month (`BP-M3-GD-001`) and tracks 1-year DOJ anniversary for annual consolidation (`BP-M3-GD-006`).
   - Step 4: **Subsystem 2 (General Staff) Consumption:** Module III tracks DOJ to initiate the mandatory 30-day onboarding goal-setting window (`BP-M3-KRA-001`) and routes quarterly self-appraisals to the active reporting supervisor (`BP-M3-KRA-003`).
   - Step 5: **Subsystem 3 (Faculty ECM) Consumption:** On the 10th of every month, Module III evaluates the Master Baseline against statutory eligibility conditions:
     $$\text{Eligibility} = (\text{Probation Completed} = \text{TRUE}) \land (\text{Service Period since DOJ or Last Appraisal} \ge 12 \text{ months})$$
   - Step 6: Module III generates the certified eligible faculty roster for Registrar routing (`BP-M3-FAC-002`).
9. **Decision Points & Evaluation Rules:**
   - Classification Branching: Employees are routed strictly into their designated performance subsystem; no employee can be evaluated under an incompatible appraisal framework.
   - Eligibility Gating: Employees on active probation are barred from annual increment reviews in Subsystems 1 and 3 until probation clearance is certified in Module I master records.
10. **Approval Points & Governance Gates:**
    - Master record changes must be fully approved by HR and Senior Management in Module I before becoming active baselines in Module III.
11. **Institutional Outputs & Deliverables:**
    - Authoritative, synchronized baseline data across all three Module III performance subsystems.
    - Certified Monthly Group-D Evaluation Roster.
    - Active Staff KRA/KPI Review Cycle Enrolment.
    - Certified Monthly Faculty ECM Eligibility Roster.
12. **Operational SLA & Business Deadlines:**
    - Baseline synchronization must be instantaneous upon effective-date activation in Module I.
    - Faculty eligibility batch evaluation must execute on the 10th of every calendar month.
13. **Reminders, Escalations & Lockouts:**
    - If an active employee lacks an assigned reporting authority in Module I, the performance system raises an immediate administrative exception to HR Operations, blocking evaluation dispatch until the hierarchy is resolved.
14. **Exception Handling & Alternate Paths:**
    - *Mid-Cycle Department Transfer:* If an employee transfers department mid-cycle, Module I updates the active baseline; Module III preserves historical quarterly reviews under the previous supervisor while routing subsequent stages to the new supervisor.
    - *Probation Extension:* If probation is extended in Module I, eligibility status in Module III remains locked to "Ineligible" until formal clearance.
15. **Cross-Module Interactions & Handoffs:**
    - Source: Module I (Central Master Database & Dynamic Org Chart).
    - Target: Module III (Subsystems 1, 2, and 3).
    - Flow Direction: Unidirectional continuous master baseline provisioning.
16. **Process Completion Criteria:**
    - Performance records reflect current master data without local discrepancies or stale caches.
17. **Audit & Compliance Requirements:**
    - Every appraisal eligibility determination must log the exact snapshot of Module I master attributes (DOJ, probation clearance date, supervisor ID) used to validate eligibility.
18. **Authoritative Source References:**
    - Module I Requirement Brief: Central Employee Database & Universal Master Baseline.
    - Module III Requirement Brief: Subsystem 1, Subsystem 2 (Stage 1), Subsystem 3 (Eligibility Criteria).
    - `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`: `REQ-INT-03` (`SHR-INT-REQ-03`), `REQ-ENT-02`.
    - `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md`: `SHR-INT-REQ-03`.
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):**
    - None. (Master baseline authority is fully established).
```

---

```markdown
### Process Identifier: BP-XMOD-004
**Process Name:** Performance Outcome Service Change Initiation into Central Records

1. **Module / Operational Track:** Cross-Module Integration (Module III Performance Outcomes → Module I Service Change Workflow).
2. **Business Purpose:** To translate formally approved annual performance outcomes (increments, merit promotions, band level upgrades) into binding employee service record modifications without manual paper processing, transcription errors, or administrative bottlenecks.
3. **Operational Trigger:** Executive sign-off and final approval of an annual performance appraisal outcome across any of the three Module III subsystems:
   - Group-D Annual Evaluation approved by VP-Administration / Management (`BP-M3-GD-007`).
   - General Staff Annual KRA/KPI consolidated review approved by HR & Management (`BP-M3-KRA-004`).
   - Faculty ECM Appraisal and TNU Protocol Matrix approved by Management (`BP-M3-FAC-007`).
4. **Prerequisites & Entry Conditions:**
   - Formal performance evaluation cycle fully concluded in Module III.
   - Final approval granted by the competent institutional governance authority (VP-Administration or Management).
   - Appraisal outcome document or compensation increment recommendation officially generated.
5. **Primary Actors:** Performance Management Authority, HR Operations Reviewer, Head HR.
6. **Supporting Actors:** Senior Management / Vice-Chancellor / Pro-Chancellor.
7. **Business Inputs & Documentation:**
   - Approved Performance Appraisal Summary / Evaluation Dossier.
   - Recommended Service Change Specifications:
     - Change Format 1: Salary Revision / Increment Amount / Revised Basic Pay.
     - Change Format 2: Designation Change / Merit Promotion Title.
     - Change Format 5: Level / Band Upgrade.
   - Effective Date of Service Change (e.g., anniversary of joining, next salary cycle, or start of financial year).
   - Official Institutional Reference (ECM Resolution Number, Management Approval Minute, or Appraisal Letter ID).
8. **Sequential Business Activities:**
   - Step 1: Upon executive approval in Module III, the performance subsystem concludes the appraisal cycle and compiles the finalized outcome package.
   - Step 2: System executes Cross-Module Handshake `BP-XMOD-004`, transmitting the outcome specifications to Module I.
   - Step 3: Module I automatically generates an in-flight Employee Service Change Request (`BP-M1-004`) pre-populated with:
     - Affected Employee Code and Current Service Record.
     - Targeted Change Format(s): Salary (Format 1), Designation (Format 2), and/or Level (Format 5).
     - Proposed New Values and Justification linking directly to the Module III Appraisal ID.
     - Mandated Institutional Effective Date.
   - Step 4: The generated change request is automatically queued in the Module I Level-1 HR Review inbox (`BP-M1-005`).
   - Step 5: HR Department reviews the pre-populated request against university compensation guidelines and submits it to Level-2 Senior Management Approval (`BP-M1-006`).
   - Step 6: Senior Management grants formal institutional approval.
   - Step 7: On the mandated effective date, Module I executes Effective-Date Activation (`BP-M1-007`), updating the active Central Master Record, committing an entry to the Immutable Audit Ledger (`BP-M1-008`), and transmitting the revision to external ERP payroll (`BP-M1-009`).
   - Step 8: Module III attaches the finalized Module I Service Change Reference to the employee's permanent appraisal archive (`BP-M3-FAC-009` or `BP-M3-KRA-005`).
9. **Decision Points & Evaluation Rules:**
   - Change Format Mapping: Performance outcomes map strictly to Formats 1 (Salary), 2 (Designation), or 5 (Level). Lateral transfers or reporting changes are never generated by performance outcomes.
   - Governance Consistency Rule: An appraisal outcome cannot bypass the mandatory Module I two-level approval hierarchy (`HR → Senior Management`) (`REQ-MOD1-05`, `REQ-MOD1-06`).
10. **Approval Points & Governance Gates:**
    - Module III Executive Sign-off (VP-Administration or Management).
    - Module I Level-1 HR Verification (`BP-M1-005`).
    - Module I Level-2 Senior Management Formal Approval (`BP-M1-006`).
11. **Institutional Outputs & Deliverables:**
    - Formally generated Module I Employee Service Change Request.
    - Updated Central Employee Master Record on Effective Date.
    - Immutable Audit Log Record in Module I Ledger.
    - Outbound ERP Payroll Synchronization Payload.
    - Linked Archive Record in Module III Performance History.
12. **Operational SLA & Business Deadlines:**
    - Handshake transmission from Module III approval to Module I request generation: Immediate / within 2 hours.
    - HR Review and Senior Management approval processing: Completed prior to the cutoff of the upcoming institutional salary cycle.
13. **Reminders, Escalations & Lockouts:**
    - If a performance-generated service change request remains unapproved in Module I within 5 days of the monthly payroll cutoff, automated escalation alerts are dispatched to Head HR.
14. **Exception Handling & Alternate Paths:**
    - *No Increment / Performance Unsatisfactory:* If annual appraisal yields no salary or designation change (e.g., performance below threshold), Handshake `BP-XMOD-004` is not initiated; appraisal outcome is archived strictly within Module III.
    - *Disputed Appraisal Outcome:* If an employee raises an appraisal dispute under institutional grievance procedures, the service change request in Module I is placed on administrative hold pending grievance committee findings.
15. **Cross-Module Interactions & Handoffs:**
    - Source: Module III (Performance Subsystems 1, 2, or 3).
    - Target: Module I (Employee Service Change Workflow `BP-M1-004` to `BP-M1-007`).
    - Downstream: Module I updates feed external ERP payroll (`BP-M1-009`).
16. **Process Completion Criteria:**
    - Approved performance changes are reflected in Module I Central Database on the designated effective date.
    - Audit ledger contains complete before/after state.
17. **Audit & Compliance Requirements:**
    - Full end-to-end traceability linking the final payroll salary figure in Module I back to the specific committee scores, peer reviews, and executive approvals in Module III.
18. **Authoritative Source References:**
    - Module III Requirement Brief: Subsystem 2 Stage 3 ("annual appraisal outcome feeds directly into Module I change request"); Subsystem 3 (TNU Protocol Matrix & Salary Cycle).
    - Module I Requirement Brief: Structure 3 (10 Service Change Formats: Salary, Designation, Level).
    - `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`: `REQ-INT-04` (`SHR-INT-REQ-04`), `REQ-ENT-02`.
    - `docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md`: `SHR-INT-REQ-04`.
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):**
    - `REQ-TBD-05`: University compensation bands, increment slabs, and formula mappings for Group-D annual reviews.
```

---

```markdown
### Process Identifier: BP-XMOD-005
**Process Name:** Organization Realignment and Supervisor Transfer to Performance Routing Update

1. **Module / Operational Track:** Cross-Module Integration (Module I Dynamic Org Chart / Service Changes → Module III Performance Routing).
2. **Business Purpose:** To dynamically realign active performance review routing, supervisory evaluation inboxes, and historical accountability across all Module III subsystems whenever organizational restructuring, faculty transfers, or reporting authority changes occur in Module I.
3. **Operational Trigger:** Effective-date activation of an approved Module I Service Change involving:
   - Change Format 4: Reporting Authority Change (`BP-M1-004d`).
   - Change Format 6: Department / School Transfer (`BP-M1-004f`).
   - Change Format 8: Additional Responsibility Allocation (`BP-M1-004h`).
   - Dynamic Organization Structure Restructuring (`BP-M1-002`).
4. **Prerequisites & Entry Conditions:**
   - Full approval of the structural or supervisory change through Module I Level-1 HR Review and Level-2 Senior Management Approval.
   - Arrival of the scheduled `effective_date` triggering activation in Module I Central Database.
5. **Primary Actors:** Module I Operations Authority (HR Records), Reporting Supervisors (Outgoing & Incoming).
6. **Supporting Actors:** Affected Employees, School Deans / Department Heads, Performance Administrators.
7. **Business Inputs & Documentation:**
   - Approved Module I Service Change Order (Format 4, 6, 8, or Org Structure Revision).
   - Affected Employee Code and Department.
   - Previous Reporting Authority / Supervisor Node.
   - Newly Assigned Reporting Authority / Supervisor Node.
   - Validated Effective Date of Realignment.
8. **Sequential Business Activities:**
   - Step 1: Module I activates the structural change on its mandated effective date (`BP-M1-007`), updating the active master record and dynamic organizational tree (`BP-M1-002`).
   - Step 2: System triggers Cross-Module Handshake `BP-XMOD-005`, transmitting the reassignment notice to Module III.
   - Step 3: **Subsystem 1 (Group-D) Realignment:**
     - Upcoming monthly evaluation forms (`BP-M3-GD-001`) are automatically routed to the new supervisor's inbox.
     - Any unsubmitted evaluation form for the current month is re-assigned to the new supervisor with an informational note on the transfer date.
     - Completed historical evaluations remain permanently attributed to the supervisor who signed them.
   - Step 4: **Subsystem 2 (General Staff KRA/KPI) Realignment:**
     - The employee's active quarterly evaluation workflow (`BP-M3-KRA-003`) updates its supervisory review stage to the newly appointed Reporting Authority.
     - If the transfer occurs mid-quarter, both outgoing and incoming supervisors receive notification, and institutional policy governs whether a joint review or split evaluation is performed (`REQ-TBD-04`).
     - Historical quarterly ratings submitted by previous supervisors are locked and preserved in the employee's appraisal history.
   - Step 5: **Subsystem 3 (Faculty ECM) Realignment:**
     - If a faculty member transfers schools, the monthly 10th eligibility scan links the faculty member to the new School Dean for verification routing (`BP-M3-FAC-004`).
     - Ongoing self-appraisal verifications submitted prior to the effective date are completed by the originating Dean unless formally transferred by Registrar directive.
   - Step 6: Module III dispatches system notifications to both outgoing and incoming supervisors confirming the transfer of performance appraisal responsibilities.
9. **Decision Points & Evaluation Rules:**
   - Active vs. Historical Separation: Completed evaluations are immutable and must never have their evaluating supervisor retroactively modified.
   - Mid-Cycle Handover Rule: In-flight evaluations currently pending supervisor sign-off are re-routed to the incoming supervisor, who is granted full visibility into previously submitted self-appraisal text and objective evidence.
10. **Approval Points & Governance Gates:**
    - Structural realignment is governed entirely by Module I Level-1 HR and Level-2 Senior Management approval; Module III routing executes automatically upon activation without requiring secondary appraisal approvals.
11. **Institutional Outputs & Deliverables:**
    - Realigned Supervisory Evaluation Inboxes in Module III.
    - Updated Workflow Routing for Group-D, Staff KRA, and Faculty ECM evaluations.
    - Automated Notifications to Outgoing and Incoming Supervisors.
    - Audit Log of Supervisory Responsibility Transfer.
12. **Operational SLA & Business Deadlines:**
    - Performance routing realignment must take operational effect synchronously with Module I effective-date activation (00:00 midnight of effective date).
13. **Reminders, Escalations & Lockouts:**
    - If a pending evaluation form remains untouched in an outgoing supervisor's inbox after the transfer date, system automatically reassigns it to the incoming supervisor after 48 hours.
14. **Exception Handling & Alternate Paths:**
    - *Interim / Vacant Supervisor Node:* If an employee is transferred to a department where the supervisor position is currently vacant, Module III automatically routes evaluation tasks to the next higher administrative level (e.g., School Dean or Department Head) until the supervisory post is filled.
15. **Cross-Module Interactions & Handoffs:**
    - Source: Module I (Dynamic Org Chart & Service Change Formats 4/6/8).
    - Target: Module III (Subsystems 1, 2, and 3 Workflow Engines).
    - Flow Direction: Unidirectional hierarchy and routing propagation.
16. **Process Completion Criteria:**
    - New supervisor possesses active review authority in Module III.
    - Outgoing supervisor retains read-only audit access to past evaluations.
    - No orphaned or stranded evaluation forms exist in the workflow.
17. **Audit & Compliance Requirements:**
    - System maintains an indelible audit record documenting every supervisory reassignment, recording the authorizing Module I Change Request ID, effective date, and timestamp of routing realignment.
18. **Authoritative Source References:**
    - Module I Requirement Brief: Structure 2 (Dynamic Org Structure), Structure 3(d) (Reporting Authority Change).
    - Module III Requirement Brief: Subsystems 1, 2, 3 (Supervisory Evaluation and Verification Stages).
    - `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`: `REQ-INT-03`, `REQ-MOD1-04`, `REQ-MOD1-08`.
    - `docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`: `MOD1-ORG-REQ-01`, `MOD1-CHG-REQ-04`.
19. **Classification:** `[B] Logical Implication`.
20. **Controlled Open Decisions (TBD):**
    - `REQ-TBD-04`: Mid-quarter supervisor transfer evaluation attribution guidelines (pro-rata vs. incoming supervisor full sign-off).
```

---

## 4. Cross-Module Data Flow & Information Matrix

The following matrix documents the specific institutional business information transferred across module boundaries for each handshake, identifying the business purpose and receiving operational process:

| Handshake ID | Source Module | Target Module | Institutional Information Transferred | Business Purpose | Receiving Business Process |
|---|---|---|---|---|---|
| **`BP-XMOD-001`** | Module II (Recruitment) | Module I (Central Master) | Full Candidate Profile, Identity Credentials, SCM/Interview Dossier, Signed LOI, Verified Joining Report, Degree Certificates, Approved Designation, Department, Band/Level, Initial Salary Structure, Reporting Authority. | Eliminates duplicate manual entry; instantiates permanent Master Record, Digital Dossier, and Org Chart node; closes recruitment position. | `BP-M1-001` (Central DB), `BP-M1-002` (Org Chart), `BP-M1-003` (Dossier), `BP-M2-TRK-002` (Open Positions). |
| **`BP-XMOD-002`** | Module I (Central Master) | Module II (Recruitment) | Resigning Employee Code, Designation, Department/School, Subject Specialization, Date of Resignation Acceptance, Last Working Day, Dean's Justification Note. | Alerts Head HR immediately; triggers urgent replacement countdown clock; opens ad-hoc MRF outside annual quota. | `BP-M2-URG-001` (Urgent Replacement Lifecycle), `BP-M2-TRK-002` (Open Positions Tracker). |
| **`BP-XMOD-003`** | Module I (Central Master) | Module III (Performance) | Unique Employee Code, Employment Category (Group-D, Staff, Faculty), Date of Joining (DOJ), Probation Status & Clearance Date, School/Department, Active Reporting Supervisor Node, Last Increment Effective Date. | Provides single authoritative source of truth driving appraisal eligibility calculations, goal-setting timers, and supervisory routing across all three subsystems. | `BP-M3-GD-001` (Group-D Monthly), `BP-M3-KRA-001` (Staff Goals), `BP-M3-FAC-001` (Faculty ECM Eligibility). |
| **`BP-XMOD-004`** | Module III (Performance) | Module I (Central Master) | Employee Code, Approved Appraisal Score/Category, Recommended Change Formats (Salary Format 1, Designation Format 2, Level Format 5), Proposed Values, Effective Date, Appraisal Letter Reference. | Pre-populates formal Service Change Request in Module I; eliminates manual re-keying; subjects appraisal increments to two-level governance approval. | `BP-M1-004` (Service Change Request), `BP-M1-005` (HR Review), `BP-M1-006` (Senior Management Approval), `BP-M1-007` (Effective Date). |
| **`BP-XMOD-005`** | Module I (Central Master) | Module III (Performance) | Employee Code, Department/School, Previous Reporting Supervisor, Newly Appointed Reporting Supervisor, Effective Date of Transfer, Authorizing Change Request ID. | Dynamically realigns active and upcoming evaluation routing in Module III; reassigns supervisor evaluation inboxes while preserving historical evaluation integrity. | `BP-M3-GD-002` (Group-D Supervisor Inbox), `BP-M3-KRA-003` (Staff Quarterly Review), `BP-M3-FAC-004` (Faculty Dean Verification). |

---

## 5. Cross-Module Requirement Traceability

The five cross-module business processes establish comprehensive traceability to official enterprise and inter-module requirements:

| Business Process ID | Process Title | Primary Requirement ID | Functional Requirement ID | Classification | Future Detailed Workflow Target |
|---|---|---|---|---|---|
| **`BP-XMOD-001`** | Candidate Onboarding to Central Employee Master Record Generation | `REQ-INT-01`, `REQ-ENT-02` | `SHR-INT-REQ-01`, `MOD1-CDB-REQ-01` | `[A]` Explicit Requirement | `TBD — Phase 6 Workflows` |
| **`BP-XMOD-002`** | Resignation Acceptance to Urgent Replacement Position Initiation | `REQ-INT-02`, `REQ-MOD2-03` | `SHR-INT-REQ-02`, `MOD2-URG-REQ-01` | `[A]` Explicit Requirement | `TBD — Phase 6 Workflows` |
| **`BP-XMOD-003`** | Employee Master Baseline and Hierarchy Provisioning to Performance Subsystems | `REQ-INT-03`, `REQ-ENT-02` | `SHR-INT-REQ-03`, `MOD3-FAC-REQ-01` | `[A]` Explicit Requirement | `TBD — Phase 6 Workflows` |
| **`BP-XMOD-004`** | Performance Outcome Service Change Initiation into Central Records | `REQ-INT-04`, `REQ-MOD3-13` | `SHR-INT-REQ-04`, `MOD1-CHG-REQ-01` | `[A]` Explicit Requirement | `TBD — Phase 6 Workflows` |
| **`BP-XMOD-005`** | Organization Realignment and Supervisor Transfer to Performance Routing Update | `REQ-INT-03`, `REQ-MOD1-04` | `MOD1-ORG-REQ-01`, `MOD1-CHG-REQ-04` | `[B]` Logical Implication | `TBD — Phase 6 Workflows` |

---

## 6. Strict Technology-Independence Declaration

In strict compliance with Phase 2 documentation governance:
- **No Technical Implementation Artifacts:** This document defines no REST API endpoints, HTTP query parameters, JSON payload schemas, WebSocket events, Socket.IO namespaces, Redis Pub/Sub channels, BullMQ jobs, database tables, foreign keys, or ORM entity models.
- **Pure Business Semantics:** All interactions are specified as institutional administrative actions, business data transfers, and governance approvals between operational HR functions.
- **Architectural Reference:** Technical mechanisms governing these handshakes (such as transactional outbox tables, message brokers, and idempotent consumers) are established under [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md) and will be formally detailed in Phase 6 (Workflows) and Phase 9 (API Specifications).

---
*End of Document — Cross-Module Business Processes.*
