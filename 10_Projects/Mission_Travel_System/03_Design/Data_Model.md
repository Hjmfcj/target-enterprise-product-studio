# Data Model — MTN Sudan Travel Mission Management System

## Purpose
Documents the logical data model (entities, attributes, relationships, and CRUD matrix), per the Data Model Standard. Sourced exclusively from uploaded project artifacts; no attributes are invented.

## Scope
Logical/business data model only. Physical implementation (SharePoint list schemas, column types, internal field names) belongs in the Technical Design Document.

## Intended Usage
Cross-reference with [../02_Requirements/FRD.md](../02_Requirements/FRD.md) and [../04_Backlog/User_Stories.md](../04_Backlog/User_Stories.md).

---

## 1. Entity List

| Entity ID | Entity Name | Description | Source |
|---|---|---|---|
| ENT-01 | Mission | The core record representing a travel mission request through its full lifecycle | `Travel_System_Requirements.docx`; MoM Confirmed Workflow; source-of-truth v3 |
| ENT-02 | Destination | A configurable list of travel destinations with associated pricing rates | `Travel_System_Requirements.docx` Business Controls ("Destination list should be configurable"); source-of-truth v3 EP-05; `MTN_Travel_Product_Backlog_TFS.docx` |
| ENT-03 | Mission Extension | An extension record linked to a Mission, capturing the new end date, reason, recalculated costs, and Extended By | MoM §10; source-of-truth v3 EP-08 |
| ENT-04 | Approval Record | A record of each approval or rejection action taken at every workflow stage for a Mission | MoM Confirmed Workflow; source-of-truth v3 — "View Approval History" appears as a user story across multiple epics |
| ENT-05 | Cost Record | Travel cost information entered by the Travel Team (Per Diem, Accommodation, Other Expenses) and subsequently validated by GL | MoM §4, §6; source-of-truth v3 EP-05, EP-06 |
| ENT-06 | Payment Record | Treasury payment confirmation details for a Mission | MoM §8; source-of-truth v3 EP-07 |
| ENT-07 | Settlement Record | Finance settlement output — planned vs. actual comparison, balance, debit/credit identification | MoM §11; source-of-truth v3 EP-10 |
| ENT-08 | Closure Record | Closure documentation uploaded by the Assigned Person at mission end | MoM §11; source-of-truth v3 EP-09 |
| ENT-09 | Employee / User | System user, provisioned via Microsoft 365 / Azure AD | Second-session transcript §7:59–§8:57; MoM §13; `Travel_System_Requirements.docx` User Roles |
| ENT-10 | Employee Grade | Grade level of an employee that determines the Accommodation rate | Second-session transcript §48:55–§50:36 — **MISSING INFORMATION**: exact grade levels and corresponding rates must be provided by MTN Sudan (BQ-02) |
| ENT-11 | Notification | An email notification triggered at each workflow stage | MoM §9; source-of-truth v3 EP-12 |
| ENT-12 | Attachment | A file uploaded to a Mission (at creation, during closure, or as supporting documentation) | Source-of-truth v3 EP-03 ("Upload Supporting Documents"); EP-09 ("Upload Closure Documents") |

---

## 2. Data Dictionary

### ENT-01 — Mission

| Attribute | Description | Data Type | Mandatory | Business Rule / Constraint | Source |
|---|---|---|---|---|---|
| Mission ID | Unique system identifier | Auto-generated | Yes | System-generated; not user-editable | `Travel_System_Requirements.docx` |
| Mission Type | National or International | Lookup (2 values) | Yes | BR-02, BR-03: determines currency automatically | MoM §2 |
| Mission Category | Training / Conference / Job Mission | Lookup (3 values) | Yes | BR-04: only these three values allowed | MoM §2 |
| Destination | Selected from the configurable Destination list | Lookup → ENT-02 | Yes | — | `Travel_System_Requirements.docx` |
| Assigned Person | The person who created the mission request (coordinator) | Lookup → ENT-09 | Yes | — | MoM §1 — Decision D-02 |
| Employee Name | The employee traveling on the mission (may differ from Assigned Person) | Lookup → ENT-09 | Yes | — | MoM §1 — Decision D-02; source-of-truth v3 EP-03 |
| Start Date | Mission start date | Date | Yes | End Date must not precede Start Date | MoM §4 |
| End Date | Mission end date | Date | Yes | End Date must not precede Start Date | MoM §4 |
| Duration (Days) | Calculated: End Date − Start Date | Calculated, Integer | Read-only | System-calculated; used in Per Diem calculation (BR-Ext-01 proposed) | MoM §4 |
| Mission Purpose | Free-text purpose of the mission | Text | Yes | — | Source-of-truth v3 EP-03 |
| Currency | SDG (National) or USD (International) | Auto-determined | Read-only | BR-02, BR-03: auto-determined from Mission Type, not user-editable | MoM §3 |
| Status | Current lifecycle status | Lookup (status list) | Yes | Governed status machine — see Status List below | Source-of-truth v3 Section 4.2 |
| Draft Flag | Whether mission is saved as draft (not yet submitted) | Boolean | — | Draft missions do not enter the approval workflow | Source-of-truth v3 EP-03 |

**Mission Status List** (per source-of-truth v3 Section 4.2):
| Status | Description | Source |
|---|---|---|
| Draft | Saved but not submitted | `Travel_System_Requirements.docx` |
| Pending Line Manager Approval | Submitted; awaiting LM | `Travel_System_Requirements.docx` |
| Pending Division Manager Approval | LM approved; awaiting DM | `Travel_System_Requirements.docx` |
| Pending HR Approval | DM approved; awaiting HR (International only) | Second-session transcript |
| Pending Travel Review | All approvals done; awaiting Travel Team | `Travel_System_Requirements.docx` |
| Pending GL Review | Travel review done; awaiting GL Team | MoM Confirmed Workflow |
| Pending Payment | GL approved; awaiting Treasury | `Travel_System_Requirements.docx` |
| Mission Active | Payment confirmed; mission underway | `Travel_System_Requirements.docx` |
| Mission Extended | Extension approved and paid | `Travel_System_Requirements.docx` |
| Mission Closed | Closure submitted; pending settlement | `Travel_System_Requirements.docx` |
| Pending Settlement | Awaiting Finance settlement | `Travel_System_Requirements.docx` |
| Completed | Settlement done; mission fully closed | `Travel_System_Requirements.docx` |
| Rejected | Rejected at any approval stage | MoM |
| Cancelled | Pre-departure cancellation — **MISSING INFORMATION**: rules undefined | Second-session transcript §52:24 |

### ENT-02 — Destination

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Destination ID | Unique identifier | Auto-generated | Yes | — | — |
| Destination Name | Name of the destination | Text | Yes | — | `Travel_System_Requirements.docx` |
| Destination Type | Internal (National) or External (International) | MISSING INFORMATION | — | MISSING INFORMATION | MISSING INFORMATION |
| Per Diem Rate | Rate per day for Per Diem (varies by destination) | Currency | Yes | **MISSING INFORMATION — MTN Sudan to provide** (BQ-05); Darfur cited as a higher-rate example in transcript §53:04–§53:49 | Second-session transcript; source-of-truth v3 GAP-04 |
| Accommodation Rate | Rate per night for accommodation (also grade-linked) | Currency | Yes | **MISSING INFORMATION — MTN Sudan to provide** (BQ-05; BQ-02) | Second-session transcript |
| Is Active | Whether the destination is currently available for selection | Boolean | Yes | Configurable by an admin role — **MISSING INFORMATION**: which role manages destination configuration is not defined in any uploaded artifact | `Travel_System_Requirements.docx` Business Controls |

### ENT-03 — Mission Extension

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Extension ID | Unique identifier | Auto-generated | Yes | — | — |
| Mission ID | Parent mission reference | FK → ENT-01 | Yes | — | MoM §10 |
| New End Date | Proposed new mission end date | Date | Yes | Must be later than the current Mission End Date | Source-of-truth v3 UAT-EP08-EXT-001 |
| Extension Reason | Reason for extension | Text | Yes | — | Source-of-truth v3 EP-08 |
| Extension Days | Calculated: New End Date − Current End Date | Calculated, Integer | Read-only | System-calculated | Source-of-truth v3 EP-08 |
| Extended By — User | Identity of the user who submitted the extension | FK → ENT-09 | Yes | Audit field — system-captured | MoM §10 Action Item 3 |
| Extended By — Timestamp | Date/time the extension was submitted | DateTime | Yes | Audit field — system-captured | MoM §10 Action Item 3 |
| Per Diem Recalculated | Recalculated Per Diem for the extension period | Currency | Yes | **BLOCKED** — formula unconfirmed (BQ-03) | MoM §10 |
| Accommodation Recalculated | Recalculated Accommodation for the extension period | Currency | Yes | **BLOCKED** — formula unconfirmed (BQ-04) | MoM §10 |
| Extension Status | Status of this extension request in its own approval cycle | Lookup (mirrors Mission status subset) | Yes | Same approval cycle as original mission per MoM §10 | MoM §10; source-of-truth v3 EP-08 |

### ENT-04 — Approval Record

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Approval ID | Unique identifier | Auto-generated | Yes | — | — |
| Mission ID | Parent mission | FK → ENT-01 | Yes | — | — |
| Stage | Workflow stage (LM / DM / HR / Travel / GL / Treasury) | Lookup | Yes | — | MoM Confirmed Workflow |
| Decision | Approved / Rejected / Confirmed Payment | Lookup | Yes | — | — |
| Notes | Approver's notes | Text | Conditional | Mandatory on Rejection; optional on Approval | Source-of-truth v3 US-EP04-LM-001 Acceptance Criteria |
| Decided By | User who made the decision | FK → ENT-09 | Yes | — | — |
| Decision Date/Time | Timestamp of decision | DateTime | Yes | — | — |

### ENT-05 — Cost Record

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Cost ID | Unique identifier | Auto-generated | Yes | — | — |
| Mission ID | Parent mission | FK → ENT-01 | Yes | — | — |
| Per Diem Amount | Per Diem as entered/confirmed by Travel Team | Currency | Yes | **BLOCKED** on confirmed formula | MoM §4, §6 |
| Accommodation Amount | Accommodation as entered/confirmed by Travel Team | Currency | Yes | **BLOCKED** on confirmed formula | MoM §4, §6 |
| Other Expenses | Other expenses entered by Travel Team | Currency | No | — | Source-of-truth v3 EP-05 |
| Total Mission Cost | Sum of all cost components | Calculated | Read-only | System-calculated | Source-of-truth v3 EP-05 |
| GL Notes | Notes added by GL Team during GL Review | Text | No | — | Source-of-truth v3 EP-06 |

### ENT-06 — Payment Record

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Payment ID | Unique identifier | Auto-generated | Yes | — | — |
| Mission ID | Parent mission | FK → ENT-01 | Yes | — | — |
| Payment Reference | Reference entered by Treasury | Text | Yes | — | Source-of-truth v3 EP-07 |
| Payment Date | Date of payment | Date | Yes | — | Source-of-truth v3 EP-07 |
| Treasury Notes | Notes added by Treasury | Text | No | — | Source-of-truth v3 EP-07 |
| Confirmed By | Treasury user who confirmed payment | FK → ENT-09 | Yes | — | — |
| Confirmed Date/Time | Timestamp of payment confirmation | DateTime | Yes | — | — |

### ENT-07 — Settlement Record

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Settlement ID | Unique identifier | Auto-generated | Yes | — | — |
| Mission ID | Parent mission | FK → ENT-01 | Yes | — | — |
| Planned Per Diem | Planned Per Diem from Cost Record | Currency | Read-only | Copied from ENT-05 | MoM §11 |
| Planned Accommodation | Planned Accommodation from Cost Record | Currency | Read-only | Copied from ENT-05 | MoM §11 |
| Planned Other Expenses | Planned Other Expenses from Cost Record | Currency | Read-only | Copied from ENT-05 | MoM §11 |
| Actual Per Diem | Actual Per Diem entered by Finance | Currency | Yes | — | Source-of-truth v3 EP-10 |
| Actual Accommodation | Actual Accommodation entered by Finance | Currency | Yes | — | Source-of-truth v3 EP-10 |
| Actual Other Expenses | Actual Other Expenses entered by Finance | Currency | No | — | Source-of-truth v3 EP-10 |
| Balance | Difference: Actual − Amount Paid (positive = employee owes, negative = company owes) | Calculated Currency | Read-only | System-calculated | Source-of-truth v3 EP-10; Figma Spec Screen 11 |
| Settlement Result | Debit (employee owes) or Credit (company owes) or Zero | Calculated Lookup | Read-only | — | Source-of-truth v3 EP-10 |
| Settlement Reference | Reference number entered by Finance | Text | Yes | — | Source-of-truth v3 EP-10 |
| Finance Notes | Notes entered by Finance | Text | No | — | Source-of-truth v3 EP-10 |
| Settlement Date | Date settlement was processed | DateTime | Yes | — | — |
| Settled By | Finance user who processed settlement | FK → ENT-09 | Yes | — | — |

### ENT-08 — Closure Record

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Closure ID | Unique identifier | Auto-generated | Yes | — | — |
| Mission ID | Parent mission | FK → ENT-01 | Yes | — | — |
| Closure Submitted By | User who submitted the closure | FK → ENT-09 | Yes | — | MoM §11 |
| Closure Date | Date submitted | DateTime | Yes | — | MoM §11 |
| Attachments | Reference to ENT-12 closure documents | FK → ENT-12 (1…*) | Yes | At least one document expected — **MISSING INFORMATION**: minimum count and file type rules not formally stated in any uploaded artifact | MoM §11; source-of-truth v3 EP-09 |

### ENT-09 — Employee / User

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| User ID | Microsoft 365 identity | M365/Azure AD sourced | Yes | Provisioned via Microsoft 365 — no manual add/remove | Second-session transcript §7:59; MoM §13 |
| Display Name | Full name | Text | Yes | From M365 directory | — |
| Email | Work email address | Email | Yes | From M365 directory; used for notifications | MoM §9 |
| Role | System role (Mission Creator / Line Manager / DM / Travel Team / GL Team / Treasury / Finance / HR) | Lookup (role list) | Yes | Role assignment mechanism **MISSING INFORMATION** — not documented how roles are assigned within the SharePoint/M365 context beyond the group-based access-control decision (Decision D-10) | MoM §5; source-of-truth v3 EP-13 |
| Grade | Employee Grade Level (Level 2 to Level 3H — exact range unconfirmed) | FK → ENT-10 | Conditional | Required for cost calculation — **MISSING INFORMATION**: grade assignment source and management not documented (BQ-02) | Second-session transcript §48:55–§50:36 |
| Line Manager | The employee's direct Line Manager | FK → ENT-09 (self-referencing) | MISSING INFORMATION | **MISSING INFORMATION** — how the system knows who an employee's Line Manager is (directory lookup vs. manual assignment) is not documented in any uploaded artifact | — |

### ENT-10 — Employee Grade

| Attribute | Description | Data Type | Mandatory | Constraint | Source |
|---|---|---|---|---|---|
| Grade ID | Unique identifier | Auto-generated | Yes | — | — |
| Grade Level | Grade label (Level 2, Level 3, Level 3H, etc.) | Text | Yes | **MISSING INFORMATION** — exact grade levels and count not provided (BQ-02) | Second-session transcript §48:55 |
| Accommodation Rate | Accommodation rate applicable to this grade | Currency | Yes | **MISSING INFORMATION** — rates not provided (BQ-02) | Second-session transcript §50:36 |

### ENT-11 — Notification

| Attribute | Description | Data Type | Notes | Source |
|---|---|---|---|---|
| Notification ID | Unique identifier | Auto-generated | — | — |
| Mission ID | Related mission | FK → ENT-01 | — | — |
| Notification Type | Stage-based type (LM Approval Due / DM Approval Due / HR Approval Due / Travel Review Due / GL Review Due / Payment Due / Approved Payment / Rejected / HR National Info) | Lookup | — | MoM §9; source-of-truth v3 EP-12 |
| Recipient | Notification recipient | FK → ENT-09 | — | MoM §9 |
| Channel | Email | Fixed value | BR-07 | MoM §9 |
| Sent Date/Time | When notification was dispatched | DateTime | — | — |
| Notification Content | Message body/template | MISSING INFORMATION | Template content not defined in any uploaded artifact | MoM Open Item 4 (for HR); others also undefined |

### ENT-12 — Attachment

| Attribute | Description | Data Type | Mandatory | Source |
|---|---|---|---|---|
| Attachment ID | Unique identifier | Auto-generated | Yes | — |
| Mission ID | Parent mission | FK → ENT-01 | Yes | Source-of-truth v3 EP-03 |
| Stage | Stage at which attachment was uploaded (Creation / Closure) | Lookup | Yes | Source-of-truth v3 EP-03, EP-09 |
| File Name | Uploaded filename | Text | Yes | — |
| Uploaded By | User who uploaded | FK → ENT-09 | Yes | — |
| Upload Date/Time | Timestamp | DateTime | Yes | — |
| File Type / Format | MISSING INFORMATION — acceptable file types not documented | MISSING INFORMATION | MISSING INFORMATION | — |
| Max File Size | MISSING INFORMATION | MISSING INFORMATION | MISSING INFORMATION | — |

---

## 3. Entity Relationships

```
ENT-09 (Employee/User) ──< ENT-01 (Mission) >── ENT-02 (Destination)
                                 │
                    ┌────────────┼──────────────────┐
                    ▼            ▼                  ▼
             ENT-03 (Extension) ENT-04 (Approval) ENT-05 (Cost)
                                                    │
                                                    ▼
                                             ENT-06 (Payment)
                                                    │
                                                    ▼
                                             ENT-08 (Closure)
                                                    │
                                                    ▼
                                             ENT-07 (Settlement)

ENT-09 (Employee/User) ──< ENT-10 (Employee Grade)
ENT-01 (Mission) ──< ENT-11 (Notification)
ENT-01 (Mission) ──< ENT-12 (Attachment)
```

---

## 4. CRUD Matrix

| Entity | Assigned Person | Line Manager | Division Manager | HR Team | Travel Team | GL Team | Treasury | Finance | System (Auto) |
|---|---|---|---|---|---|---|---|---|---|
| Mission (ENT-01) | Create, Read (own) | Read | Read | Read | Read | Read | Read | Read | Update (status) |
| Destination (ENT-02) | Read | Read | Read | Read | Read | Read | Read | Read | — |
| Mission Extension (ENT-03) | Create, Read (own) | Read, Update (approve/reject) | Read, Update | Read, Update | Read, Update | Read, Update | Read, Update (confirm) | Read | Update (status, Extended By, timestamp) |
| Approval Record (ENT-04) | Read | Create (own stage) | Create (own stage) | Create (own stage) | Create (own stage) | Create (own stage) | Create (own stage) | — | — |
| Cost Record (ENT-05) | Read | Read | Read | Read | Create, Update | Update (GL notes) | Read | Read | — |
| Payment Record (ENT-06) | Read | — | — | — | — | — | Create | — | — |
| Settlement Record (ENT-07) | Read | — | — | — | — | — | — | Create | Update (status) |
| Closure Record (ENT-08) | Create, Read | — | — | — | — | — | — | Read | — |
| Employee/User (ENT-09) | Read (own profile) | Read | Read | Read | Read | Read | Read | Read | — (M365 provisioning only) |
| Employee Grade (ENT-10) | MISSING INFORMATION | MISSING INFORMATION | MISSING INFORMATION | MISSING INFORMATION | Read | MISSING INFORMATION | MISSING INFORMATION | MISSING INFORMATION | MISSING INFORMATION |
| Notification (ENT-11) | Read (received) | Read (received) | Read (received) | Read (received) | Read (received) | Read (received) | Read (received) | Read (received) | Create |
| Attachment (ENT-12) | Create (Creation stage), Read | Read | Read | Read | Read | Read | Read | Read | — |

**MISSING INFORMATION items in CRUD Matrix:**
- Create/Update rights for ENT-02 Destination (configurable destination list — which role manages this configuration is undefined, see Screen Inventory note)
- Full CRUD for ENT-10 Employee Grade (who creates/manages grade records in the system is undefined — BQ-02)

---

## Future Expansion
Will be updated once MTN Sudan provides employee grade levels, destination pricing rates, and HR reporting requirements. The data model for ENT-09's Line Manager relationship and role-assignment mechanism also requires clarification.
