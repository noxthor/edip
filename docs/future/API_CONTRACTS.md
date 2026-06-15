# Contratos de API

Este documento futuro detalhará contratos conceituais de APIs, comandos, consultas, eventos, rejeições e integrações da EDIP.

## Status

Planejado. O repositório ainda não define APIs implementadas.

## Fontes Obrigatórias

- `../DOMAIN_MODEL.md`
- `../ARCHITECTURE.md`
- `../DATA_MODEL.md`
- `../EVENT_CATALOG.md`
- `../UX_INFORMATION_ARCHITECTURE.md`

## Escopo Esperado

- comandos por bounded context;
- consultas canônicas para workspaces, cockpits, heat maps, timelines e entity workspaces;
- contratos de lifecycle para Alert, Investigation, Decision, ActionPlan e Case;
- contratos de Case Management para criação, triagem, atribuição, vínculo, evidência, validação, closure e reabertura;
- paginação, filtros, autorização, deep links e preservação de contexto;
- command rejection, idempotência, versionamento e compatibilidade;
- contratos de graph traversal e evidence access.

## Fora de Escopo

- implementação HTTP, GraphQL, gRPC ou mensageria concreta;
- modelo físico de banco;
- SDKs ou código cliente.
