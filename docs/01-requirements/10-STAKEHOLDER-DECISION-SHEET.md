# STAKEHOLDER DECISION SHEET
## HR CHANGE MANAGEMENT & AUTOMATION SYSTEM

```
====================================================================================================
STATUS:
PENDING STAKEHOLDER CONFIRMATION

IMPORTANT GOVERNANCE NOTICE:
This document does not constitute stakeholder approval and does not modify the frozen project baseline.
All decisions documented herein remain open and pending formal confirmation by University Leadership
and Mentors. The baseline of 104 atomic requirements and 59 business processes remains strictly frozen.
====================================================================================================
```

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md` |
| **System Phase** | Phase 2 Post-Release / Stakeholder Review Preparation |
| **Project Name** | University HR Change Management & Automation System |
| **Document Purpose** | Controlled, Source-Grounded Stakeholder Decision Sheet for Formal Mentor Review |
| **Date of Preparation** | September 29, 2026 |
| **Authoritative Baselines** | `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md` (104 Frozen Requirements); `docs/02-business-process/` (59 Frozen Processes); `docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md` (Canonical Delta Review) |
| **Target Decision Authority** | Decision Authority: To be designated by University Leadership |

---

## 1. Purpose

This document provides a clean, structured, and strictly source-grounded **Stakeholder Decision Sheet** for the University HR Change Management & Automation System.

Following the completion of the baseline requirements (Phase 1), business processes (Phase 2), and functional specifications (Phase 3), new stakeholder narratives and visual complete workflows were submitted for Module I, Module II, and Module III. The subsequent canonical synthesis—documented in [`09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md)—identified **ten key governance decisions** (`CONF-01` through `CONF-10`) that involve policy choices, role assignments, workflow gates, or scope extensions.

The purpose of this decision sheet is to:
1. Present each unresolved governance item in clear, non-technical, university-relevant terms.
2. Ground every question strictly in the primary requirement briefs and new stakeholder materials.
3. Explicitly distinguish between documented source positions and proposed alternatives that require stakeholder clarification.
4. Eliminate all evaluative, subjective, or recommending language so that the stakeholder remains the sole decision-maker.
5. Provide a blank decision log and post-sign-off impact map to guide the formal review session without altering the frozen project baselines.

---

## 2. Stakeholder Review Instructions

To ensure a smooth, auditable review session, mentors and university stakeholders are requested to observe the following review protocols:

1. **Decision Authority:** Decision Authority: To be designated by University Leadership. Decisions should be confirmed by the authorized institutional authority.
2. **Reviewing Options vs. Alternatives:** For each decision card (`CONF-01` to `CONF-10`), review the documented options derived directly from official baselines or stakeholder workflows. Where operational ambiguities exist, proposed alternatives have been provided and explicitly labelled as requiring stakeholder clarification.
3. **Recording Decisions:** During the formal review session, record the confirmed option or directive in the [Stakeholder Decision Log](#5-stakeholder-decision-log) along with any clarifying comments, confirmation date, and confirming authority's name and title.
4. **Baseline Advance:** No changes will be applied to the system baselines during the discussion. Upon formal sign-off of this sheet, the engineering team will execute a single, controlled baseline update pass (Step 4 of the project sequence) to advance the requirement catalogue and update affected business processes.

---

## 3. Summary of CONF-01 to CONF-10

The following table summarizes all ten stakeholder confirmation decisions across the three functional modules, distinguishing documented source positions from proposed alternatives:

| ID | Module | Decision Topic | Current Documented Position | Stakeholder Question | Documented Options & Proposed Alternatives | Source Basis | Related DLT / Conflict | Decision Status |
|---|---|---|---|---|---|---|---|---|
| **`CONF-01`** | Mod I | Service Change Initiator Scope | Baseline restricted initiation strictly to HR Operations (`REQ-MOD1-05`). New diagram Box 2 states "HR / Admin / Dept as per policy". | Should initiation be restricted to HR Operations only, or also extended to designated Administrative Officers and Department Heads? | **Documented Options:**<br>• Opt A: HR Operations Only (Baseline `REQ-MOD1-05`)<br>• Opt B: HR + Admin + Dept Heads (Diagram Box 2)<br>*(Proposed Alternative: Employee Self-Service — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod I Brief Sec 1; Mod 1 Diagram Box 2 | `DLT-08`<br>Conflict: None | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-02`** | Mod II | Associate Dean Academic Planning Role | Baseline described manpower planning initiated broadly by HR/Deans. New narrative & diagram name Associate Dean (Academics). | Confirm whether Associate Dean (Academics) is the designated lead academic officer who initiates planning and co-consolidates requirements. | **Documented Options:**<br>• Opt A: Formally Introduce Associate Dean (Narrative Para 5 & Diagram Step 1)<br>• Opt B: Maintain Central HR / Registrar Baseline (`REQ-MOD2-02`) | Mod II Brief Sec 1; Mod 2 Narrative Para 5; Step 1 | `DLT-10` (`CAND-REQ-M2-AD`)<br>Conflict: None | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-03`** | Mod II | Academic Manpower Vetting Authority | Baseline assigned 3-month vetting to HR (`REQ-MOD2-05`). New material assigns Faculty/Lab Tech vetting to Associate Dean (Academics). | Does Associate Dean (Academics) vet academic requisitions in place of HR, or jointly / sequentially with the HR Department? | **Documented Options:**<br>• Opt A: Exclusive Associate Dean Vetting (Narrative Para 8 & Diagram Step 2)<br>• Opt B: Exclusive HR Vetting (Baseline `REQ-MOD2-05`)<br>*(Proposed Alternative: Two-Stage Joint Vetting — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod II Brief Sec 1(c); Mod 2 Narrative Para 8; Step 2 | `DLT-12`<br>Conflict: **`CFL-01`** | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-04`** | Mod II | Lab Technician Cadre Alignment | Baseline grouped Lab Technicians under Non-Academic staff (3-round interview). New material groups them with Faculty under Academic Track. | Are Lab Technicians officially governed under the Academic Track (SCM with external experts) or Non-Academic Track (3-round interviews)? | **Documented Options:**<br>• Opt A: Academic Track / SCM (Diagram Steps 1, 2, 6, 14A)<br>• Opt B: Non-Academic Track / 3 Rounds (Baseline `REQ-MOD2-01`)<br>*(Proposed Alternative: Specialized Technical Panel — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod II Brief Sec 1 & Selection A/B; Step 1, 2, 6, 14A | `DLT-11`<br>Conflict: **`CFL-02`** | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-05`** | Mod II | Management Pre-Approval for Interview | Baseline moved directly from recruiter shortlisting to interview. New diagram Step 13 introduces mandatory Management Approval for Interview. | Is executive Management approval mandatory for *all* candidates before interviews, or only for senior cadres, or remains delegated? | **Documented Options:**<br>• Opt A: Universal Mandatory Gate for All (Diagram Step 13)<br>• Opt B: Delegated Departmental Shortlisting (Baseline `BP-M2-ACAD-008`)<br>*(Proposed Alternative: Tiered Approval for Senior Only — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod II Brief Sec 3 & 7; Mod 2 Diagram Step 13; FRD Sec 19 | `DLT-19` (`CAND-REQ-M2-INTAPP`)<br>Conflict: **`CFL-03`** | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-06`** | Mod II | Post-SCM Formal HR Recommendation Review | Baseline routed SCM evaluation scorecards directly to Management. New diagram Step 14A adds formal HR recommendation review before Management. | Does the system enforce a formal HR recommendation review stage post-SCM before files route to Management for final cost approval? | **Documented Options:**<br>• Opt A: Enforce HR Recommendation Gate (Diagram Step 14A)<br>• Opt B: Direct Submission from SCM to Management (Baseline `REQ-MOD2-14`) | Mod II Brief Selection A(d, e); Mod 2 Diagram Step 14A | `DLT-21` (`CAND-REQ-M2-HRREC`)<br>Conflict: None | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-07`** | Mod III | Group-D Evaluation Form Completion | Baseline described evaluating actor as Reporting Supervisor. New diagram Box 2 & 3 explicitly states forms route to HOD who "Completes & Submits". | Does the Head of Department (HOD) personally complete Group-D evaluations, or does the immediate supervisor draft for HOD endorsement? | **Documented Options:**<br>• Opt A: Direct HOD Completion & Submission (Diagram Box 2 & 3)<br>• Opt B: Supervisor Draft + HOD Endorsement (Baseline `REQ-MOD3-01`)<br>*(Proposed Alternative: Configurable Departmental Delegation — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod III Group-D Brief Sec 1 & 2; Mod 3 Diagram Box 2 & 3 | `DLT-24`<br>Conflict: **`CFL-04`** | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-08`** | Mod III | Staff Quarterly Reminder Trigger Timing | Baseline mandated quarterly reviews by 15th with automated reminders. New diagram Box 4 states "automatic reminder after 20 days". | What is the exact trigger for the quarterly reminder: 20 days before quarter end, on Day 20 of quarter, or 5 days after submission due date? | **Documented Source Text:**<br>• Baseline: Automated reminder during quarterly review cycle (`REQ-MOD3-10`)<br>• Stakeholder Diagram: "automatic reminder after 20 days" (Track B Box 4)<br>*(Proposed Interpretations: Opt 1: 20 Days Before Quarter End; Opt 2: Day 20 of Quarter; Opt 3: 20 Days into Submission Month / Overdue Escalation — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod III KRA Brief Sec 2; Mod 3 Diagram Track B Box 4 | `DLT-32`<br>Conflict: None | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-09`** | Mod III | Multi-Unit Verification Routing Scope | Baseline routed faculty verification in parallel to 4 units. New diagram Track C Box 4 specifies the 4 units "and other stakeholders". | Does "and other stakeholders" require dynamically configurable additional verification units (e.g., IQAC, Finance), or remains fixed to 4? | **Documented Options:**<br>• Opt A: Permanently Fixed to 4 Units (Baseline `REQ-MOD3-17`)<br>*(Proposed Extension / Interpretation: Dynamically Configurable Stakeholders for "and other stakeholders" — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod III Faculty Brief Sec 3; Mod 3 Diagram Track C Box 4 | `DLT-35`<br>Conflict: None | `PENDING STAKEHOLDER CONFIRMATION` |
| **`CONF-10`** | Mod III | Faculty ECM Outcome Taxonomy Scope | Baseline focused on increments and promotions. New diagram Track C Box 10 expands outcomes to 7 types including PIP, Reprimand, Probation. | Does the University officially approve expanding ECM outcomes to include PIP, Formal Reprimand, Probation Extension, and Confirmation? | **Documented Options:**<br>• Opt A: Full 7-Outcome Taxonomy (Diagram Track C Box 10)<br>• Opt B: Compensation & Promotion Only (Baseline `REQ-MOD3-18`, `REQ-MOD3-19`)<br>*(Proposed Alternative: Phased Expansion — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification)* | Mod III Faculty Brief Sec 5 & 6; Mod 3 Diagram Box 10 | `DLT-37` (`CAND-REQ-M3-OUTCOMES`)<br>Conflict: None | `PENDING STAKEHOLDER CONFIRMATION` |

---

## 4. Detailed Decision Cards

```
====================================================================================================
                                      DETAILED DECISION CARDS
====================================================================================================
```

### CONF-01 — Authorized Initiator Scope for Service Change Requests

**Module:**  
Module I (HR Change Management & Central Employee Database)

**Current documented position:**  
The frozen requirements baseline (`REQ-MOD1-05`, `BP-M1-004`) restricts the initiation of employee service change requests strictly to the central HR Department. The newly supplied Module 1 complete workflow diagram (Box 2) broadens the initiation stage to: *"Authorized Initiator (HR / Admin / Department as per policy)"*.

**Why confirmation is required:**  
Defines system access permissions, initiation menus, role-based boundaries, and request validation logic. If initiation is decentralized to academic and administrative departments, the system must enforce strict field-level scoping and document attachment rules to prevent unauthorized or out-of-policy submissions.

**Stakeholder question:**  
Confirm the authorized initiator scope for raising employee service change requests: Should initiation be restricted strictly to HR Operations, or extended to designated Administrative Officers and Departmental authorities as stated in Module 1 Diagram Box 2 ("HR / Admin / Department as per policy")?

**Documented options:**  
- **Option A (Strict Centralized Model — Baseline `REQ-MOD1-05` / `BP-M1-004`):**  
  Only designated HR Operations officers can initiate formal Service Change Requests. School Deans and Department Heads submit change memos offline to HR.
- **Option B (Distributed Departmental Model — Diagram Box 2):**  
  HR Operations, designated Administrative Officers, and School/Department Authorities can directly raise service change requests online as permitted by university policy.

**Proposed alternative / requires clarification:**  
- **Proposed Alternative — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification: Employee Self-Service (ESS) Extension:**  
  Allow individual employees to initiate select personal/qualification change requests or resignation intake via an Employee Self-Service (ESS) portal. *(Note: ESS for general service changes is not supported in current stakeholder workflow diagrams and requires explicit policy approval).*

**Related delta item(s):**  
`DLT-08`

**Related conflict item:**  
None (Role scope clarification)

**Related TBD:**  
`REQ-TBD-01` (ERP Sync Protocol) / `REQ-TBD-06` (Resignation Intake)

**Impact area if changed:**  
Requirements Baseline (`REQ-MOD1-05`), Scope & Boundaries, Business Processes (`BP-M1-004`), FRD (`MOD1-CHG-REQ-01`), Role Permission Matrix.

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-02 — Associate Dean (Academics) Manpower Planning Role

**Module:**  
Module II (Recruitment & Selection Automation — Academic Track)

**Current documented position:**  
The frozen requirements baseline (`REQ-MOD2-02`, `BP-M2-ACAD-001`) described academic manpower planning initiated broadly by HR and Deans submitting requirements. The newly supplied Module 2 narrative (Paragraph 5) and workflow diagram (Step 1) explicitly name the **Associate Dean (Academics)** as the designated academic executive who triggers the 4-month planning communication to Deans, sets workload submission deadlines, and co-consolidates proposals.

**Why confirmation is required:**  
Establishes a new, distinct academic executive role in the system actor taxonomy, workflow trigger schedules, planning dashboards, and approval delegation rules.

**Stakeholder question:**  
Confirm whether **Associate Dean (Academics)** is formally recognized as the lead academic planning officer who triggers the 4-month manpower requirement cycle to Deans and co-consolidates faculty requisitions with HR for the Pro-Chancellor.

**Documented options:**  
- **Option A (New Stakeholder Model — Narrative Para 5 & Diagram Step 1):**  
  Formally introduce **Associate Dean (Academics)** as an authorized system role with dedicated planning dashboards, automated 4-month cycle triggers, and consolidation authority.
- **Option B (Baseline Administrative Model — `REQ-MOD2-02` / `BP-M2-ACAD-001`):**  
  Maintain HR Operations / Registrar as the institutional initiator of manpower planning calls; Associate Dean participates via standard academic committee review without dedicated system role credentials.

**Proposed alternative / requires clarification:**  
No formal alternatives are defined in the current source material outside Option A and Option B.

**Related delta item(s):**  
`DLT-10` (`CAND-REQ-M2-AD`)

**Related conflict item:**  
None (Role formalization; candidate requirement)

**Related TBD:**  
None

**Impact area if changed:**  
Requirements Catalogue (`REQ-MOD2-02` / Candidate ID `CAND-REQ-M2-AD`), Actor Matrix (`01-BUSINESS-PROCESS-FRAMEWORK.md`), Business Processes (`BP-M2-ACAD-001`), FRD (`MOD2-MP-FAC-REQ-01`).

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-03 — Academic Manpower Requisition Vetting Authority

**Module:**  
Module II (Recruitment & Selection Automation — Academic Track)

**Current documented position:**  
The original Module II Requirement Brief (Section 1) and frozen baseline (`REQ-MOD2-05`, `BP-M2-ACAD-003`) assign the 3-month review and vetting of all manpower requisitions to the **HR Department**. Conversely, the new Module 2 narrative (Paragraph 8) and workflow diagram (Step 2) assign vetting of Faculty & Lab Technician requisitions to the **Associate Dean (Academics)**, restricting Head HR to vetting Non-Faculty requisitions (Step 2B).

**Why confirmation is required:**  
Direct governance conflict (`CFL-01`). Determines who owns the vetting authority and primary review inbox for academic requisitions, and whether HR or the Associate Dean can return requisitions to Deans for clarification.

**Stakeholder question:**  
Does **Associate Dean (Academics)** vet academic requisitions (teaching workload and faculty posts) *exclusively in place of* HR, or is vetting conducted *jointly / sequentially with* the HR Department?

**Documented options:**  
- **Option A (New Stakeholder Model — Narrative Para 8 & Diagram Step 2):**  
  **Exclusive Academic Vetting by Associate Dean (Academics)**. Teaching load calculations and faculty requisitions route exclusively to the Associate Dean; HR Department receives consolidated proposals only at Step 3.
- **Option B (Original Baseline Model — Brief Sec 1, `REQ-MOD2-05`, `BP-M2-ACAD-003`):**  
  **Exclusive HR Vetting**. HR Department reviews and vets all academic requisitions against university teacher-student ratios and budget before submission to the Pro-Chancellor.

**Proposed alternative / requires clarification:**  
- **Proposed Alternative — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification: Two-Stage Joint Vetting:**  
  Associate Dean (Academics) vets academic workload justification and cadre distribution (Stage 1) → Head HR vets administrative headcount, salary band feasibility, and sanctioned post quota (Stage 2). Not explicitly defined in current source material; requires stakeholder confirmation.

**Related delta item(s):**  
`DLT-12`

**Related conflict item:**  
`CFL-01`

**Related TBD:**  
None

**Impact area if changed:**  
Requirements Catalogue (`REQ-MOD2-05`), Business Processes (`BP-M2-ACAD-003`), Business Rules (`BR-M2-003`), FRD (`MOD2-MP-FAC-REQ-03`), Workflow inbox routing.

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-04 — Lab Technician Cadre Alignment

**Module:**  
Module II (Recruitment & Selection Automation — Cadre Alignment)

**Current documented position:**  
The frozen baseline (`REQ-MOD2-01`, `BP-M2-NACAD-001`, `BP-M2-NACAD-006`) categorizes Lab Technicians under Non-Academic / Technical Staff, governed by three-round sequential interviews (Technical, HR, Management). The new Module 2 complete workflow diagram (Steps 1, 2, 6, 14A) explicitly groups **"Faculty & Lab Technician"** together under the Academic Track for planning, Dean MRF raising, Associate Dean vetting, and statutory Selection Committee Meetings (SCM).

**Why confirmation is required:**  
Direct governance conflict (`CFL-02`). Determines whether technical lab cadres require statutory selection committee panels with external subject experts or follow standard technical staff interview rounds.

**Stakeholder question:**  
Are **Lab Technicians** officially governed under the **Academic Track** (requiring Statutory SCM with external experts and teaching load vetting by Associate Dean) or under the **Non-Academic Track** (evaluated via 3-round interviews by Department Head, HR, and Management)?

**Documented options:**  
- **Option A (New Stakeholder Model — Diagram Steps 1, 2, 6, 14A):**  
  **Academic Track Alignment**. Lab Technicians are planned alongside faculty, vetted by Associate Dean (Academics), and selected via statutory Selection Committee Meetings (SCM) with external technical experts.
- **Option B (Original Baseline Model — `REQ-MOD2-01`, `BP-M2-NACAD-001/006`):**  
  **Non-Academic / Technical Track Alignment**. Lab Technicians are planned under Non-Faculty staffing, vetted by Head HR, and evaluated through 3-round interviews (Round 1: Practical/Technical Test with HOD, Round 2: HR, Round 3: Management).

**Proposed alternative / requires clarification:**  
- **Proposed Alternative — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification: Specialized Technical Interview Panel:**  
  Planned under School Academic Requirements by Deans, but evaluated via a specialized Technical Interview Panel rather than a full statutory academic SCM.

**Related delta item(s):**  
`DLT-11`

**Related conflict item:**  
`CFL-02`

**Related TBD:**  
`REQ-TBD-03` / `REQ-TBD-07`

**Impact area if changed:**  
Requirements Catalogue (`REQ-MOD2-01`, `REQ-MOD2-13`), Scope & Boundaries, Business Processes (`BP-M2-ACAD-001` vs `BP-M2-NACAD-001`), FRD (`MOD2-MP-FAC-REQ-01` vs `MOD2-MP-NF-REQ-01`).

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-05 — Management Pre-Approval for Interview (Step 13)

**Module:**  
Module II (Recruitment & Selection Automation — Common Selection Gate)

**Current documented position:**  
The earlier baseline (`REQ-MOD2-13`, `BP-M2-ACAD-008`, `BP-M2-NACAD-006`) moved directly from Recruiter Calling Sheet (RCS) shortlisting to interview panel scheduling. Management approval was required only at final offer/cost approval. Module 2 Diagram Step 13 introduces an explicit, mandatory governance gate: **"Management Approval for Interview"** prior to scheduling any interview.

**Why confirmation is required:**  
Governance conflict and candidate requirement (`CFL-03`, `DLT-19`). Adding an executive pre-interview sign-off gate introduces a potential scheduling bottleneck and alters the interview timeline.

**Stakeholder question:**  
Is executive **Management Approval (Step 13)** mandatory for *all* shortlisted candidates before interviews can be scheduled, or only for specific senior/academic tiers, or does shortlisting approval remain delegated to Deans/HR?

**Documented options:**  
- **Option A (Universal Mandatory Gate — Diagram Step 13 & `MOD2-MGT-REQ-01`):**  
  **Mandatory for All Candidates**. System strictly blocks interview scheduling until Senior Management reviews and approves candidate calling sheets across all Academic and Non-Academic positions.
- **Option B (Baseline Delegated Model — `BP-M2-ACAD-008` / `REQ-MOD2-13`):**  
  **Delegated Shortlisting**. HR and School Deans approve candidate shortlists and proceed directly to interview scheduling; Senior Management exercises governance at final cost and LOI approval post-interview.

**Proposed alternative / requires clarification:**  
- **Proposed Alternative — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification: Tiered Management Approval (Senior Posts Only):**  
  Management pre-approval is mandatory for Senior Academic posts (Professors, Associate Professors, Deans) and Senior Administrative Officers; Junior Faculty, Lab Technicians, and General Staff proceed directly from Dean/HR shortlisting.

**Related delta item(s):**  
`DLT-19` (`CAND-REQ-M2-INTAPP`)

**Related conflict item:**  
`CFL-03`

**Related TBD:**  
None

**Impact area if changed:**  
Requirements Catalogue (Candidate ID `CAND-REQ-M2-INTAPP`), Business Processes (`BP-M2-ACAD-008`), Business Rules (`BR-M2-010`), FRD (`MOD2-SEL-REQ-01`), Interview scheduling SLAs.

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-06 — Post-SCM Formal HR Recommendation Review

**Module:**  
Module II (Recruitment & Selection Automation — Academic Track)

**Current documented position:**  
The baseline (`REQ-MOD2-14`, `BP-M2-ACAD-010`) routes the statutory SCM panel evaluation matrix directly to the Vice-Chancellor and Senior Management for final selection and cost approval. The new Module 2 complete workflow diagram (Step 14A) introduces an explicit intermediate review stage: after SCM evaluators score candidates and system compiles matrix → **"HR formal recommendation review"** → Management Cost Approval → LOI.

**Why confirmation is required:**  
Adds a formal HR administrative checkpoint between statutory selection committee evaluations and executive Management sign-off.

**Stakeholder question:**  
Does the system enforce a formal **HR Recommendation review step post-SCM** before candidate files route to Senior Management for final cost approval?

**Documented options:**  
- **Option A (New Stakeholder Model — Diagram Step 14A):**  
  **Enforce HR Review Gate**. SCM scorecards and evaluation matrix route to Head HR for formal administrative verification, salary benchmarking, and written recommendation before reaching Management.
- **Option B (Direct Statutory Model — Baseline `REQ-MOD2-14` / `BP-M2-ACAD-010`):**  
  **Direct Management Submission**. SCM scorecards compile automatically and route directly to Vice-Chancellor / Senior Management; HR acts as recording secretariat.

**Proposed alternative / requires clarification:**  
No formal alternatives are defined in the current source material outside Option A and Option B.

**Related delta item(s):**  
`DLT-21` (`CAND-REQ-M2-HRREC`)

**Related conflict item:**  
None (Workflow clarification / extension)

**Related TBD:**  
None

**Impact area if changed:**  
Requirements Catalogue (Candidate ID `CAND-REQ-M2-HRREC`), Business Processes (`BP-M2-ACAD-010`), FRD (`MOD2-SCM-REQ-05`), Approval hierarchy.

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-07 — Group-D Evaluation Form Completion Responsibility

**Module:**  
Module III (Performance Management Automation — Subsystem 1: Group-D)

**Current documented position:**  
The baseline (`REQ-MOD3-01`, `BP-M3-GD-002`) describes the evaluating actor as the "Reporting Supervisor / Immediate Supervisor", recognizing that support staff report operationally to supervisors who draft scores for HOD endorsement. The new Module 3 complete workflow diagram (Box 2 & 3) explicitly states: Forms dispatched to **HOD**, and **"HOD completes and submits evaluation form online"** by the 7th of the month.

**Why confirmation is required:**  
Operational feasibility conflict (`CFL-04`). Academic Heads of Department managing large numbers of support staff may lack direct daily operational oversight without supervisor drafting.

**Stakeholder question:**  
Does the **Head of Department (HOD)** personally complete and submit monthly Group-D evaluation forms online, or does the **immediate supervisor / foreman** draft evaluations for HOD endorsement?

**Documented options:**  
- **Option A (Direct HOD Responsibility — Diagram Box 2 & 3):**  
  **HOD Direct Submission**. Evaluation forms are assigned exclusively to HODs, who personally score all criteria and submit by the 7th of the month.
- **Option B (Two-Tier Supervisory Model — Baseline `REQ-MOD3-01` / `BP-M3-GD-002`):**  
  **Supervisor Draft + HOD Endorsement**. Immediate supervisor/foreman enters operational scores (attendance, work quality, discipline); HOD reviews, adjusts, and provides final departmental submission.

**Proposed alternative / requires clarification:**  
- **Proposed Alternative — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification: Configurable Departmental Delegation:**  
  HOD may either evaluate directly or delegate drafting permissions to designated shift supervisors/foremen, retaining final sign-off authority.

**Related delta item(s):**  
`DLT-24`

**Related conflict item:**  
`CFL-04`

**Related TBD:**  
None

**Impact area if changed:**  
Business Processes (`BP-M3-GD-002`), Business Rules (`BR-M3-002`), FRD (`MOD3-GD-REQ-02`), User Roles (`05-user-roles`).

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-08 — Staff Quarterly Reminder Trigger Timing Logic

**Module:**  
Module III (Performance Management Automation — Subsystem 2: General Staff KRA/KPI)

**Current documented position:**  
The baseline (`REQ-MOD3-10`, `BP-M3-KRA-002`, `BR-M3-009`) mandates quarterly reviews (Q1–Q4) with submission by the 15th of the month following quarter-end; system sends automated reminders. The new Module 3 workflow diagram (Track B Box 4) states: **"Automatic reminder to employee and supervisor after 20 days"**.

**Why confirmation is required:**  
Notification scheduler timing ambiguity (`DLT-32`). "After 20 days" could mean 20 days prior to quarter end, Day 20 of the quarter, or 20 days after quarter start.

**Stakeholder question:**  
What is the exact temporal trigger for the automated quarterly staff review reminder: **20 days prior to quarter end**, or on the **20th calendar day of each quarter**, or **5 days after the 15th-day submission deadline** (overdue grace)?

**Documented source text:**  
- **Documented Baseline Specification (`REQ-MOD3-10`, `BP-M3-KRA-002`, `BR-M3-009`):**  
  Quarterly reviews conducted by the 15th of the month following quarter-end with automated notifications to employees and supervisors.
- **Documented Stakeholder Text (Diagram Track B Box 4):**  
  "Automatic reminder to employee and supervisor after 20 days." (Specific temporal formula not defined in source).

**Proposed alternative interpretations / requires clarification:**  
*Note: No formal temporal formula is defined in the current source material. The following operational triggers represent candidate interpretations requiring stakeholder clarification:*
- **Proposed Alternative 1 — Advance Warning Model:**  
  Reminder fires **20 calendar days before quarter-end** to prompt employees to prepare self-reviews and compile KPI evidence.
- **Proposed Alternative 2 — Quarterly Mid-Point Model:**  
  Reminder fires on the **20th day of the quarter** as an ongoing operational checkpoint.
- **Proposed Alternative 3 — Overdue Escalation Model:**  
  Reminder fires **20 days into the submission month** (5 days after the 15th submission deadline) to escalate pending quarterly appraisals before lockdown.

**Related delta item(s):**  
`DLT-32`

**Related conflict item:**  
None (Notification trigger clarification)

**Related TBD:**  
None

**Impact area if changed:**  
Business Processes (`BP-M3-KRA-002`), SLA & Escalation (`07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md`), Background Scheduler specifications.

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-09 — Configurable Multi-Unit Verification Routing Scope ("and other stakeholders")

**Module:**  
Module III (Performance Management Automation — Subsystem 3: Faculty ECM)

**Current documented position:**  
The baseline (`REQ-MOD3-17`, `BP-M3-FAC-004`) routes self-appraisal verification in parallel to exactly four units: (1) School Dean, (2) R&D Cell, (3) Placement Cell, (4) HR Department. The new Module 3 diagram (Track C Box 4) specifies routing to: School Dean, R&D Cell, Placement Cell, HR Department, **"and other stakeholders"**.

**Why confirmation is required:**  
Workflow scope extension (`DLT-35`). Determines whether the system verification workflow is hardcoded to 4 units or must support dynamic, configurable verification entities (e.g., IQAC, Examination Cell, Finance).

**Stakeholder question:**  
Does **"and other stakeholders"** require the faculty verification engine to support dynamically configurable verification units (such as IQAC or Finance) per faculty cadre, or remains permanently fixed to the 4 baseline units?

**Documented options:**  
- **Option A (Fixed 4-Unit Architecture — Baseline `REQ-MOD3-17` / `BP-M3-FAC-004`):**  
  **Permanently Fixed**. Verification routes exclusively and in parallel to School Dean, R&D Cell, Placement Cell, and HR Department.

**Proposed alternative / scope extension:**  
- **Proposed Alternative — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification: Dynamically Configurable Additional Stakeholder Units:**  
  Diagram Track C Box 4 mentions "and other stakeholders" without specifying institutional entities. Requires stakeholder clarification on which specific additional units (e.g., IQAC, Finance Officer) are intended and whether routing is cadre-specific or dynamically configurable.

**Related delta item(s):**  
`DLT-35`

**Related conflict item:**  
None (Workflow extension)

**Related TBD:**  
None

**Impact area if changed:**  
Business Processes (`BP-M3-FAC-004`), FRD (`MOD3-FAC-REQ-04`), Verification routing schema.

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

### CONF-10 — Formal Scope of Faculty Evaluation Committee Meeting (ECM) Outcomes

**Module:**  
Module III (Performance Management Automation — Subsystem 3: Faculty ECM)

**Current documented position:**  
The baseline (`REQ-MOD3-18`, `REQ-MOD3-19`, `BP-M3-FAC-008`) focuses on annual increment decisions, salary revisions, and promotions injected into Module I. The new Module 3 workflow diagram (Track C Box 10) expands the outcome taxonomy to **seven formal outcomes**: (1) Normal Increment, (2) Accelerated Increment, (3) Promotion, (4) **Performance Improvement Plan (PIP)**, (5) **Formal Reprimand**, (6) **Probation Extension**, (7) **Probation Confirmation**.

**Why confirmation is required:**  
Major functional expansion (`DLT-37`, `CAND-REQ-M3-OUTCOMES`). Expands Module III beyond compensation increments into disciplinary oversight, probationary governance, and remedial performance tracking.

**Stakeholder question:**  
Does the University officially approve expanding ECM outcomes beyond increments and promotions to include **PIP, Formal Reprimand, Probation Extension, and Confirmation** as automated system workflows?

**Documented options:**  
- **Option A (Full 7-Outcome Taxonomy — Diagram Box 10):**  
  **Approve All 7 Outcomes**. System implements dedicated state workflows for PIP monitoring, formal reprimand record flagging, probation extension timers, and confirmation letters alongside increments and promotions. *(Requires defining TBD policies REQ-TBD-17, 18, 19).*
- **Option B (Compensation & Promotion Only — Baseline `REQ-MOD3-18`, `REQ-MOD3-19`, `BP-M3-FAC-008`):**  
  **Restrict to Compensation & Cadre**. System manages Normal Increments, Accelerated Increments, and Promotions; disciplinary reprimands and PIPs remain external offline HR processes.

**Proposed alternative / requires clarification:**  
- **Proposed Alternative — Not Explicitly Defined in Current Source Material; Requires Stakeholder Clarification: Phased Implementation (Probation Now, Disciplinary Later):**  
  Approve Probation Confirmation and Extension immediately for Day-1 automation; defer automated PIP tracking and Formal Reprimand penalty workflows to a subsequent release.

**Related delta item(s):**  
`DLT-37` (`CAND-REQ-M3-OUTCOMES`)

**Related conflict item:**  
None (Major Candidate Requirement addition)

**Related TBD:**  
`REQ-TBD-17` (PIP Rules), `REQ-TBD-18` (Reprimand Policy), `REQ-TBD-19` (Probation Extension Thresholds)

**Impact area if changed:**  
Requirements Catalogue (Candidate ID `CAND-REQ-M3-OUTCOMES`; future requirement ID to be assigned during controlled post-sign-off baseline update), Business Processes (`BP-M3-FAC-008`), FRD (`MOD3-FAC-REQ-08`), TBD Register (`REQ-TBD-17`–`19`), Module I Injection Handshake (`BP-XMOD-004`).

**Decision Authority:**  
To be designated by University Leadership.

**Decision status:**  
`PENDING STAKEHOLDER CONFIRMATION`

**Stakeholder Decision:**  
`[                                                                                                  ]`

**Stakeholder Comments:**  
`[                                                                                                  ]`

---

## 5. Stakeholder Decision Log

The following template must be filled during the formal stakeholder confirmation session. All decision cells remain blank until officially confirmed by University Leadership:

| CONF ID | Decision Topic | Selected Option / Directive | Stakeholder Comments | Confirmation Date | Confirmed By (Name & Title) |
|---|---|---|---|---|---|
| **`CONF-01`** | Service Change Initiator Scope | | | | |
| **`CONF-02`** | Associate Dean Planning Role | | | | |
| **`CONF-03`** | Academic Vetting Authority | | | | |
| **`CONF-04`** | Lab Technician Cadre Alignment | | | | |
| **`CONF-05`** | Management Pre-Approval (Step 13)| | | | |
| **`CONF-06`** | Post-SCM HR Recommendation | | | | |
| **`CONF-07`** | Group-D Evaluation Completion | | | | |
| **`CONF-08`** | Staff Quarterly Reminder Timing | | | | |
| **`CONF-09`** | Multi-Unit Verification Scope | | | | |
| **`CONF-10`** | ECM 7-Outcome Taxonomy Scope | | | | |

---

## 6. Post-Sign-Off Impact Map

The following matrix identifies which formal documentation layers MAY require controlled updates AFTER stakeholder confirmation is obtained. **Zero files will be updated prior to sign-off.**

| CONF ID | Decision Topic | Documentation Layers Impacted | Post-Sign-Off Action Status |
|---|---|---|---|
| **`CONF-01`** | Service Change Initiator Scope | - Scope / Boundaries<br>- Business Processes (`BP-M1-004`)<br>- Functional Requirements (`MOD1-CHG-REQ-01`)<br>- Requirements Traceability | `POST-SIGN-OFF UPDATE REQUIRED IF DECISION EXPANDS INITIATOR SCOPE` |
| **`CONF-02`** | Associate Dean Planning Role | - Requirements Baseline (Candidate ID `CAND-REQ-M2-AD`)<br>- Requirement Catalogue (`REQ-MOD2-02`)<br>- Business Processes (`BP-M2-ACAD-001`)<br>- Functional Requirements (`MOD2-MP-FAC-REQ-01`) | `POST-SIGN-OFF UPDATE REQUIRED IF ROLE IS FORMALLY APPROVED` |
| **`CONF-03`** | Academic Vetting Authority | - Requirements Baseline (`REQ-MOD2-05`)<br>- Requirement Catalogue<br>- Business Processes (`BP-M2-ACAD-003`)<br>- Business Rules (`BR-M2-003`)<br>- Functional Requirements (`MOD2-MP-FAC-REQ-03`) | `POST-SIGN-OFF UPDATE REQUIRED IF DECISION CHANGES CURRENT BASELINE` |
| **`CONF-04`** | Lab Technician Cadre Alignment | - Requirements Baseline (`REQ-MOD2-01`, `REQ-MOD2-13`)<br>- Scope / Boundaries<br>- Business Processes (`BP-M2-ACAD-001` / `BP-M2-NACAD-001`)<br>- Functional Requirements<br>- Requirements Traceability | `POST-SIGN-OFF UPDATE REQUIRED IF DECISION CHANGES CADRE TRACK` |
| **`CONF-05`** | Management Pre-Approval (Step 13)| - Requirements Baseline (Candidate ID `CAND-REQ-M2-INTAPP`)<br>- Requirement Catalogue<br>- Business Processes (`BP-M2-ACAD-008`)<br>- Business Rules (`BR-M2-010`)<br>- Functional Requirements (`MOD2-SEL-REQ-01`) | `POST-SIGN-OFF UPDATE REQUIRED IF GATE IS MANDATED` |
| **`CONF-06`** | Post-SCM HR Recommendation | - Requirements Baseline (Candidate ID `CAND-REQ-M2-HRREC`)<br>- Requirement Catalogue (`REQ-MOD2-14`)<br>- Business Processes (`BP-M2-ACAD-010`)<br>- Functional Requirements (`MOD2-SCM-REQ-05`) | `POST-SIGN-OFF UPDATE REQUIRED IF CHECKPOINT IS ENFORCED` |
| **`CONF-07`** | Group-D Evaluation Completion | - Business Processes (`BP-M3-GD-002`)<br>- Business Rules (`BR-M3-002`)<br>- Functional Requirements (`MOD3-GD-REQ-02`)<br>- Audit / Delta Review | `POST-SIGN-OFF UPDATE REQUIRED IF DECISION CHANGES CURRENT BASELINE` |
| **`CONF-08`** | Staff Quarterly Reminder Timing | - Business Processes (`BP-M3-KRA-002`)<br>- Functional Requirements (`MOD3-KRA-REQ-02`)<br>- Architecture (Background Worker Schedules) | `POST-SIGN-OFF UPDATE REQUIRED TO CODIFY TEMPORAL TRIGGER` |
| **`CONF-09`** | Multi-Unit Verification Scope | - Business Processes (`BP-M3-FAC-004`)<br>- Functional Requirements (`MOD3-FAC-REQ-04`)<br>- Architecture (Dynamic Workflow Routing) | `POST-SIGN-OFF UPDATE REQUIRED IF DYNAMIC UNITS ARE APPROVED` |
| **`CONF-10`** | ECM 7-Outcome Taxonomy Scope | - Requirements Baseline (Candidate ID `CAND-REQ-M3-OUTCOMES`)<br>- Requirement Catalogue (Candidate ID `CAND-REQ-M3-OUTCOMES`; future requirement ID to be assigned during controlled post-sign-off baseline update)<br>- TBD / Open Decisions (`REQ-TBD-17` to `19`)<br>- Business Processes (`BP-M3-FAC-008`)<br>- Functional Requirements (`MOD3-FAC-REQ-08`) | `POST-SIGN-OFF UPDATE REQUIRED TO EXPAND FORMAL OUTCOME ENGINE` |

---

## 7. Governance & Baseline Protection Statement

```
====================================================================================================
                              GOVERNANCE & BASELINE PROTECTION INVARIANT
====================================================================================================
1. BASELINE FREEZE INTACT:
   The established baseline counts remain strictly frozen at:
   - 104 Atomic System Requirements (88 [A], 8 [B], 4 [C], 1 [D], 3 [E])
   - 11 Official Project TBD Items (REQ-TBD-01 through REQ-TBD-11)
   - 59 Discrete Business Processes (57 [A], 2 [B])
   - 60 Formal Business Rules (57 [A], 3 [B])

2. STAKEHOLDER DELTA STATUS & CANDIDATE REQUIREMENT MAPPING:
   The post-release stakeholder review findings documented in 09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md
   remain strictly provisional:
   - 37 Consolidated Delta Entries (DLT-01 through DLT-37)
   - 6 New Explicit Candidate Requirements (Provisional Total = 110 Requirements)
   - 10 Stakeholder Confirmation Decisions (CONF-01 through CONF-10)
   - 4 Documented Conflicts (CFL-01 through CFL-04)
   - 10 Reconciled Exception Conditions
   - 20 Consolidated TBD Items (11 Preserved + 9 Stakeholder-Added)

   Candidate Requirement Audit & Mapping:
   Exactly 6 DLT entries are classified as "NEW EXPLICIT REQUIREMENT":
   1. DLT-01: Multi-factor Pre-Submission Validation Checks -> Candidate ID: CAND-REQ-M1-VAL (No CONF ID; pre-validation gate)
   2. DLT-10: Associate Dean (Academics) Manpower Planning Role -> Candidate ID: CAND-REQ-M2-AD (Mapped to CONF-02)
   3. DLT-19: Mandatory Management Approval for Interview (Step 13) -> Candidate ID: CAND-REQ-M2-INTAPP (Mapped to CONF-05 / CFL-03)
   4. DLT-21: Post-SCM Formal HR Recommendation Review (Step 14A) -> Candidate ID: CAND-REQ-M2-HRREC (Mapped to CONF-06)
   5. DLT-22: Five-Stage Pre-Onboarding Milestone Tracking (Step 18) -> Candidate ID: CAND-REQ-M2-PREONB (Mapped to REQ-TBD-16; no CONF ID)
   6. DLT-37: Expanded 7-Outcome ECM Taxonomy (Track C Box 10) -> Candidate ID: CAND-REQ-M3-OUTCOMES (Mapped to CONF-10)

   Candidate Requirement Status Notice:
   Candidate IDs (CAND-REQ-*) are provisional working references established during delta review.
   They do NOT constitute frozen baseline requirement IDs. Candidate requirement ID mapping requires
   post-sign-off normalization during the controlled baseline update pass (Step 4). No future official
   requirement IDs have been manufactured or assigned prior to stakeholder sign-off.

3. IMPLEMENTATION HOLD:
   Phase 4 (Database Schema & Entity Models), Phase 5 (API Specifications), and all downstream
   implementation activities remain on strict hold until formal sign-off on this Decision Sheet
   is executed by University Leadership.
====================================================================================================
```

---
*End of Document — Stakeholder Decision Sheet.*
