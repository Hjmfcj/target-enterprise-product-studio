# Product Backlog — MTN Sudan Travel Mission Management System

## Purpose
Azure DevOps / TFS-ready backlog, per [02_Standards/Azure_DevOps.md](../../../02_Standards/Azure_DevOps.md). Reproduces and supersedes `MTN_Travel_Product_Backlog_TFS.docx`, incorporating all additions and corrections from `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 3. Items marked **[NEW]** were added from the second-session transcript; **[UPDATED]** items were corrected during the backlog analysis.

## Scope
Epics EP-01 through EP-13 (original) plus EP-NEW-01, EP-NEW-02 (added). No story is included without a source reference.

## Intended Usage
Import directly into Azure DevOps / TFS using the Epic → Feature → User Story → Task hierarchy. Stories with Status = BLOCKED or NEEDS CLARIFICATION cannot be estimated or scheduled until clarification items are resolved.

---

## EPIC EP-01 — Dashboard
**Source:** MoM §9; `Travel_System_Requirements.docx`; `MTN_Travel_Product_Backlog_TFS.docx`
**Status:** READY

### Feature: Dashboard KPIs
| User Story | Priority | Status | Source |
|---|---|---|---|
| As an authorized user, I want to view Mission KPIs on the Dashboard so that I have an at-a-glance overview of mission activity | HIGH | READY | MoM §9 |
| As an authorized user, I want to view the count of Open Missions on the Dashboard | HIGH | READY | Backlog |
| As an authorized user, I want to view the count of Active Missions on the Dashboard | HIGH | READY | Backlog |
| As an authorized user, I want to view the count of Missions Pending Settlement on the Dashboard | HIGH | READY | Backlog |

### Feature: Pending Approvals Widget
| User Story | Priority | Status |
|---|---|---|
| As an authorized user, I want to see my Pending Approvals on the Dashboard so I can act without navigating away | HIGH | READY |
| As an authorized user, I want to navigate from a Dashboard widget directly to the Mission Detail | HIGH | READY |

### Feature: Pending Payments Widget
| User Story | Priority | Status |
|---|---|---|
| As a Treasury user, I want to see Pending Payments on the Dashboard so I can act immediately | HIGH | READY |

---

## EPIC EP-02 — Mission Management
**Source:** `Travel_System_Requirements.docx`; MoM §1; Backlog
**Status:** READY

### Feature: Mission List
| User Story | Priority | Status |
|---|---|---|
| As an authorized user, I want to view the Mission List so that I can see all missions I have access to | HIGH | READY |
| As an authorized user, I want to search Missions by keyword | HIGH | READY |
| As an authorized user, I want to filter Missions by Status | HIGH | READY |
| As an authorized user, I want to filter Missions by Mission Type (National/International) | HIGH | READY |
| As an authorized user, I want to filter Missions by Employee name | HIGH | READY |
| As an authorized user, I want to filter Missions by Date Range | HIGH | READY |
| As an authorized user, I want to sort the Mission list | MEDIUM | READY |
| As an authorized user, I want to export the Mission list | MEDIUM | READY |

### Feature: Mission Details
| User Story | Priority | Status |
|---|---|---|
| As an authorized user, I want to view full Mission Details so I can see all information about a mission | HIGH | READY |
| As an authorized user, I want to view the Cost Breakdown for a mission | HIGH | READY |
| As an authorized user, I want to view the Approval History for a mission | HIGH | READY |
| As an authorized user, I want to view the Settlement History for a mission | MEDIUM | READY |
| As an authorized user, I want to view the Attachments uploaded to a mission | HIGH | READY |

### Feature: My Missions
**Note:** This screen was explicitly missing from the original UX HTML prototype — flagged and required by `MTN_Travel_System_Figma_Spec.md` Phase 1 Issue #8.
| User Story | Priority | Status |
|---|---|---|
| As an Assigned Person, I want to view only my own missions in a "My Missions" list | HIGH | READY |
| As an Assigned Person, I want to track the status of each of my missions | HIGH | READY |
| As an Assigned Person, I want to search my missions | MEDIUM | READY |
| As an Assigned Person, I want to filter my missions by status and type | MEDIUM | READY |

---

## EPIC EP-03 — Mission Creation [UPDATED]
**Source:** MoM §1–§4; `MTN_Travel_Product_Backlog_TFS.docx`
**Status:** READY (form fields); NEEDS CLARIFICATION (currency display)

### Feature: Create Mission
| User Story | Priority | Status | Source |
|---|---|---|---|
| As an Assigned Person, I want to create a new Mission Request so that it enters the approval workflow | HIGH | READY | Backlog |
| As an Assigned Person, I want to select Mission Type (National or International) | HIGH | READY | MoM §2 |
| As an Assigned Person, I want to select Mission Category (Training / Conference / Job Mission) | HIGH | READY | MoM §2 — BR-04 |
| As an Assigned Person, I want to select the Destination from the configured destination list | HIGH | READY | `Travel_System_Requirements.docx` |
| As an Assigned Person, I want to identify the Assigned Person (request creator) separately from the Employee Name (traveler) | HIGH | READY | MoM §1 Action Item 1 — Decision D-02 [UPDATED] |
| As an Assigned Person, I want to select the Start Date and End Date for the mission | HIGH | READY | MoM §4 |
| As an Assigned Person, I want to enter the Mission Purpose | HIGH | READY | Backlog |
| As an Assigned Person, I want to upload Supporting Documents | HIGH | READY | Backlog |
| As an Assigned Person, I want to save a mission as a Draft before submitting | MEDIUM | READY | Backlog |
| As an Assigned Person, I want to submit a completed Mission Request | HIGH | READY | Backlog |

### Feature: Validation
| User Story | Priority | Status |
|---|---|---|
| As an Assigned Person, I want the system to validate all mandatory fields before submission | HIGH | READY |
| As an Assigned Person, I want the system to prevent me from setting an End Date before the Start Date | HIGH | READY |
| As an Assigned Person, I want the system to validate uploaded attachments | MEDIUM | READY |
| As an Assigned Person, I want to see clear validation error messages when submission fails | HIGH | READY |
| As an Assigned Person, I want the currency to be automatically determined by Mission Type (National → SDG; International → USD) | HIGH | READY |
| As an Assigned Person, I want the system to prevent me from creating a new mission while I already have an open mission | HIGH | READY — BR-01 |

---

## EPIC EP-04 — Approval Workflow [UPDATED — HR added]
**Source:** MoM Confirmed Workflow; MoM §5; Second-session transcript
**Status:** PARTIAL — HR placement NEEDS CLARIFICATION

### Feature: Line Manager Approval
| User Story | Priority | Status | Source |
|---|---|---|---|
| As a Line Manager, I want to view all Pending Approval requests assigned to me so that I can act on them | HIGH | READY | MoM §5 |
| As a Line Manager, I want to view full Mission Details before making an approval decision | HIGH | READY | MoM §5 |
| As a Line Manager, I want to Approve a Mission Request with an optional note | HIGH | READY | MoM §5 |
| As a Line Manager, I want to Reject a Mission Request with a mandatory reason note | HIGH | READY | MoM §5 |

**Acceptance Criteria (Line Manager Approve):** Given I am logged in as Line Manager; When I open Pending Approvals; Then I see missions pending my approval with Mission ID, Employee Name, Destination, Dates, Type; When I click Approve with optional note; Then status changes to Pending Division Manager Approval and DM is notified by email; When I click Reject with mandatory note; Then status changes to Rejected and Assigned Person is notified. (Source: `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` US-EP04-LM-001)

### Feature: Division Manager Approval
| User Story | Priority | Status |
|---|---|---|
| As a Division Manager, I want to view all Pending DM Approval requests so I can act on them | HIGH | READY |
| As a Division Manager, I want to view Mission Details before approving | HIGH | READY |
| As a Division Manager, I want to Approve a Mission Request | HIGH | READY |
| As a Division Manager, I want to Reject a Mission Request with a mandatory reason note | HIGH | READY |

### Feature: [NEW] HR Approval — International Missions
**Source:** Second-session transcript §4:06–§11:21
**Status:** NEEDS CLARIFICATION — workflow placement unconfirmed (BQ-01)
| User Story | Priority | Status |
|---|---|---|
| [NEW] As an HR Team Member, I want to view Pending HR Approval requests for International missions so I can act on them | HIGH | NEEDS CLARIFICATION |
| [NEW] As an HR Team Member, I want to Approve an International mission | HIGH | NEEDS CLARIFICATION |
| [NEW] As an HR Team Member, I want to Reject an International mission with a mandatory reason note | HIGH | NEEDS CLARIFICATION |
| [NEW] As an HR Team Member, I want to add HR Notes when making my decision | MEDIUM | NEEDS CLARIFICATION |
| [NEW] As an HR Team Member, I want to view the Mission Details before making my decision | HIGH | NEEDS CLARIFICATION |

### Feature: [NEW] HR Notification — National Missions (informational, no action)
**Source:** Second-session transcript §9:55–§11:03
| User Story | Priority | Status |
|---|---|---|
| [NEW] As the System, I want to send an email notification to HR when a National Mission passes DM Approval, so that HR is informed (no action required from HR) | HIGH | NEEDS CLARIFICATION |

---

## EPIC EP-05 — Travel Review [UPDATED]
**Source:** MoM §6; Backlog
**Status:** PARTIAL READY (form/reject/submit actions READY); BLOCKED (auto-calculation pending formula confirmation)

### Feature: Travel Cost Review
| User Story | Priority | Status | Source |
|---|---|---|---|
| As a Travel Team Member, I want to view all Pending Travel Reviews so I can act on them | HIGH | READY | Backlog |
| As a Travel Team Member, I want to enter the Per Diem amount | HIGH | READY (value entry READY; formula confirmation BLOCKED) | MoM §6 |
| As a Travel Team Member, I want to enter the Accommodation Cost | HIGH | READY (value entry READY; formula confirmation BLOCKED) | MoM §6 |
| As a Travel Team Member, I want to enter Other Expenses | MEDIUM | READY | Backlog |
| As a Travel Team Member, I want to modify cost values before submission | HIGH | READY | MoM §6 |
| As a Travel Team Member, I want to Reject a mission from Travel Review with a mandatory reason | HIGH | READY | MoM §6 |
| As a Travel Team Member, I want to Submit the reviewed mission to GL Review [CORRECTED — was "Submit to Treasury"] | HIGH | READY | MoM §7; Conflict CF-01 resolved |

### Feature: Travel Cost Validation
| User Story | Priority | Status |
|---|---|---|
| As the System, I want to calculate the Mission Total cost from the cost components | HIGH | BLOCKED — formula unconfirmed (BQ-03, BQ-04) |
| As the Travel Team, I want to see the cost recalculate automatically when I modify values | HIGH | BLOCKED — formula unconfirmed |
| As the Travel Team, I want to see a Cost Summary before submitting to GL | HIGH | READY (display READY; calculated total BLOCKED) |

### Feature: [MISSING] Destination Pricing Configuration
**Status:** MISSING INFORMATION — destination-based pricing configuration screen not yet defined (GAP-04, BQ-05)

---

## EPIC EP-06 — GL Review
**Source:** MoM §7; Backlog
**Status:** READY

### Feature: Financial Validation
| User Story | Priority | Status |
|---|---|---|
| As a GL Team Member, I want to view all Pending GL Review requests | HIGH | READY |
| As a GL Team Member, I want to review the cost details submitted by the Travel Team | HIGH | READY |
| As a GL Team Member, I want to modify financial values if corrections are needed | HIGH | READY |
| As a GL Team Member, I want to Reject a mission from GL Review with a mandatory reason | HIGH | READY |
| As a GL Team Member, I want to Submit the reviewed mission to Treasury | HIGH | READY |

### Feature: GL Audit
| User Story | Priority | Status |
|---|---|---|
| As a GL Team Member, I want to view the Travel Team's original calculations for reference | MEDIUM | READY |
| As a GL Team Member, I want to view the full Financial Summary | HIGH | READY |
| As a GL Team Member, I want to record GL Notes | MEDIUM | READY |

---

## EPIC EP-07 — Treasury
**Source:** MoM §8; `Travel_System_Requirements.docx`; Backlog
**Status:** READY

### Feature: Payment Processing
| User Story | Priority | Status | Business Rule |
|---|---|---|---|
| As a Treasury Team Member, I want to view all Pending Payments | HIGH | READY | — |
| As a Treasury Team Member, I want to enter the Payment Reference | HIGH | READY | BR-05: Treasury confirms only, no reject |
| As a Treasury Team Member, I want to enter the Payment Date | HIGH | READY | — |
| As a Treasury Team Member, I want to add Treasury Notes | MEDIUM | READY | — |
| As a Treasury Team Member, I want to Confirm Payment, which sets the mission status to Mission Active | HIGH | READY | BR-05 |

### Feature: Treasury Tracking
| User Story | Priority | Status |
|---|---|---|
| As an authorized user, I want to view Payment History | MEDIUM | READY |
| As an authorized user, I want to search and filter Payments | MEDIUM | READY |

---

## EPIC EP-08 — Mission Extension [UPDATED — Approval Cycle + Recalculation + Audit Field Added]
**Source:** MoM §10; Backlog; source-of-truth v3 Section 3
**Status:** PARTIAL — recalculation BLOCKED on formula; HR sub-step NEEDS CLARIFICATION

### Feature: Extension Request
| User Story | Priority | Status | Source |
|---|---|---|---|
| As an Assigned Person, I want to request a Mission Extension when my mission is Active | HIGH | READY | Backlog |
| As an Assigned Person, I want to enter the New End Date for the extension | HIGH | READY | Backlog |
| As an Assigned Person, I want to enter the Reason for Extension | HIGH | READY | Backlog |
| As an Assigned Person, I want to submit the Extension Request into the approval cycle | HIGH | READY | MoM §10 |
| [NEW] As the System, I want to recalculate Per Diem for the extension period (New End Date − Current End Date) | HIGH | BLOCKED — formula unconfirmed (BQ-03) | MoM §10 |
| [NEW] As the System, I want to recalculate Accommodation for the extension period | HIGH | BLOCKED — formula unconfirmed (BQ-04) | MoM §10 |
| [NEW] As the System, I want to record the user who submitted the Extension ("Extended By") with a timestamp | HIGH | READY | MoM §10 Action Item 3 |

### Feature: [NEW] Extension Approval Cycle
**Source:** MoM §10: "same workflow and approval cycle as original mission"
| User Story | Priority | Status |
|---|---|---|
| [NEW] As a Line Manager, I want to Approve/Reject a Mission Extension request | HIGH | READY |
| [NEW] As a Division Manager, I want to Approve/Reject a Mission Extension request | HIGH | READY |
| [NEW] As an HR Team Member, I want to Approve/Reject an International Mission Extension | HIGH | NEEDS CLARIFICATION (BQ-09) |
| [NEW] As a Travel Team Member, I want to review costs for a Mission Extension | HIGH | BLOCKED (formula) |
| [NEW] As a GL Team Member, I want to validate financials for a Mission Extension | HIGH | READY |
| [NEW] As a Treasury Team Member, I want to confirm payment for a Mission Extension | HIGH | READY |

### Feature: Extension Tracking
| User Story | Priority | Status |
|---|---|---|
| As an authorized user, I want to view the Extension History for a mission | MEDIUM | READY |
| As an authorized user, I want to view the Extension Status | HIGH | READY |
| As an authorized user, I want to view the Approval History for an extension | MEDIUM | READY |

**Business Rule:** BR-06 — Long-term missions (monthly) must be closed and a new mission created; auto-extension is NOT supported.

---

## EPIC EP-09 — Mission Closure [UPDATED — Cancellation Added]
**Source:** MoM §11; `Travel_System_Requirements.docx`
**Status:** PARTIAL — Closure READY; Cancellation BLOCKED

### Feature: Mission Closure
| User Story | Priority | Status |
|---|---|---|
| As an Assigned Person, I want to close my mission when it has been completed | HIGH | READY |
| As an Assigned Person, I want to upload Closure Documents when closing my mission | HIGH | READY |
| As an Assigned Person, I want to Submit the Closure | HIGH | READY |

### Feature: Closure Tracking
| User Story | Priority | Status |
|---|---|---|
| As an authorized user, I want to view the documents uploaded at closure | MEDIUM | READY |
| As an authorized user, I want to view the Closure Status | MEDIUM | READY |

### Feature: [NEW] Mission Cancellation
**Source:** Second-session transcript §52:24
**Status:** MISSING INFORMATION — rules, eligible statuses, and advance-recovery handling undefined (BQ-06)
| User Story | Priority | Status |
|---|---|---|
| [NEW] As an Assigned Person, I want to cancel a mission before departure | HIGH | MISSING INFORMATION |
| [NEW] As an Assigned Person, I want to record a Cancellation Reason | HIGH | MISSING INFORMATION |

---

## EPIC EP-10 — Settlement
**Source:** MoM §11; `Travel_System_Requirements.docx`; Backlog
**Status:** READY

### Feature: Settlement Processing
| User Story | Priority | Status |
|---|---|---|
| As a Finance user, I want to view all missions Pending Settlement so I can process them | HIGH | READY |
| As a Finance user, I want to enter the Actual Costs for a mission (Per Diem, Accommodation, Other Expenses) | HIGH | READY |
| As a Finance user, I want to compare Planned vs. Actual costs side by side | HIGH | READY |
| As a Finance user, I want to see the Balance automatically calculated (Actual − Amount Paid) | HIGH | READY |
| As a Finance user, I want to add a Settlement Reference | HIGH | READY |
| As a Finance user, I want to Process the Settlement, completing the mission (status → Completed) | HIGH | READY |

### Feature: Debit/Credit Management
| User Story | Priority | Status |
|---|---|---|
| As a Finance user, I want the system to identify whether the settlement results in an Employee Debit or Employee Credit | HIGH | READY |
| As a Finance user, I want to see the Settlement Result clearly displayed (Company owes Employee / Employee owes Company / Zero balance) | HIGH | READY |

---

## EPIC EP-11 — Reporting [UPDATED — HR Reports Pending]
**Source:** `Travel_System_Requirements.docx` Screen Inventory; Backlog
**Status:** PARTIAL — existing reports READY; HR reports BLOCKED

### Feature: Employee Mission History
| User Story | Priority | Status |
|---|---|---|
| As a Finance user, I want to view the Employee Mission History report | HIGH | READY |
| As a Finance user, I want to search/filter the report by employee, date range, mission type, status | HIGH | READY |
| As a Finance user, I want to export the Employee Mission History report | HIGH | READY |

### Feature: Debit/Credit Report
| User Story | Priority | Status |
|---|---|---|
| As a Finance user, I want to view the Debit/Credit Report showing all employee balances | HIGH | READY |
| As a Finance user, I want to filter the report by date range and employee | HIGH | READY |
| As a Finance user, I want to export the Debit/Credit Report | HIGH | READY |

### Feature: [MISSING] HR Reports
**Status:** MISSING INFORMATION — pending HR workshop (BQ-08)

---

## EPIC EP-12 — Notifications [UPDATED — HR added]
**Source:** MoM §9; Second-session transcript
**Status:** READY (notification trigger points); MISSING INFORMATION (notification content/templates)

### Feature: Workflow Notifications
| User Story | Priority | Status | Source |
|---|---|---|---|
| As the System, I want to notify the Line Manager by email when a mission requires their approval | HIGH | READY | MoM §9 |
| As the System, I want to notify the Division Manager by email when a mission requires their approval | HIGH | READY | MoM §9 |
| As the System, I want to notify the Travel Team by email when a mission is ready for cost review | HIGH | READY | MoM §9 |
| As the System, I want to notify the GL Team by email when a mission is ready for GL review | HIGH | READY | MoM §9 |
| As the System, I want to notify the Treasury Team by email when a mission requires payment processing | HIGH | READY | MoM §9 |
| As the System, I want to notify the Employee by email after their mission payment has been processed | HIGH | READY | MoM §9 |
| As the System, I want to notify the Assigned Person by email when their mission is rejected at any stage | HIGH | READY | MoM §9 |
| [NEW] As the System, I want to notify the HR Team by email when an International Mission requires HR approval | HIGH | NEEDS CLARIFICATION (BQ-01 — placement) | Second-session transcript §4:06 |
| [NEW] As the System, I want to send an informational notification to HR when a National Mission passes DM Approval | HIGH | NEEDS CLARIFICATION | Second-session transcript §9:55 |

**Business Rule:** BR-07 — All notifications are via email.

---

## EPIC EP-13 — Security & Roles [UPDATED]
**Source:** MoM §5, §13; Second-session transcript; `Travel_System_Requirements.docx`
**Status:** UPDATED

### Feature: Role Management
| User Story | Priority | Status | Source |
|---|---|---|---|
| As the System, I want to provide Mission Creator (Assigned Person) access to mission creation and own-mission management | HIGH | READY | MoM §5 |
| As the System, I want to provide Line Manager access to pending approval actions for their direct reports' missions | HIGH | READY | MoM §5 |
| As the System, I want to provide Division Manager access to DM-stage approvals | HIGH | READY | MoM §5 |
| As the System, I want to provide Travel Team access to Travel Review screens | HIGH | READY | MoM §5 |
| As the System, I want to provide GL Team access to GL Review screens | HIGH | READY | MoM §5 |
| As the System, I want to provide Treasury Team access to Payment screens | HIGH | READY | MoM §5 |
| As the System, I want to provide Finance access to Settlement and Report screens | HIGH | NEEDS CLARIFICATION (BQ-07 — Finance vs GL Team role conflict) | `Travel_System_Requirements.docx` |
| [NEW] As the System, I want to provide HR Team access to HR Approval screens (International missions) and HR notification inbox | HIGH | NEEDS CLARIFICATION | Second-session transcript §4:06 |

### Feature: Authorization
| User Story | Priority | Status |
|---|---|---|
| As the System, I want to restrict screens by role so that users only see what is relevant to them | HIGH | READY |
| As the System, I want to restrict actions by role so that users can only perform authorized operations | HIGH | READY |
| As the System, I want to hide unauthorized menu items from non-authorized roles | HIGH | READY |

### Feature: [UPDATED] User Provisioning
| User Story | Priority | Status | Source |
|---|---|---|---|
| [UPDATED] As the System, I want to automatically recognize Microsoft 365 users — no manual add/remove screen is required; user provisioning is managed via Microsoft 365 / Azure AD | HIGH | READY | Second-session transcript §7:59–§8:57; MoM §13 |

---

## [NEW] EPIC EP-NEW-01 — HR Approval
**Source:** Second-session Meeting Transcript 11/06/2026 — entirely absent from original backlog
**Status:** NEEDS CLARIFICATION — workflow placement (BQ-01) unconfirmed by MTN Sudan

See EP-04 Feature "HR Approval" and Feature "HR Notification" for the related user stories (consolidated there to avoid duplication).

---

## [NEW] EPIC EP-NEW-02 — Employee Grading
**Source:** Second-session Meeting Transcript 11/06/2026 §48:55
**Status:** BLOCKED — grade levels and rate matrix MISSING INFORMATION (BQ-02)

### Feature: Grade-Based Cost
| User Story | Priority | Status | Source |
|---|---|---|---|
| [NEW] As the System, I want to automatically apply the Accommodation rate based on the Employee's Grade Level when a mission cost is calculated | HIGH | BLOCKED | Second-session transcript §48:55–§50:36 |
| [NEW] As a Travel Team Member, I want to see the grade-linked Accommodation rate displayed in the Travel Review screen | HIGH | BLOCKED | Second-session transcript §50:36 |

---

## Development Readiness Summary

| Category | Count |
|---|---|
| Epics (original, validated) | 13 |
| Epics (new, from backlog analysis) | 2 |
| User Stories — READY | ~65% |
| User Stories — NEEDS CLARIFICATION | ~25% |
| User Stories — BLOCKED / MISSING INFO | ~10% |
| Gaps identified | 12 |
| Conflicts resolved | 3 of 5 |
| Open clarification questions | 13 (see [../02_Requirements/Clarification_Register.md](../02_Requirements/Clarification_Register.md)) |

## Future Expansion
Backlog will be updated as MTN Sudan resolves clarification items. Sprint assignments (Sprint 1 scope: Mission Log List, Create Mission, My Missions, Mission Extension) are tracked in [../00_Governance/MOM_Log.md](../00_Governance/MOM_Log.md) Entry 4.
