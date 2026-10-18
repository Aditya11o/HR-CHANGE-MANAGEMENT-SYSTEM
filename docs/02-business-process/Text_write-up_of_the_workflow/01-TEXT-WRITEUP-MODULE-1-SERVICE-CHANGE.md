# The Neotia University
## Department of Technical & Academic Systems
### HR Change Management & Automation System (HRMS)

---

# Module I: Core Repository & Service Change Management
## Descriptive Operational Workflow Specification (Text Write-Up)

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-02-TWU-MOD1-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **Module Covered** | **Module I — Core Repository & Service Change Management** |
| **Institution** | The Neotia University (TNU) |
| **Mentor** | Sandipan Chakraborty |
| **Date** | October 2026 |

---

## 1. Executive Summary & Operational Mission

Module I represents the foundational operational core and authoritative single source of truth for all employment records at The Neotia University. In a complex academic enterprise spanning multiple schools, administrative departments, and research cells, personnel data is subject to continuous modifications—such as annual pay increments, promotional reclassifications, supervisor transfers, inter-departmental realignments, and additional administrative appointments.

Historically, university personnel updates were executed through disjointed paper memorandums, leading to data desynchronization between departmental records and Central HR, lack of immutable audit trails, and delayed payroll reflections. 

Module I replaces these manual workflows with a tamper-evident, rule-governed digital lifecycle. The module maintains the Central Employee Master Database, renders the live Dynamic Organization Hierarchy, archives longitudinal Digital Employee Dossiers, and governs ten (10) standardized Service Change Formats (3a through 3j). Every service change is subjected to a strict two-level sequential approval gate (Central HR Operations followed by Senior Executive Management) and is enacted through an automated midnight activation engine that synchronizes directly with the University ERP.

---

## 2. Participating Institutional Actors & Governance Responsibilities

The execution of Service Change Management involves four primary institutional roles:

1. **Initiating Authority (`ACT-HRO` / `ACT-DEA` / `ACT-HOD`):**
   * Central HR Operations Officers, or School Deans and Department Heads (subject to institutional policy `CONF-01`).
   * Responsible for selecting the employee from the Central Master Directory, choosing the appropriate change format, inputting proposed attribute values, selecting a future `effective_date`, providing mandatory written justification ($\ge 20$ characters), and uploading verified evidentiary documents into the Document Vault.
2. **Level-1 Vetting Authority — Central HR Operations (`ACT-HHR` / HR Operations Manager):**
   * Acts as the primary regulatory and policy compliance gatekeeper.
   * Responsible for evaluating pay band ceilings, validating statutory UGC tenure and credential norms, inspecting uploaded verification certificates, comparing the side-by-side Before-vs-After data diff, and approving, returning, or rejecting change requests.
3. **Level-2 Sanctioning Authority — Senior Executive Management (`ACT-PRO` / `ACT-REG` / `ACT-VC`):**
   * Pro-Chancellor, Vice-Chancellor, or University Registrar.
   * Apex administrative authority responsible for assessing institutional impact, validating budgetary clearance, ensuring alignment with Governing Body and Academic Council resolutions, and granting final administrative sanction.
4. **Automated System Engine (`ACT-SYS`):**
   * Background cron scheduler, real-time WebSocket dispatcher, and transactional outbox worker.
   * Enforces field-level concurrency locks, manages the pre-activation scheduled state, executes atomic database commits at midnight, rebuilds dynamic org chart trees, appends sanction letters to digital dossiers, and ensures guaranteed at-least-once synchronization with the University ERP.

---

## 3. The Ten Standardized Service Change Formats (3a to 3j)

Every personnel modification must map to exactly one of the ten codified change formats:

* **Format 3(a) — Basic Salary & Compensation Revision:** Governs regular annual merit increments, pay band adjustments, special allowances, and salary corrections resulting from performance appraisals.
* **Format 3(b) — Designation & Promotional Realignment:** Governs academic rank advancements (e.g., Assistant Professor to Associate Professor) and administrative promotions, updating job titles and positional hierarchy.
* **Format 3(c) — Direct Reporting Authority (Supervisor) Transfer:** Modifies supervisory reporting lines in the dynamic organization chart, recalculating management hierarchy trees without altering the employee's department.
* **Format 3(d) — Departmental & School Reassignment:** Governs lateral transfers between academic departments (e.g., Computer Science to Data Science) or administrative directorates.
* **Format 3(e) — Educational & Professional Qualification Upgrade:** Archives newly acquired academic degrees (e.g., Ph.D. award, Post-Doctoral fellowships) and professional certifications into the employee's dossier, validating UGC compliance.
* **Format 3(f) — Campus Location & Physical Facility Transfer:** Governs relocations between different campuses or institutional facilities of The Neotia University.
* **Format 3(g) — Banking & Statutory Tax Details Revision:** Manages banking mandate changes, PAN/PF details, and statutory payroll routing information.
* **Format 3(h) — Additional Institutional Responsibility / Secondary Charge:** Assigns concurrent administrative charges (e.g., School Dean, Department Head, IQAC Coordinator, Chief Proctor, Hostel Warden) with defined tenures and optional administrative allowances, maintaining primary academic posts unseated.
* **Format 3(i) — Grade Pay Band & Level Progression:** Governs progression across official institutional pay bands and Seventh Central Pay Commission (7th CPC) pay matrices.
* **Format 3(j) — Employment Cadre Conversion:** Governs structural status conversions, such as transitioning from probation to confirmed service, or contractual tenure to regular cadre.

---

## 4. End-to-End Operational Narrative (Stage-by-Stage Walkthrough)

### Stage 1: Initiation & Field-Level Concurrency Pre-Validation
1. **Target Selection:** The initiator logs into the HRMS administrative portal and queries the Central Employee Directory (`ENT-MOD1-01`). The system retrieves the active baseline snapshot from `mod1_core.employees`, rendering current salary, active designation, reporting officer, department, and tenure details.
2. **Format Selection:** The initiator selects the relevant service change format (Format 3a through 3j).
3. **Concurrency Lock Enforcement (`BR-M1-004`):** Prior to instantiating the change ticket, the system executes an automated concurrency check against `mod1_core.change_requests`.
   * *Conflict Condition:* If an active change ticket affecting the same target attribute (e.g., an in-flight salary revision or designation change) is currently in `PENDING_LEVEL1` or `PENDING_LEVEL2` state, the submission engine blocks the ticket. It presents a Concurrency Guard alert: *"A service change request affecting this attribute is currently pending Level-1/Level-2 approval. Please await completion or withdraw the existing ticket."*
   * *Orthogonal Exemption:* If the second request modifies an independent attribute (e.g., updating bank details while a reporting officer change is pending), the system allows concurrent creation under an independent ticket ID.
4. **Draft Instantiation:** When cleared, the system instantiates a new change ticket in `DRAFT` state.

### Stage 2: Payload Construction, Effective Date Selection & Documentary Enclosures
1. **Proposed Payload:** The initiator inputs the proposed values (e.g., revised basic salary, proposed designation, target department).
2. **Effective Date Selection:** The initiator defines an `effective_date`. Under standard operational policy, this is a future date on which the change should legally take effect. (In exceptional retrospective cases, such as retroactive promotions, an authorized administrator can input a past date, which triggers the retrospective journaling engine upon approval).
3. **Mandatory Business Justification:** The system enforces a mandatory text field (`justification_reason`, minimum 20 characters). The initiator must record the clear administrative rationale for the alteration.
4. **Documentary Enclosure Upload (`ENT-SHR-05`):** The initiator must upload digital proof into the Document Vault:
   * *For Format 3b (Promotion):* Governing Body / Academic Council resolution minutes.
   * *For Format 3d (Transfer):* Formal transfer office memorandum issued by the Registrar.
   * *For Format 3e (Qualification):* Scanned copies of UGC-recognized degree certificates and transcripts.
5. **Submission:** Upon clicking submit, the ticket transitions to `SUBMITTED` $\rightarrow$ `PENDING_LEVEL1`, and an immutable entry is written to `shared_platform.audit_logs`.

### Stage 3: Level-1 Central HR Operations Review & Vetting Lifecycle
1. **Queue Ingestion:** The ticket appears in the Central HR Operations Review Inbox with an amber pending status and an active SLA clock.
2. **Multi-Point Verification:** The HR Operations Officer evaluates four critical dimensions:
   * *Pay Scale & Salary Band Compliance:* Ensures proposed compensation revisions conform to university pay slabs and budgetary limits.
   * *Statutory Service Rules & UGC Compliance:* Verifies minimum qualification years, publication benchmarks, and cadre eligibility.
   * *Evidentiary Authenticity:* Validates uploaded certificates, checking file hashes and institutional signatures in `ENT-SHR-05`.
   * *Side-by-Side Data Diff Inspection:* Inspects an automated Before-vs-After comparison grid generated by the system, highlighting exact attribute mutations.
3. **Decision Gateways:**
   * *Return for Clarification (`RETURNED_FOR_CLARIFICATION`):* If documents are missing or clarifications are required, HR inputs specific deficiency remarks. The ticket loops back to the initiator. The initiator rectifies the deficiency and resubmits.
   * *Rejection (`REJECTED`):* If the request violates policy, HR rejects it with written reasons. The ticket is permanently closed, and the audit log records the rejection.
   * *Endorsement (`PENDING_LEVEL2`):* If verified, HR signs off. The ticket transitions to `PENDING_LEVEL2` and routes to the Senior Management queue.

### Stage 4: Level-2 Senior Management Executive Sanction
1. **Executive Review:** The Pro-Chancellor, Vice-Chancellor, or Registrar accesses the Executive Approval Dashboard. The screen presents the employee's career snapshot, proposed changes, HR Operations' endorsement remarks, financial impact summaries, and links to supporting proofs.
2. **Decision Branching:**
   * *Executive Veto (`REJECTED_BY_MGMT`):* If leadership rejects the request due to institutional budgetary constraints or policy realignment, the ticket is marked rejected with executive remarks.
   * *Executive Sanction (`APPROVED_SCHEDULED`):* When executive approval is granted, the ticket transitions to `APPROVED_SCHEDULED`.

### Stage 5: The Scheduled Invariant State & Revocation Protocol
1. **The Scheduled Invariant (`BR-M1-005`):** Although approved by Senior Management, the active employee record in `mod1_core.employees` remains strictly unaltered. The system maintains an invariant: *no change may mutate the active master record prior to 00:00:00 of its effective date*.
2. **Pre-Activation Revocation Window (`BP-M1-006`):** Prior to midnight of the effective date, an authorized Senior Executive or HR Administrator can cancel the approved change (e.g., if an employee tenders resignation before a scheduled promotion takes effect).
   * The user clicks `REVOKE_SCHEDULED_CHANGE` and inputs a mandatory cancellation justification.
   * Ticket status transitions immediately to `REVOKED`.
   * The master database remains completely untouched.
   * Actor credentials, revocation reason, and timestamps are committed to the immutable audit log.
3. **Post-Activation Reversal Boundary:** Once `effective_date` has elapsed and modified the master record, simple revocation is barred. Any alteration requires a formal reverse compensating change request routed through standard two-level governance.

### Stage 6: Automated Midnight Activation & Master Database Mutation
1. **Cron Trigger:** Every night at 00:01:00 IST, the Automated System Engine (`ACT-SYS`) executes the daily activation job.
2. **Batch Query:** The engine queries `mod1_core.change_requests` for all records satisfying `status = 'APPROVED_SCHEDULED'` AND `effective_date <= CURRENT_DATE`.
3. **Atomic Local Transaction (`BP-M1-006`):** To guarantee zero partial updates or data desynchronization, all modifications execute inside a single PostgreSQL ACID transaction:
   * *Master Record Mutation:* Executes SQL update statements on `mod1_core.employees`, writing new basic salary, designation, department, or grade pay values.
   * *Hierarchy Realignment:* If the change affects a supervisor (`Format 3c`) or department (`Format 3d`), parent-child edges in `mod1_core.org_nodes` are recomputed, preventing orphaned nodes or cyclical loops.
   * *Digital Dossier Archival:* The engine auto-generates a signed digital Sanction Order PDF, registers it in `ENT-SHR-05`, and appends it to the employee's longitudinal file in `mod1_core.digital_dossiers`.
   * *Immutable Audit Logging:* A comprehensive JSON diff capturing before-and-after states, actor IDs, IP addresses, and UTC timestamps is committed to `shared_platform.audit_logs`.
   * *Status Transition:* Ticket status updates to `ACTIVE`.

### Stage 7: Real-Time Event Dispatch & Outbox ERP Synchronization
1. **Real-Time Client Invalidation:** Within milliseconds of transaction commit, the in-memory domain event bus (`EventEmitter2`) emits `service_change.activated`. The Socket.IO real-time gateway intercepts this event and broadcasts `org-tree:invalidated` to client web sessions. This triggers dynamic org chart re-rendering without page reloads and pushes personal confirmation toasts to the employee portal.
2. **Transactional Outbox ERP Synchronization (`BP-M1-007`):** Within the same local database transaction as the master mutation, an outbound integration event is written to `shared_platform.outbox_events` with status `PENDING`.
3. **Guaranteed Delivery:** A persistent BullMQ queue worker polls `outbox_events` every 30 seconds and transmits the payload to the University ERP platform via the approved transport protocol (`REQ-TBD-01`). Upon receiving HTTP 200/ACK from ERP, the outbox record updates to `DELIVERED`. In case of ERP downtime or network timeout, exponential backoff retries (up to 10 attempts over 24 hours) ensure guaranteed eventual consistency without system lockup.

---

## 5. Dynamic Organization Hierarchy Realignment Rules

The Dynamic Organization Chart (`ENT-MOD1-02`) operates as a directed acyclic graph (DAG):

1. **Acyclicity Invariant (`BR-M1-003`):** No employee may report directly or indirectly to themselves. The system performs cycle detection prior to approving Format 3(c) supervisor reassignments.
2. **Orphan Prevention:** When a supervisor or department head is transferred or separated, the system flags all direct reportees as *temporarily unseated* and prompts HR to assign an interim reporting authority.
3. **Secondary Node Linking (Format 3h):** When a faculty member is assigned an additional institutional charge (e.g., Dean or Chief Proctor), the system creates a secondary role node in the org tree linked to the primary employment node, preserving dual visibility without disrupting academic reporting lines.

---

## 6. Cross-Module Architectural Handshakes

Module I serves as the data hub through five foundational handshakes:

1. **`BP-XMOD-001` (Candidate Onboarding Handshake):** Module II converts a candidate with an accepted Letter of Intent (LOI) into an active employee in Module I on Day 1, minting the unique `employee_id`, generating the initial master record, and initializing the digital dossier.
2. **`BP-XMOD-002` (Resignation Replacement Bypass):** When an employee tenders resignation and the School Dean logs acceptance in Module I, the system immediately bypasses annual requisition limits and opens an urgent replacement MRF in Module II with an active countdown clock.
3. **`BP-XMOD-003` (Master Employment Baseline Feed):** Module I continuously feeds active employment records, confirmed designations, supervisory relationships, and anniversary dates into Module III to drive performance eligibility scans.
4. **`BP-XMOD-004` (Appraisal Outcome Handshake):** Approved annual increments, promotions, or confirmations in Module III automatically generate pre-populated Change Requests (Format 3a / 3b) in Module I, routing directly through Level-1/Level-2 governance for midnight execution.
5. **`BP-XMOD-006` (Transactional ERP Outbox Sync):** Master record modifications emit outbound event payloads to the University ERP platform via the transactional outbox pattern.
