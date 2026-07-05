# UAT Scenarios — MTN Sudan Travel Mission Management System

## Purpose
User Acceptance Testing scenarios per [05_Templates/UAT_Template.md](../../../05_Templates/UAT_Template.md) and [06_Playbooks/UAT_Playbook.md](../../../06_Playbooks/UAT_Playbook.md). Reproduces and extends the UAT scenarios from `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 8.

## Scope
Covers confirmed scenarios only. Scenarios for BLOCKED or MISSING INFORMATION features are marked accordingly.

---

## UAT-EP04-LM-001 — Line Manager Approves Mission

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP04-LM-001 |
| **Scenario Name** | Line Manager Approves Mission Request |
| **Related User Story** | US-EP04-LM-001 |
| **Source** | `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 8 |
| **Preconditions** | A mission exists with status "Pending Line Manager Approval". User is logged in as Line Manager. |

**Steps:**
1. Navigate to Pending Approvals.
2. Select the mission. Review Mission ID, Employee Name, Destination, Dates, Type.
3. Click Approve. Add optional note. Confirm.

**Expected Result:** Mission status = Pending Division Manager Approval. Division Manager receives email notification. Mission no longer appears in LM Pending Approvals list.

**Negative Test:** Attempt to Reject without entering a reason note → system displays validation error and prevents rejection.

---

## UAT-EP04-LM-002 — Line Manager Rejects Mission

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP04-LM-002 |
| **Scenario Name** | Line Manager Rejects Mission Request |
| **Related User Story** | US-EP04-LM-001 |
| **Preconditions** | Mission in status "Pending Line Manager Approval". User logged in as Line Manager. |

**Steps:**
1. Navigate to Pending Approvals.
2. Select the mission.
3. Click Reject. Enter mandatory reason note. Confirm.

**Expected Result:** Mission status = Rejected. Assigned Person receives email notification. Mission no longer appears in LM Pending Approvals.

---

## UAT-EP03-CR-001 — Mission Creation (National)

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP03-CR-001 |
| **Scenario Name** | Create and Submit National Mission |
| **Related User Story** | US-EP03-CR-001 |
| **Source** | MoM §1–§4; source-of-truth v3 EP-03 |
| **Preconditions** | User logged in as Assigned Person. No other open mission exists for the traveling employee. Destination list is configured. |

**Steps:**
1. Navigate to Create Mission.
2. Select Mission Type = National. Observe Currency auto-populates as SDG.
3. Select Mission Category = Training (or Conference or Job Mission).
4. Select Destination from list.
5. Enter Assigned Person and Employee Name (may be different people).
6. Enter Start Date and End Date (End Date > Start Date).
7. Enter Mission Purpose.
8. Upload at least one supporting document.
9. Click Submit.

**Expected Result:** Mission status = Pending Line Manager Approval. Line Manager receives email notification. Mission appears in Mission List with correct status.

**Negative Test 1:** Enter End Date < Start Date → validation error prevents submission.
**Negative Test 2:** Leave mandatory field blank → validation error on that field prevents submission.
**Negative Test 3:** Submit for an Employee who already has an open mission → BR-01 error prevents submission.

---

## UAT-EP03-CR-002 — Save Mission as Draft

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP03-CR-002 |
| **Scenario Name** | Save Mission Request as Draft |
| **Preconditions** | User logged in as Assigned Person. |

**Steps:**
1. Navigate to Create Mission.
2. Enter partial information.
3. Click Save Draft.

**Expected Result:** Mission saved with status = Draft. Mission appears in My Missions and Mission List with Draft status. Mission does NOT appear in any approver's Pending Approvals.

---

## UAT-EP03-CR-003 — International Mission Currency

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP03-CR-003 |
| **Scenario Name** | International Mission Auto-sets USD |
| **Preconditions** | User logged in as Assigned Person. |

**Steps:**
1. Navigate to Create Mission.
2. Select Mission Type = International.

**Expected Result:** Currency field auto-populates as USD and is read-only (not editable by the user).

---

## UAT-EP05-TR-001 — Travel Team Reviews Mission Cost

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP05-TR-001 |
| **Scenario Name** | Travel Team Enters and Submits Mission Costs to GL Review |
| **Source** | MoM §6; source-of-truth v3 EP-05 |
| **Preconditions** | Mission in status "Pending Travel Review". User logged in as Travel Team Member. |
| **Blocked?** | Partially — cost auto-calculation is BLOCKED pending formula confirmation (BQ-03, BQ-04); manual value entry can be tested |

**Steps:**
1. Navigate to Travel Cost Review.
2. Select the pending mission.
3. Enter Per Diem amount, Accommodation Cost, Other Expenses.
4. Review the cost summary.
5. Click Submit to GL Review.

**Expected Result:** Mission status changes to Pending GL Review. GL Team receives email notification.

**Negative Test:** Attempt to Submit to GL without entering Per Diem → behavior MISSING INFORMATION (mandatory field rules for Travel Review not explicitly documented — flagged as CQ).

---

## UAT-EP06-GL-001 — GL Team Reviews and Submits to Treasury

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP06-GL-001 |
| **Scenario Name** | GL Team Validates Costs and Submits to Treasury |
| **Source** | MoM §7; source-of-truth v3 EP-06 |
| **Preconditions** | Mission in status "Pending GL Review". User logged in as GL Team Member. |

**Steps:**
1. Navigate to GL Review (Pending GL Requests).
2. Review the cost details.
3. Add GL Notes (optional).
4. Click Submit to Treasury.

**Expected Result:** Mission status = Pending Payment. Treasury Team receives email notification.

**Negative Test:** GL Reject with mandatory note → status = Rejected; Assigned Person notified.

---

## UAT-EP07-TR-001 — Treasury Confirms Payment

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP07-TR-001 |
| **Scenario Name** | Treasury Confirms Mission Payment — No Reject Action |
| **Source** | MoM §8; source-of-truth v3 EP-07; US-EP07-TR-001 |
| **Preconditions** | Mission in status "Pending Payment". User logged in as Treasury Team Member. |

**Steps:**
1. Navigate to Payments.
2. Select the pending mission.
3. Enter Payment Reference and Payment Date.
4. Optionally add Treasury Notes.
5. Click Confirm Payment.

**Expected Result:** Mission status = Mission Active. Employee is notified by email. Mission no longer appears in Pending Payments.

**Constraint Verification:** Confirm that no "Reject" button or action exists on this screen (BR-05 verification).

---

## [NEW] UAT-EP-NEW01-HR-001 — HR Approves International Mission

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP-NEW01-HR-001 |
| **Scenario Name** | HR Approves International Mission |
| **Source** | `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 8; second-session transcript |
| **Status** | NEEDS CLARIFICATION — pending BQ-01 resolution |
| **Preconditions** | International Mission in status "Pending HR Approval". User logged in as HR Team Member. |

**Steps:**
1. Navigate to Pending Approvals (HR view).
2. Review mission details including destination, employee, dates, type (International).
3. Click Approve. Mission progresses.

**Expected Result:** Mission status = Pending Travel Review. Travel Team receives email notification.

**Edge Case — National Mission Excluded:** A National mission should NOT appear in HR Pending Approvals; only an informational notification is sent. Verify HR cannot take an approval action on National missions.

**Negative Test:** HR Reject with mandatory note → status = Rejected; Assigned Person notified.

---

## [UPDATED] UAT-EP08-EXT-001 — Mission Extension Recalculates Costs

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP08-EXT-001 |
| **Scenario Name** | Mission Extension with Cost Recalculation and Audit Record |
| **Source** | `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 8; MoM §10 |
| **Status** | BLOCKED — cost formula unconfirmed (BQ-03, BQ-04) |
| **Preconditions** | Mission in status "Mission Active". Pricing matrix configured (sample data acceptable for POC). User = Assigned Person. |

**Steps:**
1. Navigate to Mission Extensions.
2. Click Request Extension.
3. Enter New End Date (later than current End Date).
4. Enter Extension Reason.
5. Observe system calculates Extension Days and shows new Per Diem + Accommodation totals.
6. Submit.

**Expected Result:**
- Extension request enters full approval chain (LM → DM → HR if International → Travel → GL → Treasury).
- "Extended By" field records the submitting user's identity and submission timestamp.
- Previous end date and costs remain in the Approval History for audit.

**Negative Test:** Enter New End Date earlier than or equal to current End Date → validation error; system prevents submission.

---

## UAT-EP10-FIN-001 — Finance Processes Settlement

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP10-FIN-001 |
| **Scenario Name** | Finance Processes Mission Settlement (Debit Scenario) |
| **Source** | MoM §11; source-of-truth v3 EP-10 |
| **Preconditions** | Mission in status "Pending Settlement" (Closure has been submitted). User logged in as Finance. |

**Steps:**
1. Navigate to Settlements.
2. Select the mission.
3. Review planned costs (read-only).
4. Enter Actual Per Diem, Actual Accommodation, Actual Other Expenses.
5. Observe Balance = Actual Total − Amount Already Paid.
6. Enter Settlement Reference.
7. Click Process Settlement.

**Expected Result:** Mission status = Completed. Balance displayed:
- Balance > 0 → "Employee owes company" displayed.
- Balance < 0 → "Company owes employee" displayed.
- Balance = 0 → "No balance due" displayed.

---

## UAT-EP13-SEC-001 — Role-Based Access Control

| Field | Value |
|---|---|
| **Scenario ID** | UAT-EP13-SEC-001 |
| **Scenario Name** | Role-Based Screen Restriction |
| **Source** | MoM §5; source-of-truth v3 EP-13 |
| **Preconditions** | Test users provisioned with different roles via Microsoft 365 / Azure AD. |

**Steps:**
1. Log in as an Assigned Person. Confirm Mission Creation, My Missions screens are accessible. Confirm GL Review, Treasury, Finance Settlement screens are NOT accessible.
2. Log in as a Line Manager. Confirm Pending Approvals (LM stage) is accessible. Confirm Treasury and Finance screens are NOT accessible.
3. Log in as Treasury. Confirm Payments screen is accessible. Confirm Create Mission and GL Review screens are NOT accessible.
4. Confirm that deactivating a user's Microsoft 365 account removes their system access without any manual system action required.

**Expected Result:** Each role sees only the screens and actions permitted by their role definition. Unauthorized menu items are hidden. M365 deactivation automatically removes access.

---

## UAT Scenarios Pending Clarification / BLOCKED

| Scenario ID | Topic | Status | Blocking Item |
|---|---|---|---|
| UAT-EP-NEW02-GRD-001 | Grade-based Accommodation Rate auto-applied in Travel Review | BLOCKED | BQ-02 — grade levels/rates not provided |
| UAT-EP09-CAN-001 | Mission Cancellation rules and advance recovery | MISSING INFORMATION | BQ-06 — cancellation rules not defined |
| UAT-EP11-HR-001 | HR Reporting requirements | MISSING INFORMATION | BQ-08 — HR workshop not held |
| UAT-EP05-DEST-001 | Destination Pricing Configuration screen | MISSING INFORMATION | GAP-04 — screen not defined |

## Future Expansion
Additional scenarios will be authored as BLOCKED/MISSING INFORMATION items are resolved. UAT sign-off artifacts will be recorded in [../06_Handover/KT_Checklist.md](../06_Handover/KT_Checklist.md).
