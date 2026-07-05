# Minutes of Meeting Log — MTN Sudan Travel Mission Management System

## Purpose
Running, append-only log of MoM entries for this project, per [05_Templates/MOM_Template.md](../../../05_Templates/MOM_Template.md).

## Scope
Covers every meeting evidenced in uploaded artifacts: client validation sessions and internal daily scrums, 01 June 2026 – 30 June 2026.

## Intended Usage
Append new dated entries below. Do not overwrite prior entries.

---

## Entry 1 — Client Validation Session (First Workshop)
**Date:** Not explicitly dated in the MoM document itself. Related email evidence (`pdf_extract/doc1/8.txt`) places the associated MoM email transmittal on **3 June 2026** ("Please find attached the Minutes of Meeting (MoM) for our recent session"), referencing a meeting agreed for "tomorrow 3-6-2026" per `pdf_extract/doc1/9.txt`.
**Attendees:** NOT DISCUSSED in the MoM document (no attendee table present in `Minutes_of_Meeting___MTN_Travel_Mission_Management_System.docx`). Related email thread cc's: Muhanad Elnayeer, El Waleed Abdelgadir Mohamed, Faten Elgamal, Abduallah Hamad, Mostafa Abdelmageed, Huda Mohamed Ahmed (Finance), Abeer Homida Satti (Finance).
**Agenda:** "Review and validate the proposed workflow, business requirements, and Prototype of the Travel Mission Management System." (`Minutes_of_Meeting___MTN_Travel_Mission_Management_System.docx`)
**Discussion Summary:** Confirmed end-to-end workflow (Mission Request → LM Approval → DM/GM Approval → Travel Review → GL Review → Treasury Payment → Mission Active → Mission Extension (Optional) → Mission Closure → Finance Settlement → Mission Completed); Employee Name vs. Assigned Person distinction; Mission Categories (Training, Conference, Job Mission); Mission Types (National/International) and currency logic (SDG/USD); Per Diem/Accommodation calculation approach (days/nights-based, exact formula pending); Roles & permissions; Travel Review and GL Review responsibilities; Treasury process (payment only, no approve/reject); Notifications; Mission Extension recalculation and audit ("Extended By"); Mission Closure & Settlement timing; HR participation to be scheduled; Microsoft 365/SharePoint platform preference confirmed.
**Decisions:** See [Decision Log](Decision_Log.md) entries D-01 through D-09.
**Action Items:** See [Action Log](Action_Log.md) entries A-01 through A-06.
**Risks / Open Items:** See [RAID Log](RAID_Log.md) — Destination Pricing Matrix, Per Diem Formula, Accommodation Formula, HR Notification Requirements, HR Reporting & Visibility Requirements (all Owner: MTN Sudan).
**Open Questions:** Exact Per Diem/Accommodation formulas and destination-based pricing matrix were NOT provided in this session ("The exact calculation formulas and destination-based pricing matrix will be provided by MTN Sudan.")
**Next Steps:** Update prototype per feedback; configure workflow updates; hold HR workshop; continue refinement.

---

## Entry 2 — Second Client Session (HR / Grading Discussion)
**Date:** 11 June 2026 (per `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx`, which cites "Meeting Transcript 11/06/2026" throughout; the raw audio file is named `last meeting_11062026.mp3` per `Minutes_of_Meeting___MTN_Travel_Mission_Management_System_2.docx`).
**Attendees:** NOT DISCUSSED as a formal attendee table. Transcript indicates multiple numbered speakers (Speaker 1–8); the source-of-truth document identifies content attributable to "Shatha" and "Moez" (HR discussion) but a fully confirmed attendee list is not present in any uploaded artifact.
**Status of this entry:** **NO formal, distilled Minutes-of-Meeting document exists for this session.** The only artifacts are: (a) the raw, untranslated meeting transcript (`Minutes_of_Meeting___MTN_Travel_Mission_Management_System_2.docx` — despite its filename, this file's content is a raw transcript, not formal minutes), and (b) the synthesis of that transcript performed in `APPROVED_SOURCE_OF_TRUTH_MTN_Travel_v3_docx.docx` Section 1.2 ("New Requirements Identified from ... Second Meeting Transcript"). This log entry reproduces only what that synthesis states, with its own timestamp citations preserved.
**Discussion Summary (per source-of-truth synthesis, with original timestamp citations):**
- HR must **approve** International missions (not merely be notified) — Transcript §4:06–§11:21.
- HR must be **notified** (email) for National missions — Transcript §9:55–§11:03.
- Employee Grade/Level determines Accommodation rate (Level 2 to Level 3H referenced) — Transcript §48:55–§50:36.
- Destination-based pricing matrix — rates differ by destination (Darfur cited as a higher-rate example) — Transcript §53:04–§53:49.
- Mission cancellation before departure raised — Transcript §52:24 (rules not defined).
- User provisioning is via Microsoft 365 — no manual add/remove screen needed — Transcript §7:59–§8:57.
**Decisions:** None formally recorded as "decisions" in this session per the available evidence; items above are captured as **new requirements pending confirmation**, not settled decisions. See [RAID Log](RAID_Log.md) items R-06 through R-11.
**Action Items:** NOT DISCUSSED as a distinct list for this session.
**Risks:** See RAID Log.
**Open Questions:** BQ-01 through BQ-09 in the source-of-truth document — see [Clarification Register](../02_Requirements/Clarification_Register.md).
**Next Steps:** MTN Sudan to confirm HR workflow placement, grade/rate matrix, destination pricing, and cancellation rules.

---

## Entry 3 — Daily Scrum, 28 June 2026
**Date/Time:** 28 June 2026, meeting invite sent 12:05 PM (`Outlook_Document1.PDF`); minutes captured in `mom_daily_6-28.docx`.
**Attendees:** Mohamed Bayoumi (Backend Dev), Hassan Mohamed (Front-End Dev), Mostafa Abdelmageed (Team Lead), Asmaa Hamrawy (UX/UI Senior), Walaa Hamdy (Backend Team Lead), Abdelrahman Hamdy (QA), Shehabeldin Yehia (PO, Facilitator).
**Agenda:** Sprint 1 kickoff daily standup — progress since last update, today's planned work, blockers.
**Discussion Summary:** Hassan completed portal structure setup, confirmed group-based access control approach (dedicated SharePoint/portal group; non-members have no access). Bayoumi completed list/library configuration for the Mission module; minor adjustments pending Walaa's confirmation. Walaa identified additional list-structure items pending alignment with Bayoumi. Abdelrahman (QA) received handover from Engineer Omar and completed form test cases. Asmaa has MTN Figma brand assets (logo, colors) ready to share; Figma subscription needed for Lovable→Figma browser extension, pending Abdullah's availability. Mostafa found a Lovable-to-Figma conversion method and will test it.
**Decisions:** See Decision Log D-10 through D-12.
**Action Items:** See Action Log A-07 through A-13.
**Risks / Blockers:** Figma subscription dependency on Abdullah's availability (workaround in progress by Mostafa); list-structure additions not yet confirmed, blocking Hassan.
**Open Questions:** None recorded beyond the blockers above.
**Next Steps:** Walaa/Bayoumi finalize list structure and notify Hassan; Shehabeldin to send Lovable link to Mostafa; Asmaa to share brand assets; Mostafa to test Figma conversion; Abdelrahman to continue QA and escalate unclear items.

---

## Entry 4 — Daily Scrum, 29 June 2026
**Date/Time:** 29 June 2026, 12:01 PM UTC, ~4 minutes (`MOM_Daily_Scrum_29June2026.docx`).
**Attendees:** Hassan Mohamed (Present), Mohamed Bayoumi (Present), Abdelrahman Hamdy (Present), Shehabeldin Yehia (Absent — facilitator not present; recorded by auto-transcript).
**Agenda:** Daily Scrum, Sprint 1 (28 Jun – 12 Jul 2026).
**Discussion Summary:** Hassan started design work on the Create Mission screen (timestamp 1:47). Bayoumi made adjustments to the Destination list with Hassan (timestamps 1:21–1:40). Abdelrahman completed test cases for the Mission module (timestamp 2:03). Sprint 1 scope confirmed in-meeting: Mission Log List, Create Mission, My Mission, Mission Extension (timestamp 2:29; extension confirmed to extend duration, timestamp 2:50).
**Decisions:** None recorded as formal decisions beyond scope confirmation above.
**Action Items:** A-01 (this entry's own numbering, per source document) Resolve Group configuration to unblock Create Mission development — Owner Hassan Mohamed, Due NOT DISCUSSED, Status Open. A-02 Deliver Create Mission design work — Owner Hassan Mohamed, Due "Possibly tomorrow or day after" (source document's own qualifier — not a confirmed date), Status Open. Mapped to [Action Log](Action_Log.md) A-14, A-15.
**Risks / Blockers:** B-01 — Group configuration not yet resolved, blocking Create Mission development (Owner: Hassan Mohamed). Carried forward — see Action Log A-14 and RAID Log R-12.
**Needs Clarification (per source document, LOW-confidence items correctly excluded from confirmed content):**
- C-01: Can Mission Extension include an additional financial amount (in addition to duration)? Hassan confirmed only duration; amount not confirmed or denied explicitly.
- C-02: Is the Create Mission screen's UI color/styling aligned with the approved reference design? Hassan stated adjustments are in progress.
**Next Steps:** NOT DISCUSSED beyond the action items above.

---

## Entry 5 — Daily Scrum, 30 June 2026
**Date/Time:** 30 June 2026, 12:00 PM UTC, 4m 2s (`Daily_Scrum_Meeting___mtn_mission_system____1_.docx` — raw transcript only; no separately distilled MoM document exists for this date).
**Attendees (per transcript):** Abdelrahman Hamdy, Hassan Mohamed. (Bayoumi referenced but did not audibly respond per transcript content.)
**Agenda:** Daily Scrum.
**Discussion Summary:** Per raw transcript — Hassan stated he is working on "the subscription for the project as a whole" (informal translation of Arabic transcript content) and continuing prior work. Abdelrahman confirmed he completed "Create" work and had begun writing test cases including headset case and "MyMission." Abdelrahman asked whether recent items required test-case changes. Hassan indicated no changes needed on his side. Abdelrahman mentioned he would be on leave the next day and asked Hassan to flag him if anything was unclear.
**Decisions:** NOT DISCUSSED — no decisions were explicitly confirmed in this transcript.
**Action Items:** NOT DISCUSSED as an explicit list; informal continuation of prior-day work only.
**Risks:** NOT DISCUSSED explicitly in this transcript (source contains an ambiguous, untranslated exchange about a "blocker" that could not be confidently classified — flagged as **LOW CONFIDENCE**, moved to [Clarification Register](../02_Requirements/Clarification_Register.md) rather than presented as a confirmed fact).
**Next Steps:** NOT DISCUSSED.

## Future Expansion
Additional entries will be appended as further meetings occur (e.g. formal MTN Sudan HR workshop, Sprint 1 review, Sprint 2 planning).
