# Screen Inventory — MTN Sudan Travel Mission Management System

## Purpose
Documents every screen with evidence, per [02_Standards/UI_UX.md](../../../02_Standards/UI_UX.md). Base inventory from `Travel_System_Requirements.docx`; detail elaborated from `MTN_Travel_System_Figma_Spec.md` where available.

## Scope
Business/functional screen definition only. Visual mockups and exports live in [Assets/](Assets/README.md).

## Intended Usage
Cross-reference the Source Reference column against [../02_Requirements/FRD.md](../02_Requirements/FRD.md) and [../04_Backlog/User_Stories.md](../04_Backlog/User_Stories.md).

| Screen Name | Purpose | Primary User | Key Fields/Actions (where documented) | Permissions | Source Reference |
|---|---|---|---|---|---|
| Dashboard | View mission statistics and pending actions | All Users | KPI cards (Open/Active/Pending Settlement counts); Pending Approvals widget; Pending Payments widget; role-based visibility. **No trend/delta indicators** (explicitly removed, Figma Spec Phase 1 Issue #9) | Visible to all authorized users; content scoped by role | `Travel_System_Requirements.docx`; `MTN_Travel_System_Figma_Spec.md` Phase 1 |
| Mission List | View and search all missions | Assigned Person (and others per role) | Search, Filter by Status/Type/Employee/Date Range, Sort, Export | Role-scoped visibility — exact scoping rule NOT DISCUSSED (e.g. whether Assigned Persons see only their own missions here or an org-wide list) — **CLARIFICATION REQUIRED** | `Travel_System_Requirements.docx`; source-of-truth v3 EP-02 |
| Create Mission | Create a new mission request | Assigned Person | Mission Type, Mission Category, Destination, Assigned Person, Employee Name, Start/End Date, Mission Purpose, Attachments, Save Draft, Submit | Assigned Person role | `Travel_System_Requirements.docx`; source-of-truth v3 EP-03; MoM §1–§4 |
| Mission Details | View mission information and workflow progress | All Users | Cost Breakdown, Approval History, Settlement History, Attachments | Role-scoped view; action buttons vary by role (Figma Spec: "Topbar CTA and table action columns are variant-driven by role property") | `Travel_System_Requirements.docx`; `MTN_Travel_System_Figma_Spec.md` |
| My Missions | Track own missions | Assigned Person | Search, Filter, Track Status | Assigned Person role | `Travel_System_Requirements.docx`; explicitly flagged in Figma Spec Phase 1 Issue #8 as missing from the original HTML design and required to be added |
| Pending Approvals | Approve or reject mission requests | Line Manager, Division Manager (and, pending clarification, HR) | View mission details, Approve (optional note), Reject (mandatory note) | Role-restricted — LM sees only LM-stage items; DM sees only DM-stage items | `Travel_System_Requirements.docx`; MoM Confirmed Workflow |
| Travel Cost Review | Enter and review travel-related costs | Travel Team | Enter Per Diem, Accommodation, Other Expenses; Modify; Reject; Submit to GL Review | Travel Team role | `Travel_System_Requirements.docx`; source-of-truth v3 EP-05 (button corrected to "Submit to GL Review") |
| GL Review | Financial validation | GL Team | Review Costs, Modify Financial Values, Reject, Submit to Treasury | GL Team role | Source-of-truth v3 EP-06 — **not present as a distinct named screen in `Travel_System_Requirements.docx` Screen Inventory; added based on validated workflow** |
| Payments | Review approved amounts and confirm payment | Treasury | Enter Payment Reference, Payment Date, Notes, Confirm Payment | Treasury role — no reject action (BR-05) | `Travel_System_Requirements.docx`; MoM §8 |
| Mission Extensions | Request and manage mission extensions | Assigned Person | New End Date, Extension Reason, recalculated Per Diem/Accommodation, "Extended By" field | Assigned Person role | `Travel_System_Requirements.docx`; MoM §10 |
| Mission Closure | Close mission and upload supporting documents | Assigned Person | Upload Closure Documents, Submit Closure | Assigned Person role | `Travel_System_Requirements.docx`; MoM §11 |
| Settlements | Calculate and process mission settlement | Finance | Planned vs. Actual comparison, Balance calculation, Settlement Reference, Process Settlement | Finance role | `Travel_System_Requirements.docx`; MoM §11 |
| Employee Mission History Report | View mission history by employee | Finance | Employee/date/type/status filters, Export | Finance role | `Travel_System_Requirements.docx` |
| Debit/Credit Report | View employee balances and settlement results | Finance | Date/employee filters, summary KPIs, Export | Finance role | `Travel_System_Requirements.docx` |
| HR Pending Approvals (International) | Approve/reject International missions | HR Team | View mission details, Approve, Reject, Add HR Notes | HR Team role — National missions must NOT appear here (notification only) | Second-session transcript §4:06–§11:21; source-of-truth v3 EP-NEW-01 — **NEEDS CLARIFICATION**: workflow placement (BQ-01) |
| HR Reports | MISSING INFORMATION | HR Team (assumed) | MISSING INFORMATION | MISSING INFORMATION | MoM Open Items 4–5 — pending HR workshop |
| Destination Pricing Configuration | MISSING INFORMATION — screen existence implied by need for configurable destination-based pricing, but no screen definition, owner role, or fields are documented | MISSING INFORMATION | MISSING INFORMATION | MISSING INFORMATION | Source-of-truth v3 GAP-04 |

## Explicitly Excluded Screens (removed from prior UX prototype — do not recreate)
Per `MTN_Travel_System_Figma_Spec.md` Phase 1 audit:
- "Archived (Rejected)" screen — no "Archived" status exists (Figma Spec Phase 1 Issue #1)
- Any Administration/Configuration module screen (beyond the still-undefined Destination Pricing Configuration item above, which remains open, not excluded)
- Any Audit Log module screen

## Future Expansion
Will be updated once destination pricing configuration, HR reports, and cancellation-related screens are clarified.
