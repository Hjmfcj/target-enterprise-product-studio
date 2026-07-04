# Contributing Guide

## Purpose
Defines how contributors add, modify, or retire content in this repository so that it remains consistent, traceable, and enterprise-grade.

## Scope
Applies to all folders and file types in this repository (Markdown documents, templates, prompts, examples).

## Intended Usage
1. New documents must use the standard structure: **Purpose, Scope, Intended Usage, Future Expansion** (plus any folder-specific sections).
2. Place new files in the correct numbered folder — do not create new top-level folders without updating the root `README.md` map.
3. Every new template or standard must be linked from its folder's `README.md`.
4. Do not delete content — move superseded material to `99_Archive/` with a note on why it was archived.
5. Follow naming convention: `Title_Case_With_Underscores.md`.
6. All BA/PO content must comply with the No-Assumptions and Source-Driven rules in [00_System/04_Project_Rules.md](00_System/04_Project_Rules.md).
7. Open a pull request against the default branch; describe what changed and why.

## Future Expansion
As the repository grows past hundreds of documents, this guide will be extended with automated linting (markdown-lint), a documentation review board process, and templated PR checklists.
