# HRMS Documentation Necessity Audit, Consolidation & Rationalization Report
## University HR Change Management & Automation System

**Document Identifier:** `DOC-AUDIT-2026-02-REV03`  
**Phase:** Enterprise Documentation Audit, Consolidation, and Rationalization (Revision 3 — Folder-Preserving Plan)  
**Location:** [`docs/DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md)  
**Status:** Proposal Under Review — Pending Mentor Review and Authorization  
**Date:** October 2, 2026  
**Workspace:** `d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM`  

---

## 1. Executive Summary

### 1.1 Context and Mandate
The **University HR Change Management & Automation System** has been systematically developed through Phase 1 (Requirements Engineering), Phase 2 (Business Process Modeling), Phase 3 (Functional Requirements Specification), Phase 1.5 (System Architecture & Real-Time ADR), and Phase 4 (Database Documentation: Steps 1 through 5).

While this rigorous progression has produced an exhaustive, auditable, and source-grounded foundation, it has generated **forty-four (44) pre-existing files** (35 active Markdown specifications in `docs/`, 2 foundational Markdown specifications in `source-requirements/`, and 7 source assets) alongside **ten (10) empty directory stubs**. The planned Phase 4 database roadmap alone contemplated thirteen (13) separate documents (`00` through `12`).

In accordance with direct mentor guidance—stipulating that the project should **not maintain an unnecessarily large number of fragmented documents**—this comprehensive **Documentation Necessity Audit, Consolidation, and Rationalization Report** has been prepared.

### 1.2 Primary Directive: Complete Folder Preservation
In strict compliance with explicit user direction:
1. **The existing folder architecture is preserved exactly as it is.**
2. No folders are renamed, removed, relocated, merged, or pruned.
3. No external `docs/reference/` directory is introduced. All documents, reference sheets, and archives remain within their respective native domain folders.
4. The consolidation objective is to rationalize files **inside each existing folder**, consolidating useful content into approximately **1–2 well-organized canonical documents per relevant folder**, while preserving 100% of all approved requirements, traceability matrices, business rules, workflows, architecture decisions, and source evidence.

> [!IMPORTANT]
> **Strict Audit-Only Change Control Invariant:** This report is strictly an audit and restructuring proposal. **No existing files have been deleted, moved, renamed, merged, or overwritten.** No folders have been deleted or pruned. No application code, database DDL/DML, migrations, ORM entities, or physical database artifacts have been generated. Execution of any consolidation awaits explicit user and mentor authorization.

---

### 1.3 Reconciled Workspace Inventory & Necessity Scorecard

The workspace contains forty-four (44) pre-existing files, plus this newly created audit report (bringing total current files to forty-five [45]):

```
====================================================================================================
                        DOCUMENTATION NECESSITY AUDIT SCORECARD
====================================================================================================
 Total Pre-Existing Workspace Files Inspected: 44 Files (100% Accounted For)
 Current Total Files (including this Report) : 45 Files
 Pre-Existing Active Specs in docs/          : 35 Markdown Specifications (12,520 lines / 1.51 MB)
 Foundational Specs in source-requirements/  :  2 Markdown Specifications ( 2,052 lines / 0.25 MB)
 Primary Source Assets in source-requirements:  7 Binary Files (5 PDFs + 2 JPEGs / 2.39 MB)
 Preserved Domain Folders in docs/           : 15 Primary Folders (01 through 15 - 100% Preserved)
 Intentionally Empty Future Folders in docs/ : 10 Subdirectories (Retained for downstream phases)
 Planned Phase 4 DB Documents Consolidated :  6 Documents (Docs 07-12 consolidated into Docs 01-02; DB phase active)
----------------------------------------------------------------------------------------------------
 NECESSITY CLASSIFICATION BREAKDOWN (Denominator: Pre-Existing Files N = 44):
 • Category A (Essential Standalone)         : 14 Files (31.8% of 44) [7 Markdown + 7 Source Assets]
 • Category B (Consolidatable)               : 21 Files (47.7% of 44) [All within existing folders]
 • Category C (Supporting / Reference)       :  9 Files (20.5% of 44) [8 in docs/ + 1 in source]
 • Category D (Redundant / Direct Deletion)  :  0 Files ( 0.0% of 44) [Zero raw deletions]
 Total Accounted For                         : 44 Files (100.0%)
----------------------------------------------------------------------------------------------------
 ACTIVE DOCUMENTATION IN docs/ BREAKDOWN (Denominator: Pre-Existing docs/ Markdown N = 35):
 • Category A (Essential Standalone in docs/):  6 Files (17.1% of 35)
 • Category B (Consolidatable in docs/)      : 21 Files (60.0% of 35)
 • Category C (Supporting/Reference in docs/):  8 Files (22.9% of 35)
 • Category D (Direct Deletion in docs/)     :  0 Files ( 0.0% of 35)
 Total Accounted For                         : 35 Files (100.0%)
----------------------------------------------------------------------------------------------------
 FOLDER-PRESERVING CONSOLIDATION IMPACT:
 • Current Active Markdown Files in docs/    : 35 Documents
 • Proposed Canonical Suite in Active Folders:  7 Core Specifications + 1 ADR = 8 Active Specs
 • Reference Material Retained in Folders    : Preserved within respective folders (01, 02, 03)
 • Net Reduction in Active docs/ File Clutter: 77.1% Reduction (from 35 down to 8 active specs)
 • All 15 Primary docs/ Folders Preserved    : Exactly 15 Folders Retained (100% Intact)
 • Baseline Information Loss Risk            : 0.0% Planned Loss (Status: PARTIALLY VERIFIED pending canonical file drafting)
====================================================================================================
```

---

## 2. Audit Scope and Methodology

### 2.1 Audit Scope
The audit encompasses every directory and file across the entire workspace:
- `docs/` Root (1 pre-existing Markdown file: `PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md`; plus 1 active audit report: `DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md`)
- `docs/01-requirements/` (11 Markdown files: `00` through `10`)
- `docs/02-business-process/` (9 Markdown files: `00` through `08`)
- `docs/03-functional-requirements/` (6 Markdown files: `00` through `05`)
- `docs/04-non-functional-requirements/` (Preserved — pending Phase 5)
- `docs/05-user-roles/` (Preserved — pending Phase 5)
- `docs/06-workflows/` (Preserved — pending Phase 6)
- `docs/07-system-architecture/` (1 Markdown file: `ADR-001-REAL-TIME-COMMUNICATION.md`)
- `docs/08-database/` (7 Markdown files: Steps 1 through 5, `00` through `06`)
- `docs/09-api/` (Preserved — pending Phase 9)
- `docs/10-ui-ux/` (Preserved — pending Phase 10)
- `docs/11-security/` (Preserved — pending Phase 11)
- `docs/12-notifications-sla/` (Preserved — pending Phase 12)
- `docs/13-reports/` (Preserved — pending Phase 13)
- `docs/14-testing/` (Preserved — pending Phase 14)
- `docs/15-deployment/` (Preserved — pending Phase 15)
- `source-requirements/` (9 files: 2 foundational specifications + 7 primary binary assets across `Module-I/`, `Module-II/`, `Module-III/`)

### 2.2 Audit Methodology & Evaluation Criteria
Each document was inspected against five formal criteria:
1. **Source Grounding & Baseline Integrity:** Does the document contain frozen baseline invariants (104 atomic requirements, 59 processes, 60 rules, 11 official TBDs, 33 entities, 41 relationships, 344 verified logical attributes, 152 functional requirements)?
2. **Semantic Uniqueness:** Does the document contain unique operational rules, field definitions, architectural decisions, or acceptance criteria that exist nowhere else?
3. **Redundancy and Overlap:** To what degree is the content repeated across other documents (e.g., actor lists repeated in 4 files; change formats repeated across requirements, processes, rules, FRDs, and database docs)?
4. **Developer & Operational Maintainability:** Does maintaining this document as a standalone file increase the risk of documentation drift, broken cross-references, or cognitive overhead for developers and evaluators?
5. **SDLC Necessity:** Is this document strictly required for understanding, designing, coding, testing, verifying, deploying, or auditing the system?

---

## 3. Complete Current Document Inventory

The table below catalogs all forty-four (44) pre-existing files in the workspace (plus the newly created audit report) with complete metadata, dependency mapping, duplication analysis, and recommended rationalization action:

| # | File Path & Name | Size / Lines | Primary Purpose & Contents | Source Authority | Related Domains | Dependencies & Inbound Refs | Unique Content? | Duplicated Elsewhere? | Necessity Class | Recommended Action |
|---|---|:---:|---|---|---|---|:---:|:---:|:---:|---|
| **1** | [`docs/01-requirements/00-REQUIREMENTS-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/00-REQUIREMENTS-INDEX.md) | 15.7 KB<br>179 lines | Index, roadmap, and governance rules for Phase 1. | Project Plan | Requirements | Referenced by README, Phase 2, Phase 3. | Partial (Index only) | Yes (Repeated in subsequent phase indexes). | **Category B** | **Consolidate** into `01-requirements/01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md`. |
| **2** | [`docs/01-requirements/01-PROJECT-REQUIREMENTS-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/01-PROJECT-REQUIREMENTS-SPECIFICATION.md) | 31.4 KB<br>351 lines | High-level vision, problem statement, business goals, module narratives. | Source Briefs | All Modules | Referenced by FRDs, BP specs, Architecture. | Yes (High-level vision & goals) | Partial (Narratives repeated in Module FRDs). | **Category B** | **Consolidate** as Section 1 ("Introduction & Business Vision") of the unified SRS. |
| **3** | [`docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/02-REQUIREMENT-CATALOGUE.md) | 38.3 KB<br>240 lines | Authoritative catalogue of **104 frozen atomic requirements** (`REQ-*`). | Source Briefs | All Modules | Critical inbound anchor for all downstream specs. | **YES (Core Baseline Invariant)** | Partial (FRDs expand them into MOD*-REQ-*). | **Category A** | **Retain as Core Section** of `01-requirements/01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md`. |
| **4** | [`docs/01-requirements/03-SCOPE-AND-BOUNDARIES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/03-SCOPE-AND-BOUNDARIES.md) | 23.4 KB<br>227 lines | In-scope vs. out-of-scope boundaries, system interfaces, assumptions. | Source Briefs | All Modules | Referenced by FRDs, Database overview. | Yes (Explicit boundary exclusions) | Partial (Repeated across module scopes). | **Category B** | **Consolidate** as Section 2 ("System Scope & Boundaries") of the unified SRS. |
| **5** | [`docs/01-requirements/04-REQUIREMENTS-TRACEABILITY.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/04-REQUIREMENTS-TRACEABILITY.md) | 16.2 KB<br>117 lines | Forward/backward traceability mapping source briefs to 104 requirements. | Analysis Matrix | All Modules | Referenced by quality audits. | Yes (Source-to-REQ matrix) | No | **Category B** | **Consolidate** as Appendix ("Traceability Matrix") of the unified SRS. |
| **6** | [`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md) | 17.0 KB<br>198 lines | Register of **11 official baseline TBDs**. Reopened and verified against Doc 05 and Table 10A: authoritative mapping establishes `REQ-TBD-01` (Resignation intake mechanism), `REQ-TBD-02` (ERP technical transport protocol), `REQ-TBD-03` (Legacy service data cutover strategy), `REQ-TBD-04` (Mid-cycle supervisor transfer evaluation attribution guidelines), `REQ-TBD-05` (University Group-D pre-defined compensation slab amounts and increment rupee values), `REQ-TBD-06` (Academic Statutory SCM digital scoring parameter percentage weights), `REQ-TBD-07` (Non-Academic three-round assessment dimension percentage weights and cutoff thresholds), `REQ-TBD-08` (Faculty ECM TNU Protocol matrix benchmark thresholds and percentage cutoffs), `REQ-TBD-09` (Group-D 12-month parameter-weighted averaging formula and coefficients), `REQ-TBD-10` (Additional Responsibility administrative allowance policy confirmation), and `REQ-TBD-11` (SCM External Subject Expert digital verification and access mechanism). Note: Cross-specification numbering discrepancy with original `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md` sequence documented (Issue `AUD-06`); technical-cadre appraisal track decoupled as standalone open institutional policy decision. | Analysis Log | All Modules | Inbound anchor for all open decision tags across phases. | **YES (Core Baseline Invariant)** | Partial (Cross-document numbering discrepancy with Doc 09 Table 10A). | **Category A** | **Retain as Dedicated Chapter** in `01-requirements/01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md`. |
| **7** | [`docs/01-requirements/06-REQUIREMENTS-QUALITY-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/06-REQUIREMENTS-QUALITY-REVIEW.md) | 22.4 KB<br>203 lines | Historical Phase 1 quality review and compliance sign-off audit. | Quality Audit | Requirements | Historical evidence. | No (One-time audit report) | No | **Category C** | **Retain in `01-requirements/`** as historical verification appendix / reference. |
| **8** | [`docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md) | 65.9 KB<br>502 lines | Post-release delta analysis of stakeholder inputs for Modules I & II. | Stakeholder Input | Modules I & II | Referenced by Doc 09 and Doc 10. | Partial (Intermediate working paper) | Yes (Subsumed by Docs 09 and 10). | **Category C** | **Retain in `01-requirements/`** as reference-only draft. |
| **9** | [`docs/01-requirements/08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md) | 60.0 KB<br>555 lines | Post-release delta analysis of stakeholder inputs for Module III. | Stakeholder Input | Module III | Referenced by Doc 09 and Doc 10. | Partial (Intermediate working paper) | Yes (Subsumed by Docs 09 and 10). | **Category C** | **Retain in `01-requirements/`** as reference-only draft. |
| **10** | [`docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md) | 48.1 KB<br>425 lines | Synthesis of deltas from 07 & 08; defines CONF-01 to 10 and 6 candidates. | Analysis Matrix | All Modules | Referenced by Doc 10 and Database index. | Yes (Consolidated delta evaluation) | Partial (Subsumed by Doc 10). | **Category C** | **Retain in `01-requirements/`** as reference-only draft. |
| **11** | [`docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md) | 47.7 KB<br>666 lines | Standardized decision cards for CONF-01 to CONF-10 for mentor review. | Decision Register | All Modules | Active decision artifact. | **YES (Authoritative review sheet)** | No | **Category C** | **Retain in `01-requirements/`** as authoritative reference decision register (`02-STAKEHOLDER-DECISION-SHEET.md`). |
| **12** | [`docs/02-business-process/00-BUSINESS-PROCESS-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/00-BUSINESS-PROCESS-INDEX.md) | 20.2 KB<br>205 lines | Master index and directory of 59 business processes. | Process Plan | Business Process | Inbound links from Phase 3 FRDs. | Partial (Index only) | Yes (Repeated in module process files). | **Category B** | **Consolidate** into `02-business-process/01-BUSINESS-PROCESS-AND-WORKFLOW-SPEC.md`. |
| **13** | [`docs/02-business-process/01-BUSINESS-PROCESS-FRAMEWORK.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/01-BUSINESS-PROCESS-FRAMEWORK.md) | 18.7 KB<br>197 lines | Process modeling methodology, actor taxonomy, and RACI matrix. | Modeling Model | All Modules | Referenced by BP specs and FRD actor lists. | Yes (RACI and Actor Taxonomy) | Partial (Actors repeated in each FRD). | **Category B** | **Consolidate** as Section 1 of unified Business Process Specification. |
| **14** | [`docs/02-business-process/02-MODULE-I-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/02-MODULE-I-BUSINESS-PROCESSES.md) | 39.0 KB<br>381 lines | 11 discrete business processes for Module I (`BP-M1-001` to `011`). | Requirements | Module I | Referenced by FRD 01, Database 03/04. | **YES (Core Baseline Invariant)** | Partial (Steps summarized in FRDs). | **Category B** | **Consolidate** as Module I Chapter in unified Business Process Specification. |
| **15** | [`docs/02-business-process/03-MODULE-II-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/03-MODULE-II-BUSINESS-PROCESSES.md) | 76.4 KB<br>783 lines | 20 discrete business processes for Module II (`BP-M2-*`). | Requirements | Module II | Referenced by FRD 02, Database 03/04. | **YES (Core Baseline Invariant)** | Partial (Workflows summarized in FRDs).| **Category B** | **Consolidate** as Module II Chapter in unified Business Process Specification. |
| **16** | [`docs/02-business-process/04-MODULE-III-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/04-MODULE-III-BUSINESS-PROCESSES.md) | 82.1 KB<br>791 lines | 22 discrete business processes for Module III (`BP-M3-*`). | Requirements | Module III | Referenced by FRD 03, Database 03/04. | **YES (Core Baseline Invariant)** | Partial (Subsystems summarized in FRDs).| **Category B** | **Consolidate** as Module III Chapter in unified Business Process Specification. |
| **17** | [`docs/02-business-process/05-CROSS-MODULE-BUSINESS-PROCESSES.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/05-CROSS-MODULE-BUSINESS-PROCESSES.md) | 47.8 KB<br>476 lines | 6 cross-module life-cycle handshakes (`BP-XMOD-001` to `006`). | Architecture | Cross-Module | Referenced by all FRDs and Database specs. | **YES (Core Baseline Invariant)** | Partial (Handshakes cited in FRDs). | **Category B** | **Consolidate** as Cross-Module Chapter in unified Business Process Specification. |
| **18** | [`docs/02-business-process/06-BUSINESS-RULES-AND-DECISION-POINTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/06-BUSINESS-RULES-AND-DECISION-POINTS.md) | 41.0 KB<br>177 lines | Authoritative catalogue of **60 frozen business rules** (`BR-01` to `60`). | Requirements | All Modules | Inbound anchor for constraints, validation, tests. | **YES (Core Baseline Invariant)** | Partial (Rules cited individually in FRDs).| **Category A** | **Retain Standalone** as dedicated `02-business-process/02-BUSINESS-RULES-SPECIFICATION.md`. |
| **19** | [`docs/02-business-process/07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md) | 25.0 KB<br>159 lines | Comprehensive SLA timers, submission windows, and grace periods. | Business Rules | All Modules | Referenced by SLA Engine specs and FRDs. | Yes (Consolidated SLA matrix) | Partial (Timers mentioned in process steps).| **Category B** | **Consolidate** as SLA Chapter in unified Business Process Specification. |
| **20** | [`docs/02-business-process/08-BUSINESS-PROCESS-QUALITY-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/08-BUSINESS-PROCESS-QUALITY-REVIEW.md) | 17.9 KB<br>154 lines | Historical Phase 2 quality audit and verification report. | Quality Audit | Business Process | Historical evidence. | No (One-time audit report) | No | **Category C** | **Retain in `02-business-process/`** as historical verification appendix / reference. |
| **21** | [`docs/03-functional-requirements/00-FRD-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/00-FRD-INDEX.md) | 16.2 KB<br>166 lines | Master index for Phase 3 Functional Requirements Documents. | FRD Plan | Functional Req | Inbound navigation. | Partial (Index only) | Yes (Repeated in FRD suite). | **Category B** | **Consolidate** into `03-functional-requirements/01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md`. |
| **22** | [`docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md) | 29.4 KB<br>330 lines | Detailed FRD for Module I: 28 functional requirements. | Requirements | Module I | Referenced by Database docs, APIs. | **YES (Core Functional Spec)** | Partial (Overlaps with BP-M1 and REQ-02). | **Category B** | **Consolidate** into Module I Section of unified Functional Specification. |
| **23** | [`docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md) | 40.4 KB<br>396 lines | Detailed FRD for Module II: 46 functional requirements. | Requirements | Module II | Referenced by Database docs, APIs. | **YES (Core Functional Spec)** | Partial (Overlaps with BP-M2 and REQ-02). | **Category B** | **Consolidate** into Module II Section of unified Functional Specification. |
| **24** | [`docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md) | 37.4 KB<br>383 lines | Detailed FRD for Module III: 52 functional requirements. | Requirements | Module III | Referenced by Database docs, APIs. | **YES (Core Functional Spec)** | Partial (Overlaps with BP-M3 and REQ-02). | **Category B** | **Consolidate** into Module III Section of unified Functional Specification. |
| **25** | [`docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/04-SHARED-FUNCTIONAL-REQUIREMENTS.md) | 17.1 KB<br>197 lines | Detailed FRD for Shared Platform: 26 functional requirements. | Requirements | Shared Platform | Referenced by Database docs, Architecture.| **YES (Core Functional Spec)** | Partial (Overlaps with Tech Architecture).| **Category B** | **Consolidate** into Shared Section of unified Functional Specification. |
| **26** | [`docs/03-functional-requirements/05-FRD-QUALITY-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/03-functional-requirements/05-FRD-QUALITY-REVIEW.md) | 31.2 KB<br>253 lines | Historical Phase 3 quality audit report (verifies 152 FRD requirements). | Quality Audit | Functional Req | Historical evidence. | No (One-time audit report) | No | **Category C** | **Retain in `03-functional-requirements/`** as historical verification appendix / reference. |
| **27** | [`docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md) | 50.5 KB<br>493 lines | Architectural Decision Record approving Socket.IO over polling/SSE. | Architecture | Architecture | Referenced by Tech Baseline, Database docs. | **YES (Approved Tech Decision)** | No | **Category A** | **Retain Standalone** in `docs/07-system-architecture/`. |
| **28** | [`docs/08-database/00-DATABASE-DOCUMENTATION-INDEX.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/00-DATABASE-DOCUMENTATION-INDEX.md) | 21.3 KB<br>210 lines | Database documentation roadmap planning 13 documents (`00` to `12`). | DB Plan | Database | Inbound roadmap. | Partial (Index only) | Yes (Repeated in subsequent DB docs). | **Category B** | **Consolidate** into `08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`. |
| **29** | [`docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md) | 38.8 KB<br>374 lines | Architecture overview, PostgreSQL, Modular Monolith, 4 domains. | Architecture | Database | Referenced by DB 03, 04, 05, 06. | Yes (High-level DB design) | Yes (Duplicated heavily in 02 and 06). | **Category B** | **Consolidate** into `08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`. |
| **30** | [`docs/08-database/02-DATA-MODEL-OVERVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/02-DATA-MODEL-OVERVIEW.md) | 55.9 KB<br>576 lines | Conceptual domains, entity classification taxonomy, entity mapping. | DB Design | Database | Referenced by DB 03, 04, 05. | Partial (Conceptual mapping) | Yes (Duplicated heavily in 01, 03, 06). | **Category B** | **Consolidate** into `08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`. |
| **31** | [`docs/08-database/03-ENTITY-IDENTIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/03-ENTITY-IDENTIFICATION.md) | 74.6 KB<br>726 lines | Inventory and profiles of **33 conceptual entities**. | Requirements | Database | Referenced by DB 04, 05, 06. | **YES (33 Entities Inventory)** | Partial (Repeated in 04, 05, 06). | **Category B** | **Consolidate** into `08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`. |
| **32** | [`docs/08-database/04-ENTITY-RELATIONSHIP-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/04-ENTITY-RELATIONSHIP-SPECIFICATION.md) | 103.5 KB<br>1,137 lines| Specifications and ERDs for **41 conceptual relationships**. | DB Design | Database | Referenced by DB 05, 06. | **YES (41 Relationships & ERD)** | Partial (Relationships summarized in 06).| **Category B** | **Consolidate** into `08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`. |
| **33** | [`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md) | 149.5 KB<br>1,082 lines| Comprehensive catalogue defining **344 logical attributes** across 33 entities. | DB Design | Database | Referenced by DB 06. | **YES (344 Attributes Catalogue)** | Partial (Referenced in 06). | **Category A** | **Retain as Canonical Data Dictionary** (`08-database/02-LOGICAL-DATA-DICTIONARY.md`). |
| **34** | [`docs/08-database/06-DATABASE-SCHEMA-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/06-DATABASE-SCHEMA-SPECIFICATION.md) | 110.0 KB<br>1,020 lines| Complete schema specification synthesizing entities, rels, domains, keys. | DB Design | Database | Primary schema reference. | **YES (Master Schema Spec)** | Partial (Synthesizes 01, 03, 04, 05). | **Category A** | **Retain as Primary Schema Spec** (`08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`). |
| **35** | [`docs/PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md) | 53.5 KB<br>674 lines | Previous governance audit report (dated Sept 29, 2026). | Governance Audit | Governance | Historical audit report. | No (One-time audit report) | No | **Category C** | **Retain in `docs/` Root** as historical audit reference. |
| **36** | [`source-requirements/PROJECT_REQUIREMENTS_ANALYSIS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/PROJECT_REQUIREMENTS_ANALYSIS.md) | 102.7 KB<br>911 lines | Foundational analysis document written at project inception. | Source Analysis | All Modules | Baseline predecessor to Phase 1. | Yes (Foundational derivation) | Partial (Subsumed by Phase 1 docs). | **Category C** | **Retain as Foundation Reference** in `source-requirements/`. |
| **37** | [`source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md) | 151.2 KB<br>1,141 lines| **Authoritative Technology Architecture Baseline** (Next.js, Vanilla CSS, NestJS, Postgres).| Architecture | Architecture | Foundational architecture baseline. | **YES (Master Architecture Baseline)** | Partial (Cited across all technical docs).| **Category A** | **Retain Untouched** in `source-requirements/` (Do NOT move or rename). |
| **38** | [`source-requirements/Module-I/27-07-26 - Revised HR Change Management & Automation System-Module I.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/Module-I/27-07-26%20-%20Revised%20HR%20Change%20Management%20&%20Automation%20System-Module%20I.pdf) | 187.2 KB<br>Binary | Official Module I requirement brief supplied by university authority. | Source of Truth | Module I | Authoritative business brief. | **YES (Primary Source Asset)** | No | **Category A** | **Retain Untouched** in `source-requirements/Module-I/`. Permanent source asset. |
| **39** | [`source-requirements/Module-I/Module_1_HR_Change_Management_Narrative_Complete.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/Module-I/Module_1_HR_Change_Management_Narrative_Complete_Workflow.pdf) | 506.9 KB<br>Binary | Complete narrative brief for Module I. | Source of Truth | Module I | Authoritative business narrative. | **YES (Primary Source Asset)** | No | **Category A** | **Retain Untouched** in `source-requirements/Module-I/`. Permanent source asset. |
| **40** | [`source-requirements/Module-II/Module_2_Recruitment_&_Selection_Automation_System.jpeg`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/Module-II/Module_2_Recruitment_&_Selection_Automation_System_Detailed_Narrative.pdf) | 182.9 KB<br>Binary | Visual workflow diagram for Module II recruitment SOP. | Source of Truth | Module II | Authoritative workflow diagram. | **YES (Primary Source Asset)** | No | **Category A** | **Retain Untouched** in `source-requirements/Module-II/`. Permanent source asset. |
| **41** | [`source-requirements/Module-II/Module_2_Recruitment_Selection_Narrative_Complete.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/Module-II/Module_2_Recruitment_Selection_Narrative_Complete_Workflow.pdf) | 508.3 KB<br>Binary | Complete narrative brief for Module II. | Source of Truth | Module II | Authoritative business narrative. | **YES (Primary Source Asset)** | No | **Category A** | **Retain Untouched** in `source-requirements/Module-II/`. Permanent source asset. |
| **42** | [`source-requirements/Module-II/Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/Module-II/Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf) | 229.5 KB<br>Binary | Structured rearrangement of Module II recruitment requirements. | Source of Truth | Module II | Authoritative requirement brief. | **YES (Primary Source Asset)** | No | **Category A** | **Retain Untouched** in `source-requirements/Module-II/`. Permanent source asset. |
| **43** | [`source-requirements/Module-III/Module_3_Performance_Management_Automation_System.jpeg`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/Module-III/Module_3_Performance_Management_Automation_System_Narrative_Workflow.pdf) | 134.6 KB<br>Binary | Visual workflow diagram for Module III performance subsystems. | Source of Truth | Module III | Authoritative workflow diagram. | **YES (Primary Source Asset)** | No | **Category A** | **Retain Untouched** in `source-requirements/Module-III/`. Permanent source asset. |
| **44** | [`source-requirements/Module-III/Requirement_Brief_Module_III_Performance_Management_Automation_System.pdf`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/Module-III/Requirement_Brief_Module_III_Performance_Management_Automation_System.pdf) | 766.0 KB<br>Binary | Official Module III requirement brief supplied by university authority. | Source of Truth | Module III | Authoritative business brief. | **YES (Primary Source Asset)** | No | **Category A** | **Retain Untouched** in `source-requirements/Module-III/`. Permanent source asset. |
| *45* | [`docs/DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md) | ~80 KB<br>Current | This audit and rationalization report. | Audit Plan | Governance | Cross-cutting audit artifact. | **YES (Active Audit Report)** | No | **Category C** | **Retain in `docs/` Root** as active audit proposal pending mentor review. |

---

## 4. Necessity Classification Summary

Following the mandatory 5-tier classification framework, the 44 pre-existing workspace assets are grouped without double-counting as follows:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            DOCUMENT NECESSITY CLASSIFICATION SUMMARY                             │
├───────────────────────────────────┬───────────────┬──────────────────────────────────────────────┤
│ CLASSIFICATION CATEGORY           │ FILE COUNT    │ PRIMARY INCLUDED DOCUMENTS                   │
├───────────────────────────────────┼───────────────┼──────────────────────────────────────────────┤
│ Category A: Essential Standalone  │ 14 Files      │ • 6 Markdown Specs in docs/:                 │
│                                   │ (31.8% of 44) │   01-reqs/02-REQUIREMENT-CATALOGUE.md,       │
│                                   │               │   01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md,│
│                                   │               │   02-bp/06-BUSINESS-RULES.md,                │
│                                   │               │   07-arch/ADR-001-REAL-TIME.md,              │
│                                   │               │   08-db/05-ENTITY-WISE-DETAILED (344 Attrs), │
│                                   │               │   08-db/06-DATABASE-SCHEMA-SPECIFICATION.    │
│                                   │               │ • 1 Master Spec in source-requirements/:     │
│                                   │               │   TECHNOLOGY_ARCHITECTURE_BASELINE.md.       │
│                                   │               │ • 7 Primary Source Binaries (PDFs/JPEGs).    │
├───────────────────────────────────┼───────────────┼──────────────────────────────────────────────┤
│ Category B: Consolidatable        │ 21 Files      │ • 4 Reqs Specs in 01-requirements/           │
│                                   │ (47.7% of 44) │ • 7 BP Specs in 02-business-process/         │
│                                   │               │ • 5 FRD Specs in 03-functional-requirements/ │
│                                   │               │ • 5 DB Specs in 08-database/                 │
├───────────────────────────────────┼───────────────┼──────────────────────────────────────────────┤
│ Category C: Supporting / Reference│  9 Files      │ • 4 Quality Reviews & Structure Audits:      │
│                                   │ (20.5% of 44) │   01/06, 02/08, 03/05, docs/STRUCTURE-AUDIT. │
│                                   │               │ • 4 Stakeholder Delta Documents:             │
│                                   │               │   01/07, 01/08, 01/09, 01/10-Decision Sheet. │
│                                   │               │ • 1 Inception Analysis in source/:           │
│                                   │               │   PROJECT_REQUIREMENTS_ANALYSIS.md.          │
├───────────────────────────────────┼───────────────┼──────────────────────────────────────────────┤
│ Category D: Redundant / Obsolete  │  0 Files      │ No files recommended for raw deletion.       │
│                                   │ ( 0.0% of 44) │ Zero baseline loss policy strictly enforced. │
├───────────────────────────────────┼───────────────┼──────────────────────────────────────────────┤
│ Category E: Pending / Stubs       │ 10 Folders    │ 10 Empty primary directories in docs/        │
│                                   │ (Intentionally│ (04, 05, 06, 09, 10, 11, 12, 13, 14, 15),    │
│                                   │  Retained)    │ 6 Halted DB docs (07 to 12),                 │
│                                   │               │ Downstream specs deferred to future phases.  │
├───────────────────────────────────┼───────────────┼──────────────────────────────────────────────┤
│ TOTAL PRE-EXISTING FILES          │ 44 Files      │ 100.0% Verified and Accounted For            │
└───────────────────────────────────┴───────────────┴──────────────────────────────────────────────┘
```

---

## 5. Duplicate and Overlapping Content Analysis

A detailed textual and structural analysis revealed significant cross-document redundancy across the documentation repository:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             PRIMARY CONTENT REDUNDANCY CLUSTERS                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘

 [Cluster 1: Functional Scope & Workflows (Repeated across 3 distinct suites)]
   docs/01-requirements/01-PROJECT-REQUIREMENTS-SPECIFICATION.md
   docs/02-business-process/02, 03, 04, 05 (Business Process Specifications)
   docs/03-functional-requirements/01, 02, 03, 04 (Module FRD Specifications)
   ──► VERIFIED DUPLICATION: Actors, workflow steps, approval hierarchies, and change formats are
       repeated up to 3 times with minor formatting variations.

 [Cluster 2: Database Conceptual Overview Proliferation (Repeated across 4 DB specs)]
   docs/08-database/01-DATABASE-DESIGN-OVERVIEW.md (374 lines)
   docs/08-database/02-DATA-MODEL-OVERVIEW.md (576 lines)
   docs/08-database/03-ENTITY-IDENTIFICATION.md (726 lines)
   docs/08-database/06-DATABASE-SCHEMA-SPECIFICATION.md (1,020 lines)
   ──► VERIFIED DUPLICATION: Entity descriptions, domain boundaries, Modular Monolith rationale,
       and PostgreSQL alignment are restated in 4 successive documents.

 [Cluster 3: Stakeholder Delta Documents (4 separate files on the same 10 CONF items)]
   docs/01-requirements/07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md
   docs/01-requirements/08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md
   docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md
   docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md
   ──► VERIFIED DUPLICATION: Docs 07 & 08 were merged into 09, which was then converted into 10.
       Maintaining all 4 files creates 222 KB of provisional stakeholder text in the approved folder.

 [Cluster 4: Historical Phase Quality Audits (3 separate audit reports)]
   docs/01-requirements/06-REQUIREMENTS-QUALITY-REVIEW.md
   docs/02-business-process/08-BUSINESS-PROCESS-QUALITY-REVIEW.md
   docs/03-functional-requirements/05-FRD-QUALITY-REVIEW.md
   docs/PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md
   ──► VERIFIED OVERLAP: These one-time sign-off reports serve audit history rather than active
       development. Keeping them alongside active specifications clutters developer navigation.
```

---

## 6. Essential Documents to Retain (Category A)

The following fourteen (14) files contain authoritative, foundational, or invariant system information that **must be retained**:

1. **`source-requirements/` (All 7 Binary Assets):** The original PDFs and JPEGs supplied by university leadership are the ultimate legal and institutional source of truth.
2. **`source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md`:** The authoritative system technology architecture baseline (Next.js, Vanilla CSS, CSS Modules, NestJS Modular Monolith, PostgreSQL, Socket.IO, Redis). **Must remain in place in `source-requirements/` untouched.**
3. **`docs/01-requirements/02-REQUIREMENT-CATALOGUE.md`:** Contains the 104 frozen atomic requirements (`REQ-*`). Invariant project baseline.
4. **[`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md):** The frozen log of 11 official baseline TBDs (`REQ-TBD-01` Resignation intake through `REQ-TBD-11` SCM External Subject Expert access). Invariant project baseline.
5. **`docs/02-business-process/06-BUSINESS-RULES-AND-DECISION-POINTS.md`:** The authoritative catalogue of 60 business rules (`BR-01` to `BR-60`). Invariant project baseline.
6. **`docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`:** Authoritative architectural decision record approving Socket.IO over polling/SSE.
7. **`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`:** Contains the complete 344 logical attribute data dictionary. Invariant data model baseline.
8. **`docs/08-database/06-DATABASE-SCHEMA-SPECIFICATION.md`:** The comprehensive schema specification synthesizing all 33 entities, 41 relationships, domain boundaries, and integration mechanics.

---

## 7. Folder-by-Folder Consolidation Plan

In strict adherence to the **Folder-Preserving Principle**, all documentation rationalization occurs **within the boundaries of each existing folder**. No folders are moved, merged, renamed, or deleted.

The table below itemizes every existing workspace folder, its current contents, unique information, redundancy, proposed canonical file targets (1–2 files per relevant active folder), absorbed content, and supersession conditions:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             FOLDER-BY-FOLDER CONSOLIDATION MATRIX                                │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### 7.1 Folder: `docs/01-requirements/` (Active Domain Folder)
- **Folder Status:** Active (Phase 1 Requirements Engineering).
- **Existing Files (11 files):**
  - `00-REQUIREMENTS-INDEX.md`
  - `01-PROJECT-REQUIREMENTS-SPECIFICATION.md`
  - `02-REQUIREMENT-CATALOGUE.md`
  - `03-SCOPE-AND-BOUNDARIES.md`
  - `04-REQUIREMENTS-TRACEABILITY.md`
  - `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`
  - `06-REQUIREMENTS-QUALITY-REVIEW.md`
  - `07-STAKEHOLDER-REQUIREMENT-DELTA-AND-IMPACT-ANALYSIS.md`
  - `08-MODULE-III-STAKEHOLDER-DELTA-ANALYSIS.md`
  - `09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md`
  - `10-STAKEHOLDER-DECISION-SHEET.md`
- **Unique Information in Folder:** 104 frozen atomic requirements (`REQ-01` to `104`); 11 official baseline TBDs (`REQ-TBD-01` to `11`); source-to-requirement forward/backward traceability matrix; system boundaries and exclusions; authoritative stakeholder delta decision cards (`CONF-01` to `10`).
- **Redundancies & Overlap:** High-level problem statements and vision in Doc 01 repeat across Doc 03 and downstream FRDs; Docs 07 and 08 were merged into 09 and finalized in 10; Doc 00 index duplicates downstream phase indexes.
- **Proposed Canonical File(s) in this Folder (Target: 1–2 files):**
  1. `01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md` *(Canonical Primary Specification)*
  2. `02-STAKEHOLDER-DECISION-SHEET.md` *(Provisional Reference Register — Retained in place)*
- **Content Absorbed into Canonical File(s):**
  - `01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md` absorbs: Vision & Problem Statement (from 01), System Scope & Boundaries (from 03), 104 Frozen Atomic Requirements (verbatim from 02), Traceability Matrix (from 04), and 11 Official Baseline TBDs (from 05).
  - `02-STAKEHOLDER-DECISION-SHEET.md` retains the authoritative decision cards from Doc 10 (clearly tagged as reference-only `[E]`).
- **Files Superseded Only After Successful Verification:**
  - Docs `00`, `01`, `03`, `04` superseded by `01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md`.
  - Docs `07`, `08`, `09` superseded by `02-STAKEHOLDER-DECISION-SHEET.md`.
  - Doc `06` (historical quality review) retained as an in-folder historical review document or appended to SRS.

---

### 7.2 Folder: `docs/02-business-process/` (Active Domain Folder)
- **Folder Status:** Active (Phase 2 Business Process Modeling).
- **Existing Files (9 files):**
  - `00-BUSINESS-PROCESS-INDEX.md`
  - `01-BUSINESS-PROCESS-FRAMEWORK.md`
  - `02-MODULE-I-BUSINESS-PROCESSES.md`
  - `03-MODULE-II-BUSINESS-PROCESSES.md`
  - `04-MODULE-III-BUSINESS-PROCESSES.md`
  - `05-CROSS-MODULE-BUSINESS-PROCESSES.md`
  - `06-BUSINESS-RULES-AND-DECISION-POINTS.md`
  - `07-BUSINESS-PROCESS-SLA-AND-ESCALATION.md`
  - `08-BUSINESS-PROCESS-QUALITY-REVIEW.md`
- **Unique Information in Folder:** 59 business processes (`BP-M1-001`..`011`, `BP-M2-001`..`020`, `BP-M3-001`..`022`, `BP-XMOD-001`..`006`); RACI responsibility matrix and actor taxonomy; 60 frozen business rules (`BR-01` to `BR-60`); SLA countdown timers, auto-lock rules, and escalation pathways.
- **Redundancies & Overlap:** Actor definitions in Doc 01 repeat across Docs 02–05 and FRDs; change request workflows in Doc 02 duplicate FRD 01 steps; SLA timers in Doc 07 are partially restated in individual process narratives.
- **Proposed Canonical File(s) in this Folder (Target: 2 files):**
  1. `01-BUSINESS-PROCESS-AND-WORKFLOW-SPECIFICATION.md` *(Canonical Workflow Model)*
  2. `02-BUSINESS-RULES-SPECIFICATION.md` *(Authoritative Business Rules Catalogue)*
- **Content Absorbed into Canonical File(s):**
  - `01-BUSINESS-PROCESS-AND-WORKFLOW-SPECIFICATION.md` absorbs: Modeling Framework & RACI Matrix (from 01), 11 Module I processes (from 02), 20 Module II processes (from 03), 22 Module III processes (from 04), 6 cross-module life-cycle handshakes (from 05), and SLA Timelines & Escalation Framework (from 07).
  - `02-BUSINESS-RULES-SPECIFICATION.md` retains verbatim the 60 frozen business rules (`BR-01` to `BR-60`) from Doc 06.
- **Files Superseded Only After Successful Verification:**
  - Docs `00`, `01`, `02`, `03`, `04`, `05`, `07` superseded by `01-BUSINESS-PROCESS-AND-WORKFLOW-SPECIFICATION.md`.
  - Doc `08` (historical quality review) retained as an in-folder historical review document or appended to workflow spec.

---

### 7.3 Folder: `docs/03-functional-requirements/` (Active Domain Folder)
- **Folder Status:** Active (Phase 3 Functional Requirements Specification).
- **Existing Files (6 files):**
  - `00-FRD-INDEX.md`
  - `01-MODULE-I-FUNCTIONAL-REQUIREMENTS.md`
  - `02-MODULE-II-FUNCTIONAL-REQUIREMENTS.md`
  - `03-MODULE-III-FUNCTIONAL-REQUIREMENTS.md`
  - `04-SHARED-FUNCTIONAL-REQUIREMENTS.md`
  - `05-FRD-QUALITY-REVIEW.md`
- **Unique Information in Folder:** 152 granular functional requirements (`MOD1-REQ-*` [28], `MOD2-REQ-*` [46], `MOD3-REQ-*` [52], `SHR-REQ-*` [26]); detailed input validation rules, acceptance criteria, UI error states, and cross-module signal triggers.
- **Redundancies & Overlap:** High-level narrative introductions in Docs 01–04 repeat Phase 1 vision; actor definitions repeat Phase 2 RACI; workflow stage descriptions duplicate business process steps.
- **Proposed Canonical File(s) in this Folder (Target: 1 file):**
  1. `01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md` *(Unified System Functional Specification)*
- **Content Absorbed into Canonical File(s):**
  - `01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md` absorbs all 152 functional requirements organized into discrete module chapters: Module I (from 01), Module II (from 02), Module III (from 03), and Shared Platform Services (from 04).
- **Files Superseded Only After Successful Verification:**
  - Docs `00`, `01`, `02`, `03`, `04` superseded by `01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md`.
  - Doc `05` (historical quality review verifying 152 FRDs) retained as an in-folder historical review document.

---

### 7.4 Folder: `docs/04-non-functional-requirements/` (Pending Folder)
- **Folder Status:** Pending / Intentionally Empty.
- **Existing Files:** None (0 files).
- **Consolidation Action:** Retain folder untouched. When Phase 5 non-functional requirements commence, author a single canonical specification: `01-NON-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md`. No filler documents created prematurely.

---

### 7.5 Folder: `docs/05-user-roles/` (Pending Folder)
- **Folder Status:** Pending / Intentionally Empty.
- **Existing Files:** None (0 files).
- **Consolidation Action:** Retain folder untouched. When user roles modeling commences, author a single canonical specification: `01-USER-ROLES-AND-PERMISSIONS-SPECIFICATION.md`.

---

### 7.6 Folder: `docs/06-workflows/` (Pending Folder)
- **Folder Status:** Pending / Intentionally Empty.
- **Existing Files:** None (0 files).
- **Consolidation Action:** Retain folder untouched. When executable workflow state machines and BPMN diagrams commence, author a single canonical specification: `01-WORKFLOW-STATE-MACHINE-SPECIFICATION.md`.

---

### 7.7 Folder: `docs/07-system-architecture/` (Active Architecture Folder)
- **Folder Status:** Active (Phase 1.5 Real-Time ADR).
- **Existing Files (1 file):**
  - `ADR-001-REAL-TIME-COMMUNICATION.md`
- **Unique Information in Folder:** Architectural Decision Record formally approving Socket.IO over polling/SSE for real-time notification push, SLA countdowns, and dynamic org-chart invalidation.
- **Redundancies & Overlap:** None.
- **Proposed Canonical File(s) in this Folder (Target: 1 file):**
  1. `ADR-001-REAL-TIME-COMMUNICATION.md` *(Retained Standalone)*
- **Consolidation Action:** Retain `ADR-001` in place. Note: [`source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md) remains in `source-requirements/` untouched.

---

### 7.8 Folder: `docs/08-database/` (Active Database Folder)
- **Folder Status:** Active (Phase 4 Database Documentation: Steps 1 through 5).
- **Existing Files (7 files):**
  - `00-DATABASE-DOCUMENTATION-INDEX.md`
  - `01-DATABASE-DESIGN-OVERVIEW.md`
  - `02-DATA-MODEL-OVERVIEW.md`
  - `03-ENTITY-IDENTIFICATION.md`
  - `04-ENTITY-RELATIONSHIP-SPECIFICATION.md`
  - `05-ENTITY-WISE-DETAILED-SPECIFICATION.md`
  - `06-DATABASE-SCHEMA-SPECIFICATION.md`
- **Unique Information in Folder:** 33 conceptual entities (`ENT-MOD1-*`, `ENT-MOD2-*`, `ENT-MOD3-*`, `ENT-SHR-*`); 41 conceptual relationships (`REL-*`); 344 verified logical attributes with domain types, requiredness, and sensitivity classifications; conceptual-to-logical schema profile mappings.
- **Redundancies & Overlap:** Architecture principles in Doc 01 duplicate `TECHNOLOGY_ARCHITECTURE_BASELINE.md`; domain mapping in Doc 02 duplicates Doc 01; entity descriptions in Doc 03 repeat in Docs 04, 05, and 06; schema profiles in Doc 06 restate entity and relationship inventories from Docs 03 and 04.
- **Proposed Canonical File(s) in this Folder (Target: 2 files):**
  1. `01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md` *(Comprehensive Conceptual, Logical & Future Physical DB Spec)*
  2. `02-LOGICAL-DATA-DICTIONARY.md` *(Authoritative 344 Attributes Data Dictionary)*
- **Status Clarification — Existing vs. Future Database Documents:**
  - **Database Phase Is NOT Cancelled:** The HRMS database engineering phase remains fully active. Steps 1 through 5 of Phase 4 are complete, establishing approved conceptual and logical data architectures across seven existing specifications (`00` through `06`).
  - **Existing Conceptual & Logical Specs:** Documents `01` through `06` rigorously define 33 conceptual entities, 41 conceptual relationships, and 344 logical attributes with zero sequence gaps.
  - **Planned Future Physical Docs (`07` through `12`):** Rather than spawning six additional fragmented standalone files (for physical indexing, partitioning, temporal audit triggers, DDL migration scripts, and outbox staging), these future technical requirements will be **directly consolidated into the canonical two-document suite** (`01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md` and `02-LOGICAL-DATA-DICTIONARY.md`) when physical database design commences. This completely prevents documentation sprawl while delivering 100% of planned database engineering coverage.
- **Content Absorbed into Canonical File(s):**
  - `01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md` absorbs: Database Design Overview (from 01), Data Model Overview & Taxonomy (from 02), 33 Conceptual Entities (from 03), 41 Conceptual Relationships & ERDs (from 04), and Logical Schema Profiles (from 06). Also serves as the canonical host for future physical schema definitions (indexes, partition keys, DDL contracts).
  - `02-LOGICAL-DATA-DICTIONARY.md` retains verbatim the complete 344 logical attribute data dictionary from Doc 05.
- **Files Superseded Only After Successful Verification:**
  - Existing Docs `00`, `01`, `02`, `03`, `04`, `06` superseded by `01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md`.
  - Existing Doc `05` transitioned to `02-LOGICAL-DATA-DICTIONARY.md`.
  - Planned separate files `07` through `12` consolidated into the two canonical specs rather than created as standalone stubs.

---

### 7.9 Folders: `docs/09-api/` through `docs/15-deployment/` (Pending Folders)
- **`docs/09-api/`:** Pending Phase 9. Retained for future REST API / OpenAPI specifications.
- **`docs/10-ui-ux/`:** Pending Phase 10. Retained for future UI/UX Design System & Wireframes.
- **`docs/11-security/`:** Pending Phase 11. Retained for future Security, IAM & Access Control specs.
- **`docs/12-notifications-sla/`:** Pending Phase 12. Retained for future Notification Templates & SLA Engine specs.
- **`docs/13-reports/`:** Pending Phase 13. Retained for future Management Reporting & Analytics specs.
- **`docs/14-testing/`:** Pending Phase 14. Retained for future Verification & Test Specifications.
- **`docs/15-deployment/`:** Pending Phase 15. Retained for future Deployment & Operations Guides.
- **Consolidation Action across Folders 09–15:** Retain all 7 folders in place without deletion or renaming. No filler documents created prematurely.

---

### 7.10 Root Folders: `docs/` Root & `source-requirements/`
- **`docs/` Root:**
  - `PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md`: Retained in `docs/` as historical audit reference.
  - `DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md`: Retained in `docs/` as the active rationalization proposal.
- **`source-requirements/`:**
  - Retained 100% untouched.
  - `PROJECT_REQUIREMENTS_ANALYSIS.md` (foundational inception analysis) retained in place.
  - `TECHNOLOGY_ARCHITECTURE_BASELINE.md` (authoritative architecture baseline) retained in place.
  - All 7 primary binary assets (PDFs/JPEGs) across `Module-I/`, `Module-II/`, `Module-III/` retained in place.

---

## 8. Content Preservation and Traceability Strategy

To guarantee that a reduction in file count never compromises baseline fidelity, the following invariant preservation rules apply:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                            BASELINE ARTIFACT PRESERVATION MAPPING                                │
├───────────────────────────────┬────────────┬─────────────────────────────────────────────────────┤
│ BASELINE ARTIFACT             │ COUNT      │ TARGET CANONICAL LOCATION                           │
├───────────────────────────────┼────────────┼─────────────────────────────────────────────────────┤
│ Atomic Requirements           │ 104 REQs   │ docs/01-requirements/01-SOFTWARE-REQUIREMENTS-SPEC  │
│ Business Processes            │ 59 BPs     │ docs/02-business-process/01-BUSINESS-PROCESS-SPEC   │
│ Business Rules                │ 60 BRs     │ docs/02-business-process/02-BUSINESS-RULES-SPEC     │
│ Functional Requirements       │ 152 FRDs   │ docs/03-functional-reqs/01-FUNCTIONAL-REQS-SPEC     │
│ Official Baseline TBDs        │ 11 TBDs    │ docs/01-requirements/01-SOFTWARE-REQUIREMENTS-SPEC  │
│ Conceptual Entities           │ 33 Ents    │ docs/08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPEC │
│ Conceptual Relationships      │ 41 Rels    │ docs/08-database/01-DATABASE-DESIGN-AND-SCHEMA-SPEC │
│ Logical Attributes            │ 344 Attrs  │ docs/08-database/02-LOGICAL-DATA-DICTIONARY.md      │
│ Real-Time Decision Record     │ ADR-001    │ docs/07-system-architecture/ADR-001-REAL-TIME.md    │
│ Technology Architecture Base  │ Baseline   │ source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE│
│ Primary Source Assets         │ 7 Binaries │ source-requirements/Module-I, II, III (Untouched)   │
└───────────────────────────────┴────────────┴─────────────────────────────────────────────────────┘
```

- **Traceability Preservation:** Every consolidated document will preserve upstream and downstream traceability matrices. Requirement codes (`REQ-*`), process codes (`BP-*`), rule codes (`BR-*`), functional codes (`MOD*-REQ-*`), entity codes (`ENT-*`), relationship codes (`REL-*`), and attribute codes (`ATTR-*`) will remain completely intact.
- **5-Tier Classification Preservation:** The tags `[A]` (Explicit Requirement), `[B]` (Logical Implication), `[C]` (Approved Technical Decision), `[D]` (Proposed Detail), and `[E]` (TBD / Open Decision) will be explicitly retained on every item.

---

## 9. Documents Recommended for Removal (Category D)

In strict accordance with project directives: **Zero (0) documents are recommended for raw, unrecoverable deletion.**

Every document flagged for consolidation has its unique content mapped into a canonical specification inside its existing folder. No business rule, requirement, process, entity, or attribute will be discarded.

---

## 10. Future Documents and Intentionally Empty Folders (Category E)

The following ten (10) folders are **intentionally empty** and are **preserved** for future phases:
- `docs/04-non-functional-requirements/`
- `docs/05-user-roles/`
- `docs/06-workflows/`
- `docs/09-api/`
- `docs/10-ui-ux/`
- `docs/11-security/`
- `docs/12-notifications-sla/`
- `docs/13-reports/`
- `docs/14-testing/`
- `docs/15-deployment/`

**Policy on Empty Folders:** Retain all 10 folders in the repository structure. They represent planned future milestones. When those phases begin, author a concise set of 1–2 canonical specifications per folder rather than creating premature filler files.

---

## 11. Proposed Folder-Preserving Target Documentation Structure

The target documentation architecture achieves maximum lean efficiency while **strictly preserving every folder**:

```
d:\Desktop\HR-CHANGE-MANAGEMENT-SYSTEM\
│
├── source-requirements/                               ◄ [Authoritative Source Assets & Inception Baseline - UNTOUCHED]
│   ├── Module-I/ (2 Official PDFs)
│   ├── Module-II/ (1 Diagram + 2 PDFs)
│   ├── Module-III/ (1 Diagram + 1 PDF)
│   ├── PROJECT_REQUIREMENTS_ANALYSIS.md              ◄ [Foundational Inception Analysis]
│   └── TECHNOLOGY_ARCHITECTURE_BASELINE.md           ◄ [Master Technology Baseline - RETAINED IN PLACE]
│
├── docs/
│   │
│   ├── PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md      ◄ [Historical Structure Audit Reference]
│   ├── DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md ◄ [This Active Audit Report]
│   │
│   ├── 01-requirements/                              ◄ [CANONICAL TARGET: 1-2 SPECS]
│   │   ├── 01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md ◄ [Unified SRS: 104 Atomic Reqs + 11 TBDs + Traceability]
│   │   └── 02-STAKEHOLDER-DECISION-SHEET.md          ◄ [Provisional Reference Cards: CONF-01 to CONF-10]
│   │
│   ├── 02-business-process/                           ◄ [CANONICAL TARGET: 2 SPECS]
│   │   ├── 01-BUSINESS-PROCESS-AND-WORKFLOW-SPEC.md  ◄ [Unified Workflow Model: 59 Processes + RACI + SLA]
│   │   └── 02-BUSINESS-RULES-SPECIFICATION.md        ◄ [Authoritative 60 Frozen Business Rules (BR-*)]
│   │
│   ├── 03-functional-requirements/                    ◄ [CANONICAL TARGET: 1 SPEC]
│   │   └── 01-FUNCTIONAL-REQUIREMENTS-SPECIFICATION.md◄ [Unified Functional Specification: 152 Functional Reqs]
│   │
│   ├── 04-non-functional-requirements/               ◄ [PRESERVED — Pending Phase 5]
│   ├── 05-user-roles/                                 ◄ [PRESERVED — Pending Phase 5]
│   ├── 06-workflows/                                  ◄ [PRESERVED — Pending Phase 6]
│   │
│   ├── 07-system-architecture/                        ◄ [CANONICAL TARGET: 1 ADR]
│   │   └── ADR-001-REAL-TIME-COMMUNICATION.md         ◄ [Active Decision Record approving Socket.IO]
│   │
│   ├── 08-database/                                   ◄ [CANONICAL TARGET: 2 SPECS]
│   │   ├── 01-DATABASE-DESIGN-AND-SCHEMA-SPEC.md      ◄ [Unified Conceptual & Logical DB Spec: 33 Ents, 41 Rels]
│   │   └── 02-LOGICAL-DATA-DICTIONARY.md              ◄ [Authoritative 344 Attributes Data Dictionary]
│   │
│   ├── 09-api/                                        ◄ [PRESERVED — Pending Phase 9]
│   ├── 10-ui-ux/                                      ◄ [PRESERVED — Pending Phase 10]
│   ├── 11-security/                                   ◄ [PRESERVED — Pending Phase 11]
│   ├── 12-notifications-sla/                          ◄ [PRESERVED — Pending Phase 12]
│   ├── 13-reports/                                    ◄ [PRESERVED — Pending Phase 13]
│   ├── 14-testing/                                    ◄ [PRESERVED — Pending Phase 14]
│   └── 15-deployment/                                 ◄ [PRESERVED — Pending Phase 15]
```

---

## 12. Verified vs. Unresolved Technical Decisions

In strict compliance with [`source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md) and approved ADRs, all technical decisions are categorized under the 5-tier classification framework:

### 12.1 Verified Approved Technical Decisions (`[C]`)
- **Frontend Presentation Framework:** Next.js (React) with App Router, TypeScript $\rightarrow$ **`[C] Approved Technical Decision`** / `APPROVED BASELINE` (`TDR-02`).
- **Frontend Styling Architecture:** Strictly **Vanilla CSS + CSS Modules (`*.module.css`) + CSS Variables** (Custom Properties Design Tokens) $\rightarrow$ **`[C] Approved Technical Decision`** / `APPROVED BASELINE` (`TDR-03`). Tailwind CSS, Shadcn UI, and utility CSS frameworks are explicitly **EXCLUDED**.
- **Backend Application Framework:** NestJS, TypeScript REST API implementing the **Modular Monolith** pattern with strict domain boundaries $\rightarrow$ **`[C] Approved Technical Decision`** / `APPROVED BASELINE` (`TDR-04`).
- **Primary Relational Store:** PostgreSQL as the system of record for ACID transactional updates and temporal logging $\rightarrow$ **`[C] Approved Technical Decision`** / `APPROVED BASELINE` (`TDR-05`).
- **Real-Time Communication Layer:** Socket.IO over WebSocket (NestJS Gateway + Redis Adapter) $\rightarrow$ **`[C] Approved Technical Decision`** (formally approved in [`ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md) and `TDR-07`).
- **In-Memory Cache & Distributed Locking:** Redis for caching org hierarchy trees, role permissions, and managing atomic distributed locks across app instances $\rightarrow$ **`[C] Approved Technical Decision`** (`TDR-06`, `APPROVED BASELINE`).
- **Asynchronous Queue Backing Store:** Redis as the backing queue store for background workers executing temporal SLA countdowns, auto-locks, reminder notifications, and PDF generation $\rightarrow$ **`[C] Approved Technical Decision`** (`TDR-06`).
- **Asynchronous Workers / Scheduler Capability:** The *generic capability* of asynchronous background workers / schedulers $\rightarrow$ **`[C] Approved Technical Decision`** (`TDR-06`).
- **Document & Binary Storage:** S3-compatible Object Storage API $\rightarrow$ **`[C] Approved Technical Decision`** (metadata managed in PostgreSQL; binaries stored in object storage accessed via time-limited presigned URLs).

### 12.2 Technical Claims Downgraded to `[D]` or `[E]` with Clear Reasoning
- **Redis as a General Enterprise Message Broker / Event Bus:**
  - **Classification:** **Downgraded to `[D] Proposed Detail` / EXCLUDED from Baseline**.
  - **Reasoning:** In `source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md` (`TDR-01`, lines 40–58 and `TDR-06`), the architectural style is strictly a **Modular Monolith**. Inter-module communication is explicitly defined as **synchronous or asynchronous in-process domain events within the same application process**. Redis is approved exclusively for in-memory caching, distributed locks, queue backing for worker jobs, and Socket.IO cluster scaling (`ADR-001`). Claiming Redis as an enterprise-wide message broker for business domain event choreography contradicts `TDR-01` and is unsupported by the architecture baseline. PostgreSQL remains the sole transactional system of record, utilizing the transactional outbox pattern (`ENT-SHR-08`) for external ERP synchronization.
- **Specific Queue Implementation Library (BullMQ):**
  - **Classification:** **`[D] Proposed Detail`**.
  - **Reasoning:** Note on line 92 of `TECHNOLOGY_ARCHITECTURE_BASELINE.md` explicitly categorizes BullMQ as a proposed detail (`[D]`). The generic capability of background queueing is approved (`[C]`), but the specific library is not mandated.
- **Containerization & Deployment Runtime (Docker / OCI):**
  - **Classification:** **`[D] Proposed Detail`**.
  - **Reasoning:** Specific multi-stage Dockerfiles, Docker Compose service definitions, and container orchestration belong to Phase 15 (`docs/15-deployment/`), not active code.
- **Physical Database Implementation Details:**
  - **Classification:** **`[D] Proposed Detail` / Draft / Pending Review**.
  - **Reasoning:** JSONB physical schemas, physical indexes (B-tree, GIN), table partitioning strategies, primary/foreign key cascade behaviors, and ORM entity models are classified as `[D]`. No physical DDL or migrations are approved for implementation during this documentation-only phase.
- **Authentication Token Lifetimes & Rotation Mechanics:**
  - **Classification:** **`[D] Proposed Detail` / `[E] Open Decision`**.
  - **Reasoning:** Specific JWT access token lifetimes, refresh token rotation mechanics, and signed guest token structures are deferred to Phase 11 (`docs/11-security/`).

---

## 13. Authoritative Official 11 TBDs Reconciliation

### 13.1 Mandated 11 TBDs Master Register
In strict accordance with the authoritative project register established by reopening and verifying [`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md), reconciled with [`docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md) Section 10 (Table 10A, lines 244–257) and confirmed in [`docs/02-business-process/08-BUSINESS-PROCESS-QUALITY-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/02-business-process/08-BUSINESS-PROCESS-QUALITY-REVIEW.md) (line 119), the eleven (11) official baseline TBD items are defined below. 

To maintain strict documentation fidelity and prevent artificial alignment, each item is cross-checked against actual requirement anchors and the entity open decisions register in [`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md) Section 12. Where a database attribute decision does not exist or has a different identifier, it is explicitly reported rather than inventing unsupported mappings:

| Official TBD ID | Authoritative Title & Domain | Catalogue Anchor Status | Database `ATTR-DEC-*` Status (`08-database/05`) | Nature of Uncertainty / Missing Specification | Required Institutional Action |
|---|---|---|---|---|---|
| **`REQ-TBD-01`** | **Resignation intake mechanism** | Qualifies **`REQ-MOD2-08`**, **`REQ-INT-02`** *(Mislabeled as `REQ-EXT-03` in Doc 09)* | Mapped in DB as **`ATTR-DEC-06`** (`ENT-MOD2-10` / `ATTR-URG-03`)<br>*(Does not map to `ATTR-DEC-01`)* | Employee self-service submission vs. administrative entry in Module I prior to replacement clock trigger. | Head of HR operational process directive. |
| **`REQ-TBD-02`** | **ERP technical transport protocol** | Standalone **`REQ-EXT-03`** (`SHR-ERP-REQ-03`, `[E]`) | Mapped in DB as **`ATTR-DEC-01`** (`ENT-MOD1-01` / `ATTR-EMP-01`, `ENT-SHR-08` / `ATTR-ERP-05`)<br>*(Does not map to `ATTR-DEC-02`)* | Specific transport mechanism (REST API webhooks, database staging tables, or batch SFTP) for external ERP reflection. | University CIO / ERP Technical Directorate confirmation. |
| **`REQ-TBD-03`** | **Legacy service data cutover strategy** | Relates to **`REQ-MOD1-01`**, **`REQ-MOD1-06`**; cited in `02-business-process/08` line 119 (`BP-M1-001`, `003`) | **UNMAPPED IN DATABASE**<br>*(No `ATTR-DEC-*` entry exists in document 05 for legacy cutover)* | Historical employee service record migration strategy and cutover window. Day-forward baseline preserved. | Registrar & HR Operations policy ruling. |
| **`REQ-TBD-04`** | **Mid-cycle supervisor transfer evaluation attribution guidelines** | Institutional policy qualifying **`REQ-MOD3-10`** | **UNMAPPED IN DATABASE**<br>*(No `ATTR-DEC-*` entry exists in document 05 for supervisor transfer)* | Rules governing score attribution and evaluation responsibilities (pro-rata vs. full cycle) when reporting supervisors change mid-cycle. | HR Leadership & Academic Council policy ruling. |
| **`REQ-TBD-05`** | **University Group-D pre-defined compensation slab amounts and increment rupee values** | Qualifies **`REQ-MOD3-09`**, **`REQ-MOD3-19`** | Mapped in DB as **`ATTR-DEC-05`** (`ENT-MOD3-03` / `ATTR-GDA-08`, `ENT-MOD3-06` / `ATTR-KRA-06`, `ENT-MOD3-09` / `ATTR-ECM-08`) | Quantitative rupee slab amounts and percentage brackets for Group-D annual compensation revisions. | Senior Management & University Finance Committee approval. |
| **`REQ-TBD-06`** | **Academic Statutory SCM digital scoring parameter percentage weights** | Qualifies **`REQ-MOD2-15`** | Mapped in DB as **`ATTR-DEC-04`** (`ENT-MOD2-07` / `ATTR-SCM-08`)<br>*(Does not map to `ATTR-DEC-06`)* | Statutory Selection Committee Meeting digital scoring parameter percentage weights and candidate evaluation dimensions. | Academic Council & Vice Chancellor approval. |
| **`REQ-TBD-07`** | **Non-Academic three-round assessment dimension percentage weights and cutoff thresholds** | Qualifies **`REQ-MOD2-16`** | **UNMAPPED IN DATABASE**<br>*(No `ATTR-DEC-*` entry exists in document 05 for Non-Academic 3-round interview scoring thresholds)* | Dimension weights, interview scoring sheets, and qualifying cutoff thresholds for Non-Academic hiring rounds. | Head of HR selection policy directive. |
| **`REQ-TBD-08`** | **Faculty ECM TNU Protocol matrix benchmark thresholds and percentage cutoffs** | Qualifies **`REQ-MOD3-18`** | Mapped in DB as **`ATTR-DEC-04`** (`ENT-MOD3-09` / `ATTR-ECM-07`)<br>*(Does not map to `ATTR-DEC-08`, which is LOI)* | Mathematical scoring formula, matrix benchmark thresholds, and percentage cutoffs for the Faculty ECM evaluation matrix. | Academic Council & Vice Chancellor approval. |
| **`REQ-TBD-09`** | **Group-D 12-month parameter-weighted averaging formula and coefficients** | Qualifies **`REQ-MOD3-04`** | **UNMAPPED IN DATABASE**<br>*(No `ATTR-DEC-*` entry exists in document 05 for Group-D monthly averaging formula)* | Formula and statistical weights for synthesizing 12 monthly ratings into the annual collation report. | HR Performance Management policy ruling. |
| **`REQ-TBD-10`** | **Additional Responsibility administrative allowance policy confirmation** | Qualifies **`REQ-MOD1-13`**, **`REQ-MOD1-14`** (Format 3h / Format 8) | Mapped in DB as **`ATTR-DEC-09`** (`ENT-MOD1-04` / `ATTR-CHG-12`)<br>*(Does not map to `ATTR-DEC-10`)* | Policy rules governing whether secondary administrative appointments (e.g., HoD, Proctor, Warden) carry mandatory administrative allowances or honorariums. | HR Leadership & Finance Directorate policy ruling. |
| **`REQ-TBD-11`** | **SCM External Subject Expert digital verification and access mechanism** | Standalone **`REQ-EXT-05`** (`[E]`) | Mapped in DB as **`ATTR-DEC-07`** (`ENT-SHR-01` / `ATTR-USR-06`)<br>*(Does not map to `ATTR-DEC-11`)* | Identity verification, time-limited tokens, and digital access mechanism for external SCM panel experts lacking institutional accounts. | University IT Systems & Cybersecurity Directorate confirmation. |

### 13.2 Technical-Cadre Appraisal Allocation: Institutional Policy Decision
- **Status:** **Separate Unresolved Institutional Policy Decision (`[E] Open Decision`)**.
- **Scope:** Workflow routing and appraisal track allocation for mid-level technical staff (Lab Technicians, Technical Assistants, and Teaching Associates) between Group-D / Band I Staff (Subsystem 1), General Staff KRA/KPI (Subsystem 2), or an adapted Faculty review track (Subsystem 3).
- **Governance Mandate:** In strict adherence to project instructions, technical-cadre appraisal allocation is maintained as a **standalone open policy question** and is **NOT** mapped to any official numbered TBD in this 11-item register (since `REQ-TBD-03` is officially allocated to *Legacy service data cutover strategy*). Requires formal ruling by the Registrar and HR Leadership.

### 13.3 Cross-Specification Discrepancy Analysis (Status: `DISCREPANCY FOUND`)
An audit across Phase 1 and Phase 4 documents reveals a structural numbering discrepancy:
1. **The Mandated Baseline (`09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md` Table 10A):** Establishes the 11 items shown in Section 13.1 above (`TBD-01` = Resignation intake, `TBD-02` = ERP protocol, `TBD-03` = Legacy cutover, etc.).
2. **The Controlled Requirements TBD Log (`05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`):** Uses an alternate numbering sequence (`TBD-01` = ERP sync, `TBD-02` = Attachment schemas, `TBD-03` = Staff appraisal track, `TBD-04` = TNU protocol weights, `TBD-05` = Compensation slabs, `TBD-06` = Resignation intake, `TBD-07` = SSO & External Expert, `TBD-08` = LOI lifecycle, `TBD-09` = Administrative allowance, `TBD-10` = Outbound gateways, `TBD-11` = Document retention). This discrepancy was formally flagged as Issue **`AUD-06`** in [`docs/PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md).
3. **Database Specification Harmonization:** Section 12 of [`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md) (`ATTR-DEC-01` to `11`) followed the numbering of Document 05 rather than Table 10A. Consequently, four items (`TBD-03`, `TBD-04`, `TBD-07`, `TBD-09`) have **no corresponding database attribute decision records** in document 05.
4. **Resolution:** During Stage 2 consolidation, a unified canonical TBD register must be formalized within `01-requirements/01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md`, establishing a single authoritative numbering scheme across all domains.

---

## 14. Official Module Requirements & Attribute Count Reconciliation

### 14.1 Lab Technician Recruitment Track — Source Evidence
A direct citation from the official source requirement brief confirms the classification:
- **Primary Source Asset:** `source-requirements/Module-II/Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf`
- **Section 1 (Introduction & Scope, Page 1):**
  > *"As the manpower-planning approval chain and the selection process differ for **Academic (Faculty & Lab Technician)** and **Non-Academic (Non-Faculty)** positions, the system shall support these as two distinct, configurable workflows, while sharing a common Sourcing and CV Database engine across both."*
- **Section 1.a & 1.c:**
  > *"from the Associate Dean (Academics) to the Deans of Schools for **Faculty & Lab Technician** positions, and from HR to the concerned Department Heads for **Non-Faculty** positions..."*
- **Selection Process Header:**
  > *"**Workflow A: Selection Process for Academic Positions (Faculty, Teaching Associates, Technical Assistants, Lab Technicians)**"*
- **Baseline Requirement Mapping:** `REQ-MOD2-01`, `REQ-MOD2-02`, `REQ-MOD2-15`.
- **Selection Workflow:** Statutory Selection Committee Meeting (SCM) process (`ENT-MOD2-07`).
- **Stakeholder Delta Boundary:** Stakeholder feedback item `CONF-04` / `CFL-02` (which suggested evaluating Lab Technicians under Non-Academic SCM or a separate panel) remains an **unapproved provisional reference item** in [`docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md) and is NOT part of the approved baseline.

### 14.2 Module III Appraisal Subsystems & Technical Staff Allocation
- **Three Distinct Approved Subsystems:**
  - *Subsystem 1:* Group-D Staff Monthly Performance Evaluation (12 monthly ratings collated into annual report, `ENT-MOD3-01` to `03`).
  - *Subsystem 2:* General Staff KRA/KPI Quarterly Performance Review (Q1-Q4 quarterly cycle, `ENT-MOD3-04` to `06`).
  - *Subsystem 3:* Faculty Annual Performance Appraisal (Self-appraisal dossier, multi-unit verification, Executive Council Meeting / ECM session, and TNU Protocol Matrix, `ENT-MOD3-07` to `09`).
- **Technical Cadre Allocation:** Kept strictly as an **unresolved institutional policy question (`[E] Open Decision`)**, requiring Registrar / HR Leadership formal ruling.

### 14.3 Command-Verified Logical Attribute Recalculation (Status: `VERIFIED`)
A rigorous AST-based verification script was executed directly on [`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md). 

#### Command-Verified Execution Output:
```
====================================================================================================
                       COMMAND-VERIFIED ATTRIBUTE AUDIT RESULTS
====================================================================================================
 Total Conceptual Entities with Attribute Tables: 33 Entities
 Total Tabular Attribute Definition Rows        : 344 Rows
 Total Unique Attribute IDs Defined             : 344 Unique IDs
 Duplicate Attribute IDs                        : 0 (Zero duplicates found)
 Prefixes Checked Across Attribute Space        : 33 Prefixes (All verified continuous 1..max)
 Prefixes with Sequence Gaps                    : 0 (Zero sequence gaps found)
 Outside Attribute Mentions (Non-Table Lines)   : 142 Occurrences across 114 Unique Attribute IDs
 Section 12 Open Decision IDs (ATTR-DEC-*)      : 11 Unique IDs (ATTR-DEC-01 through ATTR-DEC-11)
 Distinct Entity Attribute IDs Mentioned Outside: 103 Unique Attribute IDs
 Undefined Attribute IDs Mentioned Outside      : 0 (set() - All 103 resolve to defined attributes)
 Section 10 Cross-Module Mentions               : 21 Occurrences across 16 Unique Attribute IDs
====================================================================================================
```

#### Detailed Entity-by-Entity Attribute Breakdown:
| Entity ID | Entity Name | Prefix | Count | ID Range | Sequence Continuity |
|---|---|:---:|:---:|:---:|:---:|
| `ENT-MOD1-01` | Central Employee Master Record | `ATTR-EMP-` | 14 | `ATTR-EMP-01` .. `14` | Continuous (1..14) |
| `ENT-MOD1-02` | Organization Structure Hierarchy | `ATTR-ORG-` | 8 | `ATTR-ORG-01` .. `08` | Continuous (1..8) |
| `ENT-MOD1-03` | Employee Digital Dossier | `ATTR-DOS-` | 8 | `ATTR-DOS-01` .. `08` | Continuous (1..8) |
| `ENT-MOD1-04` | Service Change Request Master | `ATTR-CHG-` | 12 | `ATTR-CHG-01` .. `12` | Continuous (1..12) |
| `ENT-MOD1-05` | Change Request Approval Tier | `ATTR-APP-` | 7 | `ATTR-APP-01` .. `07` | Continuous (1..7) |
| `ENT-MOD1-06` | Service History Ledger & Version Record | `ATTR-HST-` | 12 | `ATTR-HST-01` .. `12` | Continuous (1..12) |
| **Module I Subtotal** | **6 Entities** | | **61** | | **100% Continuous** |
| `ENT-MOD2-01` | Academic Manpower Plan Post | `ATTR-AMP-` | 11 | `ATTR-AMP-01` .. `11` | Continuous (1..11) |
| `ENT-MOD2-02` | Non-Academic Manpower Plan Post | `ATTR-NMP-` | 12 | `ATTR-NMP-01` .. `12` | Continuous (1..12) |
| `ENT-MOD2-03` | Manpower Requisition Form (MRF) | `ATTR-MRF-` | 13 | `ATTR-MRF-01` .. `13` | Continuous (1..13) |
| `ENT-MOD2-04` | Open Position Registry Entry | `ATTR-OPT-` | 10 | `ATTR-OPT-01` .. `10` | Continuous (1..10) |
| `ENT-MOD2-05` | Candidate Profile & Sourced Application | `ATTR-CAN-` | 13 | `ATTR-CAN-01` .. `13` | Continuous (1..13) |
| `ENT-MOD2-06` | Recruiter Calling Stage (RCS) Feedback Record | `ATTR-RCS-` | 12 | `ATTR-RCS-01` .. `12` | Continuous (1..12) |
| `ENT-MOD2-07` | Selection Committee Meeting (SCM) Assessment | `ATTR-SCM-` | 11 | `ATTR-SCM-01` .. `11` | Continuous (1..11) |
| `ENT-MOD2-08` | Non-Academic Interview Round Assessment | `ATTR-NIR-` | 11 | `ATTR-NIR-01` .. `11` | Continuous (1..11) |
| `ENT-MOD2-09` | Letter of Intent (LOI) & Onboarding Record | `ATTR-LOI-` | 12 | `ATTR-LOI-01` .. `12` | Continuous (1..12) |
| `ENT-MOD2-10` | Urgent Replacement Pipeline Entry | `ATTR-URG-` | 10 | `ATTR-URG-01` .. `10` | Continuous (1..10) |
| **Module II Subtotal**| **10 Entities** | | **115** | | **100% Continuous** |
| `ENT-MOD3-01` | Group-D Evaluation Form Template | `ATTR-GDT-` | 7 | `ATTR-GDT-01` .. `07` | Continuous (1..7) |
| `ENT-MOD3-02` | Group-D Monthly Performance Evaluation Record | `ATTR-GDM-` | 12 | `ATTR-GDM-01` .. `12` | Continuous (1..12) |
| `ENT-MOD3-03` | Group-D Annual Collation Report | `ATTR-GDA-` | 11 | `ATTR-GDA-01` .. `11` | Continuous (1..11) |
| `ENT-MOD3-04` | General Staff KRA Goal Assignment Record | `ATTR-KRG-` | 10 | `ATTR-KRG-01` .. `10` | Continuous (1..10) |
| `ENT-MOD3-05` | General Staff Quarterly Review Record | `ATTR-KRQ-` | 12 | `ATTR-KRQ-01` .. `12` | Continuous (1..12) |
| `ENT-MOD3-06` | General Staff Annual Appraisal Assessment | `ATTR-KRA-` | 10 | `ATTR-KRA-01` .. `10` | Continuous (1..10) |
| `ENT-MOD3-07` | Faculty ECM Monthly Eligibility Batch Record | `ATTR-FEB-` | 8 | `ATTR-FEB-01` .. `08` | Continuous (1..8) |
| `ENT-MOD3-08` | Faculty Self-Appraisal Dossier & Verification | `ATTR-FSD-` | 13 | `ATTR-FSD-01` .. `13` | Continuous (1..13) |
| `ENT-MOD3-09` | Faculty ECM Session & Evaluation Matrix Record| `ATTR-ECM-` | 13 | `ATTR-ECM-01` .. `13` | Continuous (1..13) |
| **Module III Subtotal**| **9 Entities** | | **96** | | **100% Continuous** |
| `ENT-SHR-01` | User Account & Authentication Identity | `ATTR-USR-` | 8 | `ATTR-USR-01` .. `08` | Continuous (1..8) |
| `ENT-SHR-02` | Role Definition & Permission Profile | `ATTR-ROL-` | 7 | `ATTR-ROL-01` .. `07` | Continuous (1..7) |
| `ENT-SHR-03` | Universal Workflow Instance & State Record | `ATTR-WFL-` | 10 | `ATTR-WFL-01` .. `10` | Continuous (1..10) |
| `ENT-SHR-04` | SLA Countdown & Breach Registry Entry | `ATTR-SLA-` | 9 | `ATTR-SLA-01` .. `09` | Continuous (1..9) |
| `ENT-SHR-05` | Document Metadata & Object Pointer | `ATTR-DOC-` | 10 | `ATTR-DOC-01` .. `10` | Continuous (1..10) |
| `ENT-SHR-06` | Outbound Notification Dispatch Event | `ATTR-NTF-` | 9 | `ATTR-NTF-01` .. `09` | Continuous (1..9) |
| `ENT-SHR-07` | Universal Audit Log Entry | `ATTR-AUD-` | 10 | `ATTR-AUD-01` .. `10` | Continuous (1..10) |
| `ENT-SHR-08` | ERP Transactional Outbox Event | `ATTR-ERP-` | 9 | `ATTR-ERP-01` .. `09` | Continuous (1..9) |
| **Shared Subtotal** | **8 Entities** | | **72** | | **100% Continuous** |
| **GRAND TOTAL** | **33 Entities** | | **344** | | **100% CONTINUOUS (344/344)** |

#### Inferred Historical Reconciliation (Root Cause Analysis):
1. **Frozen Baseline Comparison:** The verified count of **344 attributes** matches the frozen data architecture baseline of 344 exactly.
2. **Reconciliation of Historical "355" Total:** Section 12 contains eleven (11) decision tags labeled `ATTR-DEC-01` through `ATTR-DEC-11`. An unanchored regex tool in an earlier audit scanned the entire file for `ATTR-[A-Z]+-[0-9]+` without filtering out Section 12 decision rows, yielding $344 + 11 = 355$.
3. **Reconciliation of Historical "Shared 83" Total:** Section 10 contains 21 narrative mentions across 16 unique attribute IDs. An earlier script that did not detect the closing table boundary of `ENT-SHR-08` appended those cross-references to Shared Platform ($72 + 11 = 83$).

---

## 15. Unresolved Decisions and Mentor Clarifications

Before executing the folder-by-folder consolidation plan, explicit direction should be confirmed on five governance points:

1. **Adoption of Folder-Preserving Consolidated Specifications:**
   Confirmation to proceed with consolidating the 35 active Markdown documents into **7 core specifications + 1 ADR inside their existing folders**, while retaining all 15 primary folder names.
2. **Business Process and Business Rules Separation:**
   Confirmation to maintain `docs/02-business-process/02-BUSINESS-RULES-SPECIFICATION.md` as a dedicated companion specification to `01-BUSINESS-PROCESS-AND-WORKFLOW-SPEC.md`, ensuring business rules remain directly referenceable by test suites and validation code.
3. **Database Phase Consolidation Clarification & Authorization:**
   Confirmation that Phase 4 is **NOT cancelled** and that the planned expansion to 13 separate documents is rationalized by absorbing downstream physical database specifications directly into `01-DATABASE-DESIGN-AND-SCHEMA-SPECIFICATION.md` and `02-LOGICAL-DATA-DICTIONARY.md`.
4. **Stakeholder Delta Reference Retention:**
   Confirmation that stakeholder review materials (`10-STAKEHOLDER-DECISION-SHEET.md`) will remain in `docs/01-requirements/` as a clearly labeled reference register without promoting unapproved `CONF-*` items to the approved baseline.
5. **Harmonization of TBD Numbering & Staff Appraisal Track Ruling:**
   Formal decision on reconciling the numbering discrepancy between `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md` and Table 10A, alongside an institutional policy ruling on technical-cadre appraisal track allocation.

---

## 16. Recommended Phased Execution Sequence & Change Control Invariants

To execute this consolidation safely without disrupting ongoing work or corrupting git history:

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                             RECOMMENDED EXECUTION ROADMAP                                        │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘

  STAGE 1: MENTOR REVIEW & FORMAL DIRECTION (Current Step)
  • Submit this corrected Folder-Preserving Audit Report for user and mentor review.
  • Await explicit authorization before touching any existing file.
                 │
                 ▼
  STAGE 2: IN-FOLDER CANONICAL SPECIFICATION ASSEMBLY
  • In docs/01-requirements/: Assemble `01-SOFTWARE-REQUIREMENTS-SPECIFICATION.md`
    (absorbing 00, 01, 02, 03, 04, 05). Retain Doc 10 as reference register.
  • In docs/02-business-process/: Assemble `01-BUSINESS-PROCESS-AND-WORKFLOW-SPEC.md`
    (absorbing 00, 01, 02, 03, 04, 05, 07). Retain Doc 06 as `02-BUSINESS-RULES-SPEC.md`.
  • In docs/03-functional-requirements/: Assemble `01-FUNCTIONAL-REQUIREMENTS-SPEC.md`
    (absorbing 00, 01, 02, 03, 04).
  • In docs/07-system-architecture/: Retain `ADR-001-REAL-TIME-COMMUNICATION.md`.
  • In docs/08-database/: Assemble `01-DATABASE-DESIGN-AND-SCHEMA-SPEC.md`
    (absorbing 00, 01, 02, 03, 04, 06). Transition Doc 05 to `02-LOGICAL-DATA-DICTIONARY.md`.
                 │
                 ▼
  STAGE 3: AUTOMATED BASELINE INTEGRITY VERIFICATION
  • Execute automated scripts verifying:
    - 104 Atomic Requirements (`REQ-01` to `104`) present.
    - 59 Business Processes (`BP-*`) present.
    - 60 Business Rules (`BR-01` to `60`) present.
    - 11 Official Baseline TBDs (`REQ-TBD-01` to `11`) present with reconciled mappings.
    - 33 Conceptual Entities (`ENT-*`) present.
    - 41 Conceptual Relationships (`REL-*`) present.
    - 344 Logical Attributes (`ATTR-*`) present (61 + 115 + 96 + 72).
    - 152 Functional Requirements (`MOD*-REQ-*`) present.
                 │
                 ▼
  STAGE 4: PRUNE SUPERSEDED FILES WITHIN FOLDERS
  • Safely remove superseded fragmented files after verification passes.
  • Retain all 15 primary folder structures intact.
  • Retain all 10 intentionally empty future folders.
  • Update master navigation links in `README.md`.
```

---

## 17. Non-Destructive Change Log & Invariant Verification

1. **Only the Audit Report Was Modified:**
   - Modified file: [`docs/DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/DOCUMENTATION-CONSOLIDATION-AND-RATIONALIZATION-REPORT.md)
   - `git status` verifies that no other file in the workspace has been modified, moved, renamed, merged, or deleted.
2. **Zero Code or Implementation Artifacts Created:**
   - No SQL, DDL scripts, migration scripts, ORM entities, frontend components, or backend services were generated.
3. **Zero Folders Altered or Pruned:**
   - All 15 primary folders under `docs/` and all folders under `source-requirements/` remain 100% intact.
4. **All Frozen Baselines Intact:**
   - 104 Atomic Requirements (`REQ-01` to `104`): **100% Intact**
   - 59 Business Processes (`BP-*`): **100% Intact**
   - 60 Business Rules (`BR-01` to `60`): **100% Intact**
   - 11 Official Baseline TBDs (`REQ-TBD-01` to `11`): **100% Intact**
   - 33 Conceptual Entities (`ENT-*`): **100% Intact**
   - 41 Conceptual Relationships (`REL-*`): **100% Intact**
   - 344 Logical Attributes (`ATTR-*`): **100% Intact**
   - 152 Functional Requirements (`MOD*-REQ-*`): **100% Intact**
   - Approved Technology Architecture Decisions: **100% Intact**

---

## 18. Verification Summary & Audit Findings

| # | Verification Dimension | Target Artifact / Domain | Audit Status | Audit Findings & Source Evidence |
|:---:|---|---|:---:|---|
| **1** | **Attribute Recalculation** | `docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md` | **VERIFIED** | Command execution confirmed: 344 definition rows, 344 unique IDs, 0 duplicates, 0 sequence gaps across 33 entities. All 103 distinct attribute mentions outside tables resolve to defined attributes. |
| **2** | **Baseline Comparison** | Frozen Data Architecture Baseline | **VERIFIED** | Recalculated 344 matches the frozen baseline of 344 exactly. Historical 355 ($344 + 11$ `ATTR-DEC-*`) and Shared 83 ($72 + 11$ Section 10 mentions) mathematically reconciled. |
| **3** | **Official 11 TBDs Alignment** | Requirements & Database TBD Registers | **DISCREPANCY FOUND** | Mandated 11 TBD register (`TBD-01` to `11`) documented from Doc 09 Table 10A, but conflicts with `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md` numbering (Issue `AUD-06`). Four items (`TBD-03`, `04`, `07`, `09`) have no database attribute decision records in document 05. |
| **4** | **Technical Decisions `[C]`** | `source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md` & `ADR-001` | **VERIFIED** | Redis cache, queue backing store, distributed locking, and Socket.IO adapter verified `[C]`. Redis as inter-module message broker downgraded to `[D]` (Modular Monolith uses in-process domain events per `TDR-01`). BullMQ verified `[D]`. |
| **5** | **Folder Preservation** | Workspace Directory Structure | **VERIFIED** | All 15 folders under `docs/` and 3 subfolders in `source-requirements/` preserved. No `docs/reference/` or folder deletion proposed. |
| **6** | **Consolidation Traceability & Preservation** | Folder-by-Folder Consolidation Matrices | **PARTIALLY VERIFIED** | Source-to-target mapping complete for all 104 REQs, 59 BPs, 60 BRs, 152 FRDs, 11 TBDs, 33 Ents, 41 Rels, 344 Attrs. Zero information loss is planned but cannot be certified as fully verified until canonical files are drafted and verified. |
| **7** | **Database Status Clarification** | Phase 4 Database Roadmap | **VERIFIED** | Confirmed Phase 4 is active (not cancelled). Steps 1–5 (`00`–`06`) are complete conceptual/logical designs. Future physical design (`07`–`12`) is consolidated into Docs 01–02 rather than separate files. |
| **8** | **Preservation of Frozen Baselines** | Enterprise Baseline Registers | **VERIFIED** | All frozen baseline metrics preserved without alteration or fabrication. |

---

## 19. Exact Evidence Locations

1. **Logical Attributes (344 Attributes / 33 Entities):**
   - Detailed specification tables: [`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md), Section 6 (lines 75–233, 61 attrs), Section 7 (lines 235–489, 115 attrs), Section 8 (lines 491–711, 96 attrs), Section 9 (lines 713–864, 72 attrs).
   - Attribute Open Decisions Register (11 rows, `ATTR-DEC-01`..`11`): [`docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md), Section 12 (lines 950–966).
2. **Authoritative 11 Baseline TBDs:**
   - Mandated 11 TBD Register: [`docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md), Section 10 (Table 10A, lines 244–257).
   - Controlled TBD Log (Alternate Numbering): [`docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md), Section 2 (lines 24–39).
   - TBD Inconsistency Audit Report: [`docs/PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/PROJECT-DOCUMENTATION-STRUCTURE-AUDIT.md), Issue `AUD-06` (lines 490–497).
3. **Technology Architecture Baseline & Redis Decisions:**
   - Caching, Queue Backing & Locking: [`source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md), Section 3 (lines 91–92) and `TDR-06` (lines 255–275).
   - Real-Time Communication ADR: [`docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/07-system-architecture/ADR-001-REAL-TIME-COMMUNICATION.md), Section 3 (lines 115–145).
4. **Lab Technician Classification:**
   - Academic Manpower Planning Scope: `source-requirements/Module-II/Module_II_Recruitment_Automation_Requirement_Brief_Rearranged.pdf`, Page 1, Section 1, 1a, 1c, and Workflow A Header.
   - Candidate Feedback Boundary: [`docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md`](file:///d:/Desktop/HR-CHANGE-MANAGEMENT-SYSTEM/docs/01-requirements/10-STAKEHOLDER-DECISION-SHEET.md), `CONF-04` / `CFL-02` (lines 142–180).

---

## 20. Final Readiness Status & Recommendation

```
====================================================================================================
                             FINAL AUDIT READINESS VERDICT
====================================================================================================
 AUDIT PASS STATUS        : PARTIALLY VERIFIED / DISCREPANCIES DOCUMENTED
 WORKSPACE INTEGRITY      : ZERO FILES DELETED, MOVED, RENAMED, OR MERGED (AUDIT-ONLY)
 FOLDER ARCHITECTURE      : 100% PRESERVED (15/15 DOMAIN FOLDERS INTACT)
 FROZEN BASELINE FIDELITY : 100% PRESERVED ACROSS ALL 8 SYSTEM INVARIANTS
 CONSOLIDATION READINESS  : CONDITIONAL UPON MENTOR SIGN-OFF ON TBD HARMONIZATION
====================================================================================================
```

**Recommendation:** Await explicit user and mentor authorization before initiating Stage 2 canonical file assembly. Under no circumstances should automated file merges, deletions, or coding occur prior to written instruction.

---

## 21. Targeted Corrections Change Log & Unresolved Verification Items

### 21.1 Change Log — Targeted Corrections Pass
1. **Official TBD Register Corrected (Section 13.1):** Replaced mismatched titles with the authoritative 11-item sequence (`REQ-TBD-01`: Resignation intake through `REQ-TBD-11`: External Expert access). Documented verified requirement anchors and actual database `ATTR-DEC-*` mappings without inventing false associations.
2. **Discrepancy Reporting Formalized (Section 13.3 & Section 18):** Reported the structural discrepancy between `05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md`, `09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md` Table 10A, and `08-database/05` Section 12 honestly under status **`DISCREPANCY FOUND`**.
3. **Technical-Cadre Appraisal Decoupled (Section 13.2 & Section 14.2):** Preserved technical-cadre appraisal track allocation as a standalone open institutional policy decision (`[E] Open Decision`), removing unsupported mappings to official TBDs.
4. **Command-Verified Attribute Recalculation (Section 14.3):** Distinguished verified command execution output (344 rows, 344 unique IDs, 0 duplicates, 0 sequence gaps across all 33 prefixes, 0 undefined outside mentions) from inferred historical arithmetic (355 and Shared 83).
5. **Technical Decisions Verified & Downgraded (Section 12.1 & 12.2):** Separately verified Redis cache (`[C]`), queue backing store (`[C]`), distributed locking (`[C]`), and Socket.IO adapter (`[C]`). Explicitly downgraded Redis as an inter-module message broker to `[D]` / excluded based on `TDR-01`.
6. **Consolidation Traceability Status Qualified (Section 1.3 & Section 18):** Qualified zero information loss claims to **`PARTIALLY VERIFIED`**, acknowledging that physical preservation can only be certified upon drafting the canonical specifications.

### 21.2 Remaining Unresolved Verification Items
1. **Harmonization of TBD Numbering Scheme:** A formal alignment is required between `docs/01-requirements/05-REQUIREMENTS-TBD-AND-OPEN-DECISIONS.md` and `docs/01-requirements/09-COMBINED-STAKEHOLDER-DELTA-REVIEW.md` Table 10A to standardize whether `REQ-TBD-01` refers to Resignation Intake or ERP Synchronization.
2. **Database Attribute Decisions for Unmapped TBDs:** `REQ-TBD-03` (Legacy service cutover), `REQ-TBD-04` (Supervisor transfer), `REQ-TBD-07` (Non-academic 3-round interview weights), and `REQ-TBD-09` (Group-D 12-month averaging formula) have no assigned `ATTR-DEC-*` entries in `docs/08-database/05-ENTITY-WISE-DETAILED-SPECIFICATION.md`. They must be formally incorporated when the canonical database specification is assembled.
3. **Technical Cadre Appraisal Route:** Formal ruling required from University Leadership (Registrar / HR Head) on whether Lab Technicians, Technical Assistants, and Teaching Associates participate in Group-D, Staff KRA/KPI, or an adapted Faculty appraisal track.
4. **Verification of Consolidated Drafts:** Once authorized, each canonical consolidated document must undergo an automated regex/AST verification pass to certify that all 104 requirements, 59 business processes, 60 business rules, 152 functional requirements, and 344 attributes are present verbatim.

---

*End of Document — Documentation Necessity Audit, Consolidation & Rationalization Report (Revision 3 — Folder-Preserving Plan).*
