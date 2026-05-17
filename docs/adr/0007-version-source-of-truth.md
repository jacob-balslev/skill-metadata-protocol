# ADR 0007 — Version Source of Truth

> Status: Accepted
> Date: 2026-05-18
> Linear: SH-6124 (Cross-repo version reconciliation)

## Context

Four sibling repos publish skill-related artifacts and each one has its own notion of "version":

| Repo | Versioning surface |
|---|---|
| `skill-metadata-protocol` | The normative spec + JSON schemas. Versioned twice: the package (npm `@skill-graph/protocol`) and the `schema_version` carried inside each schema file. |
| `skill-graph` | The library tooling that consumes the protocol. Versioned as npm `@skill-graph/cli` and tracks `schema_version` references in docs. |
| `skill-audit-loop` | The audit procedure that re-grounds skills. Versioned as npm `@skill-graph/audit` and references the protocol's Health Block fields. |
| `skills` | The open-source skill library that follows the protocol. No package version of its own; each skill carries its own `schema_version` frontmatter. |

Without a single source of truth, version claims drift: `skill-graph/README.md` claimed `schema_version: 4` while the canonical schema in `skill-graph/schemas/skill.v6.schema.json` had already been bumped to v6. New adopters reading docs across the four repos got contradictory answers to "what version is current?"

## Decision

**The version source of truth lives in two places, with one canonical for each kind of version.**

### 1. Schema version → `skill-metadata-protocol/schemas/`

The current `schema_version` is the **highest pinned schema file** in `skill-metadata-protocol/schemas/skill.vN.schema.json`. As of 2026-05-18 that is `skill.v6.schema.json` and the contract is `schema_version: 6`.

Concretely:

- The unversioned mirror `schemas/skill.schema.json` MUST always equal the highest pinned schema file.
- The version number stamped inside the schema (`properties.schema_version.const`) MUST match its file name.
- All other repos — `skill-graph`, `skill-audit-loop`, `skills`, plus this repo's own docs — quote this number; they do not invent their own.

### 2. Package version → each repo's own `package.json`

Each publishable npm package is versioned independently by SemVer:

- `@skill-graph/protocol` → `skill-metadata-protocol/package.json`
- `@skill-graph/cli` → `skill-graph/package.json`
- `@skill-graph/audit` → `skill-audit-loop/package.json`

A repo's README MAY display its own package version but MUST NOT claim a different package version than its `package.json`. A repo's README MUST quote the protocol's `schema_version` accurately if it mentions one.

## Consequences

### Positive

- New adopters always have one authoritative answer: open `skill-metadata-protocol/schemas/` and read the highest-numbered file. The integer at the end of the filename is the current schema version.
- Future schema bumps require a single physical addition: drop `skill.vN+1.schema.json` next to its predecessors and update `skill.schema.json` to mirror it. Every downstream repo's "current version" claim is computed from the same file system.
- Drift is detectable mechanically. A drift sentinel can grep all four repos for `schema_version: <N>` patterns and flag any mismatch with the highest pinned schema file.

### Negative

- The dual-versioning model (one schema number, three package numbers) requires every doc author to keep the two distinct. The README template for each repo SHOULD include both lines explicitly: `Version: X.Y.Z · Schema version: N`.
- Adopters who pin to a package version implicitly pin to a schema version range. The package CHANGELOG is the contract that translates between them.

### Migration impact

The 2026-05-18 sweep (SH-6124) reconciled the four repos to declare schema_version 6:

- `skill-graph/README.md` + `CHANGELOG.md` — updated stale "schema_version: 4" claims to 6.
- `skill-metadata-protocol/package.json` — bumped 1.1.0 → 1.3.0 to match the README claim already in place.
- `skill-metadata-protocol/CHANGELOG.md` — added, documenting the v6 release.
- `skill-audit-loop/package.json` — bumped 0.1.0 → 0.2.0 to match the README and the v0.2.0 release notes in-place.
- `skills/README.md` — no version claims to update; the repo follows the protocol via per-skill `schema_version` frontmatter.

## Alternatives considered

1. **Single super-version across all four repos.** Rejected: the four repos ship independently and adopters install them independently. Forcing one version number would couple unrelated release cadences and force major-version bumps in repos that did not actually change.
2. **Hosted version manifest (e.g., a `versions.json` at skillgraph.dev).** Rejected for now: adds a hosted dependency for a problem that is solvable with file-system convention. Revisit if the four-repo set grows to a number where cross-grep stops scaling.
3. **Embed schema version inside `package.json` engines field.** Rejected: misuses the `engines` field, and downstream tools (lint, manifest generator) already read the schema file directly — there is no consumer that would benefit from a duplicate copy in `package.json`.

## Related

- `docs/migrations/v5-to-v6.md` — the v6 contract migration this ADR documents the authority for.
- `SKILL_METADATA_PROTOCOL.md` — the normative spec that the schema_version pins.
- ADR 0005 — Freshness consolidation (a prior pattern of consolidating dispersed version-like signals onto one canonical field).
