# Product Model - Enterprise Delivery Intelligence Platform (EDIP)

## Objetivo

Este documento define a experiência de uso da EDIP. Ele descreve como a plataforma deve ser percebida e operada por usuários executivos, táticos, operacionais, técnicos e especialistas em uma instituição financeira.

A EDIP é uma plataforma corporativa de inteligência sobre entrega e valor. Ela conecta estratégia, portfólio, produto, delivery, engenharia, governança, observabilidade e value realization em uma experiência única de decisão, investigação e explicação.

Este documento deve permitir que UX, arquitetura e engenharia projetem fluxos, dashboards, contratos, permissões, dados e interações sem ambiguidades conceituais.

## 1. Princípios de Produto

### Estratégia Dirige Execução

Toda experiência da EDIP deve partir da premissa de que trabalho relevante precisa ter vínculo explícito com estratégia, objetivo, OKR, outcome, KPI, portfólio ou justificativa formal.

Trabalho sem rastreabilidade deve ser tratado como exceção visível, não como item neutro.

### Uma Verdade, Múltiplas Perspectivas

A EDIP deve apresentar a mesma verdade de dados para diferentes personas, variando profundidade, linguagem, filtros e ações disponíveis.

Nenhuma persona deve operar com indicadores, status ou scores incompatíveis com os demais níveis da organização.

### Drill-down Obrigatório

Todo dashboard, score, alerta, forecast e KPI deve permitir navegação até os componentes que explicam sua origem.

Agregações sem capacidade de investigação não devem ser consideradas inteligência corporativa.

### Drill-up Obrigatório

Todo item operacional deve permitir subida até sua justificativa estratégica.

Uma task deve conseguir explicar sua story, feature, épico, iniciativa, portfólio, KPI, outcome, OKR e objetivo quando a rastreabilidade existir.

### Métricas Como Produtos Governados

Todo KPI deve possuir owner, fórmula, fonte, baseline, target, periodicidade, lineage, nível de confiança e interpretação.

Indicadores sem owner ou sem fonte confiável devem aparecer como risco de governança.

### Decisão Com Evidência

Decisões de priorização, funding, pausa, cancelamento, mudança de escopo, aceite de risco, exceção arquitetural, aprovação de métrica e realização de valor devem ser registradas com justificativa e evidência.

### Forecast Explicável

Forecasts devem expor premissas, horizonte, drivers, nível de confiança, dados usados e limitações.

Forecast sem explicabilidade não deve ser usado para decisão crítica.

### Problemas Visíveis Por Padrão

Lacunas de rastreabilidade, dependências vencidas, KPIs sem owner, dados atrasados, benefícios não comprovados e scores críticos devem ser expostos de forma ativa.

A EDIP deve reduzir o esforço de descoberta de problemas, não apenas reportar problemas conhecidos.

## 2. Personas

### Diretor

**Objetivos**

- Avaliar execução da estratégia corporativa.
- Identificar objetivos, OKRs, KPIs e portfólios em risco.
- Priorizar investimentos, capacidade e decisões executivas.
- Validar se valor planejado está sendo realizado.

**Perguntas Frequentes**

- Quais objetivos estratégicos estão em risco?
- Quais portfólios consomem mais investimento e entregam menos valor?
- Quais KPIs críticos estão fora do target?
- Quais decisões dependem de mim ou do comitê?
- Onde há vazamento de valor?

**Decisões Suportadas**

- Repriorizar temas estratégicos.
- Aprovar, pausar, cancelar ou acelerar iniciativas.
- Realocar funding entre portfólios.
- Escalar dependências entre diretorias.
- Acionar plano de recuperação para KPI crítico.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Strategic Health Score | Saúde geral da execução estratégica. |
| OKR Achievement Forecast | Probabilidade de cumprimento dos OKRs no ciclo. |
| Portfolio Value Realization | Valor realizado versus planejado por portfólio. |
| Investment At Risk | Investimento exposto por iniciativas críticas. |
| KPI Target Deviation | Desvio entre target e valor atual. |
| Critical Decision Aging | Tempo de decisões executivas pendentes. |

### Superintendente

**Objetivos**

- Orquestrar portfólios, capacidade, riscos e dependências.
- Garantir que iniciativas estejam alinhadas a temas e objetivos.
- Antecipar desvios de prazo, valor e capacidade.
- Preparar decisões para diretoria.

**Perguntas Frequentes**

- Quais iniciativas ameaçam o compromisso do trimestre?
- Onde a capacidade está sobrecarregada?
- Quais dependências estão bloqueando valor?
- Quais oportunidades devem virar iniciativas?
- Qual forecast exige replanejamento?

**Decisões Suportadas**

- Rebalancear capacidade.
- Recomendar priorização, pausa ou aceleração.
- Escalar dependências.
- Ajustar compromissos trimestrais.
- Solicitar revisão de business case ou KPI.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Portfolio Health Score | Saúde consolidada da carteira. |
| Capacity Allocation Fit | Aderência da capacidade aos temas prioritários. |
| Dependency Aging | Tempo de dependências abertas. |
| Initiative Risk Exposure | Exposição por iniciativas em risco. |
| Forecast Confidence | Confiança nas projeções de entrega e valor. |
| Opportunity Conversion Rate | Efetividade do funil de oportunidades. |

### Gerente

**Objetivos**

- Gerir iniciativas, escopo, riscos, dependências e progresso.
- Conectar execução a outcomes e KPIs.
- Preparar status tático confiável.
- Acionar impedimentos e decisões de portfólio.

**Perguntas Frequentes**

- Minha iniciativa contribui para qual objetivo e KPI?
- Quais épicos e features estão atrasando o outcome?
- Quais riscos precisam de mitigação?
- O forecast de prazo e valor é confiável?
- O que deve ser escalado?

**Decisões Suportadas**

- Replanejar escopo.
- Ajustar prioridade de épicos e features.
- Abrir, mitigar ou escalar riscos.
- Acionar owners de dependências.
- Solicitar decisão de portfólio.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Initiative Health Score | Saúde geral da iniciativa. |
| Milestone Adherence | Cumprimento de marcos. |
| Epic Completion Rate | Progresso de escopo relevante. |
| Risk Burn-down | Evolução dos riscos. |
| Dependency Resolution Time | Efetividade de desbloqueio. |
| KPI Contribution Confidence | Confiança de impacto no KPI. |

### Coordenador

**Objetivos**

- Coordenar execução operacional.
- Remover bloqueios e dependências.
- Acompanhar aging, WIP, owners e compromissos.
- Manter rastreabilidade de features, stories e tasks.

**Perguntas Frequentes**

- Quais itens estão bloqueados?
- Quais stories estão envelhecendo?
- Que tasks impactam uma feature crítica?
- O time trabalha no que está mais alinhado?
- Que dependência deve ser escalada?

**Decisões Suportadas**

- Reordenar execução operacional.
- Escalar bloqueios.
- Ajustar planejamento de ciclo.
- Sinalizar risco de feature.
- Corrigir lacunas de rastreabilidade operacional.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Aging WIP | Risco de itens parados. |
| Blocked Work Count | Volume de bloqueios ativos. |
| Flow Efficiency | Eficiência de fluxo. |
| Commitment Reliability | Previsibilidade do time. |
| Backlog Traceability Rate | Aderência de backlog ao modelo EDIP. |

### Product Owner

**Objetivos**

- Maximizar valor do produto.
- Priorizar oportunidades, épicos, features e stories.
- Conectar backlog a outcomes, KPIs e estratégia.
- Validar hipóteses de valor.

**Perguntas Frequentes**

- Quais features geram maior impacto esperado?
- O backlog está alinhado a outcomes e OKRs?
- Que oportunidades têm evidência suficiente?
- Que KPI será impactado pela próxima release?
- Que item deve sair do roadmap?

**Decisões Suportadas**

- Priorizar backlog.
- Converter oportunidade em iniciativa, épico ou experimento.
- Ajustar roadmap.
- Aceitar, rejeitar ou replanejar stories.
- Solicitar revisão de hipótese ou KPI.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Product Outcome Progress | Progresso contra outcomes do produto. |
| Backlog Strategic Alignment | Alinhamento do backlog à estratégia. |
| Feature Value Score | Valor esperado por feature. |
| Opportunity Validation Rate | Qualidade do discovery. |
| Adoption Trend | Evolução de adoção ou uso. |
| Time to Outcome | Tempo até evidência de resultado. |

### Scrum Master

**Objetivos**

- Promover fluxo, previsibilidade e melhoria contínua.
- Reduzir impedimentos, WIP e aging.
- Tornar gargalos visíveis.
- Conectar métricas de fluxo a compromissos de delivery.

**Perguntas Frequentes**

- Onde o fluxo está travando?
- Quais bloqueios são recorrentes?
- O WIP está acima do aceitável?
- O compromisso do ciclo é realista?
- O time tem dependências externas críticas?

**Decisões Suportadas**

- Recomendar redução de WIP.
- Escalar impedimentos.
- Ajustar sequência de trabalho.
- Sinalizar risco de compromisso.
- Propor melhoria de processo.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Team Flow Health | Saúde operacional do time. |
| Lead Time | Tempo de entrega. |
| Cycle Time | Tempo em execução. |
| Blocker Resolution Time | Eficiência de desbloqueio. |
| Commitment Reliability | Confiabilidade de compromisso. |
| Traceability Gap Count | Lacunas de vínculo no backlog. |

### Arquiteto Corporativo

**Objetivos**

- Garantir aderência a capacidades, padrões, integrações, dados, segurança e resiliência.
- Avaliar impacto arquitetural de iniciativas e features.
- Tornar riscos técnicos estruturais visíveis.
- Conectar débitos técnicos a risco, KPI e valor.

**Perguntas Frequentes**

- Quais iniciativas impactam capacidades críticas?
- Há exceções arquiteturais vencidas?
- Que integração representa risco sistêmico?
- Qual débito técnico ameaça um outcome?
- A solução reutiliza capacidades existentes?

**Decisões Suportadas**

- Aprovar ou rejeitar aderência arquitetural.
- Solicitar ajuste de solução.
- Aceitar exceção com prazo e owner.
- Priorizar tratamento de débito técnico.
- Recomendar build, buy, reuse ou retire.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Architecture Compliance Rate | Aderência a padrões. |
| Critical Architecture Risk Count | Riscos arquiteturais críticos. |
| Technical Debt Exposure | Exposição de dívida técnica. |
| Capability Impact Coverage | Cobertura de mapeamento por capacidade. |
| Integration Risk Score | Risco de integração. |
| Standard Exception Aging | Envelhecimento de exceções. |

### PMO

**Objetivos**

- Governar portfólio, status, funding, decisões e dependências.
- Reduzir consolidação manual.
- Garantir qualidade de dados para comitês.
- Dar visibilidade a inconsistências de governança.

**Perguntas Frequentes**

- Quais iniciativas estão sem atualização confiável?
- Quais decisões estão vencidas?
- O comitê tem evidência suficiente?
- Qual portfólio está com maior risco?
- Onde há inconsistência de funding ou capacidade?

**Decisões Suportadas**

- Preparar pauta de comitê.
- Solicitar atualização de status.
- Escalar decisões e dependências.
- Recomendar replanejamento.
- Validar prontidão para funding ou gate.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Portfolio Governance Health | Saúde de governança da carteira. |
| Status Freshness | Atualidade de status. |
| Traceability Compliance | Aderência à rastreabilidade. |
| Decision SLA | Prazo de decisões. |
| Funding Variance | Variação entre aprovado, consumido e forecast. |
| Committee Readiness | Prontidão para comitês. |

### Especialista

**Objetivos**

- Validar métricas, evidências, controles, riscos, compliance, dados, produto ou processo.
- Garantir auditabilidade e confiabilidade.
- Identificar riscos regulatórios, operacionais, técnicos ou de dados.

**Perguntas Frequentes**

- A métrica possui owner, fórmula e lineage?
- Há evidência suficiente para decisão?
- O controle aplicável foi atendido?
- A fonte de dados é confiável?
- Existe exceção sem prazo ou owner?

**Decisões Suportadas**

- Validar ou rejeitar métrica.
- Aprovar ou reprovar evidência.
- Apontar risco ou não conformidade.
- Solicitar correção de fonte, fórmula ou owner.
- Aceitar exceção auditável.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Evidence Coverage | Cobertura de evidências. |
| Metric Ownership Coverage | Indicadores com owner. |
| Data Confidence Score | Confiança de dados. |
| Compliance Issue Count | Pendências de compliance. |
| Control Adherence Rate | Aderência a controles. |
| Lineage Completeness | Completude de lineage. |

### Líder Técnico

**Objetivos**

- Garantir execução técnica saudável.
- Conectar débitos, riscos, releases e decisões técnicas ao contexto de produto e estratégia.
- Avaliar prontidão técnica de entrega.

**Perguntas Frequentes**

- Que risco técnico ameaça a release?
- Que débito deve ser priorizado?
- Qual serviço ou integração está afetando a iniciativa?
- A feature está tecnicamente pronta?
- Que decisão arquitetural está pendente?

**Decisões Suportadas**

- Priorizar dívida técnica.
- Escalar dependências técnicas.
- Validar readiness de release.
- Recomendar abordagem técnica.
- Solicitar decisão arquitetural.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Technical Delivery Health | Saúde técnica da execução. |
| Technical Debt Exposure | Impacto de dívida técnica. |
| Release Readiness | Prontidão de release. |
| Defect Leakage | Defeitos escapados. |
| Rework Rate | Retrabalho técnico. |
| Technical Blocker Aging | Bloqueios técnicos envelhecidos. |

### Desenvolvedor

**Objetivos**

- Executar stories e tasks com clareza de propósito.
- Entender critérios, dependências, prioridade e impacto.
- Sinalizar bloqueios e lacunas de rastreabilidade.

**Perguntas Frequentes**

- Esta task contribui para qual feature e iniciativa?
- Qual é o critério de aceite?
- Qual dependência bloqueia meu trabalho?
- Que release inclui esta entrega?
- Qual KPI ou outcome é herdado?

**Decisões Suportadas**

- Priorizar tasks dentro de orientação aprovada.
- Sinalizar bloqueio.
- Propor quebra de task ou story.
- Solicitar esclarecimento de critério.
- Indicar lacuna de rastreabilidade.

**KPIs Relevantes**

| KPI | Uso |
| --- | --- |
| Work Traceability Rate | Clareza de vínculo do trabalho. |
| Story Cycle Time | Fluxo de story. |
| Task Completion Reliability | Previsibilidade operacional. |
| Blocker Aging | Risco de bloqueios. |
| Rework Count | Retrabalho. |
| Quality Signal | Qualidade associada à entrega. |

## 3. Enterprise Zoom Model

A EDIP deve permitir zoom contínuo entre níveis de decisão. Cada nível deve preservar filtros, permissões, contexto, origem dos dados e possibilidade de investigação.

### Estratégico

**Propósito:** explicar direção corporativa, prioridades, OKRs, outcomes e KPIs.

**Entidades:** Estratégia Corporativa, Tema Estratégico, Objetivo Estratégico, OKR, Outcome, KPI.

**Usuários principais:** Diretores, Conselho, Superintendentes, PMO, Especialistas.

**Perguntas respondidas:**

- Quais objetivos estão em risco?
- Quais OKRs têm baixa probabilidade de cumprimento?
- Quais KPIs estratégicos estão fora do target?
- Quais temas possuem execução insuficiente?

**Drill-down:** Objetivo -> OKR -> KPI -> Portfólio -> Investimento -> Iniciativa.

**Drill-up:** KPI -> Outcome -> OKR -> Objetivo -> Tema -> Estratégia.

### Executivo

**Propósito:** apoiar decisões de investimento, prioridade, risco e valor.

**Entidades:** Portfólio agregado, investimento, funding, value case, benefício, risco executivo, decisão.

**Usuários principais:** Diretores, Superintendentes, PMO, Financeiro, Riscos.

**Perguntas respondidas:**

- Onde o investimento está em risco?
- Que decisões bloqueiam valor?
- Que benefício foi realizado?
- Que portfólio exige intervenção?

**Drill-down:** Portfólio -> Iniciativa -> Risco -> Dependência -> Épico.

**Drill-up:** Iniciativa -> Investimento -> Portfólio -> Tema -> Objetivo.

### Portfólio

**Propósito:** gerir carteira, capacidade, oportunidades, dependências e funding.

**Entidades:** Portfólio, tema, oportunidade, investimento, iniciativa, capacidade, dependência, decisão.

**Usuários principais:** Superintendentes, PMO, Gerentes, Product Owners.

**Perguntas respondidas:**

- O portfólio está balanceado?
- Que capacidade está comprometida?
- Quais oportunidades devem avançar?
- Quais dependências ameaçam iniciativas críticas?

**Drill-down:** Portfólio -> Tema -> Investimento -> Iniciativa -> Épico.

**Drill-up:** Iniciativa -> Portfólio -> Objetivo -> Estratégia.

### Tático

**Propósito:** gerir iniciativas, épicos, riscos, dependências e entregas relevantes.

**Entidades:** Iniciativa, épico, feature, risco, dependência, milestone, decisão.

**Usuários principais:** Gerentes, Coordenadores, Product Owners, PMO, Líderes Técnicos.

**Perguntas respondidas:**

- Qual iniciativa precisa de ação?
- Que épico ameaça o prazo?
- Qual risco não está mitigado?
- Que decisão precisa ser tomada?

**Drill-down:** Iniciativa -> Épico -> Feature -> Story.

**Drill-up:** Feature -> Épico -> Iniciativa -> KPI -> OKR.

### Operacional

**Propósito:** acompanhar fluxo, trabalho, bloqueios, owners e execução diária.

**Entidades:** Feature, story, task, release, bloqueio, owner, time, serviço.

**Usuários principais:** Coordenadores, Scrum Masters, Líderes Técnicos, Desenvolvedores.

**Perguntas respondidas:**

- O que está bloqueado?
- Que item envelheceu?
- Que task afeta uma feature crítica?
- Qual entrega compõe a release?

**Drill-down:** Feature -> Story -> Task -> Bloqueio.

**Drill-up:** Task -> Story -> Feature -> Épico -> Iniciativa -> Objetivo.

### Analítico

**Propósito:** explicar tendências, forecasts, scores, observabilidade, lineage e value realization.

**Entidades:** Métrica, série histórica, score, forecast, alerta, evidência, benefício, sinal de observabilidade.

**Usuários principais:** Todos, com profundidade variando por permissão.

**Perguntas respondidas:**

- O score piorou por quê?
- O forecast mudou por qual driver?
- A métrica é confiável?
- O benefício foi comprovado?

**Drill-down:** Score -> Componentes -> Entidades causadoras -> Evidências.

**Drill-up:** Métrica -> KPI -> Outcome -> OKR -> Objetivo.

## 4. Dashboard Catalog

### Executive Overview

**Objetivo:** dar visão consolidada de estratégia, risco, valor, decisões e exceções.

**Usuários:** Diretores, Conselho, Superintendentes, PMO.

**KPIs:** Strategic Health Score, OKR Achievement Forecast, Portfolio Value Realization, Investment At Risk, KPI Target Deviation, Critical Decision Aging.

**Visualizações:** heatmap de objetivos, ranking de portfólios críticos, linha de valor planejado versus realizado, lista de decisões pendentes, alertas críticos.

**Filtros:** período, diretoria, tema estratégico, objetivo, portfólio, severidade, owner.

**Drill-down:** Objetivo -> OKR -> KPI -> Portfólio -> Iniciativa -> Épico.

**Drill-up:** KPI ou iniciativa -> objetivo estratégico -> tema -> estratégia.

### Strategic Alignment Dashboard

**Objetivo:** medir aderência entre estratégia, OKRs, KPIs, portfólios e trabalho.

**Usuários:** Diretores, Superintendentes, PMO, Arquitetos Corporativos.

**KPIs:** Strategic Alignment Coverage, Traceability Compliance, Unlinked Work Count, Objective Funding Coverage, KPI Ownership Coverage.

**Visualizações:** matriz estratégia-portfólio, grafo de rastreabilidade, lista de lacunas, distribuição de capacidade por tema.

**Filtros:** objetivo, OKR, tema, portfólio, unidade, produto, owner, tipo de lacuna.

**Drill-down:** Tema -> Objetivo -> OKR -> KPI -> Iniciativas vinculadas.

**Drill-up:** Work item -> iniciativa -> portfólio -> objetivo.

### Portfolio Command Center

**Objetivo:** gerir portfólios por valor, risco, capacidade, funding e dependências.

**Usuários:** Superintendentes, PMO, Gerentes, Financeiro.

**KPIs:** Portfolio Health Score, Capacity Allocation Fit, Funding Variance, Dependency Aging, Initiative Risk Exposure, Forecast Confidence.

**Visualizações:** kanban de iniciativas, mapa de capacidade, ranking de riscos, curva de funding, heatmap de dependências, cenário de priorização.

**Filtros:** portfólio, tema, status, ciclo, funding, risco, capacidade, dependência, owner.

**Drill-down:** Portfólio -> Investimento -> Iniciativa -> Épico -> Feature.

**Drill-up:** Iniciativa -> investimento -> portfólio -> tema estratégico.

### Product Value Dashboard

**Objetivo:** conectar produto, roadmap, backlog, outcomes, KPIs e valor.

**Usuários:** Product Owners, Gerentes, Superintendentes, Diretores.

**KPIs:** Product Outcome Progress, Feature Value Score, Adoption Trend, KPI Impact Forecast, Time to Outcome, Backlog Strategic Alignment.

**Visualizações:** roadmap por outcome, matriz valor-esforço-risco, funil de oportunidades, tendência de adoção, features por KPI impactado.

**Filtros:** produto, outcome, KPI, roadmap, release, feature, owner, status.

**Drill-down:** Produto -> Outcome -> KPI -> Roadmap -> Feature -> Story.

**Drill-up:** Feature -> épico -> iniciativa -> portfólio -> objetivo.

### Initiative Workspace

**Objetivo:** oferecer visão 360 graus da iniciativa.

**Usuários:** Gerentes, Coordenadores, PMO, Product Owners, Líderes Técnicos.

**KPIs:** Initiative Health Score, Milestone Adherence, Epic Completion Rate, Risk Burn-down, Dependency Resolution Time, KPI Contribution Confidence.

**Visualizações:** timeline, mapa de riscos, árvore de escopo, forecast de prazo, rastreabilidade, decisões e evidências.

**Filtros:** iniciativa, owner, status, risco, dependência, épico, feature, período.

**Drill-down:** Iniciativa -> Épico -> Feature -> Story -> Task.

**Drill-up:** Iniciativa -> investimento -> portfólio -> KPI -> OKR.

### Delivery Flow Dashboard

**Objetivo:** tornar fluxo, filas, esperas, gargalos, bloqueios, aging, desperdícios e previsibilidade visíveis.

**Usuários:** Coordenadores, Scrum Masters, Gerentes, Líderes Técnicos.

**KPIs:** Lead Time, Cycle Time, Aging WIP, Queue Time, Bottleneck Count, Flow Health Score, Blocker Resolution Time, Flow Efficiency, Commitment Reliability.

**Visualizações:** cumulative flow, aging chart, blocker board, throughput trend, WIP por estado, filas por flow stage, bottleneck map, delivery heat map, squad heat map, outliers.

**Filtros:** time, squad, sprint, release, feature, status, flow stage, queue, owner, bloqueio, tipo de item.

**Drill-down:** Métrica de fluxo -> flow stage -> queue -> bottleneck -> itens causadores -> story -> task.

**Drill-up:** Task -> story -> feature -> épico -> iniciativa.

### Flow Intelligence Dashboard

**Objetivo:** oferecer uma visão corporativa de fluxo para identificar gargalos, filas, esperas e desperdícios entre estratégia, portfólio, delivery e squads.

**Usuários:** Diretores, Superintendentes, PMO, Gerentes, Scrum Masters, Coordenadores.

**KPIs:** Flow Health Score, Queue Time, Bottleneck Severity, Flow Efficiency, Aging WIP, Throughput, Work Item Staleness.

**Visualizações:** enterprise heat map, portfolio heat map, delivery heat map, squad heat map, stage flow matrix, queue aging distribution, bottleneck trend.

**Filtros:** nível organizacional, portfólio, iniciativa, squad, flow stage, tipo de item, severidade, período, owner.

**Drill-down:** Enterprise Heat Map -> Portfolio Heat Map -> Delivery Heat Map -> Squad Heat Map -> Queue -> Work Items.

**Drill-up:** Task ou story -> queue -> flow stage -> squad -> iniciativa -> portfólio -> objetivo estratégico.

### Technical Leadership Dashboard

**Objetivo:** conectar saúde técnica, releases, débitos, riscos e arquitetura.

**Usuários:** Líderes Técnicos, Arquitetos Corporativos, Especialistas, Gerentes.

**KPIs:** Technical Delivery Health, Technical Debt Exposure, Release Readiness, Defect Leakage, Rework Rate, Integration Risk Score.

**Visualizações:** mapa de serviços, lista de débitos por severidade, release readiness, riscos técnicos, dependências técnicas, exceções arquiteturais.

**Filtros:** serviço, produto, feature, release, risco, severidade, domínio, owner.

**Drill-down:** Serviço -> release -> feature -> story -> defeito, débito ou incidente.

**Drill-up:** Débito -> feature -> iniciativa -> KPI ou risco.

### Governance and Evidence Dashboard

**Objetivo:** gerenciar decisões, aprovações, evidências, controles e compliance.

**Usuários:** Especialistas, PMO, Auditoria, Riscos, Compliance, Arquitetos.

**KPIs:** Evidence Coverage, Control Adherence Rate, Approval Cycle Time, Compliance Issue Count, Lineage Completeness, Metric Ownership Coverage.

**Visualizações:** fila de aprovações, cobertura de evidências, matriz de controles, trilha de decisão, riscos de compliance.

**Filtros:** controle, política, entidade, owner, status, severidade, período, aprovador.

**Drill-down:** Controle -> evidência -> entidade -> decisão -> owner.

**Drill-up:** Evidência -> decisão -> iniciativa -> portfólio -> objetivo.

### Value Realization Dashboard

**Objetivo:** medir valor planejado, forecast, realizado, validado e rejeitado.

**Usuários:** Diretores, Superintendentes, Financeiro, Product Owners, PMO.

**KPIs:** Planned Value, Forecast Value, Realized Benefit, Validated Benefit, Benefit Variance, ROI, Time to Value.

**Visualizações:** waterfall de valor, curva planejado-forecast-realizado, benefícios por portfólio, valor por KPI, lista de benefícios sem evidência.

**Filtros:** portfólio, iniciativa, value case, KPI, período, owner, status de validação, fonte.

**Drill-down:** Benefício -> value case -> KPI -> iniciativa -> evidência.

**Drill-up:** Benefício -> outcome -> OKR -> objetivo estratégico.

### Observability and Data Quality Dashboard

**Objetivo:** monitorar frescor, completude, latência, falhas, divergências e confiabilidade dos dados.

**Usuários:** Dados, Engenharia, PMO, Especialistas, Operações.

**KPIs:** Data Freshness, Integration Success Rate, Processing Lag, Calculation Error Rate, Source Divergence, Data Confidence Score.

**Visualizações:** status de integrações, lag por fonte, qualidade por domínio, erros de cálculo, divergência fonte-projeção.

**Filtros:** fonte, domínio, entidade, período, severidade, status, owner.

**Drill-down:** Indicador de qualidade -> fonte -> carga -> entidade afetada -> dashboard impactado.

**Drill-up:** Falha de dado -> KPI afetado -> decisão ou dashboard impactado.

## 5. Navigation Model

### Menus

Menu principal:

```text
Home
Estratégia
Portfólios
Produtos
Iniciativas
Delivery
Value Realization
Métricas e KPIs
Governança
Observabilidade
Flow Intelligence
Alertas
Busca
```

### Fluxos

**Fluxo executivo:** Home -> Executive Overview -> Objetivo em risco -> KPI desviado -> Iniciativa causadora -> Decisão.

**Fluxo de portfólio:** Portfólios -> Portfolio Command Center -> Iniciativas em risco -> Dependências -> Ações.

**Fluxo de produto:** Produtos -> Product Value Dashboard -> Outcome -> Feature -> Story -> Release.

**Fluxo operacional:** Delivery -> Delivery Flow Dashboard -> Bloqueio -> Task -> Owner -> Escalonamento.

**Fluxo de flow intelligence:** Flow Intelligence -> Enterprise Heat Map -> Portfolio Heat Map -> Delivery Heat Map -> Squad Heat Map -> Queue -> Work Items.

**Fluxo de governança:** Governança -> Evidência pendente -> Entidade -> Decisão -> Aprovação.

**Fluxo de valor:** Value Realization -> Benefício abaixo do forecast -> KPI -> Iniciativa -> Evidência.

### Navegação Contextual

Toda página de entidade deve exibir:

- Cadeia de rastreabilidade.
- Owner principal.
- Status.
- Health score.
- Alertas ativos.
- Próximas decisões.
- Evidências associadas.
- Última atualização e origem dos dados.
- Ações permitidas pela persona.

### Busca Global

A busca global deve localizar objetivos, OKRs, KPIs, portfólios, iniciativas, oportunidades, épicos, features, stories, tasks, owners, decisões, evidências, benefícios, riscos e controles.

Resultados devem ser agrupados por domínio, relevância, criticidade e permissão.

Cada resultado deve indicar contexto, owner, status, health score e caminho de rastreabilidade.

## 6. Health Scores

Health scores são sinais explicáveis de saúde. Eles priorizam atenção, mas não substituem análise.

### Tipos

| Score | Entidade |
| --- | --- |
| Strategic Health Score | Estratégia, tema, objetivo, OKR. |
| Portfolio Health Score | Portfólio e investimento. |
| Initiative Health Score | Iniciativa. |
| Product Health Score | Produto, outcome e roadmap. |
| Delivery Health Score | Épico, feature, time e fluxo. |
| Flow Health Score | Flow stage, queue, squad, iniciativa, portfólio ou enterprise flow. |
| Technical Health Score | Serviço, release, integração e débito. |
| Data Confidence Score | Métrica, KPI, fonte e dashboard. |
| Value Realization Score | Value case, benefício e KPI de valor. |

### Componentes

| Componente | Interpretação |
| --- | --- |
| Alinhamento Estratégico | Grau de vínculo com objetivo, OKR, outcome e KPI. |
| Progresso | Avanço contra plano ou compromisso. |
| Previsibilidade | Estabilidade de prazo, escopo e forecast. |
| Valor | Relação entre esforço, investimento e benefício. |
| Risco | Severidade, probabilidade, tendência e mitigação. |
| Dependências | Quantidade, criticidade e aging. |
| Capacidade | Disponibilidade e sobrecarga. |
| Governança | Decisões, aprovações, controles e evidências. |
| Observabilidade | Frescor, completude, falhas e confiabilidade. |
| Fluxo | Tempo em fila, WIP, espera, throughput, aging e gargalos. |
| Qualidade Técnica | Defeitos, retrabalho, dívida e readiness. |

### Fórmulas Conceituais

```text
Strategic Health =
  alinhamento + progresso OKR + tendência KPI + value realization - risco - lacunas

Portfolio Health =
  alinhamento + valor esperado + capacidade adequada + forecast confidence - risco - dependências vencidas

Initiative Health =
  progresso + previsibilidade + rastreabilidade + KPI contribution - riscos - bloqueios

Delivery Health =
  fluxo + commitment reliability + throughput - aging WIP - bloqueios

Flow Health =
  throughput + flow efficiency + predictability - queue time - bottleneck severity - aging WIP - stale work

Value Realization Score =
  benefício validado + evidência + confiança - desvio forecast - benefício rejeitado

Data Confidence =
  completude + frescor + lineage + sucesso de integração - divergências - erros de cálculo
```

Cada fórmula concreta deve declarar pesos, faixas, thresholds, limitações e dados ausentes.

## 6.1 Flow Intelligence

Flow Intelligence é a capacidade da EDIP de observar explicitamente fluxo, filas, esperas, gargalos e desperdícios através dos níveis corporativo, portfólio, delivery e squad.

Flow Intelligence não altera a cadeia principal de domínio. Ela projeta sinais de fluxo sobre entidades existentes como portfólio, iniciativa, épico, feature, story, task, squad e owner.

### Flow Stages

Flow Stages representam os estados conceituais pelos quais trabalho passa do compromisso até a entrega e validação.

| Flow Stage | Definição | Sinais Observáveis |
| --- | --- | --- |
| Intake | Trabalho capturado, ainda em triagem. | ideias, oportunidades, itens sem owner, itens sem qualificação. |
| Prioritization | Trabalho avaliado para decisão de prioridade. | decision gates, critérios pendentes, conflitos de prioridade. |
| Commitment | Trabalho assumido por portfólio, iniciativa ou squad. | capacidade comprometida, funding, owner, prazo. |
| Discovery | Trabalho em refinamento de hipótese, escopo ou solução. | dependências de negócio, falta de evidência, ambiguidade de requisito. |
| Ready | Trabalho pronto para execução. | fila de pronto, aging em ready, capacidade indisponível. |
| In Progress | Trabalho em execução ativa. | WIP, cycle time, bloqueios, troca de contexto. |
| Waiting | Trabalho parado aguardando decisão, dependência, aprovação ou ambiente. | queue time, aging, owner externo. |
| Validation | Trabalho aguardando aceite, evidência, controle ou validação de valor. | tempo de validação, evidência pendente, approval aging. |
| Released | Trabalho entregue ou disponibilizado. | release, readiness, incidentes pós-release. |
| Value Check | Trabalho aguardando comprovação de outcome ou benefício. | time to value, benefício sem evidência, KPI sem movimento. |

### Queue

Queue é o conjunto de itens aguardando capacidade, decisão, dependência, aprovação, validação ou próximo estágio de fluxo.

Toda queue relevante deve expor:

- flow stage.
- entidade associada.
- owner.
- tempo em fila.
- idade máxima.
- quantidade de itens.
- severidade.
- próxima ação esperada.

### Bottleneck

Bottleneck é uma restrição persistente ou recorrente que reduz throughput, aumenta espera ou degrada previsibilidade.

Um bottleneck pode ser causado por:

- excesso de WIP.
- dependência externa.
- ausência de decisão.
- approval aging.
- capacidade insuficiente.
- fila de validação.
- ambiente indisponível.
- owner ausente.
- escopo ambíguo.
- controle ou evidência pendente.

### Heat Maps

| Heat Map | Objetivo | Unidade de Análise |
| --- | --- | --- |
| Enterprise Heat Map | Mostrar gargalos e filas entre áreas, temas e objetivos. | objetivo, unidade, portfólio, domínio. |
| Portfolio Heat Map | Mostrar gargalos por portfólio, funding, capacidade e dependências. | portfólio, investimento, iniciativa. |
| Delivery Heat Map | Mostrar gargalos por iniciativa, épico, feature e release. | iniciativa, épico, feature, release. |
| Squad Heat Map | Mostrar gargalos por squad, flow stage, WIP e bloqueios. | squad, story, task, owner. |

Heat maps devem permitir drill-down até work items causadores e drill-up até objetivo, portfólio ou iniciativa afetada.

## 7. Forecasting

Forecasting deve antecipar desvios antes que eles se tornem falhas de execução ou de valor.

### Forecast de Prazo

**Objetivo:** estimar conclusão de iniciativas, épicos, features ou releases.

**Entradas:** lead time, cycle time, throughput, aging, WIP, dependências, bloqueios, capacidade, histórico de escopo.

**Saídas:** data provável, intervalo de confiança, risco de atraso, drivers e ações recomendadas.

**Drill-down:** previsão -> drivers -> itens causadores -> owners.

### Forecast de KR

**Objetivo:** estimar probabilidade de cumprir key results no ciclo.

**Entradas:** progresso atual, tendência histórica, iniciativas associadas, KPIs contribuintes, riscos, capacidade, value realization.

**Saídas:** probabilidade de cumprimento, KR em risco, variação esperada e fatores explicativos.

**Drill-down:** KR -> KPI -> iniciativas -> features ou benefícios.

### Forecast de KPI

**Objetivo:** projetar comportamento de KPI contra baseline e target.

**Entradas:** série histórica, sazonalidade, releases, iniciativas, incidentes, fonte, qualidade de dados.

**Saídas:** valor projetado, desvio esperado, confiança, tendência e causas prováveis.

**Drill-down:** KPI -> tendência -> eventos ou iniciativas associadas.

### Forecast de Valor

**Objetivo:** comparar valor planejado, forecast, realizado, validado e rejeitado.

**Entradas:** value case, baseline, target, investimento, benefício esperado, métricas financeiras, métricas operacionais, evidências.

**Saídas:** valor provável, ROI estimado, time to value, desvio, risco de não realização e ações recomendadas.

**Drill-down:** valor -> benefício -> evidência -> iniciativa -> KPI.

### Forecast de Capacidade

**Objetivo:** prever sobrecarga ou ociosidade de times, produtos, áreas ou portfólios.

**Entradas:** alocação atual, demanda planejada, WIP, roadmap, dependências, skills, indisponibilidades, histórico de throughput.

**Saídas:** capacidade disponível, gargalos, risco de overload, cenário de priorização e trade-offs.

**Drill-down:** capacidade -> time -> iniciativas -> work items.

## 8. Alertas

Alertas devem ser acionáveis, explicáveis e priorizados. Todo alerta deve possuir severidade, owner, entidade afetada, causa provável, impacto, ação sugerida, prazo e link para drill-down.

### Alertas Estratégicos

| Alerta | Critério |
| --- | --- |
| Objetivo Sem Execução | Objetivo ativo sem portfólio, investimento ou iniciativa vinculada. |
| OKR Em Risco | Forecast do KR abaixo do threshold definido. |
| KPI Crítico Fora do Target | KPI estratégico fora da faixa por período relevante. |
| Baixa Cobertura de Rastreabilidade | Percentual de iniciativas vinculadas abaixo do limite. |
| Valor Não Realizado | Benefício validado abaixo do forecast ou sem evidência. |

### Alertas de Portfólio

| Alerta | Critério |
| --- | --- |
| Capacidade Sobrecarregada | Alocação acima do limite por período. |
| Funding Divergente | Diferença material entre aprovado, consumido e forecast. |
| Dependência Vencida | Dependência crítica sem resolução até prazo acordado. |
| Iniciativa Sem KPI | Iniciativa estratégica sem KPI impactado. |
| Portfólio Crítico | Health score abaixo de threshold. |

### Alertas Operacionais

| Alerta | Critério |
| --- | --- |
| Aging WIP Alto | Story, task ou feature acima do limite de aging. |
| Bloqueio Sem Owner | Bloqueio sem responsável definido. |
| Feature Sem Épico | Violação de rastreabilidade. |
| Story Sem Feature | Item operacional sem contexto adequado. |
| Release Sem Readiness | Release próxima sem critérios técnicos ou evidências suficientes. |
| Fonte Atrasada | Dados operacionais ou analíticos fora da janela de atualização. |

## 9. Search and Intelligence

### Busca Corporativa

A busca deve cobrir entidades estratégicas, executivas, táticas, operacionais, analíticas e de governança.

Critérios de relevância:

- Correspondência textual.
- Proximidade com escopo do usuário.
- Criticidade.
- Status.
- Recentidade.
- Relação com alertas, decisões ou riscos.
- Caminho de rastreabilidade.

Resultados devem mostrar por que foram retornados.

### Perguntas em Linguagem Natural

A EDIP deve permitir perguntas como:

- Quais objetivos estão em risco neste trimestre?
- Que iniciativas impactam o KPI de inadimplência?
- Onde temos funding aprovado sem benefício comprovado?
- Quais features críticas estão bloqueadas?
- Que portfólio tem maior vazamento de valor?
- Quais decisões estão vencidas para minha área?

Respostas devem incluir dados, filtros aplicados, período, confiança e links para investigação.

### Explicabilidade

Toda resposta inteligente deve indicar:

- Fontes usadas.
- Premissas.
- Filtros.
- Nível de confiança.
- Entidades relacionadas.
- Cálculo ou regra aplicada.
- Lacunas de dados.
- Próxima ação recomendada.

A plataforma deve distinguir recomendação, inferência, fato observado e dado ausente.

## 10. Experience Principles

### Como Reduzir Reuniões

A EDIP deve reduzir reuniões ao tornar status, riscos, dependências, decisões e evidências disponíveis continuamente.

Comitês devem focar decisões, não coleta de status.

Reuniões recorrentes devem ser substituídas por dashboards acionáveis sempre que o objetivo for apenas atualização.

Toda pauta deve ser derivável de alertas, decisões pendentes, desvios, riscos e forecasts.

### Como Eliminar Relatórios Manuais

A EDIP deve substituir consolidações manuais por dados integrados, governados e rastreáveis.

Todo relatório recorrente deve ser convertido em dashboard, visão filtrada ou pergunta reutilizável.

Métricas usadas em apresentações devem ter origem, owner, fórmula e timestamp.

Exportações devem ser consequência de governança ou comunicação externa, não mecanismo primário de gestão.

### Como Tornar Problemas Visíveis

Problemas devem aparecer no fluxo natural de uso, sem depender de busca manual.

Lacunas de rastreabilidade, KPIs sem owner, evidências ausentes, dependências vencidas, benefits não validados, forecasts degradados e dados atrasados devem ser destacados por severidade.

O usuário deve sempre saber:

- O que aconteceu.
- Por que importa.
- Quem é responsável.
- Qual entidade foi afetada.
- Qual decisão ou ação é esperada.
- Qual evidência sustenta o alerta.
- Como investigar a causa.

### Como Sustentar Confiança

A EDIP deve deixar claro quando um dado é real, estimado, atrasado, inconsistente ou ausente.

Usuários devem conseguir diferenciar fato, forecast, score, alerta, recomendação e inferência.

Confiança é parte da experiência, não detalhe técnico.

### Como Orientar Ação

Toda tela deve responder pelo menos uma destas perguntas:

- O que precisa de atenção?
- Qual decisão precisa ser tomada?
- Qual valor está em risco?
- Qual trabalho está bloqueado?
- Qual métrica mudou?
- Qual evidência falta?
- Qual é a próxima melhor ação?
