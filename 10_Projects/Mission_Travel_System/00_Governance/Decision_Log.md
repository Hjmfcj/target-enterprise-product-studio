# Decision Log — MTN Sudan Travel Mission Management System

## Purpose
Running, append-only record of formal decisions, per [05_Templates](../../../05_Templates/README.md) governance standard.

## Scope
Decisions traceable to [MOM Log](MOM_Log.md) entries and the approved source-of-truth document.

## Intended Usage
Add a new row per decision; never delete — supersede instead.

| Decision ID | Date | Decision Description | Context/Rationale | Decided By | Related MOM Entry | Impact | Status |
|---|---|---|---|---|---|---|---|
| D-01 | Session 1 (early June 2026) | End-to-end workflow confirmed: Mission Request → LM Approval → DM/GM Approval → Travel Review → GL Review → Treasury Payment → Mission Active → Mission Extension (Optional) → Mission Closure → Finance Settlement → Mission Completed | Reviewed and agreed in workshop | MTN Sudan + Target Team | MOM Log Entry 1 | Scope / Workflow / BRD §7-8 | Active |
| D-02 | Session 1 | System must distinguish Assigned Person (request creator) from Employee Name (traveler); Employee Name field added to Mission Request form | Raised as a gap in existing form | MTN Sudan + Target Team | MOM Log Entry 1 | Design (Screen: Create Mission) | Active |
| D-03 | Session 1 | Mission Categories confirmed as: Training, Conference, Job Mission | Discussion and agreement | MTN Sudan + Target Team | MOM Log Entry 1 | Requirements (BR-04) | Active |
| D-04 | Session 1 | Mission Types confirmed as National / International, with currency auto-determined: National → SDG, International → USD | Discussion and agreement | MTN Sudan + Target Team | MOM Log Entry 1 | Requirements (BR-02, BR-03) | Active |
| D-05 | Session 1 | Per Diem calculated on total mission days; Accommodation calculated on total accommodation nights (exact formula and destination pricing matrix deferred to MTN Sudan) | Discussion and agreement — formula itself NOT finalized | MTN Sudan + Target Team | MOM Log Entry 1 | Requirements — Travel Cost Review (BLOCKED pending formula) | Active — Partially Open |
| D-06 | Session 1 | GL Review must occur before Treasury Payment (corrects any design showing direct Travel Review → Treasury) | Explicit workflow correction | MTN Sudan + Target Team | MOM Log Entry 1 | Design — corrects CF-01/CF-02 in source-of-truth conflict analysis | Active |
| D-07 | Session 1 | Treasury performs payment processing only — no approve/reject action at Treasury stage | Explicit role clarification | MTN Sudan + Target Team | MOM Log Entry 1 | Requirements (BR-05) | Active |
| D-08 | Session 1 | Mission Extension must recalculate Per Diem and Accommodation, follow the same approval cycle as the original mission, and record who performed the extension ("Extended By") | Discussion and agreement | MTN Sudan + Target Team | MOM Log Entry 1 | Requirements — EP-08 | Active |
| D-09 | Session 1 | Solution will be implemented directly on Microsoft 365 / SharePoint | MTN Sudan confirmed platform preference to align with existing systems | MTN Sudan | MOM Log Entry 1 | Solution Architecture | Active |
| D-10 | 28 Jun 2026 | Access control will be group-based: a dedicated portal group is created and members assigned manually; no open sign-in access | Team discussion on SharePoint permissions approach | Target delivery team | MOM Log Entry 3 | Design / Security (EP-13) | Active |
| D-11 | 28 Jun 2026 | Mostafa will attempt the Lovable-to-Figma conversion using his own account if Abdullah is unavailable | Workaround for Figma subscription dependency | Target delivery team | MOM Log Entry 3 | Design workflow (internal only — not a business requirement) | Active |
| D-12 | 28 Jun 2026 | Asmaa will share ready MTN brand assets (logo + colors) with the team immediately | Team coordination | Target delivery team | MOM Log Entry 3 | Design (branding assets) | Active |
| D-13 | 29 Jun 2026 | Sprint 1 scope confirmed: Mission Log List, Create Mission, My Missions, Mission Extension | Confirmed in daily scrum | Target delivery team | MOM Log Entry 4 | Backlog / Sprint 1 plan | Active |
| D-14 | 29 Jun 2026 (email) | Per Diem / Accommodation cost logic will be implemented per the standard formula (Per Diem = Number of Days × Rate per Destination; Accommodation = Number of Nights × Rate per Destination) using **representative sample data** for destinations/rates until MTN Sudan provides the approved rate matrix — "zero rework on the logic" once real rates are supplied | Target proposed this approach unilaterally in `629_email_request_enviroment_from_muhanad_and_alignment_on_phase_1.pdf` to avoid blocking Milestone 1; **no MTN Sudan written confirmation of this formula was found in any uploaded artifact** | Target Integrated Systems (proposed; MTN Sudan acceptance **NOT CONFIRMED** in uploaded evidence) | Not a MOM Log entry — sourced from client email | Requirements — Travel Cost Review; supersedes/extends open item from D-05 | **Proposed — Awaiting MTN Sudan confirmation** |

## Future Expansion
Will be refined as further formal decisions are recorded, particularly MTN Sudan's response to D-14 and the HR workflow placement question (see [Clarification Register](../02_Requirements/Clarification_Register.md) BQ-01).
