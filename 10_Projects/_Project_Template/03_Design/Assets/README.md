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

## Future Expansion
Will accumulate project-specific assets; a naming convention for asset files may be added to [02_Standards/Naming_Convention.md](../../../../02_Standards/Naming_Convention.md) if patterns recur across projects.
