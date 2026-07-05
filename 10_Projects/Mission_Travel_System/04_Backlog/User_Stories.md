# User Stories — MTN Sudan Travel Mission Management System

## Purpose
Azure DevOps / TFS-ready User Stories in full format, per [02_Standards/User_Stories.md](../../../02_Standards/User_Stories.md). Reproduces and extends the user stories in `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 5. Only new and representative stories are shown in full Given/When/Then format here; all others are referenced from [Product_Backlog.md](Product_Backlog.md).

---

## US-EP03-CR-001 — Create Mission Request

**Title:** Create Mission Request

**As a** Mission Creator (Assigned Person)
**I want to** create a new Mission Request with all required information
**So that** the mission enters the approval workflow and can be reviewed and approved

**Priority:** HIGH

**Source Reference:** MoM §1–§4; `Travel_System_Requirements.docx`; source-of-truth v3 EP-03

**Business Rules:** BR-01 (one open mission per employee); BR-02/BR-03 (currency auto-determined); BR-04 (Mission Category values)

**Validation Rules:**
- Mandatory fields: Mission Type, Mission Category, Destination, Assigned Person, Employee Name, Start Date, End Date, Mission Purpose
- End Date must not precede Start Date
- Attachments format/size: MISSING INFORMATION (CQ rules not defined)
- Employee must not already have an open mission (BR-01)

**Acceptance Criteria:**

*Scenario 1 — Successful National Mission Creation:*
- **Given** I am logged in as a Mission Creator
- **When** I navigate to Create Mission and complete all mandatory fields with Mission Type = National
- **Then** the system auto-populates the Currency field as SDG (read-only)
- **And** when I click Submit, the mission is created with status = Pending Line Manager Approval
- **And** the Line Manager receives an email notification

*Scenario 2 — International Mission Currency:*
- **Given** I select Mission Type = International
- **Then** the system auto-populates Currency = USD (read-only)

*Scenario 3 — Duplicate Mission Blocked:*
- **Given** Employee already has a mission with status = Pending Line Manager Approval
- **When** I attempt to submit a new mission for the same Employee
- **Then** the system displays a validation error and prevents submission (BR-01)

*Scenario 4 — Invalid Date:*
- **Given** I enter End Date earlier than Start Date
- **When** I attempt to submit
- **Then** the system displays a date validation error and prevents submission

*Scenario 5 — Save Draft:*
- **Given** I have partially completed the form
- **When** I click Save Draft
- **Then** the mission is saved with status = Draft and does NOT enter the approval workflow

**Dependencies:** Destination list (ENT-02) must be configured. Employee/User list must be available from M365.

**Development Readiness Status:** READY FOR DEVELOPMENT

---

## US-EP04-LM-001 — Approve Mission Request (Line Manager)

**Title:** Approve Mission Request — Line Manager

**As a** Line Manager
**I want to** review and approve or reject a mission request submitted by an Assigned Person
**So that** the mission can proceed to Division Manager approval

**Priority:** HIGH

**Source Reference:** MoM Confirmed Workflow; MoM §5; source-of-truth v3 US-EP04-LM-001

**Business Rules:** Rejection requires a mandatory note

**Validation Rules:** Reject action must be blocked if no reason note is entered

**Acceptance Criteria:**

*Scenario 1 — Approve:*
- **Given** I am logged in as a Line Manager
- **When** I open Pending Approvals
- **Then** I see all missions pending my approval with: Mission ID, Employee Name, Destination, Dates, Type
- **When** I click Approve with an optional note and confirm
- **Then** mission status changes to Pending Division Manager Approval
- **And** the Division Manager is notified by email
- **And** the mission no longer appears in my Pending Approvals list

*Scenario 2 — Reject:*
- **When** I click Reject and enter a mandatory reason note and confirm
- **Then** mission status changes to Rejected
- **And** the Assigned Person is notified by email

*Scenario 3 — Reject without reason (negative):*
- **When** I click Reject without entering a reason note
- **Then** the system displays a validation error and prevents the rejection

**Dependencies:** None

**Development Readiness Status:** READY FOR DEVELOPMENT

---

## US-EP04-DM-001 — Approve Mission Request (Division Manager)

**Title:** Approve Mission Request — Division Manager

**As a** Division Manager
**I want to** review and approve or reject a mission request that has passed Line Manager approval
**So that** the mission proceeds to HR (International) or Travel Review (National)

**Priority:** HIGH

**Source Reference:** MoM Confirmed Workflow; source-of-truth v3 EP-04

**Business Rules:** Rejection requires mandatory note

**Acceptance Criteria:**

*Scenario 1 — Approve International Mission:*
- **Given** I am logged in as Division Manager and a mission type = International is in Pending DM Approval
- **When** I Approve
- **Then** mission status changes to Pending HR Approval
- **And** the HR Team is notified by email for approval action

*Scenario 2 — Approve National Mission:*
- **Given** mission type = National and I Approve
- **Then** mission status changes to Pending Travel Review
- **And** the Travel Team is notified by email
- **And** an informational notification is sent to HR (no action required from HR)

*Scenario 3 — Reject:*
- **When** I Reject with a mandatory note
- **Then** status changes to Rejected and Assigned Person is notified

**Dependencies:** HR workflow placement (BQ-01) must be confirmed before this scenario can be finalized in development.

**Development Readiness Status:** NEEDS CLARIFICATION — HR routing step at DM approval unconfirmed (BQ-01)

---

## [NEW] US-EP-NEW01-HR-001 — HR Approve International Mission

**Title:** [NEW] HR Approve International Mission

**As an** HR Team Member
**I want to** review and approve or reject an International mission after Division Manager approval
**So that** International missions receive HR governance before proceeding to Travel Review

**Priority:** HIGH

**Source Reference:** Second-session transcript 11/06/2026 §4:06–§11:21; source-of-truth v3 US-EP-NEW01-HR-001

**Business Rules:** HR approves International missions; HR is only notified (not an approver) for National missions

**Acceptance Criteria:**

*Scenario 1 — HR Approve:*
- **Given** I am logged in as HR Team Member and an International mission in status Pending HR Approval is in my queue
- **When** I Approve
- **Then** mission status changes to Pending Travel Review
- **And** the Travel Team is notified by email

*Scenario 2 — HR Reject:*
- **When** I Reject with a mandatory note
- **Then** status changes to Rejected and Assigned Person is notified

*Scenario 3 — National mission does NOT appear (negative):*
- **Given** a National Mission is in the system
- **Then** it should NOT appear in my HR Pending Approvals queue
- **And** I should not be able to take any approval action on it

**Dependencies:** BQ-01 must be resolved (HR approval is before or after DM? — current assumption is "after DM" per source-of-truth v3 Section 4.1)

**Development Readiness Status:** NEEDS CLARIFICATION — Workflow position of HR approval step must be formally confirmed by MTN Sudan (BQ-01)

---

## [NEW] US-EP-NEW02-GRD-001 — Grade-Based Accommodation Rate

**Title:** [NEW] Apply Grade-Based Accommodation Rate at Mission Cost Review

**As a** Travel Team Member
**I want to** see the Accommodation cost automatically calculated based on the Employee's Grade Level
**So that** Travel Review accurately reflects the correct allowance for each employee

**Priority:** HIGH

**Source Reference:** Second-session transcript 11/06/2026 §48:55–§50:36; source-of-truth v3 US-EP-NEW02-GRD-001

**Business Rules:** BR-Grade-01 (pending) — Accommodation rate varies by employee grade (Level 2 to Level 3H; exact rates not yet provided)

**Validation Rules:** Grade level must be associated with the traveling employee before cost review begins

**Acceptance Criteria:**

*Scenario 1 — Grade Rate Auto-Applied:*
- **Given** Employee has Grade Level X and a destination rate is configured
- **When** the mission reaches Travel Review
- **Then** the Accommodation field is pre-populated with the grade-linked rate × accommodation nights
- **And** the Travel Team Member can see the applied grade and rate basis

**Dependencies:** BQ-02 must be resolved (grade levels and rates); ENT-10 (Employee Grade) must be populated

**Development Readiness Status:** BLOCKED — Grade levels and accommodation rate matrix not yet provided by MTN Sudan (BQ-02)

---

## [UPDATED] US-EP08-EXT-001 — Mission Extension with Recalculation

**Title:** [UPDATED] Request Mission Extension — Recalculate Costs and Record Auditor

**As an** Assigned Person
**I want to** submit a Mission Extension with a new end date and have Per Diem and Accommodation recalculated for the extension period
**So that** the extension accurately reflects the additional cost and is fully auditable

**Priority:** HIGH

**Source Reference:** MoM §10; source-of-truth v3 US-EP08-EXT-001

**Business Rules:** BR-06 (monthly missions are independent — this story applies to standard extensions only); BR-Ext-01 proposed formula applies

**Acceptance Criteria:**

*Scenario 1 — Successful Extension:*
- **Given** mission status = Mission Active
- **When** I submit an extension with a New End Date that is later than the current End Date and enter an Extension Reason
- **Then** the system calculates Extension Days = New End Date − Current End Date
- **And** Per Diem is recalculated for the extension days (formula: Days × Destination Rate per BR-Ext-01 proposed)
- **And** Accommodation is recalculated for the extension nights
- **And** the new cost total is displayed and enters the approval cycle (LM → DM → HR if International → Travel → GL → Treasury)
- **And** the "Extended By" field records my user ID and the submission timestamp

*Scenario 2 — Invalid Date (negative):*
- **Given** I enter a New End Date that is earlier than or equal to the current End Date
- **Then** the system displays a validation error and prevents submission

**Dependencies:** Cost formula confirmation (BQ-03, BQ-04); HR sub-step in extension cycle (BQ-09)

**Development Readiness Status:** NEEDS CLARIFICATION — Per Diem/Accommodation formulas pending (BQ-03, BQ-04); HR sub-step within extension unconfirmed (BQ-09)

---

## US-EP07-TR-001 — Treasury Confirm Payment

**Title:** Treasury Confirm Payment

**As a** Treasury Team Member
**I want to** confirm payment for an approved mission
**So that** the mission is marked as Active and the employee can proceed with their travel

**Priority:** HIGH

**Source Reference:** MoM §8; source-of-truth v3 EP-07

**Business Rules:** BR-05 — Treasury does not reject; Treasury confirms payment only

**Acceptance Criteria:**

*Scenario 1 — Confirm Payment:*
- **Given** I am logged in as Treasury and a mission is in status Pending Payment
- **When** I enter the Payment Reference, Payment Date, and optional Notes and click Confirm Payment
- **Then** mission status changes to Mission Active
- **And** the Employee is notified by email
- **And** the mission no longer appears in the Pending Payments list

*Scenario 2 — No Reject Action (negative constraint):*
- **Given** I am viewing a Pending Payment
- **Then** no "Reject" button or action is available to me (BR-05)

**Dependencies:** None

**Development Readiness Status:** READY FOR DEVELOPMENT

---

## US-EP10-FIN-001 — Process Mission Settlement

**Title:** Process Mission Settlement

**As a** Finance user
**I want to** review and finalize the settlement for a closed mission
**So that** the financial obligation between the employee and the company is formally resolved and the mission is marked Completed

**Priority:** HIGH

**Source Reference:** MoM §11; source-of-truth v3 EP-10; Figma Spec Screen 11

**Business Rules:** None specifically documented beyond the balance calculation logic

**Acceptance Criteria:**

*Scenario 1 — Settlement with Employee Debit:*
- **Given** I am logged in as Finance and a mission is in status Pending Settlement
- **When** I enter Actual Per Diem, Actual Accommodation, and Actual Other Expenses
- **Then** the system calculates Balance = Actual Total − Amount Already Paid
- **And** if Balance > 0, the result is displayed as "Employee owes company" with the amount
- **When** I enter the Settlement Reference and click Process Settlement
- **Then** mission status changes to Completed

*Scenario 2 — Settlement with Employee Credit:*
- **Given** Balance < 0
- **Then** result is displayed as "Company owes employee"

*Scenario 3 — Zero Balance:*
- **Given** Balance = 0
- **Then** result is displayed as "No balance due"

**Dependencies:** Closure documents (ENT-08) must be submitted before settlement

**Development Readiness Status:** READY FOR DEVELOPMENT

## Future Expansion
Additional full user stories will be produced for remaining READY items in [Product_Backlog.md](Product_Backlog.md) prior to each sprint. BLOCKED and NEEDS CLARIFICATION stories will be completed once MTN Sudan resolves the corresponding items in [../02_Requirements/Clarification_Register.md](../02_Requirements/Clarification_Register.md).
