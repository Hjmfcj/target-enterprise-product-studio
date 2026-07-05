# Requirements Traceability Matrix — MTN Sudan Travel Mission Management System

## Purpose
Maps Business Objective → Requirement → Epic → User Story → Source → Status, per [05_Templates/RTM_Template.md](../../../05_Templates/RTM_Template.md). Reproduces and re-verifies the RTM originally compiled in `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 7 against this repository's FRD/Backlog structure.

## Scope
Covers all 13 original Epics plus the 2 new Epics identified from the second-session transcript.

## Intended Usage
Update the Status column as clarification items are resolved and stories move from BLOCKED/NEEDS CLARIFICATION to READY.

| RTM ID | Requirement / Business Driver | Epic | Sample User Story | FR Reference | Source | Status |
|---|---|---|---|---|---|---|
| RTM-01 | Automate mission creation and submission | EP-03 Mission Creation | Create New Mission; Submit Mission; Validate Fields | FR-01, FR-02, FR-03 | MoM §1; `Travel_System_Requirements.docx` | READY |
| RTM-02 | Enforce multi-level approval workflow | EP-04 Approval Workflow | LM Approve; DM Approve; HR Approve (International) | FR-04, FR-05, FR-06 | MoM Confirmed Workflow; Second-session transcript | PARTIAL — HR step position NEEDS CLARIFICATION (BQ-01) |
| RTM-03 | Calculate and validate travel costs | EP-05 Travel Review + EP-NEW-02 Employee Grading | Enter Per Diem; Grade-Based Rate; Submit to GL | FR-07, FR-08, FR-09 | MoM §4, §6; Second-session transcript §48 | BLOCKED — formulas and grade rates unconfirmed |
| RTM-04 | GL financial validation before Treasury payment | EP-06 GL Review | Review Costs; Submit to Treasury | FR-10 | MoM §7 | READY |
| RTM-05 | Process mission payment via Treasury | EP-07 Treasury | Confirm Payment; Mark Mission Active | FR-11 | MoM §8 | READY |
| RTM-06 | Support mission extension with full re-approval | EP-08 Mission Extension | Request Extension; Recalculate Costs; Full Approval Cycle | FR-12, FR-13, FR-14 | MoM §10 | NEEDS CLARIFICATION — cost formula and HR sub-step |
| RTM-07 | Mission closure and financial settlement | EP-09 Mission Closure + EP-10 Settlement | Close Mission; Process Settlement; Debit/Credit | FR-15, FR-17, FR-18 | MoM §11 | READY (Closure) / BLOCKED (Cancellation, FR-16) |
| RTM-08 | Role-based access control via Microsoft 365 | EP-13 Security & Roles | Restrict by Role; M365 Provisioning | FR-23 | MoM §5, §13; Second-session transcript | UPDATED — M365 provisioning scope confirmed |
| RTM-09 | Email notifications at each workflow stage | EP-12 Notifications | Notify LM/DM/Travel/GL/Treasury/HR/Employee | FR-22 | MoM §9; Second-session transcript | UPDATED — HR notification added, content MISSING |
| RTM-10 | HR governance over International missions | EP-NEW-01 HR Approval | HR Approve International; HR Notify National | FR-06 | Second-session transcript §4:06 | NEEDS CLARIFICATION |
| RTM-11 | Grade-linked accommodation allowances | EP-NEW-02 Employee Grading | Auto-apply grade rate; display in Travel Review | FR-09 | Second-session transcript §48:55 | BLOCKED |
| RTM-12 | Reporting on mission history and financial balances | EP-11 Reporting | View Employee History; View Debit/Credit Report | FR-19, FR-20 | `Travel_System_Requirements.docx` Screen Inventory | READY (existing reports) / BLOCKED (HR reports, FR-21) |
| RTM-13 | Dashboard visibility of mission status and pending actions | EP-01 Dashboard | View Dashboard KPIs; View Pending Approvals/Payments | — | MoM §9; `Travel_System_Requirements.docx` | READY |
| RTM-14 | Mission and employee-level visibility/search | EP-02 Mission Management | View Mission List; View Mission Details; My Missions | — | `Travel_System_Requirements.docx`; Backlog | READY |

## Future Expansion
Status values will be updated as MTN Sudan responds to the [Clarification Register](Clarification_Register.md).
