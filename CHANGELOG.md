# Changelog

All notable changes to this repository are documented here.
This project follows a simplified [Keep a Changelog](https://keepachangelog.com/) style.

## [1.1.0] - 2026-07-04
### Added
- Persistent Governance layer inside `_Project_Template` (`00_Governance/`): MOM Log, Decision Log, RAID Log, Action Log — cross-phase artifacts previously unhoused.
- Handover phase inside `_Project_Template` (`06_Handover/`): KT Plan, KT Checklist, KT Signoff.
- Assets structure inside `_Project_Template/03_Design/Assets/`: Diagrams, Screenshots, Mockups, Icons subfolders for binary/visual artifacts.
- `Project_Metadata.md` at the project template root, capturing Client, Delivery Company, Branding, Engagement Type, Phase, and role ownership per project.
- `11_Reference/Future_Roadmap.md`, documenting deferred v2.0 plans for YAML front matter, stable document IDs, versioning, AI indexing, and automated validation.
### Changed
- `10_Projects/_Project_Template/README.md` and `03_Design/README.md` updated to reference the new folders/files.
- `11_Reference/README.md` updated to list `Future_Roadmap.md`.
### Notes
- No existing folders renamed, no existing files moved or rewritten. Fully backwards compatible with v1.0.0.

## [1.0.0] - 2026-07-04
### Added
- Initial repository scaffold: full folder structure (00_System through 99_Archive).
- Core system instructions, output standards, document standards, project rules, quality gates, glossary, and AI workflow.
- Role definitions for all nine personas.
- Documentation and engineering standards (BRD, FRD, User Stories, Acceptance Criteria, Azure DevOps, Naming Convention, API Standards, UI/UX, Security).
- Frameworks, Skills, Templates, Playbooks, Prompts, Checklists, Examples, Projects, Reference, and Archive folders with initial content.
