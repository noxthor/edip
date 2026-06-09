# Constituição Arquitetural da EDIP
## 1. Missão da EDIP
A Enterprise Delivery Intelligence Platform existe para conectar estratégia corporativa, portfólio, produto, delivery, engenharia e realização de valor em uma cadeia única de inteligência, governança e rastreabilidade.
A EDIP deve permitir que qualquer trabalho relevante seja explicado a partir da estratégia que o originou e que qualquer objetivo estratégico seja auditado até as entregas que o materializam.
A plataforma deve transformar dados dispersos de execução em decisões corporativas confiáveis, acionáveis e auditáveis.
A EDIP não é uma ferramenta operacional isolada; é uma plataforma de inteligência corporativa sobre o fluxo de valor.
A missão central é responder, com evidência: o que estamos tentando alcançar, por que isso importa, quem é responsável, como está sendo executado, qual risco existe e qual valor está sendo realizado.
## 2. Problema de Negócio
Grandes bancos executam estratégia por meio de múltiplos portfólios, produtos, times, sistemas, fornecedores, controles e ferramentas.
Essa execução normalmente se fragmenta entre planejamento estratégico, gestão de OKRs, portfólio, backlog, DevOps, financeiro, riscos, auditoria e métricas de negócio.
A fragmentação cria perda de contexto entre decisão executiva e trabalho operacional.
Sem rastreabilidade estratégica, iniciativas podem consumir capacidade e investimento sem conexão clara com temas, objetivos, OKRs, outcomes, KPIs ou benefícios esperados.
Sem governança bancária de métricas, decisões podem se apoiar em indicadores sem owner, fórmula, fonte, lineage, aprovação ou qualidade conhecida.
Sem drill-down, dashboards executivos se tornam apresentações estáticas e não mecanismos de investigação.
Sem drill-up, times operacionais executam tasks e stories sem clareza de propósito estratégico.
A EDIP resolve esse problema criando uma linguagem comum, uma cadeia corporativa de rastreabilidade, um modelo de portfólio orientado a valor e uma experiência de navegação entre níveis estratégicos, táticos, operacionais e analíticos.
## 3. Filosofia da Plataforma
Estratégia dirige execução.
Execução deve produzir evidência.
Evidência deve sustentar decisão.
Decisão deve ser auditável.
Métrica sem owner não é métrica governável.
Dashboard sem drill-down não é inteligência corporativa.
Trabalho sem rastreabilidade é risco de desperdício.
Forecast sem explicação não deve orientar decisão crítica.
Health score sem decomposição não deve ser usado como julgamento final.
A EDIP deve favorecer transparência, governança proporcional ao risco e redução de controle burocrático sem evidência.
A plataforma deve expor desalinhamentos, dependências, riscos, lacunas de dados, fragilidades operacionais e vazamento de valor.
A EDIP deve se integrar ao ecossistema existente do banco, preservando sistemas de origem quando eles forem maduros, governados e adequados ao seu domínio.
A EDIP deve criar uma visão canônica sem apagar a complexidade real da organização, dos produtos, dos portfólios e dos controles bancários.
## 4. Princípios Arquiteturais
Modelar por domínios de negócio, não por telas, times ou organograma.
Separar capacidades transacionais, analíticas e experienciais.
Manter contratos explícitos entre contextos de domínio.
Evitar acoplamento por banco de dados compartilhado entre domínios.
Usar APIs para comandos e consultas transacionais bem delimitadas.
Usar eventos para fatos de domínio relevantes, integração assíncrona e construção de projeções.
Projetar idempotência, versionamento e compatibilidade desde o início.
Tratar auditoria, segurança, autorização, observabilidade e lineage como capacidades centrais, não como anexos.
Tratar métricas, scores, forecasts e benefícios realizados como produtos de dados governados.
Separar visão executiva de cálculo analítico e de dado transacional.
Permitir evolução incremental sem quebrar a cadeia de rastreabilidade.
Garantir que a mesma verdade de dados possa ser apresentada de forma distinta para cada persona.
Privilegiar explicabilidade sobre automação opaca.
Toda decisão automatizada ou recomendação deve poder ser explicada por dados, regras e premissas.
## 5. Conceitos Fundamentais do Domínio
Estratégia Corporativa define a direção de longo prazo do banco.
Tema Estratégico agrupa prioridades corporativas de alto impacto.
Objetivo Estratégico descreve um resultado desejado e mensurável.
OKR traduz objetivos em resultados-chave acompanháveis por ciclo.
Outcome representa mudança observável em negócio, cliente, risco, eficiência, operação ou experiência.
KPI mede progresso, resultado ou saúde de uma dimensão relevante.
Portfólio organiza temas, investimentos, oportunidades, iniciativas, capacidade, riscos e decisões em torno de uma estratégia.
Investimento representa alocação aprovada ou proposta de funding, capacidade ou esforço relevante.
Funding representa envelope, ciclo ou decisão de financiamento associada a portfólio e iniciativa.
Ideia é uma possibilidade inicial ainda sem qualificação suficiente.
Oportunidade é uma hipótese qualificada de valor, risco, eficiência ou crescimento.
Iniciativa é uma unidade tática de execução conectada a portfólio, investimento, outcome ou KPI.
Épico agrupa escopo significativo dentro de uma iniciativa.
Feature materializa capacidade funcional, técnica ou operacional.
Story descreve uma fatia entregável de valor ou comportamento.
Task representa trabalho operacional necessário para concluir uma story ou feature.
Owner é a pessoa, papel ou grupo responsável por decisão, métrica, entidade ou resultado.
Evidência é qualquer artefato verificável que sustenta status, decisão, métrica, controle ou valor.
Value Case descreve hipótese, baseline, target, benefício esperado, premissas e forma de comprovação de valor.
Benefício Realizado é valor medido, validado e associado a período, evidência, fonte e responsável.
Controle é uma obrigação verificável derivada de política, risco, arquitetura, segurança, compliance ou auditoria.
Sinal de Observabilidade é dado operacional ou analítico que permite explicar saúde, comportamento, falha, atraso, risco ou tendência.
## 6. Cadeia de Rastreabilidade Corporativa
A cadeia padrão da EDIP é:
Estratégia Corporativa -> Tema Estratégico -> Objetivo Estratégico -> OKR -> Outcome -> KPI -> Portfólio -> Investimento -> Iniciativa -> Épico -> Feature -> Story -> Task -> Entrega -> Benefício Realizado.
Toda iniciativa deve possuir vínculo explícito com portfólio, investimento ou justificativa formal de exceção.
Toda iniciativa estratégica deve declarar outcome esperado, KPI impactado, owner, hipótese de valor e critério de sucesso.
Todo épico deve estar vinculado a uma iniciativa.
Toda feature deve estar vinculada a um épico.
Stories e tasks devem herdar rastreabilidade da feature ou do épico correspondente.
Todo KPI deve possuir owner, fórmula, fonte, periodicidade, baseline, target e nível de confiança.
Todo investimento deve possuir owner, ciclo, fonte, valor aprovado ou estimado, capacidade comprometida e hipótese de retorno.
Todo benefício realizado deve possuir período, evidência, fonte, método de cálculo, validador e vínculo com iniciativa ou outcome.
Toda decisão relevante deve preservar contexto, responsável, justificativa, data e evidência.
Toda lacuna de rastreabilidade deve ser visível, priorizável e tratável.
Rastreabilidade deve ser bidirecional: top-down para execução e bottom-up para justificativa estratégica.
Rastreabilidade não pode ser inferida apenas por texto, nomenclatura ou proximidade organizacional; ela deve ser representada como relação explícita e auditável.
## 7. Personas e Objetivos
Diretores precisam avaliar execução estratégica, valor, risco, prioridades e decisões executivas.
Superintendentes precisam orquestrar portfólios, capacidade, dependências, riscos e outcomes.
Gerentes precisam gerir iniciativas, escopo, riscos, dependências, progresso e comunicação tática.
Coordenadores precisam acompanhar execução operacional, bloqueios, aging, owners e previsibilidade.
Product Owners precisam maximizar valor, priorizar backlog, validar oportunidades, outcomes e KPIs.
Scrum Masters precisam promover fluxo, remover impedimentos, reduzir WIP e aumentar previsibilidade.
Arquitetos Corporativos precisam garantir aderência a capacidades, padrões, integrações, dados, segurança e resiliência.
PMO precisa governar portfólio, status, decisões, funding, dependências, comitês e qualidade de dados.
Especialistas precisam validar métricas, evidências, controles, riscos, compliance, dados, produto ou processo.
Líderes Técnicos precisam conectar decisões técnicas, débitos, riscos e releases ao contexto de produto e estratégia.
Desenvolvedores precisam entender propósito, prioridade, critérios, dependências e impacto de seu trabalho.
Cada persona deve ter uma visão própria, mas nenhuma persona deve operar sobre uma verdade de dados alternativa.
## 8. Enterprise Zoom Model
A EDIP deve permitir zoom corporativo entre níveis sem perder contexto.
O nível corporativo mostra estratégia, temas, objetivos, OKRs e KPIs.
O nível executivo mostra portfólios, investimentos, capacidade, outcomes, riscos, dependências críticas e realização de valor.
O nível tático mostra iniciativas, oportunidades, épicos, decisões, riscos e forecast.
O nível operacional mostra features, stories, tasks, bloqueios, fluxo e responsáveis.
O nível analítico mostra tendências, scores, forecasts, value realization, lineage, qualidade de dados, observabilidade e evidências.
Zoom-in significa partir de uma síntese para seus componentes causadores.
Zoom-out significa partir de um item operacional para sua justificativa estratégica.
Nenhum nível deve ocultar a origem dos dados que sustentam a visão apresentada.
Nenhum score, forecast ou alerta deve impedir investigação detalhada.
O zoom corporativo deve preservar filtros, permissões e contexto de decisão.
## 9. Modelo de Navegação
A navegação primária deve seguir o fluxo natural de decisão: estratégia, portfólio, produto, delivery, value realization, métricas, governança, observabilidade e alertas.
Todo dashboard deve possuir drill-down até o nível suportado pela rastreabilidade disponível.
Todo item operacional deve possuir drill-up até o objetivo, OKR, outcome ou KPI que justifica sua existência.
A navegação deve permitir alternar entre visão por estratégia, portfólio, investimento, produto, time, KPI, risco, benefício e controle.
Filtros devem ser consistentes entre visões e devem deixar claro o recorte aplicado.
Visões compartilháveis devem preservar filtros, período, escopo e permissões.
Entidades sem owner, sem vínculo ou com dado inconsistente devem aparecer como exceções, não desaparecer do produto.
Navegação executiva deve priorizar exceções, decisões e impactos.
Navegação operacional deve priorizar fluxo, bloqueios, contexto e próxima ação.
## 10. Health Scores
Health scores são sinais de saúde, não verdades absolutas.
Todo health score deve ser decomponível em componentes explicáveis.
Componentes típicos incluem alinhamento estratégico, progresso, previsibilidade, valor, risco, dependências, capacidade, governança, observabilidade e qualidade de dados.
Scores devem indicar tendência, não apenas posição atual.
Scores devem explicitar dados ausentes ou de baixa confiança.
Scores não devem combinar dimensões incompatíveis sem fórmula, peso, faixa e interpretação documentados.
Scores devem ajudar a priorizar investigação e decisão.
Nenhum score crítico deve existir sem owner, causa provável, impacto e ação recomendada.
Mudanças relevantes de score devem gerar eventos, histórico e justificativa.
Scores devem ser comparáveis no tempo, mas sensíveis ao contexto de cada entidade.
## 11. Forecasting
Forecasting existe para antecipar risco, prazo, valor, capacidade, funding, cumprimento de objetivos e realização de benefícios.
Forecasts devem sempre expor premissas, drivers, período e nível de confiança.
Forecasts devem diferenciar cenário otimista, provável e pessimista quando aplicável.
Forecasts não devem substituir responsabilidade humana em decisões críticas.
Forecasts devem declarar horizonte, granularidade, frequência de atualização, população analisada e uso permitido.
Forecasts devem considerar histórico, fluxo, aging, dependências, riscos, capacidade, funding, mudanças de escopo, qualidade, incidentes e tendência de KPIs.
Forecasts de valor devem distinguir valor planejado, valor previsto e valor realizado.
Forecasts de value realization devem distinguir hipótese, baseline, target, forecast, realizado, evidência e confiança.
Forecasts de entrega devem distinguir prazo, escopo, qualidade, dependência e risco.
Forecasts de OKR e KPI devem indicar probabilidade de atingir target no período.
Forecasts devem permitir drill-down para os fatores que explicam a projeção.
Forecasts com baixa qualidade de dados devem ser marcados explicitamente.
Forecasts usados em decisão executiva devem registrar versão, data, premissas e principais fatores de variação.
## 12. Governança e Auditoria
Toda decisão relevante deve ser rastreável, justificável e auditável.
Decisões de priorização, funding, pausa, cancelamento, mudança de escopo, aceite de risco, exceção arquitetural, aprovação de métrica e realização de valor exigem registro formal.
Toda aprovação deve registrar solicitante, aprovador, escopo, data, decisão, justificativa e evidência.
Toda métrica usada em decisão deve possuir lineage suficiente para auditoria.
Toda evidência deve estar associada à entidade, decisão ou controle que sustenta.
Todo controle deve possuir owner, escopo, periodicidade, evidência esperada, status e consequência de não conformidade.
Segregação de funções deve ser preservada em decisões críticas.
Permissões devem considerar persona, papel, unidade, produto, portfólio, criticidade e sensibilidade.
Auditoria deve ser consequência natural do uso da plataforma, não uma atividade manual posterior.
Exceções devem ter owner, prazo, motivo e plano de encerramento.
Dados pessoais e sensíveis devem seguir minimização, finalidade, necessidade e proteção adequada.
Governança bancária deve cobrir risco operacional, compliance, auditoria interna, segurança, privacidade, continuidade, fornecedores e resiliência.
Observabilidade corporativa deve permitir reconstruir eventos, integrações, cálculos, decisões, falhas, atrasos e impactos.
## 13. Regras de Qualidade
Toda entidade relevante deve possuir identificação, owner, status e contexto.
Todo indicador deve possuir owner, definição, fórmula, fonte, periodicidade, baseline, target e confiança.
Todo dashboard deve possuir drill-down.
Todo dado apresentado deve indicar origem ou permitir acesso à origem.
Toda integração deve tratar duplicidade, atraso, falha, reconciliação, idempotência, versionamento e indisponibilidade da fonte.
Toda regra de cálculo deve ser documentada e testável.
Toda alteração de domínio deve preservar rastreabilidade existente.
Toda lacuna de dados deve ser visível para o usuário responsável.
Toda recomendação deve indicar motivo, impacto e ação sugerida.
Toda experiência deve diferenciar ausência de dado, dado atrasado, dado inconsistente e resultado real.
Qualidade de dados deve ser medida como parte da saúde da plataforma.
Observabilidade deve medir frescor, completude, latência, falha de ingestão, lag de processamento, erro de cálculo e divergência entre fonte e projeção.
Value realization deve diferenciar benefício esperado, benefício forecast, benefício realizado, benefício validado e benefício rejeitado.
## 14. Regras para Evolução do Domínio
Novos conceitos de domínio devem ter definição clara, owner conceitual e relação com a cadeia de rastreabilidade.
Nenhuma entidade deve ser criada apenas para satisfazer uma tela, integração ou relatório específico.
Nenhum campo crítico deve ser adicionado sem entender impacto em governança, auditoria, filtros, métricas e integrações.
Novas métricas devem declarar fórmula, fonte, periodicidade, owner, unidade e interpretação.
Novas entidades de portfólio devem declarar relação com tema estratégico, investimento, capacidade, risco, decisão e valor esperado.
Novos scores devem declarar componentes, pesos, faixas, limitações e explicabilidade.
Novos forecasts devem declarar premissas, entradas, saídas, confiança e uso permitido.
Novos modelos de value realization devem declarar baseline, hipótese, método de cálculo, evidência, validação e regra de atribuição.
Novos eventos de domínio devem representar fatos relevantes, não detalhes acidentais de implementação.
Novas APIs devem respeitar fronteiras de domínio e não expor acoplamentos internos desnecessários.
Mudanças em rastreabilidade devem atualizar navegação, drill-down, drill-up, dashboards e auditoria.
Mudanças de domínio devem ser compatíveis com evolução histórica e análise temporal.
Mudanças em governança bancária devem preservar segregação de funções, trilha de auditoria, evidência e controles aplicáveis.
Toda evolução deve favorecer clareza semântica sobre conveniência técnica imediata.
## 15. Tecnologias Estratégicas
As tecnologias estratégicas devem servir à missão da plataforma, não defini-la.
Frontend estratégico: experiências web corporativas, tipadas, auditáveis e orientadas a dashboards, navegação e investigação.
Backend estratégico: serviços de domínio explícitos, APIs governadas, processamento assíncrono, integrações resilientes e regras testáveis.
Persistência transacional estratégica: armazenamento consistente para entidades de domínio, decisões, owners, estados e auditoria operacional.
Analytics estratégico: armazenamento e consulta eficiente de séries históricas, métricas, scores, forecasts, eventos e projeções.
Contratos estratégicos: APIs, eventos, schemas e modelos analíticos versionados e compatíveis.
Observabilidade estratégica: logs, métricas, traces, auditoria, lineage, qualidade de dados, qualidade de cálculo e saúde de integrações como sinais de primeira classe.
Segurança estratégica: identidade federada, autorização granular, segregação de funções, criptografia e governança de acesso.
Tecnologias podem evoluir; os princípios de rastreabilidade, governança, explicabilidade e separação de responsabilidades não podem ser descartados.
## 16. Definition of Done para alterações geradas por IA
Toda alteração gerada por IA deve preservar a missão da EDIP e a cadeia de rastreabilidade corporativa.
Toda alteração deve ser consistente com as personas, seus objetivos e suas decisões suportadas.
Toda alteração que introduz conceito de domínio deve definir seu significado, owner, relacionamentos e impacto em navegação.
Toda alteração que afeta dashboards deve preservar drill-down e, quando aplicável, drill-up.
Toda alteração que afeta métricas deve documentar fórmula, fonte, owner, periodicidade, baseline, target e qualidade.
Toda alteração que afeta health scores deve documentar componentes, interpretação, limites e explicabilidade.
Toda alteração que afeta forecasts deve documentar premissas, entradas, saídas, confiança e ações suportadas.
Toda alteração que afeta portfólio deve preservar relação com estratégia, investimento, capacidade, risco, decisão e valor.
Toda alteração que afeta value realization deve preservar baseline, hipótese, evidência, validação e atribuição de benefício.
Toda alteração que afeta governança deve preservar auditoria, evidência, segregação de funções e rastreabilidade de decisões.
Toda alteração que afeta observabilidade deve preservar capacidade de diagnosticar origem, atraso, falha, cálculo e impacto.
Toda alteração técnica deve ser acompanhada de documentação proporcional ao impacto de domínio.
Toda alteração de domínio deve considerar impacto em APIs, eventos, dados analíticos, permissões e experiência de uso.
Toda alteração deve incluir testes ou justificar explicitamente por que testes não se aplicam.
Toda alteração deve evitar refatorações não relacionadas ao objetivo solicitado.
Toda alteração deve proteger mudanças existentes de outros contribuidores.
Toda resposta final de agente deve explicar o que mudou, onde mudou e quais validações foram executadas.
Uma mudança só está concluída quando melhora a plataforma sem degradar rastreabilidade, governança, qualidade de dados ou capacidade de decisão.
