# Arquitetura da Informação UX - Enterprise Delivery Intelligence Platform (EDIP)

## 1. Missão da Arquitetura da Informação

A arquitetura da informação da EDIP existe para reduzir incerteza organizacional.

A EDIP não deve ser organizada primariamente por páginas, gráficos ou registros operacionais. Ela deve ser organizada por perguntas corporativas que exigem evidência, contexto, rastreabilidade, explicação e decisão. A plataforma deve ajudar cada persona a entender onde a organização está, o que está acontecendo, por que está acontecendo, o que está em risco, quem deveria agir e qual deve ser a próxima ação.

As perguntas centrais são:

- Onde estamos?
- O que está acontecendo?
- Por que está acontecendo?
- O que está em risco?
- Quem deveria agir?
- O que devemos fazer agora?

### Dado, Informação, Insight e Decisão

| Nível | Definição | Exemplo na EDIP | Governança Necessária |
| --- | --- | --- | --- |
| Dado | Observação bruta ou normalizada de um sistema, fonte, evento ou entidade. | Uma feature mudou de status; uma observação de KPI foi ingerida; um alerta foi detectado. | Fonte, timestamp, owner, lineage e qualidade. |
| Informação | Dado organizado em contexto para permitir entendimento de estado, escopo e significado. | Aging de fila por owner para requisitos aguardando revisão. | Contexto, filtros, relações entre entidades e confiança. |
| Insight | Descoberta contextualizada que exige investigação, ação ou decisão. | Uma fila recorrente de revisão arquitetural está atrasando um objetivo estratégico e aumentando cost of delay. | Cadeia de evidência, fatores causais, confiança e limitações. |
| Decisão | Escolha feita por autoridade humana, papel governado ou comitê sobre ação, exceção, prioridade, funding, aceite ou rejeição. | Repriorizar um portfólio, aprovar uma solução, aceitar um risco ou pausar uma iniciativa. | Owner, autoridade, justificativa, evidência, data, impacto e trilha de auditoria. |

A arquitetura deve preservar a cadeia:

```text
Dados -> Eventos -> Métricas -> Health Scores -> Forecasts -> Heat Maps -> Insights -> Explicações -> Recomendações -> Decisões -> Planos de Ação -> Aprendizado.
```

## 2. Princípios de Arquitetura da Informação

| Princípio | Significado | Exigência de Informação UX |
| --- | --- | --- |
| Question Driven Navigation | A navegação começa pela pergunta que o usuário precisa responder. | Menus, workspaces, cockpits e prompts do Copilot devem mapear perguntas de decisão, não apenas listas de entidades. |
| Persona First | Cada persona vê a mesma verdade por uma lente decisória diferente. | Visões devem adaptar profundidade, vocabulário, filtros padrão, ações e exposição de evidência por persona e autorização. |
| Explainability First | Todo score, forecast, alerta, recomendação e narrativa deve ser explicável. | Qualquer agregação deve expor componentes, eventos, evidências, premissas, causa raiz e confiança. |
| Context Preservation | O usuário não deve perder escopo ao navegar entre níveis. | Portfólio, produto, capability, período, owner, unidade de negócio, sensibilidade e permissões devem acompanhar a navegação. |
| Progressive Disclosure | O usuário vê primeiro o que importa e depois investiga causas e evidências. | Workspaces devem conduzir de sinal para driver, entidade, evidência e ação sem expor todo detalhe de início. |
| Traceability Everywhere | Todo item relevante deve exibir relações explícitas. | Caminhos Strategy-to-Delivery, Need-to-Value e Architecture Elevator devem ser navegáveis a partir de cada entidade. |
| Drill Down Everywhere | Agregações só são aceitáveis quando suas causas podem ser inspecionadas. | Dashboard, cockpit, score, heat map, KPI, forecast e alerta devem permitir drill-down para entidades de origem. |
| Drill Up Everywhere | Trabalho operacional deve explicar por que existe. | Task, story, feature, requisito, solução, alerta ou evidência devem permitir drill-up até objetivo, outcome, portfólio, capability ou valor. |
| Evidence First | Status e decisões exigem suporte verificável. | Disponibilidade, validade, owner, classificação e restrições de acesso de evidências devem ser visíveis no contexto. |
| Action Oriented Design | Sinais devem levar a próxima ação, owner e validação esperada. | Alertas, blockers, recomendações e filas devem expor ação, papel accountable, SLA, aging e consequência da inação. |
| Decision Support First | A EDIP apoia decisões, não reporting passivo. | Todo workspace deve declarar decisões suportadas e informações, métricas, eventos, evidências e explicações necessárias. |
| Single Source of Truth | Personas podem ter visões diferentes, mas não verdades conflitantes. | Projeções e dashboards devem referenciar entidades canônicas, métricas governadas e lineage, sem virar fonte de verdade independente. |

## 3. Arquitetura de Personas

| Persona | Objetivos | Responsabilidades | Perguntas Frequentes | Decisões Tomadas | Indicadores Consumidos | Alertas Relevantes | Heat Maps Relevantes | Workspaces Utilizados |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Diretores | Governar estratégia, valor, risco e prioridades executivas. | Responder por targets estratégicos, aprovar funding material e decidir escalonamentos. | Estamos entregando a estratégia? Quais objetivos estão em risco? Qual valor será realizado? | Repriorizar objetivos, aprovar funding, pausar ou acelerar iniciativas, aceitar risco executivo. | Strategic Health Score, OKR Achievement Forecast, Investment At Risk, KPI Target Deviation, Value Realization Score, Decision Latency. | Objetivo em risco, OKR em risco, value leakage, investimento em risco, decision SLA excedido. | Portfolio, Value Realization, Alert, Capability. | Executive, Strategy, Portfolio, Value Realization, Governance, Intelligence. |
| Executivos | Traduzir estratégia em escolhas de portfólio e outcomes de negócio. | Balancear funding, capacidade, risco, valor e accountability entre áreas. | Onde investir capacidade? Qual portfólio está crítico? Qual decisão bloqueia valor? | Rebalancear funding, alterar prioridade de portfólio, escalar dependências entre áreas. | Portfolio Health Score, Capacity Allocation Fit, Funding Variance, Cost of Delay, Forecast Confidence. | Portfólio crítico, funding divergente, bottleneck severity aumentado, capability traceability crítico. | Portfolio, Delivery, Capability, Alert. | Executive, Portfolio, Architecture, Intelligence, Governance. |
| Superintendentes | Orquestrar portfólios, capacidade, dependências e outcomes. | Preparar decisões executivas e garantir integridade da execução de portfólio. | Quais iniciativas ameaçam o trimestre? Onde dependências estão envelhecendo? Qual forecast exige ação? | Rebalancear capacidade, recomendar pausa ou aceleração, escalar dependências. | Portfolio Health Score, Dependency Aging, Initiative Risk Exposure, Schedule Forecast Accuracy, Flow Health Score. | Dependência vencida, flow health degradado, decision SLA excedido, iniciativa crítica. | Portfolio, Delivery, Blocker, Alert. | Portfolio, Delivery, Flow Intelligence, Governance. |
| Gerentes | Gerir iniciativas, escopo, risco, dependências e comunicação. | Manter rastreabilidade, forecast, mitigação e decisões táticas da iniciativa. | O que está bloqueado? Quais épicos atrasam o outcome? O que deve ser escalado? | Replanejar escopo, ajustar prioridade de features, mitigar risco, solicitar decisão de portfólio. | Initiative Health Score, Delivery Health Score, Milestone Adherence, Epic Completion Rate, KPI Contribution Confidence. | Feature bloqueada, dependência vencida, readiness alert, forecast degradado. | Delivery, Blocker, Requirements, Solution. | Portfolio, Requirements, Solution Design, Delivery, Validation. |
| Coordenadores | Coordenar fluxo de execução, owners, blockers, WIP e aging. | Manter o trabalho fluindo e escalar impedimentos operacionais. | Qual fila está congestionada? Qual item está envelhecendo? Quem deveria agir? | Reordenar trabalho, atribuir owner, escalar blocker, ajustar plano de ciclo. | Queue Time, Aging WIP, Blocked Time, Flow Efficiency, Commitment Reliability, Blocker Resolution Health. | Queue threshold breached, work item stale, blocker sem owner, violação de DoR. | Delivery, Blocker, Alert. | Delivery, Flow Intelligence, Validation, Governance. |
| Business Teams | Explicar needs, pains, jornadas, processos e evidências de negócio. | Ser owner do contexto de negócio e validar outcomes de negócio. | Qual dor estamos resolvendo? Qual evidência falta? O outcome é útil? | Aceitar problema, rejeitar demanda fraca, validar outcome de negócio. | Business Discovery Health, Evidence Coverage, Validation Health, Time to Outcome. | Evidência ausente, business queue aging, validação pendente. | Business Discovery, Validation, Value Realization. | Business Discovery, Validation, Knowledge. |
| Product Teams | Conectar discovery, roadmap, outcomes, backlog e valor. | Ser owner de hipóteses, priorização, requisitos e outcomes de produto. | Qual discovery está envelhecendo? Qual feature tem maior valor? Qual hipótese falhou? | Priorizar roadmap, pivotar discovery, aprovar requisito, ajustar backlog. | Product Health Score, Discovery Quality Score, Feature Value Score, Product Outcome Progress, Hypothesis Validation Accuracy. | Discovery quality degraded, requirement quality alert, value leakage detected. | Business Discovery, Requirements, Value Realization, Offer/Product composition. | Product Discovery, Requirements, Delivery, Value Realization, Knowledge. |
| Engineering Teams | Avaliar viabilidade, executar delivery e validar qualidade técnica. | Ser owner de implementação, evidência técnica, readiness e qualidade operacional. | O que bloqueia delivery? Qual risco técnico afeta release? O que deve ser validado? | Escolher abordagem técnica, mitigar risco técnico, aprovar readiness técnico. | Technical Delivery Health, Release Readiness, Integration Risk Score, Technical Debt Exposure, Cycle Time. | Technical blocker, release readiness rejected, integration risk detected, solution review alert. | Delivery, Solution, Architecture, Blocker. | Solution Design, Architecture, Delivery, Validation. |
| Arquitetos | Governar capabilities, services, offers, padrões, dívidas e decisões de solução. | Preservar integridade do Architecture Elevator e auditabilidade de decisões arquiteturais. | Qual capability está degradada? Qual offer cria risco para produto? Qual decisão está pendente? | Aprovar solução, conceder ou rejeitar exceção, priorizar modernização. | Capability Health Score, Capability Traceability Health, Architecture Debt Score, Offer Health Score, Architecture Review Health. | Architecture debt critical, capability traceability critical, architecture exception expired. | Architecture, Capability, Solution, Portfolio. | Architecture, Solution Design, Knowledge, Governance. |
| Security Specialists | Avaliar riscos, controles e evidências de segurança. | Revisar constraints, controles e aprovações de segurança. | Qual solução tem risco de segurança não resolvido? Qual evidência falta? | Aprovar, rejeitar, exigir mitigação ou aceitar risco via autoridade definida. | Security Review Time, Control Adherence Rate, Solution Health, Evidence Coverage. | Security review pending, evidence missing, regulatory critical alert. | Solution, Governance, Alert. | Solution Design, Governance, Knowledge. |
| Data Specialists | Governar lineage, qualidade, privacidade e confiança de métricas. | Validar fontes, cálculos, data confidence e uso permitido. | A métrica é confiável? Qual fonte divergiu? Este forecast pode apoiar decisão? | Aprovar fonte, bloquear métrica frágil, exigir reconciliação. | Data Confidence Score, Lineage Completeness, Data Freshness, Source Divergence, Calculation Error Rate. | Data confidence degraded, source divergence, stale KPI, forecast accuracy degraded. | Data Quality, Metrics, Alert. | Metrics, Intelligence, Governance, Knowledge. |
| Compliance Specialists | Avaliar aderência regulatória, políticas e evidência de controles. | Governar reviews de compliance, controles, exceções e prontidão de auditoria. | Qual controle está sem evidência? Qual exceção expirou? Qual alerta permanece aberto? | Aprovar review de compliance, exigir remediação, bloquear avanço, aceitar risco formal. | Governance Health Score, Control Adherence Rate, Compliance Issue Count, Approval Aging. | Compliance review pending, exception expired, evidence missing, alert resolution failed. | Governance, Alert, Solution. | Governance, Solution Design, Knowledge. |
| Auditores | Verificar decisões, evidências, rastreabilidade e segregação de funções. | Reconstruir histórico e testar auditabilidade de fluxos críticos. | Por que esta decisão foi tomada? O valor foi validado? O encerramento do alerta é válido? | Emitir achado, contestar evidência, solicitar remediação. | Auditability Coverage, Evidence Coverage, Decision Latency, Alert Resolution Health, Traceability Health Score. | Alert resolvido sem validação, decisão sem evidência, métrica sem owner. | Governance, Alert, Value Realization. | Governance, Metrics, Value Realization, Knowledge. |
| Governance Teams | Operar gates, evidências, controles, exceções, políticas e qualidade decisória. | Garantir governance by design nos fluxos. | Qual decisão está atrasada? Qual evidência falta? Qual gate bloqueia valor? | Escalar gate, exigir evidência, reabrir resolução inválida de alerta. | Governance Health Score, Decision SLA, Approval Aging, Metric Ownership Coverage, Evidence Coverage. | Decision SLA exceeded, comitê sem evidência, alert resolution failed. | Governance, Alert, Portfolio. | Governance, Portfolio, Intelligence, Knowledge. |

## 4. Arquitetura de Perguntas

Perguntas são objetos de navegação de primeira classe. Cada pergunta deve mapear entidades, métricas, eventos, evidências e decisões suportadas.

### Perguntas de Estratégia

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Estamos entregando a estratégia? | Strategy, Theme, Objective, OKR, KPI, Portfolio, Initiative. | Strategic Health Score, OKR Achievement Forecast, Strategic Alignment Coverage. | ObjectiveCreated, OKRCreated, KeyResultProgressUpdated, KPIUpdated. | Repriorizar objetivos, ajustar target de OKR, mudar foco de investimento. |
| Quais objetivos estão em risco? | Objective, KR, KPI, ValueCase, Initiative. | KPI Target Deviation, KR Forecast Probability, Investment At Risk. | ForecastUpdated, HealthScoreCalculated, ValueAtRiskIncreased. | Escalar plano de recuperação, realocar capacidade. |
| Qual valor será realizado? | Outcome, ValueCase, Benefit, Portfolio. | Forecast Value, Realized Benefit, Validated Benefit, Value Realization Score. | BenefitObserved, BenefitValidated, BenefitRejected. | Confirmar benefício, ajustar forecast, revisar compromisso estratégico. |

### Perguntas de Portfólio

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Qual portfólio apresenta maior risco? | Portfolio, Investment, Initiative, Dependency. | Portfolio Health Score, Initiative Risk Exposure, Investment At Risk. | PortfolioReprioritized, DependencyRaised, ValueAtRiskIncreased. | Rebalancear portfólio, escalar risco, mudar prioridade de funding. |
| Onde investir capacidade? | Portfolio, Team, Initiative, Capability, ValueCase. | Capacity Allocation Fit, Capacity Forecast Risk, Cost of Delay. | TeamCapacityChanged, QueueThresholdBreached, CostOfDelayCalculated. | Realocar capacidade, reduzir WIP, acelerar trabalho crítico. |
| Qual investimento está subperformando? | Investment, Initiative, ValueCase, Benefit. | Funding Variance, ROI, Benefit Variance, Value Leakage. | InvestmentUnderperformingDetected, BenefitRejected. | Pausar, cancelar, redesenhar ou revalidar investimento. |

### Perguntas de Discovery

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Onde estamos parados? | BusinessNeed, PainPoint, Discovery, Queue, Owner. | Business Discovery Health, Business Discovery Lead Time, Queue Time. | BusinessNeedCaptured, PainPointRegistered, QueueEntered. | Atribuir owner, qualificar need, iniciar discovery, rejeitar demanda. |
| Qual discovery está envelhecendo? | Discovery, Hypothesis, Experiment, Finding. | Discovery Quality Score, Discovery Rework Rate, Aging. | DiscoveryStarted, HypothesisDefined, EvidenceCollected. | Pivotar, pausar, aprofundar pesquisa, converter em oportunidade. |
| Qual evidência falta antes da priorização? | BusinessEvidence, ProblemStatement, OpportunityAssessment. | Evidence Coverage, Traceability Health Score. | BusinessEvidenceAttached, OpportunityAssessed. | Bloquear compromisso prematuro, solicitar evidência. |

### Perguntas de Requisitos

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Quais requisitos estão pendentes? | FunctionalRequirement, NonFunctionalRequirement, AcceptanceCriterion. | Requirements Health, Requirements Queue Time. | RequirementCreated, RequirementReviewed. | Atribuir reviewer, completar critérios, rejeitar requisito fraco. |
| Quais requisitos carecem de revisão? | Requirement, Reviewer, Risk, Dependency. | Review Time, Approval Time, Traceability Health Score. | RequirementReviewed, RequirementApproved, RequirementRejected. | Aprovar, rejeitar, retornar ao discovery. |
| Quais requisitos carecem de rastreabilidade? | Requirement, Opportunity, BusinessNeed, Feature. | Traceability Gap Count, Requirements Health. | RequirementCreated, EvidenceAttached. | Corrigir origem, bloquear solution design. |

### Perguntas de Solução

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Quais soluções aguardam aprovação? | SolutionDesign, SolutionReview, SolutionApproval. | Solution Health, Review Time, Approval Aging. | SolutionReviewRequested, SolutionApproved, SolutionRejected. | Aprovar, rejeitar, solicitar ajustes, conceder exceção. |
| Quais decisões arquiteturais estão pendentes? | SolutionDecision, ArchitectureReview, Capability, Offer. | Architecture Review Health, Decision Latency, Architecture Debt Score. | ArchitectureReviewCompleted, DecisionSLAExceeded. | Decidir trade-off, registrar dívida, aprovar modernização. |
| Qual solução tem risco de segurança, dados ou compliance não resolvido? | SecurityReview, DataReview, ComplianceReview, Risk. | Control Adherence Rate, Evidence Coverage, Solution Health. | SecurityReviewCompleted, DataReviewCompleted, ComplianceReviewCompleted. | Exigir mitigação, aceitar risco, bloquear readiness. |

### Perguntas de Delivery

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Qual feature está bloqueada? | Feature, Story, Task, Blocker, Owner. | Blocked Time, Blocked Work Count, Blocker Resolution Health. | FeatureBlocked, StoryBlocked, BlockerCreated. | Atribuir owner, escalar blocker, replanejar delivery. |
| Qual fila está congestionada? | Queue, FlowStage, WorkItem, Team. | Queue Time, WIP by Flow Stage, Bottleneck Severity. | QueueEntered, QueueThresholdBreached, BottleneckDetected. | Reduzir WIP, rebalancear capacidade, alterar prioridade. |
| Qual compromisso está em risco? | Initiative, Epic, Feature, Release. | Delivery Health Score, Commitment Reliability, Schedule Forecast Accuracy. | FeatureCompleted, ReleasePublished, ForecastUpdated. | Ajustar escopo, renegociar compromisso, escalar dependência. |

### Perguntas de Valor

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Qual benefício ainda não foi realizado? | ValueCase, ObservedBenefit, ValidatedBenefit. | Planned Value, Forecast Value, Realized Benefit, Validated Benefit. | BenefitObserved, BenefitValidated, BenefitRejected. | Validar benefício, corrigir atribuição, revisar value case. |
| Qual hipótese falhou? | ProductHypothesis, ValueCase, Benefit, Outcome. | Hypothesis Validation Accuracy, Benefit Variance, Value Leakage. | HypothesisInvalidated, BenefitRejected, ValueLeakageDetected. | Pivotar produto, interromper investimento, redesenhar adoção. |
| Qual valor está em risco? | Portfolio, Initiative, ValueCase, KPI. | Investment At Risk, Value Leakage, Cost of Delay. | ValueAtRiskIncreased, CostOfDelayThresholdBreached. | Acelerar, pausar, cancelar ou aceitar risco. |

### Perguntas de Governança

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Quais alertas continuam abertos? | Alert, AlertCondition, AlertAction, AlertEvidence, AlertValidation. | Alert Aging, Alert Resolution Health. | AlertDetected, AlertActionRegistered, AlertReopened. | Atribuir ação, exigir evidência, validar condição, escalar. |
| Quais evidências estão faltando? | Evidence, Decision, Validation, Control, Alert. | Evidence Coverage, Governance Health Score. | EvidenceRequested, EvidenceAttached. | Bloquear decisão, solicitar evidência, reabrir achado. |
| Quais decisões estão atrasadas? | Decision, DecisionGate, Approval. | Decision SLA, Decision Latency, Approval Aging. | DecisionCreated, DecisionSLAExceeded. | Escalar autoridade, convocar comitê, formalizar exceção. |

### Perguntas de Arquitetura

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Qual capability está degradada? | Capability, Service, Offer, Product, Initiative. | Capability Health Score, Capability Traceability Health, Architecture Debt Score. | CapabilityHealthDegraded, ArchitectureDebtRegistered. | Priorizar modernização, aceitar risco, criar iniciativa. |
| Qual offer apresenta maior risco? | Offer, BusinessService, TechnologyService, Product. | Offer Health Score, Offer Adoption Score, Offer Traceability Health. | OfferRetired, ProductOfferAssociated, ProductOfferRemoved. | Substituir offer, revisar composição de produto, planejar transição. |
| Qual produto é afetado por dívida de capability? | Product, Offer, Capability, ArchitectureDebt. | Product Health Score, Architecture Debt Score, Time to Value. | ArchitectureDebtRegistered, ProductOfferAssociated. | Remediar dívida, ajustar roadmap, comunicar impacto. |

### Perguntas de Inteligência

| Pergunta | Entidades Primárias | Métricas / Scores | Evidências e Eventos | Decisões Suportadas |
| --- | --- | --- | --- | --- |
| Qual causa raiz aparece com maior frequência? | RootCause, Insight, Alert, Blocker, Decision. | Root Cause Accuracy, Recommendation Outcome Success. | RootCauseIdentified, AlertReopened, BlockerCreated. | Criar melhoria sistêmica, atualizar política, ajustar operating model. |
| Quais recomendações estão sendo ignoradas? | Recommendation, Decision, ActionPlan, Owner. | Recommendation Acceptance Rate, Action Aging. | RecommendationGenerated, DecisionRejected, ActionOverdue. | Escalar, aposentar recomendação fraca, melhorar governança. |
| Quais respostas do Copilot têm baixa confiança? | Explanation, EvidenceChain, DataConfidence. | Copilot Answer Confidence, Data Confidence Score. | ExplanationGenerated, DataConfidenceDegraded. | Restringir uso decisório, solicitar evidência, melhorar lineage. |

## 5. Arquitetura de Navegação

Nível 1 de navegação:

```text
Strategy
Portfolio
Discovery
Requirements
Solution Design
Delivery
Validation
Value Realization
Architecture
Metrics
Events
Intelligence
Governance
Knowledge
```

| Área | Propósito | Perguntas Respondidas | Entidades Principais | Métricas Principais | Eventos Principais |
| --- | --- | --- | --- | --- | --- |
| Strategy | Conectar intenção corporativa a outcomes, KPIs e execução. | Estamos entregando estratégia? Quais objetivos estão em risco? | Strategy, Theme, Objective, OKR, KR, Outcome, KPI. | Strategic Health Score, OKR Achievement Forecast, KPI Target Deviation. | StrategyCreated, ObjectiveCreated, OKRCreated, KeyResultProgressUpdated. |
| Portfolio | Governar investimentos, capacidade, iniciativas e trade-offs de valor. | Onde investir capacidade? Qual portfólio está crítico? | Portfolio, Investment, Funding, Opportunity, Initiative. | Portfolio Health Score, Capacity Allocation Fit, Funding Variance, Investment At Risk. | InvestmentApproved, FundingAllocated, PortfolioReprioritized. |
| Discovery | Qualificar needs, pains, problemas, hipóteses e oportunidades. | Onde estamos parados? Qual evidência falta? | BusinessNeed, PainPoint, Journey, Process, Discovery, Hypothesis. | Business Discovery Health, Discovery Quality Score, Evidence Coverage. | BusinessNeedCaptured, PainPointRegistered, HypothesisValidated. |
| Requirements | Governar requisitos funcionais e não funcionais rastreáveis. | Quais requisitos estão pendentes ou incompletos? | FunctionalRequirement, NonFunctionalRequirement, AcceptanceCriterion, Dependency. | Requirements Health, Review Time, Approval Time. | RequirementCreated, RequirementReviewed, RequirementApproved. |
| Solution Design | Governar decisões, reviews, aprovações e evidências de solução. | Quais soluções aguardam aprovação? Qual decisão está pendente? | SolutionDesign, SolutionRecord, SolutionDecision, Review, SolutionApproval. | Solution Health, Architecture Review Health, Engineering Review Health. | SolutionDesignCreated, SolutionReviewRequested, SolutionApproved. |
| Delivery | Monitorar trabalho, fluxo, blockers e prontidão de release. | Qual feature está bloqueada? Qual fila está congestionada? | Initiative, Epic, Feature, Story, Task, Release, Blocker, Queue. | Lead Time, Cycle Time, Queue Time, Flow Health Score, Blocked Time. | FeatureStarted, FeatureBlocked, StoryCompleted, ReleasePublished. |
| Validation | Validar aceite, negócio, técnica, outcome e benefício. | O que aguarda validação? Qual critério falhou? | Validation, AcceptanceValidation, BusinessValidation, OutcomeValidation. | Validation Health, Validation Time, Evidence Coverage. | ValidationStarted, ValidationCompleted, ValidationRejected. |
| Value Realization | Comprovar valor planejado, forecast, observado, realizado e validado. | Qual benefício não foi realizado? Qual hipótese falhou? | ValueCase, BenefitHypothesis, ObservedBenefit, ValidatedBenefit, RejectedBenefit. | Planned Value, Forecast Value, Realized Benefit, Value Leakage, ROI. | ValueCaseCreated, BenefitObserved, BenefitValidated, BenefitRejected. |
| Architecture | Navegar Architecture Elevator e impacto product-offer-capability. | Qual capability está degradada? Qual offer está em risco? | Domain, SubDomain, BusinessLayer, Capability, Service, Offer, ApplicationService, ProductOfferAssociation. | Capability Health Score, Offer Health Score, Architecture Debt Score. | CapabilityCreated, OfferCreated, ProductOfferAssociated, ArchitectureDebtRegistered. |
| Metrics | Governar definições, observações, lineage, targets e confiança de métricas. | Esta métrica é confiável? O que mudou? | MetricDefinition, KPI, MeasurementTarget, HealthScore, Forecast, HeatMap. | Metric Ownership Coverage, Data Confidence Score, KPI Forecast Accuracy. | KPICreated, KPIUpdated, HealthScoreCalculated, ForecastGenerated. |
| Events | Reconstruir histórico causal e fatos auditáveis. | O que aconteceu? O que causou este estado? | DomainEvent, SourceEvent, GovernanceEvent, AnalyticalEvent, DerivedEvent. | Event freshness, completude, saúde de correlação. | Eventos catalogados. |
| Intelligence | Converter sinais em explicações, recomendações e decisões. | Por que está acontecendo? O que devemos fazer agora? | Signal, Insight, Explanation, RootCause, Recommendation, ActionPlan. | Recommendation Acceptance Rate, Root Cause Accuracy, Copilot Answer Confidence. | InsightGenerated, RootCauseIdentified, RecommendationGenerated. |
| Governance | Governar decisões, gates, aprovações, evidências, controles e alert closure. | Qual decisão está atrasada? Qual evidência falta? | Decision, DecisionGate, Approval, Control, Exception, Evidence, AlertResolution. | Governance Health Score, Decision Latency, Evidence Coverage, Alert Resolution Health. | DecisionCreated, GateApproved, EvidenceAttached, AlertResolved. |
| Knowledge | Explorar relações, evidências, decisões, learnings e padrões reutilizáveis. | O que sabemos? O que pode ser reutilizado? | KnowledgeGraph, KnowledgeAsset, Learning, DecisionPattern, EvidenceChain. | Knowledge Reuse Rate, validação de learning, cobertura de explicação. | LearningCaptured, KnowledgeAssetCreated, NarrativeGenerated. |

## 6. Arquitetura de Workspaces

| Workspace | Objetivo | Personas | KPIs | Alertas | Heat Maps | Decisões Suportadas |
| --- | --- | --- | --- | --- | --- | --- |
| Executive Workspace | Oferecer visão integrada de estratégia, valor, risco, decisões e prioridades. | Diretores, Executivos, Superintendentes. | Strategic Health Score, Portfolio Health Score, Investment At Risk, Value Realization Score, Decision Latency. | Objetivo em risco, value leakage, investimento em risco, decision SLA excedido. | Portfolio, Value Realization, Alert, Capability. | Repriorizar, financiar, pausar, acelerar, aceitar risco. |
| Strategy Workspace | Governar objetivos, OKRs, outcomes, KPIs e rastreabilidade para execução. | Diretores, Estratégia, PMO, Metrics Owners. | OKR Achievement Forecast, KPI Target Deviation, Strategic Alignment Coverage. | OKR em risco, KPI crítico, traceability health critical. | Portfolio, Value, Strategic Alignment. | Ajustar targets, conectar iniciativas, solicitar plano de recuperação. |
| Portfolio Workspace | Gerir funding, capacidade, iniciativas, dependências e decisões de portfólio. | Executivos, Superintendentes, PMO, Gerentes. | Portfolio Health Score, Capacity Allocation Fit, Funding Variance, Dependency Aging. | Portfólio crítico, funding divergente, bottleneck detectado. | Portfolio, Delivery, Blocker. | Rebalancear capacidade, repriorizar, escalar dependência. |
| Business Discovery Workspace | Qualificar needs, pains, jornadas, processos e evidências de negócio. | Business Teams, Product Teams, PMO. | Business Discovery Health, Business Discovery Lead Time, Evidence Coverage. | Evidência ausente, business queue aging. | Business Discovery. | Aceitar need, rejeitar demanda fraca, iniciar discovery. |
| Product Discovery Workspace | Gerir hipóteses, experimentos, findings e opportunity assessments. | Product Teams, Business Teams, Data Specialists. | Discovery Quality Score, Discovery Rework Rate, Hypothesis Validation Accuracy. | Discovery quality degraded, oportunidade parada. | Business Discovery, Value. | Pivotar, avançar, pausar, descartar oportunidade. |
| Requirements Workspace | Governar requisitos, critérios, dependências, riscos e reviews. | Product Teams, Business Analysts, Especialistas, Gerentes. | Requirements Health, Requirements Queue Time, Review Time, Approval Time. | Requirements quality alert, review pendente. | Requirements. | Aprovar, rejeitar, retornar ao discovery, completar evidência. |
| Solution Design Workspace | Coordenar solution records, reviews, decisões e aprovações. | Arquitetos, Engenharia, Segurança, Dados, Compliance, Gerentes. | Solution Health, Solution Time, Review Time, Architecture Review Health. | Solution review alert, approval aging, exception expired. | Solution, Architecture, Governance. | Aprovar solução, exigir mitigação, conceder exceção. |
| Architecture Workspace | Navegar capabilities, services, offers, application services e modernização. | Arquitetos, Executivos, Product Teams, Engenharia. | Capability Health Score, Service Health Score, Offer Health Score, Architecture Debt Score. | Capability degradada, architecture debt critical, offer retirement risk. | Architecture, Capability. | Modernizar, aposentar, substituir offer, aceitar risco. |
| Delivery Workspace | Acompanhar execução, fluxo, blockers, compromissos e releases. | Gerentes, Coordenadores, Product Teams, Engenharia. | Delivery Health Score, Lead Time, Cycle Time, Commitment Reliability, Blocked Time. | Feature bloqueada, stale work item, delivery crítico. | Delivery, Blocker. | Replanejar, atribuir owner, escalar, ajustar compromisso. |
| Validation Workspace | Gerir critérios, evidências e outcomes aceitos ou rejeitados. | Product Teams, Business Teams, Engenharia, Auditores. | Validation Health, Validation Time, Evidence Coverage, Time to Value. | Validação pendente, validação rejeitada, evidência ausente. | Validation. | Aceitar, rejeitar, reabrir, solicitar evidência. |
| Value Realization Workspace | Monitorar value case, forecast, benefício observado, validação e leakage. | Diretores, Product Teams, Financeiro, Value Sponsors. | Planned Value, Forecast Value, Realized Benefit, Validated Benefit, Value Leakage. | Value leakage detected, benefício rejeitado, forecast accuracy degraded. | Value Realization. | Validar benefício, revisar value case, pausar investimento. |
| Metrics Workspace | Governar definições, fórmulas, fontes, owners, lineage e confiança de métricas. | Data Specialists, Metrics Owners, Auditores, PMO. | Metric Ownership Coverage, Data Confidence Score, Lineage Completeness, Source Divergence. | Métrica sem owner, data confidence degraded, source divergence. | Data Quality, Metrics. | Aprovar métrica, restringir uso, solicitar reconciliação. |
| Intelligence Workspace | Investigar sinais, insights, causas raiz, recomendações e ações. | Personas decisórias, PMO, Dados, Governança. | Root Cause Accuracy, Recommendation Acceptance Rate, Copilot Answer Confidence. | Recomendação ignorada, causa raiz não resolvida, explicação de baixa confiança. | Flow, Alert, Portfolio, Value. | Aceitar recomendação, criar plano de ação, escalar causa sistêmica. |
| Governance Workspace | Gerir decisões, gates, aprovações, controles, exceções, evidências e auditabilidade. | Governance, Compliance, Auditores, PMO, Executivos. | Governance Health Score, Decision Latency, Approval Aging, Evidence Coverage. | Decision SLA exceeded, evidência ausente, alert resolution failed. | Governance, Alert. | Aprovar, rejeitar, escalar, reabrir closure inválido. |
| Knowledge Workspace | Explorar knowledge graph, learnings, decision patterns e evidence chains. | Todas as personas conforme autorização. | Knowledge Reuse Rate, validação de learning, EvidenceChain completeness. | Knowledge stale, evidence expired, resposta de baixa confiança. | Caminhos do Knowledge Graph. | Reutilizar padrão, contestar explicação, publicar learning. |

## 7. Arquitetura de Cockpits

| Cockpit | Perguntas Respondidas | Métricas Exibidas | Scores Exibidos | Heat Maps Exibidos | Recomendações Exibidas |
| --- | --- | --- | --- | --- | --- |
| Executive Cockpit | Estamos entregando estratégia? O que está em risco? O que decidir agora? | Investment At Risk, KPI Target Deviation, Cost of Delay, Decision Latency. | Strategic, Portfolio, Value Realization, Governance. | Portfolio, Value Realization, Alert, Capability. | Repriorizar, financiar, escalar, pausar, aceitar risco. |
| Portfolio Cockpit | Quais portfólios exigem ação? Onde capacidade está presa? | Funding Variance, Dependency Aging, Cost of Queue, Cost of Bottleneck. | Portfolio, Flow, Initiative. | Portfolio, Delivery, Blocker. | Rebalancear capacidade, resolver dependência, mudar prioridade. |
| Discovery Cockpit | Onde discovery está envelhecendo ou sem evidência? | Discovery Lead Time, Evidence Coverage, Discovery Rework Rate. | Business Discovery, Discovery Quality. | Business Discovery. | Qualificar, pivotar, rejeitar, solicitar evidência. |
| Requirements Cockpit | Quais requisitos bloqueiam solução ou delivery? | Requirements Queue Time, Review Time, Approval Time. | Requirements, Traceability. | Requirements. | Atribuir reviewer, corrigir critérios, rejeitar. |
| Solution Design Cockpit | Quais soluções e reviews bloqueiam readiness? | Solution Time, Review Time, Approval Aging. | Solution, Architecture Review, Engineering Review. | Solution, Architecture, Governance. | Aprovar, rejeitar, mitigar, conceder exceção. |
| Architecture Cockpit | Quais capabilities, services ou offers degradam valor? | Architecture Debt Score, Offer Adoption Score, progresso de modernização. | Capability, Service, Offer, Product. | Architecture, Capability. | Modernizar, substituir, aposentar, aceitar risco. |
| Delivery Cockpit | Qual compromisso de delivery está em risco? | Lead Time, Cycle Time, Queue Time, Blocked Time, Commitment Reliability. | Delivery, Flow, Blocker Resolution. | Delivery, Blocker. | Reduzir WIP, desbloquear, replanejar, escalar. |
| Validation Cockpit | Quais validações estão pendentes, falhas ou reabertas? | Validation Time, Evidence Coverage, taxa de rejeição. | Validation, Value Realization. | Validation. | Completar evidência, aceitar, rejeitar, reabrir. |
| Value Realization Cockpit | Que valor foi planejado, forecast, realizado e validado? | Planned Value, Forecast Value, Realized Benefit, Validated Benefit, ROI, Value Leakage. | Value Realization. | Value Realization. | Validar benefício, revisar value case, interromper leakage. |
| Governance Cockpit | Quais decisões, controles ou evidências exigem ação? | Decision SLA, Approval Aging, Evidence Coverage, Control Adherence Rate. | Governance, Alert Resolution. | Governance, Alert. | Escalar gate, exigir evidência, reabrir closure. |
| Flow Intelligence Cockpit | Onde estão filas, gargalos e perdas econômicas de fluxo? | Queue Time, Wait Time, Flow Efficiency, Bottleneck Severity, Cost of Queue. | Flow, Blocker Resolution. | Portfolio, Delivery, Blocker. | Reduzir WIP, rebalancear, remover gargalo. |
| Alert Cockpit | Quais alertas estão abertos, envelhecendo, reabertos ou falsamente resolvidos? | Alert Aging, Alert Resolution Time, Evidence Coverage. | Alert Resolution, Governance. | Alert. | Registrar ação, anexar evidência, validar condição, escalar. |
| Knowledge Cockpit | Quais learnings, padrões e caminhos causais podem ser reutilizados? | Knowledge Reuse Rate, validação de learning, outcome de recomendação. | Intelligence health, Copilot confidence. | Caminhos do Knowledge Graph. | Reutilizar padrão, publicar learning, aposentar ativo obsoleto. |

## 8. Arquitetura de Informação de Heat Maps

| Heat Map | Dimensões | Métricas Utilizadas | Drill-down | Drill-up | Ações Possíveis |
| --- | --- | --- | --- | --- | --- |
| Business Discovery Heat Map | Need, pain, jornada, processo, owner, aging. | Business Discovery Health, Business Discovery Lead Time, Evidence Coverage. | Célula -> BusinessNeed -> PainPoint -> Evidence -> Owner. | Need -> Product / Portfolio / Objective. | Qualificar, atribuir owner, solicitar evidência, rejeitar. |
| Requirements Heat Map | Requirement, reviewer, owner, produto, iniciativa, status. | Requirements Health, Requirements Queue Time, Review Time, Approval Time. | Célula -> Requirement -> Criteria -> Review -> Approval. | Requirement -> Opportunity -> Need -> Objective/Product. | Corrigir requisito, atribuir reviewer, aprovar, rejeitar. |
| Solution Heat Map | SolutionDesign, tipo de review, reviewer, risco, aprovação. | Solution Health, Solution Time, Review Time, Approval Time. | Célula -> SolutionDesign -> Review -> Evidence -> Decision. | Solution -> Requirement -> Initiative -> Product -> Capability. | Resolver review, conceder exceção, aprovar/rejeitar. |
| Architecture Heat Map | Domain, subdomain, business layer, capability, service, offer. | Capability Health Score, Service Health Score, Offer Health Score, Architecture Debt Score. | Célula -> Capability -> Service -> Offer -> Product -> Debt. | Capability -> Objective / KPI / ValueCase. | Modernizar, remediar, substituir offer, aceitar risco. |
| Delivery Heat Map | Initiative, epic, feature, release, queue, owner. | Initiative Health Score, Lead Time, Queue Time, Aging WIP, Blocked Time. | Célula -> Feature -> Story -> Task -> Blocker. | Feature -> Epic -> Initiative -> Portfolio -> Objective. | Replanejar, desbloquear, reduzir WIP, escalar. |
| Validation Heat Map | Tipo de validation, critério, owner, evidência, outcome. | Validation Health, Validation Time, Evidence Coverage, Time to Value. | Célula -> Validation -> Criterion -> Evidence -> Outcome. | Validation -> Release -> Product -> Objective. | Aceitar, rejeitar, solicitar evidência, reabrir. |
| Value Realization Heat Map | Value case, benefício, KPI, produto, portfólio, período. | Planned Value, Forecast Value, Realized Benefit, Validated Benefit, Value Leakage. | Célula -> Benefit -> ValueCase -> KPI -> Evidence. | Benefit -> Outcome -> OKR -> Objective. | Validar, rejeitar, revisar forecast, interromper leakage. |
| Capability Heat Map | Domain, subdomain, capability, offer, product, initiative. | Capability Health Score, Capability Coverage, Capability Traceability Health. | Célula -> Capability -> Services -> Offers -> Products. | Capability -> Strategic Objective -> KPI / ValueCase. | Corrigir rastreabilidade, modernizar, priorizar capability. |
| Alert Heat Map | Tipo de alerta, condição, severidade, owner, aging, estado de validação. | Alert Aging, Alert Resolution Time, Alert Resolution Health, Evidence Coverage. | Célula -> Alert -> Condition -> Action -> Evidence -> Validation. | Alert -> entidade afetada -> Portfolio / Objective. | Registrar ação, anexar evidência, validar condição, escalar. |
| Blocker Heat Map | Tipo de blocker, owner, causa, severidade, entidade, squad. | Blocked Time, Blocker Resolution Health, Bottleneck Severity. | Célula -> Blocker -> WorkItem -> Owner -> Evidence. | Blocker -> Feature -> Initiative -> Portfolio. | Atribuir owner, escalar, resolver, validar. |
| Portfolio Heat Map | Portfolio, investment, initiative, capacity, dependency, value. | Portfolio Health Score, Capacity Allocation Fit, Funding Variance, Investment At Risk. | Célula -> Portfolio -> Investment -> Initiative -> Dependency / ValueCase. | Portfolio -> Theme -> Objective -> Strategy. | Rebalancear capacidade, repriorizar, financiar, pausar. |

## 9. Arquitetura de Drill-Down

Caminhos universais de drill-down:

```text
Corporate Strategy -> Strategic Objective -> Portfolio -> Initiative -> Feature -> Story -> Task
Capability -> Service -> Offer -> Product -> Initiative -> Feature
Alert -> Root Cause -> Evidence -> Action Plan -> Validation
Metric -> Components -> Events -> Evidence -> Root Cause -> Recommendation
Forecast -> Scenario -> Assumption -> Driver -> Evidence -> Decision
Heat Map -> Cell -> Entity -> Metric Driver -> Event -> Evidence
```

Regras universais:

- Drill-down nunca deve terminar em uma agregação inexplicada quando entidades de origem existem.
- Cada passo de drill-down deve preservar filtros, período, escopo, autorização e data confidence.
- Quando um nível inferior não estiver disponível, o motivo deve ser explícito: relação ausente, permissão ausente, integração ausente, dado atrasado ou nível não suportado.
- Drill-down de score deve expor componentes, pesos, faixas, fórmulas, dados ausentes e confiança.
- Drill-down de forecast deve expor versão, premissas, drivers, cenários, horizonte e confiança.
- Drill-down de alerta deve expor condição, regra de disparo, owner, ação, evidência, validação e estado de encerramento.
- Drill-down de heat map deve expor drivers da célula e entidades afetadas.

## 10. Navegação de Rastreabilidade

O caminho Need-to-Value é:

```text
Need -> Pain -> Journey -> Discovery -> Requirement -> Solution -> Feature -> Story -> Validation -> Outcome -> Value
```

Caminho expandido da EDIP:

```text
BusinessNeed -> PainPoint -> Customer/OperationalJourney -> BusinessProcess -> ProblemStatement -> Discovery -> Hypothesis -> Opportunity -> FunctionalRequirement / NonFunctionalRequirement -> SolutionDesign -> Readiness -> Feature -> Story -> Validation -> Outcome -> ValueCase -> ValueRealization.
```

Qualquer entidade deve permitir navegação para cima e para baixo quando relações explícitas existirem:

- Navegação para cima explica propósito, origem, contexto decisório e justificativa estratégica.
- Navegação para baixo explica execução, evidência, validação e valor realizado.
- Navegação lateral explica capability, produto, owner, risco, dependência, alerta, decisão e evidência relacionados.
- Rastreabilidade ausente é exceção visível com owner, severidade, próxima ação e impacto de governança.
- Rastreabilidade deve ser explícita e auditável, não inferida apenas por nome, similaridade textual ou proximidade organizacional.

## 11. Arquitetura de Explainability

Toda métrica deve permitir:

```text
Metric -> Components -> Events -> Evidence -> Root Cause -> Recommendation
```

Toda recomendação deve permitir:

```text
Recommendation -> Insight -> Evidence -> Metrics -> Events
```

Níveis de explicabilidade:

| Nível | Exigência |
| --- | --- |
| O que mudou | Mostrar métrica, score, forecast, alerta ou estado de entidade alterado. |
| Onde | Mostrar entidade afetada, escopo, período, portfólio, produto, capability ou owner. |
| Por que | Mostrar cadeia causal, fatores contribuintes, eventos e evidências. |
| Confiança | Mostrar qualidade de dados, lineage, premissas e limitações. |
| Ação | Mostrar owner, ação recomendada, urgência e risco da inação. |
| Decisão | Mostrar autoridade, opções de decisão, evidências obrigatórias e impacto auditável. |
| Aprendizado | Mostrar casos anteriores, padrões e knowledge assets reutilizáveis. |

Explicações devem diferenciar:

- Causa comprovada.
- Fator contribuinte.
- Dependência.
- Inferência governada.
- Correlação.
- Evidência ausente.
- Dado de baixa confiança.

## 12. Modelo de Experiência de Alertas

Um alerta é uma exceção acionável, não um marcador visual.

Todo alerta deve mostrar:

- Motivo: condição original, regra de disparo, threshold, métrica ou evento de origem.
- Impacto: objetivo, portfólio, produto, capability, iniciativa, value case ou controle afetado.
- Owner: alert owner, action owner, evidence owner e validation owner.
- SLA: tempo esperado de tratamento por severidade e escopo.
- Aging: tempo aberto, tempo no estado atual e tempo desde a última ação.
- Evidências: evidência anexada, evidência ausente, validade e classificação.
- Causa raiz: causa proposta ou validada e cadeia causal.
- Ações: ação necessária, status da ação, prazo e papel accountable.
- Validações: validação da condição original e elegibilidade de encerramento.

Ciclo de vida:

```text
AlertDetected -> InTreatment -> ActionRegistered -> EvidenceAttached -> ConditionValidated -> ResolutionProposed -> AlertResolved
```

Um alerta não pode ser encerrado sem:

- AlertAction.
- AlertEvidence.
- AlertValidation confirmando que a condição original desapareceu, foi mitigada ou foi formalmente aceita por autoridade definida.

Encerramento inválido deve gerar reabertura ou rejeição:

```text
AlertResolved -> AlertReopened quando a condição retorna, a validação falha ou a evidência é insuficiente.
```

## 13. Arquitetura de Suporte à Decisão

| Classe de Decisão | Exemplos | Informações Necessárias | Métricas Necessárias | Eventos Necessários | Evidências Necessárias | Explicações Necessárias |
| --- | --- | --- | --- | --- | --- | --- |
| Operacional | Atribuir owner, desbloquear trabalho, reduzir WIP, completar readiness. | Queue, blocker, work item, owner, SLA, aging. | Queue Time, Blocked Time, Aging WIP, Blocker Resolution Health. | QueueEntered, BlockerCreated, WorkItemUnblocked. | BlockerEvidence, evidência de readiness, evidência de ação. | Causa do bloqueio, próximo evento esperado, owner. |
| Tática | Replanejar iniciativa, ajustar escopo, escalar dependência, aprovar requisito. | Initiative, epic, feature, dependency, requirement, forecast. | Initiative Health Score, Delivery Health Score, Review Time, Dependency Aging. | RequirementApproved, FeatureBlocked, DependencyRaised, ForecastUpdated. | Requirement evidence, solution evidence, dependency evidence. | Impacto em compromisso, valor, risco e rastreabilidade. |
| Executiva | Repriorizar portfólio, rebalancear capacidade, aprovar funding, aceitar risco material. | Portfolio, investment, capacity, value, risk, decision gate. | Portfolio Health Score, Investment At Risk, Cost of Delay, Capacity Allocation Fit. | FundingAllocated, ValueAtRiskIncreased, DecisionSLAExceeded. | Business case, value case, decision rationale, risk evidence. | Trade-off, consequência da inação, confiança do forecast. |
| Estratégica | Alterar objetivo, revisar target, pausar iniciativa estratégica, redirecionar tese de valor. | Objective, OKR, KPI, outcome, portfolio, benefit, forecast. | Strategic Health Score, OKR Achievement Forecast, KPI Target Deviation, Value Realization Score. | KRTargetChanged, KPIUpdated, BenefitRejected, ForecastAccuracyDegraded. | Aprovação estratégica, KPI lineage, evidência de benefício, decisão executiva. | Se o problema é execução, valor, qualidade de dados, capability ou estratégia. |

## 14. Arquitetura de Busca

A busca corporativa deve localizar:

- Estratégia, tema estratégico, objetivo, OKR, KR e KPI.
- Capability, business service, technology service, offer e application service.
- Product, product outcome, roadmap e product-offer association.
- Portfolio, investment, funding, opportunity e initiative.
- Feature, story, task, release e blocker.
- Requirement, solution design, review, approval e validation.
- Alert, decision, evidence, insight, root cause, recommendation e learning.

Filtros de busca:

| Filtro | Propósito |
| --- | --- |
| Tipo de entidade | Limitar a strategy, capability, product, initiative, feature, requirement, alert, decision, evidence ou insight. |
| Escopo | Portfolio, product, business unit, capability, domain, team, owner ou geografia. |
| Período | Criado, atualizado, período ativo, horizonte de forecast, período de benefício ou event time. |
| Status | Draft, active, blocked, pending, approved, rejected, validated, retired ou reopened. |
| Severidade / criticidade | Informational, warning, risk, critical, regulatory critical. |
| Estado de rastreabilidade | Completa, incompleta, órfã, exceção, herdada ou ausente. |
| Estado de evidência | Disponível, ausente, expirada, rejeitada, restrita ou aguardando validação. |
| Confiança | Alta, média, baixa ou dados insuficientes. |
| Autorização | Resultados devem respeitar papel, ownership, sensibilidade, evidence classification e decision classification. |

Resultados de busca devem mostrar por que o resultado apareceu, owner da entidade, contexto, caminho de rastreabilidade e próximas ações disponíveis.

## 15. Navegação de Knowledge

A exploração do Knowledge Graph deve suportar estes caminhos canônicos:

```text
Capability -> Products -> Offers -> Features -> Decisions -> Alerts -> Learnings
Need -> Pain -> Discovery -> Requirement -> Solution -> Outcome
Strategy -> Objective -> KPI -> Initiative -> ValueCase -> Benefit -> Evidence
Decision -> Evidence -> ActionPlan -> Outcome -> Learning
Alert -> Condition -> Action -> Evidence -> Validation -> Resolution
Product -> Offer -> Service -> Capability -> ArchitectureDebt -> ModernizationPlan
```

Regras de navegação de knowledge:

- Relações devem ser tipadas, direcionais e explicáveis.
- Cada relação deve exibir confiança, fonte e lineage quando relevante.
- Caminhos de knowledge devem preservar distinções semânticas: Product não é Capability, Service ou Offer.
- Traversal de Evidence Graph e Decision Graph deve obedecer classificação e autorização.
- Learnings devem expor contexto de validade, outcome observado e limitações de reutilização.

## 16. Arquitetura da Experiência do Copilot

O Copilot é uma interface de investigação e suporte à decisão. Ele não é autoridade decisória e não pode aprovar, rejeitar, encerrar alertas, aceitar risco ou alterar estado de domínio sem comando governado executado por serviço autorizado.

| Pergunta | Contexto Necessário | Métricas Necessárias | Evidências Necessárias | Explicações Necessárias |
| --- | --- | --- | --- | --- |
| Onde estamos atrasados? | Portfolio, initiative, queue, flow stage, work items, owner, período. | Lead Time, Queue Time, Blocked Time, Schedule Forecast Accuracy. | Histórico de fila, blocker evidence, dependency evidence, forecast drivers. | Cadeia de atraso com causa direta e contribuintes, objetivo afetado e próxima ação. |
| Onde está o maior gargalo? | Heat maps enterprise, portfolio, delivery e squad; capacidade de fila; owner. | Bottleneck Severity, Queue Time, WIP by Flow Stage, Cost of Bottleneck. | Eventos de entrada/saída de fila, bottleneck detection e tentativas de resolução. | Local do gargalo, escopo, impacto econômico, owner e opções de mitigação. |
| Quem deveria agir? | Modelo de owner, RACI, role assignments, caminho de escalation, SLA atual. | SLA breach, Alert Aging, Decision Latency, Blocker Aging. | Atribuições de owner, decision gates, histórico de ações. | Papel accountable, action owner, alvo de escalonamento e limites de autoridade. |
| O que está bloqueando valor? | ValueCase, initiative, feature, blocker, alert, decision e contexto de KPI. | Investment At Risk, Value Leakage, Cost of Delay, Benefit Variance. | Value evidence, blocker evidence, decision evidence. | Caminho causal do blocker ou decisão até impacto em valor. |
| Qual capability está degradada? | Capability graph, service, offer, product, initiative e architecture debt. | Capability Health Score, Architecture Debt Score, Capability Traceability Health. | Architecture assessment, debt evidence, exception evidence. | Drivers da capability, produtos afetados e impacto estratégico. |
| Qual benefício está em risco? | Value case, período do benefício, KPI, outcome, portfolio e estado de delivery. | Forecast Value, Realized Benefit, Validated Benefit, Value Forecast Accuracy. | Baseline, target, benefit evidence, validation evidence. | Se o risco vem de hipótese, delivery, adoção, atribuição ou evidência. |

Requisitos de resposta do Copilot:

- Declarar sempre confiança e limitações.
- Citar entidades, métricas, eventos e referências de evidência disponíveis ao usuário.
- Separar fatos de inferência.
- Oferecer próxima ação, owner e caminho de decisão.
- Não apresentar conclusões sem suporte como fato.

## 17. Arquitetura de Personalização

| Tipo de Personalização | Significado | Efeito Padrão |
| --- | --- | --- |
| Role Based Views | Experiência por persona, autoridade e responsabilidade. | Diretores veem risco estratégico e decisões; coordenadores veem fluxo, blockers e owners. |
| Context Based Views | Experiência por pergunta ativa, investigação ou contexto decisório. | Uma pergunta de valor prioriza value cases, benefícios e evidências. |
| Capability Based Views | Escopo por domain, subdomain, capability, service ou offer do Architecture Elevator. | Arquitetos e capability owners veem produtos, iniciativas e dívidas afetadas. |
| Portfolio Based Views | Escopo por portfolio, investment, initiative e funding cycle. | Executivos e PMO veem capacidade, funding, dependências e valor. |
| Product Based Views | Escopo por product, roadmap, outcome, offer composition e backlog. | Product teams veem discovery, requisitos, features e evidência de outcome. |
| Business Unit Based Views | Escopo por unidade organizacional, diretoria, área ou executivo accountable. | Executivos comparam estratégia, risco, valor e decisões entre unidades. |
| Ownership Based Views | Escopo por entidades em que o usuário é owner, reviewer, approver ou action owner. | Usuários veem decisões, alertas, blockers, reviews e obrigações de evidência pendentes. |

Personalização não deve criar verdades alternativas. Ela altera apenas priorização, profundidade, acesso e contexto padrão.

## 18. Prevenção de Sobrecarga de Informação

A EDIP deve evitar excesso de dashboards, métricas, alertas e filtros.

Mecanismos:

- Progressive disclosure: mostrar primeiro o sinal dominante, depois drivers e evidências.
- Contextual filtering: filtros padrão devem vir de persona, workspace, pergunta e entidade atual.
- Persona prioritization: cada persona começa pelas decisões e obrigações relevantes à sua autoridade.
- Alert deduplication: agrupar alertas por condição, entidade, owner, causa raiz e cadeia causal.
- Governança de métricas: apenas métricas governadas com owner, fórmula e fonte devem aparecer como decision-grade.
- Catálogo de perguntas: evitar variantes de dashboard que respondem a mesma pergunta com nomes diferentes.
- Confidence gating: métricas e forecasts de baixa confiança devem aparecer como problemas de qualidade, não misturados silenciosamente a dados confiáveis.
- Exposição de exceções: owner ausente, evidência ausente, rastreabilidade ausente e dado stale devem aparecer como exceções.
- Disciplina de filtros: filtros devem ser reutilizáveis, nomeados, compartilháveis e rastreáveis a escopo.

## 19. Governança de UX

Princípios de governança de UX:

- Toda tela deve responder uma pergunta.
- Todo dashboard deve possuir drill-down.
- Todo item operacional deve possuir drill-up quando houver rastreabilidade.
- Toda métrica deve possuir owner, fórmula, fonte, periodicidade, baseline, target e confiança.
- Todo alerta deve possuir owner, ação, evidência e validação.
- Toda recomendação deve possuir evidência, impacto, urgência, owner sugerido e risco da inação.
- Todo forecast deve mostrar premissas, drivers, horizonte, cenários e confiança.
- Todo heat map deve expor drivers, entidades, drill-down e drill-up.
- Todo caminho de decisão deve preservar evidência, autoridade, justificativa e trilha de auditoria.
- Toda resposta do Copilot deve mostrar confiança, fontes, limitações e próxima ação.
- Toda visão deve diferenciar dado ausente, dado atrasado, dado inconsistente e resultado real.

## 20. Persona Landing Architecture

A EDIP deve suportar Landing Pages personalizadas por persona. A navegação não deve começar obrigatoriamente por menus; ela deve começar pelo contexto decisório do usuário, por suas responsabilidades, por suas pendências e pelos riscos sob sua autoridade.

Landing Page é a home page especializada de uma persona. Ela não é uma página promocional nem um dashboard genérico. Ela é um ponto de entrada decisório que combina sinais prioritários, obrigações, alertas, recomendações, investigações abertas, comparações relevantes e caminhos de drill-down/drill-up.

### Regras Universais de Landing

- Toda landing deve mostrar contexto de escopo: persona, período, portfolio, product, capability, business unit, ownership e permissões aplicadas.
- Toda landing deve priorizar exceções, decisões pendentes, valor em risco, evidências ausentes e recomendações acionáveis.
- Todo widget conceitual deve permitir drill-down para entidades causadoras e drill-up para justificativa estratégica.
- Toda métrica exibida deve preservar owner, fonte, confidence, periodicidade e lineage.
- Toda recomendação exibida deve mostrar evidência, impacto, owner sugerido, urgência e risco da inação.
- Personalização pode alterar prioridade e profundidade, mas não pode criar verdade alternativa.

### Landings por Persona

| Landing | Widgets Conceituais | Informações Obrigatórias | Decisões Suportadas | Personalização |
| --- | --- | --- | --- | --- |
| Director Landing | Objetivos em risco, valor em risco, decisões pendentes, portfólios críticos, capabilities degradadas, alertas críticos, recomendações prioritárias. | Strategic Health Score, OKR Achievement Forecast, Investment At Risk, Value Leakage, Decision Latency, Critical Alerts, Capability Health Score. | Repriorizar objetivos, aprovar funding, pausar ou acelerar iniciativa, aceitar risco, escalar decisão executiva. | Escopo por diretoria, tema estratégico, período executivo, comitê, portfolio e owner estratégico. |
| Executive Landing | Portfólios críticos, investimentos críticos, dependências críticas, funding em risco, capacidade insuficiente. | Portfolio Health Score, Funding Variance, Capacity Allocation Fit, Dependency Aging, Cost of Delay, Value at Risk. | Rebalancear portfólio, realocar capacidade, liberar funding, escalar dependência, revisar compromisso. | Escopo por business unit, portfolio, investment cycle, sponsor e capacidade disponível. |
| Superintendent Landing | Forecast trimestral, iniciativas críticas, dependências envelhecidas, filas críticas, value leakage. | Schedule Forecast Accuracy, Initiative Risk Exposure, Queue Time, Bottleneck Severity, Dependency Aging, Value Leakage. | Replanejar trimestre, priorizar iniciativas, destravar dependência, ajustar capacidade, escalar risco. | Escopo por trimestre, portfolio, produto, time, owner e stage do fluxo. |
| Manager Landing | Blockers, readiness, iniciativas atrasadas, entregas em risco, aprovações pendentes. | Initiative Health Score, Readiness Health, Blocked Time, Delivery Health Score, Approval Aging, Release Readiness. | Replanejar escopo, atribuir owner, escalar blocker, solicitar aprovação, ajustar release. | Escopo por iniciativa, release, squad, product, dependency e milestone. |
| Coordinator Landing | Aging, filas, WIP, blockers, SLA breaches. | Aging WIP, Queue Time, WIP by Flow Stage, Blocker Resolution Health, SLA breach, Flow Efficiency. | Reduzir WIP, mover fila, atribuir action owner, escalar blocker, corrigir aging. | Escopo por squad, queue, flow stage, ciclo, owner e severidade. |
| Architect Landing | Capabilities degradadas, architecture debt, reviews pendentes, offers em risco, modernizações prioritárias. | Capability Health Score, Architecture Debt Score, Architecture Review Health, Offer Health Score, Capability Modernization Score. | Aprovar solution design, registrar dívida, priorizar modernização, substituir offer, aceitar exceção. | Escopo por architecture domain, subdomain, capability, service, offer, product e architecture board. |

### Relação com Workspaces

Landings não substituem workspaces. Elas selecionam o ponto de entrada mais relevante para a persona e encaminham para Executive Workspace, Portfolio Workspace, Architecture Workspace, Delivery Workspace, Governance Workspace, Investigation Workspace ou Entity Workspace conforme a pergunta ativa.

## 21. Timeline Navigation Architecture

A EDIP deve oferecer navegação temporal corporativa. Toda entidade relevante deve possuir histórico navegável, reconstruível a partir de eventos, métricas, scores, forecasts, decisões, evidências, alertas e validações.

Timeline não é apenas log. Timeline é uma narrativa temporal investigável que permite responder o que aconteceu, onde estamos e para onde estamos indo.

### Timelines Obrigatórias

| Timeline | Propósito | Conteúdo Temporal |
| --- | --- | --- |
| Strategy Timeline | Explicar evolução de estratégia, objetivos, OKRs, KRs, KPIs e decisões executivas. | ObjectiveCreated, KRTargetChanged, KPIUpdated, Strategic Health Score, forecasts de KR/KPI, decisões e evidências estratégicas. |
| Portfolio Timeline | Explicar evolução de funding, investimentos, capacidade, dependências, repriorizações e valor em risco. | InvestmentApproved, FundingAllocated, PortfolioReprioritized, DependencyRaised, Portfolio Health Score, Investment At Risk. |
| Capability Timeline | Explicar evolução de capability, serviços, offers, dívidas, exceções e modernização. | CapabilityCreated, CapabilityUpdated, CapabilityHealthDegraded, ArchitectureDebtRegistered, ArchitectureExceptionExpired, modernization events. |
| Product Timeline | Explicar evolução de produto, composição de offers, roadmap, outcomes e valor. | ProductCreated, ProductOfferAssociated, ProductOfferRemoved, OutcomeAssigned, ProductHealthCalculated, BenefitRejected. |
| Initiative Timeline | Explicar origem, escopo, progresso, riscos, blockers, decisões e impacto. | InitiativeCreated, InitiativeStarted, FeatureBlocked, ForecastUpdated, ValueAtRiskIncreased, DecisionSLAExceeded. |
| Feature Timeline | Explicar readiness, execução, bloqueios, validação e release. | FeatureCreated, ReadinessApproved, FeatureStarted, FeatureBlocked, FeatureCompleted, ValidationStarted. |
| Alert Timeline | Explicar condição original, ação, evidência, validação, resolução e reabertura. | AlertDetected, AlertActionRegistered, AlertEvidenceAttached, AlertConditionValidated, AlertResolved, AlertReopened. |
| Decision Timeline | Explicar criação, análise, aprovação, rejeição, evidências e resultado observado. | DecisionCreated, DecisionSLAExceeded, DecisionApproved, DecisionRejected, EvidenceAttached, DecisionOutcome observed. |
| Value Timeline | Explicar hipótese, baseline, target, forecast, benefício observado, validado, rejeitado e leakage. | ValueCaseCreated, ForecastGenerated, BenefitObserved, BenefitValidated, BenefitRejected, ValueLeakageDetected. |

### Modos de Timeline

| Modo | Pergunta | Conteúdo Obrigatório |
| --- | --- | --- |
| Historical View | O que aconteceu? | Eventos, decisões, evidências, mudanças de status, métricas observadas, alertas e validações. |
| Current State View | Onde estamos? | Estado atual, owner, SLA, aging, scores, evidências pendentes, riscos e recomendações ativas. |
| Future Projection View | Para onde estamos indo? | Forecasts, cenários, premissas, drivers, confidence, riscos futuros e decisões necessárias. |

### Regras de Timeline

- Toda timeline deve permitir alternar entre visão por entidade, por evento, por métrica, por decisão e por evidência.
- Eventos críticos devem mostrar causation, correlation, source, owner e confidence quando aplicável.
- Forecasts devem exibir versão, premissas, drivers, horizonte, cenário e accuracy histórica.
- Evidências sensíveis devem respeitar classification, access policy e finalidade de uso.
- Timeline deve permitir comparar antes/depois de uma decisão, aprovação, release, alerta ou mudança de forecast.

## 22. Comparative Analysis Architecture

A EDIP deve possuir capacidade nativa de comparação. Comparações são instrumentos de decisão, não rankings descontextualizados. Toda comparação deve preservar escopo, período, criticidade, confiança, fonte, contexto organizacional e diferenças de governança.

### Comparações Obrigatórias

| Comparação | Métricas Comparáveis | Scores Comparáveis | Heat Maps Comparáveis | Riscos Comparáveis | Valor Comparável |
| --- | --- | --- | --- | --- | --- |
| Portfolio vs Portfolio | Funding Variance, Capacity Allocation Fit, Dependency Aging, Cost of Delay, Investment At Risk. | Portfolio Health Score, Governance Health Score, Flow Health Score. | Portfolio, Delivery, Alert. | Dependências críticas, funding em risco, capacity shortage, value leakage. | Planned Value, Forecast Value, Realized Benefit, ROI. |
| Capability vs Capability | Capability Coverage, Architecture Debt Score, Modernization progress, Objective to Capability Coverage. | Capability Health Score, Capability Traceability Health. | Capability, Architecture. | Dívida, exceções expiradas, impacto em produto, lacunas de rastreabilidade. | ValueCase impactado, KPI impactado, produtos afetados. |
| Product vs Product | Product Outcome Progress, Adoption Trend, Time to Outcome, Feature Value Score. | Product Health Score, Value Realization Score. | Value Realization, Offer/Product composition. | Offer risk, baixa adoção, backlog desalinhado, leakage. | Forecast Value, Validated Benefit, Benefit Variance. |
| Offer vs Offer | Offer Adoption Score, Offer Traceability Health, service criticality, product usage. | Offer Health Score, Service Health Score. | Architecture, Capability, Offer/Product composition. | Aposentadoria, baixa adoção, debt, impacto em produto. | Produtos sustentados, value cases afetados, custo de transição. |
| Business Unit vs Business Unit | Strategic Alignment Coverage, Funding Variance, Decision Latency, Evidence Coverage. | Strategic Health Score, Portfolio Health Score, Governance Health Score. | Portfolio, Governance, Alert. | Decisões atrasadas, evidência ausente, capacidade insuficiente. | Valor planejado, forecast, realizado e validado por unidade. |
| Team vs Team | Lead Time, Cycle Time, Queue Time, WIP by Flow Stage, Blocked Time, Throughput. | Delivery Health Score, Flow Health Score, Blocker Resolution Health. | Delivery, Blocker, Flow. | WIP excessivo, blockers recorrentes, SLA breaches, baixa previsibilidade. | Cost of Queue, Cost of Bottleneck, impacto em release/value case. |
| Release vs Release | Release Lead Time, Release Readiness, Defect Leakage, Validation Time. | Technical Delivery Health, Validation Health. | Delivery, Validation. | Readiness rejeitado, defeitos, validação pendente, risco técnico. | Time to Value, benefício associado, value leakage. |
| Value Case vs Value Case | Planned Value, Forecast Value, Realized Benefit, Validated Benefit, Benefit Variance, ROI. | Value Realization Score, Data Confidence Score. | Value Realization. | Benefício rejeitado, evidência fraca, atribuição incerta, hipótese inválida. | Baseline, target, forecast, realized, validated, rejected. |

### Comparison Workspace

Comparison Workspace deve permitir:

- Selecionar entidades comparáveis por tipo e escopo.
- Normalizar período, unidade de medida, criticidade, portfolio, business unit e confidence.
- Exibir diferenças por métrica, score, heat map, risco, valor, owner, decisão e evidência.
- Evidenciar quando a comparação não é válida por diferença de fórmula, fonte, periodicidade, baseline, target, escopo ou qualidade de dado.
- Gerar recomendação quando a comparação revelar padrão de risco, oportunidade, underperformance ou learning reutilizável.

## 23. Investigation Workspace Architecture

A EDIP deve suportar investigações corporativas estruturadas. Uma investigação é um processo governado de apuração que transforma sinal, alerta ou pergunta em evidência, achados, insights, causa raiz, recomendações, decisões, outcomes e aprendizados.

### Entidade Conceitual: Investigation

Investigation pode ser iniciada por:

- Alerta.
- Valor não realizado.
- KPI degradado.
- Capability degradada.
- Incidente.
- Forecast degradado.
- Recomendação ignorada.

Modelo conceitual:

```text
Investigation -> Evidence -> Findings -> Insights -> Root Causes -> Recommendations -> Decisions -> Outcomes -> Learnings
```

### Investigation Workspace

| Área do Workspace | Propósito | Informação Obrigatória |
| --- | --- | --- |
| Trigger | Explicar por que a investigação começou. | Alert, KPI degraded, ValueLeakageDetected, CapabilityHealthDegraded, ForecastAccuracyDegraded, Recommendation ignored. |
| Scope | Definir o escopo investigado. | Entidade afetada, período, portfolio, product, capability, owner, severidade e autorização. |
| Evidence Board | Organizar evidências aceitas, rejeitadas, ausentes e expiradas. | EvidenceChain, source events, metric snapshots, decisionIds, lineageStatus. |
| Findings | Registrar achados verificáveis. | Achado, evidência associada, impacto, confidence e limitação. |
| Causal Analysis | Diferenciar causa, fator contribuinte, dependência, inferência e correlação. | CausalChain, RootCause, contributing factors, confidence. |
| Recommendations | Transformar causa em opções de ação. | Ação recomendada, impacto esperado, owner sugerido, urgência, risco da inação. |
| Decisions | Registrar decisão humana ou de comitê. | Decision, authority, rationale, evidence, expected outcome. |
| Outcomes | Medir resultado após ação. | DecisionOutcome, metric movement, validation, benefit impact. |
| Learnings | Consolidar conhecimento reutilizável. | Learning, applicability, limitation, related patterns. |

Perguntas obrigatórias:

- O que aconteceu?
- Por que aconteceu?
- Quem foi impactado?
- O que devemos fazer?
- O que aprendemos?

### Regras de Investigação

- Investigation deve preservar hipóteses testadas, evidências aceitas e evidências descartadas.
- Investigation crítica deve possuir owner, prazo, status, escopo, evidência mínima e decisão de encerramento.
- Encerramento de investigation deve declarar causa raiz validada ou limitação explícita quando a causa não puder ser comprovada.
- Investigation pode originar Narrative, Recommendation, Decision, ActionPlan e Learning.
- Investigation não substitui auditoria, mas deve produzir material suficiente para auditoria quando envolver decisão crítica, controle, valor ou alerta regulatório.

## 24. Narrative Architecture

A arquitetura de narrativas integra UX com o Intelligence Model. Narrative é uma explicação estruturada, auditável e orientada a decisão, derivada de eventos, métricas, scores, forecasts, heat maps, insights, evidências e decisões.

### Capacidades de Narrativa

| Capacidade | Propósito |
| --- | --- |
| Narrative Workspace | Criar, revisar, aprovar, publicar e acompanhar narrativas decisórias. |
| Narrative Explorer | Navegar narrativas por período, escopo, entidade, causa raiz, decisão, risco, valor e evidência. |
| Narrative Library | Reutilizar narrativas aprovadas, padrões, anti-patterns e learnings. |

### Tipos de Narrativa

| Tipo | Propósito | Gatilhos Típicos |
| --- | --- | --- |
| Weekly Executive Narrative | Explicar mudanças relevantes da semana para decisões executivas. | HealthScoreDegraded, BottleneckDetected, DecisionSLAExceeded, ForecastUpdated. |
| Monthly Portfolio Narrative | Explicar saúde, funding, capacidade, valor e riscos do portfólio. | PortfolioReprioritized, ValueAtRiskIncreased, InvestmentUnderperformingDetected. |
| Quarterly Strategy Narrative | Explicar progresso estratégico, OKRs, KPIs, outcomes e benefícios. | KeyResultProgressUpdated, KPIUpdated, BenefitValidated. |
| Value Narrative | Explicar captura, perda, rejeição ou validação de valor. | BenefitObserved, BenefitValidated, BenefitRejected, ValueLeakageDetected. |
| Capability Narrative | Explicar saúde, cobertura, dívida, offers, produtos e iniciativas afetadas por capability. | CapabilityUpdated, CapabilityHealthDegraded, ArchitectureDebtRegistered. |
| Incident Narrative | Explicar degradação severa, timeline, causa raiz, impacto e plano corretivo. | FlowHealthDegraded, DataConfidenceDegraded, BottleneckSeverityIncreased. |
| Decision Narrative | Explicar decisão, alternativas, evidências, autoridade, impacto esperado e resultado observado. | DecisionCreated, DecisionApproved, DecisionRejected, DecisionOutcome observed. |
| Alert Narrative | Explicar alerta, condição original, ação, evidência, validação e status de resolução. | AlertDetected, AlertActionRegistered, AlertResolved, AlertReopened. |

Cada narrativa deve responder:

- O que aconteceu?
- Por que aconteceu?
- O que está em risco?
- O que deve ser feito?
- Qual evidência suporta esta conclusão?

Navegação obrigatória:

```text
Narrative -> Insight -> Evidence -> Recommendation -> Decision
```

Regras de narrativa:

- Narrative não substitui evento, métrica, evidência ou decisão.
- Narrative deve preservar sourceEventIds, metricIds, scoreIds, evidenceIds, decisionIds, confidence e limitações.
- Narrative usada em comitê deve possuir versão, período, audiência, owner, status de revisão e trilha de aprovação.
- Narrative deve permitir drill-down para evidências e drill-up para estratégia, portfolio, capability, value case ou decisão.

## 25. Entity Workspace Architecture

Toda entidade relevante da EDIP deve possuir um workspace próprio. Entity Workspace é o ponto de investigação, decisão e rastreabilidade de uma entidade específica.

Entidades obrigatórias:

- Strategy.
- Portfolio.
- Initiative.
- Product.
- Offer.
- Capability.
- BusinessNeed.
- Opportunity.
- Requirement.
- Solution Design.
- Feature.
- Story.
- Validation.
- Value Case.
- Alert.
- Decision.
- Learning.

### Estrutura Universal de Entity Workspace

| Área | Propósito | Conteúdo Obrigatório |
| --- | --- | --- |
| Overview | Resumo executivo. | Status, owner, criticidade, health, período, próxima ação, riscos e exceções. |
| Traceability | Relações completas. | Drill-up, drill-down, relações laterais, lacunas, herança de rastreabilidade e justificativas formais. |
| Metrics | KPIs, scores e forecasts. | Metric definitions, observations, health scores, forecast scenarios, confidence e lineage. |
| Events | Histórico de eventos. | Domain events, source events, governance events, analytical events e derived events. |
| Evidence | Evidências associadas. | Evidence references, classification, validity, owner, access policy e evidence chain. |
| Decisions | Decisões associadas. | Decision, gate, approval, rationale, authority, evidence e outcome. |
| Alerts | Alertas associados. | Alert condition, severity, owner, action, evidence, validation, resolution e reopening. |
| Knowledge | Insights, learnings e recomendações. | Insights, root causes, recommendations, narratives, learnings e knowledge assets. |
| Timeline | Histórico temporal completo. | Eventos, métricas, scores, forecasts, decisões, evidências, alertas e validações ao longo do tempo. |
| Impact Analysis | Quem depende desta entidade e quem é impactado por ela. | Upstream/downstream dependencies, products, capabilities, initiatives, value cases, controls e business units afetadas. |

### Regras Universais de Navegação entre Entity Workspaces

- Todo Entity Workspace deve permitir abrir entidades relacionadas sem perder contexto de origem.
- Navegação deve preservar filtros, período, persona, escopo, confidence e autorização.
- Impact Analysis deve distinguir dependência direta, dependência indireta, impacto inferido e impacto comprovado.
- Entity Workspace de Alert deve destacar condição original, action, evidence, validation e closure eligibility.
- Entity Workspace de Decision deve destacar autoridade, rationale, evidência, impacto esperado, resultado observado e learning.
- Entity Workspace de Capability deve preservar a distinção Product != Capability, Product != Service e Product != Offer.
- Entity Workspace de Value Case deve diferenciar benefício planejado, forecast, observado, realizado, validado, rejeitado e leakage.

## 26. Navigation Intelligence Layer

A EDIP deve possuir uma camada de inteligência de navegação. Essa camada usa contexto, knowledge graph, evidências, métricas, eventos, investigações e padrões de decisão para sugerir próximos caminhos sem substituir autoridade humana.

Capacidades:

- Sugerir próximos passos.
- Sugerir investigações.
- Sugerir comparações.
- Sugerir entidades relacionadas.
- Sugerir narrativas relevantes.
- Sugerir evidence gaps e data quality checks.
- Sugerir casos semelhantes e learnings reutilizáveis.

### Regras da Navigation Intelligence Layer

- Sugestões devem declarar motivo, evidência, confidence, impacto esperado e limitação.
- Sugestões não podem ocultar baixa qualidade de dado, evidência ausente ou autorização insuficiente.
- Sugestões devem respeitar persona, role, ownership, scope, evidence classification e decision classification.
- Sugestões podem abrir workspace, investigation, comparison, narrative ou entity workspace, mas não podem executar decisão crítica sem comando autorizado.

### Exemplo: Visualização de Alert

Ao visualizar um Alert, a EDIP deve sugerir:

- Root Cause provável ou investigação pendente.
- Investigation relacionada ou criação de nova Investigation.
- Capability impactada.
- Produto impactado.
- Value case afetado.
- Narrativas relacionadas.
- Casos semelhantes.
- Evidence gaps para encerramento.
- Próxima ação e owner recomendado.

## 27. UX Maturity Model

O UX Maturity Model posiciona a EDIP pela capacidade de transformar dados em decisão, investigação e aprendizado organizacional.

| Nível | Nome | Característica | Capacidade UX |
| --- | --- | --- | --- |
| Nível 1 | Reporting | Exibe dados consolidados e status. | Dashboards básicos, filtros e exportação. |
| Nível 2 | Observability | Expõe origem, frescor, qualidade, eventos e estado atual. | Drill-down, lineage, data confidence, alertas e timelines básicas. |
| Nível 3 | Decision Support | Conecta métricas, riscos, evidências e recomendações a decisões. | Cockpits, workspaces decisórios, alertas acionáveis e Copilot com evidência. |
| Nível 4 | Investigation | Suporta investigação estruturada de causas, impactos e evidências. | Investigation Workspace, root cause, evidence board, timeline navegável e impact analysis. |
| Nível 5 | Organizational Learning | Captura outcomes, learnings, padrões e reutilização de conhecimento. | Knowledge Workspace, Narrative Library, Decision Patterns e learning reuse. |
| Nível 6 | Intelligence Driven Navigation | A navegação é assistida por inteligência e orientada por contexto decisório. | Landing personalizada, Navigation Intelligence Layer, sugestões de investigação, comparação, narrativa e entidades relacionadas. |

### Posicionamento da EDIP

A arquitetura da informação alvo da EDIP está desenhada para o Nível 6: Intelligence Driven Navigation. A implementação deve evoluir incrementalmente:

- MVP de experiência deve atingir pelo menos Nível 2 para evitar dashboards sem lineage.
- Primeiras decisões executivas exigem Nível 3.
- Alertas críticos, value leakage e capability degradation exigem Nível 4.
- Copilot executivo e recomendações reutilizáveis exigem Nível 5.
- Persona Landings inteligentes e navegação assistida exigem Nível 6.

## 28. Lacunas Remanescentes para Escala Enterprise

A arquitetura da informação da EDIP está preparada para sustentar uma plataforma corporativa de observabilidade, investigação, explicabilidade, governança, conhecimento e tomada de decisão em larga escala, desde que as lacunas abaixo sejam endereçadas nos próximos artefatos.

| Lacuna | Impacto | Artefato Responsável |
| --- | --- | --- |
| Contratos de consulta para landings, timelines, comparisons e entity workspaces ainda não formalizados. | Risco de frontend criar read models inconsistentes ou acoplados a projeções frágeis. | API_CONTRACTS.md e FRONTEND_ARCHITECTURE.md. |
| Modelo analítico de comparação ainda precisa normalizar período, confidence, baseline, fórmula e contexto. | Risco de comparações injustas ou decisões baseadas em métricas incompatíveis. | ANALYTICS_ARCHITECTURE.md e METRICS_CATALOG.md. |
| Knowledge Graph precisa definir schemas de relação, confidence por edge, stewardship e traversal autorizado. | Risco de Copilot e Navigation Intelligence sugerirem caminhos inconsistentes. | KNOWLEDGE_ARCHITECTURE.md. |
| Investigation precisa de contratos de lifecycle, evidence board, finding, closure e learning. | Risco de investigações virarem notas não auditáveis. | API_CONTRACTS.md, DATA_MODEL.md e KNOWLEDGE_ARCHITECTURE.md. |
| Narrative governance precisa definir review, approval, versioning e retention. | Risco de narrativa executiva virar apresentação sem auditabilidade. | KNOWLEDGE_ARCHITECTURE.md e EVENT_CATALOG.md. |
| Frontend ainda precisa definir arquitetura de rotas, estado contextual, deep links, permissões e componentes de investigação. | Risco de perda de contexto entre workspaces e entidades. | FRONTEND_ARCHITECTURE.md. |

## 29. Avaliação de Prontidão UX

| Alvo | Prontidão | Justificativa |
| --- | --- | --- |
| API_CONTRACTS.md | YES WITH ADJUSTMENTS | A arquitetura da informação define navegação, comandos implícitos por ações, escopos de consulta, busca, drill paths, timelines, comparisons, investigations, narratives, entity workspaces e contratos de perguntas do Copilot. Os contratos de API ainda devem formalizar canonical queries, autorização, paginação, acesso a evidência, graph traversal, timeline retrieval, comparison queries, investigation lifecycle e respostas de command rejection. |
| ANALYTICS_ARCHITECTURE.md | YES WITH ADJUSTMENTS | Métricas, health scores, forecasts, heat maps, cadeias de explicabilidade e perguntas de decisão estão especificadas. A inclusão de comparisons, timelines, persona landings e navigation intelligence exige detalhar normalização temporal, comparabilidade, confidence por célula, forecast versioning e métricas de maturity/learning. |
| KNOWLEDGE_ARCHITECTURE.md | YES WITH ADJUSTMENTS | Navegação de knowledge, Evidence Graph, Decision Graph, Capability Graph, Narrative, Investigation, Entity Workspace e Navigation Intelligence estão explícitos. A arquitetura de knowledge ainda deve definir schemas de relação, confidence por edge, graph stewardship, traversal autorizado, reusable learnings e governança da Narrative Library. |
| FRONTEND_ARCHITECTURE.md | YES WITH ADJUSTMENTS | A IA define landings, workspaces, cockpits, dashboards, heat maps, filtros, busca, timelines, comparisons, investigation workspace, narrative explorer, entity workspaces, alert experience e Copilot behavior. A arquitetura frontend ainda precisa definir routing contextual, state preservation, deep links, permission-aware rendering, data fetching, cache, acessibilidade e component contracts. |

## 30. Registro de Mudanças

| Área | Mudança |
| --- | --- |
| Personas | Expandida arquitetura de personas para diretores, executivos, superintendentes, gerentes, coordenadores, business, product, engineering, arquitetura, segurança, dados, compliance, auditoria e governança. |
| Perguntas | Criado catálogo formal de perguntas para estratégia, portfólio, discovery, requisitos, solução, delivery, valor, governança, arquitetura e inteligência. |
| Workspaces | Definidos workspaces obrigatórios com objetivos, personas, KPIs, alertas, heat maps e decisões suportadas. |
| Cockpits | Definidos cockpits corporativos para executive, portfolio, discovery, requirements, solution, architecture, delivery, validation, value, governance, flow, alert e knowledge. |
| Heat Maps | Definidas dimensões, métricas, drill-down, drill-up e ações para análise operacional, valor, arquitetura, alerta e portfólio. |
| Navegação | Definida navegação principal e propósito, perguntas, entidades, métricas e eventos por área. |
| Drill-down e Drill-up | Formalizadas regras universais e navegação de rastreabilidade para estratégia, Architecture Elevator, alertas e Need-to-Value. |
| Explainability | Definidas cadeias de explicabilidade para métricas e recomendações e níveis de explicação. |
| Alert Experience | Formalizado modelo informacional, ciclo de vida e restrições de encerramento com ação, evidência e validação. |
| Suporte à Decisão | Classificadas decisões operacionais, táticas, executivas e estratégicas com informações, métricas, eventos, evidências e explicações necessárias. |
| Busca | Definidos alvos e filtros de busca corporativa com expectativas de autorização, confiança e rastreabilidade. |
| Knowledge Navigation | Definidos caminhos de exploração do Knowledge Graph e regras de governança semântica. |
| Copilot Experience | Definidas perguntas obrigatórias do Copilot, contexto, métricas, evidências e comportamento explicativo. |
| Personalização | Definidas visões por papel, contexto, capability, portfólio, produto, unidade de negócio e ownership sem criar verdades alternativas. |
| Governança | Definidas regras de governança de UX conectando toda visão a pergunta, ownership de métrica, drill-down, ação e evidência. |
| Persona Landing Architecture | Adicionadas landing pages personalizadas por persona com widgets conceituais, informações obrigatórias, decisões suportadas e personalização. |
| Timeline Architecture | Adicionada navegação temporal corporativa para strategy, portfolio, capability, product, initiative, feature, alert, decision e value timelines. |
| Comparative Analysis Architecture | Adicionada capacidade nativa de comparação e Comparison Workspace para portfolios, capabilities, products, offers, business units, teams, releases e value cases. |
| Investigation Workspace | Adicionada entidade conceitual Investigation e workspace estruturado para evidência, findings, insights, root causes, recommendations, decisions, outcomes e learnings. |
| Narrative Architecture | Adicionadas capacidades de Narrative Workspace, Narrative Explorer e Narrative Library integradas ao Intelligence Model. |
| Entity Workspace Architecture | Definido workspace universal para entidades relevantes com overview, traceability, metrics, events, evidence, decisions, alerts, knowledge, timeline e impact analysis. |
| Navigation Intelligence Layer | Adicionada camada de navegação assistida por inteligência para sugerir próximos passos, investigações, comparações, entidades, narrativas e casos semelhantes. |
| UX Maturity Model | Adicionado modelo de maturidade de UX em seis níveis, posicionando a EDIP como alvo de Intelligence Driven Navigation. |
