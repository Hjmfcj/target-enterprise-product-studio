# Discovery Notes — MTN Sudan Travel Mission Management System

## Purpose
Synthesizes raw discovery inputs (initial requirements brief, process flow proposal, UI prototype, meeting transcripts) into structured discovery findings, ahead of formal requirements validation in [02_Requirements](../02_Requirements/README.md).

## Scope
Covers the pre-Sprint discovery period. Does not restate governance items already tracked in [00_Governance](../00_Governance/README.md) — see that folder for MOM/Decision/RAID/Action logs.

## System Overview (as initially proposed)
Source: `Travel_System_Requirements.docx`.

> The system manages employee travel missions from request creation until financial settlement and closure. Mission Types: National, International. The system automates approvals, travel cost calculation, payment processing, mission closure, and financial settlement.

## Initial Proposed Workflow (pre-validation)
Source: `MTN_Travel_Process_Flow.docx` / `Process_Validation_Document_.docx` (identical process flow diagram in both, shared by Target with MTN Sudan for review):

1. Assigned Person creates a Mission Request.
2. Line Manager reviews and approves/rejects.
3. Division Manager reviews and approves/rejects.
4. Travel Team reviews the mission and enters travel-related costs (Per Diem, Accommodation, Visa Cost, Taxi Cost, Other Expenses — per `MTN_Travel_Process_Flow.docx`; the `Process_Validation_Document_.docx` version of the same diagram lists only Per Diem and Accommodation under Travel Team Review — **discrepancy between the two source diagrams; Visa Cost and Taxi Cost do not reappear in any later validated document and are therefore NOT carried into the requirements baseline** — see Clarification Register).
5. Treasury processes the mission payment.
6. Employee performs the mission (Mission Active).
7. Mission Extension optional.
8. Assigned Person closes the mission, uploads supporting documents.
9. Finance performs settlement (Debit/Credit review).
10. Mission Completed.

Rejection path (as originally proposed, before GL Review was added): Line Manager Reject → Rejected; Division Manager Reject → Rejected.

**Note — this initial flow was subsequently corrected in the validated MoM (see [00_Governance/MOM_Log.md](../00_Governance/MOM_Log.md) Entry 1 / Decision D-06): GL Review was inserted between Travel Review and Treasury Payment. This Discovery Notes section is preserved as the AS-PROPOSED / pre-validation baseline; the [BRD AS-IS/TO-BE](../02_Requirements/BRD.md) reflects the validated version.**

## UI Prototype Reference
`https://mtn-sudan-mission-forge.lovable.app` — shared with MTN Sudan on 1 June 2026 (`pdf_extract/doc1/11.txt`: "please find below the initial UI Prototype and attached Process Flow"). Screenshots of this prototype (as later reviewed on 30 June 2026 per file timestamps) are retained in [03_Design/Assets/Screenshots](../03_Design/Assets/Screenshots/).

## Initial Business Controls Discussed (pre-validation)
Source: `Travel_System_Requirements.docx`, `Process_Validation_Document_.docx`:
- Employee cannot have more than one open mission at a time.
- National and International missions supported.
- National missions use local currency; International missions use foreign currency.
- Destination list is configurable.
- Mission Extension is supported.
- Long-term missions are handled as separate monthly missions.

## Initial Navigation / Screen Inventory Candidates (pre-validation)
Source: `Travel_System_Requirements.docx` — carried forward into [03_Design/Screen_Inventory.md](../03_Design/Screen_Inventory.md) after validation against the confirmed workflow.

## Initial Roles Identified (pre-validation)
Source: `Travel_System_Requirements.docx`: Assigned Person, Line Manager, Division Manager, Travel Team, Treasury, Finance, HR.
**Note:** This list already includes HR and Finance as of the initial requirements document, even though the formal MoM (Session 1) roles list (§5) names only: Mission Creator / Line Manager / Division Manager-GM / Travel Team / GL Team / Treasury Team — omitting Finance and HR. This is the origin of RAID item R-11 (Finance vs. GL Team) and the reason HR involvement required a dedicated follow-up session.

## Client Communication Timeline (from email evidence)
| Date | Event | Source |
|---|---|---|
| 1 Jun 2026 | Target shares initial UI Prototype + Process Flow with MTN Sudan for review | `pdf_extract/doc1/11.txt` |
| 2 Jun 2026 | MTN Sudan (Muhanad Elnayeer) responds positively; meeting proposed | `pdf_extract/doc1/9.txt` |
| 3 Jun 2026 (proposed) | Session held; MoM subsequently shared | `pdf_extract/doc1/8.txt` |
| 8–9 Jun 2026 | Follow-up scheduling for updated-prototype review session | `pdf_extract/doc1/6.txt`, `7.txt` |
| 10 Jun 2026 | Teams meeting held ("Travelling ERP") — attendees list includes Finance and HR contacts at MTN Sudan for the first time in the email chain | `pdf_extract/doc1/5.txt` |
| 11 Jun 2026 | Second validation session held (audio: `last meeting_11062026.mp3`) — HR approval and employee-grading requirements surface | `Minutes_of_Meeting___MTN_Travel_Mission_Management_System_2.docx` |
| 22 Jun 2026 | Source-of-truth v3 document dated ("Post-Backlog Analysis") | `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` |
| 28 Jun 2026 | Sprint 1 begins; POC development starts at Dev Site | `Outlook_Document1.PDF`; `pdf_extract/doc1/1.txt` |
| 29 Jun 2026 | Target requests SharePoint POC environment + test user accounts from MTN Sudan; proposes Milestone 1 (15 Jul 2026) delivery plan and sample-data approach for cost formulas | `629_email_request_enviroment_from_muhanad_and_alignment_on_phase_1.pdf` |

## Unresolved Discovery-Level Item
**MISSING INFORMATION – BUSINESS CLARIFICATION REQUIRED**: The raw transcript `Session_25May2026_Earlier_Meeting_Transcript_Raw.docx` (audio file dated 25 May 2026) could not be confidently mapped to a specific distilled MoM or a specific position in the timeline above, because it contains no explicit date/attendee header and was not directly cited by document/timestamp in the approved source-of-truth v3 document (which cites only the 11 June 2026 session by name). It is retained in `Raw_Transcripts/` for completeness and traceability, but no requirements in this workspace are attributed to it beyond what is independently corroborated by other, dated sources.

## Future Expansion
Will accumulate further discovery artifacts as the HR workshop and any subsequent discovery sessions occur.
