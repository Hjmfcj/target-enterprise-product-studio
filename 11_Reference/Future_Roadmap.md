# Future Roadmap

## Purpose
Documents structural evolution deliberately deferred out of the current repository version, so that decisions not to implement something now are recorded rather than lost, and so future work has a stated direction to build toward.

## Scope
Applies repository-wide. Covers evolution of the repository's own structure and tooling — not project content.

## Intended Usage
Consult before proposing a new metadata, versioning, or automation mechanism, to check whether it is already planned and under what scope. Update this document (not silently) whenever a deferred item is scheduled, changed, or superseded.

## Deferred to Repository Version 2.0

### 1. YAML Front Matter
Each Markdown file will gain a front-matter block, e.g.:
```yaml
---
id: STD-BRD-001
title: Business Requirements Document Standard
type: Standard
owner: TBD
version: 1.0
status: Active
last_reviewed: TBD
---
```
This repository intentionally does not implement front matter in v1.x, to keep the initial content-authoring phase focused on substance over tooling. Front matter is deferred, not rejected.

### 2. Stable Document IDs
Every Standard, Template, Skill, Playbook, and Prompt will receive a stable ID (e.g. `STD-BRD-001`, `TPL-UAT-004`) independent of filename or folder position, so that references (in RTMs, backlog items, or the Governance logs introduced in v1.1) survive future renames or reorganizations.

### 3. Versioning Model
A per-file `version` field (front matter) plus a repository-wide semantic version (already tracked in [CHANGELOG.md](../CHANGELOG.md)) will allow individual documents to evolve independently while the repository as a whole tracks a release history.

### 4. AI Indexing
Once IDs and front matter exist, an index (generated, not hand-maintained) will allow an AI assistant to enumerate "all Active Standards," "all Templates referencing Azure DevOps," etc., programmatically rather than by reading folder READMEs. This depends on items 1–3 above being in place first.

### 5. Automated Validation
Once structure stabilizes: markdown-lint, a check that every file has the mandatory Purpose/Scope/Intended Usage/Future Expansion sections, and a check that every folder's README `Contents` list matches its actual file listing.

## Not Deferred (Already in v1.1)
For contrast — items addressed directly in Repository Structure v1.1 rather than deferred: the persistent Governance layer, the Handover phase, the Assets structure, and per-project metadata (Client/Branding/Roles). These were judged to affect content correctness now (especially branding, which must never be assumed), whereas items above are tooling/automation concerns that do not block correct content authoring.

## Future Expansion
This roadmap itself will be revised as v2.0 planning firms up; items may move from "deferred" to "in progress" to a dedicated CHANGELOG entry.
