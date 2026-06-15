# Arquitetura de Conhecimento

Este documento futuro detalhará a arquitetura de conhecimento da EDIP.

## Status

Planejado. O Knowledge Graph já possui base conceitual em `../DATA_MODEL.md` e `../INTELLIGENCE_MODEL.md`, mas ainda não possui arquitetura própria detalhada.

## Fontes Obrigatórias

- `../DATA_MODEL.md`
- `../INTELLIGENCE_MODEL.md`
- `../EVENT_CATALOG.md`
- `../UX_INFORMATION_ARCHITECTURE.md`
- `../DOMAIN_MODEL.md`

## Escopo Esperado

- schemas de nós e relações do Knowledge Graph;
- Evidence Graph, Decision Graph, Value Graph, Capability Graph e Case Timeline;
- relações `contains`, `relatesTo`, `escalates`, `resolves`, `reopenedBy`, `evidencedBy`, `validatedBy` e `learnedFrom`;
- confidence por edge, provenance, stewardship e qualidade semântica;
- causal chains, root cause patterns, similar cases e organizational learning;
- Narrative Library, Narrative Explorer e governança de narrativas;
- regras de traversal autorizado para Copilot e Navigation Intelligence.

## Fora de Escopo

- motor de grafo específico;
- embedding store físico;
- implementação de Copilot;
- APIs de consulta.
