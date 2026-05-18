# Skill Metadata Protocol

> ⚠️ **DEPRECATED — content consolidated into [@skill-graph/cli](https://www.npmjs.com/package/@skill-graph/cli) as of v0.5.6.**
> Install via `npm install -g @skill-graph/cli`. This repo is now a **docs-only mirror** preserved for historical reference and inbound-link stability. See [SH-6132](https://linear.app/sales-hub/issue/SH-6132) for the consolidation rationale.

> The normative specification for `SKILL.md` — the portable skill packaging format used by AI agent systems.

**npm**: `@skill-graph/protocol` · **Version**: 1.3.0 · **Schema version**: 6 · **License**: Apache-2.0

This repo is now a **docs-only mirror**. Source files (schemas/, examples/, package.json) have been consolidated into [`@skill-graph/cli`](https://www.npmjs.com/package/@skill-graph/cli) as of v0.5.6.

---

## What this mirror contains

| Path | Purpose |
|------|---------|
| `SKILL_METADATA_PROTOCOL.md` | The full normative specification (field definitions, requirements, examples) |
| `CHANGELOG.md` | Historical npm package version history (`@skill-graph/protocol`) |

> **Version authority (post-consolidation):** Schemas now live in `@skill-graph/cli`. See [ADR 0007](docs/adr/0007-version-source-of-truth.md) for the dual-versioning model and the 2026-05-18 consolidation addendum.

> **Surface scope:** The v6 contract targets the OSS-portable canonical library. Personal and tenant-specific surfaces are out of scope and not subject to v6 migration — see [skill-graph ADR 0008](https://github.com/jacob-balslev/skill-graph/blob/main/docs/adr/0008-skill-surface-split-and-curation-policy.md).

## Consolidated location

All schemas, migrations, examples, and tooling are now in [`@skill-graph/cli`](https://www.npmjs.com/package/@skill-graph/cli):

```bash
npm install -g @skill-graph/cli
```

Schemas: [`https://github.com/jacob-balslev/skill-graph/blob/main/lib/schemas/`](https://github.com/jacob-balslev/skill-graph/blob/main/lib/schemas/)

Docs: [`https://github.com/jacob-balslev/skill-graph/blob/main/docs/SKILL_METADATA_PROTOCOL.md`](https://github.com/jacob-balslev/skill-graph/blob/main/docs/SKILL_METADATA_PROTOCOL.md)

## Related repos

| Repo | Purpose |
|------|---------|
| [skill-graph](https://github.com/jacob-balslev/skill-graph) | Canonical home — library tooling, schemas, lint, manifest compiler, router, drift sentinel |
| [skill-audit-loop](https://github.com/jacob-balslev/skill-audit-loop) | Docs-only mirror — audit procedure docs (source consolidated into @skill-graph/cli) |
| [skills](https://github.com/jacob-balslev/skills) | Public open-source skill library |

## License

Apache-2.0 — see [LICENSE](LICENSE).
