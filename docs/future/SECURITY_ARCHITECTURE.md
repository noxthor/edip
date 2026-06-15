# Arquitetura de Seguranca

Este documento futuro detalhará segurança, privacidade, autorização, segregação de funções, auditoria e proteção de dados da EDIP.

## Status

Planejado. A documentação central já define princípios de governança, evidência, auditoria e minimização, mas ainda não detalha arquitetura de segurança.

## Fontes Obrigatórias

- `../ARCHITECTURE.md`
- `../DATA_MODEL.md`
- `../DOMAIN_MODEL.md`
- `../EVENT_CATALOG.md`
- `../UX_INFORMATION_ARCHITECTURE.md`

## Escopo Esperado

- identidade federada;
- autorização por persona, papel, unidade, produto, portfólio, criticidade e sensibilidade;
- segregação de funções para decisões, aprovações, closure de alertas e closure de cases;
- classificação de evidências e políticas de acesso;
- audit trail, retention e legal hold;
- proteção de dados pessoais e sensíveis;
- segurança para Copilot, search, graph traversal e narrative access;
- controles para Case Management, Evidence, Decision e Governance.

## Fora de Escopo

- configuração de provedor IAM específico;
- implementação de criptografia;
- controles físicos de infraestrutura;
- código de segurança.
