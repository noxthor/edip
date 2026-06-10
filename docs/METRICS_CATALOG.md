# Metrics Catalog - Enterprise Delivery Intelligence Platform (EDIP)

## Objetivo

Este documento define o catálogo governado de métricas da EDIP. Cada métrica deve ser tratada como produto de dados: possui definição, owner, entidade medida, fórmula conceitual, fonte esperada, periodicidade, uso em dashboards, alertas associados, nível de confiança e capacidade explícita de navegação por drill-down e drill-up.

O catálogo não define banco de dados, APIs, pipelines, queries ou implementação técnica.

## Princípios de Métricas

- Toda métrica deve possuir owner.
- Toda métrica deve medir uma entidade de domínio explícita.
- Toda métrica deve ter fórmula conceitual compreensível por negócio, produto, arquitetura e engenharia.
- Toda métrica deve indicar fonte esperada e periodicidade.
- Toda métrica usada em decisão crítica deve permitir drill-down, drill-up e auditabilidade.
- Métricas sem fonte confiável devem continuar visíveis, mas com confiança reduzida.
- Métricas podem medir objetivos, key results, outcomes, produtos, portfólios, iniciativas, features, value cases, benefícios, controles, qualidade de dados, queues, bottlenecks, flow stages ou heat maps.
- KPI não é elo obrigatório entre strategy e portfolio; KPI é uma métrica governada aplicada a um alvo de medição.
- Flow Intelligence mede filas, esperas, gargalos, desperdícios e capacidade de fluidez sem alterar a cadeia principal do domínio.

## Escala de Confiança

| Nível | Definição |
| --- | --- |
| Alta | Fonte governada, owner definido, fórmula aprovada, atualização dentro da periodicidade e lineage conhecido. |
| Média | Fonte conhecida e owner definido, mas com dependência de reconciliação, atualização manual controlada ou lineage parcial. |
| Baixa | Fonte instável, atualização irregular, owner ausente, fórmula em validação ou divergência entre fontes. |
| Desconhecida | Métrica proposta, ainda sem validação suficiente. |

## Health Scores Governados

| Score | Distinção Conceitual | Componentes Principais | Dashboards |
| --- | --- | --- | --- |
| Strategic Health Score | Saúde de objetivos estratégicos, OKRs, KPIs, riscos e valor. | progresso OKR, tendência de KPI, value realization, riscos, traceability health, delay impact, decision latency. | Executive Overview, Strategic Alignment Dashboard |
| Portfolio Health Score | Saúde de portfólio por valor, risco, capacidade, dependências, forecast e governança. | alinhamento, valor esperado, capacidade, forecast confidence, forecast accuracy, dependências, funding, flow health, cost of delay, governance. | Portfolio Command Center, Executive Overview |
| Initiative Health Score | Saúde de uma iniciativa como unidade de execução e governança. | progresso, forecast, riscos, dependências, rastreabilidade, valor, milestones, flow health, cost of delay, decision latency. | Initiative Workspace, Portfolio Command Center |
| Delivery Health Score | Saúde da execução delivery considerando progresso, previsibilidade e impedimentos. | milestones, épicos, blockers, commitment reliability, readiness, riscos de entrega. | Delivery Flow Dashboard, Initiative Workspace |
| Flow Health Score | Saúde específica do fluxo, distinta de Delivery Health Score, focada em filas, espera, gargalos, desperdício e impacto econômico do fluxo. | queue time, wait time, flow efficiency, bottleneck severity, aging WIP, throughput, staleness, cost of queue, cost of bottleneck. | Flow Intelligence Dashboard, Delivery Flow Dashboard, Portfolio Command Center, Executive Overview |
| Product Health Score | Saúde de produto por outcome, adoção, roadmap, qualidade, risco e valor. | outcome progress, adoção, roadmap confidence, qualidade, risco, valor. | Product Value Dashboard |
| Technical Delivery Health | Saúde técnica de entrega. | release readiness, qualidade, observabilidade, débito, riscos técnicos, blockers. | Technical Leadership Dashboard |
| Value Realization Score | Saúde de realização de valor. | benefício validado, evidência, confiança, value forecast accuracy, value leakage, time to value, desvio de forecast, rejeições. | Value Realization Dashboard, Executive Overview |
| Data Confidence Score | Confiança de dado, métrica ou cálculo. | completude, frescor, lineage, sucesso de integração, divergência, erro. | Observability and Data Quality Dashboard, Governance and Evidence Dashboard |
| Governance Health Score | Saúde de governança, decisões, evidências, controles, exceções e alertas críticos. | decision latency, approval aging, evidence coverage, control adherence, exception aging, alert resolution health, auditability. | Governance and Evidence Dashboard, Portfolio Command Center, Executive Overview |
| Business Discovery Health | Saúde da descoberta de negócio antes de produto ou solução. | necessidade com owner, evidência, dor clara, jornada/processo, problema definido, aging. | Business Discovery Dashboard, Executive Overview |
| Requirements Health | Saúde de requisitos funcionais e não funcionais. | origem rastreável, completude, critérios de aceite, revisão, aprovação, rejeições, retrabalho. | Requirements Dashboard, Initiative Workspace |
| Solution Health | Saúde do desenho de solução. | requisitos cobertos, revisões concluídas, pendências, evidências, aprovações, rejeições, riscos. | Solution Review Dashboard, Architecture Cockpit |
| Architecture Review Health | Saúde das revisões arquiteturais. | review time, pendências, dívidas, exceções, evidências, aprovações. | Architecture Review Heat Map, Governance and Evidence Dashboard |
| Engineering Review Health | Saúde das revisões de engenharia. | review time, viabilidade, riscos técnicos, pendências, evidências, aprovações. | Engineering Review Heat Map, Technical Leadership Dashboard |
| Readiness Health | Saúde de prontidão para delivery. | DOR, capacidade, dependências, riscos, checklist, blockers, approval aging. | Readiness Dashboard, Delivery Flow Dashboard |
| Validation Health | Saúde de validação pós-entrega. | critérios validados, evidência, rejeições, validation time, outcome validation. | Validation Dashboard, Value Realization Dashboard |
| Alert Resolution Health | Saúde de tratamento efetivo de alertas. | alert aging, ação, evidência, validação da condição original, resolução, reabertura. | Alert Heat Map, Governance and Evidence Dashboard |
| Blocker Resolution Health | Saúde de resolução de bloqueadores. | blocked time, aging, owner, severidade, evidência de resolução, reabertura. | Blocker Heat Map, Flow Intelligence Dashboard |

## Strategy Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Strategic Health Score | Mede a saúde consolidada de objetivos estratégicos, OKRs, KPIs, riscos e valor. | Strategy | Diretor | StrategicObjective | progresso OKR + tendência de KPI + value realization + cobertura de execução - riscos - lacunas de rastreabilidade | Strategy, Metrics, Portfolio, Value Realization | Semanal | Owner do objetivo estratégico | Executive Overview, Strategic Alignment Dashboard | Objetivo em risco, OKR em risco, KPI crítico fora do target | Média | Tema, objetivo, OKR, KR, KPI, iniciativa, value case | Estratégia corporativa, tema estratégico |
| Strategic Alignment Coverage | Percentual de iniciativas rastreáveis a objetivo, OKR, outcome ou justificativa formal. | Strategy | PMO | Initiative | iniciativas com vínculo estratégico válido / total de iniciativas estratégicas | Strategy, Portfolio, Delivery | Diário | PMO | Strategic Alignment Dashboard, Portfolio Command Center | Baixa cobertura de rastreabilidade, iniciativa sem objetivo | Alta | Iniciativa, épico, feature, roadmap item, evidência | Tema, objetivo estratégico, portfólio |
| Objective Funding Coverage | Mede cobertura de funding para objetivos estratégicos ativos. | Strategy | Diretor | StrategicObjective | objetivos com investimento aprovado ou portfólio ativo / objetivos ativos | Strategy, Portfolio | Semanal | PMO / Financeiro | Strategic Alignment Dashboard, Executive Overview | Objetivo sem execução, objetivo sem funding | Média | Objetivo, investimento, portfólio, iniciativa | Tema estratégico, estratégia corporativa |
| OKR Achievement Forecast | Estima probabilidade de cumprimento de OKRs no ciclo. | Strategy | Diretor | OKR | projeção dos key results ponderada por progresso, tendência, riscos e iniciativas associadas | Strategy, Metrics, Delivery, Value Realization | Semanal | Owner do OKR | Executive Overview, Strategic Alignment Dashboard | OKR em risco | Média | KR, KPI, iniciativa, risco, value case | Objetivo estratégico, tema estratégico |
| Key Result Progress | Mede avanço atual de um key result contra target. | Strategy | Superintendente | KeyResult | valor atual / target esperado no período | Strategy, Metrics | Semanal | Owner do KR | Strategic Alignment Dashboard | KR abaixo do esperado | Alta | KPI, outcome, iniciativa contribuinte, evidência | OKR, objetivo estratégico |
| KPI Target Deviation | Mede desvio entre valor atual e target de KPI. | Metrics and Intelligence | Diretor | KPI | valor atual - target, normalizado pela escala da métrica | Metrics, fonte governada do KPI | Conforme periodicidade do KPI | Owner da métrica | Executive Overview, KPI and Outcomes Dashboard | KPI crítico fora do target | Alta | Alvo medido, série histórica, fonte, evidência | KR, outcome, objetivo, produto, iniciativa ou value case |

## Portfolio Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Portfolio Health Score | Mede saúde de portfólio por valor, risco, capacidade, dependências, forecast e governança. | Portfolio | Superintendente | Portfolio | alinhamento + valor esperado + capacidade adequada + forecast confidence + flow health - riscos - dependências vencidas - lacunas de dados | Portfolio, Delivery, Value Realization, Metrics | Semanal | Owner do portfólio | Portfolio Command Center, Executive Overview | Portfólio crítico, Flow Health Degraded | Média | Investimento, iniciativa, dependência, bottleneck, queue, value case | Tema estratégico, objetivo, unidade executiva |
| Capacity Allocation Fit | Mede aderência da capacidade aos temas e objetivos prioritários. | Portfolio | Superintendente | CapacityAllocation | capacidade alocada a temas prioritários / capacidade total alocada | Portfolio, Organization | Semanal | PMO / Superintendente | Portfolio Command Center | Capacidade desalinhada, capacidade sobrecarregada | Média | Time, squad, iniciativa, produto, flow stage | Portfólio, objetivo estratégico |
| Funding Variance | Mede diferença entre funding aprovado, consumido e forecast. | Portfolio | PMO | Investment | funding consumido ou forecast - funding aprovado | Portfolio, Financeiro, Value Realization | Mensal | Financeiro / PMO | Portfolio Command Center, Governance and Evidence Dashboard | Funding divergente | Média | Investimento, iniciativa, value case, decisão | Portfólio, objetivo financiado |
| Investment At Risk | Quantifica investimento associado a iniciativas em risco ou críticas. | Portfolio | Diretor | Investment | soma de investimentos vinculados a iniciativas com health score em risco, flow health crítico ou value realization degradado | Portfolio, Delivery, Metrics | Semanal | Owner do portfólio | Executive Overview, Portfolio Command Center | Investimento em risco | Média | Iniciativa, bottleneck, dependência, value case | Portfólio, tema estratégico |
| Initiative Risk Exposure | Mede exposição do portfólio por iniciativas em risco. | Portfolio | Superintendente | Initiative | peso de iniciativas em risco ponderado por criticidade, investimento, valor esperado, flow health e dependências | Portfolio, Delivery, Metrics | Semanal | PMO | Portfolio Command Center, Initiative Workspace | Iniciativa crítica, portfólio crítico | Média | Iniciativa, risco, bottleneck, blocker, feature | Portfólio, objetivo estratégico |
| Dependency Aging | Mede tempo de dependências abertas no portfólio. | Portfolio | Superintendente | Dependency | média ou percentil de dias em aberto por dependência ativa | Portfolio, Delivery | Diário | Owner da dependência | Portfolio Command Center, Dependency Map, Flow Intelligence Dashboard | Dependência vencida, Bottleneck Detected | Alta | Dependência, owner, iniciativa, queue afetada | Portfólio, heat map corporativo |
| Opportunity Conversion Rate | Mede taxa de oportunidades convertidas em iniciativas, experimentos ou decisões formais. | Portfolio | Product Owner | Opportunity | oportunidades convertidas / oportunidades qualificadas | Portfolio, Product | Mensal | Product Owner / PMO | Portfolio Command Center, Product Value Dashboard | Oportunidade parada, funil sem conversão | Média | Ideia, oportunidade, value case, decisão | Tema, objetivo, portfólio |
| Committee Readiness | Mede prontidão de itens de comitê com dados, owner e evidências suficientes. | Governance and Audit | PMO | DecisionGate | itens de pauta completos / itens de pauta planejados | Governance, Portfolio, Metrics | Semanal | PMO | Portfolio Command Center, Governance and Evidence Dashboard | Comitê sem evidência, decisão sem owner | Média | Decision gate, evidência, iniciativa, investimento | Portfólio, governança executiva |

## Product Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Product Outcome Progress | Mede progresso de outcomes de produto contra target. | Product | Product Owner | ProductOutcome | valor atual do outcome / target do outcome | Product, Metrics, fontes digitais | Semanal | Product Owner | Product Value Dashboard, Executive Overview | Outcome sem progresso, KPI de produto fora do target | Média | KPI, roadmap item, release, evidência | Produto, objetivo, value case |
| Product Health Score | Mede saúde do produto por outcome, roadmap, adoção, qualidade, risco e valor. | Product | Product Owner | Product | outcome progress + adoção + roadmap progress + value realization - riscos - débitos - lacunas | Product, Delivery, Engineering, Value Realization | Semanal | Product Owner | Product Value Dashboard | Produto em risco | Média | Outcome, capability, roadmap item, initiative, release | Produto, portfólio, objetivo |
| Backlog Strategic Alignment | Mede alinhamento do backlog a objetivos, outcomes ou iniciativas. | Product / Delivery | Product Owner | RoadmapItem, Feature, Story | itens de backlog com rastreabilidade válida / total de itens relevantes | Product, Delivery | Diário | Product Owner | Product Value Dashboard, Delivery Flow Dashboard, Initiative Workspace | Item sem rastreabilidade | Alta | Roadmap item, feature, story, owner | Produto, iniciativa, objetivo |
| Feature Value Score | Mede valor esperado de uma feature no Delivery. | Delivery | Product Owner | Feature | valor esperado + impacto em KPI + urgência + confiança - esforço - risco | Product, Delivery, Metrics | Semanal | Product Owner | Product Value Dashboard, Initiative Workspace | Feature crítica em risco | Média | Feature, story, release, KPI, evidência | Roadmap item, iniciativa, produto |
| Roadmap Confidence | Mede confiança do roadmap em relação a capacidade, dependências e evidência de valor. | Product | Product Owner | Roadmap | itens com owner, capacidade, dependências mapeadas e vínculo a outcome / itens do roadmap | Product, Portfolio, Delivery | Semanal | Product Owner | Product Value Dashboard | Roadmap sem confiança | Média | Roadmap item, capability, dependência, iniciativa | Produto, portfólio |
| Adoption Trend | Mede evolução de uso, adoção ou engajamento de produto. | Product | Product Owner | Product | tendência temporal de usuários, transações, uso ou comportamento relevante | Analytics, canais digitais, produto | Semanal | Product Owner / Dados | Product Value Dashboard, KPI and Outcomes Dashboard | Adoção em queda | Média | Segmento, jornada, canal, release | Produto, outcome, objetivo |
| Time to Outcome | Mede tempo entre início de iniciativa ou release e evidência de outcome. | Product / Value Realization | Product Owner | ProductOutcome | data da primeira evidência de outcome - data de início da iniciativa ou release | Product, Delivery, Value Realization | Mensal | Product Owner | Product Value Dashboard, Value Realization Dashboard | Outcome sem evidência após entrega | Média | Release, iniciativa, KPI, evidência | Produto, value case, objetivo |

## Discovery Quality Metrics

Estas métricas medem a qualidade do processo de discovery e da tomada de decisão de produto antes do comprometimento de capacidade relevante.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Discovery Quality Score | Mede qualidade de discovery por hipóteses validadas, evidências, premissas, clareza de outcome e readiness. | Product / Discovery | Product Owner | Opportunity, ProductHypothesis, RoadmapItem | hipóteses validadas + evidências coletadas + qualidade das premissas + clareza de outcome + readiness - lacunas críticas | Product, Discovery, Metrics, Governance | Semanal | Product Owner | Product Value Dashboard, Initiative Workspace, Portfolio Command Center | Discovery Quality Degraded | Média | Ideia, oportunidade, hipótese, evidência, roadmap item, readiness | Produto, portfólio, objetivo |
| Discovery Rework Rate | Percentual de itens que retornaram ao discovery após aprovação, compromisso ou entrada em delivery. | Product / Discovery | Product Owner | RoadmapItem, Feature, Opportunity | itens retornados ao discovery após aprovação / itens aprovados para avanço | Product, Delivery, Governance | Mensal | Product Owner | Product Value Dashboard, Flow Intelligence Dashboard | Discovery Quality Degraded, retrabalho de discovery elevado | Média | Roadmap item, feature, hipótese, decisão de retorno | Produto, iniciativa, portfólio |
| Hypothesis Validation Accuracy | Mede precisão das hipóteses originalmente formuladas comparando benefício previsto e benefício realizado. | Product / Value Realization | Product Owner | ProductHypothesis, ValueCase, RealizedBenefit | proximidade entre benefício previsto pela hipótese e benefício realizado validado | Product, Value Realization, Analytics, Metrics | Mensal | Product Owner / Sponsor de valor | Product Value Dashboard, Value Realization Dashboard, Executive Overview | Discovery Quality Degraded, Value Leakage Detected | Média | Hipótese, benefício previsto, benefício realizado, KPI, release | Produto, value case, objetivo estratégico |

## Delivery Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Initiative Health Score | Mede saúde de uma iniciativa por progresso, forecast, risco, dependências, valor e rastreabilidade. | Delivery | Gerente | Initiative | progresso + previsibilidade + rastreabilidade + contribuição a KPI + flow health - riscos - bloqueios - dependências vencidas | Delivery, Portfolio, Metrics, Value Realization | Semanal | Gerente | Initiative Workspace, Portfolio Command Center | Iniciativa crítica, Flow Health Degraded | Média | Épico, feature, release, blocker, bottleneck, KPI | Portfólio, objetivo estratégico |
| Delivery Health Score | Mede saúde de execução de uma iniciativa ou frente de delivery sem substituir Flow Health Score. | Delivery | Gerente | Initiative, Team | progresso + milestone adherence + commitment reliability + blocker resolution + release readiness - riscos de entrega | Delivery, Engineering, Portfolio | Semanal | Gerente / Coordenador | Delivery Flow Dashboard, Initiative Workspace | Entrega crítica, forecast de prazo degradado | Média | Milestone, épico, feature, blocker, release | Iniciativa, portfólio |
| Milestone Adherence | Mede cumprimento de marcos planejados. | Delivery | Gerente | Initiative | milestones cumpridos no prazo / milestones planejados no período | Delivery | Semanal | Gerente | Initiative Workspace | Marco vencido | Alta | Milestone, deliverable, owner, evidência | Iniciativa, portfólio |
| Epic Completion Rate | Mede conclusão de épicos dentro de uma iniciativa. | Delivery | Gerente | Epic | épicos concluídos / épicos planejados ou ativos | Delivery | Semanal | Gerente | Initiative Workspace | Épico atrasado | Alta | Épico, feature, story, blocker | Iniciativa, roadmap item |
| Lead Time | Mede tempo entre entrada e conclusão de um item de trabalho. | Delivery | Scrum Master | Feature, Story | data de conclusão - data de entrada no fluxo | Delivery / ALM | Diário | Scrum Master | Delivery Flow Dashboard, Flow Intelligence Dashboard, Initiative Workspace | Lead time acima do limite | Alta | Flow stage, queue, bottleneck, story, task | Feature, épico, iniciativa, portfólio |
| Cycle Time | Mede tempo de execução desde o início efetivo até conclusão. | Delivery | Scrum Master | Story, Task | data de conclusão - data de início de execução | Delivery / ALM | Diário | Scrum Master | Delivery Flow Dashboard | Cycle time acima do limite | Alta | Story, task, flow stage, owner | Feature, iniciativa, squad |
| Commitment Reliability | Mede confiabilidade entre compromisso e entrega. | Delivery | Coordenador | Team, Feature, Story | itens entregues conforme compromisso / itens comprometidos | Delivery | Por ciclo | Coordenador / Scrum Master | Delivery Flow Dashboard, Initiative Workspace | Compromisso em risco | Média | Item comprometido, causa de desvio, blocker | Squad, iniciativa, portfólio |
| Traceability Gap Count | Mede itens operacionais sem vínculo adequado. | Delivery | PMO | Feature, Story, Task | contagem de itens sem épico, iniciativa, owner ou vínculo herdado | Delivery, Product | Diário | PMO / Product Owner | Strategic Alignment Dashboard, Delivery Flow Dashboard | Feature sem épico, story sem feature | Alta | Feature, story, task, owner | Iniciativa, produto, objetivo |
| Blocked Work Count | Mede volume de trabalho explicitamente bloqueado. | Delivery | Coordenador | Blocker | contagem de itens bloqueados ativos por severidade | Delivery / ALM | Diário | Coordenador | Delivery Flow Dashboard, Flow Intelligence Dashboard | Bloqueio sem owner, bloqueio crítico | Alta | Blocker, work item, owner, causa | Squad, iniciativa, portfólio |
| Blocker Resolution Time | Mede tempo de resolução de bloqueios. | Delivery | Scrum Master | Blocker | data de resolução - data de abertura do bloqueio | Delivery | Diário | Scrum Master | Delivery Flow Dashboard, Technical Leadership Dashboard | Bloqueio envelhecido | Alta | Blocker, causa, owner, work item | Squad, iniciativa, portfólio |

## Traceability Metrics

Estas métricas medem a qualidade da cadeia de rastreabilidade corporativa sem duplicar métricas de alinhamento estratégico ou lacunas operacionais.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Traceability Health Score | Mede saúde da rastreabilidade corporativa por completude, consistência, ownership, atualização e integridade dos vínculos. | Strategy / Metrics and Intelligence | PMO | TraceabilityLink, Initiative, Epic, Feature, Story, Task | completude dos vínculos + consistência semântica + ownership + atualização recente + integridade referencial - lacunas e conflitos | Strategy, Portfolio, Product, Delivery, Metrics | Diário | PMO / Owner de métricas | Strategic Alignment Dashboard, Portfolio Command Center, Governance and Evidence Dashboard, Executive Overview | Traceability Health Critical, iniciativa sem vínculo estratégico, item sem owner | Média | Iniciativa, épico, feature, story, task, vínculo, owner | Portfólio, objetivo, tema, estratégia corporativa |

## Flow Intelligence Metrics

Estas métricas tornam explícitos gargalos, filas, esperas e desperdícios. Elas alimentam Enterprise Heat Map, Portfolio Heat Map, Delivery Heat Map e Squad Heat Map sem criar novos níveis estruturais de domínio.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Queue Time | Mede o tempo em que um item permanece em uma queue aguardando capacidade, decisão, dependência, aprovação, validação ou próximo flow stage. | Flow Intelligence | Scrum Master | Queue, Feature, Story, Task | soma do tempo em queue por item ou percentil por flow stage | Delivery / ALM, Governance, Portfolio | Diário | Scrum Master / Owner do flow stage | Flow Intelligence Dashboard, Delivery Flow Dashboard, Initiative Workspace, Portfolio Command Center | Queue Threshold Breached, Waiting Stage Aging Breached | Alta | Queue, flow stage, work item, owner, causa de espera | Squad Heat Map, Delivery Heat Map, Portfolio Heat Map, Enterprise Heat Map |
| Wait Time | Mede tempo sem trabalho ativo, incluindo ready, waiting, approval, dependency e validation waits. | Flow Intelligence | Coordenador | Feature, Story, Task | soma de períodos sem touch time dentro do lead time | Delivery / ALM, Governance, Dependency Map | Diário | Coordenador / Scrum Master | Flow Intelligence Dashboard, Delivery Flow Dashboard, Initiative Workspace | Waiting Stage Aging Breached, Work Item Stale | Média | Período de espera, stage, blocker, dependency, approval | Squad, iniciativa, portfólio, enterprise |
| Touch Time | Mede tempo de trabalho ativo aplicado ao item, distinto de espera e fila. | Flow Intelligence | Líder Técnico | Feature, Story, Task | soma de períodos com execução ativa validada por mudança de estado, esforço ou evidência de progresso | Delivery / ALM, Engenharia | Diário | Líder Técnico / Scrum Master | Delivery Flow Dashboard, Flow Intelligence Dashboard | Baixo touch time, Work Item Stale | Média | Story, task, owner, stage ativo | Feature, iniciativa, squad |
| Flow Efficiency | Mede proporção entre tempo ativo e tempo total de fluxo. | Flow Intelligence | Scrum Master | Feature, Story, Task | touch time / lead time total | Delivery / ALM | Semanal | Scrum Master | Delivery Flow Dashboard, Flow Intelligence Dashboard, Portfolio Command Center | Baixa eficiência de fluxo, Flow Health Degraded | Média | Item, flow stage, queue, bottleneck | Squad, iniciativa, portfólio, enterprise |
| Flow Health Score | Score próprio de saúde de fluxo, distinto de Delivery Health Score. | Flow Intelligence | Superintendente | FlowHealthScore, Queue, FlowStage, Portfolio, Initiative, Team | throughput + flow efficiency + previsibilidade - queue time - wait time - bottleneck severity - aging WIP - staleness | Delivery, Metrics, Portfolio, Observability | Diário / Semanal | Owner de Flow Intelligence | Flow Intelligence Dashboard, Executive Overview, Portfolio Command Center, Delivery Flow Dashboard | Flow Health Degraded, Bottleneck Detected, Queue Threshold Breached | Média | Driver do score, queue, bottleneck, stage, work item | Squad Heat Map, Delivery Heat Map, Portfolio Heat Map, Enterprise Heat Map |
| Bottleneck Count | Mede quantidade de gargalos ativos ou recorrentes por nível de análise. | Flow Intelligence | PMO | Bottleneck | contagem de bottlenecks ativos, recorrentes ou reabertos por período e severidade | Delivery, Portfolio, Governance, Observability | Diário | PMO / Owner da restrição | Flow Intelligence Dashboard, Portfolio Command Center, Executive Overview, Initiative Workspace | Bottleneck Detected | Alta | Bottleneck, queue, flow stage, causa, owner, plano de ação | Squad, iniciativa, portfólio, enterprise |
| Bottleneck Severity | Mede severidade de gargalo por impacto, duração, recorrência e escopo afetado. | Flow Intelligence | Superintendente | Bottleneck | impacto em prazo, valor, capacidade ou risco + duração + recorrência + criticidade do escopo | Delivery, Portfolio, Metrics, Value Realization | Diário | Owner da restrição | Flow Intelligence Dashboard, Portfolio Command Center, Executive Overview | Bottleneck Severity Increased, Flow Health Degraded | Média | Causa, queue afetada, work items, dependências, plano de ação | Delivery Heat Map, Portfolio Heat Map, Enterprise Heat Map |
| Aging WIP | Mede envelhecimento de itens em progresso ou aguardando avanço em flow stage não final. | Flow Intelligence | Coordenador | Feature, Story, Task | data atual - data de entrada no flow stage atual | Delivery / ALM | Diário | Coordenador | Delivery Flow Dashboard, Flow Intelligence Dashboard, Squad Heat Map | Aging WIP alto, Work Item Stale, Waiting Stage Aging Breached | Alta | Work item, stage, owner, queue, blocker | Squad, iniciativa, portfólio |
| Work Item Staleness | Mede ausência de avanço, atualização significativa ou evidência de progresso em item ativo. | Flow Intelligence | Scrum Master | Feature, Story, Task | data atual - última mudança relevante de estado, owner, evidência ou progresso | Delivery / ALM, Observability | Diário | Scrum Master | Flow Intelligence Dashboard, Delivery Flow Dashboard, Initiative Workspace | Work Item Stale | Alta | Work item, owner, último evento, stage, queue | Squad, iniciativa, portfólio |
| Throughput | Mede volume de itens concluídos por período, tipo, squad, iniciativa ou flow stage. | Flow Intelligence | Coordenador | Feature, Story, Task | contagem de itens concluídos no período | Delivery / ALM | Diário / Semanal | Coordenador / Scrum Master | Delivery Flow Dashboard, Flow Intelligence Dashboard, Portfolio Command Center | Throughput degradado, Flow Health Degraded | Alta | Tipo de item, squad, stage, iniciativa | Squad, iniciativa, portfólio, enterprise |
| WIP by Flow Stage | Mede distribuição de trabalho em progresso por FlowStage. | Flow Intelligence | Scrum Master | FlowStage, Feature, Story, Task | contagem de itens ativos por flow stage e classe de trabalho | Delivery / ALM | Diário | Scrum Master | Flow Intelligence Dashboard, Delivery Flow Dashboard, Squad Heat Map | Queue Threshold Breached, Bottleneck Detected | Alta | Flow stage, queue, work item, owner | Squad, iniciativa, portfólio |
| Blocked Time | Mede tempo em que item permaneceu sob bloqueio explícito. | Flow Intelligence | Líder Técnico | Blocker, Feature, Story, Task | soma dos períodos com blocker ativo por item | Delivery / ALM, Engenharia | Diário | Líder Técnico / Scrum Master | Delivery Flow Dashboard, Flow Intelligence Dashboard, Initiative Workspace | Bloqueio crítico, Work Item Stale, Flow Health Degraded | Alta | Blocker, causa, owner, dependência, evidência | Squad, iniciativa, portfólio |
| Approval Aging | Mede envelhecimento de itens aguardando aprovação, gate ou decisão formal. | Flow Intelligence / Governance | PMO | DecisionGate, Approval, Queue | data atual - data de entrada em estágio de aprovação | Governance, Portfolio, Delivery | Diário | PMO / Owner do gate | Flow Intelligence Dashboard, Portfolio Command Center, Initiative Workspace, Governance and Evidence Dashboard | Approval Aging Breached, Queue Threshold Breached | Alta | Approval, decision gate, iniciativa, owner, evidência pendente | Portfólio, comitê, enterprise |
| Discovery Lead Time | Mede tempo entre entrada em discovery e decisão de readiness, compromisso ou descarte. | Flow Intelligence / Product | Product Owner | Opportunity, RoadmapItem, Feature | data de saída de discovery - data de entrada em discovery | Product, Delivery, Portfolio | Semanal | Product Owner | Flow Intelligence Dashboard, Product Value Dashboard, Initiative Workspace | Discovery aging alto, Work Item Stale | Média | Ideia, oportunidade, hipótese, roadmap item, evidência | Produto, portfólio, objetivo |
| Funding Lead Time | Mede tempo entre solicitação de investimento e decisão de funding. | Flow Intelligence / Portfolio | PMO | Investment, DecisionGate | data de aprovação ou rejeição - data de submissão do funding | Portfolio, Financeiro, Governance | Semanal | PMO / Financeiro | Portfolio Command Center, Flow Intelligence Dashboard, Executive Overview | Approval Aging Breached, Funding decision delayed | Média | Investment, decision gate, value case, evidência | Portfólio, objetivo, comitê executivo |
| Release Lead Time | Mede tempo entre readiness de release ou escopo comprometido e release efetivamente liberada. | Flow Intelligence / Delivery | Líder Técnico | Release, Feature | data de release - data de readiness ou compromisso de release | Delivery, Engineering, Release Management | Diário / Por release | Líder Técnico | Delivery Flow Dashboard, Flow Intelligence Dashboard, Initiative Workspace | Release aging alto, Bottleneck Detected | Média | Release, feature, controle, blocker, dependência | Iniciativa, produto, portfólio |
| Time to Value | Mede tempo desde entrega ou release até benefício validado, conectando fluxo a value realization. | Value Realization / Flow Intelligence | Product Owner | RealizedBenefit, ValueCase, Release | data de validação do benefício - data da entrega ou release | Value Realization, Delivery, Product | Mensal | Product Owner / Sponsor | Executive Overview, Value Realization Dashboard, Flow Intelligence Dashboard, Portfolio Command Center | Benefício atrasado, Flow Health Degraded | Média | Release, iniciativa, value case, benefício, KPI | Produto, portfólio, objetivo estratégico |

## Execution Economics Metrics

Estas métricas conectam atrasos, filas e gargalos ao impacto econômico, permitindo que decisões executivas priorizem valor, risco financeiro e custo de oportunidade.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Cost of Delay | Valor potencial perdido por unidade de tempo devido ao atraso de uma iniciativa, feature, release ou benefício. | Execution Economics / Value Realization | Diretor | Initiative, Feature, Release, ValueCase | valor esperado sensível ao tempo x tempo de atraso x criticidade de janela de oportunidade | Value Realization, Portfolio, Delivery, Financeiro | Semanal / Mensal | Sponsor de valor / Financeiro | Executive Overview, Portfolio Command Center, Value Realization Dashboard, Initiative Workspace | Cost of Delay Critical, Value Leakage Detected | Média | Iniciativa, feature, release, value case, benefício | Portfólio, objetivo estratégico |
| Cost of Queue | Impacto econômico associado ao trabalho parado em filas. | Execution Economics / Flow Intelligence | Superintendente | Queue, FlowStage, Initiative | queue time x valor esperado ou custo de capacidade x criticidade do item, ajustado por wait time e WIP by flow stage | Delivery, Flow Intelligence, Portfolio, Financeiro | Semanal | Owner do portfólio / PMO | Flow Intelligence Dashboard, Portfolio Command Center, Executive Overview | Cost of Delay Critical, Queue Threshold Breached | Média | Queue, flow stage, work item, owner, value case | Squad, iniciativa, portfólio, objetivo |
| Cost of Bottleneck | Impacto econômico gerado por gargalos persistentes. | Execution Economics / Flow Intelligence | Superintendente | Bottleneck, Portfolio, Initiative | bottleneck severity x investimento ou valor esperado afetado x duração do gargalo | Flow Intelligence, Portfolio, Delivery, Value Realization | Semanal | Owner da restrição / PMO | Flow Intelligence Dashboard, Portfolio Command Center, Executive Overview | Cost of Delay Critical, Bottleneck Severity Increased | Média | Bottleneck, queue, iniciativa, investimento, plano de ação | Delivery Heat Map, Portfolio Heat Map, Enterprise Heat Map |
| Delay Impact Score | Score que estima impacto estratégico, operacional e econômico causado por atrasos. | Execution Economics | Diretor | Initiative, Release, ValueCase | valor esperado + criticidade estratégica + dependências + pressão de prazo + exposição financeira - mitigação ativa | Strategy, Portfolio, Delivery, Value Realization, Risk | Semanal | PMO / Sponsor de valor | Executive Overview, Portfolio Command Center, Initiative Workspace | Cost of Delay Critical, forecast de prazo degradado | Média | Iniciativa, release, dependência, value case, risco | Portfólio, objetivo, estratégia |
| Value Leakage | Valor esperado que deixou de ser capturado devido a atrasos, cancelamentos, baixa adoção, baixa realização de benefícios ou degradação de outcomes. | Execution Economics / Value Realization | Diretor | ValueCase, ProductOutcome, RealizedBenefit | valor planejado ou forecast - valor validado, ajustado por causa de perda e confiança da evidência | Value Realization, Product, Delivery, Financeiro, Analytics | Mensal | Sponsor de valor / Product Owner | Executive Overview, Value Realization Dashboard, Portfolio Command Center | Value Leakage Detected, KPI crítico fora do target | Média | Value case, outcome, release, adoção, causa de perda | Produto, portfólio, objetivo estratégico |

## Engineering Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Technical Delivery Health | Mede saúde técnica por risco, débito, qualidade, readiness e bloqueios. | Engineering | Líder Técnico | TechnicalService, Feature, Release | release readiness + qualidade + observabilidade - débitos - riscos - bloqueios técnicos | Engineering, Delivery, Observability | Semanal | Líder Técnico | Technical Leadership Dashboard | Saúde técnica crítica | Média | Serviço, release, feature, blocker técnico | Produto, iniciativa, arquitetura corporativa |
| Technical Debt Exposure | Mede exposição causada por débitos técnicos. | Engineering | Arquiteto Corporativo | TechnicalDebt | severidade x criticidade do serviço x impacto em KPI, release ou risco | Engineering, Architecture, Delivery | Semanal | Líder Técnico / Arquiteto | Technical Leadership Dashboard | Débito técnico crítico | Média | Débito, serviço, feature, risco | Domínio técnico, produto, portfólio |
| Release Readiness | Mede prontidão técnica de uma release. | Engineering | Líder Técnico | Release | critérios técnicos atendidos / critérios obrigatórios | Engineering, Delivery, Governance | Por release | Líder Técnico | Technical Leadership Dashboard, Initiative Workspace | Release sem readiness | Média | Critério, controle, evidência, blocker | Release, iniciativa, produto |
| Defect Leakage | Mede defeitos escapados para fases posteriores ou produção. | Engineering | Líder Técnico | Release, Feature | defeitos detectados após aceite ou produção / total de defeitos detectados | Engineering, Quality, Incident | Semanal | Líder Técnico | Technical Leadership Dashboard | Vazamento de defeitos | Média | Defeito, release, feature, causa | Produto, iniciativa |
| Rework Rate | Mede retrabalho técnico ou funcional. | Engineering / Delivery | Líder Técnico | Story, Feature | itens reabertos ou refeitos / itens concluídos | Delivery / ALM, Quality | Semanal | Líder Técnico | Technical Leadership Dashboard, Delivery Flow Dashboard | Retrabalho elevado | Média | Story, feature, causa, owner | Squad, iniciativa, produto |
| Technical Blocker Aging | Mede envelhecimento de bloqueios técnicos. | Engineering | Líder Técnico | Blocker | dias em aberto de bloqueios técnicos ativos | Delivery, Engineering | Diário | Líder Técnico | Technical Leadership Dashboard, Flow Intelligence Dashboard | Bloqueio técnico vencido, Bottleneck Detected | Alta | Blocker, serviço, dependência, owner | Squad, iniciativa, arquitetura |
| Integration Risk Score | Mede risco associado a integrações críticas. | Engineering | Arquiteto Corporativo | Integration | criticidade + dependências + incidentes + mudanças planejadas - controles mitigadores | Engineering, Observability, Governance | Semanal | Arquiteto Corporativo | Technical Leadership Dashboard | Risco de integração crítico | Média | Integração, serviço, incidente, dependência | Domínio técnico, produto, portfólio |
| Standard Exception Aging | Mede envelhecimento de exceções arquiteturais ou técnicas. | Governance / Engineering | Arquiteto Corporativo | Exception | data atual - data de abertura da exceção | Governance, Engineering | Semanal | Arquiteto Corporativo | Governance and Evidence Dashboard | Exceção vencida | Alta | Exceção, controle, evidência, owner | Arquitetura corporativa, governança |

## Governance and Audit Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Governance Health Score | Mede saúde de governança por decisões, aprovações, evidências, controles, exceções e resolução de alertas. | Governance and Audit | PMO / Auditoria | Decision, DecisionGate, Control, Exception, Alert | decision SLA + evidence coverage + control adherence + alert resolution health - approval aging - exception aging - decision rework | Governance, Metrics, Alerts, Audit | Semanal | PMO / Governança | Governance and Evidence Dashboard, Portfolio Command Center, Executive Overview | Governance Health Degraded, Decision Latency Critical, Alert Resolution Failed | Média | Decision, gate, approval, evidence, control, exception, alert | Portfólio, objetivo, enterprise |
| Evidence Coverage | Mede cobertura de evidências para decisões, métricas, controles e benefícios. | Governance and Audit | Especialista | Evidence | entidades que exigem evidência e possuem evidência válida / entidades que exigem evidência | Governance, Value Realization, Metrics | Diário | Especialista / PMO | Governance and Evidence Dashboard | Evidência ausente | Alta | Entidade, evidência, owner, decisão | Comitê, portfólio, auditoria |
| Control Adherence Rate | Mede aderência a controles aplicáveis. | Governance and Audit | Especialista | Control | controles atendidos / controles aplicáveis | Governance, Risk, Compliance | Semanal | Riscos / Compliance | Governance and Evidence Dashboard | Controle não atendido | Média | Controle, evidência, exceção, owner | Domínio regulatório, auditoria |
| Approval Cycle Time | Mede tempo total de ciclo de aprovações concluídas. | Governance and Audit | PMO | Approval | data da decisão - data da solicitação | Governance | Diário | PMO | Governance and Evidence Dashboard, Portfolio Command Center | Aprovação vencida | Alta | Approval, decision gate, evidência, owner | Comitê, portfólio, enterprise |
| Compliance Issue Count | Mede volume de pendências de compliance. | Governance and Audit | Especialista | Control, Exception | contagem de issues abertas por severidade | Governance, Risk, Compliance | Diário | Compliance | Governance and Evidence Dashboard | Pendência crítica de compliance | Média | Issue, controle, exceção, owner | Auditoria, domínio regulatório |
| Decision SLA | Mede cumprimento de prazo de decisões. | Governance and Audit | PMO | Decision | decisões dentro do prazo / decisões com prazo definido | Governance, Portfolio | Diário | PMO | Portfolio Command Center, Governance and Evidence Dashboard | Decisão vencida, Approval Aging Breached | Alta | Decision, gate, evidência, iniciativa | Comitê, portfólio, objetivo |
| Metric Ownership Coverage | Mede percentual de métricas com owner definido. | Metrics and Intelligence | Especialista | KPI, MetricDefinition | métricas com owner / total de métricas ativas | Metrics | Diário | Owner de métricas | Governance and Evidence Dashboard | KPI sem owner | Alta | Métrica, owner, domínio, dashboard | Governança de dados, enterprise |
| Lineage Completeness | Mede completude de lineage de métricas e cálculos. | Metrics and Intelligence | Especialista | KPI, MetricDefinition | métricas com fonte, fórmula, transformação e owner / métricas ativas | Metrics, Observability | Semanal | Dados / Analytics | Governance and Evidence Dashboard | Lineage incompleto | Média | Métrica, fonte, cálculo, evidência | Governança de dados, auditoria |

## Decision Intelligence Metrics

Estas métricas medem velocidade, volume e qualidade de decisões, separando latência decisória de aging de aprovação e de SLAs formais.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Decision Latency | Mede tempo entre identificação do problema e tomada da decisão. | Decision Intelligence / Governance | PMO | Decision, DecisionGate, Issue | data da decisão - data de identificação formal do problema ou necessidade decisória | Governance, Portfolio, Flow Intelligence, Alerts | Diário / Semanal | PMO / Owner do gate | Executive Overview, Portfolio Command Center, Governance and Evidence Dashboard | Decision Latency Critical, Approval Aging Breached | Média | Problema, decisão, gate, owner, evidência, iniciativa | Comitê, portfólio, objetivo estratégico |
| Decision Throughput | Mede quantidade de decisões concluídas por período. | Decision Intelligence / Governance | PMO | Decision | contagem de decisões concluídas no período por tipo, comitê, portfólio ou gate | Governance, Portfolio | Semanal | PMO | Portfolio Command Center, Governance and Evidence Dashboard | baixa vazão decisória | Média | Decision, tipo, comitê, gate, owner | Portfólio, governança executiva |
| Decision Rework Rate | Mede percentual de decisões revertidas, refeitas ou reavaliadas. | Decision Intelligence / Governance | PMO | Decision | decisões revertidas, refeitas ou reavaliadas / decisões concluídas | Governance, Portfolio, Audit | Mensal | PMO / Governança | Governance and Evidence Dashboard, Portfolio Command Center, Executive Overview | Decision Latency Critical, decisão reavaliada recorrente | Média | Decision, motivo de retrabalho, evidência, impacto | Comitê, portfólio, auditoria |

## Operating Model Metrics

Estas métricas medem o fluxo corporativo Need-to-Value, incluindo discovery de negócio, requirements, solution design, reviews, readiness, validation, blockers e resolução efetiva de alertas.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Business Discovery Lead Time | Mede tempo entre captura de necessidade e problema qualificado ou decisão de descarte. | Business Discovery | Business Teams / Product Owner | BusinessNeed, BusinessProblem | data de qualificação ou descarte - data de captura da necessidade | Business Discovery, Governance | Diário / Semanal | Business Owner | Business Discovery Dashboard, Executive Overview | Business Discovery Aging Breached | Média | Need, pain, journey, process, evidence | Produto, portfólio, objetivo |
| Business Discovery Health | Mede saúde da descoberta de negócio por owner, evidência, dor, jornada, processo e aging. | Business Discovery | Business Teams | BusinessNeed, BusinessProblem | completude + evidência + clareza do problema + owner - aging - lacunas | Business Discovery, Governance | Semanal | Business Owner | Business Discovery Dashboard | Discovery Intake Risk | Média | Need, pain, evidence, process, owner | Produto, portfólio |
| Requirements Health | Mede qualidade e prontidão de requisitos. | Requirements | Product Owner | FunctionalRequirement, NonFunctionalRequirement | origem rastreável + critérios + revisão + aprovação + owner - rejeições - lacunas | Requirements, Product Discovery, Governance | Diário / Semanal | Product Owner / Business Analyst | Requirements Dashboard, Initiative Workspace | Requirements Quality Alert | Média | Requisito, origem, critério, reviewer, evidência | Iniciativa, produto, objetivo |
| Requirements Queue Time | Mede tempo de requisitos aguardando revisão, owner, evidência ou aprovação. | Requirements / Flow | Product Owner | FunctionalRequirement, NonFunctionalRequirement | soma de tempo em estados ou filas de requirements sem avanço | Requirements, Flow Intelligence | Diário | Product Owner / PMO | Requirements Dashboard, Flow Intelligence Dashboard | Requirements Queue Threshold Breached | Média | Requisito, fila, reviewer, blocker | Produto, iniciativa |
| Review Time | Mede tempo consumido em revisões de solução por especialidade. | Solution Design | Arquiteto Corporativo | ArchitectureReview, EngineeringReview, SecurityReview, DataReview, ComplianceReview | data de conclusão da revisão - data de solicitação da revisão | Solution Design, Governance | Diário | Owner da revisão | Solution Review Dashboard, Architecture Review Heat Map, Engineering Review Heat Map | Review Aging Breached | Alta | Review, reviewer, solução, pendência, SLA | Iniciativa, produto, capability |
| Approval Time | Mede tempo entre solicitação e aprovação ou rejeição formal. | Governance / Solution Design | PMO | SolutionApproval, Approval, DecisionGate | data de decisão - data de solicitação | Governance, Solution Design | Diário | PMO / Autoridade do gate | Governance and Evidence Dashboard, Solution Review Dashboard | Approval Aging Breached | Alta | Aprovação, gate, approver, evidência | Iniciativa, portfólio |
| Solution Time | Mede tempo entre criação de solution design e aprovação, rejeição ou retorno. | Solution Design | Arquiteto Corporativo | SolutionDesign | data de decisão de solução - data de criação do solution design | Solution Design, Governance | Diário / Semanal | Solution Owner | Solution Review Dashboard, Architecture Cockpit | Solution Review Alert | Média | Solution design, requisito, review, pendência | Produto, iniciativa, capability |
| Solution Health | Mede saúde do desenho de solução por cobertura, revisão, evidência e decisão. | Solution Design | Arquiteto Corporativo | SolutionDesign | requisitos cobertos + reviews concluídos + evidências + aprovação - pendências - rejeições - riscos | Solution Design, Architecture, Engineering | Semanal | Solution Owner | Solution Review Dashboard, Architecture Cockpit | Solution Health Degraded | Média | Solução, requirement, review, evidence, exception | Iniciativa, produto, capability |
| Architecture Review Health | Mede saúde das revisões arquiteturais. | Solution Design / Architecture | Arquiteto Corporativo | ArchitectureReview | reviews concluídas no SLA + evidências + decisões - pendências críticas - exceções vencidas | Solution Design, Architecture Capability, Governance | Semanal | Arquiteto Corporativo | Architecture Review Heat Map, Governance and Evidence Dashboard | Architecture Review Degraded | Média | Review, capability, service, debt, exception | Domain, produto, iniciativa |
| Engineering Review Health | Mede saúde das revisões de engenharia. | Solution Design / Engineering | Líder Técnico | EngineeringReview | reviews concluídas no SLA + riscos tratados + evidências - pendências técnicas - rejeições | Solution Design, Engineering | Semanal | Líder Técnico | Engineering Review Heat Map, Technical Leadership Dashboard | Engineering Review Degraded | Média | Review, risco, serviço, feature, evidência | Iniciativa, release |
| Readiness Time | Mede tempo entre início e aprovação ou rejeição de readiness. | Delivery Readiness | Scrum Master | ReadinessAssessment | data de decisão de readiness - data de início do assessment | Delivery Readiness, Flow Intelligence | Diário | Scrum Master / Delivery Owner | Readiness Dashboard, Delivery Flow Dashboard | Readiness Aging Breached | Alta | Assessment, DOR, blocker, dependência, capacidade | Iniciativa, portfólio |
| Readiness Health | Mede saúde de prontidão para execução. | Delivery Readiness | Gerente | ReadinessAssessment | DOR atendido + capacidade disponível + dependências tratadas + riscos aceitos - blockers - lacunas | Delivery Readiness, Delivery, Governance | Diário / Semanal | Delivery Owner | Readiness Dashboard, Initiative Workspace | Readiness Alert | Média | Assessment, checklist, blocker, capacity, dependency | Iniciativa, produto |
| Validation Time | Mede tempo entre início e conclusão de validação. | Validation | Product Owner | Validation | data de conclusão da validação - data de início da validação | Validation, Delivery, Value Realization | Diário / Semanal | Validation Owner | Validation Dashboard, Value Realization Dashboard | Validation Aging Breached | Média | Validação, critério, evidência, validador | Outcome, value case |
| Validation Health | Mede saúde de validação por evidência, critérios, aceite e outcome. | Validation | Product Owner | Validation, OutcomeValidation | critérios validados + evidências + owner + resultado - rejeições - lacunas | Validation, Product, Value Realization | Semanal | Validation Owner | Validation Dashboard, Product Value Dashboard | Validation Health Degraded | Média | Critério, feature, outcome, evidence | Produto, iniciativa, value case |
| Alert Aging | Mede tempo de alerta aberto desde detecção até resolução válida. | Metrics and Intelligence / Governance | PMO | Alert | data atual ou resolução - data de detecção | Alerts, Metrics, Governance | Contínua / Diária | Alert Owner | Alert Heat Map, Governance and Evidence Dashboard | Alert Aging Breached | Alta | Alert, owner, action, evidence, validation | Dashboard, domínio, enterprise |
| Alert Resolution Time | Mede tempo entre alerta detectado e AlertResolution válido. | Metrics and Intelligence / Governance | PMO | AlertResolution | data de resolução válida - data de detecção do alerta | Alerts, Governance | Diário / Semanal | Alert Owner | Alert Heat Map, Governance and Evidence Dashboard | Alert Resolution Failed | Alta | Alert, action, evidence, validation, resolution | Domínio, portfólio, enterprise |
| Alert Resolution Health | Mede qualidade de resolução de alertas por ação, evidência, validação e reabertura. | Metrics and Intelligence / Governance | PMO | Alert, AlertResolution | alertas resolvidos com ação + evidência + validação / alertas encerrados - reaberturas - aging | Alerts, Governance, Evidence | Semanal | PMO / Alert Owner | Alert Heat Map, Governance and Evidence Dashboard | Alert Resolution Health Degraded | Alta | Alert, action, evidence, validator, cause | Domínio, dashboard, enterprise |
| Blocker Resolution Health | Mede efetividade de resolução de bloqueadores. | Delivery / Flow Intelligence | Coordenador | Blocker | blockers resolvidos com evidência no SLA / blockers abertos - reaberturas - severidade vencida | Delivery, Flow Intelligence, Governance | Diário / Semanal | Blocker Owner | Blocker Heat Map, Flow Intelligence Dashboard | Blocker Resolution Degraded | Média | Blocker, owner, cause, evidence, impacted item | Squad, iniciativa, portfólio |

## Architecture Metrics

Estas métricas consolidam o Architecture Elevator e suas relações com strategy, product, delivery, value, governance e modernization.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Capability Health Score | Mede saúde de capability por criticidade, rastreabilidade, dívida, modernização, risco e valor. | Architecture Capability | Arquiteto Corporativo | Capability | cobertura + rastreabilidade + modernization + service health - debt - exceptions - risk | Architecture Capability, Metrics, Governance | Semanal | Capability Owner | Capability Landscape, Architecture Cockpit | Capability Health Degraded | Média | Capability, service, offer, product, debt | Domain, subdomain, objetivo |
| Capability Coverage | Mede cobertura de capabilities mapeadas e com owner. | Architecture Capability | Arquiteto Corporativo | Capability | capabilities com owner, propósito e criticidade / capabilities esperadas ou ativas | Architecture Capability | Mensal | Arquiteto Corporativo | Capability Landscape | Capability Coverage Alert | Média | Domain, subdomain, business layer, owner | Enterprise architecture |
| Service Health Score | Mede saúde de BusinessService ou TechnologyService. | Architecture Capability | Líder Técnico / Arquiteto | BusinessService, TechnologyService | disponibilidade conceitual + modernization + adoption + traceability - debt - exceptions - risk | Architecture, Engineering, Governance | Semanal | Service Owner | Service Landscape, Modernization Cockpit | Service Health Degraded | Média | Service, offer, app service, debt, exception | Capability, domain |
| Offer Health Score | Mede saúde de offer por adoção, rastreabilidade, serviços, produtos e risco. | Architecture Capability / Product | Product Owner / Offer Owner | Offer | adoption + product traceability + service health + value support - debt - retirement risk | Architecture, Product, Metrics | Semanal | Offer Owner | Offer Landscape, Product Value Dashboard | Offer Health Degraded | Média | Offer, service, product, app service | Capability, product, objective |
| Product Health Score | Mede saúde de produto incluindo composição de offers, outcomes, valor, delivery e arquitetura. | Product / Architecture | Product Owner | Product | outcome progress + offer health + value realization + delivery health - risk - debt | Product, Architecture, Delivery, Value Realization | Semanal | Product Owner | Product Value Dashboard, Architecture Cockpit | Product Health Degraded | Média | Product, offer, outcome, initiative, value case | Portfolio, objective |
| Capability Modernization Score | Mede progresso e efetividade da modernização de capability. | Architecture Capability | Arquiteto Corporativo | Capability, ModernizationPlan | progresso de modernização + redução de debt + service modernization - atraso - exceções | Architecture Capability, Delivery, Governance | Mensal | Capability Owner / PMO | Modernization Cockpit | Capability Modernization Delayed | Média | Capability, modernization plan, service, initiative | Domain, portfólio |
| Service Modernization Score | Mede progresso de modernização de services. | Architecture Capability / Engineering | Líder Técnico | BusinessService, TechnologyService | progresso de modernização + redução de risco + racionalização - atraso - debt | Architecture, Engineering, Delivery | Mensal | Service Owner | Modernization Cockpit, Technical Leadership Dashboard | Service Modernization Delayed | Média | Service, application service, initiative, debt | Capability, domain |
| Architecture Debt Score | Mede severidade e exposição de dívida arquitetural. | Architecture Capability | Arquiteto Corporativo | ArchitectureDebt | soma ponderada de dívidas por severidade, criticidade, aging e impacto em product/offers | Architecture, Governance | Semanal | Arquiteto Corporativo | Architecture Cockpit, Modernization Cockpit | Architecture Debt Critical | Média | Debt, capability, service, offer, product | Domain, portfolio |
| Architecture Exception Rate | Mede frequência e envelhecimento de exceções arquiteturais. | Architecture Capability / Governance | Arquiteto Corporativo | ArchitectureException | exceções ativas e vencidas / entidades avaliadas ou decisões arquiteturais | Architecture, Governance | Semanal | Governança de Arquitetura | Governance and Evidence Dashboard | Architecture Exception Expired | Alta | Exception, entity, owner, expiration, evidence | Domain, governance |
| Technology Rationalization Score | Mede racionalização tecnológica de services e application services. | Architecture Capability / Engineering | Arquiteto Corporativo | TechnologyService, ApplicationService | redução de redundância + aderência a padrão + modernization - legacy exposure - exceptions | Architecture, Engineering | Mensal | Technology Service Owner | Modernization Cockpit | Technology Rationalization Degraded | Média | Technology service, app service, standard, debt | Capability, domain |
| Offer Adoption Score | Mede adoção de offer por produtos e valor associado. | Architecture Capability / Product | Offer Owner | Offer | products ativos usando offer + outcomes suportados + valor associado - baixa adoção - retirement risk | Product, Architecture, Value Realization | Mensal | Offer Owner | Offer Landscape, Product Value Dashboard | Offer Adoption Low | Média | Offer, product, outcome, value case | Capability, product portfolio |
| Objective to Capability Coverage | Mede cobertura de objetivos estratégicos por capabilities. | Strategy / Architecture Capability | Diretor / Arquiteto | StrategicObjective, Capability | objetivos com capabilities vinculadas / objetivos que exigem suporte arquitetural | Strategy, Architecture | Mensal | Arquiteto Corporativo / PMO | Strategic Alignment Dashboard, Capability Landscape | Objective Without Capability | Média | Objective, capability, domain, owner | Strategy, theme |
| Capability to Initiative Coverage | Mede cobertura de capabilities críticas por iniciativas ativas ou justificativa formal. | Architecture Capability / Portfolio | PMO | Capability, Initiative | capabilities críticas com iniciativa, modernization plan ou justificativa / capabilities críticas | Architecture, Portfolio, Delivery | Semanal | Capability Owner / PMO | Capability Landscape, Portfolio Command Center | Critical Capability Without Initiative | Média | Capability, initiative, modernization plan, owner | Domain, portfolio |
| Capability Traceability Health | Mede integridade de vínculos de capability com objetivos, produtos, iniciativas, KPIs e value cases. | Architecture Capability | Arquiteto Corporativo | Capability | completude + consistência + owner + atualização dos vínculos - gaps | Architecture, Strategy, Product, Delivery, Metrics | Semanal | Arquiteto Corporativo | Capability Landscape, Governance and Evidence Dashboard | Capability Traceability Critical | Média | Capability, objective, product, initiative, KPI | Domain, enterprise |
| Offer Traceability Health | Mede integridade de vínculos entre offer, services, application services e products. | Architecture Capability / Product | Offer Owner | Offer | offers com services, app services, products, owner e vigência / offers ativas | Architecture, Product | Semanal | Offer Owner | Offer Landscape, Product Value Dashboard | Offer Traceability Critical | Média | Offer, service, app service, product association | Capability, domain |

## Value Realization Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Planned Value | Valor esperado declarado no value case. | Value Realization | Diretor | ValueCase | soma de benefícios esperados aprovados | Value Realization, Portfolio, Financeiro | Mensal | Sponsor de valor | Value Realization Dashboard | Value case sem baseline | Média | Benefício, premissa, investimento, evidência | Value case, portfólio, objetivo |
| Forecast Value | Valor previsto com base em tendência, entregas e evidências parciais. | Value Realization | Superintendente | ValueCase | projeção de benefício por cenário e confiança | Value Realization, Metrics, Delivery | Mensal | Sponsor de valor | Value Realization Dashboard, Executive Overview | Forecast de valor degradado | Média | Benefit, forecast driver, KPI, release | Value case, portfólio, objetivo |
| Realized Benefit | Valor medido em período com evidência associada. | Value Realization | Financeiro / PMO | RealizedBenefit | benefício medido conforme método do value case | Value Realization, Financeiro, Analytics | Mensal | Owner de valor | Value Realization Dashboard | Benefício sem evidência | Média | Benefício, evidência, período, fonte | Value case, produto, portfólio |
| Validated Benefit | Benefício realizado validado por autoridade definida. | Value Realization | Diretor | BenefitValidation | soma de benefícios realizados com validação aprovada | Value Realization, Governance | Mensal | Validador de benefício | Value Realization Dashboard, Executive Overview | Benefício pendente de validação | Alta | Validação, evidência, benefício, owner | Value case, objetivo estratégico |
| Benefit Variance | Diferença entre valor planejado, forecast e validado. | Value Realization | Diretor | ValueCase | benefício validado - benefício planejado ou forecast | Value Realization | Mensal | Sponsor de valor | Value Realization Dashboard | Valor não realizado | Média | Benefício, premissa, KPI, iniciativa | Value case, portfólio, objetivo |
| ROI | Relação entre benefício validado e investimento associado. | Value Realization | Diretor | ValueCase, Investment | benefício validado / investimento associado | Value Realization, Portfolio, Financeiro | Mensal | Financeiro / Sponsor | Value Realization Dashboard, Executive Overview | ROI abaixo do esperado | Média | Investimento, benefício, value case | Portfólio, objetivo, enterprise |
| Value Realization Score | Mede saúde geral de realização de valor. | Value Realization | Diretor | ValueCase | benefício validado + evidência + confiança - desvio de forecast - benefício rejeitado | Value Realization, Governance, Metrics | Mensal | Sponsor de valor | Executive Overview, Value Realization Dashboard | Score de valor crítico | Média | Value case, benefício, evidência, forecast | Produto, portfólio, objetivo |

## Observability and Data Quality Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Data Freshness | Mede atualidade dos dados frente à periodicidade esperada. | Observability and Data Quality | Dados / Analytics | SourceSystem, KPI | data atual - última atualização válida | Observability, Source Systems | Contínua / Diária | Dados / Analytics | Observability and Data Quality Dashboard | Fonte atrasada | Alta | Fonte, métrica, carga, período | Domínio, dashboard, enterprise |
| Integration Success Rate | Mede taxa de integrações bem-sucedidas. | Observability and Data Quality | Engenharia / Dados | SourceSystem | execuções bem-sucedidas / execuções totais | Observability, Integration | Contínua / Diária | Engenharia de Dados | Observability and Data Quality Dashboard | Falha de integração | Alta | Integração, fonte, erro, execução | Plataforma, domínio de dados |
| Processing Lag | Mede atraso entre evento/fonte e projeção disponível. | Observability and Data Quality | Dados / Analytics | ObservabilitySignal | horário de disponibilização - horário de origem | Observability | Contínua | Engenharia de Dados | Observability and Data Quality Dashboard | Lag de processamento | Alta | Evento, fonte, projeção, período | Métrica, dashboard, enterprise |
| Calculation Error Rate | Mede erros em cálculos de métricas, scores ou forecasts. | Observability and Data Quality | Especialista | MetricDefinition, Forecast, HealthScore | cálculos com erro / cálculos executados | Observability, Metrics | Diário | Dados / Analytics | Observability and Data Quality Dashboard | Erro de cálculo | Média | Métrica, score, forecast, fonte | Domínio, governança |
| Source Divergence | Mede divergência entre fonte operacional e projeção analítica. | Observability and Data Quality | Especialista | SourceSystem, MeasurementTarget | diferença entre valor da fonte e valor projetado normalizada | Observability, Source Systems, Metrics | Diário | Dados / Analytics | Observability and Data Quality Dashboard | Divergência de fonte | Média | Fonte, target, métrica, período | Domínio, dashboard |
| Data Confidence Score | Mede confiança de dado, métrica ou cálculo. | Observability and Data Quality | Especialista | KPI, MetricDefinition, SourceSystem | completude + frescor + lineage + sucesso de integração - divergências - erros | Observability, Metrics | Diário | Dados / Analytics | Observability and Data Quality Dashboard, Governance and Evidence Dashboard | Confiança baixa | Média | Fonte, métrica, owner, lineage | Dashboard, domínio, enterprise |

## Forecast Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Schedule Forecast Confidence | Mede confiança no forecast de prazo. | Metrics and Intelligence | Gerente | Forecast, Initiative, Feature | qualidade dos drivers + histórico disponível + estabilidade de escopo + confiança de dados + flow health | Delivery, Metrics, Observability | Semanal | Gerente | Initiative Workspace, Portfolio Command Center | Forecast de prazo degradado, Flow Health Degraded | Média | Forecast driver, feature, queue, bottleneck | Iniciativa, portfólio |
| KR Forecast Probability | Mede probabilidade de cumprimento de um key result. | Metrics and Intelligence | Diretor | KeyResult, Forecast | probabilidade derivada de progresso, tendência, iniciativas e riscos | Strategy, Metrics, Delivery | Semanal | Owner do KR | Executive Overview | KR em risco | Média | KR, KPI, iniciativa, driver | OKR, objetivo |
| KPI Forecast Deviation | Mede desvio previsto de KPI contra target. | Metrics and Intelligence | Diretor | KPI, Forecast | valor previsto - target | Metrics, Source Systems | Conforme KPI | Owner da métrica | KPI and Outcomes Dashboard, Executive Overview | KPI com forecast negativo | Média | KPI, fonte, driver, evidência | KR, outcome, objetivo |
| Capacity Forecast Risk | Mede risco futuro de sobrecarga de capacidade. | Metrics and Intelligence | Superintendente | CapacityAllocation | demanda prevista - capacidade disponível, ponderada por criticidade, WIP, queue time e bottlenecks | Portfolio, Organization, Delivery | Semanal | PMO / Superintendente | Portfolio Command Center, Flow Intelligence Dashboard | Capacidade futura sobrecarregada, Bottleneck Detected | Média | Squad, iniciativa, flow stage, queue | Portfólio, enterprise |
| Value Forecast Confidence | Mede confiança no forecast de valor. | Metrics and Intelligence | Diretor | ValueCase, Forecast | qualidade da evidência + estabilidade de premissas + histórico + confiança de fontes | Value Realization, Metrics, Observability | Mensal | Sponsor de valor | Value Realization Dashboard, Executive Overview | Forecast de valor sem confiança | Média | Value case, benefício, KPI, release | Portfólio, objetivo |

## Forecast Quality Metrics

Estas métricas avaliam precisão histórica de previsões. Elas não substituem Forecast Confidence: confidence mede confiança prospectiva; accuracy mede aderência entre previsão anterior e resultado observado.

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Schedule Forecast Accuracy | Mede diferença entre prazo previsto e prazo real. | Metrics and Intelligence / Forecast Quality | Gerente | Forecast, Initiative, Release, Feature | proximidade entre data prevista em baseline de forecast e data real observada | Delivery, Metrics, Observability | Mensal / Por release | Gerente / PMO | Portfolio Command Center, Initiative Workspace, Executive Overview | Forecast Accuracy Degraded | Média | Forecast, baseline, iniciativa, release, feature, driver de erro | Portfólio, objetivo |
| Value Forecast Accuracy | Mede diferença entre valor previsto e valor realizado. | Metrics and Intelligence / Forecast Quality | Diretor | Forecast, ValueCase, RealizedBenefit | proximidade entre valor previsto em forecast e benefício validado observado | Value Realization, Financeiro, Metrics | Mensal | Sponsor de valor / Financeiro | Value Realization Dashboard, Executive Overview, Portfolio Command Center | Forecast Accuracy Degraded, Value Leakage Detected | Média | Value case, benefício, forecast, premissa | Portfólio, objetivo estratégico |
| KPI Forecast Accuracy | Mede diferença entre KPI previsto e KPI efetivamente observado. | Metrics and Intelligence / Forecast Quality | Diretor | Forecast, KPI | proximidade entre valor previsto de KPI e valor observado na fonte governada | Metrics, Source Systems, Observability | Conforme KPI | Owner da métrica | Executive Overview, KPI and Outcomes Dashboard | Forecast Accuracy Degraded, KPI crítico fora do target | Média | KPI, forecast, fonte, período, driver | KR, outcome, objetivo |
| Capacity Forecast Accuracy | Mede diferença entre capacidade prevista e capacidade efetivamente consumida. | Metrics and Intelligence / Forecast Quality | Superintendente | Forecast, CapacityAllocation, Team | proximidade entre capacidade prevista e capacidade consumida por período, squad ou iniciativa | Portfolio, Organization, Delivery | Mensal | PMO / Superintendente | Portfolio Command Center, Flow Intelligence Dashboard | Forecast Accuracy Degraded, capacidade sobrecarregada | Média | Squad, iniciativa, capacidade prevista, capacidade consumida | Portfólio, unidade executiva |

## Search and Intelligence Metrics

| Nome | Descrição | Domínio | Persona Principal | Entidade Medida | Fórmula Conceitual | Fonte Esperada | Periodicidade | Owner | Uso em Dashboard | Alertas Associados | Nível de Confiança | Possibilidade de Drill-down | Possibilidade de Drill-up |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Search Result Explainability | Mede percentual de resultados de busca com contexto, owner, status e caminho de rastreabilidade. | Metrics and Intelligence | Todos | SearchResult | resultados com explicação completa / resultados retornados | Search, Domain Model, Ownership | Diário | Product Owner da plataforma | Search and Intelligence | Resultado sem explicação | Média | Resultado, entidade, owner, evidência | Domínio, persona, jornada |
| Natural Language Answer Confidence | Mede confiança de respostas em linguagem natural. | Metrics and Intelligence | Diretor | IntelligenceAnswer | confiança das fontes + completude de contexto + ausência de lacunas críticas | Search, Metrics, Observability | Contínua | Product Owner da plataforma | Search and Intelligence | Resposta com baixa confiança | Média | Fonte, métrica, entidade, evidência | Pergunta, dashboard, domínio |
| Recommendation Actionability | Mede se recomendações possuem motivo, impacto e próxima ação. | Metrics and Intelligence | PMO | Recommendation | recomendações com ação, owner e impacto / recomendações geradas | Metrics, Alerts, Governance | Semanal | Product Owner da plataforma | Executive Overview, Alerts, Flow Intelligence Dashboard | Recomendação não acionável | Média | Recomendação, alerta, entidade, owner | Dashboard, persona, enterprise |

## Heat Map Enablement

| Heat Map | Métricas Base | Unidade de Agregação | Ações Suportadas |
| --- | --- | --- | --- |
| Enterprise Heat Map | Strategic Health Score, Flow Health Score, Bottleneck Severity, Queue Time, Wait Time, Cost of Delay, Value Leakage, Investment At Risk, Traceability Health Score | objetivo, tema, unidade executiva, portfólio, domínio | priorizar intervenção executiva, remover gargalos transversais, ajustar funding, escalar decisões. |
| Portfolio Heat Map | Portfolio Health Score, Flow Health Score, Bottleneck Count, Bottleneck Severity, Funding Lead Time, Capacity Forecast Risk, Cost of Queue, Cost of Bottleneck, WIP by Flow Stage | portfólio, investimento, iniciativa, dependência | rebalancear capacidade, acelerar funding, resolver dependências, reordenar iniciativas. |
| Delivery Heat Map | Initiative Health Score, Lead Time, Release Lead Time, Queue Time, Aging WIP, Blocked Time, Flow Efficiency, Delay Impact Score, Schedule Forecast Accuracy | iniciativa, épico, feature, release | destravar entrega, ajustar planos, remover filas, corrigir previsibilidade. |
| Squad Heat Map | WIP by Flow Stage, Work Item Staleness, Touch Time, Wait Time, Blocked Time, Throughput, Aging WIP, Flow Efficiency | squad, owner, flow stage, story, task | reduzir WIP, redistribuir trabalho, resolver bloqueios, melhorar cadence. |
| Business Discovery Heat Map | Business Discovery Health, Business Discovery Lead Time, Traceability Health Score, Evidence Coverage | business need, pain point, journey, process, owner | qualificar necessidade, exigir evidência, descartar demandas sem problema claro. |
| Requirements Heat Map | Requirements Health, Requirements Queue Time, Review Time, Approval Time, Traceability Health Score | requisito, reviewer, owner, produto, iniciativa | destravar revisão, corrigir requisitos, priorizar critérios críticos. |
| Architecture Review Heat Map | Architecture Review Health, Review Time, Approval Time, Architecture Debt Score, Architecture Exception Rate | capability, service, solution design, reviewer | destravar revisão arquitetural, registrar exceção ou remediação. |
| Engineering Review Heat Map | Engineering Review Health, Review Time, Technical Delivery Health, Technical Debt Exposure | service, feature, release, reviewer | remover pendências técnicas, revisar viabilidade e risco. |
| Readiness Heat Map | Readiness Health, Readiness Time, Queue Time, Blocker Resolution Health, Capacity Forecast Risk | readiness assessment, feature, story, squad | impedir entrada sem DOR, resolver dependências e capacidade. |
| Validation Heat Map | Validation Health, Validation Time, Time to Value, Evidence Coverage | validation, criterion, outcome, value case | acelerar aceite, completar evidência e conectar outcome a valor. |
| Blocker Heat Map | Blocker Resolution Health, Blocked Time, Blocker Resolution Time, Bottleneck Severity | blocker, owner, cause, entity, squad | tratar bloqueadores antigos, escalonar owners e reduzir blocked time. |
| Alert Heat Map | Alert Resolution Health, Alert Aging, Alert Resolution Time, Evidence Coverage, Decision Latency | alert, owner, action, evidence, validation | manter alertas abertos até ação, evidência e validação efetiva. |
| Capability Heat Map | Capability Health Score, Capability Coverage, Capability Modernization Score, Architecture Debt Score, Capability Traceability Health | domain, subdomain, business layer, capability | priorizar capability crítica, modernização e correção de rastreabilidade. |
| Service Heat Map | Service Health Score, Service Modernization Score, Technology Rationalization Score, Architecture Debt Score | business service, technology service, application service | priorizar modernização, racionalização e remediação de serviço. |
| Offer Heat Map | Offer Health Score, Offer Adoption Score, Offer Traceability Health, Product Health Score | offer, product, service, application service | revisar composição de produto e offers com baixa adoção ou risco. |

### Heat Map Dimensions

| Dimensão | Composição Conceitual | Uso Principal |
| --- | --- | --- |
| Flow | Flow Health Score, Queue Time, Wait Time, Flow Efficiency, Bottleneck Count, Bottleneck Severity, WIP by Flow Stage, Work Item Staleness. | Tornar filas, gargalos, esperas e desperdícios visíveis por nível corporativo. |
| Capacity | Capacity Allocation Fit, Capacity Forecast Risk, Capacity Forecast Accuracy, Throughput, WIP by Flow Stage, Cost of Queue. | Identificar sobrecarga, desalinhamento de capacidade e capacidade presa em filas. |
| Value | Planned Value, Forecast Value, Realized Benefit, Validated Benefit, ROI, Time to Value, Cost of Delay, Value Leakage. | Mostrar onde valor esperado está sendo realizado, atrasado, perdido ou degradado. |
| Risk | Investment At Risk, Initiative Risk Exposure, Dependency Aging, Delay Impact Score, Integration Risk Score, Technical Debt Exposure. | Priorizar riscos com impacto financeiro, estratégico ou operacional. |
| Governance | Committee Readiness, Approval Aging, Decision SLA, Decision Latency, Decision Throughput, Decision Rework Rate, Evidence Coverage, Control Adherence Rate. | Tornar decisões lentas, gates envelhecidos e lacunas de evidência acionáveis. |
| Data Quality | Data Freshness, Integration Success Rate, Processing Lag, Calculation Error Rate, Source Divergence, Data Confidence Score, Lineage Completeness. | Expor confiabilidade das leituras executivas e impedir decisões com dados frágeis. |
| Strategic Alignment | Strategic Alignment Coverage, Traceability Health Score, Traceability Gap Count, Objective Funding Coverage, KPI Target Deviation, OKR Achievement Forecast. | Verificar se execução, funding, métricas e valor continuam conectados à estratégia. |
| Operating Flow | Business Discovery Health, Requirements Health, Solution Health, Readiness Health, Validation Health, Alert Resolution Health, Blocker Resolution Health. | Verificar onde o fluxo Need-to-Value está parado, quem deveria agir e qual evidência falta. |
| Architecture | Capability Health Score, Service Health Score, Offer Health Score, Product Health Score, Architecture Debt Score, Modernization Scores, Traceability Health. | Verificar saúde, cobertura, modernização, dívida e impacto de capabilities, services e offers. |

## Alertas Conceituais

| Alerta | Condição Conceitual | Métricas Acionadoras | Ação Esperada |
| --- | --- | --- | --- |
| Queue Threshold Breached | Queue excede limite de idade, volume ou criticidade definido para o flow stage. | Queue Time, WIP by Flow Stage, Approval Aging | Owner do stage deve revisar fila, remover impedimento ou escalar decisão. |
| Bottleneck Detected | Restrição persistente ou recorrente degrada throughput, prazo, valor ou capacidade. | Bottleneck Count, Bottleneck Severity, Throughput, Queue Time | Registrar gargalo, atribuir owner, definir causa provável e plano de ação. |
| Bottleneck Severity Increased | Severidade de gargalo aumenta por duração, impacto, recorrência ou escopo afetado. | Bottleneck Severity, Flow Health Score, Investment At Risk | Escalar para portfólio ou comitê conforme impacto. |
| Flow Health Degraded | Flow Health Score cai abaixo de threshold ou apresenta tendência negativa relevante. | Flow Health Score, Flow Efficiency, Aging WIP, Wait Time | Revisar heat map, priorizar gargalos e atualizar plano de mitigação. |
| Work Item Stale | Item ativo fica sem avanço ou atualização significativa além do limite. | Work Item Staleness, Aging WIP, Touch Time | Owner deve atualizar status, remover bloqueio ou replanejar. |
| Waiting Stage Aging Breached | Item permanece em estágio de espera além do limite esperado. | Wait Time, Queue Time, Aging WIP | Scrum Master ou PMO deve identificar causa e acionar owner. |
| Approval Aging Breached | Aprovação, decision gate ou funding permanece pendente além do SLA. | Approval Aging, Funding Lead Time, Decision SLA | PMO deve escalar gate, registrar decisão ou formalizar impedimento. |
| Cost of Delay Critical | Atraso ultrapassa limite econômico, estratégico ou temporal definido para iniciativa, feature, release ou benefício. | Cost of Delay, Delay Impact Score, Time to Value | Sponsor e PMO devem decidir aceleração, replanejamento, descopo ou escalonamento executivo. |
| Value Leakage Detected | Valor esperado deixa de ser capturado ou apresenta perda material por atraso, cancelamento, baixa adoção ou benefício não realizado. | Value Leakage, Benefit Variance, Value Forecast Accuracy, Hypothesis Validation Accuracy | Product Owner e sponsor devem identificar causa de perda e atualizar plano de realização de valor. |
| Forecast Accuracy Degraded | Previsões históricas ficam materialmente distantes dos resultados observados. | Schedule Forecast Accuracy, Value Forecast Accuracy, KPI Forecast Accuracy, Capacity Forecast Accuracy | Owner do forecast deve revisar premissas, drivers e confiança de dados. |
| Traceability Health Critical | Rastreabilidade apresenta lacunas, inconsistência, ownership ausente ou vínculos desatualizados em cadeia crítica. | Traceability Health Score, Strategic Alignment Coverage, Traceability Gap Count | PMO deve corrigir vínculos, owners e evidências antes de decisão crítica. |
| Decision Latency Critical | Tempo entre identificação do problema e decisão ultrapassa limite de risco, valor ou governança. | Decision Latency, Approval Aging, Decision SLA, Funding Lead Time | PMO deve escalar gate, remover ambiguidade decisória ou formalizar impedimento. |
| Discovery Quality Degraded | Discovery avança com baixa evidência, hipóteses frágeis, baixo readiness ou retrabalho recorrente. | Discovery Quality Score, Discovery Rework Rate, Hypothesis Validation Accuracy | Product Owner deve reforçar evidências, revisar hipóteses e evitar compromisso prematuro de capacidade. |
| Requirements Quality Alert | Requisitos apresentam baixa rastreabilidade, critérios ausentes, rejeições recorrentes ou aging elevado. | Requirements Health, Requirements Queue Time, Review Time | Product Owner deve corrigir origem, critérios, owner e evidências antes de solution design. |
| Solution Review Alert | Solution design está pendente, rejeitado ou com reviews críticos vencidos. | Solution Health, Solution Time, Review Time, Architecture Review Health, Engineering Review Health | Solution Owner deve resolver pendências, registrar exceções ou revisar escopo. |
| Readiness Alert | Item tenta avançar sem DOR, capacidade, dependência tratada ou evidência obrigatória. | Readiness Health, Readiness Time, Blocker Resolution Health | Scrum Master ou Delivery Owner deve bloquear entrada, completar readiness ou formalizar exceção. |
| Alert Resolution Failed | Alerta foi encerrado sem condição removida, reaberto ou sem evidência suficiente. | Alert Resolution Health, Alert Aging, Alert Resolution Time | PMO deve reabrir tratamento, exigir ação, evidência e validação da condição original. |
| Architecture Debt Critical | Dívida arquitetural crítica afeta capability, service, offer, application service ou produto. | Architecture Debt Score, Capability Health Score, Service Health Score | Arquiteto Corporativo deve criar plano, associar iniciativa ou registrar aceite formal de risco. |
| Capability Traceability Critical | Capability crítica possui lacuna de rastreabilidade com objetivo, produto, iniciativa, KPI ou value case. | Capability Traceability Health, Objective to Capability Coverage, Capability to Initiative Coverage | Capability Owner deve corrigir vínculos ou registrar justificativa formal. |

## Métricas Críticas Por Dashboard

| Dashboard | Métricas Obrigatórias |
| --- | --- |
| Executive Overview | Strategic Health Score, OKR Achievement Forecast, Portfolio Health Score, Flow Health Score, Bottleneck Severity, Investment At Risk, Cost of Delay, Delay Impact Score, Value Leakage, KPI Target Deviation, Time to Value, Value Realization Score, Decision Latency |
| Strategic Alignment Dashboard | Strategic Alignment Coverage, Traceability Health Score, Objective Funding Coverage, OKR Achievement Forecast, Key Result Progress, KPI Target Deviation, Traceability Gap Count |
| Portfolio Command Center | Portfolio Health Score, Capacity Allocation Fit, Funding Variance, Funding Lead Time, Dependency Aging, Initiative Risk Exposure, Bottleneck Count, Bottleneck Severity, Flow Health Score, WIP by Flow Stage, Cost of Queue, Cost of Bottleneck, Schedule Forecast Accuracy, Decision Throughput |
| Product Value Dashboard | Product Outcome Progress, Product Health Score, Backlog Strategic Alignment, Feature Value Score, Adoption Trend, Time to Outcome, Discovery Lead Time, Discovery Quality Score, Discovery Rework Rate, Hypothesis Validation Accuracy |
| Initiative Workspace | Initiative Health Score, Delivery Health Score, Milestone Adherence, Epic Completion Rate, Queue Time, Bottleneck Severity, Approval Aging, Release Lead Time, Time to Value, Cost of Delay, Delay Impact Score |
| Delivery Flow Dashboard | Lead Time, Cycle Time, Touch Time, Queue Time, Wait Time, Aging WIP, Blocked Time, Throughput, WIP by Flow Stage, Flow Efficiency, Commitment Reliability |
| Flow Intelligence Dashboard | Flow Health Score, Queue Time, Wait Time, Touch Time, Flow Efficiency, Bottleneck Count, Bottleneck Severity, Aging WIP, Work Item Staleness, Throughput, WIP by Flow Stage, Blocked Time, Approval Aging, Discovery Lead Time, Funding Lead Time, Release Lead Time, Time to Value, Cost of Queue, Cost of Bottleneck |
| Technical Leadership Dashboard | Technical Delivery Health, Technical Debt Exposure, Release Readiness, Release Lead Time, Defect Leakage, Rework Rate, Technical Blocker Aging, Integration Risk Score |
| Business Discovery Dashboard | Business Discovery Health, Business Discovery Lead Time, Evidence Coverage, Traceability Health Score |
| Requirements Dashboard | Requirements Health, Requirements Queue Time, Review Time, Approval Time, Traceability Health Score |
| Solution Review Dashboard | Solution Health, Solution Time, Review Time, Approval Time, Architecture Review Health, Engineering Review Health |
| Readiness Dashboard | Readiness Health, Readiness Time, Queue Time, Blocker Resolution Health, Capacity Forecast Risk |
| Validation Dashboard | Validation Health, Validation Time, Time to Value, Evidence Coverage, Value Realization Score |
| Architecture Cockpit | Capability Health Score, Service Health Score, Offer Health Score, Product Health Score, Architecture Debt Score, Architecture Exception Rate |
| Capability Landscape | Capability Health Score, Capability Coverage, Capability Modernization Score, Objective to Capability Coverage, Capability Traceability Health |
| Service Landscape | Service Health Score, Service Modernization Score, Technology Rationalization Score, Architecture Debt Score |
| Offer Landscape | Offer Health Score, Offer Adoption Score, Offer Traceability Health, Product Health Score |
| Modernization Cockpit | Capability Modernization Score, Service Modernization Score, Architecture Debt Score, Technology Rationalization Score |
| Governance and Evidence Dashboard | Evidence Coverage, Control Adherence Rate, Approval Cycle Time, Approval Aging, Compliance Issue Count, Decision SLA, Decision Latency, Decision Rework Rate, Metric Ownership Coverage, Lineage Completeness, Traceability Health Score, Alert Resolution Health |
| Value Realization Dashboard | Planned Value, Forecast Value, Realized Benefit, Validated Benefit, Benefit Variance, ROI, Time to Value, Value Realization Score, Value Forecast Accuracy, Cost of Delay, Value Leakage |
| Observability and Data Quality Dashboard | Data Freshness, Integration Success Rate, Processing Lag, Calculation Error Rate, Source Divergence, Data Confidence Score |

## Regras de Governança do Catálogo

- Métrica nova deve declarar entidade medida e owner antes de entrar em dashboard executivo.
- Métrica usada em comitê deve possuir fonte esperada, periodicidade e nível de confiança.
- Métrica com confiança baixa deve continuar visível, mas não pode ser apresentada como fato sem ressalva.
- Métrica sem owner deve gerar alerta de governança.
- Métrica sem atualização dentro da periodicidade deve gerar alerta de frescor.
- Fórmula conceitual deve ser compreensível sem acesso a implementação técnica.
- Toda métrica crítica deve permitir drill-down para entidades causadoras, evidências e owners.
- Toda métrica crítica deve permitir drill-up para iniciativa, portfólio, objetivo ou nível enterprise quando aplicável.
- Métrica de Flow Intelligence deve indicar se suporta análise de queue, bottleneck, heat map, waste ou plano de ação.
- Flow Health Score deve permanecer distinto de Delivery Health Score: delivery mede execução e compromissos; flow mede fluidez, espera, filas, gargalos e desperdício.
- Métrica de operating model deve indicar etapa Need-to-Value, owner, SLA, aging e evento de entrada/saída esperado.
- Métrica de resolução de alerta deve considerar resolução válida apenas quando existir ação, evidência e validação da condição original.
- Métrica de arquitetura deve preservar distinção entre Product, Capability, Service e Offer.

## Change Log

### Métricas Adicionadas

- Queue Time.
- Wait Time.
- Touch Time.
- Flow Health Score.
- Bottleneck Count.
- Bottleneck Severity.
- Work Item Staleness.
- Throughput.
- WIP by Flow Stage.
- Blocked Time.
- Approval Aging.
- Discovery Lead Time.
- Funding Lead Time.
- Release Lead Time.
- Delivery Health Score.
- Cost of Delay.
- Cost of Queue.
- Cost of Bottleneck.
- Delay Impact Score.
- Value Leakage.
- Discovery Quality Score.
- Discovery Rework Rate.
- Hypothesis Validation Accuracy.
- Traceability Health Score.
- Schedule Forecast Accuracy.
- Value Forecast Accuracy.
- KPI Forecast Accuracy.
- Capacity Forecast Accuracy.
- Decision Latency.
- Decision Throughput.
- Decision Rework Rate.
- Governance Health Score.
- Business Discovery Lead Time.
- Business Discovery Health.
- Requirements Health.
- Requirements Queue Time.
- Review Time.
- Approval Time.
- Solution Time.
- Solution Health.
- Architecture Review Health.
- Engineering Review Health.
- Readiness Time.
- Readiness Health.
- Validation Time.
- Validation Health.
- Alert Aging.
- Alert Resolution Time.
- Alert Resolution Health.
- Blocker Resolution Health.
- Capability Health Score.
- Capability Coverage.
- Service Health Score.
- Offer Health Score.
- Capability Modernization Score.
- Service Modernization Score.
- Architecture Debt Score.
- Architecture Exception Rate.
- Technology Rationalization Score.
- Offer Adoption Score.
- Objective to Capability Coverage.
- Capability to Initiative Coverage.
- Capability Traceability Health.
- Offer Traceability Health.

### Métricas Revisadas

- Flow Efficiency foi reposicionada em Flow Intelligence e definida por touch time sobre lead time.
- Aging WIP foi revisada para considerar flow stage e item em estágio não final.
- Time to Value foi ampliada para conectar entrega, release, benefício validado e Flow Intelligence.
- Strategic Health Score passou a considerar traceability health, delay impact e decision latency.
- Portfolio Health Score passou a considerar Flow Health Score, forecast accuracy, cost of delay e economics of flow.
- Initiative Health Score passou a considerar Flow Health Score, cost of delay e decision latency.
- Flow Health Score passou a considerar cost of queue e cost of bottleneck sem deixar de ser score de fluxo.
- Value Realization Score passou a considerar value forecast accuracy, value leakage e time to value.
- Capacity Forecast Risk passou a considerar WIP, queue time e bottlenecks.
- Dependency Aging passou a alimentar Flow Intelligence e detecção de gargalos.
- Technical Blocker Aging passou a alimentar Bottleneck Detected quando bloqueios técnicos degradam fluxo.
- Métricas críticas por dashboard foram revisadas para incluir Delivery Flow Dashboard, Flow Intelligence Dashboard, Portfolio Command Center, Initiative Workspace e Executive Overview.
- Heat Map Enablement foi revisado para incorporar dimensões de Flow, Capacity, Value, Risk, Governance, Data Quality e Strategic Alignment.
- Health Scores Governados foi revisado para incluir Business Discovery Health, Requirements Health, Solution Health, Architecture Review Health, Engineering Review Health, Readiness Health, Validation Health, Alert Resolution Health e Blocker Resolution Health.
- Product Health Score foi revisado para considerar composição de offers e sinais arquiteturais sem confundir Product com Capability, Service ou Offer.
- Governance and Evidence Dashboard foi revisado para incluir Alert Resolution Health.
- Governance Health Score foi formalizado como score próprio para consolidar decisão, evidência, controle, exceção e resolução de alertas.

### Dashboards Impactados

- Executive Overview recebeu Cost of Delay, Delay Impact Score, Value Leakage e Decision Latency.
- Portfolio Command Center recebeu Cost of Queue, Cost of Bottleneck, Schedule Forecast Accuracy e Decision Throughput.
- Flow Intelligence Dashboard recebeu Cost of Queue e Cost of Bottleneck como sinais econômicos de filas e gargalos.
- Value Realization Dashboard recebeu Value Forecast Accuracy, Cost of Delay e Value Leakage.
- Governance and Evidence Dashboard recebeu Decision Latency, Decision Rework Rate e Traceability Health Score.
- Product Value Dashboard recebeu Discovery Quality Score, Discovery Rework Rate e Hypothesis Validation Accuracy.
- Strategic Alignment Dashboard recebeu Traceability Health Score.
- Business Discovery Dashboard, Requirements Dashboard, Solution Review Dashboard, Readiness Dashboard, Validation Dashboard, Architecture Cockpit, Capability Landscape, Service Landscape, Offer Landscape e Modernization Cockpit foram adicionados ao catálogo de métricas críticas.
- Heat maps operacionais e arquiteturais foram incorporados como consumidores formais de métricas.

### Alertas Adicionados

- Cost of Delay Critical.
- Value Leakage Detected.
- Forecast Accuracy Degraded.
- Traceability Health Critical.
- Decision Latency Critical.
- Discovery Quality Degraded.
- Requirements Quality Alert.
- Solution Review Alert.
- Readiness Alert.
- Alert Resolution Failed.
- Architecture Debt Critical.
- Capability Traceability Critical.

### Métricas Preservadas

- Strategic Health Score.
- Strategic Alignment Coverage.
- Objective Funding Coverage.
- OKR Achievement Forecast.
- Key Result Progress.
- KPI Target Deviation.
- Capacity Allocation Fit.
- Funding Variance.
- Investment At Risk.
- Initiative Risk Exposure.
- Opportunity Conversion Rate.
- Committee Readiness.
- Product Outcome Progress.
- Product Health Score.
- Backlog Strategic Alignment.
- Feature Value Score.
- Roadmap Confidence.
- Adoption Trend.
- Time to Outcome.
- Milestone Adherence.
- Epic Completion Rate.
- Lead Time.
- Cycle Time.
- Commitment Reliability.
- Traceability Gap Count.
- Blocked Work Count.
- Blocker Resolution Time.
- Technical Delivery Health.
- Technical Debt Exposure.
- Release Readiness.
- Defect Leakage.
- Rework Rate.
- Integration Risk Score.
- Standard Exception Aging.
- Evidence Coverage.
- Control Adherence Rate.
- Approval Cycle Time.
- Compliance Issue Count.
- Decision SLA.
- Metric Ownership Coverage.
- Lineage Completeness.
- Planned Value.
- Forecast Value.
- Realized Benefit.
- Validated Benefit.
- Benefit Variance.
- ROI.
- Value Realization Score.
- Data Freshness.
- Integration Success Rate.
- Processing Lag.
- Calculation Error Rate.
- Source Divergence.
- Data Confidence Score.
- Schedule Forecast Confidence.
- KR Forecast Probability.
- KPI Forecast Deviation.
- Capacity Forecast Risk.
- Value Forecast Confidence.
- Search Result Explainability.
- Natural Language Answer Confidence.
- Recommendation Actionability.
