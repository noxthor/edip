# Domain Model - Enterprise Delivery Intelligence Platform (EDIP)

## Objetivo

Este documento modela formalmente o domínio da EDIP utilizando princípios de Domain Driven Design. O foco é a linguagem de negócio, os limites de contexto, os agregados, as entidades, os value objects, as regras, os eventos e as relações que sustentam rastreabilidade, governança, forecasting, health scores e value realization.

Este documento não define banco de dados, APIs, endpoints, telas, componentes de interface ou arquitetura física.

## 1. Bounded Contexts

### Strategy Context

Responsável por estratégia corporativa, temas estratégicos, objetivos estratégicos, OKRs e outcomes estratégicos.

Linguagem principal:

- Estratégia Corporativa
- Tema Estratégico
- Objetivo Estratégico
- OKR
- Key Result
- Outcome

Responsabilidade de domínio:

- Definir direção estratégica.
- Explicitar prioridades corporativas.
- Manter objetivos e OKRs rastreáveis.
- Determinar quais outcomes devem ser perseguidos.

Não é responsável por:

- Detalhamento operacional de backlog.
- Cálculo financeiro de benefício realizado.
- Gestão de funding.

### Portfolio Context

Responsável por portfólios, temas de investimento, funding, investimentos, ideias, oportunidades, capacidade, priorização e decisões de portfólio.

Linguagem principal:

- Portfólio
- Investimento
- Funding
- Ideia
- Oportunidade
- Capacidade
- Decisão de Portfólio
- Dependência Estratégica

Responsabilidade de domínio:

- Organizar execução estratégica em carteiras.
- Priorizar oportunidades e iniciativas.
- Controlar relação entre investimento, capacidade, risco e valor esperado.
- Registrar decisões de priorização, pausa, cancelamento e continuidade.

Não é responsável por:

- Quebra operacional de features, stories e tasks.
- Validação final de benefício realizado.

### Product Context

Responsável por produtos, outcomes de produto, roadmaps, oportunidades de produto, hipóteses, itens de roadmap e composição de produto por ofertas.

Linguagem principal:

- Produto
- Roadmap
- RoadmapItem
- Outcome de Produto
- Hipótese
- Adoção
- Offer consumida
- Composição de Produto

Responsabilidade de domínio:

- Conectar produto a outcomes e KPIs.
- Priorizar oportunidades e roadmap items por valor.
- Manter roadmap rastreável.
- Explicar como produto contribui para estratégia.
- Representar produto como empacotamento, experiência, jornada, canal, solução ou proposição de valor formada por ofertas.

Não é responsável por:

- Gestão financeira de funding.
- Execução detalhada de tasks técnicas.
- Definir capabilities corporativas, services, offers ou application services.
- Substituir o Architecture Capability Context.

Regras semânticas:

- Product não é Capability.
- Product não é Service.
- Product não é Offer.
- Product é uma composição flexível de N Offers.
- Product pode possuir ProductCapability como conceito interno de produto, mas ProductCapability não é a Capability do Architecture Capability Context.

### Architecture Capability Context

Responsável por modelar o elevador de arquitetura corporativo que conecta domínios de negócio, subdomínios, camadas, capabilities, serviços, offers, application services, produtos, iniciativas, métricas e valor.

Linguagem principal:

- Architecture Domain
- Architecture SubDomain
- Business Layer
- Capability
- Business Service
- Technology Service
- Offer
- Application Service
- Product Offer Association
- Architecture Assessment
- Architecture Debt
- Architecture Exception
- Modernization Plan

Responsabilidade de domínio:

- Manter a taxonomia corporativa de arquitetura: Domain -> SubDomain -> BusinessLayer -> Capability -> BusinessService / TechnologyService -> Offer -> ApplicationService.
- Explicitar quais capabilities sustentam objetivos estratégicos, produtos, iniciativas, KPIs e value cases.
- Representar services e offers que compõem produtos sem confundir produto com capability ou service.
- Registrar assessments, dívidas, exceções, aposentadorias e planos de modernização arquitetural.
- Permitir análise de impacto entre strategy, architecture, product, delivery, engineering, metrics, governance e value realization.

Não é responsável por:

- Definir backlog operacional, stories, tasks ou fluxo de delivery.
- Ser catálogo técnico de infraestrutura ou CMDB física.
- Substituir Product Context, Delivery Context ou Engineering Context.
- Calcular métricas, health scores ou forecasts.
- Aprovar funding ou decisões de portfólio.

### Delivery Context

Responsável por iniciativas, épicos, features, stories, tasks, fluxo, bloqueios, dependências de entrega e releases de negócio.

Linguagem principal:

- Iniciativa
- Épico
- Feature
- Story
- Task
- Flow Stage
- Queue
- Bottleneck
- Bloqueio
- Release
- Fluxo

Responsabilidade de domínio:

- Representar execução tática e operacional.
- Preservar rastreabilidade do trabalho.
- Medir fluxo e previsibilidade.
- Tornar filas, esperas, gargalos, bloqueios e dependências visíveis.

Não é responsável por:

- Definir estratégia corporativa.
- Validar value realization.

### Engineering Context

Responsável por serviços técnicos, integrações, débitos técnicos, riscos técnicos, prontidão de release, qualidade técnica e decisões técnicas.

Linguagem principal:

- Serviço
- Integração
- Débito Técnico
- Risco Técnico
- Release Readiness
- Defeito
- Incidente Técnico

Responsabilidade de domínio:

- Conectar saúde técnica a delivery e valor.
- Representar riscos técnicos e débitos.
- Sustentar decisões de arquitetura e release readiness.

Não é responsável por:

- Priorização executiva de portfólio.
- Definição de OKRs.

### Metrics and Intelligence Context

Responsável por KPIs, métricas, health scores, forecasts, flow intelligence, tendências, alertas inteligentes, measurement targets e explicabilidade.

Linguagem principal:

- KPI
- Métrica
- Measurement Target
- Health Score
- Flow Health Score
- Forecast
- Driver
- Tendência
- Confiança

Responsabilidade de domínio:

- Governar métricas como produtos de dados.
- Permitir que KPIs meçam outcomes, objetivos, key results, produtos, iniciativas ou value cases sem se tornarem elo estrutural da cadeia de rastreabilidade.
- Produzir scores e forecasts explicáveis.
- Produzir projeções de flow intelligence para queues, bottlenecks e heat maps.
- Identificar desvios, tendências e alertas.
- Manter fórmulas conceituais e lineage lógico.

Não é responsável por:

- Ser fonte operacional de todas as entidades medidas.
- Tomar decisões de negócio sem owner humano.

### Value Realization Context

Responsável por value cases, hipóteses de valor, baseline, target, benefício esperado, forecast de valor, benefício realizado, validação e atribuição de benefício.

Linguagem principal:

- Value Case
- Hipótese de Valor
- Baseline
- Target
- Benefício Esperado
- Benefício Forecast
- Benefício Realizado
- Benefício Validado

Responsabilidade de domínio:

- Modelar valor planejado, previsto, realizado e validado.
- Conectar benefício a KPI, outcome, iniciativa e evidência.
- Diferenciar benefício esperado, forecast, realizado, validado e rejeitado.

Não é responsável por:

- Executar contabilidade financeira oficial.
- Substituir sistemas financeiros de origem.

### Governance and Audit Context

Responsável por decisões, decision gates, aprovações, evidências, controles, exceções, trilhas de auditoria, segregação de funções e compliance.

Linguagem principal:

- Decisão
- Decision Gate
- Aprovação
- Evidência
- Controle
- Exceção
- Auditoria
- Política

Responsabilidade de domínio:

- Garantir que decisões críticas sejam rastreáveis e auditáveis.
- Definir gates transversais que condicionam avanço de oportunidades, investimentos, iniciativas, releases, métricas ou benefícios.
- Controlar evidências e aprovações.
- Preservar segregação de funções.
- Representar controles bancários.

Não é responsável por:

- Definir conteúdo estratégico.
- Calcular métricas de negócio.

### Organization and Ownership Context

Responsável por owners, papéis, unidades organizacionais, times, responsabilidades e escopos de atuação.

Linguagem principal:

- Owner
- Persona
- Papel
- Time
- Unidade Organizacional
- Responsabilidade

Responsabilidade de domínio:

- Determinar ownership de entidades, métricas, decisões e ações.
- Apoiar permissões conceituais e segregação de funções.
- Representar responsabilidade corporativa.

Não é responsável por:

- Autenticação técnica.
- Estrutura física de identidade.

### Observability and Data Quality Context

Responsável por sinais de observabilidade corporativa, frescor, completude, latência, divergência entre fonte e projeção, falhas de ingestão e qualidade de cálculo.

Linguagem principal:

- Sinal de Observabilidade
- Data Freshness
- Data Confidence
- Processing Lag
- Source Divergence
- Calculation Error

Responsabilidade de domínio:

- Explicar saúde dos dados e cálculos.
- Indicar impacto de falhas de fonte em métricas, dashboards e decisões.
- Diferenciar ausência de dado, atraso, inconsistência e resultado real.

Não é responsável por:

- Monitoramento técnico de infraestrutura como fim em si mesmo.
- Substituir observabilidade operacional de sistemas externos.

## 2. Context Map

### Relações Entre Contextos

| Origem | Destino | Relação DDD | Descrição |
| --- | --- | --- | --- |
| Strategy | Portfolio | Customer/Supplier | Portfolio consome objetivos, temas e OKRs para organizar funding e iniciativas. |
| Strategy | Metrics and Intelligence | Customer/Supplier | Metrics mede progresso de objetivos, OKRs e outcomes. |
| Strategy | Architecture Capability | Customer/Supplier | Strategy define objetivos que capabilities devem sustentar. |
| Portfolio | Product | Partnership | Produto e portfólio alinham roadmap, oportunidades, investimentos e outcomes. |
| Portfolio | Delivery | Customer/Supplier | Delivery executa iniciativas priorizadas e financiadas pelo portfólio. |
| Product | Delivery | Partnership | Product define valor e escopo; Delivery representa execução. |
| Architecture Capability | Product | Partnership | Product consome Offers; Offers derivam de Services e Capabilities. |
| Architecture Capability | Delivery | Partnership | Delivery executa iniciativas que criam, alteram, modernizam ou aposentam capabilities, services, offers e application services. |
| Architecture Capability | Engineering | Partnership | Engineering implementa e opera ApplicationServices, integrações, riscos técnicos e dívidas. |
| Architecture Capability | Metrics and Intelligence | Customer/Supplier | Métricas e scores medem health, cobertura, modernização, dívida, adoção e rastreabilidade arquitetural. |
| Architecture Capability | Governance and Audit | Partnership | Assessments, exceções, debts, standards e decisões arquiteturais são governados e auditáveis. |
| Delivery | Engineering | Partnership | Delivery depende da viabilidade técnica e Engineering expõe riscos e readiness. |
| Delivery | Value Realization | Customer/Supplier | Value Realization mede se entregas produziram benefício. |
| Metrics and Intelligence | Todos | Conformist/Published Language | Contextos usam definições governadas de KPI, score e forecast. |
| Governance and Audit | Todos | Shared Kernel conceitual | Decisão, evidência, controle e auditoria atravessam contextos. |
| Organization and Ownership | Todos | Shared Kernel conceitual | Owner, papel e responsabilidade são conceitos transversais. |
| Observability and Data Quality | Todos | Supporting Context | Explica confiança dos dados consumidos pelos demais contextos. |

### Diagrama Mermaid - Context Map

```mermaid
flowchart LR
  STR[Strategy Context]
  PORT[Portfolio Context]
  PROD[Product Context]
  ARCH[Architecture Capability Context]
  DEL[Delivery Context]
  ENG[Engineering Context]
  MET[Metrics and Intelligence Context]
  VAL[Value Realization Context]
  GOV[Governance and Audit Context]
  ORG[Organization and Ownership Context]
  OBS[Observability and Data Quality Context]

  STR --> PORT
  STR --> MET
  STR --> ARCH
  PORT <--> PROD
  PORT --> DEL
  PROD <--> DEL
  ARCH <--> PROD
  ARCH <--> DEL
  ARCH <--> ENG
  ARCH --> MET
  ARCH <--> GOV
  DEL <--> ENG
  DEL --> VAL
  MET --> STR
  MET --> PORT
  MET --> PROD
  MET --> DEL
  MET --> VAL
  GOV -.-> STR
  GOV -.-> PORT
  GOV -.-> PROD
  GOV -.-> ARCH
  GOV -.-> DEL
  GOV -.-> ENG
  GOV -.-> VAL
  ORG -.-> STR
  ORG -.-> PORT
  ORG -.-> PROD
  ORG -.-> DEL
  ORG -.-> MET
  OBS -.-> MET
  OBS -.-> VAL
```

## 3. Entidades

### Strategy Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| CorporateStrategy | Direção estratégica válida para um horizonte. | strategyId |
| StrategicTheme | Agrupador de prioridades corporativas. | themeId |
| StrategicObjective | Resultado desejado e mensurável. | objectiveId |
| OKR | Estrutura de objetivo e resultados-chave. | okrId |
| KeyResult | Resultado-chave mensurável dentro de um OKR. | keyResultId |
| StrategicOutcome | Mudança observável esperada. | outcomeId |

### Portfolio Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| Portfolio | Carteira de investimentos, iniciativas e capacidade. | portfolioId |
| Investment | Alocação de funding, capacidade ou esforço relevante. | investmentId |
| FundingCycle | Ciclo de planejamento e decisão de funding. | fundingCycleId |
| Idea | Possibilidade inicial ainda não qualificada. | ideaId |
| Opportunity | Hipótese qualificada de valor ou risco. | opportunityId |
| PortfolioDecision | Decisão sobre priorização, funding, pausa ou cancelamento. | decisionId |
| CapacityAllocation | Alocação de capacidade por período e escopo. | allocationId |

### Product Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| Product | Empacotamento, experiência, jornada, canal, solução ou proposição de valor formada por uma composição flexível de offers. Product não é Capability, Service ou Offer. | productId |
| ProductCapability | Capacidade interna de produto ou plataforma, usada para organizar roadmap e outcomes de produto; não representa Capability do Architecture Capability Context. | productCapabilityId |
| Roadmap | Plano evolutivo de produto. | roadmapId |
| ProductOutcome | Outcome sob responsabilidade de produto. | productOutcomeId |
| ProductHypothesis | Hipótese de produto ou oportunidade. | hypothesisId |
| RoadmapItem | Item de roadmap que referencia capability, outcome, hipótese ou intenção de entrega. | roadmapItemId |

### Architecture Capability Context

| Entidade | Descrição | Identidade | Ownership | Propósito |
| --- | --- | --- | --- | --- |
| ArchitectureDomain | Domínio arquitetural corporativo que agrupa subdomínios e capabilities relacionadas. | architectureDomainId | Arquiteto Corporativo / Domain Owner | Organizar análise por domínio e permitir heat maps, ownership e rastreabilidade arquitetural. |
| ArchitectureSubDomain | Subdivisão de um ArchitectureDomain com escopo de negócio ou arquitetura mais específico. | architectureSubDomainId | Domain Owner / SubDomain Owner | Estruturar capabilities por subdomínio e reduzir ambiguidade de responsabilidade. |
| BusinessLayer | Camada de negócio dentro de um subdomínio. | businessLayerId | Business Architect / Capability Architect | Agrupar capabilities por camada de negócio e facilitar análise de cobertura. |
| Capability | Capacidade corporativa com owner, propósito, criticidade e rastreabilidade. | capabilityId | Capability Owner / Arquiteto Corporativo | Explicar o que a organização precisa ser capaz de fazer para sustentar estratégia, produto, delivery e valor. |
| BusinessService | Serviço de negócio exposto por uma capability. | businessServiceId | Business Service Owner | Representar serviço de negócio consumível por offers e produtos. |
| TechnologyService | Serviço tecnológico exposto por uma capability. | technologyServiceId | Technology Service Owner / Líder Técnico | Representar sustentação tecnológica, racionalização e modernização de offers. |
| Offer | Oferta consumível por produtos, derivada de BusinessService ou TechnologyService. | offerId | Offer Owner | Conectar services a produtos sem confundir produto com capability ou service. |
| ApplicationService | Serviço de aplicação que implementa ou suporta uma offer. | applicationServiceId | Application Service Owner / Líder Técnico | Representar implementação aplicacional de uma offer e seus riscos. |
| ProductOfferAssociation | Associação governada entre Product e Offer. | productOfferAssociationId | Product Owner / Offer Owner | Registrar composição de produto, vigência, motivo e impacto. |
| ArchitectureAssessment | Avaliação arquitetural de capability, service, offer, application service ou produto. | architectureAssessmentId | Arquiteto Corporativo | Registrar aderência, risco, dívida, recomendação, evidência e decisão. |
| ArchitectureDebt | Dívida arquitetural que afeta capability, service, offer ou application service. | architectureDebtId | Arquiteto Corporativo / Owner da entidade afetada | Tornar explícito custo, risco, severidade e plano de remediação arquitetural. |
| ArchitectureException | Exceção arquitetural temporária com prazo, controles e risco aceito. | architectureExceptionId | Arquiteto Corporativo / Governança | Permitir desvio controlado, auditável e com plano de encerramento. |
| ModernizationPlan | Plano de modernização de capability ou service. | modernizationPlanId | Capability Owner / Service Owner / PMO | Coordenar objetivo, escopo, decisão, evidência e progresso de modernização. |

### Delivery Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| Initiative | Unidade tática de execução. | initiativeId |
| Epic | Bloco relevante de escopo dentro de iniciativa. | epicId |
| Feature | Item de entrega que implementa um RoadmapItem ou escopo técnico/operacional aprovado. | featureId |
| Story | Fatia entregável de valor ou comportamento. | storyId |
| Task | Trabalho operacional necessário à entrega. | taskId |
| FlowStage | Estágio conceitual do fluxo em que trabalho se encontra. | flowStageId |
| Queue | Conjunto de itens aguardando capacidade, decisão, dependência, aprovação ou próximo estágio. | queueId |
| Bottleneck | Restrição persistente ou recorrente que reduz throughput, aumenta espera ou degrada previsibilidade. | bottleneckId |
| Blocker | Impedimento explícito que trava fluxo. | blockerId |
| Release | Conjunto de entregas disponibilizadas. | releaseId |
| Dependency | Relação de dependência entre entidades. | dependencyId |

### Engineering Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| TechnicalService | Serviço, aplicação ou componente técnico. | serviceId |
| Integration | Relação técnica entre serviços, domínios ou fontes. | integrationId |
| TechnicalDebt | Compromisso técnico pendente que gera risco ou custo. | debtId |
| TechnicalRisk | Risco técnico com impacto em entrega, operação ou valor. | technicalRiskId |
| ReleaseReadinessAssessment | Avaliação de prontidão técnica. | assessmentId |

### Metrics and Intelligence Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| KPI | Indicador governado e rastreável. | kpiId |
| MetricDefinition | Definição formal de métrica. | metricDefinitionId |
| MeasurementTarget | Entidade de domínio medida por um KPI. | measurementTargetId |
| HealthScore | Sinal composto de saúde de entidade. | scoreId |
| FlowHealthScore | Sinal composto de saúde do fluxo para stage, queue, squad, iniciativa, portfólio ou enterprise flow. | flowHealthScoreId |
| HeatMap | Projeção de intensidade de gargalos, filas, esperas e desperdícios. | heatMapId |
| Forecast | Projeção explicável de prazo, valor, KPI, KR ou capacidade. | forecastId |
| Alert | Sinal acionável de exceção ou desvio. | alertId |

### Value Realization Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| ValueCase | Caso de valor com hipótese, baseline, target e evidência esperada. | valueCaseId |
| BenefitHypothesis | Hipótese específica de benefício. | benefitHypothesisId |
| RealizedBenefit | Benefício medido em período. | benefitId |
| BenefitValidation | Validação ou rejeição de benefício realizado. | validationId |

### Governance and Audit Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| Decision | Decisão relevante de domínio. | decisionId |
| DecisionGate | Ponto formal de avaliação que condiciona avanço de entidade ou processo. | gateId |
| Approval | Aprovação formal associada a decisão ou entidade. | approvalId |
| Evidence | Artefato verificável. | evidenceId |
| Control | Obrigação verificável derivada de política ou risco. | controlId |
| Exception | Desvio aceito temporariamente. | exceptionId |
| AuditTrailEntry | Registro auditável de ação ou decisão. | auditEntryId |

### Organization and Ownership Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| Owner | Responsável por entidade, métrica, decisão ou ação. | ownerId |
| RoleAssignment | Associação entre pessoa/time e papel. | roleAssignmentId |
| OrganizationUnit | Unidade organizacional. | orgUnitId |
| Team | Time responsável por execução ou ownership. | teamId |

### Observability and Data Quality Context

| Entidade | Descrição | Identidade |
| --- | --- | --- |
| ObservabilitySignal | Sinal que explica saúde, atraso, falha ou divergência. | signalId |
| DataQualityAssessment | Avaliação de qualidade de dado ou cálculo. | assessmentId |
| SourceSystem | Sistema de origem conceitual. | sourceSystemId |

## 4. Value Objects

| Value Object | Descrição |
| --- | --- |
| Period | Intervalo temporal com início e fim. |
| Horizon | Janela estratégica, anual, trimestral ou operacional. |
| MoneyAmount | Valor financeiro com moeda. |
| Percentage | Percentual normalizado. |
| ConfidenceLevel | Alta, média, baixa ou desconhecida. |
| HealthScoreValue | Valor de score com faixa e interpretação. |
| ForecastScenario | Otimista, provável ou pessimista. |
| MetricFormula | Expressão conceitual de cálculo. |
| BaselineTarget | Par baseline-target de medição. |
| TraceabilityPath | Sequência explícita de vínculos entre entidades. |
| OwnershipScope | Escopo de responsabilidade do owner. |
| RiskRating | Combinação de probabilidade, impacto e severidade. |
| EvidenceReference | Referência verificável a evidência. |
| DecisionRationale | Justificativa formal de decisão. |
| DataFreshness | Atualidade do dado frente à periodicidade esperada. |
| SourceLineage | Origem e transformação conceitual de um dado. |
| CapacityAmount | Capacidade expressa por unidade de planejamento. |
| TimeToValue | Tempo entre entrega e evidência de benefício. |
| QueueTime | Tempo que item permanece em fila sem avanço de estágio. |
| FlowStageType | Intake, Prioritization, Commitment, Discovery, Ready, In Progress, Waiting, Validation, Released ou Value Check. |
| BottleneckSeverity | Severidade de gargalo por impacto, duração, recorrência e escopo afetado. |
| HeatMapCell | Célula de heat map com dimensão, intensidade, entidade e período. |

## 5. Agregados

### Strategy Aggregate

Root: `CorporateStrategy`

Entidades internas:

- StrategicTheme
- StrategicObjective
- OKR
- KeyResult
- StrategicOutcome

Invariantes:

- Objetivo estratégico ativo deve pertencer a uma estratégia.
- OKR deve estar associado a objetivo estratégico.
- Key Result deve possuir forma mensurável.
- Outcome deve ter owner ou owner herdado do objetivo.

### Portfolio Aggregate

Root: `Portfolio`

Entidades internas:

- Investment
- FundingCycle
- Idea
- Opportunity
- CapacityAllocation
- PortfolioDecision

Invariantes:

- Investimento deve possuir owner e ciclo.
- Iniciativa financiada deve estar vinculada a investimento.
- Ideia qualificada deve gerar oportunidade ou descarte justificado.
- Oportunidade aprovada deve gerar iniciativa, experimento ou decisão de descarte.
- Decisão de portfólio deve possuir justificativa.

### Product Aggregate

Root: `Product`

Entidades internas:

- ProductCapability
- Roadmap
- ProductOutcome
- ProductHypothesis
- RoadmapItem
- ProductOfferAssociation

Invariantes:

- Roadmap deve pertencer a produto.
- RoadmapItem deve estar ligado a ProductCapability interna de produto, outcome ou hipótese.
- Outcome de produto deve possuir KPI associado ou justificativa.
- Product não é Capability, Service ou Offer.
- Product é uma composição flexível de N Offers.
- ProductOfferAssociation deve possuir owner, motivo e período de vigência.
- ProductCapability é conceito interno do Product Context e não substitui Capability do Architecture Capability Context.

### ArchitectureDomain Aggregate

Root: `ArchitectureDomain`

Entidades internas:

- ArchitectureSubDomain
- BusinessLayer
- Capability

Invariantes:

- ArchitectureDomain deve possuir owner.
- ArchitectureSubDomain deve pertencer a um ArchitectureDomain.
- BusinessLayer deve pertencer a um ArchitectureSubDomain.
- Capability deve pertencer a uma BusinessLayer.
- Capability deve possuir owner, propósito e criticidade.
- Toda Capability crítica deve permitir rastreabilidade até objetivos, produtos, iniciativas, métricas, value cases ou justificativa formal.

### Service Aggregate

Root: `Capability`

Entidades internas:

- BusinessService
- TechnologyService
- Offer
- ApplicationService

Invariantes:

- BusinessService deve pertencer a uma Capability.
- TechnologyService deve pertencer a uma Capability.
- Offer deve estar associada a pelo menos um BusinessService ou TechnologyService.
- Offer pode ser composta por N ApplicationServices.
- ApplicationService não é Product.
- Capability não é Product.
- Service não é Product.

### Product Composition Aggregate

Root: `Product`

Entidades internas:

- ProductOfferAssociation

Invariantes:

- Product pode associar-se a N Offers.
- Offer pode compor N Products.
- Toda associação Product-Offer deve possuir owner, motivo e período de vigência.
- ProductOfferAssociation deve preservar histórico de inclusão, remoção, vigência e substituição de offer.

### Architecture Governance Aggregate

Root: `ArchitectureAssessment`

Entidades internas:

- ArchitectureDebt
- ArchitectureException
- ModernizationPlan

Invariantes:

- ArchitectureAssessment deve declarar escopo, entidade avaliada, resultado, evidências, recomendação e decisão associada quando aplicável.
- ArchitectureDebt deve possuir owner, severidade, entidade afetada e plano de tratamento ou aceite formal de risco.
- ArchitectureException deve possuir owner, prazo, justificativa, controles compensatórios e plano de encerramento.
- Toda modernização de Capability ou Service deve possuir owner, objetivo, escopo, decisão e evidência.

### Initiative Aggregate

Root: `Initiative`

Entidades internas:

- Epic
- Dependency

Invariantes:

- Épico deve estar vinculado a iniciativa.
- Initiative deve possuir owner, status e vínculo com portfólio, investimento ou exceção formal.
- Dependência crítica deve possuir owner, severidade e prazo.

### Feature Aggregate

Root: `Feature`

Entidades internas:

- Story
- Task
- Blocker

Invariantes:

- Feature deve estar vinculada a exatamente um épico.
- Feature pode implementar um RoadmapItem ou representar escopo técnico/operacional aprovado.
- Story deve estar vinculada a Feature ou herdar vínculo por regra explícita.
- Task deve estar vinculada a Story.
- Blocker deve possuir owner, causa e impacto.

### Flow Intelligence Aggregate

Root: `Queue`

Entidades internas:

- FlowStage
- Bottleneck

Invariantes:

- Queue deve declarar flow stage, entidade associada, owner, período e critério de entrada.
- Bottleneck deve estar associado a queue, flow stage ou entidade afetada.
- Bottleneck deve possuir severidade, causa provável, duração e impacto.
- FlowStage deve ser usado como classificação conceitual de fluxo, não como substituto dos estados específicos das entidades.

### Release Aggregate

Root: `Release`

Entidades internas:

- Feature

Invariantes:

- Release deve declarar escopo de features.
- Release crítica deve possuir evidência de prontidão ou DecisionGate aplicável.

### Engineering Aggregate

Root: `TechnicalService`

Entidades internas:

- Integration
- TechnicalDebt
- TechnicalRisk
- ReleaseReadinessAssessment

Invariantes:

- Débito técnico deve ter impacto, owner e plano ou justificativa.
- Risco técnico crítico deve estar vinculado a iniciativa, serviço ou release.
- Release readiness deve declarar critérios avaliados.

### KPI Aggregate

Root: `KPI`

Entidades internas:

- MetricDefinition

Invariantes:

- KPI deve possuir owner, fórmula, fonte, baseline, target, periodicidade e confiança.
- KPI deve medir pelo menos um MeasurementTarget.
- KPI não é elo estrutural obrigatório entre estratégia, portfólio e delivery.

### Health Score Aggregate

Root: `HealthScore`

Entidades internas:

- MeasurementTarget
- FlowHealthScore

Invariantes:

- Health score deve possuir componentes explicáveis.
- Health score deve declarar entidade medida e período.
- FlowHealthScore deve decompor queue time, bottleneck severity, WIP, aging, throughput e flow efficiency.

### Heat Map Aggregate

Root: `HeatMap`

Entidades internas:

- FlowHealthScore
- Queue
- Bottleneck

Invariantes:

- HeatMap deve declarar nível de análise: enterprise, portfolio, delivery ou squad.
- HeatMap deve permitir drill-down até queues, bottlenecks e work items causadores.
- HeatMap deve permitir drill-up até objetivo, portfólio ou iniciativa impactada.

### Forecast Aggregate

Root: `Forecast`

Entidades internas:

- MeasurementTarget

Invariantes:

- Forecast deve possuir horizonte, premissas, cenário, drivers e confiança.
- Forecast usado em decisão executiva deve ser auditável.

### Alert Aggregate

Root: `Alert`

Entidades internas:

- MeasurementTarget

Invariantes:

- Alerta deve possuir owner, severidade, causa provável e ação sugerida.
- Alerta deve referenciar entidade afetada.

### Value Realization Aggregate

Root: `ValueCase`

Entidades internas:

- BenefitHypothesis
- RealizedBenefit
- BenefitValidation

Invariantes:

- Value case deve possuir hipótese, baseline, target e método de comprovação.
- Benefício realizado deve possuir período, fonte e evidência.
- Benefício validado deve possuir validador e critério de aceite.

### Governance Aggregate

Root: `Decision`

Entidades internas:

- DecisionGate
- Approval
- Evidence
- Control
- Exception
- AuditTrailEntry

Invariantes:

- Decisão crítica deve possuir evidência ou exceção formal.
- DecisionGate deve declarar critério de entrada, critério de saída, escopo e autoridade responsável.
- Aprovação deve registrar solicitante e aprovador.
- Exceção deve possuir owner, prazo e plano de encerramento.
- Controle deve declarar evidência esperada.

## 6. Relacionamentos

| Origem | Relação | Destino |
| --- | --- | --- |
| CorporateStrategy | contém | StrategicTheme |
| StrategicTheme | orienta | StrategicObjective |
| StrategicObjective | possui | OKR |
| OKR | possui | KeyResult |
| StrategicObjective | espera | StrategicOutcome |
| KPI | mede | StrategicObjective, KeyResult, StrategicOutcome, Product, Initiative ou ValueCase |
| Portfolio | alinha-se a | StrategicTheme |
| Portfolio | contribui para | StrategicObjective |
| Portfolio | organiza | Investment |
| Portfolio | prioriza | Initiative |
| Investment | financia | Initiative |
| Idea | pode evoluir para | Opportunity |
| Opportunity | pode originar | Initiative |
| Product | possui | ProductCapability interna de produto |
| Product | possui | Roadmap |
| Product | é composto por | Offer |
| Offer | compõe | Product |
| Roadmap | planeja | RoadmapItem |
| RoadmapItem | referencia | ProductCapability interna de produto |
| ArchitectureDomain | contém | ArchitectureSubDomain |
| ArchitectureSubDomain | contém | BusinessLayer |
| BusinessLayer | contém | Capability |
| Capability | expõe | BusinessService |
| Capability | expõe | TechnologyService |
| BusinessService | oferece | Offer |
| TechnologyService | oferece | Offer |
| Offer | é implementada por | ApplicationService |
| ApplicationService | implementa | Offer |
| Capability | suporta | StrategicObjective |
| Capability | suporta | Initiative |
| Capability | suporta | ValueCase |
| Capability | impacta | KPI |
| Offer | suporta | ProductOutcome |
| ArchitectureDebt | afeta | Capability, BusinessService, TechnologyService, Offer ou ApplicationService |
| ModernizationPlan | moderniza | Capability, BusinessService ou TechnologyService |
| Initiative | decompõe-se em | Epic |
| Epic | decompõe-se em | Feature |
| RoadmapItem | pode ser implementado por | Feature |
| Feature | decompõe-se em | Story |
| Story | decompõe-se em | Task |
| Feature, Story ou Task | posiciona-se em | FlowStage |
| Queue | agrupa | Feature, Story ou Task |
| Bottleneck | afeta | Queue, FlowStage, Initiative, Portfolio ou Team |
| Feature | entregue em | Release |
| Initiative | associado a | ValueCase |
| Initiative | contribui para | StrategicOutcome |
| ValueCase | mede valor de | StrategicOutcome |
| ValueCase | medido por | KPI |
| ValueCase | possui | BenefitHypothesis |
| ValueCase | comprova | RealizedBenefit |
| RealizedBenefit | validado por | BenefitValidation |
| KPI | possui | MetricDefinition |
| KPI | possui | MeasurementTarget |
| KPI | recebe | Forecast |
| Entidade de domínio | pode possuir | HealthScore |
| Queue, Bottleneck ou FlowStage | pode possuir | FlowHealthScore |
| HeatMap | agrega | Queue, Bottleneck e FlowHealthScore |
| Entidade de domínio | pode disparar | Alert |
| Entidade crítica | sustentada por | Evidence |
| Decision | pode exigir | Approval |
| DecisionGate | avalia | Entidade de domínio |
| Control | exige | Evidence |
| Owner | responsabiliza-se por | Entidade de domínio |
| ObservabilitySignal | afeta | KPI ou Dashboard conceitual |

## 7. Cardinalidades

| Relação | Cardinalidade |
| --- | --- |
| CorporateStrategy -> StrategicTheme | 1:N |
| StrategicTheme -> StrategicObjective | 1:N |
| StrategicObjective -> OKR | 1:N |
| OKR -> KeyResult | 1:N |
| StrategicObjective -> StrategicOutcome | 1:N |
| KPI -> MeasurementTarget | N:M |
| KPI -> StrategicObjective | N:M |
| KPI -> KeyResult | N:M |
| KPI -> StrategicOutcome | N:M |
| KPI -> Product | N:M |
| KPI -> Initiative | N:M |
| KPI -> ValueCase | N:M |
| StrategicOutcome -> Portfolio | N:M |
| StrategicObjective -> Portfolio | N:M |
| Portfolio -> Initiative | N:M |
| Portfolio -> Investment | 1:N |
| Investment -> Initiative | N:M |
| Idea -> Opportunity | 0..1 |
| Opportunity -> Initiative | 0:N |
| Product -> ProductCapability | 0:N |
| Product -> Roadmap | 1:N |
| Product -> Offer | N:M |
| Offer -> Product | N:M |
| ArchitectureDomain -> ArchitectureSubDomain | 1:N |
| ArchitectureSubDomain -> BusinessLayer | 1:N |
| BusinessLayer -> Capability | 1:N |
| Capability -> BusinessService | 1:N |
| Capability -> TechnologyService | 1:N |
| BusinessService -> Offer | 1:N |
| TechnologyService -> Offer | 1:N |
| Offer -> ApplicationService | 1:N |
| Capability -> StrategicObjective | N:M |
| Capability -> Initiative | N:M |
| Capability -> KPI | N:M |
| Capability -> ValueCase | N:M |
| Roadmap -> RoadmapItem | 1:N |
| RoadmapItem -> ProductCapability | N:0..1 |
| Initiative -> Epic | 1:N |
| Epic -> Feature | 1:N |
| RoadmapItem -> Feature | 0..1:N |
| Feature -> Story | 1:N |
| Story -> Task | 1:N |
| WorkItem -> FlowStage | N:1 temporal |
| Queue -> WorkItem | 1:N temporal |
| Bottleneck -> Queue | N:M |
| Bottleneck -> FlowStage | N:M |
| HeatMap -> FlowHealthScore | 1:N |
| HeatMap -> Queue | 1:N |
| HeatMap -> Bottleneck | 0:N |
| Feature -> Release | N:M |
| Initiative -> StrategicOutcome | N:M |
| Initiative -> ValueCase | N:M |
| ValueCase -> StrategicOutcome | N:M |
| ValueCase -> KPI | N:M |
| ValueCase -> BenefitHypothesis | 1:N |
| ValueCase -> RealizedBenefit | 0:N |
| RealizedBenefit -> BenefitValidation | 0..1:1 |
| KPI -> Forecast | 0:N |
| Forecast -> MeasurementTarget | N:M |
| KPI -> MetricDefinition | 1:1 |
| Entidade -> Evidence | 0:N |
| Entidade -> Owner | N:1 |
| Decision -> Approval | 0:N |
| DecisionGate -> Decision | 0:N |
| DecisionGate -> Approval | 0:N |
| Control -> Evidence | 0:N |
| Entity -> HealthScore | 0:N temporal |
| Entity -> Alert | 0:N |

## 8. Regras de Negócio

### Rastreabilidade

- Toda iniciativa estratégica deve possuir vínculo explícito com portfólio, investimento, owner, outcome esperado e KPI impactado.
- Todo épico deve estar vinculado a exatamente uma iniciativa.
- Toda Feature deve estar vinculada a exatamente um épico.
- RoadmapItem e Feature são conceitos distintos; RoadmapItem expressa intenção de produto/roadmap, Feature expressa item executável de entrega no Delivery Context.
- Story deve estar vinculada a uma Feature, salvo exceção transitória formal.
- Task deve estar vinculada a uma story.
- Rastreabilidade não pode ser inferida apenas por texto, nomenclatura ou proximidade organizacional.

### Métricas

- Todo KPI deve possuir owner, fórmula, fonte, baseline, target, periodicidade e confiança.
- KPI deve medir explicitamente um ou mais alvos: objetivo, key result, outcome, produto, iniciativa ou value case.
- KPI não deve ser modelado como etapa obrigatória entre outcome e portfólio.
- Métrica sem owner não pode ser usada como base de decisão crítica.
- KPI com fonte atrasada deve sinalizar redução de confiança.
- Forecast usado em decisão executiva deve preservar versão, premissas e drivers.

### Portfólio

- Investimento aprovado deve possuir ciclo de funding.
- Ideia qualificada deve virar oportunidade ou ser descartada com justificativa.
- Iniciativa financiada deve estar vinculada a investimento.
- Oportunidade descartada deve possuir justificativa.
- Portfólio crítico deve possuir owner e plano de ação.
- Capacidade alocada acima de limite definido deve gerar risco ou alerta.

### Value Realization

- Value case deve declarar hipótese, baseline, target, método de comprovação e owner.
- Benefício realizado deve possuir período, fonte, método de cálculo e evidência.
- Benefício só pode ser considerado validado após validação explícita.
- Benefício rejeitado deve registrar motivo e responsável pela rejeição.

### Governança Bancária

- Decisão crítica deve possuir justificativa e evidência.
- DecisionGate deve declarar critérios de entrada, critérios de saída, autoridade responsável e entidades avaliadas.
- Exceção deve possuir owner, prazo e plano de encerramento.
- Aprovação deve respeitar segregação de funções.
- Controle deve possuir evidência esperada.
- Auditoria deve conseguir reconstruir quem decidiu, quando, por quê e com qual evidência.

### Observabilidade e Qualidade de Dados

- Ausência de dado, dado atrasado, dado inconsistente e resultado real são estados semanticamente diferentes.
- Falha de fonte que impacta KPI deve afetar confiança do KPI.
- Divergência entre fonte e projeção deve gerar avaliação de qualidade.

### Flow Intelligence

- Todo work item relevante deve poder ser classificado em um FlowStage conceitual.
- Queue deve ser visível quando itens aguardam capacidade, decisão, dependência, aprovação, validação ou próximo estágio.
- Queue sem owner deve gerar alerta de fluxo.
- Bottleneck deve ser registrado quando fila, espera ou restrição persistente degrada throughput, previsibilidade ou valor.
- Flow Health Score deve decompor seus drivers: queue time, bottleneck severity, aging WIP, WIP, throughput e flow efficiency.
- Enterprise Heat Map, Portfolio Heat Map, Delivery Heat Map e Squad Heat Map são projeções analíticas de fluxo, não novos níveis de domínio.
- Heat maps devem permitir drill-down até work items causadores e drill-up até objetivo, portfólio ou iniciativa afetada.

### Architecture Capability Rules

- ArchitectureDomain deve possuir owner e escopo explícito.
- ArchitectureSubDomain deve pertencer a exatamente um ArchitectureDomain.
- BusinessLayer deve pertencer a exatamente um ArchitectureSubDomain.
- Capability deve pertencer a exatamente uma BusinessLayer.
- Capability deve possuir owner, propósito e criticidade.
- Capability crítica deve possuir rastreabilidade até StrategicObjective, Product, Initiative, KPI, ValueCase ou justificativa formal.
- Capability não é Product.
- BusinessService e TechnologyService devem pertencer a uma Capability.
- Service, quando usado neste contexto, significa BusinessService ou TechnologyService.
- Service não é Product.
- Offer deve estar associada a pelo menos um BusinessService ou TechnologyService.
- Offer pode ser implementada por N ApplicationServices.
- ApplicationService não é Product.
- Product não é Capability, Service ou Offer.
- Product representa empacotamento, experiência, jornada, canal, solução ou proposição de valor formada por offers.
- Product pode associar-se a N Offers.
- Offer pode compor N Products.
- Toda ProductOfferAssociation deve possuir owner, motivo, período de vigência, status e evidência quando crítica.
- Rastreabilidade Offer-Product deve permitir identificar quais products são afetados por aposentadoria, degradação, dívida ou exceção de uma offer.
- Rastreabilidade Capability-Strategy deve permitir identificar quais strategic objectives, KPIs, value cases e initiatives são afetados por capability crítica.
- ModernizationPlan de Capability ou Service deve possuir owner, objetivo, escopo, decisão, evidência, prazo e critério de conclusão.
- ArchitectureDebt deve declarar entidade afetada, severidade, causa, owner, impacto e plano de remediação ou aceite formal de risco.
- ArchitectureAssessment deve registrar escopo, entidade avaliada, resultado, evidências, recomendações e decisão associada quando aplicável.
- Aposentadoria de Capability, Service ou Offer deve registrar motivo, substituto esperado, produtos afetados, iniciativas afetadas, decisão e plano de transição.
- CapabilityRetired ou OfferRetired deve gerar análise de impacto em Product, Initiative, KPI, ValueCase e ProductOutcome.
- ProductOfferAssociation removida deve preservar histórico e alternativa de substituição quando aplicável.

## 9. Máquinas de Estado

### Idea

```mermaid
stateDiagram-v2
  [*] --> Captured
  Captured --> Qualified
  Captured --> Discarded
  Qualified --> ConvertedToOpportunity
  Qualified --> Discarded
  ConvertedToOpportunity --> [*]
  Discarded --> [*]
```

### Opportunity

```mermaid
stateDiagram-v2
  [*] --> Captured
  Captured --> Qualified
  Qualified --> Approved
  Qualified --> Discarded
  Approved --> ConvertedToInitiative
  Discarded --> [*]
  ConvertedToInitiative --> [*]
```

### Investment

```mermaid
stateDiagram-v2
  [*] --> Proposed
  Proposed --> UnderReview
  UnderReview --> Approved
  UnderReview --> Rejected
  Approved --> Active
  Active --> Paused
  Paused --> Active
  Active --> Completed
  Active --> Cancelled
  Rejected --> [*]
  Completed --> [*]
  Cancelled --> [*]
```

### Initiative

```mermaid
stateDiagram-v2
  [*] --> Draft
  Draft --> ReadyForFunding
  ReadyForFunding --> Funded
  Funded --> InDelivery
  InDelivery --> Blocked
  Blocked --> InDelivery
  InDelivery --> Released
  Released --> Closed
  InDelivery --> Cancelled
  Closed --> [*]
  Cancelled --> [*]
```

### Feature

```mermaid
stateDiagram-v2
  [*] --> Proposed
  Proposed --> Ready
  Ready --> InProgress
  InProgress --> Blocked
  Blocked --> InProgress
  InProgress --> Done
  Done --> Released
  Released --> Validated
  Validated --> [*]
```

### KPI

```mermaid
stateDiagram-v2
  [*] --> Draft
  Draft --> Defined
  Defined --> Active
  Active --> Stale
  Stale --> Active
  Active --> Retired
  Retired --> [*]
```

### Value Case

```mermaid
stateDiagram-v2
  [*] --> Draft
  Draft --> BaselineDefined
  BaselineDefined --> Approved
  Approved --> Measuring
  Measuring --> BenefitRecorded
  BenefitRecorded --> Validated
  BenefitRecorded --> Rejected
  Rejected --> Measuring
  Validated --> Realized
  Realized --> [*]
```

### Alert

```mermaid
stateDiagram-v2
  [*] --> Detected
  Detected --> Acknowledged
  Acknowledged --> InTreatment
  InTreatment --> Mitigated
  Mitigated --> Resolved
  Resolved --> Reopened
  Reopened --> InTreatment
  Resolved --> [*]
```

### Decision Gate

```mermaid
stateDiagram-v2
  [*] --> Defined
  Defined --> Open
  Open --> UnderAssessment
  UnderAssessment --> Approved
  UnderAssessment --> Rejected
  UnderAssessment --> Waived
  Approved --> Closed
  Rejected --> Closed
  Waived --> Closed
  Closed --> [*]
```

## 10. Eventos de Domínio

### Strategy Events

| Evento | Fato |
| --- | --- |
| CorporateStrategyDefined | Estratégia corporativa foi definida. |
| StrategicThemeCreated | Tema estratégico foi criado. |
| StrategicObjectiveActivated | Objetivo estratégico foi ativado. |
| OKRDefined | OKR foi definido. |
| KeyResultUpdated | Resultado-chave foi atualizado. |
| StrategicOutcomeLinked | Outcome foi vinculado a objetivo. |

### Portfolio Events

| Evento | Fato |
| --- | --- |
| IdeaCaptured | Ideia foi capturada. |
| IdeaQualified | Ideia foi qualificada. |
| IdeaDiscarded | Ideia foi descartada. |
| OpportunityQualified | Oportunidade foi qualificada. |
| InvestmentProposed | Investimento foi proposto. |
| InvestmentApproved | Investimento foi aprovado. |
| FundingAllocated | Funding foi alocado. |
| PortfolioDecisionRecorded | Decisão de portfólio foi registrada. |
| CapacityAllocated | Capacidade foi alocada. |
| InitiativePrioritized | Iniciativa foi priorizada. |

### Product Events

| Evento | Fato |
| --- | --- |
| ProductOutcomeDefined | Outcome de produto foi definido. |
| RoadmapPublished | Roadmap foi publicado. |
| RoadmapItemPrioritized | RoadmapItem foi priorizado. |
| ProductHypothesisValidated | Hipótese de produto foi validada. |

### Delivery Events

| Evento | Fato |
| --- | --- |
| InitiativeCreated | Iniciativa foi criada. |
| InitiativeFunded | Iniciativa recebeu funding. |
| EpicCreated | Épico foi criado. |
| FeatureLinkedToEpic | Feature foi vinculada ao épico. |
| RoadmapItemMappedToFeature | RoadmapItem foi mapeado para Feature. |
| WorkItemBlocked | Item de trabalho foi bloqueado. |
| DependencyRaised | Dependência foi registrada. |
| ReleaseCompleted | Release foi concluída. |
| FlowStageChanged | Item mudou de flow stage. |
| QueueThresholdBreached | Queue ultrapassou limite definido. |
| BottleneckDetected | Gargalo foi detectado. |
| BottleneckResolved | Gargalo foi resolvido. |

### Engineering Events

| Evento | Fato |
| --- | --- |
| TechnicalDebtRegistered | Débito técnico foi registrado. |
| TechnicalRiskRaised | Risco técnico foi levantado. |
| ReleaseReadinessAssessed | Prontidão de release foi avaliada. |
| IntegrationRiskDetected | Risco de integração foi detectado. |

### Architecture Capability Events

| Evento | Fato |
| --- | --- |
| DomainCreated | ArchitectureDomain foi criado. |
| SubDomainCreated | ArchitectureSubDomain foi criado. |
| CapabilityCreated | Capability foi criada. |
| CapabilityUpdated | Capability foi atualizada. |
| CapabilityRetired | Capability foi aposentada. |
| BusinessServiceCreated | BusinessService foi criado. |
| TechnologyServiceCreated | TechnologyService foi criado. |
| OfferCreated | Offer foi criada. |
| OfferRetired | Offer foi aposentada. |
| ProductOfferAssociated | Product foi associado a Offer. |
| ProductOfferRemoved | Associação Product-Offer foi removida. |
| ArchitectureAssessmentRequested | Assessment arquitetural foi solicitado. |
| ArchitectureAssessmentCompleted | Assessment arquitetural foi concluído. |
| ArchitectureDebtRegistered | Dívida arquitetural foi registrada. |
| ArchitectureDebtResolved | Dívida arquitetural foi resolvida. |
| ArchitectureExceptionGranted | Exceção arquitetural foi concedida. |
| ArchitectureExceptionExpired | Exceção arquitetural expirou. |
| CapabilityModernizationStarted | Modernização de capability foi iniciada. |
| CapabilityModernizationCompleted | Modernização de capability foi concluída. |
| ServiceModernizationStarted | Modernização de service foi iniciada. |
| ServiceModernizationCompleted | Modernização de service foi concluída. |

### Metrics and Intelligence Events

| Evento | Fato |
| --- | --- |
| KPIDefined | KPI foi definido. |
| KPIBecameStale | KPI ficou desatualizado. |
| HealthScoreChanged | Health score mudou de forma relevante. |
| FlowHealthScoreChanged | Flow health score mudou de forma relevante. |
| HeatMapGenerated | Heat map foi gerado. |
| ForecastGenerated | Forecast foi gerado. |
| ForecastConfidenceChanged | Confiança do forecast mudou. |
| AlertDetected | Alerta foi detectado. |

### Value Realization Events

| Evento | Fato |
| --- | --- |
| ValueCaseCreated | Caso de valor foi criado. |
| BenefitHypothesisDefined | Hipótese de benefício foi definida. |
| BenefitRecorded | Benefício foi registrado. |
| BenefitValidated | Benefício foi validado. |
| BenefitRejected | Benefício foi rejeitado. |

### Governance and Audit Events

| Evento | Fato |
| --- | --- |
| DecisionRecorded | Decisão foi registrada. |
| DecisionGateOpened | DecisionGate foi aberto. |
| DecisionGatePassed | DecisionGate foi aprovado. |
| DecisionGateRejected | DecisionGate foi rejeitado. |
| ApprovalGranted | Aprovação foi concedida. |
| ApprovalRejected | Aprovação foi rejeitada. |
| EvidenceAttached | Evidência foi anexada. |
| ControlAssessmentCompleted | Avaliação de controle foi concluída. |
| ExceptionAccepted | Exceção foi aceita. |
| AuditTrailRecorded | Registro auditável foi produzido. |

### Observability and Data Quality Events

| Evento | Fato |
| --- | --- |
| DataFreshnessBreached | Frescor esperado do dado foi violado. |
| SourceDivergenceDetected | Divergência de fonte foi detectada. |
| CalculationErrorDetected | Erro de cálculo foi detectado. |
| DataConfidenceChanged | Confiança do dado mudou. |

## 11. Ownership

| Objeto de Domínio | Owner Obrigatório | Observação |
| --- | --- | --- |
| CorporateStrategy | Diretor ou comitê executivo | Responsável por direção. |
| StrategicObjective | Diretor ou superintendente | Responsável por resultado. |
| OKR | Owner executivo ou tático | Responsável por ciclo. |
| KPI | Owner de métrica | Responsável por definição e confiança. |
| Portfolio | Superintendente ou PMO responsável | Responsável por carteira. |
| Investment | Sponsor ou owner de portfólio | Responsável por funding e retorno. |
| Idea | Originador ou owner de triagem | Responsável por qualificação inicial. |
| Opportunity | Product Owner, PMO ou owner de portfólio | Responsável por hipótese e decisão de conversão. |
| Initiative | Gerente ou accountable tático | Responsável por execução e status. |
| Epic | Product Owner ou gerente | Responsável por escopo. |
| RoadmapItem | Product Owner | Responsável por valor e aceite de produto. |
| Feature | Product Owner, gerente ou líder técnico | Responsável por entrega e rastreabilidade operacional. |
| Story | Time ou responsável operacional | Responsável por entrega. |
| Queue | Owner do flow stage ou entidade associada | Responsável por ação sobre espera. |
| Bottleneck | Owner da restrição ou área causadora | Responsável por mitigação. |
| FlowHealthScore | Owner do domínio medido | Responsável por interpretação e ação. |
| HeatMap | PMO, Scrum Master ou owner executivo conforme nível | Responsável por leitura e ação. |
| ArchitectureDomain | Arquiteto Corporativo ou Domain Owner | Responsável por escopo, taxonomia e ownership do domínio. |
| ArchitectureSubDomain | Domain Owner ou SubDomain Owner | Responsável por coerência do subdomínio. |
| BusinessLayer | Business Architect ou Capability Architect | Responsável por classificação e organização das capabilities. |
| Capability | Capability Owner ou Arquiteto Corporativo | Responsável por propósito, criticidade, rastreabilidade e evolução. |
| BusinessService | Business Service Owner | Responsável por serviço de negócio e relação com offers. |
| TechnologyService | Technology Service Owner ou Líder Técnico | Responsável por sustentação tecnológica e modernização. |
| Offer | Offer Owner | Responsável por oferta, vigência, adoção e impacto em produtos. |
| ApplicationService | Application Service Owner ou Líder Técnico | Responsável por implementação, operação e riscos da aplicação. |
| ProductOfferAssociation | Product Owner e Offer Owner | Responsáveis por motivo, vigência, impacto e remoção da associação. |
| ArchitectureAssessment | Arquiteto Corporativo | Responsável por avaliação, recomendação, evidências e decisão. |
| ArchitectureDebt | Arquiteto Corporativo ou owner da entidade afetada | Responsável por plano de remediação ou aceite formal. |
| ArchitectureException | Arquiteto Corporativo, risco ou governança | Responsável por prazo, controles e encerramento da exceção. |
| ModernizationPlan | Capability Owner, Service Owner ou PMO | Responsável por objetivo, escopo, execução, evidência e conclusão. |
| TechnicalDebt | Líder Técnico | Responsável por plano de tratamento. |
| ValueCase | Sponsor de valor | Responsável por hipótese e comprovação. |
| RealizedBenefit | Owner de valor e validador | Responsável por evidência e validação. |
| Control | Especialista, risco ou compliance | Responsável por aderência. |
| Evidence | Owner da entidade evidenciada | Responsável por validade. |
| DecisionGate | Autoridade definida pelo gate | Responsável por avaliação e decisão. |
| Alert | Owner da entidade afetada | Responsável por ação. |

## 12. Auditabilidade

### Requisitos de Auditoria de Domínio

- Decisões críticas devem preservar decisão, justificativa, owner, data, evidência e escopo.
- Alterações em KPI devem preservar versão da fórmula, fonte, owner e motivo.
- Alterações em forecast devem preservar premissas, data, drivers e nível de confiança.
- Alterações em health score devem preservar componentes e dados de entrada.
- Benefícios realizados devem preservar período, método de cálculo, evidência e validação.
- Exceções devem preservar prazo, owner, razão e plano de encerramento.
- Mudanças de rastreabilidade devem preservar relação anterior e nova relação.
- DecisionGates devem preservar critérios, avaliadores, resultado, evidência e decisão associada.
- ProductOfferAssociation deve preservar owner, motivo, vigência, status, evidência e histórico de remoção.
- CapabilityRetired e OfferRetired devem preservar decisão, impacto, substituto, produtos afetados e plano de transição.
- ArchitectureAssessment deve preservar escopo, entidade avaliada, resultado, evidências, recomendações e decisão associada.
- ArchitectureDebt deve preservar severidade, causa, impacto, owner, plano de remediação e aceite de risco quando aplicável.
- ArchitectureException deve preservar aprovador, prazo, justificativa, controles compensatórios, risco aceito e encerramento.
- ModernizationPlan deve preservar objetivo, escopo, owner, decisão, evidências, progresso e critério de conclusão.

### Entidades Auditáveis

| Entidade | Auditoria Obrigatória |
| --- | --- |
| StrategicObjective | Sim |
| OKR | Sim |
| KPI | Sim |
| Portfolio | Sim |
| Investment | Sim |
| Initiative | Sim |
| RoadmapItem | Sim quando crítica ou vinculada a KPI |
| Feature | Sim quando crítica ou vinculada a KPI |
| Queue | Sim quando crítica ou vencida |
| Bottleneck | Sim |
| FlowHealthScore | Sim quando crítico |
| HeatMap | Sim quando usado em comitê |
| ProductOfferAssociation | Sim |
| ArchitectureDomain | Sim quando crítico ou usado em decisão executiva |
| ArchitectureSubDomain | Sim quando crítico ou usado em decisão executiva |
| BusinessLayer | Sim quando crítico ou usado em decisão executiva |
| Capability | Sim |
| BusinessService | Sim quando crítico |
| TechnologyService | Sim quando crítico |
| Offer | Sim |
| ApplicationService | Sim quando crítico |
| CapabilityRetired | Sim |
| OfferRetired | Sim |
| ArchitectureAssessment | Sim |
| ArchitectureDebt | Sim |
| ArchitectureException | Sim |
| ModernizationPlan | Sim |
| ValueCase | Sim |
| RealizedBenefit | Sim |
| Decision | Sim |
| Approval | Sim |
| Evidence | Sim |
| Control | Sim |
| Exception | Sim |
| DecisionGate | Sim |
| Forecast | Sim quando usado em decisão |
| HealthScore | Sim quando crítico |

## 13. Diagramas Mermaid

### Cadeia de Rastreabilidade

```mermaid
flowchart TD
  Strategy[Corporate Strategy] --> Theme[Strategic Theme]
  Theme --> Objective[Strategic Objective]
  Objective --> OKR[OKR]
  OKR --> Outcome[Outcome]
  Objective --> Capability[Capability]
  Capability --> BusinessService[Business Service]
  Capability --> TechnologyService[Technology Service]
  BusinessService --> Offer[Offer]
  TechnologyService --> Offer
  Offer --> Product[Product]
  Offer --> ApplicationService[Application Service]
  Objective -. measured by .-> KPI[KPI]
  OKR -. measured by .-> KPI
  Outcome -. measured by .-> KPI
  Outcome --> Portfolio[Portfolio]
  Product --> Outcome
  Portfolio --> Investment[Investment]
  Investment --> Initiative[Initiative]
  Capability -. supports .-> Initiative
  Initiative -. measured by .-> KPI
  Initiative --> Epic[Epic]
  Epic --> DFeature[Feature]
  DFeature -. flow stage .-> FlowStage[Flow Stage]
  FlowStage -. waits in .-> Queue[Queue]
  Queue -. constrained by .-> Bottleneck[Bottleneck]
  DFeature --> Story[Story]
  Story --> Task[Task]
  Task --> Delivery[Delivery]
  Delivery --> Benefit[Realized Benefit]
  Benefit -. measured by .-> KPI
```

### Agregados Principais

```mermaid
classDiagram
  class CorporateStrategy
  class StrategicTheme
  class StrategicObjective
  class OKR
  class KeyResult
  class StrategicOutcome
  class Portfolio
  class Investment
  class Idea
  class Opportunity
  class Product
  class ProductOfferAssociation
  class ArchitectureDomain
  class ArchitectureSubDomain
  class BusinessLayer
  class Capability
  class BusinessService
  class TechnologyService
  class Offer
  class ApplicationService
  class ArchitectureAssessment
  class ArchitectureDebt
  class ArchitectureException
  class ModernizationPlan
  class Initiative
  class Epic
  class RoadmapItem
  class Feature
  class Story
  class Task
  class FlowStage
  class Queue
  class Bottleneck
  class FlowHealthScore
  class HeatMap
  class KPI
  class MeasurementTarget
  class ValueCase
  class RealizedBenefit
  class Decision
  class DecisionGate
  class Evidence

  CorporateStrategy "1" --> "*" StrategicTheme
  StrategicTheme "1" --> "*" StrategicObjective
  StrategicObjective "1" --> "*" OKR
  OKR "1" --> "*" KeyResult
  StrategicObjective "1" --> "*" StrategicOutcome
  StrategicOutcome "*" --> "*" Portfolio
  Portfolio "1" --> "*" Investment
  Portfolio "*" --> "*" Initiative
  Investment "*" --> "*" Initiative
  Idea "0..1" --> "0..1" Opportunity
  Opportunity "0..1" --> "0..*" Initiative
  ArchitectureDomain "1" --> "*" ArchitectureSubDomain
  ArchitectureSubDomain "1" --> "*" BusinessLayer
  BusinessLayer "1" --> "*" Capability
  Capability "1" --> "*" BusinessService
  Capability "1" --> "*" TechnologyService
  BusinessService "1" --> "*" Offer
  TechnologyService "1" --> "*" Offer
  Offer "1" --> "*" ApplicationService
  Product "*" --> "*" Offer
  Product "1" --> "*" ProductOfferAssociation
  ProductOfferAssociation "*" --> "1" Offer
  Capability "*" --> "*" StrategicObjective
  Capability "*" --> "*" Initiative
  Capability "*" --> "*" KPI
  Capability "*" --> "*" ValueCase
  ArchitectureAssessment "1" --> "*" ArchitectureDebt
  ArchitectureAssessment "1" --> "*" ArchitectureException
  ArchitectureAssessment "1" --> "*" ModernizationPlan
  ArchitectureDebt "*" --> "*" Capability
  ModernizationPlan "*" --> "*" Capability
  ModernizationPlan "*" --> "*" BusinessService
  ModernizationPlan "*" --> "*" TechnologyService
  Initiative "*" --> "*" StrategicOutcome
  Initiative "1" --> "*" Epic
  Epic "1" --> "*" Feature
  RoadmapItem "0..1" --> "*" Feature
  Feature "1" --> "*" Story
  Story "1" --> "*" Task
  Feature "*" --> "1" FlowStage
  Queue "1" --> "*" Feature
  Bottleneck "*" --> "*" Queue
  HeatMap "1" --> "*" FlowHealthScore
  KPI "*" --> "*" MeasurementTarget
  Initiative "*" --> "*" ValueCase
  ValueCase "*" --> "*" StrategicOutcome
  ValueCase "*" --> "*" KPI
  ValueCase "1" --> "*" RealizedBenefit
  DecisionGate "1" --> "*" Decision
  Decision "1" --> "*" Evidence
```

### Architecture Elevator

```mermaid
flowchart LR
  Domain[Architecture Domain] --> SubDomain[Architecture SubDomain]
  SubDomain --> BusinessLayer[Business Layer]
  BusinessLayer --> Capability[Capability]
  Capability --> BusinessService[Business Service]
  Capability --> TechnologyService[Technology Service]
  BusinessService --> Offer[Offer]
  TechnologyService --> Offer
  Offer --> ApplicationService[Application Service]
  Offer --> Product[Product]
  ApplicationService -. supports via Offer .-> Product
  Product --> Initiative[Initiative]
  Initiative --> Feature[Feature]
  Feature --> Outcome[Outcome]
  Outcome --> KPI[KPI]
  Outcome --> ValueCase[Value Case]
  Capability -. supports .-> Objective[Strategic Objective]
  Capability -. impacts .-> KPI
  Capability -. supports .-> ValueCase
```

### Value Realization

```mermaid
flowchart LR
  Initiative[Initiative] --> ValueCase[Value Case]
  ValueCase --> Hypothesis[Benefit Hypothesis]
  Hypothesis --> Baseline[Baseline]
  Hypothesis --> Target[Target]
  ValueCase --> Forecast[Value Forecast]
  ValueCase --> Benefit[Realized Benefit]
  Benefit --> Evidence[Evidence]
  Benefit --> Validation[Benefit Validation]
  Validation --> Validated[Validated Benefit]
  Validation --> Rejected[Rejected Benefit]
```

### Governança e Auditoria

```mermaid
flowchart TD
  Entity[Domain Entity] --> Decision[Decision]
  Decision --> Approval[Approval]
  Decision --> Evidence[Evidence]
  Decision --> Audit[Audit Trail Entry]
  Control[Control] --> Evidence
  Exception[Exception] --> Decision
  Owner[Owner] --> Decision
  Owner --> Entity
```

### Flow Intelligence

```mermaid
flowchart TD
  Enterprise[Enterprise Heat Map] --> PortfolioMap[Portfolio Heat Map]
  PortfolioMap --> DeliveryMap[Delivery Heat Map]
  DeliveryMap --> SquadMap[Squad Heat Map]
  SquadMap --> Stage[Flow Stage]
  Stage --> Queue[Queue]
  Queue --> Bottleneck[Bottleneck]
  Queue --> WorkItems[Features / Stories / Tasks]
  Bottleneck --> Impact[Impacto em prazo, valor, capacidade ou risco]
  WorkItems --> Initiative[Initiative]
  Initiative --> Portfolio[Portfolio]
  Portfolio --> Objective[Strategic Objective]
```

## 14. Glossário Formal

| Termo | Definição |
| --- | --- |
| Estratégia Corporativa | Direção de longo prazo da organização. |
| Tema Estratégico | Agrupamento de prioridades estratégicas. |
| Objetivo Estratégico | Resultado desejado e mensurável. |
| OKR | Estrutura de objetivo e resultados-chave. |
| Key Result | Resultado mensurável de um OKR. |
| Outcome | Mudança observável em negócio, cliente, risco, eficiência, operação ou experiência. |
| KPI | Indicador governado usado para medir progresso, resultado ou saúde. |
| Portfólio | Carteira que organiza temas, investimentos, iniciativas, capacidade, riscos e decisões. |
| Investimento | Alocação de funding, capacidade ou esforço relevante. |
| Funding | Envelope, ciclo ou decisão de financiamento. |
| Ideia | Possibilidade inicial ainda não qualificada. |
| Oportunidade | Hipótese qualificada de valor, risco, eficiência ou crescimento. |
| Architecture Domain | Domínio arquitetural corporativo que agrupa subdomínios, business layers e capabilities relacionadas. |
| Architecture SubDomain | Subdivisão de um Architecture Domain com escopo de negócio ou arquitetura mais específico. |
| Business Layer | Camada de negócio que organiza capabilities dentro de um subdomínio. |
| Capability | Capacidade corporativa com owner, propósito, criticidade e rastreabilidade para estratégia, produto, delivery, métricas ou valor. |
| Business Service | Serviço de negócio exposto por uma capability e consumível por offers. |
| Technology Service | Serviço tecnológico exposto por uma capability e consumível por offers. |
| Offer | Oferta consumível por products, derivada de BusinessService ou TechnologyService. |
| Application Service | Serviço de aplicação que implementa ou suporta uma offer. |
| Product Offer Association | Associação governada entre Product e Offer, com owner, motivo, vigência e histórico. |
| Architecture Assessment | Avaliação arquitetural de capability, service, offer, application service ou product. |
| Architecture Debt | Dívida arquitetural que afeta capability, service, offer ou application service. |
| Architecture Exception | Exceção arquitetural temporária, auditável e controlada. |
| Modernization Plan | Plano de modernização de capability ou service com owner, escopo, decisão, evidência e critério de conclusão. |
| Iniciativa | Unidade tática de execução conectada a portfólio, investimento, outcome ou KPI. |
| Épico | Bloco relevante de escopo dentro de uma iniciativa. |
| RoadmapItem | Item de roadmap priorizado por valor, outcome, hipótese ou intenção de evolução de produto. |
| Feature | Item executável de entrega que implementa um RoadmapItem ou escopo técnico/operacional aprovado. |
| Story | Fatia entregável de valor ou comportamento. |
| Task | Trabalho operacional necessário para concluir uma story ou feature. |
| Release | Conjunto de entregas disponibilizadas. |
| Flow Intelligence | Capacidade de observar fluxo, filas, esperas, gargalos e desperdícios em múltiplos níveis corporativos. |
| Flow Stage | Estágio conceitual do fluxo em que trabalho se encontra. |
| Queue | Conjunto de itens aguardando capacidade, decisão, dependência, aprovação, validação ou próximo estágio. |
| Bottleneck | Restrição persistente ou recorrente que reduz throughput, aumenta espera ou degrada previsibilidade. |
| Flow Health Score | Score que mede saúde do fluxo por queue time, bottleneck severity, WIP, aging, throughput e flow efficiency. |
| Enterprise Heat Map | Projeção corporativa de gargalos, filas, esperas e desperdícios. |
| Portfolio Heat Map | Projeção de fluxo por portfólio, investimento, capacidade e dependências. |
| Delivery Heat Map | Projeção de fluxo por iniciativa, épico, feature e release. |
| Squad Heat Map | Projeção de fluxo por squad, story, task, owner e flow stage. |
| Owner | Responsável por entidade, métrica, decisão ou ação. |
| Evidência | Artefato verificável que sustenta status, decisão, métrica, controle ou valor. |
| Value Case | Caso de valor com hipótese, baseline, target e evidência esperada. |
| Benefício Realizado | Valor medido em período e associado a evidência. |
| Benefício Validado | Benefício aceito após validação formal. |
| Controle | Obrigação verificável derivada de política, risco, arquitetura, segurança, compliance ou auditoria. |
| DecisionGate | Ponto formal de avaliação que condiciona avanço de entidade ou processo. |
| Exceção | Desvio aceito temporariamente com owner, prazo e justificativa. |
| Health Score | Sinal composto e explicável de saúde de entidade. |
| Forecast | Projeção explicável de prazo, valor, KPI, KR ou capacidade. |
| Alert | Sinal acionável de exceção, risco ou desvio. |
| Traceability Path | Sequência explícita e auditável de vínculos entre entidades. |
| Measurement Target | Entidade de domínio medida por KPI, score ou forecast. |
| Data Confidence | Grau de confiança de dado, métrica ou cálculo. |
| Observability Signal | Sinal que explica saúde, comportamento, falha, atraso, risco ou tendência. |

## 15. Change Log

### Evolução do Architecture Capability Context

- Adicionado formalmente o Architecture Capability Context como bounded context da EDIP.
- Incorporado o Architecture Elevator: ArchitectureDomain -> ArchitectureSubDomain -> BusinessLayer -> Capability -> BusinessService / TechnologyService -> Offer -> ApplicationService.
- Adicionadas entidades de domínio para ArchitectureDomain, ArchitectureSubDomain, BusinessLayer, Capability, BusinessService, TechnologyService, Offer, ApplicationService, ProductOfferAssociation, ArchitectureAssessment, ArchitectureDebt, ArchitectureException e ModernizationPlan.
- Adicionados agregados ArchitectureDomain Aggregate, Service Aggregate, Product Composition Aggregate e Architecture Governance Aggregate.

### Correção Semântica de Product

- Corrigida a definição de Product para remover qualquer sugestão de equivalência com Capability.
- Explicitado que Product não é Capability, Product não é Service e Product não é Offer.
- Definido Product como composição flexível de N Offers.
- Mantido ProductCapability apenas como conceito interno do Product Context, sem equivalência com Capability do Architecture Capability Context.

### Rastreabilidade e Relacionamentos

- Adicionadas relações entre Strategy e Architecture Capability para objetivos suportados por capabilities.
- Adicionadas relações entre Product e Offer por ProductOfferAssociation.
- Adicionadas relações entre Capability, StrategicObjective, Initiative, KPI e ValueCase.
- Adicionadas relações de ArchitectureDebt e ModernizationPlan com Capability, Service, Offer e ApplicationService.
- Atualizadas cardinalidades do Architecture Elevator e de Product -> Offer como N:M.

### Governança, Eventos e Auditoria

- Adicionadas Architecture Capability Rules para composição Product-Offer, rastreabilidade, modernização, dívida, assessment, aposentadoria e impacto.
- Adicionada referência aos eventos de Architecture Capability já previstos no EVENT_CATALOG.
- Atualizados owners obrigatórios para entidades arquiteturais.
- Atualizada auditabilidade obrigatória para ProductOfferAssociation, CapabilityRetired, OfferRetired, ArchitectureAssessment, ArchitectureDebt, ArchitectureException e ModernizationPlan.

### Diagramas

- Atualizado Context Map para incluir Architecture Capability Context.
- Atualizada Cadeia de Rastreabilidade com capability, services, offers, application services e product composition.
- Atualizado diagrama de Agregados Principais com entidades e relações arquiteturais.
- Adicionado diagrama Architecture Elevator.
