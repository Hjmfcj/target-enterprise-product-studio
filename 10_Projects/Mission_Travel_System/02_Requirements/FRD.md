# Functional Requirements Document — MTN Sudan Travel Mission Management System

## Purpose
Itemized functional requirements register, per [05_Templates/FRD_Template.md](../../../05_Templates/FRD_Template.md) and [02_Standards/BRD.md](../../../02_Standards/BRD.md) (Functional Requirements section).

## Scope
Decomposes the [BRD](BRD.md) Functional Requirements section (§9) and the validated Product Backlog into discrete, traceable functional requirement statements.

## Intended Usage
Cross-reference against [../04_Backlog/User_Stories.md](../04_Backlog/User_Stories.md) via the Linked User Stories column, and against [RTM.md](RTM.md).

| FR ID | Description | Source Reference | Business Rules | Validation Rules | Linked User Stories / Epic |
|---|---|---|---|---|---|
| FR-01 | Assigned Person can create a new Mission Request, selecting Mission Type (National/International), Mission Category (Training/Conference/Job Mission), Destination, Assigned Person, Employee Name, Start Date, End Date, and Mission Purpose, and can upload supporting documents | MoM §1–§2; source-of-truth v3 EP-03 | BR-01, BR-02, BR-03, BR-04 | Mandatory fields must be validated; End Date must not precede Start Date; attachments validated | EP-03 |
| FR-02 | System auto-determines mission currency from Mission Type (National → SDG, International → USD) | MoM §3 | BR-02, BR-03 | N/A — system-determined, not user-editable | EP-03 |
| FR-03 | Assigned Person can save a Mission Request as Draft prior to submission | `MTN_Travel_Product_Backlog_TFS.docx` EPIC 3 | — | Draft missions do not enter the approval workflow | EP-03 |
| FR-04 | Line Manager can view, approve (with optional note), or reject (with mandatory note) a pending Mission Request | MoM Confirmed Workflow; source-of-truth v3 US-EP04-LM-001 | — | Rejection requires a reason; system must prevent rejection without one | EP-04 |
| FR-05 | Division Manager / GM can view, approve, or reject a Mission Request that has passed Line Manager approval | MoM Confirmed Workflow | — | Same as FR-04, applied at DM stage | EP-04 |
| FR-06 | System routes International missions to HR for Approval, and sends an informational email notification to HR for National missions, after Division Manager approval | Second-session transcript §4:06–§11:21, §9:55–§11:03 | — | **NEEDS CLARIFICATION** — exact workflow position (before/after DM) unconfirmed (BQ-01) | EP-NEW-01 |
| FR-07 | Travel Team can view pending Travel Reviews, enter Per Diem, Accommodation Cost, and Other Expenses, modify cost values, reject, and submit to GL Review | MoM §6; source-of-truth v3 (corrects "Submit to Treasury" → "Submit to GL") | BR-Ext-01 (proposed) | Recalculation must occur if values are modified | EP-05 |
| FR-08 | System calculates Mission Total cost and displays a cost summary in Travel Review | MoM §4 | BR-Ext-01 (proposed) | **BLOCKED** — formula not confirmed by MTN Sudan (BQ-03, BQ-04) | EP-05 |
| FR-09 | System applies employee-grade-linked Accommodation rate | Second-session transcript §48:55–§50:36 | BR-Grade-01 (pending) | **BLOCKED** — grade levels/rates MISSING INFORMATION (BQ-02) | EP-NEW-02 |
| FR-10 | GL Team can view pending GL Requests, review/modify financial values, reject, and submit to Treasury | MoM §7 | — | GL Review must occur before Treasury (BR sequencing) | EP-06 |
| FR-11 | Treasury can view pending payments, enter payment reference and date, add notes, and confirm payment; confirming payment sets mission status to Mission Active | MoM §8 | BR-05 | Treasury has no reject action | EP-07 |
| FR-12 | Assigned Person can request a Mission Extension with a new end date and reason; system recalculates Per Diem and Accommodation for the extension period and records the submitting user and timestamp ("Extended By") | MoM §10 | BR-Ext-01 (proposed) | New End Date must be later than current End Date; **BLOCKED on cost formula** (BQ-03, BQ-04) | EP-08 |
| FR-13 | Mission Extension requests pass through the same approval cycle as the original mission (LM → DM → HR if International → Travel → GL → Treasury) | MoM §10: "same workflow and approval cycle" | — | **NEEDS CLARIFICATION** whether HR sub-step follows the same International/National distinction on extension (BQ-09) | EP-08 |
| FR-14 | Long-term (monthly) missions must be closed and a new mission created for each subsequent month; the system does not auto-extend | `Travel_System_Requirements.docx` Business Controls | BR-06 | — | EP-08 |
| FR-15 | Assigned Person can close a Mission, uploading closure documents | MoM §11; `Travel_System_Requirements.docx` | — | — | EP-09 |
| FR-16 | Assigned Person can cancel a Mission prior to departure | Second-session transcript §52:24 | — | **MISSING INFORMATION** — cancellation rules, eligible statuses, and impact on paid advances not defined (BQ-06) | EP-09 |
| FR-17 | Finance can process Settlement: enter actual costs, compare planned vs. actual, calculate balance, add settlement reference, and complete the mission (status → Completed) | MoM §11; source-of-truth v3 EP-10 | — | — | EP-10 |
| FR-18 | System identifies whether settlement results in an employee debit or credit and displays the result | MoM §11 | — | — | EP-10 |
| FR-19 | Finance can view/search/filter/export Employee Mission History | `Travel_System_Requirements.docx` Screen Inventory | — | — | EP-11 |
| FR-20 | Finance can view/search/filter/export the Debit/Credit Report | `Travel_System_Requirements.docx` Screen Inventory | — | — | EP-11 |
| FR-21 | HR reporting requirements | Second-session transcript, MoM Open Items 4–5 | — | **MISSING INFORMATION** — pending HR workshop (BQ-08) | EP-11 |
| FR-22 | System sends email notifications to Line Manager, Division Manager, Travel Team, GL Team, Treasury Team, Employee (post-payment and on rejection), and HR (per FR-06), at the corresponding workflow stage | MoM §9 | BR-07 | — | EP-12 |
| FR-23 | System restricts screens, actions, and menus by role, and recognizes Microsoft 365 accounts automatically without a manual user-management screen | Second-session transcript §7:59–§8:57; MoM §13 | BR-Sec-01 | — | EP-13 |

## Future Expansion
Will be extended once MTN Sudan resolves the BLOCKED / NEEDS CLARIFICATION items above, converting proposed rules into confirmed Business Rules.
