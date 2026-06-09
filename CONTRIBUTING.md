# Contributing

Thank you for considering feedback or contributions to EDIP.

EDIP is a personal, independent and proprietary project maintained by Francisco Azevedo Alves. Contributions are welcome only if they respect the proprietary license and the confidentiality rules described in `LICENSE` and `NOTICE.md`.

## Contribution Rules

- Do not submit confidential, proprietary, internal, strategic or restricted information from employers, clients, banks, financial institutions or any third party.
- Do not submit content derived from internal documents, internal systems, private repositories, proprietary processes or non-public organizational practices.
- Do not add references to any employer, client, bank, internal company name or proprietary corporate information.
- Do not present EDIP as an implemented or production-ready platform.
- Keep clear that the project is in conceptual modeling and architecture preparation.
- Preserve the personal authorship of Francisco Azevedo Alves.

## Change Classification

Every proposal should indicate whether it changes one or more of the following areas:

- Domain model.
- Product model.
- Metrics catalog.
- Event catalog.
- Intelligence model.
- Architecture documentation.
- Governance or legal metadata.
- Repository organization.

Conceptual changes must update all related documentation. For example, a new domain entity may require updates to the domain model, metrics catalog, event catalog, intelligence model and README.

## Commit Convention

Use clear and traceable commits.

Recommended prefixes:

- `docs:` documentation changes.
- `model:` domain, product or conceptual model changes.
- `architecture:` architecture documentation changes.
- `metrics:` metrics, KPIs, health scores, forecasts or heat map changes.
- `events:` event catalog or event relationship changes.
- `intelligence:` intelligence, explainability, recommendation or knowledge model changes.
- `legal:` license, notice or legal metadata changes.
- `chore:` repository organization, formatting or non-conceptual maintenance.

Examples:

- `docs: update repository README`
- `model: add architecture capability context`
- `metrics: add capability health metrics`
- `events: add architecture events`
- `intelligence: add capability intelligence model`
- `legal: add proprietary license and notice`
- `chore: organize repository structure`

## Changelog

Every relevant change must be recorded in `CHANGELOG.md`.

Each changelog entry should describe:

- Date.
- Author.
- Type of change.
- Documents affected.
- Summary.
- Rationale.

## Review Checklist

Before proposing a change, verify:

- The chain of traceability remains clear.
- Product, Capability, Service and Offer are not confused.
- Metrics have owners and conceptual formulas where applicable.
- Events represent completed facts, not commands or metrics.
- Forecasts remain explainable.
- Critical decisions remain auditable.
- No third-party confidential or proprietary information is included.
