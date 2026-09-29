# Module III Stakeholder Requirement Delta & Impact Analysis
## Post-Release Analysis of Newly Supplied Performance Management Automation Workflow Material

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/01-requirements/08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md` |
| **System Phase** | Phase 2 Post-Release / Controlled Module III Impact Analysis |
| **Project** | University HR Change Management & Automation System |
| **Status** | `PROPOSED DELTA ANALYSIS — AWAITING STAKEHOLDER CONFIRMATION` |
| **Scope** | Controlled Impact Analysis of Newly Received Module III Complete Workflow Diagram |
| **Authoritative Sources** | Original Module III Requirement Brief PDF; Newly Supplied Stakeholder Workflow Diagram (`Module 3 – Performance Management Automation System Complete Workflow`); `PROJECT_REQUIREMENTS_ANALYSIS.md`; `docs/01-requirements/`; `docs/02-business-process/`; `docs/03-functional-requirements/`; `TECHNOLOGY_ARCHITECTURE_BASELINE.md` |
| **File Safety** | Strictly Analysis-Only — Zero Existing Baseline Files Modified |

---

## 1. Purpose

This document performs a formal, controlled **Requirement Delta and Impact Analysis** specifically for **Module III: Performance Management Automation System**, triggered by the receipt of new authoritative stakeholder workflow material provided by the University leadership and project mentors following the completion of Phase 2 Business Process Documentation.

The primary objectives of this analysis are:
1. **Analyze the newly supplied workflow diagram:** `Module 3 — Performance Management Automation System Complete Workflow`, which visually formalizes the three independent performance subsystems alongside shared integration layers.
2. **Evaluate the three performance tracks independently:**
   - **Track A:** Group-D / Band I Employees (Monthly Evaluation, Annual Report & Compensation)
   - **Track B:** General Employees (Non-Faculty) (KRA/KPI, Quarterly Review & Annual Appraisal)
   - **Track C:** Faculty Members (ECM Based Annual Performance Appraisal)
3. **Analyze the four shared governance layers:**
   - **Section D:** Employee File Integration
   - **Section E:** Audit Trail & Version History
   - **Section F:** Reporting (Configurable)
   - **Section G:** Central Employee Database & HR Integration
4. **Catalogue every confirmed rule, clarification, operational extension, potential conflict, and open decision** against established Phase 1 requirements, Phase 2 business processes, and Phase 3 functional requirements.
5. **Maintain strict anti-invention safeguards:** Ensure no evaluation weights, compensation slabs, committee quorums, scoring formulas, or disciplinary policies are arbitrarily invented.
6. **Formulate a controlled change sequence and decision register** for institutional stakeholder review prior to modifying any established baseline.

---

## 2. Baseline Compared

The analysis compares the new stakeholder workflow material against the established project baseline:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                               ESTABLISHED PROJECT BASELINE                              │
├────────────────────────────────┬───────────────────────────────────────────────────────┤
│ Authoritative Source PDF       │ source-requirements/Module-III/                       │
│                                │ Requirement_Brief_Module_III_Performance_Management_   │
│                                │ Automation_System.pdf                                 │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Requirements Analysis Baseline │ PROJECT_REQUIREMENTS_ANALYSIS.md (Section 5)          │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Phase 1 Requirements Layer     │ docs/01-requirements/ (00 to 06, REQ-MOD3-01 to 19,    │
│                                │ REQ-TBD-04, 05, 08, 09)                               │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Phase 2 Business Processes     │ docs/02-business-process/04-MODULE-III-BUSINESS-       │
│                                │ PROCESSES.md (BP-M3-GD-001–008, BP-M3-KRA-001–005,    │
│                                │ BP-M3-FAC-001–009) & Cross-Module BP-XMOD-003–005     │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Phase 3 Functional Reqs (FRD)  │ docs/03-functional-requirements/03-MODULE-III-         │
│                                │ FUNCTIONAL-REQUIREMENTS.md (MOD3-GD, KRA, FAC FRDs)   │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Architecture Baseline          │ TECHNOLOGY_ARCHITECTURE_BASELINE.md & ADR-001         │
└────────────────────────────────┴───────────────────────────────────────────────────────┘
```

---

## 3. New Stakeholder Material

The new asset analyzed is the visual specification diagram:
- **Asset Name:** `Module 3 — Performance Management Automation System Complete Workflow` (`Module_3_Performance_Management_Automation_System.jpeg`)
- **Structure:** Structured into three vertical functional tracks (Track A: Orange, Track B: Green, Track C: Purple) and four horizontal shared utility sections (D, E, F, G: Blue/Grey).
- **Scope Covered:**
  - **Track A (8 stages):** Evaluation Form Repository, Monthly Routing to HOD, Online Submission, VP-Administration Approval, Submission Timeline (7th due, 10th grace, auto-lockout), Monthly Report Generation, Annual Report Generation (1-year milestone, weighted average), Compensation Review (predefined slabs, probation gate).
  - **Track B (6 stages):** Employee Joining & Notification (30 days), KRA/KPI Setup, Joint HR & Management Verification (Goal Lock), Quarterly Review Cycle (Q1 90d, Q2 180d, Q3 270d, Q4 360d, 15d submission, 20d reminder, 7d supervisor verification, HR/Management review), Annual Appraisal, HR Change Integration into Module I.
  - **Track C (10 stages):** Dual Eligibility Check (Probation completed, $\ge$ 12 months service), Monthly 10th List Generation & Registrar Routing, Faculty Self-Appraisal (7 working days), Verification of Documents (Dean, R&D, Placement, HR) with Discrepancy Return Loop, Monthly ECM Scheduling by Registrar, ECM Digital Score Sheet, Evaluation Matrix (TNU Protocol & previous increments), Management Decision, Outcome & Implementation (Salary cycle), Comprehensive Other Outcomes Taxonomy (7 outcomes).
  - **Sections D–G:** Employee Digital File integration, Audit Trail & Version History, Configurable Real-Time Reporting, and Central Employee Database / Module I Synchronization.

---

## 4. Analysis Method & Classification Taxonomy

Every item in the new diagram was examined against existing baselines and classified into standard analytical categories:

| Analytical Category | Operational Definition | Governance Rule |
|---|---|---|
| **1. ALREADY COVERED** | Fully aligned with existing requirement briefs, business processes, and FRDs. | Reaffirms baseline design; no modification needed. |
| **2. NEW EXPLICIT REQUIREMENT** | Introduces a concrete institutional step, role, or feature not previously documented. | Formulate candidate requirement ID; pending review. |
| **3. CLARIFICATION** | Provides crucial operational detail, explicit role assignment, or terminology refinement. | Refine existing process or FRD description upon approval. |
| **4. POTENTIAL CONFLICT** | Inconsistent with existing baseline requirement, role assignment, or timing. | Document divergence; do NOT choose winner; mark confirmation needed. |
| **5. NEW EXCEPTION / SPECIAL CONDITION** | Introduces an explicit alternate path, exception flow, or edge case. | Incorporate into exception catalogue and workflow state machine. |
| **6. TBD / INCOMPLETE** | Acknowledges an institutional policy or rule, but leaves exact formulas or thresholds unspecified. | Map to or create entry in the official TBD register (`REQ-TBD-*`). |

---

## 5. Track A: Group-D / Band I Employees Delta Analysis

### A. Subsystem Narrative & Flow
Track A governs monthly operational evaluations and annual compensation reviews for university support cadres. The diagram reaffirms a disciplined monthly operational cadence coupled with an annual compensation review linked to probation clearance and master data.

```
 [1. Form Repository] ──► [2. Monthly Route to HOD] ──► [3. HOD Completes & Submits]
                                                                  │
                                                                  ▼
                                                   [4. VP-Administration Approval]
                                                                  │
  ┌───────────────────────────────────────────────────────────────┴────────────────────────────────┐
  ▼                                                                                                ▼
 [5. Submission Timeline: 7th Due Date] ──► (8th–10th Grace Period) ──► [If Not Submitted by 10th]
  │                                                                     - Auto-lock submission
  │                                                                     - Mark as "Not Submitted"
  ▼ (Approved)                                                          - Record reason & visible to HR
 [6. Monthly Report Generation (Automatic)]
  │
  ▼ (1-Year from DOJ Anniversary)
 [7. Annual Report Generation (Automatic)] ──► [Management Review]
  - 12-Month Collated Reports
  - Weighted Average (as per HR/Mgmt)
  │
  ▼
 [8. Compensation Review Workflow]
  - Check Probation Status (Must be Completed)
  - Apply Predefined Compensation Slabs
  - Management Decision on Compensation Change
```

### B. Detailed Element-by-Element Comparison

| Diagram Element / Stage | Existing Baseline Representation | New Stakeholder Diagram Representation | Classification | Analysis & Impact |
|---|---|---|---|---|
| **1. Evaluation Form Repository** | `MOD3-GD-REQ-01` cited Enclosure 1 standardized form. | Box 1: Standardized form per Group-D role; role-specific KPIs and competencies; configurable by HR; version control with audit trail; linked to Module I CDB. | **CLARIFICATION** | Clarifies that the repository contains role-specific KPI and competency configurations managed by HR with version control. |
| **2. Monthly Evaluation Routing to HOD** | `BP-M3-GD-002` cited "Reporting Supervisor / Evaluating Supervisor". | Box 2: System routes monthly form to **HOD** (based on department / reporting hierarchy). | **POTENTIAL CONFLICT / CLARIFICATION** | Naming the **HOD** as the receiving and evaluating actor clarifies that department heads directly evaluate Group-D staff or supervise the evaluation hierarchy. |
| **3. HOD Completion and Online Submission** | `BP-M3-GD-002` covered online form submission. | Box 3: HOD completes form online; submits for approval. | **CLARIFICATION** | Reaffirms online web-based completion by HOD. |
| **4. VP-Administration Approval** | `REQ-MOD3-04`, `BP-M3-GD-004`, `BR-M3-004`. Exclusive VP-Admin sign-off. | Box 4: Vice President – Administration reviews and approves monthly form. | **ALREADY COVERED** | Baseline aligns 100%. Reaffirms exclusive executive approval authority. |
| **5. Due Date (7th of Month)** | `REQ-MOD3-01`, `BP-M3-GD-002`, `BR-M3-001`. Due by 7th. | Box 5: Due date: 7th of every month. Automated reminders before due date. | **ALREADY COVERED** | Baseline aligns 100%. |
| **6. Grace Period (Up to 10th)** | `REQ-MOD3-02`, `BP-M3-GD-002`, `BR-M3-002`. Grace period 8th–10th. | Box 5: Grace period: 3 days (up to 10th); automated reminders during grace period. | **ALREADY COVERED** | Baseline aligns 100%. |
| **7. Auto-Lockout on 10th Cutoff** | `REQ-MOD3-03`, `BP-M3-GD-003`, `BR-M3-003`. Form locks on 10th. | Box 5: "If not submitted by 10th $\rightarrow$ Auto-lock submission; Mark as 'Not Submitted'; Record reason; Visible to HR." | **CLARIFICATION** | Reaffirms auto-lockout; explicitly mandates status label **"Not Submitted"**, mandatory reason capture, and administrative visibility to HR. |
| **8. Monthly Report Generation (Automatic)** | `REQ-MOD3-05`, `BP-M3-GD-005`, `BR-M3-005`. Enclosure 2 format. | Box 6: System collates all approved monthly forms; generates Monthly Performance Report (pre-defined template). | **ALREADY COVERED** | Baseline aligns 100%. |
| **9. Annual Report Generation (Automatic)** | `REQ-MOD3-06`, `BP-M3-GD-006`, `BR-M3-006`. Triggered at 1-year DOJ. | Box 7: Triggered on completion of 1 year (and every year); collates all monthly reports; computes weighted average (as per HR/Management); Management Review. | **ALREADY COVERED** | Baseline aligns 100%. Reaffirms that weighting formula is governed by HR/Management policy (`REQ-TBD-09`). |
| **10. Mandatory Probation Verification Gate** | `REQ-MOD3-07`, `BP-M3-GD-007`, `BR-M3-007`. Probation must be cleared. | Box 8: Check probation status (must be completed); blocks increment if uncompleted. | **ALREADY COVERED** | Baseline aligns 100%. |
| **11. Predefined Compensation Slabs & Decision** | `REQ-MOD3-08`, `BP-M3-GD-008`, `BR-M3-008`, `REQ-TBD-05`. Predefined slabs. | Box 8: Apply predefined compensation slabs; Management decision on compensation change. | **ALREADY COVERED** | Baseline aligns 100%. Monetary rupee slabs remain institutional TBD (`REQ-TBD-05`). |

---

## 6. Track B: General Employees (Non-Faculty) KRA/KPI Delta Analysis

### A. Subsystem Narrative & Flow
Track B governs the goal-setting, quarterly evaluation, and annual appraisal lifecycle for university non-teaching officers, administrative executives, and technical staff. The diagram confirms the strict 30-day onboarding window, 4 quarterly review cycles, 3-tier review chain, and direct Module I service change integration.

```
 [1. Employee Joins] ──► (Notify within 30d of DOJ) ──► [2. Set KRAs & KPIs] (Submit within 30d)
                                                                 │
                                                                 ▼
                                                 [3. HR & Management Verification]
                                                 - HR verifies, Management verifies
                                                 - Once verified, goals are locked
                                                                 │
                                                                 ▼
 ┌───────────────────────────────────────────────────────────────┴────────────────────────────────┐
 │                     [4. QUARTERLY REVIEW CYCLE (Q1, Q2, Q3, Q4)]                               │
 │                                                                                                │
 │   Q1 (90 Days)        Q2 (180 Days)       Q3 (270 Days)       Q4 (360 Days)                    │
 │  Employee submits    Employee submits    Employee submits    Employee submits                  │
 │  review + evidence   review + evidence   review + evidence   review + evidence                 │
 │  (within 15 days)    (within 15 days)    (within 15 days)    (within 15 days)                  │
 │                                                                                                │
 │            [Notification Banner: Automatic reminder after 20 days if pending]                  │
 │                                               │                                                │
 │                                               ▼                                                │
 │                           [Sub-Step 4a: Reporting Authority Verification]                      │
 │                           - Verify submission and forward to HR (within 7 days)                │
 │                                               │                                                │
 │                                               ▼                                                │
 │                           [Sub-Step 4b: HR Review]                                             │
 │                           - Record change request / recommendation / observation               │
 │                                               │                                                │
 │                                               ▼                                                │
 │                           [Sub-Step 4c: Management Review]                                     │
 │                           - Record comment or recommendation                                   │
 └───────────────────────────────────────────────┬────────────────────────────────────────────────┘
                                                 │
                                                 ▼
                                     [5. Annual Appraisal]
                                     - Triggered after Q4 completion
                                     - HR generates Annual Appraisal
                                     - Management records final recommendation
                                                 │
                                                 ▼
                               [6. HR Change Integration (Module I)]
                               - IF approved (increment / designation change / level change)
                               - HR initializes change requirement in Module I
                               - Links appraisal outcome to employee record
```

### B. Detailed Element-by-Element Comparison

| Diagram Element / Stage | Existing Baseline Representation | New Stakeholder Diagram Representation | Classification | Analysis & Impact |
|---|---|---|---|---|
| **1. Employee Joins & Notification** | `REQ-MOD3-09`, `BP-M3-KRA-001`. System tracks DOJ. | Box 1: System notifies employee and reporting authority to set KRAs and KPIs (within 30 days of Date of Joining). | **ALREADY COVERED** | Baseline aligns 100%. |
| **2. Set KRAs & KPIs (30-Day Window)** | `REQ-MOD3-09`, `BP-M3-KRA-001`. Goals set in 30 days. | Box 2: Employee / Reporting Authority enters KRAs and KPIs; submission within 30 days of joining. | **ALREADY COVERED** | Baseline aligns 100%. |
| **3. Joint HR & Management Verification (Goal Lock)** | `REQ-MOD3-09`, `BP-M3-KRA-001`, `BR-M3-010`. Joint approval locks goals. | Box 3: HR verifies and Management verifies; once verified, goals are locked. | **ALREADY COVERED** | Baseline aligns 100%. Confirms mandatory dual-sign-off before goal lock. |
| **4. Quarterly Cadence (Q1 to Q4 Windows)** | `REQ-MOD3-10`, `BP-M3-KRA-002`, `BR-M3-011`. Q1 (90d), Q2 (180d), Q3 (270d), Q4 (360d). | Box 4: Q1 (90 days), Q2 (180 days), Q3 (270 days), Q4 (360 days); employee submits review + supporting docs within 15 days. | **ALREADY COVERED** | Baseline aligns 100%. Confirms 15-day employee submission window for every quarter. |
| **5. Quarterly Reminder Timing** | `REQ-MOD3-10` stated "20-day reminder window" before quarter end. | Box 4 banner: "Automatic reminder after 20 days if pending". | **CLARIFICATION** | Clarifies the automated reminder mechanism: dispatches if review remains pending after 20 days. |
| **6. Reporting Authority 7-Day Verification** | `REQ-MOD3-11`, `BP-M3-KRA-003`, `BR-M3-011`. 7-day verification window. | Box 4 sub-step: Reporting Authority verifies submission and forwards to HR (within 7 days). | **ALREADY COVERED** | Baseline aligns 100%. |
| **7. Sequential HR Review & Management Review** | `REQ-MOD3-11`, `REQ-MOD3-12`, `BP-M3-KRA-004`, `BR-M3-012`. HR observations and Management review. | Box 4 sub-steps: HR Review (record change request/recommendation/observation) $\rightarrow$ Management Review (record comment or recommendation). | **ALREADY COVERED** | Baseline aligns 100%. Confirms the sequential post-supervisor review chain. |
| **8. Annual Appraisal Trigger (Post-Q4)** | `REQ-MOD3-13`, `BP-M3-KRA-005`. Triggered post-Q4. | Box 5: Triggered after Q4 completion; HR generates Annual Appraisal; Management records final recommendation. | **ALREADY COVERED** | Baseline aligns 100%. |
| **9. Direct Handshake to Module I** | `REQ-INT-04`, `SHR-INT-REQ-04`, `BP-XMOD-004`, `BR-M3-013`. Direct service change injection. | Box 6: "HR Change Integration (Module I) — IF approved (increment / designation change / level change) $\rightarrow$ HR initializes change requirement in Module I; links appraisal outcome to employee record." | **ALREADY COVERED** | Baseline aligns 100%. Reaffirms that approved appraisal increments directly initiate Module I service change requests. |

---

## 7. Track C: Faculty Members — ECM Based Annual Performance Appraisal Delta Analysis

### A. Subsystem Narrative & Flow
Track C governs statutory faculty appraisals evaluated through the university's Executive Committee Meeting (ECM). The diagram confirms the dual eligibility criteria, monthly 10th batch scan, Registrar routing, 7-working-day submission window, 4-unit parallel verification with discrepancy loop, ECM scoring under TNU Protocol, and Management decision, while introducing a comprehensive taxonomy of **seven potential appraisal outcomes**.

```
 [1. Eligibility Check] 
   - Probation period completed = TRUE
   - At least 12 months since last appraisal (DOJ & previous appraisal)
                 │
                 ▼
 [2. Generate Eligible Faculty List]
   - System generates list and routes to Office of the Registrar by 10th of every month
   - Automated reminder if delayed
                 │
                 ▼
 [3. Self-Appraisal Submission]
   - Faculty completes self-appraisal form + supporting docs
   - Submit within 7 working days (automated reminders)
                 │
                 ▼
 [4. Verification of Documents]
   - Routed in parallel to: School Dean, R&D Cell, Placement Cell, HR Department & other stakeholders
                 │
                 ├───────────────────────────────┐
                 ▼ (Discrepancy Found: YES)      ▼ (Discrepancy Found: NO)
   [Return to Faculty for correction]            [5. Evaluation Committee Meeting (ECM)]
   - Updated resubmission                        - Office of Registrar schedules monthly ECM
                 │                               - Notify faculty member of schedule
                 └───────────────────────────────►
                                                 │
                                                 ▼
                               [6. ECM Evaluation & Score Sheet]
                               - Committee records scores (digital score sheet)
                               - Submitted to HR
                                                 │
                                                 ▼
                               [7. Compile Evaluation Matrix]
                               - System compiles matrix using TNU Protocol parameters
                                 and previous increment details
                                                 │
                                                 ▼
                               [8. Management Decision]
                               - Review evaluation matrix and compensation recommendation
                                                 │
                                                 ▼
                               [9. Outcome & Implementation]
                               - Record recommendation (compensation change, etc.)
                               - Track implementation in next applicable salary cycle
                               - Generate and route letter to HR/Payroll
                                                 │
                                                 ▼
                              [10. Comprehensive Other Outcomes Taxonomy]
                              - Confirmation of employment
                              - Extension of probation (if minimum score not achieved)
                              - Rewards & recognition
                              - Compensation revision
                              - Additional responsibilities
                              - Performance Improvement Plan (PIP)
                              - Reprimand
```

### B. Detailed Element-by-Element Comparison

| Diagram Element / Stage | Existing Baseline Representation | New Stakeholder Diagram Representation | Classification | Analysis & Impact |
|---|---|---|---|---|
| **1. Dual Eligibility Check** | `REQ-MOD3-14`, `BP-M3-FAC-001`, `BR-M3-014`. Probation completed AND $\ge$ 12 months. | Box 1: Probation period completed; At least 12 months since last appraisal (based on Date of Joining & previous appraisal). | **ALREADY COVERED** | Baseline aligns 100%. Reaffirms the dual statutory eligibility condition. |
| **2. Monthly 10th Scan & Registrar Routing** | `REQ-MOD3-15`, `BP-M3-FAC-002`, `BR-M3-015`. Batch scan on 10th. | Box 2: System generates list and routes to Office of the Registrar by **10th of every month**; automated reminder if delayed. | **ALREADY COVERED** | Baseline aligns 100%. |
| **3. Self-Appraisal Submission (7 Working Days)** | `REQ-MOD3-16`, `BP-M3-FAC-003`, `BR-M3-016`. 7 working days submission window. | Box 3: Faculty completes self-appraisal form + supporting docs; submit within 7 working days; automated reminders. | **ALREADY COVERED** | Baseline aligns 100%. |
| **4. Multi-Unit Parallel Verification** | `REQ-MOD3-17`, `BP-M3-FAC-004`, `BR-M3-017`. Dean, R&D Cell, Placement Cell, HR Dept. | Box 4: Route to School Dean, R&D Cell, Placement Cell, HR Department **"and other stakeholders"**. | **CLARIFICATION / EXTENSION** | Reaffirms 4 primary verifying bodies; adds phrase "and other stakeholders" allowing future institutional verification units (e.g. IQAC). |
| **5. Discrepancy & Resubmission Loop** | `REQ-MOD3-17`, `BP-M3-FAC-005`, `BR-M3-018`. Circular correction loop. | Box 4 Decision Diamond: "Discrepancy found? $\rightarrow$ Yes: Return to Faculty for correction / updated submission; No: Moves to Step 5." | **ALREADY COVERED** | Baseline aligns 100%. Visualises the circular discrepancy and resubmission loop. |
| **6. Monthly ECM Scheduling by Registrar** | `REQ-MOD3-18`, `BP-M3-FAC-006`. Monthly ECM session. | Box 5: **Office of the Registrar schedules monthly ECM**; notify faculty member of schedule. | **CLARIFICATION** | Explicitly assigns responsibility for scheduling monthly ECM sessions and issuing schedule notices to the **Office of the Registrar**. |
| **7. ECM Digital Score Sheet** | `REQ-MOD3-18`, `BP-M3-FAC-006`. Digital score sheet (Enclosure 2). | Box 6: Evaluation Committee records scores (digital ECM score sheet); score sheet submitted to HR. | **ALREADY COVERED** | Baseline aligns 100%. |
| **8. TNU Protocol Matrix & Previous Increments** | `REQ-MOD3-19`, `BP-M3-FAC-007`, `BR-M3-020`. TNU Protocol matrix (Enclosure 3). | Box 7: System compiles evaluation matrix using TNU Protocol parameters **and previous increment details**. | **CLARIFICATION** | Clarifies that the compiled matrix incorporates historical compensation and previous increment details alongside TNU Protocol scores. |
| **9. Management Decision & Next Salary Cycle** | `REQ-MOD3-20`, `BP-M3-FAC-007`, `BP-M3-FAC-008`, `BR-M3-021`. Management decision in next cycle. | Box 8 & 9: Management reviews matrix; records recommendation; tracks implementation in next applicable salary cycle; generates and routes letter to HR/Payroll. | **ALREADY COVERED** | Baseline aligns 100%. |
| **10. Comprehensive Other Outcomes Taxonomy** | Baseline focused primarily on merit increment, promotion, and salary revision. | Box 10: Explicitly lists 7 distinct institutional outcomes: (1) Confirmation of employment, (2) Extension of probation (if minimum score not achieved), (3) Rewards & recognition, (4) Compensation revision, (5) Additional responsibilities, (6) Performance Improvement Plan (PIP), (7) Reprimand. | **NEW EXPLICIT REQUIREMENT / TBD** | **MAJOR GOVERNANCE EXTENSION.** Broadens ECM outcomes to include corrective/punitive actions (PIP, Reprimand, Probation Extension). Specific policy rules and score thresholds remain `[E] TBD`. |

---

## 8. Shared Integration Delta Analysis (Sections D, E, F, G)

The diagram establishes four shared integration layers that span all three performance tracks:

### A. Section D: Employee File Integration
- **Diagram Text:** *"All evaluation forms, monthly reports, annual reports stored in employee's digital file; Available for HR decisions with linked records."*
- **Existing Baseline:** Aligns with `BP-M1-003` (Digital Employee Dossier), `BP-M3-GD-008`, and `BP-M3-FAC-009` (Archival in Digital Personal File).
- **Classification:** **ALREADY COVERED / CLARIFICATION**. Confirms that every performance record (Group-D monthly forms, Staff quarterly reviews, Faculty ECM scorecards, letters) is automatically linked to the employee's master digital dossier in Module I.

### B. Section E: Audit Trail & Version History
- **Diagram Text:** *"All evaluation, approval and report status time-stamped; Complete audit trail and version history; Database change methodology consistent with Module I."*
- **Existing Baseline:** Aligns with `REQ-AUD-01` to `04`, `BP-M1-008`, and `BR-ENT-004`.
- **Classification:** **ALREADY COVERED**. Confirms that Module III adheres strictly to the same immutable audit logging and versioning standards established in Module I.

### C. Section F: Reporting (Configurable)
- **Diagram Text:** *"Monthly Performance Report (Group-D); Annual Report (Group-D); Quarter-wise and Annual Reports (General Employees); ECM related reports (Faculty); Real-time reporting (add/delete reports as needed)."*
- **Existing Baseline:** Aligns with `REQ-REP-01` to `09` and `BP-M1-010`.
- **Classification:** **ALREADY COVERED**. Confirms the reporting scope across all three tracks and reiterates the requirement for configurable, real-time reporting.

### D. Section G: Central Employee Database & HR Integration
- **Diagram Text:** *"Employee data (DOJ, department, reporting hierarchy, probation status, etc.); Organization structure consistency; Approved changes integrated with Module I."*
- **Existing Baseline:** Aligns with Cross-Module Handshakes `BP-XMOD-003` (Master Data Feed), `BP-XMOD-004` (Appraisal Outcomes to Change Request), and `BP-XMOD-005` (Org Hierarchy Updates).
- **Classification:** **ALREADY COVERED**. Reaffirms the bidirectional master data and service change relationship between Module I and Module III.

---

## 9. Cross-Module Impact Analysis

The new Module III diagram strongly corroborates the cross-module business relationships defined in [`docs/02-business-process/05-CROSS-MODULE-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/05-CROSS-MODULE-BUSINESS-PROCESSES.md):

```
                      ┌────────────────────────────────────────────────────────┐
                      │          MODULE I: CENTRAL EMPLOYEE DATABASE           │
                      │  - Employee Master Attributes: DOJ, Department,        │
                      │    Designation, Band/Level, Probation Clearance        │
                      │  - Reporting Hierarchy & Org Chart Nodes               │
                      └──────────────────────────┬─────────────────────────────┘
                                                 │
                     Handshake BP-XMOD-003       │ Handshake BP-XMOD-005
                     Master Data Feed            │ Org Realignment & Transfer
                                                 ▼
                      ┌────────────────────────────────────────────────────────┐
                      │          MODULE III: PERFORMANCE AUTOMATION            │
                      │  Track A (Group-D): 1st Dispatch, 1-Yr DOJ Review      │
                      │  Track B (Staff): 30d Goal Timer, Q1–Q4 Reviews        │
                      │  Track C (Faculty): Monthly 10th Dual Eligibility Scan │
                      └──────────────────────────┬─────────────────────────────┘
                                                 │
                                                 │ Handshake BP-XMOD-004
                                                 │ Appraisal Outcomes
                                                 ▼
                      ┌────────────────────────────────────────────────────────┐
                      │          MODULE I: SERVICE CHANGE REQUEST              │
                      │  - Change Format 1: Salary Revision / Increment        │
                      │  - Change Format 2: Designation Change / Merit Title   │
                      │  - Change Format 5: Level / Band Promotion             │
                      │  - Mandatory Level-1 HR & Level-2 Mgmt Governance      │
                      └────────────────────────────────────────────────────────┘
```

1. **Module I $\rightarrow$ Module III (`BP-XMOD-003`):** Box G and Track C Box 1 explicitly confirm that employee Date of Joining (DOJ), department allocation, reporting supervisor hierarchy, and probation clearance status originate exclusively from Module I Central Database to drive Group-D scheduling, Staff 30-day goal timers, and Faculty monthly 10th eligibility queries.
2. **Module III $\rightarrow$ Module I (`BP-XMOD-004`):** Track B Box 6, Track C Box 9, and Track A Box 8 explicitly confirm that approved annual appraisal outcomes (increments, designation promotions, level changes) directly initialize Module I service change requests, subjecting them to official governance before effective-date activation and payroll synchronization.
3. **Hierarchy Changes $\rightarrow$ Performance Routing (`BP-XMOD-005`):** Box G reinforces that organization structure consistency is maintained dynamically, ensuring that supervisor transfers in Module I automatically realign active evaluation inboxes across all three subsystems.

---

## 10. Potential Conflicts & Divergences Requiring Confirmation

The analysis identified **four specific areas of divergence, role refinement, or timing nuance** requiring formal stakeholder clarification:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        AREAS REQUIRING STAKEHOLDER CONFIRMATION                         │
├──────────────────────┬──────────────────────────┬──────────────────────────────────────┤
│ Operational Topic    │ Earlier Baseline         │ New Stakeholder Diagram              │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 1. Group-D Monthly   │ Assigned to "Reporting   │ Explicitly routes to "HOD" who       │
│    Evaluating Actor  │ Supervisor / Evaluator"  │ "Completes & Submits" online (Box 2) │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 2. General Staff     │ 20-day reminder before   │ Notification banner reads:           │
│    Reminder Timing   │ quarter close            │ "Automatic reminder after 20 days    │
│                      │                          │ if pending" (Box 4)                  │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 3. Faculty Document  │ 4 specific units: Dean,  │ Routes to Dean, R&D, Placement, HR   │
│    Verifiers         │ R&D, Placement, HR       │ "and other stakeholders" (Box 4)     │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 4. Faculty Appraisal │ Focused on increment,    │ Explicitly adds PIP, Reprimand,      │
│    Outcomes Scope    │ promotion, salary cycle  │ Probation Extension, Confirmation    │
└──────────────────────┴──────────────────────────┴──────────────────────────────────────┘
```

### Detailed Conflict Analysis

#### Conflict 1: Group-D Evaluating Actor (HOD vs. Supervisor)
- **Earlier Baseline:** `BP-M3-GD-002` described the evaluating actor as "Reporting Supervisor" / "Evaluating Supervisor", acknowledging that operational staff (sweepers, peons, drivers) report to immediate supervisors or foremen.
- **New Stakeholder Diagram:** Box 2 and Box 3 explicitly state: *"System routes monthly form to HOD (based on department / reporting hierarchy)"* and *"HOD Completes & Submits"*.
- **Analysis:** In large university departments, routing all Group-D forms directly to the HOD for online completion may create administrative bottlenecks if the HOD does not directly oversee daily operational shifts.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Clarify whether the HOD personally completes the online evaluation form, or whether the immediate supervisor completes the draft and the HOD endorses/submits it to VP-Administration.

#### Conflict 2: Staff Quarterly Review Reminder Timing
- **Earlier Baseline:** In Module III PDF Stage 2 and `REQ-MOD3-10`, the timing was specified as: *"90-day intimation, 20-day reminder window, 15-day submission window"*. This meant a reminder was sent 20 days prior to the quarter close (Day 70).
- **New Stakeholder Diagram:** The visual banner in Box 4 states: *"Automatic reminder after 20 days if pending"*.
- **Analysis:** Since the employee submission window is 15 days, sending a reminder "after 20 days if pending" would mean the reminder is sent *after* the deadline has already expired (Day 20 of a 15-day window), representing an overdue escalation rather than a pre-deadline reminder. Alternatively, it could mean 20 days into the quarter.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Clarify whether the 20-day reminder fires: (a) 20 days before the quarter end, (b) on Day 20 after quarter opening, or (c) as an overdue reminder 5 days after the 15-day submission window closes.

#### Conflict 3: Verification Units Scope ("and other stakeholders")
- **Earlier Baseline:** Module III PDF and `REQ-MOD3-17` strictly designated four parallel verifying units: School Dean, R&D Cell, Placement Cell, and HR Department.
- **New Stakeholder Diagram:** Box 4 states: *"Route to School Dean, R&D Cell, Placement Cell, HR Department and other stakeholders"*.
- **Analysis:** This open-ended wording suggests that the university may wish to include additional institutional verification units (such as IQAC for academic quality, Examination Cell for results processing, or Finance for fee clearance) for specific faculty categories.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Confirm whether the four verifying units are permanently fixed, or whether "other stakeholders" indicates an institutional requirement for configurable verification routing per faculty cadre.

#### Conflict 4: Expanded Faculty Appraisal Outcomes Scope
- **Earlier Baseline:** The official PDF focused almost exclusively on merit salary increments and promotions implemented through the next monthly salary cycle.
- **New Stakeholder Diagram:** Box 10 introduces a comprehensive taxonomy of **seven potential outcomes**: (1) Confirmation of employment, (2) Extension of probation, (3) Rewards & recognition, (4) Compensation revision, (5) Additional responsibilities, (6) Performance Improvement Plan (PIP), and (7) Reprimand.
- **Analysis:** This transforms Module III from a pure reward/increment system into a complete performance governance framework encompassing corrective, disciplinary, and probationary actions.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Confirm the inclusion of PIP, Reprimand, and Probation Extension as formal system-supported ECM outcomes, and solicit university policy thresholds governing their application.

---

## 11. New & Clarified Open Decisions (TBD)

In strict accordance with the project's anti-invention mandate, operational parameters, scoring thresholds, and disciplinary rules shown on the diagram but lacking concrete business rules are catalogued as open decisions:

| TBD Register ID | Domain | Topic & Stakeholder Statement | Status & Scope |
|---|---|---|---|
| **`REQ-TBD-17`** | Module III (Faculty) | **Performance Improvement Plan (PIP) Workflow & Criteria:** Diagram Box 10 lists "Performance Improvement Plan" as an ECM outcome. | **`[E] TBD`** — University policy must define PIP duration, review milestones, assigned mentor roles, and exit/termination consequences. |
| **`REQ-TBD-18`** | Module III (Faculty) | **Formal Reprimand Policy & Governance Impact:** Diagram Box 10 lists "Reprimand" as an ECM outcome. | **`[E] TBD`** — Institutional rules governing the issuance of reprimand letters, service record flags, and increment bar periods. |
| **`REQ-TBD-19`** | Module III (Faculty) | **Probation Extension Score Thresholds & Max Duration:** Diagram Box 10 lists "Extension of probation (if minimum score not achieved)". | **`[E] TBD`** — Minimum TNU Protocol score cutoff required for employment confirmation, maximum permissible probation extension duration, and re-evaluation timeline. |
| **`REQ-TBD-20`** | Module III (Group-D) | **"Not Submitted" Reason Taxonomy & Administrative Re-open Authority:** Diagram Box 5 mandates recording reason when auto-locked after 10th. | **`[E] TBD`** — Standardized reason codes for overdue Group-D submissions and formal procedure for administrative unlock by VP-Administration. |

---

## 12. Impact Matrix: Comprehensive Module III Delta Catalogue

The following consolidated matrix details all 15 material items identified from the new Module III stakeholder diagram:

| Delta ID | Subsystem | Stakeholder Diagram Element | Existing Baseline Status | Analytical Classification | Requirement Class | Impact Level | Affected Baseline Documents | Recommended Governance Action | TBD / Confirmation Required? |
|---|---|---|---|---|---|---|---|---|---|
| **`DLT-M3-01`** | Group-D | Box 1: Evaluation Form Repository | `MOD3-GD-REQ-01` cited Enclosure 1 | **CLARIFICATION** | `[A]` Explicit | **LOW** | `03-MODULE-III-FUNCTIONAL-REQS.md`, `04-MODULE-III-BUSINESS-PROCESSES.md` | Document role-specific KPI configuration in Form Repository. | No |
| **`DLT-M3-02`** | Group-D | Box 2 & 3: Monthly Routing to HOD | `BP-M3-GD-002` cited "Reporting Supervisor" | **POTENTIAL CONFLICT** | `[A]` Explicit | **MEDIUM** | `04-MODULE-III-BUSINESS-PROCESSES.md` (`BP-M3-GD-002`) | Seek confirmation on HOD vs. immediate supervisor evaluation role. | **Needs Confirmation** |
| **`DLT-M3-03`** | Group-D | Box 4: VP-Administration Approval | Covered in `REQ-MOD3-04`, `BP-M3-GD-004` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-04`** | Group-D | Box 5: Submission Timeline (7th Due, 10th Lock) | Covered in `REQ-MOD3-01`–`03`, `BP-M3-GD-002`–`003` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-05`** | Group-D | Box 5: "Not Submitted" Status & Reason | Baseline locked form without explicit reason field | **CLARIFICATION** | `[A]` Explicit | **LOW** | `03-MODULE-III-FUNCTIONAL-REQS.md`, `04-MODULE-III-BUSINESS-PROCESSES.md` | Formalize "Not Submitted" status and register `REQ-TBD-20`. | **YES (`REQ-TBD-20`)** |
| **`DLT-M3-06`** | Group-D | Box 7: Annual Report at 1-Year DOJ | Covered in `REQ-MOD3-06`, `BP-M3-GD-006` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-07`** | Group-D | Box 8: Predefined Slabs & Probation Gate | Covered in `REQ-MOD3-07`–`08`, `BP-M3-GD-007`–`008` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-08`** | Staff KRA | Box 1–3: 30-Day Setup & Joint Verification | Covered in `REQ-MOD3-09`, `BP-M3-KRA-001` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-09`** | Staff KRA | Box 4: Quarterly Review Windows & Reviews | Covered in `REQ-MOD3-10`–`12`, `BP-M3-KRA-002`–`004` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-10`** | Staff KRA | Box 4: "Automatic reminder after 20 days" | Baseline stated 20-day reminder before end | **CLARIFICATION** | `[A]` Explicit | **LOW** | `04-MODULE-III-BUSINESS-PROCESSES.md` (`BP-M3-KRA-002`) | Clarify whether reminder is pre-deadline or post-deadline. | **Needs Confirmation** |
| **`DLT-M3-11`** | Staff KRA | Box 6: Direct Module I Integration | Covered in `REQ-INT-04`, `BP-XMOD-004` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-12`** | Faculty | Box 1–3: Dual Eligibility & 7-Day Submission | Covered in `REQ-MOD3-14`–`16`, `BP-M3-FAC-001`–`003` | **ALREADY COVERED** | `[A]` Explicit | **NONE** | None | Reaffirms baseline design. | No |
| **`DLT-M3-13`** | Faculty | Box 4: Verification "and other stakeholders" | Baseline cited 4 specific units | **CLARIFICATION** | `[B]` Implication | **LOW** | `04-MODULE-III-BUSINESS-PROCESSES.md` (`BP-M3-FAC-004`) | Seek confirmation on potential additional verification units. | **Needs Confirmation** |
| **`DLT-M3-14`** | Faculty | Box 5 & 7: Registrar ECM Scheduling & Previous Increments | Matrix compiled per TNU Protocol | **CLARIFICATION** | `[A]` Explicit | **MEDIUM** | `04-MODULE-III-BUSINESS-PROCESSES.md` (`BP-M3-FAC-006`, `007`) | Document Registrar ECM scheduling role and inclusion of previous increments in matrix. | No |
| **`DLT-M3-15`** | Faculty | Box 10: Expanded Outcomes Taxonomy (PIP, Reprimand, Probation Ext, Rewards) | Baseline focused on increments/promotions | **NEW EXPLICIT REQUIREMENT** | `[A]` Explicit | **HIGH** | `02-REQUIREMENT-CATALOGUE.md`, `04-MODULE-III-BUSINESS-PROCESSES.md`, `03-MODULE-III-FUNCTIONAL-REQS.md` | Formalize 7 outcome types; register `REQ-TBD-17`, `18`, `19` for policy rules. | **YES (`REQ-TBD-17`–`19`)** |

---

## 13. Document Impact Analysis

The following table assesses the extent of impact across all system documentation layers:

| Documentation Layer / File Group | Impact Assessment | Summary of Direct / Indirect Implications |
|---|---|---|
| **`docs/01-requirements/`** (Phase 1 Baseline) | **DIRECT IMPACT** | - `01-PROJECT-REQUIREMENTS-SPECIFICATION.md`: Add comprehensive 7-outcome taxonomy for Faculty ECM.<br>- `02-REQUIREMENT-CATALOGUE.md`: Formulate candidate requirement IDs for new ECM outcomes, HOD evaluation routing, and Registrar ECM scheduling.<br>- `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`: Add 4 new TBD items (`REQ-TBD-17` to `REQ-TBD-20`).<br>- `06-REQUIREMENTS-QUALITY-REVIEW.md`: Reconcile requirement counts upon baseline update. |
| **`docs/02-business-process/`** (Phase 2 Baseline) | **DIRECT IMPACT** | - `04-MODULE-III-BUSINESS-PROCESSES.md`: Refine `BP-M3-GD-002` (HOD role), `BP-M3-GD-003` ("Not Submitted" status), `BP-M3-FAC-006` (Registrar scheduling), `BP-M3-FAC-007` (previous increment data), and `BP-M3-FAC-008` (7-outcome execution).<br>- `06-BUSINESS-RULES-AND-DECISION-POINTS.md`: Add business rules for ECM outcomes and HOD routing.<br>- `07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md`: Add SLA rules for Registrar ECM scheduling and reminder timing. |
| **`docs/03-functional-requirements/`** (Phase 3 Baseline) | **DIRECT IMPACT** | - `03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`: Add functional specifications for PIP tracking (`MOD3-PIP-REQ-*`), reprimand logging (`MOD3-REP-REQ-*`), probation extension workflows, and HOD Group-D review interfaces. |
| **`TECHNOLOGY_ARCHITECTURE_BASELINE.md`** & **ADRs** | **INDIRECT IMPACT** | - Performance review state machines must accommodate new terminal/sub-terminal outcome states: `PIP_ASSIGNED`, `PROBATION_EXTENDED`, `REPRIMANDED`, `CONFIRMED`. Core technical architecture (PostgreSQL, NestJS, Next.js) remains completely unaffected. |
| **Future Workflows (`docs/06-workflows/`)** | **DIRECT IMPACT** | Future Phase 6 workflow documentation will directly model the refined 8-step Group-D flow, 6-step Staff KRA flow, and 10-step Faculty ECM flow with expanded outcome branches. |

---

## 14. Traceability Impact & Candidate Requirement Identifiers

To preserve rigorous traceability without prematurely mutating the approved 104-requirement catalogue, the new items are provisionally assigned **Candidate Traceability Identifiers**:

| Candidate Requirement ID | Descriptive Title | Mapped Business Process Target | Mapped Functional Requirement Target | Classification |
|---|---|---|---|---|
| `CAND-REQ-M3-OUTCOMES` | Comprehensive ECM Appraisal Outcomes Taxonomy (PIP, Reprimand, Probation Extension, Confirmation, Rewards) | `BP-M3-FAC-008`, `BP-M3-FAC-009` | `MOD3-FAC-REQ-09` (New) | `[A]` Explicit Requirement |
| `CAND-REQ-M3-HODROUTING`| Group-D Monthly Online Evaluation Routing to HOD with "Not Submitted" Tracking | `BP-M3-GD-002`, `BP-M3-GD-003` | `MOD3-GD-REQ-09` (New) | `[A]` Explicit (Pending Confirmation) |
| `CAND-REQ-M3-REGSCHED` | Office of the Registrar Monthly ECM Scheduling & Faculty Notification | `BP-M3-FAC-006` | `MOD3-FAC-REQ-10` (New) | `[A]` Explicit Requirement |
| `CAND-REQ-M3-MATRPREV` | Evaluation Matrix Compilation Incorporating TNU Protocol & Previous Increment Records | `BP-M3-FAC-007` | `MOD3-FAC-REQ-07` (Refined) | `[A]` Explicit Requirement |

---

## 15. Evaluation of Baseline Counts

The Phase 2 Completion Report stated:
1. *104 atomic requirements fully mapped.*
2. *59 business processes complete.*
3. *0 unmapped requirements & 0 inconsistencies.*

### Critical Assessment:
- **Does the 104-Requirement Baseline Remain Valid?**  
  The 104 atomic requirements established in Phase 1 (`docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`) were complete and accurate with respect to the original PDFs. However, with the release of the new Module III workflow diagram (coupled with the earlier Module I and Module II materials), **the claim that "104 requirements represent 100% of all stakeholder requirements" is now OUTDATED**. New explicit requirements (such as the comprehensive ECM 7-outcome taxonomy, Registrar ECM scheduling, and HOD Group-D routing) represent formal candidate additions to the requirements baseline.
- **Does the 59-Business Process Baseline Remain Valid?**  
  The 59 business processes documented in `docs/02-business-process/` remain **structurally sound as the macro operational framework**. Module III's 22 business processes (`BP-M3-GD-001`–`008`, `BP-M3-KRA-001`–`005`, `BP-M3-FAC-001`–`009`) map perfectly to Tracks A, B, and C of the new diagram. However, the claim that the business processes represent the final operational detail is now **SUBJECT TO PLANNED REVISION**, as internal activities within `BP-M3-GD-002`, `BP-M3-FAC-006`, and `BP-M3-FAC-008` require step and outcome expansions.
- **Inconsistencies:** The earlier baseline had zero internal contradictions against the original PDF. The new diagram introduces **four operational nuances** (HOD evaluating actor role, reminder timing wording, verification units scope, and expanded outcome taxonomy) that require formal stakeholder confirmation.

---

## 16. Recommended Controlled Change Sequence

To maintain enterprise document integrity and prevent unauthorized baseline drift across all three modules, the following unified change sequence is recommended:

```
 [1. ALL STAKEHOLDER MATERIALS RECEIVED] (Module I, II & III Narratives & Diagrams)
                 │
                 ▼
 [2. COMBINED DELTA & IMPACT ANALYSIS COMPLETED] (Documents 07 and 08 in docs/01-requirements/)
                 │
                 ▼
 [3. STAKEHOLDER REVIEW & CONFIRMATION] (Resolve All Potential Conflicts & TBDs across Mod I, II, III)
                 │
                 ▼
 [4. COMPREHENSIVE REQUIREMENT BASELINE UPDATE] (docs/01-requirements/ - Update Catalogue & TBD Register)
                 │
                 ▼
 [5. AFFECTED BUSINESS PROCESS UPDATE] (docs/02-business-process/ - Refine Process Steps across Mod I, II, III)
                 │
                 ▼
 [6. AFFECTED FUNCTIONAL REQUIREMENT UPDATE] (docs/03-functional-requirements/ - Update FRDs)
                 │
                 ▼
 [7. QUALITY AUDIT & RE-RECONCILIATION] (Verify New Atomic Requirement & Process Counts)
                 │
                 ▼
 [8. BASELINE FREEZE]
                 │
                 ▼
 [9. PROCEED TO NEXT DOCUMENTATION PHASE] (Phase 4: Database Schema Documentation)
```

---

## 17. Items Requiring Stakeholder Confirmation

Before any baseline updates are executed, university leadership and mentors must formally confirm the following four Module III decisions:

1. **Confirmation Item 1 (Group-D Evaluating Role - HOD vs. Supervisor):**  
   Does the **HOD** directly complete and submit the online monthly evaluation form for Group-D employees, or does the employee's immediate operational supervisor (e.g. Foreman / Shift Supervisor) draft the ratings for HOD endorsement before transmission to VP-Administration?
2. **Confirmation Item 2 (Quarterly Review Reminder Timing):**  
   Does the automated reminder in the General Staff quarterly cycle fire: (a) 20 days *before* the quarter end (advance reminder), (b) 20 days *into* the 90-day quarter, or (c) 5 days *after* the 15-day submission window as an overdue reminder?
3. **Confirmation Item 3 (Faculty Verification Stakeholders Scope):**  
   Are the four verifying units for Faculty ECM (School Dean, R&D Cell, Placement Cell, HR Department) permanently fixed, or does the phrase "and other stakeholders" mandate system support for configurable additional verification units (e.g. IQAC, Finance, Examination Cell)?
4. **Confirmation Item 4 (Expanded ECM Outcomes Scope & Policies):**  
   Does the university officially confirm the inclusion of **Performance Improvement Plan (PIP)**, **Reprimand**, **Extension of Probation**, **Confirmation of Employment**, and **Rewards & Recognition** as formal system-supported ECM outcomes, and what are the institutional policy thresholds governing their application?

---

## 18. Final Delta Summary & Quantitative Findings

| Metric / Dimension | Quantitative Finding | Status / Classification |
|---|---|---|
| **Total Material Items Analyzed** | **15 distinct items** | Catalogued in Section 12 Impact Matrix |
| **Already Covered Items** | **9 items** | Baseline completely aligned |
| **New Explicit Requirements** | **1 item (7 outcome types)**| Candidate ID `CAND-REQ-M3-OUTCOMES` provisionally assigned |
| **Clarifications** | **4 items** | Operational details refined |
| **Potential Conflicts** | **1 item** | HOD evaluating actor role (Awaiting confirmation) |
| **New Exceptions / Special Conditions** | **2 items** | "Not Submitted" auto-lockout flow + Discrepancy return flow |
| **New / Clarified TBD Items** | **4 items** | `REQ-TBD-17` through `REQ-TBD-20` |
| **Impact Level Breakdown** | **High: 1, Medium: 2, Low: 3, None: 9** | 15 total items evaluated |
| **Affected Existing Document Groups** | **4 document layers** | `01-reqs`, `02-business-process`, `03-functional-reqs`, architecture |
| **Current 104-Requirement Baseline Status** | **Historically valid for PDFs; requires planned expansion** | New candidate requirements identified |
| **Current 59-Business Process Baseline Status**| **Structurally sound foundation; requires internal step updates** | Macro processes preserved; steps refined |
| **File Safety & Integrity** | **Zero existing files modified** | Strictly analysis-only execution |

---
*End of Document — Module III Stakeholder Requirement Delta & Impact Analysis.*
