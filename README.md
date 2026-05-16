# Skill Metadata Protocol

> The normative specification for `SKILL.md` — the portable skill packaging format used by AI agent systems.

**npm**: `@skill-graph/protocol` · **Version**: 1.1.0 · **Schema version**: 4 · **License**: Apache-2.0

This repo contains the protocol specification, JSON schemas, and documentation only. It has no runtime tooling.

---

## What this repo contains

| Path | Purpose |
|------|---------|
| `SKILL_METADATA_PROTOCOL.md` | The full normative specification (field definitions, requirements, examples) |
| `schemas/` | JSON Schema files — v2, v3, v4 pinned versions + unversioned current |
| `docs/` | Deep-dive documentation: field reference, primer, adoption guide, conformance, glossary, ADRs |
| `examples/` | Authoring template and sample manifest |

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
node_modules/@skill-graph/protocol/schemas/skill.v4.schema.json
```

## Quick start

See [`docs/QUICKSTART-30MIN.md`](docs/QUICKSTART-30MIN.md) and [`examples/skill-metadata-template.md`](examples/skill-metadata-template.md).

## License

Apache-2.0 — see [LICENSE](LICENSE).
