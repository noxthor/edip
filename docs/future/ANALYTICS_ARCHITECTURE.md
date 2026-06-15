# Arquitetura Analitica

Este documento futuro detalhará como a EDIP produz, governa e serve métricas, health scores, forecasts, heat maps, alertas e projeções analíticas.

## Status

Planejado. Ainda não define arquitetura analítica implementável.

## Fontes Obrigatórias

- `../METRICS_CATALOG.md`
- `../EVENT_CATALOG.md`
- `../INTELLIGENCE_MODEL.md`
- `../DATA_MODEL.md`
- `../UX_INFORMATION_ARCHITECTURE.md`

## Escopo Esperado

- modelos analíticos para métricas governadas;
- séries históricas, snapshots e versionamento de forecasts;
- materializações para cockpits, heat maps, timelines e comparisons;
- agregações para Case Management, alertas, blockers, value realization e operating flow;
- confidence, freshness, lineage e qualidade de cálculo;
- regras de comparabilidade por período, escopo, baseline, target e população analisada.

## Fora de Escopo

- contratos de API;
- modelo físico de banco;
- implementação de pipelines;
- componentes frontend.
