# Skill Metadata Protocol

[![DEPRECATED](https://img.shields.io/badge/status-deprecated%20%C2%B7%20docs--only%20mirror-9ca3af?style=flat-square)](https://github.com/jacob-balslev/skill-graph/blob/main/docs/adr/0009-sibling-repo-deprecation.md) [![Canonical home](https://img.shields.io/badge/canonical%20home-%40skill--graph%2Fcli-cb3837?style=flat-square&logo=npm)](https://www.npmjs.com/package/@skill-graph/cli) [![Schema v6](https://img.shields.io/badge/schema-v6-blueviolet?style=flat-square)](https://github.com/jacob-balslev/skill-graph/blob/main/schemas/skill.v6.schema.json) [![License Apache-2.0 + CC-BY-4.0](https://img.shields.io/badge/license-Apache--2.0%20%2B%20CC--BY--4.0-green?style=flat-square)](LICENSE)

> ⚠️ **This repository is deprecated as of 2026-05-18.**
>
> The Skill Metadata Protocol — schemas, normative spec, migrations, examples, and tooling — has been consolidated into [`@skill-graph/cli`](https://www.npmjs.com/package/@skill-graph/cli) (v0.5.6 onward). This repository is preserved as a **docs-only mirror** for historical reference and inbound-link stability. It is not archived — links into the README and `SKILL_METADATA_PROTOCOL.md` here continue to resolve, but source files (`schemas/`, `examples/`, `package.json`, ADRs, migrations) have moved.
>
> See [ADR 0009 — Sibling Repo Deprecation](https://github.com/jacob-balslev/skill-graph/blob/main/docs/adr/0009-sibling-repo-deprecation.md) for the consolidation rationale, and [SH-6132](https://linear.app/sales-hub/issue/SH-6132) for the original decision.

## Where to find the canonical content

| You're looking for… | Canonical home |
|---|---|
| Install the protocol & tooling | `npm install -g @skill-graph/cli` → [npm](https://www.npmjs.com/package/@skill-graph/cli) |
| The normative `SKILL.md` spec | [`docs/SKILL_METADATA_PROTOCOL.md`](https://github.com/jacob-balslev/skill-graph/blob/main/docs/SKILL_METADATA_PROTOCOL.md) in `skill-graph` |
| JSON Schemas (v2–v6) | [`schemas/`](https://github.com/jacob-balslev/skill-graph/tree/main/schemas) in `skill-graph` |
| Author template | [`examples/skill-metadata-template.md`](https://github.com/jacob-balslev/skill-graph/blob/main/examples/skill-metadata-template.md) in `skill-graph` |
| Field-by-field reference | [`docs/field-reference.md`](https://github.com/jacob-balslev/skill-graph/blob/main/docs/field-reference.md) in `skill-graph` |
| Migration guides (v3→v4, v4→v5, v5→v6) | [`docs/migrations/`](https://github.com/jacob-balslev/skill-graph/tree/main/docs/migrations) in `skill-graph` |
| Architecture Decision Records (ADRs) | [`docs/adr/`](https://github.com/jacob-balslev/skill-graph/tree/main/docs/adr) in `skill-graph` |
| Public skill library | [`jacob-balslev/skills`](https://github.com/jacob-balslev/skills) — `npx skills add jacob-balslev/skills` |

## What's still here

The two files below remain in this repo as historical snapshots. The authoritative versions are in [`skill-graph`](https://github.com/jacob-balslev/skill-graph) — links above. Treat the copies here as frozen at the deprecation point (2026-05-18, commit [`176d69d`](https://github.com/jacob-balslev/skill-metadata-protocol/commit/176d69d)) and not subject to further updates.

| File | Status |
|---|---|
| [`SKILL_METADATA_PROTOCOL.md`](SKILL_METADATA_PROTOCOL.md) | Historical snapshot of the normative spec. **Canonical version:** [skill-graph/docs/SKILL_METADATA_PROTOCOL.md](https://github.com/jacob-balslev/skill-graph/blob/main/docs/SKILL_METADATA_PROTOCOL.md). |
| [`CHANGELOG.md`](CHANGELOG.md) | Historical npm version history for `@skill-graph/protocol` 1.0.0 → 1.3.0. Subsequent releases ship as `@skill-graph/cli`. |

## The Skill Graph ecosystem

<p align="center">
  <img src="docs/images/skill-graph-ecosystem.svg" alt="Skill Graph ecosystem — skill-graph is the canonical monolith that exports SKILL.md into the skills library; skill-metadata-protocol and skill-audit-loop are docs-only mirrors." width="640">
</p>

| Repo | Status | Purpose |
|---|---|---|
| [skill-graph](https://github.com/jacob-balslev/skill-graph) | **active** | Canonical home — protocol spec, schemas, CLI, lint, manifest, router, drift, audit loop, export |
| [skills](https://github.com/jacob-balslev/skills) | **active** | Public open-source skill library |
| **skill-metadata-protocol** *(this repo)* | mirror | Historical docs-only mirror of the normative spec |
| [skill-audit-loop](https://github.com/jacob-balslev/skill-audit-loop) | mirror | Historical docs-only mirror of the audit procedure |

## Contributing & Trust

This repo is read-only. To contribute to the active project:

- **Issues, PRs, discussions** → file against [`jacob-balslev/skill-graph`](https://github.com/jacob-balslev/skill-graph/issues).
- **Security** — report vulnerabilities privately via the [security policy](SECURITY.md), not as public issues.
- **Code of Conduct** — this project follows the [Contributor Covenant 2.1](CODE_OF_CONDUCT.md).
- **License** — Apache-2.0 for code, CC-BY-4.0 for the spec text. See [`LICENSE`](LICENSE) and [`NOTICE`](NOTICE).
