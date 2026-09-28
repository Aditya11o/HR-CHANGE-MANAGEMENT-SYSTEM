# Requirements Traceability Matrix
## University HR Change Management & Automation System

**Document Identifier:** `DOC-01-RTM-04`  
**Phase:** Phase 1 — Requirements Engineering & Specification (Documentation-Only)  
**Location:** `docs/01-requirements/04-REQUIREMENTS-TRACEABILITY.md`  
**Status:** Approved Requirements Traceability Baseline  
**Date:** September 29, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Document Purpose

This document establishes the formal **Requirements Traceability Matrix (RTM)** for the University HR Change Management & Automation System. Its purpose is to demonstrate end-to-end documentation lineage, ensuring that every business mandate originating in the official source briefs maps directly to an atomic requirement, links to its corresponding Functional Requirement (FRD), and indicates its downstream documentation dependencies.

> [!IMPORTANT]
> **Documentation Traceability Only:**  
> In strict compliance with the current documentation-only phase, this matrix tracks **DOCUMENTATION LINEAGE ONLY**. It does not claim implementation traceability, as no application code, database migrations, or API endpoints exist yet.

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                 DOCUMENTATION TRACEABILITY FLOW                                  │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│ Official Source Brief (PDF)                                                                     │
│        ↓                                                                                         │
│ Traceability ID & Requirement Statement                                                          │
│        ↓                                                                                         │
│ Functional Module Domain                                                                         │
│        ↓                                                                                         │
│ Functional Requirement Mapping (docs/03-functional-requirements/)                                │
│        ↓                                                                                         │
│ Future Documentation Target (Phases 02, 04, 05, 06, 08, 09, 10, 11, 12, 13)                      │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Module I Traceability: HR Change Management & Core DB

| Official Source Reference | Baseline Traceability ID | Requirement Statement (Abridged) | Functional Requirement Mapping | Downstream Documentation Targets |
|---|---|---|---|---|
| Module I PDF, Structure (1) | `MOD1-CDB-01` | Central Database of all Employees fully reflected in ERP. | `MOD1-CDB-REQ-01` to `04` | Phase 08 (ERD: `employees`), Phase 09 (API: Master Data), Phase 11 (Security: PII) |
| Module I PDF, Structure (2) | `MOD1-ORG-01` | Dynamic Organization Chart auto-updating upon approved changes. | `MOD1-ORG-REQ-01` to `04` | Phase 06 (Workflows: DAG Realignment), Phase 08 (ERD: hierarchy DAG), Phase 10 (UI: Org Tree) |
| Module I PDF, Objective | `MOD1-FIL-01` | Connected Digital Employee File aggregating longitudinal service history. | `MOD1-FIL-REQ-01` to `02` | Phase 08 (ERD: `employee_dossier`), Phase 10 (UI: Employee Profile) |
| Module I PDF, Structure 3(a) | `MOD1-CHG-01(a)` | Standardized digital format for Change in Salary. | `MOD1-CHG-REQ-01` to `02` | Phase 06 (Workflows: Form a), Phase 08 (ERD: `service_change_requests`), Phase 10 (UI) |
| Module I PDF, Structure 3(b) | `MOD1-CHG-01(b)` | Standardized digital format for Change in Designation. | `MOD1-CHG-REQ-03` to `04` | Phase 06 (Workflows: Form b), Phase 08 (ERD: designations), Phase 10 (UI) |
| Module I PDF, Structure 3(c) | `MOD1-CHG-01(c)` | Standardized digital format for Change in Reportee. | `MOD1-CHG-REQ-05` to `06` | Phase 06 (Workflows: Form c), Phase 08 (ERD: reporting edges), Phase 10 (UI) |
| Module I PDF, Structure 3(d) | `MOD1-CHG-01(d)` | Standardized digital format for Change in Reporting Authority. | `MOD1-CHG-REQ-07` to `08` | Phase 06 (Workflows: Form d), Phase 08 (ERD: reporting edges), Phase 10 (UI) |
| Module I PDF, Structure 3(e) | `MOD1-CHG-01(e)` | Standardized digital format for Change in Level. | `MOD1-CHG-REQ-09` to `10` | Phase 06 (Workflows: Form e), Phase 08 (ERD: salary bands), Phase 10 (UI) |
| Module I PDF, Structure 3(f) | `MOD1-CHG-01(f)` | Standardized digital format for Change in Department/School. | `MOD1-CHG-REQ-11` to `12` | Phase 06 (Workflows: Form f), Phase 08 (ERD: departments), Phase 10 (UI) |
| Module I PDF, Structure 3(g) | `MOD1-CHG-01(g)` | Standardized digital format for Change in Location. | `MOD1-CHG-REQ-13` | Phase 06 (Workflows: Form g), Phase 08 (ERD: campus locations), Phase 10 (UI) |
| Module I PDF, Structure 3(h) | `MOD1-CHG-01(h)` | Standardized digital format for Additional Responsibility Added. | `MOD1-CHG-REQ-14` to `15` | Phase 06 (Workflows: Form h), Phase 08 (ERD: secondary roles), Phase 10 (UI) |
| Module I PDF, Structure 3(i) | `MOD1-CHG-01(i)` | Standardized digital format for Change in Qualifications. | `MOD1-CHG-REQ-16` to `17` | Phase 06 (Workflows: Form i), Phase 08 (ERD: qualifications), Phase 10 (UI) |
| Module I PDF, Structure 3(j) | `MOD1-CHG-01(j)` | Extensible format for Any Other Employee Service Condition. | `MOD1-CHG-REQ-18` | Phase 06 (Workflows: Form j), Phase 08 (ERD: JSONB custom fields), Phase 10 (UI) |
| Module I PDF, Approvals (a, b) | `MOD1-APP-01` | Mandatory 2-level approval hierarchy: HR Level then Senior Management. | `MOD1-APP-REQ-01` to `02` | Phase 05 (User Roles: HR & Mgmt), Phase 06 (Workflows: 2-stage approval FSM) |
| Module I PDF, Methodology | `MOD1-DAT-01` | Database change methodology with effective date, audit trail, version history. | `MOD1-EFF-REQ-01`, `MOD1-AUD-REQ-01`, `MOD1-VER-REQ-01` | Phase 06 (Workflows: Effective Date Scheduler), Phase 08 (ERD: `audit_logs`, temporal tables) |
| Module I PDF, Reports | `MOD1-REP-01` | Extensible reporting engine with real-time generation and format management. | `MOD1-REP-REQ-01` to `03` | Phase 09 (API: Report Execution), Phase 10 (UI: Reports), Phase 13 (Reporting Specifications) |

---

## 3. Module II Traceability: Recruitment & Selection Automation

| Official Source Reference | Baseline Traceability ID | Requirement Statement (Abridged) | Functional Requirement Mapping | Downstream Documentation Targets |
|---|---|---|---|---|
| Module II PDF, Section 1(a) | `MOD2-MP-FAC-01` | Academic manpower planning advance trigger $\ge$ 4 months before semester. | `MOD2-REC-REQ-02` | Phase 06 (Workflows: Manpower Initiation), Phase 12 (Notifications & SLA Engine) |
| Module II PDF, Section 1(b) | `MOD2-MP-FAC-02` | Deans submit requirements + teaching load (Attachment 1) within 15 days. | `MOD2-REC-REQ-03` | Phase 06 (Workflows: Dean Submission FSM), Phase 12 (SLA: 15-day countdown) |
| Module II PDF, Section 1(c-f) | `MOD2-REC-01` | HR 3-month vetting, 7-day Pro-Chancellor approval, 7-day ad launch. | `MOD2-REC-REQ-04` to `06` | Phase 06 (Workflows: Vetting & Ad Launch), Phase 12 (SLA: 7-day timers) |
| Module II PDF, Section 1(g) | `MOD2-MP-NF-01` | Non-Academic manpower planning restricted to 1 planned requisition per year. | `MOD2-REC-REQ-07` | Phase 06 (Workflows: Staff Planning), Phase 08 (ERD: Quota Constraint) |
| Module II PDF, Section 1(i) | `MOD2-RES-01` | Resignation acceptance by Dean starts urgent replacement clock, notifies HR. | `MOD2-REC-REQ-08` to `09` | Phase 06 (Workflows: Urgent Replacement), Phase 12 (SLA: Urgent countdown) |
| Module II PDF, Section 2 & 3 | `MOD2-TRK-01` | Open Positions Tracker in Attachment 3 maintained within 30 days; weekly reports. | `MOD2-REC-REQ-11` to `12` | Phase 08 (ERD: `open_positions_tracker`), Phase 13 (Reports: Executive Weekly) |
| Module II PDF, Section 4 | `MOD2-SRC-01` | Capture applications into Central CV Database across multiple sourcing channels. | `MOD2-REC-REQ-13` | Phase 08 (ERD: `cv_database`), Phase 09 (API: Sourcing Ingestion) |
| Module II PDF, Section 5 | `MOD2-SRC-02` | Auto-segregate, classify, and shortlist CVs against UGC and statutory norms. | `MOD2-REC-REQ-14` | Phase 06 (Workflows: Rules Engine Shortlisting), Phase 09 (API: Screening) |
| Module II PDF, Section 6 & 7 | `MOD2-RCS-01` | Recruiter Calling Sheet (RCS) phone screening reviewed by HR, approved by Mgmt. | `MOD2-REC-REQ-15` to `16` | Phase 06 (Workflows: RCS Approval), Phase 08 (ERD: `recruiter_calling_sheets`) |
| Module II PDF, Selection A | `MOD2-SEL-FAC-01` | Academic SCM statutory committee with external expert and digital scoring sheet. | `MOD2-REC-REQ-17` to `18` | Phase 05 (User Roles: SCM Panel & Expert), Phase 06 (Workflows: Academic SCM) |
| Module II PDF, Selection B | `MOD2-SEL-NF-01` | Non-Academic 3-Round interview assessing Job Knowledge, Communication, Attitude. | `MOD2-REC-REQ-19` to `20` | Phase 05 (User Roles: Interviewers), Phase 06 (Workflows: 3-Tier Staff Interview) |
| Module II PDF, Selection A(e), B(b) | `MOD2-ONB-01` | Automated LOI generation, "Yet to Join" pipeline tracking, pre-onboarding alerts. | `MOD2-REC-REQ-21` to `23` | Phase 06 (Workflows: Onboarding), Phase 08 (ERD: `letters_of_intent`), Phase 12 (SLA) |

---

## 4. Module III Traceability: Performance Management Automation

| Official Source Reference | Baseline Traceability ID | Requirement Statement (Abridged) | Functional Requirement Mapping | Downstream Documentation Targets |
|---|---|---|---|---|
| Group-D Brief, Section 1 & 2 | `MOD3-GD-EVAL-01` | Monthly Group-D rating form (Enclosure 1) to HOD; due 7th; grace to 10th; auto-lock. | `MOD3-GD-REQ-01` to `08` | Phase 06 (Workflows: Monthly Rating FSM), Phase 12 (SLA: 7th/10th auto-lock) |
| Group-D Brief, Section 2(b) | `MOD3-GD-APP-01` | Mandatory VP – Administration approval before evaluation is final. | `MOD3-GD-REQ-09` | Phase 05 (User Roles: VP-Admin), Phase 06 (Workflows: VP Gate) |
| Group-D Brief, Section 3 | `MOD3-GD-REP-01` | Automated collation of submitted monthly forms into Monthly Report (Enclosure 2). | `MOD3-GD-REQ-10` | Phase 08 (ERD: monthly collations), Phase 13 (Reports: Enclosure 2 Report) |
| Group-D Brief, Section 4 | `MOD3-GD-ANN-01` | Annual report at 1-year service from DOJ; parameter-wise weighted average scores. | `MOD3-GD-REQ-11` to `13` | Phase 06 (Workflows: Annual Anniversary Trigger), Phase 13 (Reports: Weighted Aggregation) |
| Group-D Brief, Section 5(b) | `MOD3-GD-PRB-01` | Mandatory probation verification gate before compensation review. | `MOD3-GD-REQ-14` | Phase 06 (Workflows: Probation Validation Gate), Phase 08 (ERD: probation flags) |
| KRA/KPI Brief, Stage 1 | `MOD3-KRA-SET-01` | New joiner KRA/KPI setup within 30 days of DOJ; locked by HR & Management. | `MOD3-KRA-REQ-01` to `02` | Phase 06 (Workflows: Goal Setting FSM), Phase 12 (SLA: 30-day countdown) |
| KRA/KPI Brief, Stage 2 | `MOD3-KRA-QTR-01` | 4 quarterly review cycles (Q1–Q4): 90-day intimation, 20-day reminder, 15-day submit, 7-day supervisor verify. | `MOD3-KRA-REQ-03` to `04` | Phase 06 (Workflows: Quarterly Cadence), Phase 12 (SLA: 4-tier timing sequence) |
| KRA/KPI Brief, Stage 3 | `MOD3-KRA-INT-01` | Annual appraisal outcome feeds directly into Module I change request. | `MOD3-KRA-REQ-05` | Phase 06 (Workflows: Cross-Module Handshake), Phase 09 (API: Inter-Module Event) |
| Faculty Brief, Section 1 | `MOD3-FAC-ELG-01` | Auto-identify eligible faculty (probation + $\ge$ 12 mo service) on 10th; list to Registrar. | `MOD3-FAC-REQ-01` to `02` | Phase 06 (Workflows: Monthly Eligibility Scheduler), Phase 13 (Reports: Eligible List) |
| Faculty Brief, Section 2 | `MOD3-FAC-APP-01` | Faculty submit self-appraisal form (Enclosure 1) within 7 working days. | `MOD3-FAC-REQ-03` | Phase 06 (Workflows: Self-Appraisal FSM), Phase 12 (SLA: 7-day turnaround) |
| Faculty Brief, Section 3 | `MOD3-FAC-VER-01` | Parallel verification across Dean, R&D, Placement, HR; discrepancy return loop. | `MOD3-FAC-REQ-04` to `05` | Phase 05 (User Roles: Verifiers), Phase 06 (Workflows: Parallel Review & Dispute Loop) |
| Faculty Brief, Section 4 & 5 | `MOD3-FAC-ECM-01` | Monthly ECM scheduled by Registrar; digital score sheet; TNU Protocol matrix. | `MOD3-FAC-REQ-06` to `07` | Phase 05 (User Roles: ECM Panel), Phase 06 (Workflows: ECM Matrix Compilation) |
| Faculty Brief, Section 6 | `MOD3-FAC-SAL-01` | Track compensation in next salary cycle; auto-generate revision letter. | `MOD3-FAC-REQ-08` to `09` | Phase 06 (Workflows: Compensation Tracking), Phase 08 (ERD: Letters), Phase 13 |

---

## 5. Shared & Cross-Module Traceability

| Official Source Reference | Baseline Traceability ID | Requirement Statement (Abridged) | Functional Requirement Mapping | Downstream Documentation Targets |
|---|---|---|---|---|
| Mod II Selection & Mod I CDB | `SHR-INT-01` | Accepted LOI onboarding automatically creates master employee in Module I. | `SHR-INT-REQ-01` | Phase 06 (Workflows: Onboarding Bridge), Phase 09 (API: Event Consumer) |
| Mod II Section 1(i) & Mod I CDB | `SHR-INT-02` | Resignation accepted by Dean in Module I triggers Module II urgent replacement. | `SHR-INT-REQ-02` | Phase 06 (Workflows: Resignation Event), Phase 12 (SLA: Replacement Trigger) |
| Universal Master Baseline | `SHR-INT-03` | Module I continuously synchronizes employee master data to Module III. | `SHR-INT-REQ-03` | Phase 08 (ERD: Master Foreign Keys), Phase 09 (API: Master Data Provider) |
| Mod III Outcomes & Mod I Change | `SHR-INT-04` | Approved annual appraisal outcomes inject service change requests into Module I. | `SHR-INT-REQ-04` | Phase 06 (Workflows: Appraisal Handshake), Phase 09 (API: Change Request Injection) |
| Module I Brief, Structure (1) | `SHR-ERP-01` | Central Employee Database fully reflected and synchronized with ERP. | `SHR-ERP-REQ-01` to `03` | Phase 06 (Workflows: Transactional Outbox), Phase 09 (API: ERP Adapter) |
| Universal Security Baseline | `SHR-AUT-01` | Role-Based Access Control enforcing least-privilege scoping across all modules. | `SHR-AUT-REQ-01` to `04` | Phase 05 (User Roles: Permission Matrix), Phase 11 (Security: Authorization) |
| Universal Compliance Baseline | `SHR-AUD-01` | Universal tamper-evident, append-only audit trail logging actor, IP, timestamp, diffs. | `SHR-AUD-REQ-01` to `03` | Phase 08 (ERD: `audit_logs`), Phase 11 (Security: Compliance Auditing) |

---
*End of Document — Requirements Traceability Matrix.*
