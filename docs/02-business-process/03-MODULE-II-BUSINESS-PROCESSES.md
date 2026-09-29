# Module II Business Processes — Recruitment & Selection Automation
## University HR Change Management & Automation System

**Document Identifier:** `DOC-02-BPM-03`  
**Phase:** Phase 2 — Business Process Documentation (Documentation-Only)  
**Location:** `docs/02-business-process/03-MODULE-II-BUSINESS-PROCESSES.md`  
**Status:** Approved Business Process Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Module Overview & Mandatory Track Segregation

Module II governs the end-to-end recruitment, selection, and pre-onboarding lifecycle across the University.

> [!IMPORTANT]
> **Strict Operational Separation of Academic and Non-Academic Tracks:**  
> In strict accordance with the authoritative Module II Requirement Brief (Section 1), the University mandates a **complete, uncompromising operational segregation** between:
> 1. **Academic Recruitment Track:** Governing Faculty members (Professors, Associate Professors, Assistant Professors), Teaching Associates, Technical Assistants, and Laboratory Technicians. Governed by advance semester planning (>= 4 months), teaching load calculations (Attachment 1), 3-month HR vetting, statutory Selection Committee Meetings (SCM) with external subject experts, and UGC compliance norms.
> 2. **Non-Academic Recruitment Track:** Governing administrative, clerical, operational, and support staff. Governed by annual manpower requisitions, strict departmental submission quotas (1 planned MRF per department per year), and a sequential 3-Round interview process (Round 1: Technical, Round 2: HR, Round 3: Management) evaluating Job Knowledge, Communication, and Attitude.
> 3. **Urgent Replacement Track:** Fast-track ad-hoc requisition process triggered strictly by a School Dean's acceptance of an employee resignation, bypassing annual planned quotas.

Under no circumstances are Academic and Non-Academic recruitment processes merged into a single generic workflow.

---

## 2. Itemized Business Process Directory

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                           MODULE II BUSINESS PROCESS INVENTORY                                   │
├───────────────────┬──────────────────────────────────────────────────┬───────────────────────────┤
│ Process ID        │ Process Name                                     │ Classification & Source   │
├───────────────────┼──────────────────────────────────────────────────┼───────────────────────────┤
│ **ACADEMIC**      │                                                  │                           │
│ `BP-M2-ACAD-001`  │ Academic Manpower Planning Advance Initiation    │ `[A]` Mod II Sec 1(a)     │
│ `BP-M2-ACAD-002`  │ Academic Requirement & Teaching Load Submission  │ `[A]` Mod II Sec 1(b)     │
│ `BP-M2-ACAD-003`  │ Academic Teaching Load Vetting & Consolidation   │ `[A]` Mod II Sec 1(c, d)  │
│ `BP-M2-ACAD-004`  │ Academic Consolidated Approval Gate (Pro-Chanc.) │ `[A]` Mod II Sec 1(e)     │
│ `BP-M2-ACAD-005`  │ Academic Recruitment Advertisement Launch        │ `[A]` Mod II Sec 1(f)     │
│ `BP-M2-ACAD-006`  │ Academic Multi-Channel Sourcing & Intake         │ `[A]` Mod II Sec 4        │
│ `BP-M2-ACAD-007`  │ Academic CV Screening & UGC Norms Compliance     │ `[A]` Mod II Sec 5        │
│ `BP-M2-ACAD-008`  │ Academic RCS & Pre-Interview Management Gate     │ `[A]` Mod II Sec 6, 7     │
│ `BP-M2-ACAD-009`  │ Statutory Selection Committee Meeting (SCM)      │ `[A]` Mod II Sel A(a-d)   │
│ `BP-M2-ACAD-010`  │ Academic Digital Scoring & Selection Matrix      │ `[A]` Mod II Sel A(c, d)  │
│ `BP-M2-ACAD-011`  │ Academic Letter of Intent (LOI) Issuance         │ `[A]` Mod II Sel A(e)     │
│ `BP-M2-ACAD-012`  │ Academic "Yet to Join" Pre-Onboarding Tracking   │ `[A]` Mod II Sel A(e)     │
├───────────────────┼──────────────────────────────────────────────────┼───────────────────────────┤
│ **NON-ACADEMIC**  │                                                  │                           │
│ `BP-M2-NACAD-001` │ Non-Academic Manpower Advance Initiation         │ `[A]` Mod II Sec 1(g)     │
│ `BP-M2-NACAD-002` │ Non-Academic Annual Requisition Restriction      │ `[A]` Mod II Sec 1(g)     │
│ `BP-M2-NACAD-003` │ Non-Academic Vetting, Consolidation & Approval   │ `[A]` Mod II Sec 1(g, h)  │
│ `BP-M2-NACAD-004` │ Non-Academic Recruitment Launch & Sourcing       │ `[A]` Mod II Sec 1(h), 4  │
│ `BP-M2-NACAD-005` │ Non-Academic CV Screening & RCS Pre-Interview    │ `[A]` Mod II Sec 5, 6, 7  │
│ `BP-M2-NACAD-006` │ Non-Academic Three-Round Sequential Selection    │ `[A]` Mod II Sel B(a)     │
│ `BP-M2-NACAD-007` │ Non-Academic Selection Decision & LOI Issuance   │ `[A]` Mod II Sel B(b)     │
├───────────────────┼──────────────────────────────────────────────────┼───────────────────────────┤
│ **URGENT & TRK**  │                                                  │                           │
│ `BP-M2-URG-001`   │ Urgent Replacement Recruitment (Resignation)     │ `[A]` Mod II Sec 1(i)     │
│ `BP-M2-TRK-001`   │ Central CV Database Ingestion & Deduplication    │ `[A]` Mod II Sec 4        │
│ `BP-M2-TRK-002`   │ Open Positions Tracker & Weekly Executive Brief  │ `[A]` Mod II Sec 2, 3     │
└───────────────────┴──────────────────────────────────────────────────┴───────────────────────────┘
```

---

## 3. Academic Recruitment Track (Processes 001–012)

### Process Identifier: BP-M2-ACAD-001
**Process Name:** Academic Manpower Planning Advance Initiation (>= 4 Months Prior)

1. **Module / Operational Track:** Module II — Academic Recruitment Track (Faculty, Teaching Associates, Technical Assistants, Lab Technicians).
2. **Business Purpose:** Initiate advance academic workforce planning sufficiently ahead of the academic semester to ensure zero teaching disruption.
3. **Operational Trigger:** Temporal calendar trigger reaching **at least four (4) months prior** to the commencement of the upcoming academic semester or academic year.
4. **Prerequisites & Entry Conditions:** Academic calendar established by Academic Council; semester start date officially recorded.
5. **Primary Actors:** Associate Dean (Initiator), School Deans (Recipients).
6. **Supporting Actors:** HR Department (Facilitator).
7. **Business Inputs & Documentation:** Official academic calendar, projected student enrollments, curriculum revisions, current faculty rosters.
8. **Sequential Business Activities:**
   - Step 1: System detects calendar milestone (>= 4 months before semester commencement).
   - Step 2: Associate Dean issues formal academic manpower planning call to all School Deans.
   - Step 3: Deans are provided standardized manpower request forms and teaching load calculation templates (Attachment 1).
   - Step 4: System starts a strict 15-day submission countdown timer.
9. **Decision Points & Evaluation Rules:** Verification of eligible academic units requiring manpower assessments.
10. **Approval Points & Governance Gates:** Call authorized by Associate Dean in accordance with statutory academic governance.
11. **Institutional Outputs & Deliverables:** Formal Manpower Planning Call distributed to School Deans with attached Enclosure 2 (Attachment 1).
12. **Operational SLA & Business Deadlines:** Initiated >= 4 months before semester start (`REQ-MOD2-02`, `REQ-SLA-01`).
13. **Reminders, Escalations & Lockouts:** Automated reminders sent to Deans as the 15-day window elapses.
14. **Exception Handling & Alternate Paths:** Unresponsive schools escalate to the Vice Chancellor's office.
15. **Cross-Module Interactions & Handoffs:** Consumes active departmental faculty rosters from Module I (`BP-XMOD-003`).
16. **Process Completion Criteria:** Planning call formally dispatched to all School Deans with active tracking.
17. **Audit & Compliance Requirements:** Dispatch timestamp, recipient list, and semester reference recorded.
18. **Authoritative Source References:** Module II Brief, Section 1(a); [`REQ-MOD2-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-01`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-ACAD-002
**Process Name:** Academic Requirement Submission & Teaching Load Calculation (15 Days)

1. **Module / Operational Track:** Module II — Academic Recruitment Track.
2. **Business Purpose:** Capture granular, evidence-based academic staffing requirements justified by curriculum teaching loads and laboratory session allocations.
3. **Operational Trigger:** Receipt of the Manpower Planning Call from Associate Dean (`BP-M2-ACAD-001`).
4. **Prerequisites & Entry Conditions:** Active academic planning window; accessible Attachment 1 template.
5. **Primary Actors:** School Deans (Submitting Authority).
6. **Supporting Actors:** Department Heads, Program Coordinators.
7. **Business Inputs & Documentation:** Attachment 1 (Teaching Load Calculation Sheet), subject-wise lecture hours, tutorial hours, practical/lab contact hours, student-faculty ratio targets.
8. **Sequential Business Activities:**
   - Step 1: School Dean collates departmental teaching loads across all academic programs.
   - Step 2: Dean calculates total contact hours per discipline against statutory UGC faculty workload norms.
   - Step 3: Dean compiles requested faculty positions by specialization, rank (Professor, Associate Professor, Assistant Professor), and technical support roles (Lab Techs).
   - Step 4: Dean signs and submits completed requirements along with Attachment 1 within the mandatory 15-day window.
9. **Decision Points & Evaluation Rules:** Verification that requested positions strictly correspond to demonstrable teaching load deficits.
10. **Approval Points & Governance Gates:** Formal submission sign-off executed by School Dean.
11. **Institutional Outputs & Deliverables:** Submitted School Manpower Dossier including completed Attachment 1 and position justification narrative.
12. **Operational SLA & Business Deadlines:** Mandatory submission within **fifteen (15) days** of receipt (`REQ-MOD2-03`, `REQ-SLA-02`).
13. **Reminders, Escalations & Lockouts:** Daily countdown reminders dispatched during final 5 days; overdue submissions escalated to Associate Dean.
14. **Exception Handling & Alternate Paths:** Late submissions require formal extension request endorsed by Vice Chancellor.
15. **Cross-Module Interactions & Handoffs:** Routes submitted teaching load dossiers to HR Department for vetting (`BP-M2-ACAD-003`).
16. **Process Completion Criteria:** Formal receipt and logging of completed Attachment 1 by HR Department.
17. **Audit & Compliance Requirements:** Submitted files, contact hour calculations, and submission timestamps archived.
18. **Authoritative Source References:** Module II Brief, Section 1(b); [`REQ-MOD2-03`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Attachment 1 standardized schema is classified under `REQ-TBD-02`.

---

### Process Identifier: BP-M2-ACAD-003
**Process Name:** Academic Teaching Load Vetting & Manpower Consolidation (3 Months)

1. **Module / Operational Track:** Module II — Academic Recruitment Track.
2. **Business Purpose:** Rigorously verify submitted teaching loads against regulatory norms, audit existing departmental allocations, and consolidate institutional academic hiring needs into standardized Manpower Requisition Forms (MRFs).
3. **Operational Trigger:** Receipt of submitted School Manpower Dossiers (`BP-M2-ACAD-002`).
4. **Prerequisites & Entry Conditions:** Completed Attachment 1 submissions from all constituent Schools.
5. **Primary Actors:** HR Department (Academic Vetting Desk / Head HR).
6. **Supporting Actors:** School Deans, Academic Registrar, Finance Department.
7. **Business Inputs & Documentation:** Submitted Attachment 1 sheets, UGC workload norms, current faculty deployment rosters, sanctioned post budgets.
8. **Sequential Business Activities:**
   - Step 1: HR conducts mathematical audit of submitted teaching loads over a structured **three (3) month vetting window**.
   - Step 2: HR reconciles contact hours against visiting faculty allocations and sabbatical leaves.
   - Step 3: HR conducts clarification sessions with Deans regarding disputed workload calculations.
   - Step 4: HR consolidates verified positions into **Enclosure 1 (Standardized MRF)** and **Enclosure 3 (Attachment 2 — Vacancy Specification Sheet)**.
   - Step 5: HR completes institutional consolidation within a **15-day consolidation window** following vetting completion.
9. **Decision Points & Evaluation Rules:** Validation of student-faculty ratios; compliance with statutory UGC norms; budget availability check.
10. **Approval Points & Governance Gates:** Endorsement of consolidated academic hiring plan by Head of HR.
11. **Institutional Outputs & Deliverables:** Consolidated Institutional Academic Manpower Plan comprising formal MRFs (Enclosure 1) and Attachment 2.
12. **Operational SLA & Business Deadlines:** Vetting conducted over a 3-month window; consolidation finalized within 15 days (`REQ-MOD2-04`).
13. **Reminders, Escalations & Lockouts:** Milestone tracking ensures consolidation finishes >= 2 months prior to semester start.
14. **Exception Handling & Alternate Paths:** Unjustified position requests are excised or reduced following joint HR-Dean reconciliation.
15. **Cross-Module Interactions & Handoffs:** Submits consolidated dossier to Pro-Chancellor for executive approval (`BP-M2-ACAD-004`).
16. **Process Completion Criteria:** Finalized Academic MRF package signed by Head HR and ready for apex executive submission.
17. **Audit & Compliance Requirements:** Vetting adjustment logs, workload audit notes, and consolidation diffs archived.
18. **Authoritative Source References:** Module II Brief, Section 1(c, d); [`REQ-MOD2-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Enclosure 1 (MRF) and Attachment 2 field schemas are classified under `REQ-TBD-02`.

---

### Process Identifier: BP-M2-ACAD-004
**Process Name:** Academic Consolidated Approval Gate — Pro-Chancellor Turnaround (7 Days)

1. **Module / Operational Track:** Module II — Academic Executive Governance.
2. **Business Purpose:** Provide apex institutional governance and formal financial authorization for all consolidated academic hiring plans.
3. **Operational Trigger:** Submission of the Consolidated Academic Manpower Plan by HR (`BP-M2-ACAD-003`).
4. **Prerequisites & Entry Conditions:** Verified MRF package and Attachment 2 endorsed by Head HR.
5. **Primary Actors:** Pro-Chancellor (Apex Approving Authority).
6. **Supporting Actors:** Head HR, Vice Chancellor.
7. **Business Inputs & Documentation:** Consolidated Academic MRF package, teaching load summary, financial outlay estimate, school-by-school vacancy breakdowns.
8. **Sequential Business Activities:**
   - Step 1: Pro-Chancellor reviews consolidated institutional academic hiring dossier.
   - Step 2: Pro-Chancellor assesses strategic program priorities and overall university financial commitments.
   - Step 3: Pro-Chancellor executes formal determination within a strict **7-day turnaround time (TAT)**:
     - **Approve:** Formally sanctions the full academic hiring plan.
     - **Partial / Conditional Approval:** Sanctions specific positions while deferring others.
     - **Return / Reject:** Rejects plan with executive directives.
   - Step 4: Approval decision is officially communicated to HR within **seven (7) days**.
9. **Decision Points & Evaluation Rules:** Executive determination of institutional financial viability and strategic academic expansion goals.
10. **Approval Points & Governance Gates:** Mandatory Pro-Chancellor Approval Gate. No academic recruitment advertisement or selection may occur without this sign-off.
11. **Institutional Outputs & Deliverables:** Formally Approved Academic Manpower Plan; executive sanction memo.
12. **Operational SLA & Business Deadlines:** Mandatory **7-day turnaround time (TAT)** for Pro-Chancellor review and approval communication (`REQ-MOD2-05`, `REQ-SLA-03`).
13. **Reminders, Escalations & Lockouts:** Daily executive pending alerts delivered to Chancellor's Secretariat.
14. **Exception Handling & Alternate Paths:** Disapproved positions are archived with documented executive rationale.
15. **Cross-Module Interactions & Handoffs:** Triggers immediate Open Positions Tracker instantiation (`BP-M2-TRK-002`) and Advertisement Launch (`BP-M2-ACAD-005`).
16. **Process Completion Criteria:** Formal approval memo signed by Pro-Chancellor and received by HR.
17. **Audit & Compliance Requirements:** Executive signature, approval date, sanctioned position counts, and conditions permanently archived.
18. **Authoritative Source References:** Module II Brief, Section 1(e); [`REQ-MOD2-05`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-03`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-ACAD-005
**Process Name:** Academic Recruitment Advertisement Launch (7 Days Post-Approval)

1. **Module / Operational Track:** Module II — Sourcing Operations.
2. **Business Purpose:** Publicly announce sanctioned academic vacancies across designated media and digital channels to initiate candidate attraction.
3. **Operational Trigger:** Receipt of official Pro-Chancellor approval (`BP-M2-ACAD-004`).
4. **Prerequisites & Entry Conditions:** Formally sanctioned MRFs; approved vacancy specifications (Attachment 2).
5. **Primary Actors:** HR Department (Recruitment Desk).
6. **Supporting Actors:** Public Relations / Media Cell, School Deans.
7. **Business Inputs & Documentation:** Approved Attachment 2 (job descriptions, specializations, qualifications, experience criteria, UGC norms).
8. **Sequential Business Activities:**
   - Step 1: HR drafts advertisement copy aligning strictly with approved Attachment 2 specifications and statutory UGC requirements.
   - Step 2: HR books multi-channel media placements: national print newspapers, university careers portal, professional academic networks, and digital platforms.
   - Step 3: Advertisements are publicly launched within **seven (7) days** of receiving Pro-Chancellor approval.
   - Step 4: Target completion milestone: Entire recruitment lifecycle must be completed **at least one (1) month prior** to semester commencement.
9. **Decision Points & Evaluation Rules:** Verification of advertisement text compliance with statutory reservation policies and UGC minimum standards.
10. **Approval Points & Governance Gates:** Final sign-off on ad copy executed by Head HR.
11. **Institutional Outputs & Deliverables:** Published public recruitment notices; live job postings on University Careers Portal.
12. **Operational SLA & Business Deadlines:** Advertisement launched within **7 days** of approval; all hiring completed **>= 1 month before semester** (`REQ-MOD2-06`, `REQ-SLA-04`).
13. **Reminders, Escalations & Lockouts:** Daily countdown alerts tracking the 7-day launch window; escalation to Head HR if publication is delayed.
14. **Exception Handling & Alternate Paths:** Media agency delays trigger digital-first publishing on careers portal to preserve timeline.
15. **Cross-Module Interactions & Handoffs:** Opens candidate intake channels feeding Central CV Database (`BP-M2-ACAD-006`, `BP-M2-TRK-001`).
16. **Process Completion Criteria:** Advertisements confirmed live across target media channels.
17. **Audit & Compliance Requirements:** Published tear sheets, digital links, launch timestamps, and cost invoices archived.
18. **Authoritative Source References:** Module II Brief, Section 1(f); [`REQ-MOD2-06`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-SLA-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-ACAD-006
**Process Name:** Academic Multi-Channel Sourcing & CV Intake

1. **Module / Operational Track:** Module II — Candidate Ingestion.
2. **Business Purpose:** Ingest, parse, and centralize applicant dossiers from multiple recruitment channels into a single institutional repository.
3. **Operational Trigger:** Candidate application submitted via any supported channel.
4. **Prerequisites & Entry Conditions:** Active advertised academic vacancy in Open Positions Tracker (`BP-M2-TRK-002`).
5. **Primary Actors:** Candidates (Applicants), Recruiter / HR Intake Desk.
6. **Supporting Actors:** Third-Party Portal Administrators (Internshala, Job Boards).
7. **Business Inputs & Documentation:** Resumes/CVs, cover letters, published research papers, teaching statements, portfolio links arriving via:
   - Print media advertisement responses
   - University Careers Portal
   - Social media recruitment channels (LinkedIn, etc.)
   - Dedicated email inbox
   - Internal employee referrals
   - Internshala / Academic internship portals
8. **Sequential Business Activities:**
   - Step 1: System captures applicant submission regardless of entry channel.
   - Step 2: System extracts core candidate metadata (name, email, contact number, highest qualification, total experience, current institution).
   - Step 3: Deduplication check executed against Central CV Database (`BP-M2-TRK-001`).
   - Step 4: Candidate profile instantiated and tagged to the target Academic MRF position.
9. **Decision Points & Evaluation Rules:** Deduplication logic (matching primary email and mobile number to prevent duplicate candidate dossiers).
10. **Approval Points & Governance Gates:** Automated ingestion verification.
11. **Institutional Outputs & Deliverables:** Centralized candidate dossier archived in Central CV Database.
12. **Operational SLA & Business Deadlines:** Ingestion and profile tagging completed within 24 hours of application receipt.
13. **Reminders, Escalations & Lockouts:** Unparsed or corrupted resume files alert recruitment desk for manual indexing.
14. **Exception Handling & Alternate Paths:** Unsolicited applications indexed into generic talent pool for future requisition matching.
15. **Cross-Module Interactions & Handoffs:** Feeds candidate pool to Academic Screening (`BP-M2-ACAD-007`).
16. **Process Completion Criteria:** Candidate record confirmed active in Central CV Database.
17. **Audit & Compliance Requirements:** Sourcing channel attribution, submission timestamp, and original document checksum preserved.
18. **Authoritative Source References:** Module II Brief, Section 4; [`REQ-MOD2-11`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-ACAD-007
**Process Name:** Academic CV Screening & UGC Norms Compliance

1. **Module / Operational Track:** Module II — Compliance & Screening.
2. **Business Purpose:** Filter, classify, and shortlist academic applicants against mandatory statutory UGC qualification criteria, experience thresholds, and departmental specializations.
3. **Operational Trigger:** Candidate profile indexed in Central CV Database for an active vacancy (`BP-M2-ACAD-006`).
4. **Prerequisites & Entry Conditions:** Structured candidate profile with verified educational credentials.
5. **Primary Actors:** HR Department (Recruitment Desk / Screening Specialist).
6. **Supporting Actors:** School Dean, Department Head.
7. **Business Inputs & Documentation:** Candidate CV, educational qualifications, Ph.D. status, NET/SLET certifications, publication counts, statutory UGC minimum qualification regulations.
8. **Sequential Business Activities:**
   - Step 1: System evaluates candidate data against statutory UGC norms:
     - Assistant Professor: Master's degree (55% or equivalent) + NET/SLET or Ph.D.
     - Associate Professor: Ph.D. + 8 years experience + minimum publication threshold.
     - Professor: Ph.D. + 10 years experience + research guidance threshold.
   - Step 2: System segregates candidates into compliance categories:
     - **Eligible (UGC Compliant):** Meets all statutory norms and position specializations.
     - **Ineligible / Rejected:** Fails mandatory statutory degrees or minimum experience.
     - **Borderline / Requires Review:** Foreign qualifications or interdisciplinary degrees requiring Dean review.
   - Step 3: School Dean reviews borderline candidates for departmental relevance.
   - Step 4: Shortlisted pool advances to Recruiter Calling Stage (`BP-M2-ACAD-008`).
9. **Decision Points & Evaluation Rules:** Strict statutory binary check: Does candidate possess UGC-mandated qualifications? Does specialization match MRF requirements?
10. **Approval Points & Governance Gates:** Screening sign-off executed by HR Screening Specialist and endorsed by School Dean.
11. **Institutional Outputs & Deliverables:** Verified Academic Shortlist; automated rejection communication dispatched to non-compliant applicants.
12. **Operational SLA & Business Deadlines:** Screening executed within 5 business days of application pool milestone.
13. **Reminders, Escalations & Lockouts:** Unreviewed candidate dossiers alert screening desk.
14. **Exception Handling & Alternate Paths:** Highly distinguished industry experts lacking standard academic degrees routed for special "Professor of Practice" policy determination where permitted.
15. **Cross-Module Interactions & Handoffs:** Advances compliant candidates to Recruiter Calling Stage (`BP-M2-ACAD-008`).
16. **Process Completion Criteria:** Candidate formally tagged as `SHORTLISTED_FOR_RCS` or `REJECTED_UGC_NON_COMPLIANT`.
17. **Audit & Compliance Requirements:** Reason for rejection documented; UGC compliance verification checklist archived.
18. **Authoritative Source References:** Module II Brief, Section 5; [`REQ-MOD2-12`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-ACAD-008
**Process Name:** Academic Recruiter Calling Stage (RCS) & Pre-Interview Management Gate

1. **Module / Operational Track:** Module II — Telephonic Screening & Executive Gate.
2. **Business Purpose:** Conduct structured preliminary telephonic interviews to verify candidate availability, communication competence, and compensation expectations, followed by mandatory executive pre-approval before scheduling interviews.
3. **Operational Trigger:** Candidate successfully passes UGC screening (`BP-M2-ACAD-007`).
4. **Prerequisites & Entry Conditions:** Candidate in `SHORTLISTED_FOR_RCS` status.
5. **Primary Actors:** Recruiter (Interviewer), HOD-HR (Reviewer), Senior Management (Pre-Approval Authority).
6. **Supporting Actors:** Candidate.
7. **Business Inputs & Documentation:** Standardized Recruiter Calling Sheet (RCS), candidate CV, vacancy salary parameters.
8. **Sequential Business Activities:**
   - Step 1: Recruiter contacts candidate and completes structured RCS evaluation:
     - Verifying willingness to relocate to university campus.
     - Documenting notice period and earliest date of joining.
     - Documenting current compensation and salary expectations.
     - Evaluating spoken communication clarity and professional demeanor.
     - Logging qualitative remarks in the digital RCS.
   - Step 2: HOD-HR reviews compiled RCS remarks and candidate dossier.
   - Step 3: HOD-HR submits shortlisted candidates with RCS notes to **Management for formal pre-approval**.
   - Step 4: Management reviews the dossier and signs off on inviting candidate to the statutory Selection Committee Meeting (SCM).
9. **Decision Points & Evaluation Rules:** Management pre-approval check: Does candidate salary expectation fit institutional budget? Are RCS ratings satisfactory?
10. **Approval Points & Governance Gates:** Mandatory Management Pre-Approval Gate (`REQ-MOD2-14`). Candidates **cannot** be scheduled for SCM without explicit Management sign-off on the RCS.
11. **Institutional Outputs & Deliverables:** Completed, signed digital RCS; Management-approved candidate list ready for SCM scheduling.
12. **Operational SLA & Business Deadlines:** RCS completed within 3 days of shortlisting; Management review within 3 days of submission.
13. **Reminders, Escalations & Lockouts:** Delinquent RCS reviews alert HOD-HR.
14. **Exception Handling & Alternate Paths:** Candidates exceeding salary thresholds flagged for special executive budget clearance.
15. **Cross-Module Interactions & Handoffs:** Advances approved candidates to Statutory SCM Selection (`BP-M2-ACAD-009`).
16. **Process Completion Criteria:** Formal Management sign-off logged on candidate RCS profile.
17. **Audit & Compliance Requirements:** Complete RCS logs, interviewer identity, and Management pre-approval decision archived.
18. **Authoritative Source References:** Module II Brief, Sections 6 and 7; [`REQ-MOD2-13`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD2-14`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** RCS standardized schema is classified under `REQ-TBD-02`.

---

### Process Identifier: BP-M2-ACAD-009
**Process Name:** Statutory Selection Committee Meeting (SCM) & External Expert Participation

1. **Module / Operational Track:** Module II — Statutory Academic Selection.
2. **Business Purpose:** Conduct rigorous statutory academic interview evaluations adhering strictly to University statutes and UGC governance requirements, incorporating independent external subject expertise.
3. **Operational Trigger:** Candidate passes Management RCS pre-approval (`BP-M2-ACAD-008`).
4. **Prerequisites & Entry Conditions:** SCM date scheduled; external expert confirmed; statutory panel constituted.
5. **Primary Actors:** Statutory Selection Committee (SCM) Panel:
   - Vice Chancellor (Chairperson)
   - School Dean
   - Department Head (HOD)
   - External Subject Expert (Mandatory independent specialist from outside institution)
6. **Supporting Actors:** HR Secretary / Coordinator, Candidate.
7. **Business Inputs & Documentation:** Candidate academic dossier, research publications, teaching portfolio, SCM interview scorecard, UGC compliance certificate.
8. **Sequential Business Activities:**
   - Step 1: System issues secure digital invitations to SCM panel members, including time-limited secure access for the External Subject Expert (`REQ-EXT-05`).
   - Step 2: SCM convenes; candidate presents research seminar, teaching demonstration, and participates in academic viva.
   - Step 3: Each panel member (including External Expert) independently evaluates candidate performance across prescribed statutory dimensions: Domain Knowledge, Research Quality/Potential, Pedagogical Competence, and Institutional Fit.
   - Step 4: External Subject Expert enters independent evaluations and remarks.
   - Step 5: Chairperson compiles committee recommendations.
9. **Decision Points & Evaluation Rules:** Statutory quorum verification; independent assessment by External Expert.
10. **Approval Points & Governance Gates:** Formal committee sign-off. The presence and evaluation of the External Subject Expert is a mandatory statutory requirement for faculty appointment validity.
11. **Institutional Outputs & Deliverables:** Individual panel evaluation sheets; signed SCM Committee Recommendation Minutes.
12. **Operational SLA & Business Deadlines:** SCM scheduled and executed within 15 days of Management RCS pre-approval.
13. **Reminders, Escalations & Lockouts:** Invitation reminders dispatched to panel members 48h and 24h prior to meeting.
14. **Exception Handling & Alternate Paths:** Inability of External Expert to attend mandates rescheduling; statutory faculty appointments cannot proceed without external representation.
15. **Cross-Module Interactions & Handoffs:** Passes individual score sheets to Digital Scoring & Selection Matrix Compilation (`BP-M2-ACAD-010`).
16. **Process Completion Criteria:** SCM proceedings concluded and all individual scoring sheets digitally submitted.
17. **Audit & Compliance Requirements:** SCM constitution memo, external expert affiliation records, attendance signatures, and scoring sheets archived permanently for UGC/NAAC compliance.
18. **Authoritative Source References:** Module II Brief, Selection A(a–d); [`REQ-MOD2-15`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-EXT-05`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** External expert secure access mechanism is classified under `REQ-TBD-07(b)`; statutory committee quorum specifications are classified under `REQ-TBD-04`.

---

### Process Identifier: BP-M2-ACAD-010
**Process Name:** Academic Digital Scoring & Selection Matrix Compilation

1. **Module / Operational Track:** Module II — Evaluation Synthesis.
2. **Business Purpose:** Systematically aggregate digital marks from all SCM panel members into an authoritative Selection Matrix for final executive appointment decisions.
3. **Operational Trigger:** Conclusion of SCM candidate interviews (`BP-M2-ACAD-009`).
4. **Prerequisites & Entry Conditions:** Completed digital scorecards from all participating SCM panel members.
5. **Primary Actors:** HR Department (Recruitment Desk), Senior Management (Final Approving Authority).
6. **Supporting Actors:** Selection Committee Members.
7. **Business Inputs & Documentation:** Digital score entries from VC, Dean, HOD, and External Expert; candidate compensation expectations; sanctioned salary range from MRF.
8. **Sequential Business Activities:**
   - Step 1: System aggregates individual panel marks across evaluated academic parameters.
   - Step 2: System compiles the formal **Selection Matrix** detailing candidate rank-order, individual interviewer marks, external expert qualitative endorsement, and recommended salary.
   - Step 3: Selection Matrix is submitted to **Senior Management** for final appointment and compensation authorization.
   - Step 4: Management reviews the matrix and executes final selection determination:
     - **Selected:** Candidate approved for offer issuance at designated salary.
     - **Waitlisted:** Candidate designated as reserve in event primary candidate declines.
     - **Rejected:** Candidate not selected.
9. **Decision Points & Evaluation Rules:** Verification of minimum passing threshold; executive salary approval within sanctioned band.
10. **Approval Points & Governance Gates:** Apex Management Appointment Approval Gate. Legally authorizes the issuance of employment offer.
11. **Institutional Outputs & Deliverables:** Final Approved Academic Selection Matrix; official appointment authorization record.
12. **Operational SLA & Business Deadlines:** Matrix compiled within 24 hours of SCM; Management determination within 48 hours.
13. **Reminders, Escalations & Lockouts:** Pending matrices alert Chancellor's Secretariat.
14. **Exception Handling & Alternate Paths:** If selected candidate's salary demand exceeds MRF sanction, special executive compensation waiver is required.
15. **Cross-Module Interactions & Handoffs:** Selected candidate record advances to Letter of Intent (LOI) Issuance (`BP-M2-ACAD-011`).
16. **Process Completion Criteria:** Formal Management signature on Selection Matrix approving candidate hiring.
17. **Audit & Compliance Requirements:** Raw scorecards, compilation formulas, and executive sign-off permanently preserved.
18. **Authoritative Source References:** Module II Brief, Selection A(c, d); [`REQ-MOD2-16`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Scoring dimension percentage weights are classified under `REQ-TBD-04`.

---

### Process Identifier: BP-M2-ACAD-011
**Process Name:** Academic Letter of Intent (LOI) Generation & Issuance

1. **Module / Operational Track:** Module II — Offer Administration.
2. **Business Purpose:** Generate and issue the official institutional Letter of Intent (LOI) populated with approved compensation, designation, and reporting parameters upon Management authorization.
3. **Operational Trigger:** Senior Management approval of Selection Matrix (`BP-M2-ACAD-010`).
4. **Prerequisites & Entry Conditions:** Selected candidate in `APPROVED_FOR_OFFER` status with authorized compensation structure.
5. **Primary Actors:** HR Department (Offer Desk / Head HR).
6. **Supporting Actors:** Candidate (Recipient).
7. **Business Inputs & Documentation:** Approved Selection Matrix, standardized LOI template, candidate personal details, salary breakup, reporting date expectations.
8. **Sequential Business Activities:**
   - Step 1: System automatically generates official Letter of Intent (LOI) populated with candidate name, designation, school/department, base compensation, allowances, joining deadline, and contingency conditions (e.g., medical fitness, background verification).
   - Step 2: Head HR digitally signs the generated LOI.
   - Step 3: LOI is formally dispatched to candidate with a tracked acceptance window (e.g., 7 calendar days).
   - Step 4: Candidate executes formal response:
     - **Accepts:** Submits signed acceptance with anticipated Date of Joining (DOJ).
     - **Declines:** Formally rejects offer with documented reasons.
     - **Expires:** Acceptance window elapses without response.
9. **Decision Points & Evaluation Rules:** Verification that generated LOI parameters match authorized Selection Matrix figures.
10. **Approval Points & Governance Gates:** Head HR digital signature required prior to offer dispatch.
11. **Institutional Outputs & Deliverables:** Official Letter of Intent (PDF); candidate signed acceptance copy.
12. **Operational SLA & Business Deadlines:** LOI issued within **48 hours** of Management approval; candidate acceptance tracked against offer validity window.
13. **Reminders, Escalations & Lockouts:** Reminder notifications dispatched to candidate 48h prior to offer expiration; expired offers release vacancy to waitlisted candidates.
14. **Exception Handling & Alternate Paths:** Candidate salary negotiation requests route back to Management for re-approval; declination triggers offer issuance to waitlisted candidate.
15. **Cross-Module Interactions & Handoffs:** Accepted LOI transitions candidate to "Yet to Join" Tracking (`BP-M2-ACAD-012`).
16. **Process Completion Criteria:** Candidate signed acceptance received and validated by HR.
17. **Audit & Compliance Requirements:** Generated LOI PDF, cryptographic hash, dispatch timestamp, and signed acceptance copy archived in candidate dossier.
18. **Authoritative Source References:** Module II Brief, Selection A(e); [`REQ-MOD2-19`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-DOC-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Relationship between initial LOI and post-joining formal appointment contract is classified under `REQ-TBD-08`.

---

### Process Identifier: BP-M2-ACAD-012
**Process Name:** Academic "Yet to Join" Pre-Onboarding Tracking

1. **Module / Operational Track:** Module II — Pre-Onboarding Pipeline.
2. **Business Purpose:** Monitor accepted candidates throughout their previous employer notice period, coordinate institutional pre-onboarding logistics, and ensure seamless Day-1 joining.
3. **Operational Trigger:** Receipt of signed LOI acceptance from candidate (`BP-M2-ACAD-011`).
4. **Prerequisites & Entry Conditions:** Candidate in `LOI_ACCEPTED` status with documented Date of Joining (DOJ).
5. **Primary Actors:** HR Department (Onboarding Desk).
6. **Supporting Actors:** School Dean, Department Head, IT Administrator, Candidate.
7. **Business Inputs & Documentation:** Signed LOI, confirmed DOJ, pre-onboarding verification checklist, IT resource request form.
8. **Sequential Business Activities:**
   - Step 1: System tags candidate as **"Yet to Join"** and adds profile to the executive Yet-to-Join Dashboard (`REQ-REP-04`).
   - Step 2: System dispatches automated pre-onboarding alerts to:
     - **School Dean & HOD:** For teaching schedule planning and lab assignment.
     - **IT Administrator:** For institutional email provisioning, ERP credentials, and workstation allocation.
     - **Campus Facilities:** For office space and faculty housing allocations.
   - Step 3: HR onboarding desk executes periodic engagement touchpoints during notice period.
   - Step 4: On confirmed DOJ, candidate arrives on campus to complete Day-1 physical verification.
9. **Decision Points & Evaluation Rules:** Verification of notice period progress; candidate confirmation of joining date adherence.
10. **Approval Points & Governance Gates:** Final Day-1 joining sign-off executed by HR Onboarding Officer.
11. **Institutional Outputs & Deliverables:** Completed Pre-Onboarding Checklist; provisioned institutional IT accounts; candidate ready for master database instantiation.
12. **Operational SLA & Business Deadlines:** Pre-onboarding alerts dispatched immediately upon LOI acceptance; logistics completed >= 48 hours prior to DOJ.
13. **Reminders, Escalations & Lockouts:** Candidate notice period delays alert School Dean to arrange temporary teaching coverage.
14. **Exception Handling & Alternate Paths:** If candidate reneges or fails to report on DOJ, vacancy is reopened in Open Positions Tracker and offer is formally revoked.
15. **Cross-Module Interactions & Handoffs:** Day-1 joining triggers the formal creation of the Master Employee Record in Module I Central Database (`BP-XMOD-001`).
16. **Process Completion Criteria:** Candidate formally reports on Day-1, verified by HR.
17. **Audit & Compliance Requirements:** Pre-onboarding notifications, joining confirmation memo, and arrival timestamps logged.
18. **Authoritative Source References:** Module II Brief, Selection A(e); [`REQ-MOD2-20`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

## 4. Non-Academic Recruitment Track (Processes 013–019)

### Process Identifier: BP-M2-NACAD-001
**Process Name:** Non-Academic Manpower Advance Initiation (>= 4 Months Prior)

1. **Module / Operational Track:** Module II — Non-Academic Recruitment Track (Administrative, Clerical, Technical, and Support Staff).
2. **Business Purpose:** Initiate advance operational staffing reviews for non-academic administrative and support departments.
3. **Operational Trigger:** Temporal calendar trigger reaching **at least four (4) months prior** to scheduled operational requirement or annual financial onboarding cycle.
4. **Prerequisites & Entry Conditions:** Annual university administrative operational calendar.
5. **Primary Actors:** HR Department (Operations / Manpower Planning Desk).
6. **Supporting Actors:** Department Heads (HODs) of Administrative Units.
7. **Business Inputs & Documentation:** Departmental operational reports, current staff deployment rolls, retirement forecasts, administrative workload metrics.
8. **Sequential Business Activities:**
   - Step 1: HR initiates annual non-academic manpower planning cycle >= 4 months prior to planned onboarding.
   - Step 2: HR communicates requisition guidelines and quota limits to all administrative Department Heads.
   - Step 3: HODs are provided standardized Non-Academic Manpower Requisition Forms (MRF).
   - Step 4: System starts standard 15-day submission countdown timer.
9. **Decision Points & Evaluation Rules:** Verification of administrative units eligible to submit planned requisitions.
10. **Approval Points & Governance Gates:** Planning call issued by Head HR.
11. **Institutional Outputs & Deliverables:** Formal Non-Academic Manpower Planning Intimation distributed to administrative HODs.
12. **Operational SLA & Business Deadlines:** Initiated >= 4 months prior to operational requirement (`REQ-MOD2-07`).
13. **Reminders, Escalations & Lockouts:** Reminder notices dispatched to HODs during the submission window.
14. **Exception Handling & Alternate Paths:** Emergency mid-year staffing needs are handled strictly under the Urgent Replacement track (`BP-M2-URG-001`).
15. **Cross-Module Interactions & Handoffs:** Consumes active departmental staff counts from Module I (`BP-XMOD-003`).
16. **Process Completion Criteria:** Planning intimation formally received by all administrative HODs.
17. **Audit & Compliance Requirements:** Call timestamp and recipient registry archived.
18. **Authoritative Source References:** Module II Brief, Section 1(g); [`REQ-MOD2-07`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-NACAD-002
**Process Name:** Non-Academic Annual Requisition Restriction (Strict 1 Planned MRF/Dept/Year)

1. **Module / Operational Track:** Module II — Non-Academic Recruitment Track.
2. **Business Purpose:** Enforce strict administrative discipline and budget control by restricting non-academic departments to exactly one (1) planned Manpower Requisition Form (MRF) per department per year.
3. **Operational Trigger:** Administrative Department Head attempts to submit a planned MRF (`BP-M2-NACAD-001`).
4. **Prerequisites & Entry Conditions:** Active non-academic planning window.
5. **Primary Actors:** Department Heads (HODs).
6. **Supporting Actors:** HR Department (Compliance Desk).
7. **Business Inputs & Documentation:** Completed Non-Academic MRF, justification of administrative workload, duty descriptions, proposed job specifications.
8. **Sequential Business Activities:**
   - Step 1: HOD prepares comprehensive annual staffing requisition consolidating all proposed non-academic positions.
   - Step 2: System evaluates annual submission quota rule:
     - **Zero Prior Submissions for Current Academic/Financial Year:** Submission permitted.
     - **Prior Planned MRF Already Submitted for Current Year:** System enforces **hard administrative block**, rejecting duplicate planned requisition.
   - Step 3: HOD submits single consolidated annual MRF within the **15-day submission window**.
9. **Decision Points & Evaluation Rules:** Strict quota check: Has this department already submitted a planned MRF for the current academic year?
10. **Approval Points & Governance Gates:** Mandatory Quota Gate (`REQ-MOD2-07`). System enforces strict single-submission policy.
11. **Institutional Outputs & Deliverables:** Single consolidated Annual Departmental MRF submitted to HR.
12. **Operational SLA & Business Deadlines:** Submitted within **15 days** of planning call; restricted to **1 planned submission per year** (`REQ-MOD2-07`).
13. **Reminders, Escalations & Lockouts:** System prevents submission of second planned MRF; HOD alerted to quota policy.
14. **Exception Handling & Alternate Paths:** Mid-year vacancies created by unexpected staff resignations must follow the Urgent Replacement workflow (`BP-M2-URG-001`).
15. **Cross-Module Interactions & Handoffs:** Routes submitted MRF to HR for administrative vetting (`BP-M2-NACAD-003`).
16. **Process Completion Criteria:** Single annual MRF formally logged and validated against departmental quota.
17. **Audit & Compliance Requirements:** Departmental submission quota counter incremented; timestamp and HOD signature archived.
18. **Authoritative Source References:** Module II Brief, Section 1(g); [`REQ-MOD2-07`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-NACAD-003
**Process Name:** Non-Academic Requirement Vetting, Consolidation & Approval Gate

1. **Module / Operational Track:** Module II — Non-Academic Governance.
2. **Business Purpose:** Vet administrative staffing justifications, audit operational workload allocations, and secure apex institutional approval from the Pro-Chancellor.
3. **Operational Trigger:** Receipt of annual non-academic MRFs from administrative departments (`BP-M2-NACAD-002`).
4. **Prerequisites & Entry Conditions:** Submitted annual MRF within quota limits.
5. **Primary Actors:** Head HR (Vetting Authority), Pro-Chancellor (Apex Approving Authority).
6. **Supporting Actors:** Submitting HODs, Vice President – Administration.
7. **Business Inputs & Documentation:** Departmental MRFs, operational justification statements, administrative organizational charts, sanctioned staff budgets.
8. **Sequential Business Activities:**
   - Step 1: Head HR vets submitted requests against institutional efficiency benchmarks and automation alternatives.
   - Step 2: Head HR consolidates verified positions into an Institutional Non-Academic Manpower Plan.
   - Step 3: Consolidated plan is submitted to the **Pro-Chancellor** for executive review.
   - Step 4: Pro-Chancellor executes formal approval determination.
9. **Decision Points & Evaluation Rules:** Executive assessment of administrative staffing ratios, operational overheads, and financial budgets.
10. **Approval Points & Governance Gates:** Mandatory Pro-Chancellor Approval Gate. No non-academic staff hiring may proceed without Pro-Chancellor authorization.
11. **Institutional Outputs & Deliverables:** Formally Sanctioned Non-Academic Hiring Authorization memo; approved Non-Academic MRFs.
12. **Operational SLA & Business Deadlines:** Vetting and consolidation finalized ahead of recruitment launch.
13. **Reminders, Escalations & Lockouts:** Pending approvals surfaced in executive queue.
14. **Exception Handling & Alternate Paths:** Disapproved administrative positions returned with reduction directives.
15. **Cross-Module Interactions & Handoffs:** Approved positions populate Open Positions Tracker (`BP-M2-TRK-002`) and advance to Recruitment Launch (`BP-M2-NACAD-004`).
16. **Process Completion Criteria:** Pro-Chancellor formal signature on Non-Academic Manpower Plan.
17. **Audit & Compliance Requirements:** Executive approval memo, position counts, and salary bands permanently archived.
18. **Authoritative Source References:** Module II Brief, Section 1(g, h); [`REQ-MOD2-07`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-NACAD-004
**Process Name:** Non-Academic Recruitment Launch & Sourcing Window

1. **Module / Operational Track:** Module II — Sourcing Operations.
2. **Business Purpose:** Launch public recruitment and candidate sourcing for sanctioned non-academic staff vacancies.
3. **Operational Trigger:** Official Pro-Chancellor approval of Non-Academic Manpower Plan (`BP-M2-NACAD-003`).
4. **Prerequisites & Entry Conditions:** Formally approved non-academic MRFs.
5. **Primary Actors:** HR Department (Recruitment Desk).
6. **Supporting Actors:** Media Vendors, Employment Portals.
7. **Business Inputs & Documentation:** Approved MRF job descriptions, qualification criteria, experience thresholds.
8. **Sequential Business Activities:**
   - Step 1: HR initiates public recruitment operations within **seven (7) days** of receiving Pro-Chancellor approval.
   - Step 2: Advertisements and postings are published across employment portals, print media, social channels, and university website.
   - Step 3: Sourcing and selection operations execute with the mandatory target of completing all hiring **at least fifteen (15) days prior** to planned onboarding date.
9. **Decision Points & Evaluation Rules:** Media channel selection based on role category (technical, clerical, administrative).
10. **Approval Points & Governance Gates:** Job posting copy approved by Head HR.
11. **Institutional Outputs & Deliverables:** Live job postings; applicant pipeline established in Central CV Database.
12. **Operational SLA & Business Deadlines:** Recruitment launched within **7 days** of approval; recruitment fully completed **>= 15 days before onboarding** (`REQ-MOD2-07`).
13. **Reminders, Escalations & Lockouts:** Milestone alerts track the 15-day pre-onboarding completion deadline.
14. **Exception Handling & Alternate Paths:** Insufficient candidate applications trigger extended sourcing across secondary portals.
15. **Cross-Module Interactions & Handoffs:** Applications feed Central CV Database (`BP-M2-TRK-001`) and Screening (`BP-M2-NACAD-005`).
16. **Process Completion Criteria:** Candidate application pool established for screening.
17. **Audit & Compliance Requirements:** Publication dates, portal links, and applicant counts logged.
18. **Authoritative Source References:** Module II Brief, Section 1(h) and Section 4; [`REQ-MOD2-07`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-NACAD-005
**Process Name:** Non-Academic CV Screening & RCS Pre-Interview Gate

1. **Module / Operational Track:** Module II — Screening & Pre-Interview Governance.
2. **Business Purpose:** Filter staff applicants against job descriptions, conduct structured telephonic evaluations via the Recruiter Calling Sheet (RCS), and secure Management pre-approval before scheduling interviews.
3. **Operational Trigger:** Candidate application received for an open non-academic vacancy (`BP-M2-NACAD-004`).
4. **Prerequisites & Entry Conditions:** Candidate profile indexed in Central CV Database.
5. **Primary Actors:** Recruiter (Interviewer), HOD-HR (Reviewer), Senior Management (Pre-Approval Authority).
6. **Supporting Actors:** Submitting Department Head (Consulted).
7. **Business Inputs & Documentation:** Candidate CV, MRF job specifications, digital Recruiter Calling Sheet (RCS).
8. **Sequential Business Activities:**
   - Step 1: Recruiter screens applicant qualifications against minimum educational criteria and years of relevant technical/administrative experience.
   - Step 2: Recruiter conducts telephonic interview, evaluating communication clarity, job fit, notice period, and salary expectations, logging remarks in the digital RCS.
   - Step 3: HOD-HR reviews compiled RCS remarks and endorses qualified candidates.
   - Step 4: Candidate dossier and RCS are submitted to **Management for formal pre-approval** prior to scheduling interviews.
   - Step 5: Management approves candidates for 3-round interview scheduling.
9. **Decision Points & Evaluation Rules:** Management pre-approval decision: Does applicant profile warrant executive and technical interview time?
10. **Approval Points & Governance Gates:** Mandatory Management Pre-Approval Gate (`REQ-MOD2-14`). No candidate may be scheduled for interviews without Management sign-off.
11. **Institutional Outputs & Deliverables:** Completed digital RCS; Management-approved candidate shortlist.
12. **Operational SLA & Business Deadlines:** Screening and RCS completed within 5 business days; Management review within 3 days.
13. **Reminders, Escalations & Lockouts:** Aged screening queues alert HOD-HR.
14. **Exception Handling & Alternate Paths:** Rejected candidates receive automated digital rejection notifications.
15. **Cross-Module Interactions & Handoffs:** Advances approved candidates to Non-Academic Three-Round Selection (`BP-M2-NACAD-006`).
16. **Process Completion Criteria:** Formal Management digital approval logged on candidate profile.
17. **Audit & Compliance Requirements:** RCS scores, reviewer comments, and Management pre-approval decision archived.
18. **Authoritative Source References:** Module II Brief, Sections 5, 6, 7; [`REQ-MOD2-12`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD2-13`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD2-14`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-NACAD-006
**Process Name:** Non-Academic Three-Round Sequential Selection (Technical, HR, Management)

1. **Module / Operational Track:** Module II — Non-Academic Interview Evaluation.
2. **Business Purpose:** Execute a structured, three-round sequential interview evaluation for non-academic candidates across three mandatory institutional evaluation dimensions.
3. **Operational Trigger:** Candidate receives Management RCS pre-approval (`BP-M2-NACAD-005`).
4. **Prerequisites & Entry Conditions:** Candidate in `APPROVED_FOR_INTERVIEW` status.
5. **Primary Actors:**
   - **Round 1 (Technical Interview):** Department Head (HOD) / Technical Subject Specialists.
   - **Round 2 (HR Interview):** HR Department (Head HR / HR Specialist).
   - **Round 3 (Management Interview):** Senior Management (Vice President – Administration / Executive Designee).
6. **Supporting Actors:** Candidate, Recruitment Coordinator.
7. **Business Inputs & Documentation:** Candidate dossier, job description, 3-Round Evaluation Scorecard evaluating the three mandatory dimensions:
   - **Job Knowledge:** Technical competence, operational capability, skill mastery.
   - **Communication Skills:** Spoken clarity, written proficiency, interpersonal effectiveness.
   - **Attitude:** Professionalism, institutional alignment, teamwork, adaptability.
8. **Sequential Business Activities:**
   - Step 1: Candidate undergoes **Round 1 (Technical Interview)**. Evaluators enter scores for Job Knowledge, Communication, and Attitude. Candidate must achieve satisfactory rating to advance.
   - Step 2: Successful candidates advance to **Round 2 (HR Interview)**. HR evaluates organizational fit, behavioral attributes, and compensation parameters.
   - Step 3: Successful candidates advance to **Round 3 (Management Interview)**. Executive leadership evaluates strategic alignment, leadership maturity, and final institutional suitability.
   - Step 4: System aggregates round scores into the consolidated Non-Academic Evaluation Matrix.
9. **Decision Points & Evaluation Rules:** Sequential elimination gate: Candidate must pass Round 1 to enter Round 2; must pass Round 2 to enter Round 3.
10. **Approval Points & Governance Gates:** Round-level sign-offs executed sequentially by HOD, Head HR, and Executive Evaluator.
11. **Institutional Outputs & Deliverables:** Completed, multi-signature 3-Round Evaluation Scorecard; consolidated candidate scoring matrix.
12. **Operational SLA & Business Deadlines:** Entire 3-round sequence completed within 10 business days of scheduling.
13. **Reminders, Escalations & Lockouts:** Unsubmitted scorecards alert interview coordinators.
14. **Exception Handling & Alternate Paths:** Candidate failing any single round is flagged as `REJECTED_IN_INTERVIEW` and exits the workflow.
15. **Cross-Module Interactions & Handoffs:** Advances final candidates to Non-Academic Selection Decision (`BP-M2-NACAD-007`).
16. **Process Completion Criteria:** Formal completion and submission of all three round scorecards.
17. **Audit & Compliance Requirements:** Individual round scores, interviewer remarks, and progression timestamps permanently archived.
18. **Authoritative Source References:** Module II Brief, Selection B(a); [`REQ-MOD2-17`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD2-18`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Scoring weight distribution across the three rounds is classified under `REQ-TBD-04`.

---

### Process Identifier: BP-M2-NACAD-007
**Process Name:** Non-Academic Selection Decision, LOI Generation & Pre-Onboarding

1. **Module / Operational Track:** Module II — Offer Administration & Pre-Onboarding.
2. **Business Purpose:** Finalize executive selection for non-academic candidates, issue official Letter of Intent (LOI), and track the candidate through notice periods to Day-1 onboarding.
3. **Operational Trigger:** Successful completion of Round 3 Management Interview (`BP-M2-NACAD-006`).
4. **Prerequisites & Entry Conditions:** Completed 3-Round Scorecard with favorable recommendations.
5. **Primary Actors:** Senior Management (Approving Authority), HR Department (Offer Desk).
6. **Supporting Actors:** Candidate (Recipient), Department Head, IT Administrator.
7. **Business Inputs & Documentation:** 3-Round Evaluation Matrix, approved salary band from MRF, standardized LOI template.
8. **Sequential Business Activities:**
   - Step 1: Senior Management reviews consolidated 3-Round matrix and authorizes appointment at designated salary.
   - Step 2: System auto-generates official Letter of Intent (LOI) populated with candidate and compensation details.
   - Step 3: LOI is signed by Head HR and issued to candidate with tracked acceptance window.
   - Step 4: Candidate accepts LOI; candidate profile is tagged as **"Yet to Join"**.
   - Step 5: Pre-onboarding notifications are dispatched to HOD and IT Administrator; onboarding countdown monitored.
9. **Decision Points & Evaluation Rules:** Verification of final compensation approval against sanctioned MRF budget.
10. **Approval Points & Governance Gates:** Senior Management Appointment Approval Gate.
11. **Institutional Outputs & Deliverables:** Official Letter of Intent (PDF); signed candidate acceptance; active "Yet to Join" tracker entry.
12. **Operational SLA & Business Deadlines:** LOI issued within 48 hours of Management approval; pre-onboarding completed >= 15 days before onboarding.
13. **Reminders, Escalations & Lockouts:** Expiration alerts track candidate acceptance window.
14. **Exception Handling & Alternate Paths:** Offer declination prompts offer to secondary candidate if approved by Management.
15. **Cross-Module Interactions & Handoffs:** Day-1 reporting instantiates master employee record in Module I Central Database (`BP-XMOD-001`).
16. **Process Completion Criteria:** Candidate formally reports on Day-1, verified by HR.
17. **Audit & Compliance Requirements:** Signed LOI, acceptance memo, and joining timestamps archived.
18. **Authoritative Source References:** Module II Brief, Selection B(b); [`REQ-MOD2-19`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD2-20`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-DOC-04`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Formal post-joining appointment contract terms are classified under `REQ-TBD-08`.

---

## 5. Urgent Replacement Track (Process 020)

### Process Identifier: BP-M2-URG-001
**Process Name:** Urgent Replacement Recruitment Initiation (Resignation Trigger & Ad-Hoc MRF)

1. **Module / Operational Track:** Module II — Urgent Replacement Track.
2. **Business Purpose:** Provide a dedicated, accelerated recruitment pipeline triggered by employee resignations, bypassing annual planned manpower quotas to prevent institutional capability gaps.
3. **Operational Trigger:** Acceptance of an employee resignation by the School Dean or Department Head (`BP-XMOD-002`).
4. **Prerequisites & Entry Conditions:** Formal acceptance of resignation officially recorded; outgoing employee ID and vacancy details confirmed.
5. **Primary Actors:** School Dean / Department Head (Initiator), HR Department (Head HR / Rapid Recruitment Desk).
6. **Supporting Actors:** Senior Management, Pro-Chancellor.
7. **Business Inputs & Documentation:** Resignation acceptance confirmation memo, outgoing employee service profile, Enclosure 1 (Ad-Hoc MRF flagged "URGENT REPLACEMENT").
8. **Sequential Business Activities:**
   - Step 1: Upon Dean's formal acceptance of resignation, the system **immediately starts the replacement countdown clock** and notifies Head HR (`REQ-MOD2-08`).
   - Step 2: Dean/HOD submits an **Ad-Hoc MRF (Enclosure 1)** explicitly designated as an urgent replacement, stating reason for hire and replacement justification (`REQ-MOD2-09`).
   - Step 3: System verifies that this requisition is an authorized replacement, **bypassing the annual planned MRF quota** (`REQ-MOD2-07`).
   - Step 4: Ad-hoc MRF undergoes fast-track vetting by Head HR and expedited approval by the Pro-Chancellor.
   - Step 5: Immediate sourcing commences via existing Central CV Database talent pools and expedited job postings.
9. **Decision Points & Evaluation Rules:** Verification that requisition represents a genuine replacement for an accepted resignation (and not an unbudgeted new post).
10. **Approval Points & Governance Gates:** Expedited Pro-Chancellor Approval Gate for ad-hoc replacement authorization.
11. **Institutional Outputs & Deliverables:** Approved Ad-Hoc Replacement MRF; active position entry in Open Positions Tracker with "URGENT REPLACEMENT" flag; active replacement SLA countdown.
12. **Operational SLA & Business Deadlines:** Replacement countdown clock starts immediately upon resignation acceptance; ad-hoc MRF submitted within 5 days; replacement target aligned with outgoing employee notice period.
13. **Reminders, Escalations & Lockouts:** Daily replacement clock countdown alerts delivered to Dean and Head HR.
14. **Exception Handling & Alternate Paths:** If department decides not to fill the vacated post, formal restructuring memo must be submitted to Management.
15. **Cross-Module Interactions & Handoffs:** Triggered by Module I resignation acceptance (`BP-XMOD-002`); replaces departed employee node in dynamic Organization Chart upon hiring completion (`BP-M1-002`).
16. **Process Completion Criteria:** Replacement candidate successfully hired and onboarded on or before outgoing employee last working day.
17. **Audit & Compliance Requirements:** Resignation acceptance timestamp, replacement clock start event, and ad-hoc MRF justification archived.
18. **Authoritative Source References:** Module II Brief, Section 1(i); [`REQ-MOD2-08`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-MOD2-09`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-INT-02`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Upstream employee resignation submission and institutional clearance workflow is classified under `REQ-TBD-06`.

---

## 6. Sourcing Infrastructure & Recruitment Registries (Processes 021–022)

### Process Identifier: BP-M2-TRK-001
**Process Name:** Central CV Database Ingestion, Profile Management & Deduplication

1. **Module / Operational Track:** Module II — Sourcing Infrastructure.
2. **Business Purpose:** Maintain a centralized institutional talent pool capturing candidate profiles from all inbound sourcing channels with automated deduplication and profile archiving.
3. **Operational Trigger:** Inbound resume submission via careers portal, email, job board, referral, or social platform.
4. **Prerequisites & Entry Conditions:** Receipt of digital candidate document or application payload.
5. **Primary Actors:** System Sourcing Engine, HR Recruitment Desk.
6. **Supporting Actors:** Applicants.
7. **Business Inputs & Documentation:** Candidate CV, contact coordinates, educational credentials, work history, portfolio links.
8. **Sequential Business Activities:**
   - Step 1: System extracts candidate primary identifiers (email address, mobile phone number, full name).
   - Step 2: System searches Central CV Database for existing profile matches:
     - **Match Found:** System appends new application to existing candidate dossier without overwriting historical interview records.
     - **No Match:** System instantiates new candidate master record.
   - Step 3: Candidate skills, qualifications, and experience are parsed and indexed for keyword search.
   - Step 4: Profile is categorized into talent pool disciplines (e.g., Computer Science, Mechanical Engineering, Administration).
9. **Decision Points & Evaluation Rules:** Deduplication criteria (exact match on verified email or mobile phone).
10. **Approval Points & Governance Gates:** Automated ingestion.
11. **Institutional Outputs & Deliverables:** Centralized, searchable candidate profile in Central CV Database.
12. **Operational SLA & Business Deadlines:** Instantaneous profile creation upon document receipt.
13. **Reminders, Escalations & Lockouts:** N/A.
14. **Exception Handling & Alternate Paths:** Incomplete contact details flag profile for manual recruiter review.
15. **Cross-Module Interactions & Handoffs:** Provides candidate sourcing pool for both Academic (`BP-M2-ACAD-006`) and Non-Academic (`BP-M2-NACAD-004`) recruitment.
16. **Process Completion Criteria:** Candidate successfully indexed in Central CV Database.
17. **Audit & Compliance Requirements:** Sourcing source attribution, consent records, and profile creation timestamps preserved.
18. **Authoritative Source References:** Module II Brief, Section 4; [`REQ-MOD2-11`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** None.

---

### Process Identifier: BP-M2-TRK-002
**Process Name:** Open Positions Tracker Maintenance & Weekly Executive Briefing

1. **Module / Operational Track:** Module II — Executive Recruitment Analytics.
2. **Business Purpose:** Maintain an authoritative, real-time registry of all sanctioned vacancies in the standardized Attachment 3 format, generating weekly executive briefings for Senior Management.
3. **Operational Trigger:**  
   - Formal Pro-Chancellor approval of an Academic or Non-Academic MRF (`BP-M2-ACAD-004`, `BP-M2-NACAD-003`).
   - Scheduled weekly management reporting cadence.
4. **Prerequisites & Entry Conditions:** Formally sanctioned MRF.
5. **Primary Actors:** HR Department (Recruitment Desk), Senior Management (Executive Reviewer).
6. **Supporting Actors:** School Deans, Department Heads.
7. **Business Inputs & Documentation:** Approved MRFs, candidate stage movement data, Attachment 3 (Enclosure 4 — Open Positions Tracker template).
8. **Sequential Business Activities:**
   - Step 1: System instantiates new position record in the Open Positions Tracker **within thirty (30) days** of MRF approval.
   - Step 2: Tracker continuously reflects vacancy lifecycle stage: `OPEN` $\rightarrow$ `ADVERTISED` $\rightarrow$ `SOURCING` $\rightarrow$ `SCREENING` $\rightarrow$ `INTERVIEWING` $\rightarrow$ `OFFERED` $\rightarrow$ `YET_TO_JOIN` $\rightarrow$ `FILLED` (or `CANCELLED`).
   - Step 3: Every week, the system compiles the **Weekly Open Positions Report** formatted in accordance with Attachment 3.
   - Step 4: Report is formally submitted to **Senior Management** detailing active vacancies, aging against SLAs, sourcing bottlenecks, and projected joining dates.
9. **Decision Points & Evaluation Rules:** Verification of position status transitions based on validated workflow events.
10. **Approval Points & Governance Gates:** Weekly report endorsement by Head HR prior to executive briefing.
11. **Institutional Outputs & Deliverables:** Living Open Positions Tracker (Attachment 3); Weekly Executive Recruitment Briefing Report.
12. **Operational SLA & Business Deadlines:** Maintained within **30 days** of approval; executive report compiled and submitted **weekly** (`REQ-MOD2-10`, `REQ-REP-03`).
13. **Reminders, Escalations & Lockouts:** Vacancies exceeding target SLA aging thresholds (e.g., unfilled > 60 days) automatically highlighted in red on executive dashboard.
14. **Exception Handling & Alternate Paths:** Position cancellations require formal executive withdrawal memo signed by Pro-Chancellor.
15. **Cross-Module Interactions & Handoffs:** Position marked `FILLED` upon candidate Day-1 onboarding in Module I (`BP-XMOD-001`).
16. **Process Completion Criteria:** Position record transitions to `FILLED` status.
17. **Audit & Compliance Requirements:** Full lifecycle audit trail capturing date of approval, advertisement date, interview dates, offer date, and joining date.
18. **Authoritative Source References:** Module II Brief, Sections 2 and 3; [`REQ-MOD2-10`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md), [`REQ-REP-03`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md).
19. **Classification:** `[A] Explicit Requirement`.
20. **Controlled Open Decisions (TBD):** Attachment 3 standardized schema is classified under `REQ-TBD-02`.

---
*End of Document — Module II Business Processes.*
