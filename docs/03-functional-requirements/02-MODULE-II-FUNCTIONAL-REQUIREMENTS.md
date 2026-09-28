# Module II — Recruitment & Selection Automation
## Functional Requirements Specification

**Document Identifier:** `DOC-03-FRD-MOD-02`  
**Phase:** Phase 3 — Functional Requirements Specification (Documentation-Only)  
**Location:** `docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`  
**Status:** Approved Functional Baseline  
**Authoritative Baseline:** [`PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/PROJECT_REQUIREMENTS_ANALYSIS.md) & [`TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/TECHNOLOGY_ARCHITECTURE_BASELINE.md)  
**Source Requirement:** `Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf`  
**Date:** September 29, 2026  

---

## 1. Purpose

The purpose of Module II is to automate the University's end-to-end Standard Operating Procedure (SOP) for Recruitment & Selection within the unified HR Change Management & Automation System ecosystem. The system governs manpower planning, position requisitioning, multi-channel candidate sourcing, centralized CV database processing, statutory selection committees, multi-round interviews, executive approvals, Letter of Intent (LOI) generation, and "Yet to Join" pre-onboarding tracking.

The system enforces distinct, non-interchangeable workflows for **Academic positions** (Faculty & Lab Technicians) and **Non-Academic positions** (Staff), while providing a shared sourcing and CV management engine.

---

## 2. Scope

Module II encompasses:
1. Two distinct Manpower Planning workflows:
   - *Academic Track:* Faculty, Teaching Associates, Technical Assistants, and Lab Technicians.
   - *Non-Academic Track:* Administrative, operational, and non-faculty staff.
2. The *Urgent Replacement Workflow* triggered by employee resignations.
3. The *Manpower Requisition Form (MRF)* lifecycle and validation rules.
4. The system-based *Open Positions Tracker* (Attachment 3).
5. *Omnichannel Sourcing* and the *Central CV Database*.
6. Automated *Classification, Screening, and UGC Norm Validation*.
7. The *Recruiter Calling Stage* and *Recruiter Calling Sheet (RCS)* feedback loop.
8. Statutory *Selection Committee Meetings (SCM)* for academic candidates, including digital invitations and scoring for External Subject Experts.
9. *Three-Round Sequential Interviews* for non-academic candidates (Technical, HR, Management).
10. *Management Pre-Approval* gates prior to interview initiation and cost approval for offers.
11. Automated generation of the *Letter of Intent (LOI)* and formal offer letters.
12. *"Yet to Join" Tracking* and pre-onboarding automated notifications to Deans, HODs, and IT Admin teams.
13. Comprehensive *Recruitment Reporting* (weekly status, sourcing analytics, interview funnels).

---

## 3. Actors and Roles

The following actors and roles are explicitly defined within Module II:

| Actor / Role | Documented Responsibilities in Recruitment & Selection | Source Reference | Classification |
|---|---|---|---|
| **Hon'ble Pro-Chancellor** | Final approval authority for Academic Manpower Planning recommendations; final approval authority for Non-Academic annual and ad-hoc MRFs. | Module II, Section 1(d, e, i) & Approval Hierarchy (1, 3) | `[A] EXPLICIT REQUIREMENT` |
| **Senior Management / Management** | Grants pre-approval for candidate shortlists prior to interview scheduling; grants final recommendation and cost approval for LOI issuance across Academic and Non-Academic tracks; conducts Round 3 interviews for Non-Faculty; receives weekly progress reports. | Module II, Section 3, 7, Selection A(d, e), B(a, b) | `[A] EXPLICIT REQUIREMENT` |
| **Associate Dean (Academics)** | Triggers the 4-month academic manpower planning communication to Deans; reviews and vets teaching load submissions (Attachment 1); seeks clarifications; consolidates and recommends proposals to the Pro-Chancellor within 15 days; vets ad-hoc academic replacement MRFs. | Module II, Section 1(a, c, d, i) & Approval Hierarchy (1) | `[A] EXPLICIT REQUIREMENT` |
| **Deans of Schools / School Deans** | Submits academic manpower requirements with teaching loads (Attachment 1) within 15 days; raises MRF upon Pro-Chancellor approval; accepts faculty resignations (initiating replacement clock); raises ad-hoc replacement MRFs; receives "Yet to Join" pre-onboarding notifications. | Module II, Section 1(b, f, i), Selection B(c) | `[A] EXPLICIT REQUIREMENT` |
| **Head of HR / HOD-HR / HR Team** | Triggers 4-month Non-Faculty manpower planning; reviews and vets Non-Faculty MRFs; consolidates and forwards proposals to Pro-Chancellor within 15 days; initiates public advertisements within 7 days of MRF; maintains RCS tracker; reviews recruiter call inputs; conducts Round 2 HR Interviews; compiles SCM matrix. | Module II, Section 1(a, c, d, g), 6, Selection A(d), B(a) | `[A] EXPLICIT REQUIREMENT` |
| **Heads of Department (HOD) / Dept Heads** | Submits annual Non-Faculty MRF (restricted to 1 planned requisition per year) within 15 days; raises ad-hoc replacement MRFs; conducts Round 1 Technical Interviews for Non-Faculty candidates; receives "Yet to Join" pre-onboarding reports. | Module II, Section 1(b, i), Selection B(a, c) | `[A] EXPLICIT REQUIREMENT` |
| **Selection Committee (SCM Members)** | Statutory panel for Academic recruitment (including internal leadership and External Subject Experts); receives digital invitations, CVs, and evaluation sheets; evaluates candidates in online/offline interviews; enters evaluation marks directly. | Module II, Selection A(a, c) & Approval Hierarchy (2) | `[A] EXPLICIT REQUIREMENT` |
| **External Subject Expert** | External statutory academic expert participating in SCM; receives secure digital access to resumes and evaluation sheets; evaluates and enters marks. | Module II, Selection A(a) | `[A] EXPLICIT REQUIREMENT` |
| **Technical Interview Panel** | Department Head and/or technical subject expert conducting Round 1 evaluation for Non-Faculty positions. | Module II, Selection B(a) & Approval Hierarchy (4) | `[A] EXPLICIT REQUIREMENT` |
| **Recruiter** | Conducts preliminary telephonic screening; captures candidate responses in the Recruiter Calling Sheet (RCS). | Module II, Section 6 | `[A] EXPLICIT REQUIREMENT` |
| **Candidate / Applicant** | Applies through configured channels; participates in interviews; accepts or declines LOI; completes pre-onboarding verifications. | Module II, Section 4, Selection A(e), B(b) | `[A] EXPLICIT REQUIREMENT` |
| **Admin & System IT Teams** | Receives automated "Yet to Join" pre-onboarding notifications to prepare physical workstations, computing hardware, email accounts, and system access prior to Day 1. | Module II, Selection B(c) | `[A] EXPLICIT REQUIREMENT` |

---

## 4. Academic Manpower Planning Workflow

*(Covers: Teaching Faculty, Teaching Associates, Technical Assistants, Lab Technicians)*

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             ACADEMIC MANPOWER PLANNING TIMELINE                                  │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ T - 4 MONTHS                  │ WITHIN 15 DAYS                 │ T - 3 MONTHS                    │
│ System auto-communication     │ Deans submit requirements with │ Associate Dean (Academics)      │
│ from Associate Dean (Acad)    │ Teaching Load (Attachment 1).  │ completes review and vetting    │
│ to Deans of Schools.          │ System tracks SLA + reminders. │ (clarification loop supported). │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ WITHIN 15 DAYS OF RECEIPT     │ WITHIN 7 DAYS                  │ IMMEDIATELY ON APPROVAL         │
│ Associate Dean forwards       │ Pro-Chancellor approval        │ Dean raises MRF to HR.          │
│ consolidated proposals to     │ communicated back to Dean.     │ HR initiates ads within 7 days  │
│ Hon'ble Pro-Chancellor.       │                                │ alongside RCS Tracker.          │
├───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┤
│ TARGET COMPLETION: Entire recruitment completed >= 1 month before semester start.                │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

- **`MOD2-MP-FAC-REQ-01` [A] 4-Month Automated Trigger:** The system shall trigger an automated manpower-requirement communication at least four (4) months before the start of the semester / academic year from the Associate Dean (Academics) to the Deans of Schools to assess faculty and technical workload.
- **`MOD2-MP-FAC-REQ-02` [A] 15-Day Dean Submission Window:** The concerned Dean shall submit finalized requirements along with the teaching load in the prescribed format (**Attachment 1**) within fifteen (15) days of the communication; the system shall track this deadline with automated reminders.
- **`MOD2-MP-FAC-REQ-03` [A] Vetting by 3-Month Mark:** The system shall route the submission for review and vetting to the Associate Dean (Academics), to be completed at least three (3) months before the start of the academic year, with provision to seek clarification / additional information from the concerned Dean.
- **`MOD2-MP-FAC-REQ-04` [A] 15-Day Consolidation to Pro-Chancellor:** The Associate Dean (Academics) shall consolidate submissions along with recommendations and forward them to the Hon'ble Pro-Chancellor within fifteen (15) days of receipt; the system shall track this SLA.
- **`MOD2-MP-FAC-REQ-05` [A] 7-Day Pro-Chancellor Turnaround:** The Hon'ble Pro-Chancellor's approval shall be communicated back to the concerned Dean within seven (7) days; the system shall track and notify accordingly.
- **`MOD2-MP-FAC-REQ-06` [A] Post-Approval MRF Generation:** On approval, the system shall enable the concerned Dean to immediately raise a Manpower Requisition Form (MRF) and route it to the HR team.
- **`MOD2-MP-FAC-REQ-07` [A] 7-Day Recruitment Ad Initiation:** HR shall initiate the recruitment process (newspaper and social media advertisements) within seven (7) days of receiving the MRF; the system shall track this SLA and initialize the RCS tracker.
- **`MOD2-MP-FAC-REQ-08` [A] 1-Month Semester Completion Gate:** The system shall flag and track that the entire recruitment process is completed at least one (1) month before the start of the semester, with the target completion date auto-calculated accordingly.

---

## 5. Non-Academic Manpower Planning Workflow

*(Covers: Administrative, Technical, Operational, and Non-Faculty Positions)*

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                           NON-ACADEMIC MANPOWER PLANNING TIMELINE                                │
├───────────────────────────────┬────────────────────────────────┬─────────────────────────────────┤
│ T - 4 MONTHS                  │ WITHIN 15 DAYS                 │ T - 3 MONTHS                    │
│ System auto-communication     │ Department Heads submit MRF.   │ Head HR completes vetting       │
│ from HR to Department Heads.  │ Strictly restricted to ONE     │ (operational needs, replacement,│
│                               │ planned requisition per year.  │ workload, expansion).           │
├───────────────────────────────┼────────────────────────────────┼─────────────────────────────────┤
│ WITHIN 15 DAYS OF RECEIPT     │ ON PRO-CHANCELLOR CLEARANCE    │ WITHIN 7 DAYS                   │
│ Head HR forwards consolidated │ Approval communicated back to  │ HR initiates public ads and     │
│ proposals to Pro-Chancellor.  │ Department Head.               │ opens RCS Tracker.              │
├───────────────────────────────┴────────────────────────────────┴─────────────────────────────────┤
│ TARGET COMPLETION: Entire recruitment completed >= 15 days before candidate onboard date.        │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

- **`MOD2-MP-NF-REQ-01` [A] 4-Month Automated Communication:** The system shall trigger an automated communication at least four (4) months before the start of the academic year from HR to concerned Department Heads to assess operational needs, workload analysis, replacement requirements, or expansion of services.
- **`MOD2-MP-NF-REQ-02` [A] 15-Day Annual MRF Submission Window:** The concerned Department Head shall submit their finalized requirement as a Manpower Requisition Form (MRF) within fifteen (15) days of the communication; the system shall track this deadline with reminders.
- **`MOD2-MP-NF-REQ-03` [A] Single Annual Planned MRF Restriction:** The system shall strictly restrict Department Heads to one (1) planned requisition per year (with urgent replacement MRFs permitted at any time).
- **`MOD2-MP-NF-REQ-04` [A] Vetting by Head HR by 3-Month Mark:** The system shall route the submission for review and vetting to Head HR, to be completed at least three (3) months before the start of the academic year, with provision to seek clarification.
- **`MOD2-MP-NF-REQ-05` [A] 15-Day Consolidation to Pro-Chancellor:** Head HR shall consolidate submissions along with recommendations and forward them to the Hon'ble Pro-Chancellor within fifteen (15) days of receipt (SLA tracked).
- **`MOD2-MP-NF-REQ-06` [A] Approval Communication:** The Hon'ble Pro-Chancellor's approval shall be communicated back to the concerned Department Head; the system shall track and notify accordingly.
- **`MOD2-MP-NF-REQ-07` [A] 7-Day Advertisement Initiation:** HR shall initiate the recruitment process within seven (7) days of receiving cleared MRF authorization, creating the RCS tracker.
- **`MOD2-MP-NF-REQ-08` [A] 15-Day Onboarding Completion Gate:** The system shall flag and track that the entire recruitment process is completed at least fifteen (15) days before the candidate is required to be onboarded, with target dates auto-calculated.

---

## 6. Urgent Replacement Workflow (Resignations)

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                               URGENT REPLACEMENT PIPELINE                                        │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. Resignation Accepted by Dean ──► Auto-Alert Head HR & Start Replacement Countdown Clock       │
│ 2. Dean / HOD submits Ad-Hoc MRF at any time                                                     │
│ 3. Sequential SLA Pipeline: Ad-hoc MRF ──► Vetting ──► Pro-Chancellor Approval                  │
│ 4. Monitored Execution Block: Sourcing ──► Shortlisting ──► SCM / Interview                      │
│ 5. Stage-wise Offer Flow: Evaluation ──► Management Cost Approval ──► Auto Offer Letter          │
│ 6. Candidate Milestones: Acceptance ──► Notice Period ──► Verification ──► Joining / Onboard     │
│ 7. Final Closeout: Onboarding completes ──► Closes Position in Open Positions Tracker            │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

- **`MOD2-RES-REQ-01` [A] Replacement Clock Trigger:** The replacement clock shall start immediately upon resignation acceptance by the School Dean, automatically notifying Head HR.
- **`MOD2-RES-REQ-02` [A] Ad-Hoc MRF Authority:** For urgent or replacement requirements arising from resignation, the system shall allow the concerned Dean / Department Head to raise an ad-hoc MRF at any time.
- **`MOD2-RES-REQ-03` [A] Sequential SLA Vetting Pipeline:** The system shall track:
  $$\text{MRF Submission} \longrightarrow \text{Vetting (Assoc. Dean / Head HR)} \longrightarrow \text{Pro-Chancellor Approval}$$
  as sequential SLA stages, with automated reminders on timeline overruns.
- **`MOD2-RES-REQ-04` [A] Monitored Sourcing Block:** Sourcing $\rightarrow$ Shortlisting $\rightarrow$ Selection Committee Meeting (or Interview) shall be tracked as one monitored execution block.
- **`MOD2-RES-REQ-05` [A] Stage-Wise Offer & Auto-Generated Letter:** Post-selection evaluation, approval, and offer-letter issuance shall be tracked stage-wise, with an auto-generated offer letter.
- **`MOD2-RES-REQ-06` [A] Candidate Lifecycle Closeout:** Candidate-side milestones (offer acceptance, notice period, verification, joining) shall be tracked through to onboarding, closing out the cycle and updating the Open Positions Tracker.

---

## 7. Manpower Requisition Form (MRF) Lifecycle

- **`MOD2-MRF-REQ-01` [A] Standardized MRF:** The system shall enforce the standardized Manpower Requisition Form (**Enclosure 1**) capturing position details, justification, required qualifications, experience, and budget band.
- **`MOD2-MRF-REQ-02` [B] Position Classification:** Every MRF shall be tagged as either Academic (Faculty/Lab Tech) or Non-Academic (Staff), and as Planned Annual Requisition vs. Urgent Replacement.
- **`MOD2-MRF-REQ-03` [B] MRF State Machine:** MRF records shall transition through: `DRAFT`, `SUBMITTED`, `UNDER_VETTING`, `RECOMMENDED`, `PRO_CHANCELLOR_APPROVED`, `REJECTED`, `IN_RECRUITMENT`, `FILLED`, `CANCELLED`.

---

## 8. Open Positions Tracker

- **`MOD2-POS-REQ-01` [A] Automated Maintenance:** All approved manpower positions (Faculty & Lab Technician and Non-Faculty) shall be recorded and automatically maintained in the system-based Open Positions Tracker (**Attachment 3 format**).
- **`MOD2-POS-REQ-02` [A] 30-Day Setup SLA:** Recording of approved positions into the Open Positions Tracker shall be completed within thirty (30) days of approval.
- **`MOD2-POS-REQ-03` [A] Weekly Progress Reporting:** The system shall auto-generate weekly progress reports to Management on the status of open / pending positions.
- **`MOD2-POS-REQ-04` [B] Real-Time Status Synchronization:** The Open Positions Tracker shall update in real time as candidates progress from sourcing to SCM, LOI issuance, and onboarding completion.

---

## 9. Multi-Channel Candidate Sourcing

- **`MOD2-SRC-REQ-01` [A] Omnichannel Publishing:** The system shall publish / advertise approved positions across configured channels (print media, social media, University website) linked to the approved MRF, categorized by position type.
- **`MOD2-SRC-REQ-02` [A] Designated Channel Ingestion:** The system shall capture applications received through:
  1. Designated recruitment email IDs
  2. University Website application portals
  3. Facebook
  4. Instagram
  5. LinkedIn
  6. Newspaper advertisements (coded application links)
  7. Internal employee references
  8. External platforms (such as Internshala for interns)

---

## 10. Central CV Database

- **`MOD2-CVD-REQ-01` [A] Unified CV Repository:** All incoming applications across all channels shall be ingested into a central, shared CV Database.
- **`MOD2-CVD-REQ-02` [B] Profile Deduplication:** The system shall automatically detect and merge duplicate candidate profiles based on verified email address, mobile number, and government ID / PAN where available.
- **`MOD2-CVD-REQ-03` [C] Binary Storage Separation:** Candidate resumes and portfolios shall be stored in Object Storage with metadata, parsed text, and storage URIs indexed in PostgreSQL.

---

## 11. CV Classification and Screening

- **`MOD2-SCR-REQ-01` [A] Auto-Segregation & Classification:** The system shall automatically segregate and classify incoming applications by position type, discipline, school, and department.
- **`MOD2-SCR-REQ-02` [A] Criteria Shortlisting:** The system shall enable shortlisting of candidates against the position's educational qualifications and experience criteria specified in the approved MRF.

---

## 12. UGC Norm Screening

- **`MOD2-UGC-REQ-01` [A] UGC Statutory Norm Compliance:** For academic faculty positions, the system shall evaluate candidate educational qualifications and credentials against applicable University Grants Commission (UGC) norms (e.g., minimum percentage in Master's degree, NET/SET qualification, Ph.D. requirements, and API/research benchmark scores).
- **`MOD2-UGC-REQ-02` [B] Compliance Flagging:** The system shall visually flag candidates meeting, exceeding, or failing statutory UGC criteria for recruiter and evaluator visibility.

---

## 13. Recruiter Calling Sheet (RCS)

- **`MOD2-RCS-REQ-01` [A] Recruiter-Calling Stage:** Shortlisted applications shall move to the recruiter-calling stage for preliminary screening.
- **`MOD2-RCS-REQ-02` [A] Standardized RCS Format:** Call inputs, candidate availability, current compensation, expected compensation, notice period, and communication assessment shall be captured in the system in the standardized **Recruiter Calling Sheet (RCS)** format.
- **`MOD2-RCS-REQ-03` [A] HOD-HR Review Loop:** RCS records shall be routed to HOD-HR for formal feedback and verification.

---

## 14. Academic Selection Workflow (Selection Committee Meeting - SCM)

*(Applies to: Teaching Faculty, Teaching Associates, Technical Assistants, Lab Technicians)*

- **`MOD2-SCM-REQ-01` [A] Statutory SCM Process:** The system shall support the Selection Committee Meeting (SCM) process as outlined in the university statutes.
- **`MOD2-SCM-REQ-02` [A] Digital Invitations & Document Sharing:** The system shall dispatch digital invitations to SCM members (including the External Subject Expert) with candidate resumes and digital evaluation sheets shared directly through the system.
- **`MOD2-SCM-REQ-03` [A] Online and Offline Interview Modes:** The system shall support scheduling interviews in online mode, with provision for offline mode in exceptional cases.
- **`MOD2-SCM-REQ-04` [A] Evaluator Marks Entry:** The system shall allow evaluators to enter marks directly into the digital evaluation sheet during or immediately following the interview.
- **`MOD2-SCM-REQ-05` [A] Evaluation Matrix Compilation:** The system shall compile SCM member feedback and scores into an Evaluation Matrix and route it to Management along with HR recommendations.
- **`MOD2-SCM-REQ-06` [A] Management Approval & LOI Issuance:** On receiving Management's final recommendation and cost approval, the system shall auto-generate the Letter of Intent (LOI); on candidate acceptance, the candidate shall be recorded as "Yet to Join" in the internal HR database.

---

## 15. External Subject Expert Participation

- **`MOD2-EXP-REQ-01` [A] External Expert Inclusion:** The system shall support statutory external subject experts as authenticated participants in the SCM process.
- **`MOD2-EXP-REQ-02` [C] Secure Tokenized Portal:** External experts shall receive secure, time-limited magic links granting access strictly to assigned candidate CVs and digital evaluation sheets, preventing unauthorized access to broader university databases.

---

## 16. Non-Academic Selection Workflow (Three-Round Interviews)

*(Applies to: Non-Faculty Staff)*

- **`MOD2-SEL-NF-REQ-01` [A] Three Sequential Interview Rounds:** The system shall enforce three rounds of interviews for non-academic positions:
  1. *Round 1: Technical Interview* (conducted by Department Head / Subject Expert)
  2. *Round 2: HR Interview* (conducted by Head of HR)
  3. *Round 3: Management Interview*
- **`MOD2-SEL-NF-REQ-02` [A] Three Evaluation Competencies:** Evaluator feedback in digital evaluation sheets shall assess three mandatory parameters:
  1. *Job Knowledge*
  2. *Communication Skills*
  3. *Attitude*
- **`MOD2-SEL-NF-REQ-03` [A] LOI & "Yet to Join" Tracking:** On receiving Management's final recommendation and cost approval, the system shall auto-generate the Letter of Intent (LOI); on acceptance, the candidate shall be recorded as "Yet to Join" in the internal HR database.

---

## 17. Interview Rounds Management

- **`MOD2-INT-REQ-01` [B] Interview Scheduling & Calendar Dispatches:** The system shall allow scheduling of interview sessions with automated calendar invites, attendee links (for online mode), and location details (for offline mode).
- **`MOD2-INT-REQ-02` [B] Sequential Round Gating:** For Non-Academic candidates, progression to Round 2 (HR) requires clearance of Round 1 (Technical); progression to Round 3 (Management) requires clearance of Round 2.

---

## 18. Candidate Evaluation and Scoring

- **`MOD2-SCR-REQ-01` [B] Digital Scoring Records:** Individual evaluator scores, comments, recommendations (Select, Reject, Hold), and quantitative marks shall be permanently recorded with timestamps.
- **`MOD2-SCR-REQ-02` [B] Consolidated Committee Scorecards:** The system shall calculate consolidated average or weighted scores across committee members and highlight discrepancies between evaluators.

---

## 19. Management Pre-Approval Gate

- **`MOD2-MGT-REQ-01` [A] Pre-Interview Authorization:** On completion of candidate shortlisting and RCS screening, the shortlisted inputs shall be routed to Management for formal approval before the interview process is initiated.
- **`MOD2-MGT-REQ-02` [B] Schedule Freeze:** The system shall prevent interview scheduling or invitation dispatch until Management pre-approval is recorded in the audit trail.

---

## 20. Letter of Intent (LOI) & Offer Generation

- **`MOD2-LOI-REQ-01` [A] Auto-Generated LOI:** Upon receiving Management's final recommendation and cost approval, the system shall auto-generate the Letter of Intent (LOI) populated with candidate details, designation, department, proposed compensation, and response deadline.
- **`MOD2-LOI-REQ-02` [A] Auto-Generated Offer Letter for Replacements:** For urgent replacement workflows, the system shall auto-generate the formal offer letter following evaluation and approval.
- **`MOD2-LOI-REQ-03` [B] Digital Acceptance Interface:** Candidates shall receive secure digital access to accept or decline the LOI with date-stamped confirmation.

---

## 21. "Yet-to-Join" Pre-Onboarding Tracking

- **`MOD2-YTI-REQ-01` [A] "Yet to Join" Status Flag:** Upon candidate acceptance of the LOI, the candidate record shall immediately be tagged as "Yet to Join" in the internal HR database.
- **`MOD2-YTI-REQ-02` [A] Automated Cross-Departmental Sharing:** The system shall auto-share internal reports with concerned HODs, Deans, and Admin / System IT teams for "Yet to Join" candidates, ensuring pre-onboarding requirements (workstation, computing hardware, email account, access badges) are completed on time.
- **`MOD2-YTI-REQ-03` [A] Milestone Tracking:** The system shall track candidate-side milestones: Offer Acceptance $\rightarrow$ Notice Period $\rightarrow$ Document Verification $\rightarrow$ Day-1 Joining $\rightarrow$ Onboarding Complete.
- **`MOD2-YTI-REQ-04` [B] Handshake into Module I:** Upon verified Day-1 joining, the system shall initialize the master employee record in the Central Employee Database (Module I), update the dynamic Org Chart, and close out the position in the Open Positions Tracker.

---

## 22. Recruitment Reporting

- **`MOD2-REP-REQ-01` [A] Minimum Mandatory Reports:** HR shall provide the list and format of reports, which shall at minimum include:
  1. *Weekly Open / Pending Positions Report* (auto-generated to Management)
  2. *CV Database / Sourcing Channel Report*
  3. *Shortlisting and Interview Funnel Report*
  4. *"Yet to Join" Pre-Onboarding Tracker* (for both Faculty and Non-Faculty positions)
- **`MOD2-REP-REQ-02` [A] Real-Time Reporting & Extensibility:** Provision for real-time reports shall exist, with administrative support for adding or deleting report formats over time.

---

## 23. Functional Requirement Catalogue

| Requirement ID | Section | Requirement Title | Classification | Source Brief Ref |
|---|---|---|---|---|
| `MOD2-MP-FAC-REQ-01` | 4 | Academic 4-Month Automated Communication | `[A] EXPLICIT` | Module II, Section 1(a) |
| `MOD2-MP-FAC-REQ-02` | 4 | Academic 15-Day Teaching Load Submission | `[A] EXPLICIT` | Module II, Section 1(b) |
| `MOD2-MP-FAC-REQ-03` | 4 | Academic Vetting by 3-Month Mark | `[A] EXPLICIT` | Module II, Section 1(c) |
| `MOD2-MP-FAC-REQ-04` | 4 | Academic 15-Day Consolidation to Pro-Chancellor | `[A] EXPLICIT` | Module II, Section 1(d) |
| `MOD2-MP-FAC-REQ-05` | 4 | Academic 7-Day Pro-Chancellor Turnaround | `[A] EXPLICIT` | Module II, Section 1(e) |
| `MOD2-MP-FAC-REQ-06` | 4 | Academic Post-Approval MRF Generation | `[A] EXPLICIT` | Module II, Section 1(f) |
| `MOD2-MP-FAC-REQ-07` | 4 | Academic 7-Day Ad Initiation & RCS Tracker | `[A] EXPLICIT` | Module II, Section 1(g) |
| `MOD2-MP-FAC-REQ-08` | 4 | Academic 1-Month Semester Completion Gate | `[A] EXPLICIT` | Module II, Section 1(h) |
| `MOD2-MP-NF-REQ-01` | 5 | Non-Academic 4-Month Automated Communication | `[A] EXPLICIT` | Module II, Section 1(a) |
| `MOD2-MP-NF-REQ-02` | 5 | Non-Academic 15-Day MRF Submission | `[A] EXPLICIT` | Module II, Section 1(b) |
| `MOD2-MP-NF-REQ-03` | 5 | Non-Academic Single Annual MRF Restriction | `[A] EXPLICIT` | Module II, Section 1(b) |
| `MOD2-MP-NF-REQ-04` | 5 | Non-Academic Vetting by Head HR (3-Month Mark) | `[A] EXPLICIT` | Module II, Section 1(c) |
| `MOD2-MP-NF-REQ-05` | 5 | Non-Academic 15-Day Consolidation to Pro-Chancellor | `[A] EXPLICIT` | Module II, Section 1(d) |
| `MOD2-MP-NF-REQ-06` | 5 | Non-Academic Approval Notification | `[A] EXPLICIT` | Module II, Section 1(e) |
| `MOD2-MP-NF-REQ-07` | 5 | Non-Academic 7-Day Ad Initiation & RCS Tracker | `[A] EXPLICIT` | Module II, Section 1(g) |
| `MOD2-MP-NF-REQ-08` | 5 | Non-Academic 15-Day Onboarding Completion Gate | `[A] EXPLICIT` | Module II, Section 1(h) |
| `MOD2-RES-REQ-01` | 6 | Resignation Acceptance Replacement Clock Trigger | `[A] EXPLICIT` | Module II, Section 1(i) |
| `MOD2-RES-REQ-02` | 6 | Ad-Hoc MRF Submission Authority | `[A] EXPLICIT` | Module II, Section 1(i) |
| `MOD2-RES-REQ-03` | 6 | Sequential SLA Vetting Pipeline | `[A] EXPLICIT` | Module II, Section 1(i) |
| `MOD2-RES-REQ-04` | 6 | Monitored Execution Block (Sourcing $\rightarrow$ SCM) | `[A] EXPLICIT` | Module II, Section 1(i) |
| `MOD2-RES-REQ-05` | 6 | Auto-Generated Offer Letter for Replacements | `[A] EXPLICIT` | Module II, Section 1(i) |
| `MOD2-RES-REQ-06` | 6 | Candidate Milestone Tracking to Onboarding | `[A] EXPLICIT` | Module II, Section 1(i) |
| `MOD2-MRF-REQ-01` | 7 | Standardized MRF Enclosure 1 Capture | `[A] EXPLICIT` | Module II, Enclosures (1) |
| `MOD2-POS-REQ-01` | 8 | Automated Open Positions Tracker (Attachment 3) | `[A] EXPLICIT` | Module II, Section 1(j) |
| `MOD2-POS-REQ-02` | 8 | 30-Day Open Positions Tracker Maintenance SLA | `[A] EXPLICIT` | Module II, Section 1(j) |
| `MOD2-POS-REQ-03` | 8 | Weekly Progress Reports to Management | `[A] EXPLICIT` | Module II, Section 3 |
| `MOD2-SRC-REQ-01` | 9 | Omnichannel Job Advertising Linked to MRF | `[A] EXPLICIT` | Module II, Section 2 |
| `MOD2-SRC-REQ-02` | 9 | 8-Channel Candidate Application Capture | `[A] EXPLICIT` | Module II, Section 4 |
| `MOD2-CVD-REQ-01` | 10 | Central CV Database Ingestion | `[A] EXPLICIT` | Module II, Section 4 |
| `MOD2-SCR-REQ-01` | 11 | Automated Application Classification | `[A] EXPLICIT` | Module II, Section 5 |
| `MOD2-SCR-REQ-02` | 11 | Qualification and Experience Shortlisting | `[A] EXPLICIT` | Module II, Section 5 |
| `MOD2-UGC-REQ-01` | 12 | UGC Norms Automated Verification | `[A] EXPLICIT` | Module II, Section 5 |
| `MOD2-RCS-REQ-01` | 13 | Recruiter Calling Stage Transition | `[A] EXPLICIT` | Module II, Section 6 |
| `MOD2-RCS-REQ-02` | 13 | Recruiter Calling Sheet (RCS) Format Capture | `[A] EXPLICIT` | Module II, Section 6 |
| `MOD2-RCS-REQ-03` | 13 | RCS Review & Feedback by HOD-HR | `[A] EXPLICIT` | Module II, Section 6 |
| `MOD2-MGT-REQ-01` | 19 | Management Pre-Approval Before Interviews | `[A] EXPLICIT` | Module II, Section 7 |
| `MOD2-SCM-REQ-01` | 14 | Statutory SCM Process Support | `[A] EXPLICIT` | Module II, Selection A(a) |
| `MOD2-SCM-REQ-02` | 14 | SCM Digital Invitations & Document Sharing | `[A] EXPLICIT` | Module II, Selection A(a) |
| `MOD2-SCM-REQ-03` | 14 | Online & Offline Interview Mode Scheduling | `[A] EXPLICIT` | Module II, Selection A(b) |
| `MOD2-SCM-REQ-04` | 14 | Digital Evaluation Sheet Marks Entry | `[A] EXPLICIT` | Module II, Selection A(c) |
| `MOD2-SCM-REQ-05` | 14 | SCM Evaluation Matrix Compilation | `[A] EXPLICIT` | Module II, Selection A(d) |
| `MOD2-SCM-REQ-06` | 14 | Management Approval & Direct LOI Generation | `[A] EXPLICIT` | Module II, Selection A(e) |
| `MOD2-EXP-REQ-01` | 15 | External Subject Expert SCM Participation | `[A] EXPLICIT` | Module II, Selection A(a) |
| `MOD2-EXP-REQ-02` | 15 | Secure Tokenized Portal for External Experts | `[C] APPROVED TECH` | Tech Architecture Baseline, Section 13 |
| `MOD2-SEL-NF-REQ-01` | 16 | Three Sequential Non-Academic Interview Rounds | `[A] EXPLICIT` | Module II, Selection B(a) |
| `MOD2-SEL-NF-REQ-02` | 16 | Assessment of Knowledge, Communication, Attitude | `[A] EXPLICIT` | Module II, Selection B(a) |
| `MOD2-SEL-NF-REQ-03` | 16 | Non-Academic LOI Generation & "Yet to Join" Flag | `[A] EXPLICIT` | Module II, Selection B(b) |
| `MOD2-YTI-REQ-01` | 21 | "Yet to Join" Internal Database Status | `[A] EXPLICIT` | Module II, Selection A(e), B(b) |
| `MOD2-YTI-REQ-02` | 21 | Automated Pre-Onboarding Alerts (HOD/Dean/IT) | `[A] EXPLICIT` | Module II, Selection B(c) |
| `MOD2-YTI-REQ-03` | 21 | Candidate Milestone Tracking | `[A] EXPLICIT` | Module II, Section 1(i) |
| `MOD2-YTI-REQ-04` | 21 | Final Handshake into Module I Master DB | `[B] LOGICAL` | Derived from Onboarding Objective |
| `MOD2-REP-REQ-01` | 22 | Mandatory Recruitment Reports Suite | `[A] EXPLICIT` | Module II, Reports |

---

## 24. Requirement Traceability

| Functional Requirement ID | Source Document Reference | Base Traceability ID (`PROJECT_REQUIREMENTS_ANALYSIS.md`) | Downstream Phase Dependency |
|---|---|---|---|
| `MOD2-MP-FAC-REQ-01` to `08` | Module II PDF, Page 1-2, Section 1(a-h) | `MOD2-MP-FAC-01`, `MOD2-MP-FAC-02` | Phase 5 (Workflows: Academic Manpower Planning) |
| `MOD2-MP-NF-REQ-01` to `08` | Module II PDF, Page 1-2, Section 1(a-h) | `MOD2-MP-NF-01` | Phase 5 (Workflows: Non-Academic Manpower Planning) |
| `MOD2-RES-REQ-01` to `06` | Module II PDF, Page 2, Section 1(i) | `MOD2-RES-01` | Phase 5 (Workflows: Resignation Replacement Tracker) |
| `MOD2-POS-REQ-01` to `03` | Module II PDF, Page 2, Section 1(j), 3 | `MOD2-POS-01` | Phase 4 (ERD: `open_positions_tracker`), Phase 6 (API: `/positions`) |
| `MOD2-SRC-REQ-01` to `02` | Module II PDF, Page 2, Section 2, 4 | `MOD2-SRC-01` | Phase 6 (API: Ingestion webhooks), Phase 8 (Object Store: CVs) |
| `MOD2-CVD-REQ-01` to `03` | Module II PDF, Page 2, Section 4 | `MOD2-SRC-01` | Phase 4 (ERD: `candidates`, `applications`) |
| `MOD2-SCR-REQ-01` to `02` | Module II PDF, Page 2, Section 5 | `MOD2-SRC-02` | Phase 6 (Rules Engine: qualification filter) |
| `MOD2-UGC-REQ-01` to `02` | Module II PDF, Page 2, Section 5 | `MOD2-SRC-02` | Phase 6 (UGC Norms Evaluator Service) |
| `MOD2-RCS-REQ-01` to `03` | Module II PDF, Page 2, Section 6 | `MOD2-RCS-01` | Phase 7 (UI: RCS form), Phase 6 (API: `/rcs`) |
| `MOD2-MGT-REQ-01` to `02` | Module II PDF, Page 3, Section 7 | `MOD2-MGT-01` | Phase 5 (State Machine: Pre-interview approval gate) |
| `MOD2-SCM-REQ-01` to `06` | Module II PDF, Page 3, Selection A | `MOD2-SEL-FAC-01` | Phase 5 (Workflows: SCM portal & marks compilation) |
| `MOD2-EXP-REQ-01` to `02` | Module II PDF, Page 3, Selection A(a) | `MOD2-SEL-FAC-01` | Phase 8 (Security: External expert magic link authentication) |
| `MOD2-SEL-NF-REQ-01` to `03` | Module II PDF, Page 3, Selection B | `MOD2-SEL-NF-01` | Phase 5 (Workflows: 3-round interview sequential pipeline) |
| `MOD2-LOI-REQ-01` to `03` | Module II PDF, Page 3, Selection A(e), B(b) | `MOD2-ONB-01` | Phase 6 (PDF Service: LOI template generator) |
| `MOD2-YTI-REQ-01` to `04` | Module II PDF, Page 3, Selection B(c) | `MOD2-ONB-01` | Phase 5 (Onboarding state machine & Module I event emission) |
| `MOD2-REP-REQ-01` to `02` | Module II PDF, Page 4, Reports | `MOD2-REP-01` | Phase 7 (UI: Recruitment Analytics Dashboard) |

---

## 25. Open Questions / TBD

The following items are officially classified as **`[E] TBD / OPEN DECISION`** requiring confirmation from University leadership:

1. **`MOD2-TBD-01` Attachment Schemas (1, 2, 3):** Physical Excel/Word templates for Teaching Load / Workload Format (**Attachment 1**), Position / Vacancy Specification Format (**Attachment 2**), and Open Positions Tracker Format (**Attachment 3**) must be obtained from HR.
2. **`MOD2-TBD-02` Statutory SCM Member Quorum:** What are the exact statutory quorum requirements and composition rules for SCM panels across Professor, Associate Professor, Assistant Professor, and Lab Technician positions?
3. **`MOD2-TBD-03` UGC Scoring Formula & Matrix:** What exact quantitative scoring formula is used to evaluate academic candidates against UGC guidelines (e.g., minimum score thresholds for shortlisting)?
4. **`MOD2-TBD-04` External Channel API Availability:** Will social media channels (LinkedIn, Facebook, Instagram) and job boards (Internshala) push applications directly via webhook APIs, or will candidates be directed to a University application portal page?
5. **`MOD2-TBD-05` LOI vs. Formal Appointment Letter Transition:** Does candidate acceptance of the LOI constitute final appointment, or does a formal Appointment Letter get issued subsequently upon completion of document verification and police/credential checks?

---
*End of Module II Functional Requirements Specification.*
