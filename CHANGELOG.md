# Changelog

All notable changes to Skill Metadata Protocol are recorded here.

The format is based on [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/) and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

The `schema_version` field in `schemas/skill.vN.schema.json` tracks contract shape (currently `6`). This changelog tracks the npm package `@skill-graph/protocol` as a whole — the spec, the schemas, and the docs. The two are intentionally distinct: see ADR 0007 for the source-of-truth split.

## [1.3.0] — 2026-05-17

### Added

- **`schema_version: 6`.** The protocol's sixth contract shape. Promotes the seven nested `concept.*` sub-fields to flat top-level fields (`mental_model`, `purpose`, `boundary`, `analogy`, `misconception`; `definition` collapses into `description`; `taxonomy` collapses into `category` + `relations.broader`) and introduces the seven-field flat Health Block (`last_audited`, `last_changed`, `audit_verdict`, `eval_score`, `eval_failed_ids`, `lint_verdict`, `drift_status`) so a skill's audit fingerprint lives in its own frontmatter instead of scattered log files.
- **`schemas/skill.v6.schema.json` + `schemas/manifest.v4.schema.json`.** Pinned v6 schema files. The unversioned `schemas/skill.schema.json` mirror now tracks v6.
- **`docs/migrations/v5-to-v6.md`.** Author-facing migration procedure: what changed, conditional edits, codemod commands, verification checklist, and rollback procedure. Covers the flat-fields flattening, the Health Block, and the SAME-DOMAIN `relations.boundary[]` doctrine.
- **`docs/adr/0007-version-source-of-truth.md`.** Codifies where the schema version and package versions live across the four-repo set (`skill-metadata-protocol`, `skill-graph`, `skill-audit-loop`, `skills`).

### Changed

- **Comprehension-state `allOf` rule accepts either shape.** v5 required the nested `concept` block when `comprehension_state: present`; v6 changes the rule to `anyOf` — the author can satisfy the requirement by populating the five flat Understanding fields (preferred), the nested `concept` block (v5 back-compat), or both. Flat fields win when both are present.
- **Cross-Domain Boundary Doctrine codified.** `relations.boundary[]` entries should declare same-domain handoffs only. Cross-category or cross-sub-domain handoffs belong in `anti_examples` + `relations.related`. See `docs/migrations/v5-to-v6.md` § "Cross-Domain Boundary Doctrine" for the runtime mechanic and the empirical justification (Tier C″ sweep, 2026-05-17 — 16 cross-domain entries removed across 8 Wave 6 skills caused 0 top-1 routing changes).

### Deprecated

- **Nested `concept` block.** Retained in v6 for v5 back-compat (the `anyOf` rule accepts either shape) but new skills should populate the flat top-level fields instead. The body section `## Concept Card` is retired — the flat frontmatter fields are now the canonical location.

## [1.2.0] — 2026-05-16

### Added

- **`schema_version: 5`.** Closed the `category` field to a 6-value enum (`foundations | engineering | design | quality | agent | product`) and removed 7 deprecated values. Promoted `quality` from facet to 6th category per Rule 2 (property vs subject). Introduced `foundations` as the new browse home for epistemic preconditions per Rule 1 (primary surface).
- **`schemas/skill.v5.schema.json`.** Pinned v5 schema with the closed `category` enum.
- **`docs/migrations/v4-to-v5.md`.** Author-facing migration procedure for the v4 → v5 category enum closure, including the value-by-value remap table and the foundations-gate anti-junk-drawer rule.

## [1.1.0] — 2026-05-13

### Added

- **`schema_version: 4`.** Naming cleanup. Renamed `browse_category` to `category`, hierarchical `category` / `category_path` to `domain`, `project_tags` to `workspace_tags`, and `routing_groups` to `routing_bundles`.
- **`schemas/skill.v4.schema.json`.** Pinned v4 schema with the cleaned-up field names.

## [1.0.0] — 2026-04-26

### Added

- **Initial public release.** The Skill Metadata Protocol carved out of the parent `skill-graph` monorepo into a docs-and-schemas-only repo. v2 and v3 schemas, the `SKILL_METADATA_PROTOCOL.md` normative spec, the field reference, the primer, and the six original ADRs (predicate set, JSON-LD context, OntoClean rigidity tags, persistent identifiers, freshness consolidation, revise predicate rename).
