---
name: Academic Operations & Change Orchestration
colors:
  surface: '#f9f9ff'
  surface-dim: '#cfdaf2'
  surface-bright: '#f9f9ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f0f3ff'
  surface-container: '#e7eeff'
  surface-container-high: '#dee8ff'
  surface-container-highest: '#d8e3fb'
  on-surface: '#111c2d'
  on-surface-variant: '#464554'
  inverse-surface: '#263143'
  inverse-on-surface: '#ecf1ff'
  outline: '#777586'
  outline-variant: '#c7c4d7'
  surface-tint: '#5148d7'
  primary: '#2a14b4'
  on-primary: '#ffffff'
  primary-container: '#4338ca'
  on-primary-container: '#c1beff'
  inverse-primary: '#c3c0ff'
  secondary: '#505f76'
  on-secondary: '#ffffff'
  secondary-container: '#d0e1fb'
  on-secondary-container: '#54647a'
  tertiary: '#4700ab'
  on-tertiary: '#ffffff'
  tertiary-container: '#6029c9'
  on-tertiary-container: '#cfbaff'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#e3dfff'
  primary-fixed-dim: '#c3c0ff'
  on-primary-fixed: '#100069'
  on-primary-fixed-variant: '#372abf'
  secondary-fixed: '#d3e4fe'
  secondary-fixed-dim: '#b7c8e1'
  on-secondary-fixed: '#0b1c30'
  on-secondary-fixed-variant: '#38485d'
  tertiary-fixed: '#e9ddff'
  tertiary-fixed-dim: '#d0bcff'
  on-tertiary-fixed: '#23005c'
  on-tertiary-fixed-variant: '#5516be'
  background: '#f9f9ff'
  on-background: '#111c2d'
  surface-variant: '#d8e3fb'
typography:
  headline-xl:
    fontFamily: Inter
    fontSize: 30px
    fontWeight: '700'
    lineHeight: 38px
    letterSpacing: -0.02em
  headline-xl-mobile:
    fontFamily: Inter
    fontSize: 24px
    fontWeight: '700'
    lineHeight: 32px
    letterSpacing: -0.015em
  headline-lg:
    fontFamily: Inter
    fontSize: 22px
    fontWeight: '600'
    lineHeight: 28px
    letterSpacing: -0.015em
  headline-md:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
    letterSpacing: -0.01em
  headline-sm:
    fontFamily: Inter
    fontSize: 15px
    fontWeight: '600'
    lineHeight: 20px
    letterSpacing: -0.005em
  body-lg:
    fontFamily: Inter
    fontSize: 15px
    fontWeight: '400'
    lineHeight: 22px
  body-md:
    fontFamily: Inter
    fontSize: 13px
    fontWeight: '400'
    lineHeight: 18px
  body-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  label-md:
    fontFamily: Inter
    fontSize: 13px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0em
  label-sm:
    fontFamily: Inter
    fontSize: 11px
    fontWeight: '600'
    lineHeight: 14px
    letterSpacing: 0.03em
  code-sm:
    fontFamily: JetBrains Mono
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
rounded:
  sm: 0.125rem
  DEFAULT: 0.25rem
  md: 0.375rem
  lg: 0.5rem
  xl: 0.75rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-desktop: 1.5rem
  margin: 1rem
  margin-desktop: 2rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 0.75rem
  space-lg: 1.25rem
  space-xl: 2rem
---

## Brand & Style

This design system serves complex higher education institutions undergoing faculty restructuring, tenure reviews, position reclassifications, and campus-wide HR automation. The interface balances academic gravitas with the streamlined efficiency of world-class enterprise SaaS.

### Personality & Tone
- **Authoritative yet Unobtrusive:** The system prioritizes high-stakes institutional records, compliance trails, and personnel decisions without visual noise.
- **Clarity under Density:** Information architecture handles multidimensional academic hierarchies (e.g., provosts, deans, department chairs, adjunct pools) with structural calm.
- **Precision Engineered:** Drawing inspiration from tools like Linear and Stripe, the aesthetic emphasizes clean division, micro-interactions, explicit feedback states, and strict typographic rhythm.

### Visual Language
The design system operates on a **Corporate Modern Minimalist** foundation: crisp 1px structural framing, neutral base surfaces, subtle depth through low-contrast ambient shadows, and purposeful status accents. Decorative styling is eliminated in favor of functional clarity and predictable interactive targets.

## Colors

The palette establishes an institutional, trustworthy atmosphere while supporting critical operational workflows through distinct semantic tokens.

### Core Palette
- **Primary (`#4338CA` - Indigo 700):** Represents action, primary focal points, key triggers, and systemic progress markers.
- **Secondary (`#64748B` - Slate 500):** Governs structural metadata, secondary icons, inactive states, and non-actionable subtexts.
- **Tertiary (`#8B5CF6` - Purple 500):** Specifically allocated for academic senate workflows, tenure evaluations, sabbatical petitions, and dossier assessments.
- **Neutral Base (`#1E293B` - Slate 800):** The primary typographic ink, anchoring high-contrast readability against crisp backgrounds.

### Background & Surface Hierarchy
- **Canvas Base:** `#F8FAFC` (Slate 50) creates an anti-glare, calm work surface.
- **Surface Elevation 0 (Card/Panel):** `#FFFFFF` (Pure White) defines content islands, form blocks, and data grids.
- **Surface Elevation 1 (Muted/Inset):** `#F1F5F9` (Slate 100) handles table headers, disabled form wells, and sub-navigation tracks.
- **Structural Border:** `#E2E8F0` (Slate 200) strictly delimits modular boundaries with continuous 1px integrity.

### Semantic Status Tokens
- **Approved / Completed:** Ink `#059669`, Fill `#ECFDF5`, Border `#A7F3D0`
- **Pending / In-Progress:** Ink `#D97706`, Fill `#FFFBEB`, Border `#FDE68A`
- **Overdue / Critical / Rejected:** Ink `#DC2626`, Fill `#FEF2F2`, Border `#FECACA`
- **Academic Review / Governance:** Ink `#7C3AED`, Fill `#F5F3FF`, Border `#DDD6FE`

## Typography

The type system relies on **Inter** across all interface layers, leveraging tabular figures for audit tables, currency, tenure clocks, and position budget metrics. **JetBrains Mono** is reserved exclusively for audit hashes, employee IDs, automated event triggers, and system rule logic.

### Rules of Usage
- **Dense Data Display:** Data tables and metric rollups rely on `body-md` (13px) and `body-sm` (12px) to maximize screen real estate while retaining legibility through open counter spaces.
- **Section Headers & Metrics:** Headings utilize tight negative letter spacing (-0.01em to -0.02em) to maintain crisp visual density similar to Linear and Stripe dashboards.
- **Metadata Badges & Micro-Labels:** `label-sm` utilizes uppercase rendering with `0.03em` letter spacing for categorization badges, compliance tags, and role pills.

## Layout & Spacing

The system implements a fluid 12-column responsive layout engine optimized for dense operational views, structured review panels, and side-by-side workflow validations.

### Grid & Breakpoints
- **Desktop (>= 1280px):** 12 columns with `24px` (`gutter-desktop`) gutters and `32px` (`margin-desktop`) exterior margin. Supports dual-drawer layouts (e.g., change request dossier on the left, live audit trail and approval stepper on the right).
- **Tablet (768px - 1279px):** 8 columns with `16px` gutters and `24px` margins. Secondary workflow drawers collapse into floating modal panels or tabbed views.
- **Mobile (< 768px):** 4 columns with `16px` gutters and `16px` margins. Action bars become sticky footers; complex matrix approvals convert to sequential single-touch cards.

### Layout Philosophy
- Spacing follows an absolute 4px/8px rhythm. Component internal padding leans toward compact vertical dimensions (`space-xs`, `space-sm`) and generous horizontal cushions (`space-md`, `space-lg`) to preserve information scanning speed across dense enterprise forms.

## Elevation & Depth

This system avoids heavy drop shadows, relying on tonal separation and razor-thin borders to convey structure, with ambient shadows reserved strictly for transient overlays.

### Elevation Levels
- **Level 0 (Flat / Canvas):** Applied to the base canvas (`#F8FAFC`). No shadow. Separated from content areas using 1px continuous borders (`#E2E8F0`).
- **Level 1 (Structural Cards / Data Grids):** Applied to standard modular containers. Background `#FFFFFF`, border `1px solid #E2E8F0`, and an ultra-subtle ambient shadow: `0 1px 2px 0 rgba(15, 23, 42, 0.04)`.
- **Level 2 (Popovers, Select Menus, Tooltips):** Applied to interactive dropdowns and status overlays. Border `1px solid #E2E8F0`, shadow: `0 4px 6px -1px rgba(15, 23, 42, 0.06), 0 2px 4px -2px rgba(15, 23, 42, 0.04)`.
- **Level 3 (Modals / Stage Change Drawers):** Applied to major interruption layers (e.g., reclassification approvals, academic override prompts). Shadow: `0 20px 25px -5px rgba(15, 23, 42, 0.08), 0 8px 10px -6px rgba(15, 23, 42, 0.04)`. Accompanied by a muted backdrop blur (`backdrop-filter: blur(4px); background-color: rgba(15, 23, 42, 0.3)`).

## Shapes

The design system employs a **Soft (Level 1)** geometric standard. This geometry produces a precise, software-instrument feel that keeps dense tables and nested form structures orderly without visual rounding artifacts.

### Radius Specifications
- **Base Components (Inputs, Buttons, Badges, Table Rows):** `0.25rem` (4px). Provides clean, modern boundaries that fit into compact table cells and tight grid lines.
- **Large Panels (Cards, Drawers, Summary Modules):** `rounded-lg` at `0.5rem` (8px). Softens larger surface divisions while maintaining a professional enterprise baseline.
- **Modals & Flyouts:** `rounded-xl` at `0.75rem` (12px). Delivers subtle framing for overlay dialogs without breaking visual cohesion.
- **Pill Indicators (Audit Status, Role Tags):** Full pill rounding (`9999px`) is reserved exclusively for inline status indicators and identity tokens.

## Components

### Buttons
- **Primary:** Solid `#4338CA` background, `#FFFFFF` text, `4px` radius. Hover: `#3730A3`. Active: `#312E81`. Focus: `0 0 0 2px #FFFFFF, 0 0 0 4px #818CF8`. Height: `32px` for data density; `38px` for primary submission flows.
- **Secondary:** Surface `#FFFFFF`, border `1px solid #E2E8F0`, text `#1E293B`. Hover: `#F8FAFC`, border `#CBD5E1`.
- **Destructive:** Surface `#FEF2F2`, border `1px solid #FECACA`, text `#DC2626`. Hover: `#FEE2E2`.

### Form Controls & Inputs
- **Text & Select Inputs:** Height `32px` (compact) or `36px` (standard), background `#FFFFFF`, border `1px solid #CBD5E1`, text `13px`, font `#1E293B`. Placeholder: `#94A3B8`. Focus: border `#4338CA`, box-shadow `0 0 0 1px #4338CA`.
- **Validation State:** Red border (`#EF4444`) with an inline micro-caption (`body-sm`) coupled with a distinct error icon.

### Status Badges & Audit Tags
- **Structure:** Height `20px`, padding `0 6px`, radius `9999px` (pill), font `label-sm` (11px semi-bold).
- **Variants:**
  - *Completed/Approved:* `#ECFDF5` background, `#059669` text, `1px solid #A7F3D0`.
  - *In-Review/Pending:* `#FFFBEB` background, `#D97706` text, `1px solid #FDE68A`.
  - *Critical/Rejected:* `#FEF2F2` background, `#DC2626` text, `1px solid #FECACA`.
  - *Governance/Academic:* `#F5F3FF` background, `#7C3AED` text, `1px solid #DDD6FE`.

### Data Cards & KPI Metrics
- **Card Container:** `#FFFFFF` background, `1px solid #E2E8F0`, padding `16px`, radius `8px`.
- **Metric Modules:** Label in `label-sm` (`#64748B`, uppercase tracking), raw metric value in `headline-lg` (`#1E293B`, tabular lining numbers), delta pill aligned top-right.

### Approval Stepper (Workflow Automation)
- Connected linear nodes with a `2px` tracking line (`#E2E8F0` pending, `#4338CA` completed).
- Step indicator size: `24px` circle. Completed steps show a mini checkmark icon in a solid indigo fill; the active step presents a white circle with a `2px` ring in `#4338CA`; pending steps show a `#F1F5F9` neutral ring.

### Role Badges
- Boxed label (`4px` radius), padding `2px 6px`, font `code-sm` (11px).
- Differentiates operational capacity: `DEAN`, `PROVOST`, `HR_SUPERVISOR`, `DEPARTMENT_CHAIR`. Background `#F1F5F9`, border `1px solid #E2E8F0`, text `#475569`.