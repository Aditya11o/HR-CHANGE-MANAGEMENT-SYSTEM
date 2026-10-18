# The Neotia University
## Department of Technical & Academic Systems
### HR Change Management & Automation System (HRMS)

---

# Module III: 3-Track Performance Management Engine
## End-to-End Graphic Workflow & Lifecycle Specification

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-02-GIW-MOD3-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **Module Covered** | **Module III — 3-Track Performance Management Engine** |
| **Institution** | The Neotia University (TNU) |
| **Mentor** | Sandipan Chakraborty |
| **Date** | October 2026 |

---

## 1. Executive Summary & Module Scope

Module III automates performance evaluation across the university's diverse employment cadres through three segregated, non-interfering evaluation tracks:

1. **Track 1: Group-D / Band-I Operational Staff:** Monthly evaluation cadence with strict SLA enforcement:
   * 1st of month: Automated form dispatch to supervisors.
   * 7th of month: Standard submission deadline.
   * 8th–10th: 3-day automated grace period with daily SMS/Email chasers.
   * 10th at 23:59:59 IST: Automated hard lockout (`AUTO_LOCKED`); non-compliance flagged to HR.
   * VP-Administration exclusive approval authority.
   * Annual 12-month parameter-weighted average synthesis and increment disbursement.
2. **Track 2: General Administrative Staff (KRA/KPI Track):**
   * 30 days from Date of Joining: Joint goal-setting (3–5 measurable KRAs).
   * Joint version lock by HR and Senior Management.
   * Quarterly review cadence (Q1–Q4) with automated reminders and escalation ladder.
   * Annual consolidated scoring and automated Module I handshake (`BP-XMOD-004`).
3. **Track 3: Academic Faculty (Statutory ECM Route):**
   * Monthly 10th background scan identifying faculty with completed probation and $\ge 12$ months continuous service.
   * Certified eligibility roster issued to Registrar.
   * 7 working days for digital Self-Appraisal (Enclosure 1) submission.
   * **4-Unit Parallel Independent Verification Gate:** (1) School Dean, (2) Dean R&D, (3) Director of Placement & Internships, (4) Central HR Operations, featuring a 3-day dispute clarification return loop.
   * Monthly statutory Evaluation Committee Meeting (ECM) panel scoring.
   * TNU Protocol Benchmark Matrix (Enclosure 3) composite calculation: Teaching (40%), Research (30%), Placement (15%), Institutional Service (15%).
   * Executive management sanction, auto-generation of compensation revision letters, and payroll enactment via Module I.

---

## 2. Graphic Workflow Diagram (Module III)

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#1e293b', 'primaryTextColor': '#f8fafc', 'primaryBorderColor': '#38bdf8', 'lineColor': '#64748b', 'secondaryColor': '#0f172a', 'tertiaryColor': '#1e293b'}}}%%
flowchart TD
    %% Styling Classes
    classDef t1Node fill:#0c4a6e,stroke:#38bdf8,stroke-width:2px,color:#f8fafc;
    classDef t2Node fill:#064e3b,stroke:#34d399,stroke-width:2px,color:#f8fafc;
    classDef t3Node fill:#2e1065,stroke:#c084fc,stroke-width:2px,color:#f8fafc;
    classDef lockNode fill:#450a0a,stroke:#f87171,stroke-width:2px,color:#fecaca;
    classDef reviewNode fill:#312e81,stroke:#818cf8,stroke-width:2px,color:#f8fafc;
    classDef checkNode fill:#1e1b4b,stroke:#818cf8,stroke-width:2px,color:#ffffff;
    classDef handoffNode fill:#14532d,stroke:#4ade80,stroke-width:2px,color:#f0fdf4;

    %% -------------------------------------------------------------
    %% TRACK 1: GROUP-D STAFF
    %% -------------------------------------------------------------
    subgraph TRACK1 ["TRACK 1: GROUP-D / BAND-I STAFF (MONTHLY CADENCE & HARD LOCK)"]
        direction TB
        G_DISP["<b>1. 1st of Every Month:</b> Digital Forms Dispatched<br/><i>Auto-routed to evaluating HODs / Supervisors (BP-M3-001)</i>"]:::t1Node
        G_EVAL["<b>2. 1st–7th of Month:</b> Supervisory Evaluation<br/><i>Rates Task Diligence, Conduct, Attendance & Hygiene (SLA-M3-01)</i>"]:::t1Node
        G_GRACE["<b>3. 8th–10th:</b> 3-Day Automated Grace Period<br/><i>Daily SMS & Email reminders sent to Supervisor (SLA-M3-02)</i>"]:::t1Node
        G_LOCK["<b>4. 10th at 23:59:59 IST: Automated Hard Lockout</b><br/><i>Unsubmitted forms locked permanently; HR non-compliance alert (SLA-M3-03)</i>"]:::lockNode
        G_VP{"<b>5. VP-Administration Exclusive Review</b><br/><i>Approves or Rejects Monthly Ratings (BP-M3-004)</i>"}:::reviewNode
        G_ANNUAL["<b>6. 12-Month Milestone Synthesis</b><br/><i>Parameter-weighted composite annual score compiled (BP-M3-006)</i>"]:::t1Node
        G_PROB{"<b>7. Probation Verification Gate</b><br/><i>Has employee completed statutory probation?</i>"}:::checkNode
        G_INC["<b>8. Pre-Defined Slab Increment</b><br/><i>Auto-dispatched to Payroll / Module I Change Engine</i>"]:::handoffNode

        G_DISP --> G_EVAL --> G_GRACE --> G_LOCK --> G_VP
        G_VP -- " Approved " --> G_ANNUAL --> G_PROB
        G_PROB -- " Confirmed " --> G_INC
    end

    %% -------------------------------------------------------------
    %% TRACK 2: GENERAL STAFF KRA
    %% -------------------------------------------------------------
    subgraph TRACK2 ["TRACK 2: GENERAL ADMINISTRATIVE STAFF (KRA/KPI CADENCE)"]
        direction TB
        K_GOAL["<b>1. 30 Days from Date of Joining:</b> Goal Setting<br/><i>Employee & Supervisor configure 3–5 measurable KRAs (SLA-M3-04)</i>"]:::t2Node
        K_LOCK["<b>2. Joint Annual Version Lock</b><br/><i>HR Operations & Management freeze annual targets (BP-M3-010)</i>"]:::t2Node
        K_CADENCE["<b>3. Quarterly Review Cycle (Q1–Q4)</b><br/>━━━━━━━━━━━━━━━━━━━━━━━━━━━━━<br/>• T-90d Cycle Notice -> T-20d Mid-Cycle Reminder<br/>• 15d Employee Self-Rating Window (SLA-M3-05)<br/>• 7d Supervisory Final Scoring & Observations (SLA-M3-06)</i>"]:::t2Node
        K_ESCALATE{"<b>Review Completed on Time?</b>"}:::checkNode
        K_WARN["<b>Escalation Sequence (BP-M3-011)</b><br/>• Day +7: Amber Warning Alert<br/>• Day +14: Escalated to School Dean<br/>• Day +21: System Hard Lockout"]:::lockNode
        K_ANNUAL["<b>4. Consolidated Q1–Q4 Annual Synthesis</b><br/><i>System computes cumulative weighted performance score</i>"]:::t2Node
        K_HANDOFF["<b>5. Module I Handshake (BP-XMOD-004)</b><br/><i>Auto-injects Format 3(a) Increment or 3(b) Promotion ticket</i>"]:::handoffNode

        K_GOAL --> K_LOCK --> K_CADENCE --> K_ESCALATE
        K_ESCALATE -- " Missed Deadline " --> K_WARN
        K_ESCALATE -- " Completed " --> K_ANNUAL --> K_HANDOFF
    end

    %% -------------------------------------------------------------
    %% TRACK 3: FACULTY ECM ROUTE
    %% -------------------------------------------------------------
    subgraph TRACK3 ["TRACK 3: UNIVERSITY FACULTY ANNUAL APPRAISAL (STATUTORY ECM ROUTE)"]
        direction TB
        F_SCAN["<b>1. Monthly 10th Eligibility Scan Engine</b><br/><i>Identifies faculty completing probation & ≥12m continuous service (SLA-M3-07)</i>"]:::t3Node
        F_ROSTER["<b>2. Certified Roster Issued to Registrar</b><br/><i>HR validates and freezes monthly eligible appraisal cohort</i>"]:::t3Node
        F_SELF["<b>3. 7-Working-Day Self-Appraisal Window</b><br/><i>Faculty submits digital Enclosure 1 dossier with research & teaching proofs (SLA-M3-08)</i>"]:::t3Node
        
        subgraph F_VET ["4-UNIT INDEPENDENT PARALLEL VERIFICATION GATE (BP-M3-016)"]
            direction TB
            V_DEAN["<b>Unit 1: School Dean</b><br/><i>Teaching Load & Student Feedback</i>"]:::t3Node
            V_RND["<b>Unit 2: Dean R&D</b><br/><i>Scopus Papers, Patents & Grants</i>"]:::t3Node
            V_PLACE["<b>Unit 3: Placement Head</b><br/><i>Industry Projects & Internships</i>"]:::t3Node
            V_HR["<b>Unit 4: Central HR</b><br/><i>Leaves, Conduct & Service Rules</i>"]:::t3Node
        end

        F_LOOP{"<b>Any Discrepancies Flagged?</b>"}:::checkNode
        F_REMED["<b>Clarification Return Loop (BP-M3-017)</b><br/><i>Faculty has 3-day window to rectify; unrectified >48h deferred to next month</i>"]:::lockNode

        F_ECM["<b>4. Statutory ECM Panel Convened</b><br/><i>VC (Chair), Deans, Registrar & External Subject Experts evaluate dossier (BP-M3-018)</i>"]:::reviewNode
        F_MATRIX["<b>5. TNU Benchmark Matrix Synthesis (Encl 3)</b><br/><i>Teaching (40%), Research (30%), Placement (15%), Service (15%)</i>"]:::t3Node
        F_SANCTION{"<b>Senior Management Sanction Gate</b>"}:::checkNode
        F_LETTER["<b>6. Automated Letter & Payroll Enactment</b><br/><i>Auto-injects into Module I; effective in next immediate salary cycle (SLA-M3-09)</i>"]:::handoffNode

        F_SCAN --> F_ROSTER --> F_SELF --> F_VET --> F_LOOP
        F_LOOP -- " Queries Raised " --> F_REMED
        F_REMED -.->|" Rectified Evidentiary Proof "| F_VET
        F_LOOP -- " All 4 Units Cleared " --> F_ECM --> F_MATRIX --> F_SANCTION
        F_SANCTION -- " Sanctioned " --> F_LETTER
    end

    %% -------------------------------------------------------------
    %% INTER-MODULE CROSS-HANDSHAKES
    %% -------------------------------------------------------------
    G_INC ==>|"<b>BP-XMOD-004</b><br/>Service Change Injection"| MOD1_RECEIVER[("<b>Module I: Service Change Engine</b><br/><i>Level-1/Level-2 Governance</i>")]:::handoffNode
    K_HANDOFF ==>|"<b>BP-XMOD-004</b><br/>Service Change Injection"| MOD1_RECEIVER
    F_LETTER ==>|"<b>BP-XMOD-004</b><br/>Service Change Injection"| MOD1_RECEIVER
```

---

## 3. Step-by-Step Workflow Walkthrough

### Track 1: Group-D / Band-I Staff Lifecycle
1. **1st of Month:** Background worker auto-dispatches digital evaluation forms (`ENT-MOD3-01`) to supervisors and HODs (`BP-M3-001`).
2. **1st–7th Due Date:** Supervisors evaluate attendance, conduct, task diligence, and cleanliness on structured 5-point rubrics (`BP-M3-002`, `SLA-M3-01`).
3. **8th–10th Grace Window:** Automated 3-day grace period with high-priority SMS and email alerts dispatched daily to supervisors (`SLA-M3-02`).
4. **10th at 23:59:59 IST Hard Lockout:** System executes an automated hard lock (`AUTO_LOCKED`). Unsubmitted forms lock permanently; an administrative non-compliance notice is auto-escalated to HR Operations (`REQ-MOD3-04`).
5. **VP-Administration Review:** Submitted evaluations route exclusively to the Vice President – Administration for executive sign-off (`BP-M3-004`).
6. **12-Month Anniversary Synthesis:** Exactly 1 year from the employee's Date of Joining (DOJ), the system calculates the 12-month parameter-weighted composite score (`BP-M3-006`).
7. **Probation Verification Gate:** The system verifies probation completion (`BR-M3-009`). If confirmed, predefined increment slabs are applied and dispatched to payroll via Module I (`BP-XMOD-004`).

### Track 2: General Administrative Staff (KRA/KPI Track)
1. **30-Day Goal Setting:** Within 30 calendar days from Date of Joining, the employee and supervisor formulate 3 to 5 measurable Key Result Areas (KRAs) with quantitative KPI targets (`BP-M3-009`, `SLA-M3-04`).
2. **Joint Version Lock:** HR Operations and Senior Management review and freeze the target sheet, rendering it immutable for the annual cycle (`BP-M3-010`).
3. **Quarterly Review Cadence (Q1–Q4):**
   * T-90 days: Advance quarterly cycle notice.
   * T-20 days: Mid-review reminder.
   * 15 calendar days: Employee self-rating submission window (`SLA-M3-05`).
   * 7 calendar days: Supervisory scoring, observations, and recommendations window (`SLA-M3-06`).
4. **Escalation Protocol:** If review is missed: Day 0 notice $\rightarrow$ Day +7 warning $\rightarrow$ Day +14 Dean escalation $\rightarrow$ Day +21 hard system lockout (`AUTO_LOCKED`). Unlocking requires formal approval from the Registrar.
5. **Annual Synthesis & Handshake:** Cumulative quarterly scores are synthesized into an annual rating, automatically injecting a Service Change Request (Format 3a or 3b) into Module I (`BP-XMOD-004`).

### Track 3: Academic Faculty (Statutory ECM Route)
1. **Monthly 10th Scan Engine:** Background worker executes on the 10th of every month, scanning for faculty who have completed probation and achieved $\ge 12$ months of continuous service (`BP-M3-014`, `SLA-M3-07`).
2. **Certified Roster:** HR verifies and dispatches the certified eligibility roster to the Registrar within 24 hours.
3. **7-Working-Day Self-Appraisal:** Qualified faculty submit a digital Enclosure 1 dossier containing evidence of publications, student feedback, and workloads within 7 working days (`BP-M3-015`, `SLA-M3-08`).
4. **4-Unit Independent Parallel Verification Gate:** Dossier routes simultaneously to:
   * *Unit 1 (School Dean):* Vetting teaching contact hours, pedagogy, and student feedback indices.
   * *Unit 2 (Dean R&D):* Verifying Scopus/SCI indexed papers, impact factors, patents, and funded grants.
   * *Unit 3 (Director of Placement & Internships):* Verifying industry projects, internships, and corporate linkages.
   * *Unit 4 (Central HR Operations):* Verifying leave records, statutory compliance, and university service history.
5. **Clarification Return Loop (`BP-M3-017`):** Verifying units can return queries (`RETURNED_FOR_CLARIFICATION`). Faculty have 3 working days to provide corrected proofs. Unresolved queries 48 hours prior to the scheduled ECM meeting cause the candidate's docket to be deferred to the subsequent monthly session, allowing cleared candidates to proceed.
6. **Statutory ECM Committee Session:** Panel convenes with Vice-Chancellor (Chair), School Deans, Registrar, and external subject experts. Committee members enter marks digitally in Enclosure 2 scorecards (`BP-M3-018`).
7. **TNU Benchmark Matrix Synthesis (Enclosure 3):** System calculates the composite score using the approved formula:
   $$\text{Composite Score} = (0.40 \times \text{Teaching}) + (0.30 \times \text{Research}) + (0.15 \times \text{Placement}) + (0.15 \times \text{Service})$$
8. **Sanction & Enactment:** Management sanctions the revision (Standard Increment, Accelerated Increment, Promotion, Confirmation, Probation Extension, or PIP). The system auto-generates formal revision letters and injects the change into Module I for enactment in the next immediate payroll cycle (`BP-XMOD-004`, `SLA-M3-09`).

---

## 4. Statutory Performance SLA Matrix

| SLA Identifier | Governed Performance Action | Statutory SLA Window / Cutoff | Escalation Pathway & Non-Compliance Action |
|---|---|---|---|
| `SLA-M3-01` | **Group-D Evaluation Due Date** | 7th of Every Month | System initiates 3-day grace period with reminder toasts |
| `SLA-M3-02` | **Group-D Grace Period Reminders** | Daily on 8th, 9th, and 10th | High-priority SMS and email alerts sent to evaluating supervisor |
| `SLA-M3-03` | **Group-D Automated Lockout** | 10th of Month at 23:59:59 IST | Form auto-locks permanently; non-compliance logged to HR |
| `SLA-M3-04` | **Staff KRA Goal Setting** | 30 Days from Date of Joining | Overdue alert dispatched to Direct Supervisor & Head of HR |
| `SLA-M3-05` | **Staff Quarterly Self-Review** | 15 Calendar Days from Open | Automated reminder to Employee & Direct Supervisor |
| `SLA-M3-06` | **Staff Supervisor Review Verification** | 7 Calendar Days from Self-Review | Escalation ticket dispatched to HR Operations Manager |
| `SLA-M3-07` | **Faculty Eligibility Scan** | 10th of Every Month at 00:01 IST | Automated generation and certified dispatch to Registrar |
| `SLA-M3-08` | **Faculty Self-Appraisal Submission** | 7 Working Days from Notice | Formal reminder to Faculty Member & School Dean |
| `SLA-M3-09` | **Faculty Increment Enactment** | Next Immediate Payroll Cycle | Financial discrepancy escalation to Chief Finance Officer |

---

## 5. Cross-Module Appraisal Outcome Handshake (`BP-XMOD-004`)

When Senior Management sanctions an appraisal outcome in Module III:
1. The system creates a pre-populated Change Request ticket in Module I (`ENT-MOD1-04`):
   * *Salary Increment:* Format 3(a) with new basic pay and effective date.
   * *Promotion:* Format 3(b) with new designation and grade band.
2. The ticket is tagged with source reference `SOURCE_MOD3_APPRAISAL` and the compiled scorecard metadata pointer (`ENT-SHR-05`).
3. The ticket bypasses redundant data entry and routes directly for midnight scheduled activation and ERP payroll synchronization.


