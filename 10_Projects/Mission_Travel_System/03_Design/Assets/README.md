# Assets

## Purpose
Provides a designated location for binary/visual artifacts referenced by this project's Design deliverables (and, by reference, its BRD/FRD), so they do not end up scattered or embedded ad hoc.

## Scope
Applies to this specific project workspace only.

## Intended Usage
Place exported files in the matching subfolder and reference them by relative path from the deliverable that uses them (e.g. a BRD's Process Flow section linking to `Assets/Diagrams/AS-IS_Approval_Flow.png`):
- `Diagrams/` — exported Mermaid/BPMN process flow images
- `Screenshots/` — existing-system screenshots gathered during discovery
- `Mockups/` — Figma/UI mockup exports
- `Icons/` — icon assets used in mockups or presentations

## Contents

### Diagrams/
Exported process flow diagrams (AS-PROPOSED versions, retained for traceability):
- `Process_Flow_AS_PROPOSED.png` — initial process flow shared with MTN Sudan for validation (`MTN_Travel_Process_Flow.docx`)
- `Process_Flow_AS_PROPOSED_Abdullah.png` — variant process flow diagram from `Process_Flow_abdullah.png` in project files

### Screenshots/
Lovable UI prototype screenshots captured ~30 June 2026, referenced in [../Screen_Inventory.md](../Screen_Inventory.md) and [../MTN_Travel_System_Figma_Spec.md](../MTN_Travel_System_Figma_Spec.md):
- Dashboard, Create Mission, Mission List, My Missions, Approvals, Travel Review, GL Review, Mission Closure, Settlements, Payments, Settlement Detail, Mission Extensions, Reports (Employee History, Debit/Credit), individual Mission details
- Teams screenshots: `Screenshot_20260628_161108_Teams.jpg` (28 Jun 2026 SharePoint screenshot), `Screenshot_20260630_103815.png`

### Mockups/
- `MTN_Travel_System_UX_Design.html` — initial HTML UX prototype (pre-correction version; 10 known issues identified in [../MTN_Travel_System_Figma_Spec.md](../MTN_Travel_System_Figma_Spec.md) Phase 1 Audit — use for historical reference only, not as the current design baseline)

### Icons/
- `mtn_logo.jpg` — MTN brand logo asset (prepared by Asmaa Hamrawy per `mom_daily_6-28.docx` Daily Scrum Decision D-12)

## Future Expansion
Will accumulate project-specific assets; a naming convention for asset files may be added to [02_Standards/Naming_Convention.md](../../../../02_Standards/Naming_Convention.md) if patterns recur across projects.
