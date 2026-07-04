# Example User Stories (Sanitized)

## Purpose
Illustrates correctly structured User Stories using a generic, non-confidential scenario.

## Scope
Covers a generic 'Purchase Order Approval' example scenario only.

## Intended Usage
Use as a structural reference for Title, Acceptance Criteria, Priority, Dependencies, and Business Rules formatting.

## Example Story

**Title:** As an Approver, I want to review a pending purchase order, so that I can approve or reject it within SLA.

**Acceptance Criteria:**
- Given a pending PO assigned to me, When I open it, Then I see the requester, amount, and line items.
- Given I approve the PO, When I submit my decision, Then the PO status changes to Approved and the requester is notified.

**Priority:** High | **Dependencies:** Notification Service | **Business Rules:** Second-level approval required above threshold (illustrative).

## Future Expansion
Will be expanded with additional example stories covering rejection and escalation flows.
