# Stakeholder Requirement Delta & Impact Analysis
## Post-Release Analysis of Newly Supplied University/Mentor Stakeholder Materials

| Document Metadata | Specification Detail |
|---|---|
| **Document Reference** | `docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md` |
| **System Phase** | Phase 2 Post-Release / Controlled Requirement Impact Analysis |
| **Project** | University HR Change Management & Automation System |
| **Status** | `PROPOSED DELTA ANALYSIS — AWAITING STAKEHOLDER CONFIRMATION` |
| **Scope** | Controlled Impact Analysis of Newly Received Module I & Module II Stakeholder Narratives and Workflow Diagrams |
| **Authoritative Sources** | Original Module I, II, III Requirement PDFs; Newly Supplied Stakeholder Narratives & Workflow Diagrams; `PROJECT_REQUIREMENTS_ANALYSIS.md`; `docs/01-requirements/`; `docs/02-business-process/`; `docs/03-functional-requirements/`; `TECHNOLOGY_ARCHITECTURE_BASELINE.md` |
| **File Safety** | Strictly Analysis-Only — Zero Existing Baseline Files Modified |

---

## 1. Purpose

This document performs a formal, controlled **Requirement Delta and Impact Analysis** triggered by the receipt of new stakeholder materials provided by the University leadership and project mentors following the completion and freeze of the Phase 2 Business Process Documentation baseline.

The primary objectives of this analysis are:
1. **Identify and catalogue every difference, clarification, extension, and new concept** introduced in the newly supplied stakeholder narratives and complete workflow diagrams for Module I and Module II.
2. **Evaluate the exact impact** on the existing documentation baseline across Phase 1 Requirements (`docs/01-requirements/`), Phase 2 Business Processes (`docs/02-business-process/`), Phase 3 Functional Requirements (`docs/03-functional-requirements/`), and the approved Technology Architecture Baseline (`TECHNOLOGY_ARCHITECTURE_BASELINE.md`).
3. **Classify every identified delta** into standard analytical categories: *Already Covered*, *New Explicit Requirement*, *Clarification*, *Potential Conflict*, *New Exception / Special Condition*, or *TBD / Incomplete*.
4. **Determine whether previous audit declarations** (e.g., "104 atomic requirements fully mapped", "59 business processes complete") require planned adjustments or updates.
5. **Formulate a controlled change sequence and decision register** for university stakeholder review before any modifications are applied to existing baselines.

---

## 2. Baseline Being Compared

The analysis compares the new stakeholder materials against the established, internally verified project baseline:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                               ESTABLISHED PROJECT BASELINE                              │
├────────────────────────────────┬───────────────────────────────────────────────────────┤
│ Authoritative Requirements     │ source-requirements/ (Original Official Module I, II,  │
│                                │ III Requirement PDFs)                                 │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Requirements Analysis Baseline │ PROJECT_REQUIREMENTS_ANALYSIS.md                      │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Phase 1 Requirements Layer     │ docs/01-requirements/ (00 to 06, 104 Atomic REQs,      │
│                                │ 11 TBD Items REQ-TBD-01 to REQ-TBD-11)                │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Phase 2 Business Processes     │ docs/02-business-process/ (00 to 08, 59 BPs, 60 BRs,  │
│                                │ SLA Matrix, Handshakes BP-XMOD-001 to BP-XMOD-005)    │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Phase 3 Functional Reqs (FRD)  │ docs/03-functional-requirements/ (00 to 05, MOD1,      │
│                                │ MOD2, MOD3, Shared FRDs)                              │
├────────────────────────────────┼───────────────────────────────────────────────────────┤
│ Architecture Baseline          │ TECHNOLOGY_ARCHITECTURE_BASELINE.md & ADR-001         │
└────────────────────────────────┴───────────────────────────────────────────────────────┘
```

---

## 3. New Stakeholder Materials

The analysis investigates three new authoritative assets provided by institutional stakeholders:

1. **Document Asset 1:** `Module_1_HR_Change_Management_Narrative_Complete.docx` (and companion PDF), 87 paragraphs / 9,839 characters, detailing the institutional journey of employee service changes from current master record through submission, validation, two-level approval, effective-date activation, org structure reflection, audit logging, configurable reporting, and explicit exception conditions.
2. **Document Asset 2:** `Module_2_Recruitment_Selection_Narrative_Complete.docx` (and companion PDF), 60 paragraphs / 9,917 characters, detailing the 21-step end-to-end recruitment lifecycle across academic and non-academic tracks, role specializations, sourcing, RCS screening, interview approvals, Selection Committee mechanics, multi-round interviews, LOI issuance, and 5-stage pre-onboarding tracking.
3. **Visual Asset 1:** `Module 1 – HR Change Management & Automation System Complete Workflow Diagram` (embedded within Module 1 narrative docx), visualising the 15-stage workflow, system validation rules, two-level approval branches, and 7 explicit exception conditions.
4. **Visual Asset 2:** `Module 2 – Recruitment & Selection Automation System Complete Workflow Diagram` (embedded within Module 2 narrative docx and user-uploaded media), visualising the 21 numbered operational stages, dual-track routing (Academic: Faculty & Lab Technician vs. Non-Academic: Non-Faculty), Exception 5A (Urgent Replacement MRF), Step 13 (Management Approval for Interview), and pre-onboarding milestones.

---

## 4. Analysis Method & Classification Taxonomy

Every distinct institutional requirement, workflow step, governance role, or operational condition identified in the new stakeholder materials was evaluated against the established baseline and classified into exactly one of six analytical categories:

| Category | Definition | Governance Action |
|---|---|---|
| **1. ALREADY COVERED** | The concept, role, rule, or timeline is already fully captured in existing documentation without substantive discrepancy. | No change required; confirm alignment. |
| **2. NEW EXPLICIT REQUIREMENT** | The new material introduces a concrete requirement, governance gate, or role not previously specified in the official PDFs or baseline. | Formulate candidate requirement ID; await stakeholder confirmation before adding. |
| **3. CLARIFICATION** | The requirement existed in the baseline, but the new material provides crucial operational detail, explicit sub-steps, or clearer interpretation. | Refine existing requirement or process description during planned update. |
| **4. POTENTIAL CONFLICT** | The new material appears inconsistent with an existing documented requirement, role assignment, or timing. | Document divergence; do NOT resolve unilaterally; mark "NEEDS STAKEHOLDER CONFIRMATION". |
| **5. NEW EXCEPTION / SPECIAL CONDITION** | The new material introduces an explicit alternate path, exception flow, or edge case not previously documented. | Incorporate into exception catalogue and workflow branching logic upon approval. |
| **6. TBD / INCOMPLETE** | The new material names an important concept or policy condition, but explicitly notes that detailed rules, formulas, or thresholds must not be invented by developers and require university policy definition. | Map to or create an entry in the official TBD register (`REQ-TBD-*`). |

---

## 5. Module I Delta Analysis (HR Change Management)

### A. Narrative & Workflow Deep-Dive
The new Module I narrative and workflow diagram outline a 15-stage lifecycle for employee service changes. The central conceptual paradigm reinforces that Module I is not an administrative data-editing form, but a **controlled, audited state journey** from existing master data to approved, scheduled, and effective state.

```
 [1. Employee Current Info] ──► [2. Initiate Request] ──► [3. Submit & System Validation]
                                                                     │
  ┌──────────────────────────────────────────────────────────────────┴────────────────────────────────┐
  ▼                                                                                                   ▼
 [4. HR Review (Level 1)] ──(Clarification / Resubmit)──► [Initiator]                 [System Validation Fails]
  │        │ (Reject: Closed with Reason)                                                             │
  │        ▼                                                                                          ▼
  │     [Closed]                                                                        [Invalid / Out of Policy]
  ▼ (Approve)
 [5. Senior Management Approval (Level 2)] ──(Clarification)──► [HR Review]
  │        │ (Reject: Closed with Reason)
  │        ▼
  │     [Closed]
  ▼ (Approve)
 [6. Approved Change: "Approved (Yet to be Effective)"]
  │
  ▼
 [7. Effective Date Handling: "Scheduled"] ──► [8. Change Becomes Effective]
                                                         │
  ┌──────────────────────────────────────────────────────┴────────────────────────────────────────────┐
  ▼                                                      ▼                                            ▼
 [9. Update Central Employee DB]          [10. Update Organization Structure]          [11. Related Systems & ERP]
  │                                                      │                                            │
  └──────────────────────────────────────────────────────┬────────────────────────────────────────────┘
                                                         ▼
                                 [13. Audit Trail & Version History]
                                 [14. Configurable Real-Time Reporting]
                                 [15. Completed Change Lifecycle]
```

### B. Detailed Comparative Findings

| Topic / Dimension | Existing Baseline Representation | New Stakeholder Material Representation | Classification | Analysis & Impact |
|---|---|---|---|---|
| **A. Proposed vs. Approved Change Distinction** | Covered in `BP-M1-004`, `BP-M1-007`, `MOD1-CHG-REQ-11`. Pending requests remain separate from active data. | Narrative paragraphs 9–10, 28–30; Diagram Box 1, 3, 6. Emphasizes that proposed changes do not mutate master fields until approved and effective. | **ALREADY COVERED** | Baseline aligns 100%. Reaffirms the multi-state lifecycle model. |
| **B. Pending Approval State** | Covered in `BP-M1-004`, `MOD1-CHG-REQ-11` as `SUBMITTED_PENDING_HR`. | Diagram Box 12 (Special Condition 3): "Pending Approval — Request remains in workflow; Not treated as approved change; Status visible in reports." | **CLARIFICATION** | Explicit requirement that pending changes must remain visible in operational reports while isolating active records. |
| **C. HR Review & Clarification Loop** | `BP-M1-005` covers Level-1 HR Review and return for correction. | Diagram Box 4 & Box 12: "Clarification Required — Sent back to initiator (with comments) $\rightarrow$ Resubmit (with updated information)." | **CLARIFICATION** | Visualises and specifies the bidirectional clarification loop between HR and Initiator with mandatory comments. |
| **D. Senior Management Approval & HR Loop** | `BP-M1-006` covers Level-2 Senior Management Approval and Rejection. | Diagram Box 5 & Box 12: Management reviews HR-approved request, checks justification, impact, and budget. May return to HR for clarification ("Send back to HR with comments"). | **CLARIFICATION** | Clarifies that Management can return requests to HR (Level 1) with comments rather than outright rejection. |
| **E. Effective Date Handling** | Covered in `BP-M1-007`, `BR-M1-005`, `MOD1-EFF-REQ-01` to `03`. Future changes scheduled; past changes effective upon approval. | Diagram Boxes 6, 7, 8: Introduces explicit intermediate statuses: "Approved (Yet to be Effective)" and "Scheduled". System tracks and activates on date. | **CLARIFICATION** | Adopts explicit stakeholder status labels (`APPROVED_YET_EFFECTIVE`, `SCHEDULED`). |
| **F. Approval Date vs. Effective Date** | `MOD1-EFF-REQ-01` separates `approval_date` and `effective_date`. | Narrative paragraphs 25–26: "The approval date and the effective date do not necessarily have to be the same... system preserves the approved effective date." | **ALREADY COVERED** | Reaffirms baseline architectural separation of decision timestamps from legal enactment dates. |
| **G. Central Employee Database** | `BP-M1-001`, `MOD1-CDB-REQ-01`. Central DB is master of all employee records, reflected in ERP. | Diagram Box 9 & Narrative paragraphs 32–33. Updated values written on effective date; historical record maintained; ERP synchronization. | **ALREADY COVERED** | Baseline aligns 100%. |
| **H. Organization Chart Reflection** | `BP-M1-002`, `BR-M1-002`, `MOD1-ORG-REQ-01`. Structural changes reflect on effective date. | Diagram Box 10: "If change affects reporting authority, reportee, department, location, level etc. Organization chart is updated automatically or through defined process." | **ALREADY COVERED** | Confirms baseline dynamic org chart reflection requirement. |
| **I. Audit Trail & Version History** | `BP-M1-008`, `BR-M1-006`, `MOD1-AUD-REQ-01` to `04`. Before/after values, timestamps, operator IDs. | Diagram Box 13 & Narrative paragraphs 40–46: "All changes recorded with timestamp; Previous and new values stored; Who initiated, who approved, who changed." | **ALREADY COVERED** | Baseline aligns 100%. |
| **J. System Validation at Submission** | `MOD1-CHG-REQ-12` specifies basic mandatory field validation. | Diagram Box 3: Explicitly mandates 4 automated validation checks: (1) Mandatory fields, (2) Data format, (3) Effective date rules (e.g. not past/future as per policy), (4) Check for existing pending changes (conflict/dependency). | **NEW EXPLICIT REQUIREMENT** | Elevates submission-time pre-validation checks into formal functional requirements. |
| **K. Multiple / Conflicting Changes** | Noted in Phase 2 as an anti-invention caution; no detailed arbitration algorithm defined. | Narrative paragraphs 56–63 & Diagram Box 12: "Simultaneous requests possible; Detailed business rules to be defined by University; System should not automatically overwrite or assume priority." | **TBD / INCOMPLETE** | Explicitly confirms that developers must NOT invent priority rules (e.g. "latest wins"). Requires dedicated TBD entry. |
| **L. Cancellation / Withdrawal** | Identified in Phase 2 as an unspecified alternate path. | Diagram Box 12: "Cancellation / Withdrawal — May be allowed as per policy; Status updated and recorded; No change applied." | **TBD / INCOMPLETE** | Requires formal stakeholder policy on who can withdraw a change request (initiator vs. HR) and at what workflow stages. |
| **M. Invalid / Out-of-Policy Request** | Implicit in UI submission errors. | Diagram Box 12: "Invalid / Out of Policy Request — System validation fails; Correct information required; Resubmit after correction." | **CLARIFICATION** | Formalizes client-side and server-side validation error handling state. |
| **N. Authorized Initiator Role Definition** | `MOD1-CHG-REQ-01` stated HR Initiator / Employee Self-Service (clarified as TBD in `REQ-TBD-01`). | Diagram Box 2: "Authorized Initiator (HR / Admin / Department as per policy)." | **CLARIFICATION / TBD** | Confirms initiator permissions are governed by university policy across HR, Administrative officers, and Departments. |
| **O. Configurable Real-Time Reporting** | `BP-M1-010`, `MOD1-REP-REQ-01` to `04`. Dynamic queries, exportable formats. | Diagram Box 14 & Narrative paragraphs 68–70: HR provides list and formats; reports can be added/deleted dynamically; real-time execution required. | **ALREADY COVERED** | Reaffirms dynamic, non-static reporting architecture. |

---

## 6. Module II Delta Analysis (Recruitment & Selection Automation)

### A. Narrative & Workflow Deep-Dive
The newly supplied Module II narrative and workflow diagram present a complete **21-stage end-to-end recruitment lifecycle**, structured into distinct but interconnected operational tracks:
- **Academic Track (Faculty & Lab Technician):** Managed through Associate Dean (Academics), School Deans, Statutory Selection Committee with External Expert, HR recommendation, and Management recommendation with cost approval.
- **Non-Academic Track (Non-Faculty):** Managed through HR, Department Heads, 3-round interview (Technical, HR, Management), and Management recommendation with cost approval.
- **Common Engine:** Manpower planning timing, Consolidation, Pro-Chancellor approval, MRF processing, Open Positions Tracker, multi-channel sourcing, Central CV Database, RCS phone screening, Management Interview Approval, LOI generation, Yet-to-Join tracking, 5-stage pre-onboarding, and Central DB onboarding handshake.

```
 [1. Manpower Planning: >= 4 Months] 
   ├─► Academic: Associate Dean (Academics) -> Deans (15 Days) [Faculty & Lab Tech]
   └─► Non-Academic: HR -> Department Heads [1 MRF/Year] (15 Days) [Non-Faculty]
                         │
                         ▼
 [2. Vetting of Requirement] ──(Clarification Loop)──► [Deans / Dept Heads]
   ├─► Faculty & Lab Tech: Vetted by Associate Dean (Academics)
   └─► Non-Faculty: Vetted by Head HR
                         │
                         ▼
 [3. Consolidation: 15 Days] ──► [4. Approval: Pro-Chancellor] ──► [5. Communication: 7 Days]
                         │
                         ├──────────────────────────────────────────┐
                         ▼                                          ▼
 [6. MRF Creation & HR Initiation: 7 Days]               [5A. Exception: Urgent / Replacement MRF]
   ├─► Faculty & Lab Tech: Dean raises after approval     (Resignation accepted by Dean -> Urgent MRF
   └─► Non-Faculty: MRF raised at requisition stage        -> Vetting -> Pro-Chancellor Approval -> Fast Track)
                         │                                          │
                         └───────────────────┬──────────────────────┘
                                             ▼
                                [7. Open Positions Tracker]
                                             │
                                             ▼
                                [8. Advertisement & Sourcing]
                                             │
                                             ▼
                                [9. Applications Collection]
                                             │
                                             ▼
                               [10. Central CV Database]
                                             │
                                             ▼
                             [11. Classification & Shortlisting]
                                             │
                                             ▼
                                 [12. Recruiter Calling (RCS)]
                                             │
                                             ▼
                           [13. Management Approval for Interview]  ◄── [CRITICAL NEW GOVERNANCE GATE]
                                             │
                         ┌───────────────────┴──────────────────────┐
                         ▼                                          ▼
           [14A. Academic Selection]                  [14B. Non-Academic Selection]
           - Selection Committee (SCM)                - Round 1: Technical (HOD/Expert)
           - External Subject Expert                  - Round 2: HR (Head HR)
           - Digital Scoring / Evaluation Matrix      - Round 3: Management
           - HR Recommendation                        - Evaluation Sheet (Job Knowledge,
           - Management Recommendation & Cost Appr      Communication, Attitude)
                         │                            - Management Recommendation & Cost Appr
                         └───────────────────┬──────────────────────┘
                                             ▼
                               [15. Generate Letter of Intent (LOI)]
                                             │
                                             ▼
                               [16. Candidate Accepts LOI]
                                             │
                                             ▼
                               [17. Status: "Yet to Join"]
                                             │
                                             ▼
                               [18. Pre-Onboarding & Joining]
                               - Offer acceptance, Notice period, Verification, Joining, Onboarding
                                             │
                                             ▼
                               [19. Close Recruitment Cycle]
                               - Open Positions Tracker: Closed
                               - Candidate Handshake -> Module I Central DB
                                             │
                                             ▼
                               [20. Management Reporting] & [21. Audit Trail & Timelines]
```

### B. Detailed Comparative Findings

| Step / Topic | Existing Baseline Representation | New Stakeholder Material Representation | Classification | Analysis & Impact |
|---|---|---|---|---|
| **1. Academic Planning Lead Time & Roles** | `BP-M2-ACAD-001`, `REQ-MOD2-02`. 4 months prior to semester; Dean submits within 15 days. Initiator listed as HR/Deans. | Step 1 & Narrative paragraph 5: **Associate Dean (Academics)** communicates to Deans; Deans assess workload, teaching load, replacement, and expansion. Covers **Faculty & Lab Technician**. | **NEW EXPLICIT REQUIREMENT / CLARIFICATION** | Introduces **Associate Dean (Academics)** as lead academic planning officer; explicitly groups **Lab Technician** under Academic Track. |
| **2. Non-Academic Planning Lead Time & Quota** | `BP-M2-NACAD-001`, `REQ-MOD2-09`, `10`. 4 months prior; 15-day submission; 1 planned MRF per department per year. | Step 1: HR communicates to Department Heads; Department Head assesses operational need; submits MRF (One planned requisition per year; urgent MRF any time). | **ALREADY COVERED** | Baseline aligns 100%. Reaffirms the strict 1 planned MRF/year quota. |
| **3. Vetting Authority & Clarification Loop** | `BP-M2-ACAD-003` assigned 3-month vetting broadly to HR Department. | Step 2: **Associate Dean (Academics)** vets Faculty & Lab Technician; **Head HR** vets Non-Faculty. Explicit diamond: "Clarification needed? $\rightarrow$ Send back for clarification/additional information (System tracks timeline)". | **POTENTIAL CONFLICT / CLARIFICATION** | Divergence from earlier brief assigning vetting exclusively to HR. Now split between Associate Dean (Academics) and Head HR with explicit clarification loop. |
| **4. Consolidation & Forwarding to Management** | `BP-M2-ACAD-004`, `REQ-MOD2-06`. HR consolidates within 15 days. | Step 3: **Associate Dean (Academics) / Head HR** consolidates requirements with recommendations within 15 days of receipt. | **CLARIFICATION** | Confirms joint or cadre-specific consolidation responsibility. |
| **5. Pro-Chancellor Approval & Communication** | `BP-M2-ACAD-005`, `REQ-MOD2-07`. Pro-Chancellor approves; communicated within 7 days. | Steps 4 & 5: Pro-Chancellor reviews/approves; system tracks timeline and notifies; approval communicated to Dean / Dept Head within 7 days. | **ALREADY COVERED** | Baseline aligns 100%. |
| **6. MRF Creation Timing Asymmetry** | `BP-M2-ACAD-006` assumed HR generated MRF upon plan approval. | Step 6: Explicit asymmetry: **Faculty & Lab Technician:** Dean raises MRF *after* approval and routes to HR; **Non-Faculty:** MRF already raised at requisition stage. HR initiates recruitment within 7 days. | **CLARIFICATION** | Resolves MRF generation mechanics: Academic MRFs are raised post-approval by Deans; Non-Academic MRFs originate at planning. |
| **7. Urgent / Replacement MRF (Step 5A)** | `BP-M2-URG-001`, `BP-XMOD-002`, `REQ-MOD2-03`. Resignation accepted by Dean triggers urgent replacement. | Step 5A: Resignation accepted by Dean $\rightarrow$ Raise urgent/replacement MRF at any time $\rightarrow$ Vetting (Associate Dean / Head HR) $\rightarrow$ Pro-Chancellor approval $\rightarrow$ Recruitment process. | **CLARIFICATION / NEW EXCEPTION FLOW** | Clarifies governance of urgent MRF: still requires Vetting (Associate Dean / Head HR) and Pro-Chancellor approval before sourcing. |
| **8. Open Positions Tracker Maintenance** | `BP-M2-TRK-002`, `REQ-MOD2-21`. Maintained within 30 days. | Step 7: All approved positions recorded and maintained in Open Positions Tracker (Completed within 30 days). | **ALREADY COVERED** | Baseline aligns 100%. |
| **9. Sourcing Channels & Application Collection** | `BP-M2-ACAD-006`, `BP-M2-TRK-001`. Multi-channel sourcing. | Steps 8 & 9: Advertisements across print media, social media, University website. Ingestion from Email, Facebook, Instagram, LinkedIn, website, newspapers, internal references, Internshala (internships). | **CLARIFICATION** | Explicitly confirms Internshala for internships and full social media roster. |
| **10. Central CV Database & Classification** | `BP-M2-TRK-001`, `REQ-MOD2-19`. Central searchable database. | Steps 10 & 11: All applications in one place; auto-segregation and classification based on Educational qualification, Experience, Applicable UGC norms. | **ALREADY COVERED** | Baseline aligns 100%. |
| **11. Shortlisting Algorithms & UGC Norms** | Phase 2 flagged scoring weights and rejection rules as `[E] TBD`. | Narrative paragraph 22: Qualification/experience screening is required, but system must NOT assume unshortlisted candidates are rejected; detailed exception rules and scoring formulas remain institutional policy TBD. | **TBD / INCOMPLETE** | Reaffirms baseline position: developers must not invent ranking or disqualification algorithms. |
| **12. Recruiter Calling Sheet (RCS)** | `BP-M2-NACAD-005`, `BP-M2-TRK-001`, `BR-M2-021`. RCS tracks all calls. | Step 12: Recruiter records call inputs in prescribed RCS format; routed to Head HR. | **ALREADY COVERED** | Baseline aligns 100%. |
| **13. Management Approval for Interview** | **Not present in earlier baseline.** Baseline moved from RCS directly to SCM/Round 1 scheduling. | **Step 13: "MANAGEMENT APPROVAL FOR INTERVIEW — Shortlisted candidates' information routed to Management for approval."** | **NEW EXPLICIT REQUIREMENT** | **CRITICAL NEW GOVERNANCE GATE.** Interviews cannot be scheduled after shortlisting without prior executive Management approval. |
| **14. Academic Selection Process (14A)** | `BP-M2-ACAD-008`–`010`. SCM with External Expert; digital scoring matrix. | Step 14A: SCM (Internal + External expert where required); digital invitations, resume, evaluation sheet; online interview default (offline if necessary); evaluator scoring; **HR recommendation**; **Management recommendation and cost approval**. | **NEW EXPLICIT REQUIREMENT / CLARIFICATION** | Confirms: (1) Online interview scheduling default, (2) Explicit **HR recommendation** stage post-SCM, (3) Formal **Management cost approval** before LOI. |
| **15. Non-Academic Selection Process (14B)** | `BP-M2-NACAD-006`. 3 rounds (Technical, HR, Management) evaluating Job Knowledge, Communication, Attitude. | Step 14B: Round 1 Technical (HOD/expert) $\rightarrow$ Round 2 HR (Head HR) $\rightarrow$ Round 3 Management $\rightarrow$ Evaluation sheet (3 dimensions) $\rightarrow$ **Management recommendation and cost approval**. | **ALREADY COVERED / CLARIFICATION** | Reaffirms 3-round sequence and 3 dimensions; clarifies that Management round culminates in formal cost approval. |
| **16. LOI Generation & Acceptance** | `BP-M2-ACAD-011`, `REQ-MOD2-17`. System generates LOI. | Steps 15 & 16: System automatically generates LOI after Management approval; candidate accepts LOI. | **ALREADY COVERED** | Baseline aligns 100%. |
| **17. Yet-to-Join State** | `BP-M2-ACAD-012`, `REQ-MOD2-18`. Intermediate status before joining. | Step 17 & Narrative paragraphs 35–36: Candidate status updated to "Yet to Join" in internal HR database; candidate not treated as employee yet. | **ALREADY COVERED** | Baseline aligns 100%. |
| **18. Pre-Onboarding Milestones Tracking** | Mentioned generally in `BP-M2-ACAD-012` as check-ins. | Step 18: Mandates explicit tracking of 5 distinct candidate milestones: (1) Offer acceptance, (2) Notice period, (3) Verification, (4) Joining, (5) Onboarding. | **NEW EXPLICIT REQUIREMENT** | Formalizes candidate lifecycle tracking into 5 explicit milestone stages with associated reporting. |
| **19. Pre-Onboarding Exception Rules** | Not defined in official PDFs. | Narrative paragraphs 49–50: Notice period delays, verification failures, no-shows must be tracked, but exact policy rules are institutional TBD. | **TBD / INCOMPLETE** | Requires formal stakeholder policy on candidate dropout, notice extension, and offer revocation. |
| **20. Close Recruitment Cycle & Handshake** | `BP-M2-TRK-002`, `BP-XMOD-001`. Position marked closed; record instantiated in Module I. | Step 19: Update Open Positions Tracker (Position status: Closed); new employee moves to Central Employee Database (Module I). | **ALREADY COVERED** | Baseline aligns 100%. |
| **21. Reporting & Audit Trail** | `BP-M2-TRK-002`, `REQ-REP-05`, `REQ-AUD-01` to `04`. Weekly reporting; timestamped stages. | Steps 20 & 21: Weekly progress reports to Management; all stages timestamped; complete audit trail and version history for Academic & Non-Academic. | **ALREADY COVERED** | Baseline aligns 100%. |

---

## 7. Cross-Module Impact

The newly supplied stakeholder materials reinforce the cross-module boundaries while introducing critical refinements to inter-module data handshakes:

```
   ┌────────────────────────────────────────────────────────────────────────────────────────┐
   │                               MODULE II: RECRUITMENT                                   │
   │  Step 19: Close Cycle ──► Candidate Onboarded                                          │
   │                               │                                                        │
   │                               ▼ Handshake BP-XMOD-001                                  │
   │  ┌──────────────────────────────────────────────────────────────────────────────────┐  │
   │  │ Module I: Central Employee Database (Box 1 & 9)                                  │  │
   │  │ - Instantiates Master Record & Unique Code                                       │  │
   │  │ - Attaches Dossier Documents & Certificates                                      │  │
   │  │ - Updates Organization Structure (Box 10)                                        │  │
   │  │ - Reflected in ERP (Box 11)                                                      │  │
   │  └────────────────────────────┬─────────────────────────────────────────────────────┘  │
   │                               │                                                        │
   │                               │ Resignation Accepted by Dean (Box 5A)                  │
   │                               ▼ Handshake BP-XMOD-002                                  │
   │  Step 5A: Urgent / Replacement MRF ──► Vetting ──► Pro-Chancellor Approval ──► Sourcing │
   └────────────────────────────────────────────────────────────────────────────────────────┘
```

1. **Handshake `BP-XMOD-001` (Onboarding $\rightarrow$ Central DB):** Reconfirmed by Step 19 of Module II and Boxes 1, 9, 10, 11 of Module I. When a candidate completes onboarding, the master employee record, dossier, dynamic org chart node, and ERP reflection are established.
2. **Handshake `BP-XMOD-002` (Resignation $\rightarrow$ Urgent Replacement MRF):** Reconfirmed and clarified by Module II Step 5A. Resignation acceptance by Dean in Module I triggers an urgent MRF in Module II, which undergoes fast-track vetting by Associate Dean / Head HR and Pro-Chancellor approval.
3. **Module I Service Changes $\rightarrow$ Downstream ERP & Org Chart:** Module I Boxes 9, 10, and 11 explicitly confirm that effective service changes propagate to the connected Organization Chart and external ERP payroll.

---

## 8. New Exceptions & Special Conditions

The new stakeholder materials introduce **eight explicit exception categories and special operational conditions** that require formal documentation:

### Module I Exceptions (From Workflow Diagram Box 12)
1. **Clarification Required (HR / Senior Management):** A change request may be returned with structured comments by HR (to the initiator) or Senior Management (to HR). The request transitions to `CLARIFICATION_REQUIRED` and re-enters review upon resubmission.
2. **Rejection with Reason:** An authorized reviewer (HR or Senior Management) may reject a request. The request transitions to `REJECTED`, the mandatory institutional reason is recorded, and employee master data remains unchanged.
3. **Pending Approval Reporting Isolation:** While a request is in `PENDING_HR_REVIEW` or `PENDING_MANAGEMENT_APPROVAL`, it remains part of the in-flight workflow and must be reported as pending without prematurely modifying active employee records.
4. **Future Effective Date Scheduling:** If `effective_date` > `approval_date`, the request transitions to `APPROVED_SCHEDULED`. System tracks the scheduled change and executes activation automatically at 00:00 on the effective date.
5. **Multiple / Conflicting Changes Exception:** When two simultaneous change requests affect the same employee (e.g., salary change and designation change), the system must detect the conflict during pre-validation and flag it for administrative review rather than arbitrarily overwriting values.
6. **Cancellation / Withdrawal:** An initiator or HR may withdraw an in-flight request prior to final approval as permitted by university policy. The request transitions to `WITHDRAWN` with an audit record, and no change is applied.
7. **Invalid / Out-of-Policy Request:** System pre-validation fails upon submission (e.g., missing mandatory documents, malformed dates, invalid salary bands). The form is rejected back to the initiator with specific validation error codes.

### Module II Exceptions (From Workflow Diagram Step 5A & Narrative)
8. **Urgent / Replacement MRF (Exception 5A):** Triggered immediately upon Dean's formal acceptance of an employee resignation. Bypasses the annual planning window and the non-academic 1-MRF/year quota; undergoes expedited vetting (Associate Dean / Head HR) and Pro-Chancellor approval.

---

## 9. Potential Conflicts & Divergences Requiring Confirmation

The analysis identified **four specific areas of divergence or tension** between the newly supplied materials and the earlier documentation baseline:

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        AREAS REQUIRING STAKEHOLDER CONFIRMATION                         │
├──────────────────────┬──────────────────────────┬──────────────────────────────────────┤
│ Operational Topic    │ Earlier Baseline         │ New Stakeholder Material             │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 1. Academic Vetting  │ Assigned broadly to HR   │ Assigned to Associate Dean           │
│    Authority         │ Department (3 months)    │ (Academics) for Faculty & Lab Tech   │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 2. Lab Technician    │ Categorized generally as │ Explicitly placed under Academic     │
│    Track Placement   │ non-teaching / technical │ Track with Faculty (SCM Selection)   │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 3. Pre-Interview     │ RCS shortlist scheduled  │ Mandatory "Management Approval for   │
│    Approval Gate     │ directly for interview   │ Interview" (Step 13) before schedule │
├──────────────────────┼──────────────────────────┼──────────────────────────────────────┤
│ 4. Post-SCM Decision │ SCM Matrix submitted     │ SCM -> HR Recommendation ->          │
│    Flow              │ directly to Management   │ Management Cost Approval             │
└──────────────────────┴──────────────────────────┴──────────────────────────────────────┘
```

### Detailed Conflict Analysis

#### Conflict 1: Academic Vetting Authority
- **Earlier Baseline:** Module II PDF Section 1 and `docs/01-requirements/02-REQUIREMENT-CATALOGUE.md` (`REQ-MOD2-05`) state that the HR Department conducts a 3-month vetting of academic requirements submitted by Deans.
- **New Stakeholder Material:** Module II Narrative paragraph 8 and Diagram Step 2 state: *"For Faculty and Lab Technician positions, it goes to the Associate Dean; for Non-Faculty positions, it goes to the Head HR."*
- **Analysis:** This introduces a new institutional role (**Associate Dean - Academics**) as the primary vetting authority for academic positions, while retaining Head HR for non-academic positions.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Clarify whether Associate Dean (Academics) conducts vetting *in place of* HR, or whether Associate Dean conducts academic curriculum vetting *jointly with* HR's administrative cadre vetting.

#### Conflict 2: Lab Technician Cadre Placement
- **Earlier Baseline:** Lab Technicians were presumed to fall under Non-Academic / Technical staff subject to the 3-round selection process.
- **New Stakeholder Material:** Module II Diagram Steps 1, 2, 6, and 14A explicitly classify **"Faculty & Lab Technician"** together under the **Academic Track**, subject to Associate Dean vetting and Selection Committee interview!
- **Analysis:** This is an explicit stakeholder reclassification. Lab Technicians follow the Academic Track selection rather than the Non-Academic 3-round interview.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Confirm that Lab Technicians are evaluated by the Statutory Selection Committee rather than the 3-round Non-Academic interview.

#### Conflict 3: Mandatory Management Approval for Interview (Step 13)
- **Earlier Baseline:** In Phase 1 (`REQ-MOD2-13`) and Phase 2 (`BP-M2-ACAD-008`, `BP-M2-NACAD-006`), candidates passing RCS screening were scheduled directly for interview panels.
- **New Stakeholder Material:** Module II Diagram Step 13 introduces an explicit, mandatory governance gate: **"MANAGEMENT APPROVAL FOR INTERVIEW: Shortlisted candidates' information routed to Management for approval"** prior to scheduling interviews.
- **Analysis:** This adds an additional approval step in both Academic and Non-Academic recruitment pipelines, preventing recruiters from issuing interview invitations without prior executive Management sign-off.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Confirm whether Management Approval for Interview is an institutional requirement for all positions or only senior/specific cadres.

#### Conflict 4: Decision Sequence Post-SCM (Step 14A)
- **Earlier Baseline:** SCM Digital Scoring Matrix was compiled and submitted to Management for appointment approval (`REQ-MOD2-14`).
- **New Stakeholder Material:** Step 14A shows: Evaluators record marks $\rightarrow$ System compiles evaluation matrix $\rightarrow$ **HR recommendation** $\rightarrow$ **Management recommendation and cost approval** $\rightarrow$ System generates LOI.
- **Analysis:** The new material introduces an explicit **HR recommendation** review between the Selection Committee scoring and final Management cost approval.
- **Recommendation:** **NEEDS STAKEHOLDER CONFIRMATION.** Confirm the inclusion of the interim HR recommendation step post-SCM.

---

## 10. New & Clarified Open Decisions (TBD)

The new stakeholder materials explicitly forbid software developers from inventing institutional policies, validation thresholds, or resolution algorithms. The following items must be integrated into the official TBD register:

| TBD Candidate ID | Domain | Topic & Stakeholder Statement | Status & Scope |
|---|---|---|---|
| **`REQ-TBD-12`** | Module I | **Simultaneous & Conflicting Change Request Resolution Policy:** Narrative explicitly states that when two changes are submitted around the same time for the same employee, developers must not assume "latest wins". | **`[E] TBD`** — University policy must define priority rules, concurrency locking, or HR arbitration procedures. |
| **`REQ-TBD-13`** | Module I | **Change Request Cancellation & Withdrawal Authority:** Diagram Box 12 states cancellation/withdrawal "may be allowed as per policy". | **`[E] TBD`** — Institutional rules governing who can cancel a request (initiator vs. HR) and up to which approval stage. |
| **`REQ-TBD-14`** | Module I | **Reason Taxonomy for Clarification & Rejection:** Narrative paragraph 20 states the requirement does not specify every possible reason for returning or rejecting a request. | **`[E] TBD`** — University HR must provide standardized dropdown reason codes for rejection and clarification. |
| **`REQ-TBD-15`** | Module II | **Automated Qualification & Experience Shortlisting Thresholds:** Narrative paragraph 22 states that qualification/experience screening is required, but developers must not invent scoring formulas or auto-rejection rules. | **`[E] TBD`** — Definition of strict vs. advisory screening filters and UGC norm evaluation algorithms. |
| **`REQ-TBD-16`** | Module II | **Pre-Onboarding Milestone Exception Handling Rules:** Narrative paragraph 50 notes that candidates with notice period extensions, delayed verification, or no-show risks require tracking, but exception outcomes must be defined by HR. | **`[E] TBD`** — Rules governing offer revocation, notice period extension caps, and waitlist activation timelines. |

---

## 11. Impact Matrix: Comprehensive Delta Catalogue

The following consolidated matrix details all 22 material items identified from the new stakeholder materials:

| Delta ID | Module | Stakeholder Source | Step / Section | New Requirement / Clarification Description | Existing Documentation Status | Analytical Classification | Impact Level | Affected Baseline Documents | Recommended Governance Action | TBD Required? |
|---|---|---|---|---|---|---|---|---|---|---|
| **`DLT-M1-01`** | Mod I | Diagram & Narrative | Box 3, Para 16 | System Validation at Submission: Checks mandatory fields, data format, effective date rules, and pending change conflicts. | Partial (`MOD1-CHG-REQ-12`) | **NEW EXPLICIT REQUIREMENT** | **MEDIUM** | `01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`, `02-MODULE-I-BUSINESS-PROCESSES.md` | Add formal functional validation requirements to Module I. | No |
| **`DLT-M1-02`** | Mod I | Diagram | Box 4 & Box 12 | Clarification Loop at HR Review: HR can return request to initiator with comments for resubmission. | Covered in narrative; explicit visual loop | **CLARIFICATION** | **LOW** | `02-MODULE-I-BUSINESS-PROCESSES.md` (`BP-M1-005`) | Refine `BP-M1-005` to explicitly document clarification loop state. | No |
| **`DLT-M1-03`** | Mod I | Diagram | Box 5 & Box 12 | Clarification Loop at Management Review: Management can return request to HR with comments. | Not explicit in baseline | **CLARIFICATION** | **LOW** | `02-MODULE-I-BUSINESS-PROCESSES.md` (`BP-M1-006`) | Add return-to-HR path in `BP-M1-006`. | No |
| **`DLT-M1-04`** | Mod I | Diagram | Box 6 & 7 | Intermediate Statuses: "Approved (Yet to be Effective)" and "Scheduled". | Semantics covered; terms informal | **CLARIFICATION** | **LOW** | `02-MODULE-I-BUSINESS-PROCESSES.md` (`BP-M1-007`), State Machine ADR | Standardize state machine labels to match stakeholder terminology. | No |
| **`DLT-M1-05`** | Mod I | Diagram & Narrative | Box 12, Para 56–63 | Multiple / Conflicting Changes: Handling of simultaneous change requests for the same employee without arbitrary overwrites. | Cautioned in Phase 2; no rule defined | **TBD / INCOMPLETE** | **HIGH** | `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`, `01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md` | Register `REQ-TBD-12`; require stakeholder policy confirmation. | **YES (`REQ-TBD-12`)** |
| **`DLT-M1-06`** | Mod I | Diagram & Narrative | Box 12, Para 63 | Cancellation / Withdrawal Policy: Ability to cancel in-flight request prior to approval. | Not explicitly catalogued | **TBD / INCOMPLETE** | **MEDIUM** | `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`, `02-MODULE-I-BUSINESS-PROCESSES.md` | Register `REQ-TBD-13`; define withdrawal permissions with HR. | **YES (`REQ-TBD-13`)** |
| **`DLT-M1-07`** | Mod I | Narrative | Para 20 | Return / Rejection Reason Taxonomy: Standardized reason tracking for returned or rejected requests. | Baseline captured reason field | **TBD / INCOMPLETE** | **LOW** | `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md` | Register `REQ-TBD-14`; solicit standard HR reason codes. | **YES (`REQ-TBD-14`)** |
| **`DLT-M1-08`** | Mod I | Diagram | Box 2 | Authorized Initiator Scope: "HR / Admin / Department as per policy". | Baseline assigned initiation to HR | **CLARIFICATION** | **MEDIUM** | `01-BUSINESS-PROCESS-FRAMEWORK.md`, `02-MODULE-I-BUSINESS-PROCESSES.md` | Clarify initiator role permissions in Actor Matrix. | No |
| **`DLT-M1-09`** | Mod I | Diagram | Box 14, Para 68–70 | Configurable Reporting: HR provides formats; dynamic add/delete of report definitions. | Covered in `BP-M1-010` | **ALREADY COVERED** | **NONE** | None | Reaffirms baseline dynamic reporting design. | No |
| **`DLT-M2-01`** | Mod II | Diagram & Narrative | Step 1, Para 5 | Academic Planning Initiation by Associate Dean (Academics): Communicates to Deans; Deans assess workload. | Baseline cited HR/Deans | **NEW EXPLICIT REQUIREMENT** | **MEDIUM** | `02-REQUIREMENT-CATALOGUE.md`, `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-ACAD-001`) | Add Associate Dean (Academics) to actor taxonomy and planning process. | Needs Confirmation |
| **`DLT-M2-02`** | Mod II | Diagram & Narrative | Step 1, 2, 6, 14A | Scope Classification: Lab Technician placed under Academic Track alongside Faculty. | Technicians assumed non-academic | **POTENTIAL CONFLICT** | **HIGH** | `03-SCOPE-AND-BOUNDARIES.md`, `03-MODULE-II-BUSINESS-PROCESSES.md` | Seek stakeholder confirmation on Lab Technician evaluation track. | Needs Confirmation |
| **`DLT-M2-03`** | Mod II | Diagram & Narrative | Step 2, Para 8 | Vetting Authority Split: Associate Dean (Academics) vets Faculty & Lab Tech; Head HR vets Non-Faculty. | Baseline assigned vetting to HR | **POTENTIAL CONFLICT** | **HIGH** | `02-REQUIREMENT-CATALOGUE.md`, `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-ACAD-003`) | Seek confirmation on HR vs. Associate Dean academic vetting authority. | Needs Confirmation |
| **`DLT-M2-04`** | Mod II | Diagram | Step 2 | Vetting Clarification Loop: Vetting authority can return requisition for additional information. | Implicit in administrative reviews | **CLARIFICATION** | **LOW** | `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-ACAD-003`) | Add explicit clarification loop to manpower vetting process. | No |
| **`DLT-M2-05`** | Mod II | Diagram | Step 3 | Joint Consolidation: Associate Dean (Academics) / Head HR consolidates requirements. | Baseline assigned consolidation to HR | **CLARIFICATION** | **LOW** | `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-ACAD-004`) | Update consolidation actor description. | No |
| **`DLT-M2-06`** | Mod II | Diagram | Step 6 | MRF Generation Asymmetry: Faculty MRF raised by Dean post-approval; Non-Faculty MRF raised upfront. | Baseline treated MRF generation uniformly | **CLARIFICATION** | **MEDIUM** | `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-ACAD-006`, `BP-M2-NACAD-002`) | Document distinct MRF origination points for Academic vs. Non-Academic. | No |
| **`DLT-M2-07`** | Mod II | Diagram | Step 5A | Urgent MRF Fast-Track Governance: Requires Vetting (Associate Dean / Head HR) and Pro-Chancellor approval. | `BP-M2-URG-001` covered Dean trigger | **CLARIFICATION** | **MEDIUM** | `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-URG-001`) | Incorporate fast-track vetting and Pro-Chancellor approval into urgent MRF. | No |
| **`DLT-M2-08`** | Mod II | Diagram | Step 9 | Sourcing Ingestion Scope: Explicit inclusion of Internshala (internships), Instagram, Facebook. | Covered multi-channel generally | **CLARIFICATION** | **LOW** | `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-TRK-001`) | Add Internshala and specific social channels to sourcing catalogue. | No |
| **`DLT-M2-09`** | Mod II | Narrative | Para 22 | Screening Disqualification TBD: System must not auto-reject candidates without defined business rules. | Baseline flagged weights as TBD | **TBD / INCOMPLETE** | **MEDIUM** | `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md` | Register `REQ-TBD-15`; define qualification screening thresholds. | **YES (`REQ-TBD-15`)** |
| **`DLT-M2-10`** | Mod II | Diagram | Step 13 | Management Approval for Interview: Mandatory executive sign-off on shortlisted candidates before interview scheduling. | Not in earlier baseline | **NEW EXPLICIT REQUIREMENT** | **HIGH** | `02-REQUIREMENT-CATALOGUE.md`, `03-MODULE-II-BUSINESS-PROCESSES.md`, `02-MODULE-II-FUNCTIONAL-REQS.md` | Add formal governance gate Step 13 across Academic & Non-Academic tracks. | Needs Confirmation |
| **`DLT-M2-11`** | Mod II | Diagram & Narrative | Step 14A, Para 30 | Online Interview Scheduling as Default: Offline mode if deemed necessary. | Offline assumed default in statutes | **CLARIFICATION** | **LOW** | `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-ACAD-008`) | Explicitly support digital/online interview panel scheduling. | No |
| **`DLT-M2-12`** | Mod II | Diagram | Step 14A | Post-SCM HR Recommendation: Explicit HR recommendation step between SCM evaluation and Management cost approval. | Matrix went directly to Management | **NEW EXPLICIT REQUIREMENT** | **MEDIUM** | `03-MODULE-II-BUSINESS-PROCESSES.md` (`BP-M2-ACAD-010`) | Add HR Recommendation step post-SCM before final Management approval. | Needs Confirmation |
| **`DLT-M2-13`** | Mod II | Diagram & Narrative | Step 18, Para 48–50 | Pre-Onboarding 5-Stage Milestone Tracking: Offer acceptance, Notice period, Verification, Joining, Onboarding. | General tracking in `BP-M2-ACAD-012` | **NEW EXPLICIT REQUIREMENT** | **MEDIUM** | `02-REQUIREMENT-CATALOGUE.md`, `03-MODULE-II-BUSINESS-PROCESSES.md` | Formalize 5 pre-onboarding tracking stages and register `REQ-TBD-16` for exceptions. | **YES (`REQ-TBD-16`)** |

---

## 12. Document Impact Analysis

The following table assesses the extent of impact across all system documentation layers:

| Documentation Layer / File Group | Impact Assessment | Summary of Direct / Indirect Implications |
|---|---|---|
| **`docs/01-requirements/`** (Phase 1 Baseline) | **DIRECT IMPACT** | - `01-PROJECT-REQUIREMENTS-SPECIFICATION.md`: Add Associate Dean (Academics) role, Step 13 Management Interview Approval, Lab Technician academic scope.<br>- `02-REQUIREMENT-CATALOGUE.md`: Formulate candidate requirement IDs for Step 13, pre-validation checks, and pre-onboarding milestones.<br>- `03-SCOPE-AND-BOUNDARIES.md`: Clarify Lab Technician placement under Academic track.<br>- `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`: Add 5 new TBD items (`REQ-TBD-12` to `REQ-TBD-16`).<br>- `06-REQUIREMENTS-QUALITY-REVIEW.md`: Reconcile requirement counts upon baseline update. |
| **`docs/02-business-process/`** (Phase 2 Baseline) | **DIRECT IMPACT** | - `01-BUSINESS-PROCESS-FRAMEWORK.md`: Add Associate Dean to Actor Taxonomy.<br>- `02-MODULE-I-BUSINESS-PROCESSES.md`: Incorporate pre-validation rules, clarification loops, and 7 explicit exception conditions into `BP-M1-004`–`007`.<br>- `03-MODULE-II-BUSINESS-PROCESSES.md`: Restructure `BP-M2-ACAD-001`–`012` and `BP-M2-NACAD-001`–`007` to incorporate Associate Dean, Lab Technician, Step 13 Management Interview Approval, post-SCM HR recommendation, and 5-stage pre-onboarding milestones.<br>- `06-BUSINESS-RULES-AND-DECISION-POINTS.md`: Add business rules for Step 13, Lab Technician, and validation rules.<br>- `07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md`: Add SLA commitments for Step 13 and clarification loops. |
| **`docs/03-functional-requirements/`** (Phase 3 Baseline) | **DIRECT IMPACT** | - `01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`: Add submission validation rules (`MOD1-VAL-REQ-*`) and clarification workflow states.<br>- `02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`: Add functional specifications for Step 13 (`MOD2-INTAPP-REQ-*`) and 5-stage pre-onboarding tracker (`MOD2-PREONB-REQ-*`). |
| **`TECHNOLOGY_ARCHITECTURE_BASELINE.md`** & **ADRs** | **INDIRECT IMPACT** | - State machine architectures for change requests and candidate applications must accommodate new intermediate states: `CLARIFICATION_REQUIRED`, `MGMT_INTERVIEW_APPROVAL_PENDING`, `APPROVED_YET_EFFECTIVE`.<br>- No fundamental tech stack changes (PostgreSQL, NestJS, Next.js baseline remains 100% valid). |
| **Future Workflows (`docs/06-workflows/`)** | **DIRECT IMPACT** | Future Phase 6 workflow documentation will directly model the 15-stage Module I workflow and 21-stage Module II recruitment workflow. |

---

## 13. Traceability Impact & Candidate Requirement Identifiers

To preserve rigorous traceability without prematurely mutating the approved 104-requirement catalogue, the new items are provisionally assigned **Candidate Traceability Identifiers**:

| Candidate Requirement ID | Descriptive Title | Mapped Business Process Target | Mapped Functional Requirement Target | Classification |
|---|---|---|---|---|
| `CAND-REQ-M1-VAL` | Pre-Submission Multi-Factor System Validation Checks | `BP-M1-004` (Step 3) | `MOD1-CHG-REQ-12` (Refined) | `[A]` Explicit Requirement |
| `CAND-REQ-M1-CLAR` | Bidirectional Clarification & Resubmission Workflow | `BP-M1-005`, `BP-M1-006` | `MOD1-APP-REQ-05` (New) | `[A]` Explicit Requirement |
| `CAND-REQ-M2-AD` | Associate Dean (Academics) Manpower Planning & Vetting Authority | `BP-M2-ACAD-001`, `003` | `MOD2-MPL-REQ-11` (New) | `[A]` Explicit (Pending Confirmation) |
| `CAND-REQ-M2-LT` | Academic Track Scope Inclusion of Lab Technician Cadre | `BP-M2-ACAD-001` to `012` | `MOD2-REC-REQ-02` (New) | `[A]` Explicit (Pending Confirmation) |
| `CAND-REQ-M2-INTAPP` | Mandatory Management Approval for Interview Scheduling (Step 13) | `BP-M2-ACAD-008`, `BP-M2-NACAD-006` | `MOD2-SEL-REQ-03` (New) | `[A]` Explicit (Pending Confirmation) |
| `CAND-REQ-M2-HRREC` | Post-SCM Institutional HR Recommendation Review | `BP-M2-ACAD-010` | `MOD2-SCM-REQ-03` (New) | `[A]` Explicit (Pending Confirmation) |
| `CAND-REQ-M2-PREONB`| Five-Stage Pre-Onboarding & Candidate Milestone Tracking | `BP-M2-ACAD-012`, `BP-M2-NACAD-007` | `MOD2-YTJ-REQ-02` (New) | `[A]` Explicit Requirement |

---

## 14. Special Evaluation of Previous Audit Declarations

The Phase 2 Completion Report stated:
1. *104 atomic requirements fully mapped.*
2. *0 unmapped requirements.*
3. *59 business processes complete.*
4. *0 inconsistencies found.*

### Are These Declarations Made Outdated by the New Material?
- **Regarding the 104 Atomic Requirements:** The 104 requirements established in Phase 1 were strictly derived from the three official PDFs. That count was mathematically accurate and complete with respect to the original PDFs. However, with the release of the new stakeholder narratives and workflow diagrams, **the claim that "104 requirements represent 100% of all stakeholder requirements" is now OUTDATED**. New explicit requirements (such as Step 13 Management Interview Approval, Lab Technician academic scope, and 5-stage pre-onboarding milestones) represent candidate additions to the requirements baseline.
- **Regarding the 59 Business Processes:** The 59 business processes established in Phase 2 remain structurally valid as the macro operational framework. However, the claim that the business processes represent the final, complete operational detail is now **SUBJECT TO PLANNED REVISION**. Specifically, existing processes (`BP-M1-004` to `007`, `BP-M2-ACAD-001`, `003`, `008`, `010`, `012`, and `BP-M2-NACAD-006`) require internal step expansions and governance refinements to incorporate the new stakeholder workflow steps.
- **Regarding 0 Inconsistencies:** The earlier baseline had zero internal contradictions against the original PDFs. However, the new stakeholder material introduces **four potential policy divergences** (Associate Dean vs. HR vetting, Lab Technician cadre placement, Step 13 pre-interview approval, and post-SCM HR recommendation) that must be formally confirmed by institutional stakeholders.

---

## 15. Recommended Controlled Change Sequence

To maintain enterprise document integrity and prevent unauthorized baseline drift, the following controlled change sequence is recommended:

```
 [1. NEW STAKEHOLDER MATERIAL RECEIVED]
                 │
                 ▼
 [2. DELTA & IMPACT ANALYSIS COMPLETED] (This Document: 07-STAKEHOLDER-REQUIREMENT-DELTA)
                 │
                 ▼
 [3. STAKEHOLDER REVIEW & CONFIRMATION] (Resolve 4 Potential Conflicts & 5 TBDs)
                 │
                 ▼
 [4. REQUIREMENT BASELINE UPDATE] (docs/01-requirements/ - Update Catalogue & TBDs)
                 │
                 ▼
 [5. AFFECTED BUSINESS PROCESS UPDATE] (docs/02-business-process/ - Refine Process Steps)
                 │
                 ▼
 [6. AFFECTED FUNCTIONAL REQUIREMENT UPDATE] (docs/03-functional-requirements/ - Update FRDs)
                 │
                 ▼
 [7. QUALITY AUDIT & RE-RECONCILIATION] (Verify New Requirement & Process Counts)
                 │
                 ▼
 [8. BASELINE FREEZE]
                 │
                 ▼
 [9. PROCEED TO NEXT DOCUMENTATION PHASE] (Phase 4: Database Schema Documentation)
```

---

## 16. Items Requiring Stakeholder Confirmation

Before any baseline updates are executed, institutional stakeholders must formally confirm the following four decisions:

1. **Confirmation Item 1 (Academic Vetting Role):** Does the **Associate Dean (Academics)** replace the HR Department as the primary vetting authority for academic manpower requisitions, or is academic vetting conducted *jointly* by Associate Dean (curriculum/workload) and HR (budget/cadre ratio)?
2. **Confirmation Item 2 (Lab Technician Cadre Alignment):** Is the **Lab Technician** position officially classified under the **Academic Track** (following Associate Dean vetting, Dean MRF raising, and Selection Committee interview), or should Lab Technicians follow the Non-Academic 3-round interview?
3. **Confirmation Item 3 (Management Approval for Interview - Step 13):** Is executive **Management Approval for Interview** mandatory for *all* shortlisted candidates across all positions before interviews can be scheduled, or is it reserved for specific senior tiers?
4. **Confirmation Item 4 (Post-SCM HR Recommendation):** Following Selection Committee evaluation, does the system route the scoring matrix to **HR for formal recommendation** before submission to Management for final cost approval?

---

## 17. Final Delta Summary & Quantitative Findings

| Metric / Dimension | Quantitative Finding | Status / Classification |
|---|---|---|
| **Total Material Items Analyzed** | **22 distinct items** | Catalogued in Section 11 Impact Matrix |
| **Already Covered Items** | **6 items** | Baseline completely aligned |
| **New Explicit Requirements** | **5 items** | Candidate IDs provisionally assigned |
| **Clarifications** | **8 items** | Operational details refined |
| **Potential Conflicts** | **3 items** | Documented in Section 9 (Awaiting confirmation) |
| **New Exceptions / Special Conditions** | **8 items** | 7 Module I exceptions + 1 Module II urgent MRF flow |
| **New / Clarified TBD Items** | **5 items** | `REQ-TBD-12` through `REQ-TBD-16` |
| **Affected Existing Document Groups** | **4 document layers** | `01-reqs`, `02-business-process`, `03-functional-reqs`, architecture |
| **Current 104-Requirement Baseline Status** | **Historically valid for PDFs; requires planned expansion** | New candidate requirements identified |
| **Current 59-Business Process Baseline Status**| **Structurally sound foundation; requires internal step updates** | Macro processes preserved; steps refined |
| **File Safety & Integrity** | **Zero existing files modified** | Strictly analysis-only execution |

---
*End of Document — Stakeholder Requirement Delta & Impact Analysis.*
