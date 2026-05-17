# Skill Metadata Protocol

> The normative specification for `SKILL.md` — the portable skill packaging format used by AI agent systems.

**npm**: `@skill-graph/protocol` · **Version**: 1.3.0 · **Schema version**: 6 · **License**: Apache-2.0

This repo contains the protocol specification, JSON schemas, and documentation only. It has no runtime tooling.

---

## What this repo contains

| Path | Purpose |
|------|---------|
| `SKILL_METADATA_PROTOCOL.md` | The full normative specification (field definitions, requirements, examples) |
| `schemas/` | JSON Schema files — v2, v3, v4, v5, v6 pinned versions + unversioned current (tracks v6) |
| `docs/` | Deep-dive documentation: field reference, primer, adoption guide, conformance, glossary, ADRs |
| `docs/migrations/` | Per-bump author migration procedures (currently v3→v4, v4→v5, v5→v6) |
| `docs/adr/` | Architecture Decision Records — including [ADR 0007](docs/adr/0007-version-source-of-truth.md) on the cross-repo version source of truth |
| `CHANGELOG.md` | npm package version history (`@skill-graph/protocol`) |
| `examples/` | Authoring template and sample manifest |

> **Version authority:** The current `schema_version` is the highest pinned schema file in `schemas/skill.vN.schema.json` — currently `skill.v6.schema.json`. The npm package version is in `package.json`. See [ADR 0007](docs/adr/0007-version-source-of-truth.md) for the dual-versioning model used across the four sibling repos.

> **Surface scope:** The v6 contract targets the OSS-portable canonical library. Personal and tenant-specific surfaces are out of scope and not subject to v6 migration — see [skill-graph ADR 0008](https://github.com/jacob-balslev/skill-graph/blob/main/docs/adr/0008-skill-surface-split-and-curation-policy.md).

## Related repos

| Repo | Purpose |
|------|---------|
| [skill-graph](https://github.com/jacob-balslev/skill-graph) | Library tooling: lint, manifest compiler, router, drift sentinel |
| [skill-audit-loop](https://github.com/jacob-balslev/skill-audit-loop) | 5-phase audit procedure for keeping skills grounded |
| [skills](https://github.com/jacob-balslev/skills) | Public open-source skill library |

## Using the schemas

```js
const schema = require('@skill-graph/protocol/schemas/skill.schema.json');
```

Or reference directly in your JSON Schema tooling:

```
node_modules/@skill-graph/protocol/schemas/skill.v6.schema.json
```

## Quick start

See [`docs/QUICKSTART-30MIN.md`](docs/QUICKSTART-30MIN.md) and [`examples/skill-metadata-template.md`](examples/skill-metadata-template.md).

## License

Apache-2.0 — see [LICENSE](LICENSE).
